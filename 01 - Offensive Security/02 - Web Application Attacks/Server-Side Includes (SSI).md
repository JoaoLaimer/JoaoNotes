## Server-Side Includes (SSI) Injection

Similar to server-side templates, server-side includes (SSI) can be used to generate HTML responses dynamically. SSI directives instruct the webserver to include additional content dynamically. These directives are embedded into HTML files. For instance, SSI can be used to include content that is present in all HTML pages, such as headers or footers. When an attacker can inject commands into the SSI directives, [Server-Side Includes (SSI) Injection](https://owasp.org/www-community/attacks/Server-Side_Includes_\(SSI\)_Injection) can occur. SSI injection can lead to data leakage or even remote code execution.
SSI is supported by many popular web servers such as [Apache](https://httpd.apache.org/docs/current/howto/ssi.html) and [IIS](https://learn.microsoft.com/en-us/iis/configuration/system.webserver/serversideinclude). The use of SSI can often be inferred from the file extension. Typical file extensions include `.shtml`, `.shtm`, and `.stm`. However, web servers can be configured to support SSI directives in arbitrary file extensions.

## SSI Directives
SSI utilizes `directives` to add dynamically generated content to a static HTML page. These directives consist of the following components:
- `name`: the directive's name
- `parameter name`: one or more parameters
- `value`: one or more parameter values
An SSI directive has the following syntax:
```ssi
<!--#name param1="value1" param2="value" -->
```

The following are some common SSI directives.
#### printenv
This directive prints environment variables. It does not take any variables.
```ssi
<!--#printenv -->
```
#### config
This directive changes the SSI configuration by specifying corresponding parameters. For instance, it can be used to change the error message using the `errmsg` parameter:
```ssi
<!--#config errmsg="Error!" -->
```
#### echo
This directive prints the value of any variable given in the `var` parameter. Multiple variables can be printed by specifying multiple `var` parameters. For instance, the following variables are supported:
- `DOCUMENT_NAME`: the current file's name
- `DOCUMENT_URI`: the current file's URI
- `LAST_MODIFIED`: timestamp of the last modification of the current file
- `DATE_LOCAL`: local server time
```ssi
<!--#echo var="DOCUMENT_NAME" var="DATE_LOCAL" -->
```
#### exec
This directive executes the command given in the `cmd` parameter:
```ssi
<!--#exec cmd="whoami" -->
```

#### include
This directive includes the file specified in the `virtual` parameter. It only allows for the inclusion of files in the web root directory.
```ssi
<!--#include virtual="index.html" -->
```
