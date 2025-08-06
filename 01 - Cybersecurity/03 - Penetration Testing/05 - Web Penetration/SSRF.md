SSRF (Server Side Request Forgery) is a web application security vulnerability that allows the attacker to force the server to make **unauthorised requests to any local or external source** on behalf of the web server. SSRF **allows an attacker to interact with internal systems**, potentially leading to data leaks, service disruption, or even remote code execution.

An SSRF can arise when user-provided data is used to construct a request, such as forming a URL. An SSRF can arise from different types of software system as long as the software operates in a networked environment.

SSRF earned a spot in [OWASP's top 10 list](https://owasp.org/Top10/A10_2021-Server-Side_Request_Forgery_%28SSRF%29/) making it imperative to understand and defend against it.

## Basic SSRF
﻿Basic SSRF is a web attack technique where an attacker tricks a server into making requests on their behalf, often targeting internal systems or third-party services. By exploiting vulnerabilities in input validation, the attacker can gain unauthorized access to sensitive information or control over remote resources, posing a significant security risk to the targeted application and its underlying infrastructure.
## Blind SSRF With Out-of-Band
Out-of-band communication is a channel used to receive responses indirectly from the target server. This approach is practical when the server's responses are not directly accessible to the attacker.
## Semi-Blind SSRF (Time-based)  
Time-based SSRF is a variation of SSRF where the attacker leverages timing-related clues or delays to infer the success or failure of their malicious requests. By **observing how long it takes for the application to respond**, the attacker can make educated guesses about whether their SSRF attack was successful.