## Characteristics of Strong Keys:

1. **Length**: Longer keys significantly increase the computational effort required to brute-force them.
2. **Entropy**: Keys must be truly random, not derived from predictable inputs like timestamps or user data.
3. **Uniqueness**: Keys must be unique across different encryptions or systems to prevent correlation attacks.
## Math of RSA
RSA encryption, named after its inventors Rivest, Shamir, and Adleman, is based on the difficulty of factoring large numbers.  
A public key consists of:
- n=p×q: The product of two large prime numbers, (p) and (q).
- e: A small public exponent (commonly (e = 65537)).
The private key is derived from:

- ϕ(n)=(p−1)×(q−1), where ϕ is Euler's totient function.
- (d): The modular inverse of 𝑒 e modulo 𝜙 ( 𝑛 ) ϕ(n), satisfying 𝑒 × 𝑑 ≡ 1 ( mod 𝜙 ( 𝑛 ) ) e×d≡1 (mod ϕ(n)).

The security of RSA depends on the difficulty of factoring (n) into its prime components (p) and (q). However, if (p) or (q) is poorly generated or shared across keys, this foundational assumption breaks down.
## What is "P's and Q's"?
The [paper](https://www.cl.cam.ac.uk/archive/rja14/Papers/psandqs.pdf) "P's and Q's" by Ross Anderson and Serge Vaudenay explores how poor randomness in RSA key generation can lead to severe vulnerabilities. It outlines key weaknesses that attackers can exploit:
**Predictable Primes**:  
If (p) or (q) are generated using a weak random number generator (e.g., seeded with system time), an attacker can recreate the key generation process and derive the primes.
**Shared Primes Across Keys**:  
When multiple RSA keys share a common prime (p), the attacker can use the greatest common divisor (GCD) method to factor n1​=p×q1​ and n2​=p×q2​, breaking both keys.
**Small Differences Between Primes**:  
If (p) and (q) are too close in value, efficient algorithms such as [Fermat's factorisation](https://en.wikipedia.org/wiki/Fermat%27s_factorization_method) method can quickly factor (n).
**Mathematical Exploits Using GCD**:  
The GCD of two public keys that share a prime can be computed in polynomial time:
GCD(n1​,n2​)=p
These vulnerabilities highlight the critical importance of randomness and diversity in prime generation for RSA security.

## Breaking Hashes
Hashing is a cryptographic process that transforms an input (e.g., a password or a message) into a fixed-size string, often called a hash. The transformation is one-way, meaning it’s not feasible to reverse the hash to recover the original input. Hashing is used for:

1. **Password Storage:** Instead of storing plaintext passwords, systems store their hashes. During login, the input password is hashed and compared to the stored hash.
2. **Data Integrity:** Hashes verify that data has not been altered during transmission.
3. **Message Authentication (HMAC):** Hashes combined with a secret key verify that a message hasn’t been tampered with.
#### Common Vulnerabilities in Hashing
**Weak Hash Algorithms**  
Older algorithms like MD5 and SHA-1 are considered insecure due to their susceptibility to collisions (two inputs producing the same hash).
**Lack of Salting**  
When the same input consistently produces the same hash, attackers can use precomputed databases (rainbow tables) to reverse the hash to its original value.
**Insecure HMACs**  
Hash-based Message Authentication Codes (HMACs) rely on a hash function combined with a secret key to ensure message authenticity. Weaknesses arise when:
- The hash function is insecure.
- The key is short, predictable, or reused.

## Exposed Keys
**Key risks include:**
1. **Unauthorised Access:** Exposed keys can be used to decrypt sensitive data or interact with backend APIs as an authenticated user.
2. **Data Tampering:** An attacker can use the keys to generate signed payloads or modify encrypted messages, bypassing integrity checks.
3. **API Abuse:** Hardcoded API keys may allow attackers to access privileged API endpoints without authorization.
#### Common Scenarios of Key Exposure
1. **Hardcoded API Keys in JavaScript**  
    Developers often embed API keys in front-end code for convenience, forgetting that anyone can view this code using browser developer tools.
2. **Encryption Keys in Client-Side Frameworks**  
    Encryption keys are sometimes included in front-end libraries or scripts to encrypt/decrypt data locally. These keys can be easily extracted and used maliciously.
3. **Unsecured Configuration Files**  
    Configuration files embedded in web applications may contain sensitive credentials or keys in plain text.
## Unauthenticated Encryption
Unauthenticated encryption refers to encryption that does not include a mechanism to verify the integrity or authenticity of the ciphertext. This means that an attacker can modify encrypted data that is in transit, and the system will still accept and process it without detecting any tampering.

## Bit Flipping Attacks
Bit flipping attacks target systems that use unauthenticated encryption, allowing an attacker to modify ciphertext so that the decrypted plaintext is manipulated in predictable ways. This type of attack is particularly dangerous when systems assume that encrypted data is inherently safe to trust without verifying its integrity.

Encryption schemes like AES-CBC (Cipher Block Chaining) are vulnerable to bit flipping when no integrity check, such as a Message Authentication Code (MAC), is applied. In CBC mode:

1. The plaintext is XORed with the previous ciphertext block before encryption.
2. If an attacker alters bits in a ciphertext block, it changes the corresponding plaintext block during decryption.