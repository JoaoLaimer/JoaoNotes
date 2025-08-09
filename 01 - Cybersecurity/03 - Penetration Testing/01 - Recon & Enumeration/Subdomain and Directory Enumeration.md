After finding domains, we should now find as many subdomains as we can on the target. The best way of finding subdomains is using automation. Tools like Sublist3r, SubBrute, Amass and Gobuster can enumerate subdomains automatically.
Tools like Dirsearch and Gobuster can enumerate directories using wordlists.

### Spidering the Site
Another way of discovering directories and paths is through web spidering, or web crawling, a process used to identify all pages on a site. A web spider tool starts with a page to visit, it then identifies all URLs in that page and visits them. Recursively it visits as many sites it uncovers.
OWASP Zed Attack Proxy (ZAP) has a web spider tool you can use. Burpsuite has an equivalent tool called crawler.