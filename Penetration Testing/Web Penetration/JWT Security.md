## Token-Based Authentication
### Token-Based Session Management
Instead of using the browser's cookie management features, it relies on client-side code for the process for the process. After authentication, the web app provides a token within the request body. Using client-side JS code, this token is then stored in the browser's LocalStorage.
When a new request is made, JavaScript code must load the token from storage and attach it as a header. 
One of the most common types of tokens is JSON Web Tokens (JWT), which are passed through the `Authorization: Bearer` header.

## JSON Web Tokens
JWTs are self-contained tokens that can be used to securely transmit session information. It is an [open standard](https://tools.ietf.org/html/rfc7519), providing information for any developer or library creator who wants to use JWTs.

#### JWT Structure
Consists of three components, each Base64Url encoded and separated by dots:
- **Header**: The header usually indicates the type of token, which is JWT, as well as the signing algorithm that is used.
- **Payload**: The body of the token, which contain the claims. A claim is a piece of information provided for a specific entity. In JWTs, there are registered claims, which are claim predefined by the JWT standard and public or private claim. The public and private claims are those which are defined by the developer.
- **Signature**: The signature is the part of the token that provides a method for verifying the token's authenticity. The signature is created by using the algorithm specified in the header of the JWT.
#### Signing Algorithms
There are several different algorithms in the JWT standard, we only really care about three main ones:
- **None**: This is a JWT without a signature, meaning that the verification of the claims provided in the JWT cannot be verified through the signature.
- **Symmetric Signing**: A symmetric signing algorithm, such as HS265, creates the signature by appending a secret value to the header and body of the JWT before generating a hash value. Verification of the signature can be performed by any system that has knowledge of the secret key.
- **Asymmetric Signing**: An asymmetric signing algorithm, such as RS256, creates the signature by using a private key to sign the header and body of the JWT. This is created by generating the hash and then encrypting the hash using the private key. Verification of the signature can be performed by any system that has knowledge of the public key associated with the private key that was used to create the signature.
#### Security in the Signature
JWTs can be encrypted (called JWEs), but the key power of JWTs comes from the signature. Once a JWT is signed, it can be sent to the client, who can use this JWT wherever needed. We can have a centralised authentication server that creates the JWTs used on several applications. Each application can then verify the signature of the JWT; if verified, the claims provided within the JWT can be trusted and acted upon.

## Sensitive Information Disclosure
A common cookie-based session management approach is using the server-side session to store several parameters. In PHP, for example, you can use $SESSION['var']=data to store a value associated with the user's session. These values are not exposed client-side and can therefore only be recovered server-side. However, with tokens, the claims are exposed as the entire JWT is sent client-side. If the same development practice is followed, sensitive information can be disclosed. Some examples are seen on real applications:

- Credential disclosure with the password hash, or even worse, the clear-text password being sent as a claim.
- Exposure of internal network information such as the private IP or hostname of the authentication server.

# Practical Examples
### 1. Sensitive Information on Claim
Simply decode the claim part of the token.
### 2. Not verifying the Signature
We can remove the signature part to test with the request can pass through, with it works, we can modify the claim directly to tamper with the application.
### 3. Downgrading to None
Sometimes JWTs support the None signing. We can modify the alg part of the JWT to None, and make the request.

### 4. Weak Symmetric Secrets
We can save the JWT and crack the secret, then use the secret to generate a signed tampered claim. Make use of [jwt.io](https://jwt.io).
### 5. Signature Algorithm Confusion
Similar to example 4, but if an asymmetric algorithm is being used, it may be possible to downgrade to a symmetric signing algorithm, using the public key as to sign the JWT.
### 6. Token Lifetime
When the exp time is too large or not set at all, makes so we can use old token to authenticate.

## Cross-Service Relay Attacks
JWTs are often used in systems with a centralised authentication system that serves multiple applications. However, in some cases, we may want to restrict which applications are accessed with a JWT, especially when there are claims that should only be valid for certain applications. This can be done by using the audience claim. However, if the audience claim isn't correctly enforced, a Cross-Service Relay attack can be executed to perform a privilege escalation attack.

**The Audience Claim**
JWTs can have an audience claim. In cases where a single authentication system serves multiple applications, the audience claim can indicate which application the JWT is intended for.