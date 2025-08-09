Search for an organization's GitHub repositories for sensitive data that has been accidentally committed, or information that could lead to the discovery of a vulnerability.
Start by finding the GitHub usernames relevant to you target.
Search of the product names via GitHub's search bar.
When you've found a relevant repository, pay special attention for the Issues and Commits sections. Look for any protection mechanisms implemented to see if you can bypass them.
Search for terms like 'key', 'secret' and 'password' to locate hardcoded user credentials. 
After you've found leaked credentials, you can use [KeyHacks](https://github.com/streaak/keyhacks/).
See if the source code deals with important functions like such as authentication to code that deals with user input, such as HTTP requests parameters, HTTP headers, HTTP request paths, database entries, file reads and file uploads.
Pay attention to outdated dependencies an the unchecked use of dangerous functions are also a huge source of bugs.
Tools like Gitrob and TruffleHog can automate the GitHub recon process. [Gitrob](https://github.com/michenriksen/gitrob)
locates potentially sensitive files pushed to public repositories on GitHub. [TruffleHog](https://github.com/trufflesecurity/trufflehog/) 
specializes in finding secrets in repositories by conducting regex searches and scanning for high-entropy strings.
