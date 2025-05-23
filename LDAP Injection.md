LDAP injection happens when input is not sanitized before being incorporated into queries. This can lead to manipulation of directory data and unauthorized access.
The process is analogous to SQL Injection, where malicious SQL statements are injected into queries to manipulate database operations. In LDAP Injection, the malicious code targets LDAP queries instead.
### Common Attack Vectors
1. **Authentication Bypass:** Modifying LDAP authentication queries to log in as another user without knowing their password.
2. **Unauthorized Data Access:** Altering LDAP search queries to retrieve sensitive information not intended for the attacker's access.
3. **Data Manipulation:** Injecting queries that modify the LDAP directory, such as adding or modifying user attributes.
## Authentication Bypass Techniques
#### Tautology-Based Injection
Involves inserting conditions into an LDAP query that are inherently true, thus ensuring the query always returns a positive result, irrespective of the intended logic.
Example: Consider a simple username and password query
`(&(uid={userInput})(userPassword={passwordInput}))`
We can use tautology-based input, such as `*)(|(&` for `{userInput}` and `pwd)` for `{passwordInput}` which transforms the query into:

`(&(uid=*)(|(&)(userPassword=pwd)))`

This query bypasses password checking due to how logical operators are used within the filter.
1. `(uid=*)`: This filter matches with any entry with `uid` attribute, due to the wildcard `*`.
2. `(|(&)(userPassword=pwd))`: The OR(`|`) operator, meaning that any of the two conditions enclosed needs to be true for the filter to pass. In LDAP an empty AND (`(&)`) condition is always considered true.
Putting all together the filter will always be evaluated as true because of the `(&)` condition.
#### Wildcard Injection
An attacker might use a wildcard as input in both uid and userPassword. Using a `*` for `{userInput}` could force the query to ignore specific usernames and focus instead on the password. However, since a wildcard is also present in the `{passwordInput}`, it does not validate the content of the password field against a specific expected value. Instead, it only checks for the presence of the `userPassword` attribute, regardless of its content.

This means that the query will return a positive match for any user without verifying that the password provided during authentication matches the stored password. As a result, this effectively bypasses the password-checking mechanism.

## Blind LDAP Injection
Blind LDAP Injection is a more subtle variant of LDAP Injection, where the attacker doesn't receive direct output from the injected payload. Instead, they must infer information based on the application's behavior.
#### Techniques for Extracting Information
1. **Boolean Exploitation:** This involves injecting conditions that are evaluated to be true or false and observing the application's response to infer data. For example, if the application behaves differently when the condition is true, the attacker can deduce that the injected condition matches an existing entry in the LDAP directory.
2. **Error-Based Inference:** In some cases, specific injections might trigger error messages or peculiar application behaviour, providing clues about the LDAP structure or confirming the success of particular payloads.