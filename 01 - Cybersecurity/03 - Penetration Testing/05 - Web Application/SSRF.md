SSRF (Server Side Request Forgery) is a web application security vulnerability that allows the attacker to force the server to make **unauthorised requests to any local or external source** on behalf of the web server. SSRF **allows an attacker to interact with internal systems**, potentially leading to data leaks, service disruption, or even remote code execution.

An SSRF can arise when user-provided data is used to construct a request, such as forming a URL. An SSRF can arise from different types of software system as long as the software operates in a networked environment.

SSRF earned a spot in [OWASP's top 10 list](https://owasp.org/Top10/A10_2021-Server-Side_Request_Forgery_%28SSRF%29/) making it imperative to understand and defend against it.
The following URL schemes are commonly used in the exploitation of SSRF vulnerabilities:

- `http://` and `https://`: These URL schemes fetch content via HTTP/S requests. An attacker might use this in the exploitation of SSRF vulnerabilities to bypass WAFs, access restricted endpoints, or access endpoints in the internal network
- `file://`: This URL scheme reads a file from the local file system. An attacker might use this in the exploitation of SSRF vulnerabilities to read local files on the web server (LFI)
- `gopher://`: This protocol can send arbitrary bytes to the specified address. An attacker might use this in the exploitation of SSRF vulnerabilities to send HTTP POST requests with arbitrary payloads or communicate with other services such as SMTP servers or databases
## Basic SSRF
﻿Basic SSRF is a web attack technique where an attacker tricks a server into making requests on their behalf, often targeting internal systems or third-party services. By exploiting vulnerabilities in input validation, the attacker can gain unauthorized access to sensitive information or control over remote resources, posing a significant security risk to the targeted application and its underlying infrastructure.

```shell
$ ffuf -w /opt/SecLists/Discovery/Web-Content/raft-small-words.txt -u http://172.17.0.2/index.php -X POST -H "Content-Type: application/x-www-form-urlencoded" -d "dateserver=http://dateserver.htb/FUZZ.php&date=2024-01-01" -fr "Server at dateserver.htb Port 80"
```

## Confirming SSRF
To confirm an SSRF vulnerability, let us supply a URL pointing to our system to the web application.
In a `netcat` listener, we can receive a connection, thus confirming SSRF

## Local File Inclusion (LFI)
Since the URL scheme is part of the URL supplied to the web application, let us attempt to read local files from the file system using the `file://` URL scheme. We can achieve this by supplying the URL `file:///etc/passwd`
## The gopher Protocol
We need to URL-encode all special characters to construct a valid gopher URL
In particular, spaces (`%20`) and newlines (`%0D%0A`) must be URL-encoded. Afterward, we need to prefix the data with the gopher URL scheme, the target host and port, and an underscore, resulting in the following gopher URL:

```
gopher://dateserver.htb:80/_POST%20/admin.php%20HTTP%2F1.1%0D%0AHost:%20dateserver.htb%0D%0AContent-Length:%2013%0D%0AContent-Type:%20application/x-www-form-urlencoded%0D%0A%0D%0Aadminpw%3Dadmin
```
We can use the `gopher` protocol to interact with many internal services, not just HTTP servers. Imagine a scenario where we identify, through an SSRF vulnerability, that TCP port 25 is open locally. This is the standard port for SMTP servers. We can use Gopher to interact with this internal SMTP server as well. However, constructing syntactically and semantically correct gopher URLs can take time and effort. Thus, we will utilize the tool [Gopherus](https://github.com/tarunkant/Gopherus) to generate gopher URLs for us. The following services are supported:

- MySQL
- PostgreSQL
- FastCGI
- Redis
- SMTP
- Zabbix
- pymemcache
- rbmemcache
- phpmemcache
- dmpmemcache
## Blind SSRF With Out-of-Band
Out-of-band communication is a channel used to receive responses indirectly from the target server. This approach is practical when the server's responses are not directly accessible to the attacker.
Exploiting blind SSRF vulnerabilities is generally severely limited compared to non-blind SSRF vulnerabilities. However, depending on the web application's behavior, we might still be able to conduct a (restricted) local port scan of the system, provided the response differs for open and closed ports.
## Semi-Blind SSRF (Time-based)  
Time-based SSRF is a variation of SSRF where the attacker leverages timing-related clues or delays to infer the success or failure of their malicious requests. By **observing how long it takes for the application to respond**, the attacker can make educated guesses about whether their SSRF attack was successful.


