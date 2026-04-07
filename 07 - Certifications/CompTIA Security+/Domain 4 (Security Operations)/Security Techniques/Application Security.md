Critical aspect of software development that focuses on building applications that are secure by design.
## Input Validation
Acts as a gatekeeper to ensure that applications only act on well-defined and uncontaminated data.
### Validation Rules
These rules delineate acceptable and unacceptable inputs.
## Cookies
Small pieces of data stored on the user's computer by the web browser while browsing a website.
### Secure Cookies
Transmitted over secure HTTPS connections to prevent potential eavesdroppers from intercepting the cookie data.
Always refrain from utilizing persistent cookies for session verification.

Enable the secure attribute on the cookie to ensure that is not transmitted over an insecure HTTP connection accidentally.

To secure cookies from clinet-side access, use the HttpOnly attribute.
## Static Code Analysis (SAST)
A method of debugging an application by reviewing and examining its source code before the program is ever run.
### Manual Code Review
Performing the code review using a human instead of a static software analysis tool.
### Dynamic Code Analysis
Testing method that analyzes an application while it's running.
**Fuzzing**: Finds software flaws by bombarding it with random data to trigger crashes and security vulnerabilities.
**Stress Testing**: Type of software testing that evaluates the stability and reliability of a system undes extreme conditions.
## Code Signing
Technique used to confirm the identity of the software author and guarantee that the code has not been altered or corrupted since it was signed.
The certificate has a a public key that the receiving computer uses to check and confirm the signature is valid.
The presence of a digital signature on a file or program does not guarantee its absolute security.

The digital signature confirms that the file is in the same state that the developer intended it to be when they distributed it.
## Sandboxing
Security mechanism that is used to isolate running program by limiting the resources they can access and the changes they can make to a system.
Sandboxes allow for testing code under various environment, not just the current system configuration.
