One-way cryptographic function that takes an input and produces a unique message digest as its output.
The hash digest is always the same length regardless of how long the input is.
## MD5
Creates a 128-bit hash value that is unique to the input file.
## Secure Hash Algorithm
### SHA-1
Creates a 160-bit hash digest, which significantly reduces the number of collisions that occur.
### SHA-2
Family of hash function that contain longer hash digests.
- SHA-224
- SHA-256
- SHA-384
- SHA-512
Each  version pf SHA performs a different number of rounds of mathematical computations to create the hash digest.
### SHA-3 
Newer family of hash function, and its hash digest can go between 224-bits and 512-bits. It uses 120 rounds of computations.
## RIPEMD(RACE Integrity Primitive Evaluation Message Digest)
Comes in 160, 256 and 320 bit versions. Open-source.
## HMAC(Hash-based Message Authentication Code)
Used to check the integrity of a message and provides some level of assurance that its authenticity is real.
## Digital Signature
Created by hashing a file then taking that resulting hash digest and encrypting it with a private key.
## Digital Security Standard (DSS)
Relies upon a 160-bit message digest created by a Digital Security Algorithm.

