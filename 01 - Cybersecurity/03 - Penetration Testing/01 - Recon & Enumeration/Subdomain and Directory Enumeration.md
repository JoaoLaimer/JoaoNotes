After finding domains, we should now find as many subdomains as we can on the target. The best way of finding subdomains is using automation. Tools like Sublist3r, SubBrute, Amass and Gobuster can enumerate subdomains automatically.
Tools like Dirsearch and Gobuster can enumerate directories using wordlists.

### Spidering the Site
Another way of discovering directories and paths is through web spidering, or web crawling, a process used to identify all pages on a site. A web spider tool starts with a page to visit, it then identifies all URLs in that page and visits them. Recursively it visits as many sites it uncovers.
OWASP Zed Attack Proxy (ZAP) has a web spider tool you can use. Burpsuite has an equivalent tool called crawler.

### Active Subdomain Enumeration

This involves directly interacting with the target domain's DNS servers to uncover subdomains. One method is attempting a `DNS zone transfer`, where a misconfigured server might inadvertently leak a complete list of subdomains. However, due to tightened security measures, this is rarely successful.

A more common active technique is `brute-force enumeration`, which involves systematically testing a list of potential subdomain names against the target domain. Tools like `dnsenum`, `ffuf`, and `gobuster` can automate this process, using wordlists of common subdomain names or custom-generated lists based on specific patterns.

There are several tools available that excel at brute-force enumeration:

|Tool|Description|
|---|---|
|[dnsenum](https://github.com/fwaeytens/dnsenum)|Comprehensive DNS enumeration tool that supports dictionary and brute-force attacks for discovering subdomains.|
|[fierce](https://github.com/mschwager/fierce)|User-friendly tool for recursive subdomain discovery, featuring wildcard detection and an easy-to-use interface.|
|[dnsrecon](https://github.com/darkoperator/dnsrecon)|Versatile tool that combines multiple DNS reconnaissance techniques and offers customisable output formats.|
|[amass](https://github.com/owasp-amass/amass)|Actively maintained tool focused on subdomain discovery, known for its integration with other tools and extensive data sources.|
|[assetfinder](https://github.com/tomnomnom/assetfinder)|Simple yet effective tool for finding subdomains using various techniques, ideal for quick and lightweight scans.|
|[puredns](https://github.com/d3mondev/puredns)|Powerful and flexible DNS brute-forcing tool, capable of resolving and filtering results effectively.|

### Passive Subdomain Enumeration

This relies on external sources of information to discover subdomains without directly querying the target's DNS servers. One valuable resource is `Certificate Transparency (CT) logs`, public repositories of SSL/TLS certificates. These certificates often include a list of associated subdomains in their Subject Alternative Name (SAN) field, providing a treasure trove of potential targets.

Another passive approach involves utilising `search engines` like Google or DuckDuckGo. By employing specialised search operators (e.g., `site:`), you can filter results to show only subdomains related to the target domain.

Additionally, various online databases and tools aggregate DNS data from multiple sources, allowing you to search for subdomains without directly interacting with the target.

### Virtual Hosts
Virtual hosts are configurations within a web server that allow multiple websites or applications to be hosted on a single server. They can be associated with top-level domains (e.g., `example.com`) or subdomains (e.g., `dev.example.com`). Each virtual host can have its own separate configuration, enabling precise control over how requests are handled. 
Websites often have subdomains that are not public and won't appear in DNS records. These `subdomains` are only accessible internally or through specific configurations. `VHost fuzzing` is a technique to discover public and non-public `subdomains` and `VHosts` by testing various hostnames against a known IP address.

There are three primary types of virtual hosting, each with its advantages and drawbacks:

1. `Name-Based Virtual Hosting`: This method relies solely on the `HTTP Host header` to distinguish between websites. It is the most common and flexible method, as it doesn't require multiple IP addresses. It’s cost-effective, easy to set up, and supports most modern web servers. However, it requires the web server to support name-based `virtual hosting` and can have limitations with certain protocols like `SSL/TLS`.
2. `IP-Based Virtual Hosting`: This type of hosting assigns a unique IP address to each website hosted on the server. The server determines which website to serve based on the IP address to which the request was sent. It doesn't rely on the `Host header`, can be used with any protocol, and offers better isolation between websites. Still, it requires multiple IP addresses, which can be expensive and less scalable.
3. `Port-Based Virtual Hosting`: Different websites are associated with different ports on the same IP address. For example, one website might be accessible on port 80, while another is on port 8080. `Port-based virtual hosting` can be used when IP addresses are limited, but it’s not as common or user-friendly as `name-based virtual hosting` and might require users to specify the port number in the URL.

Several tools are available to aid in the discovery of virtual hosts:

| Tool                                                 | Description                                                                                                      | Features                                                        |
| ---------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| [gobuster](https://github.com/OJ/gobuster)           | A multi-purpose tool often used for directory/file brute-forcing, but also effective for virtual host discovery. | Fast, supports multiple HTTP methods, can use custom wordlists. |
| [Feroxbuster](https://github.com/epi052/feroxbuster) | Similar to Gobuster, but with a Rust-based implementation, known for its speed and flexibility.                  | Supports recursion, wildcard discovery, and various filters.    |
| [[ffuf]]                                             | Another fast web fuzzer that can be used for virtual host discovery by fuzzing the `Host` header.                | Customizable wordlist input and filtering options.              |
