Does not require a shared secret key, often referred as public key cryptography since their key is considered to be 
freely and openly available to the public. 
- Confidentiality
- Integrity
- Authentication
- Non-repudiation
> Does not require the exchange of a key, but it is used to exchange a symmetric key.
### Digital Signature
A hash digest of a message encrypted with the sender's private key to let the recipient know the document was created and sent by the person claiming to have sent it.
## Diffie-Hellman (DH)
Used to conduct key exchanges and secure key distribution over an unsecure network.
- Used for the key exchange inside of ceating a VPN tunnel establishment as part of IPSec or to be able to do a key exchange over the internet.
## RSA (Rivest, Shamir, and Adleman)
Asymmetric algorithm that relies on the mathematical difficulty of factoring large prime numbers.
- Can support key sizes up to 1024-bits and 4096-bits.
## Elliptic Curve Cryptography (ECC)
Heavily used in mobile devices and it's based on the algebraic structure of elliptical curves over finite fields to define its key.
- ECC with a 256-bit key is just as secure as RSA with a 2048-bit key.
#### Elliptic Curve Diffie-Hellman (ECDH)
ECC version of the Diffie-Hellman key exchange protocol.
#### Elliptic Curve Diffie-Hellman Ephemeral
Uses a different key for each portion of the key establishment process inside the Diffie-Hellman key exchange.
#### Eliptic Curve Digital Signature Algorithm (ECDSA)
Used as public key encryption algorithm by the US Government in their digital signatures.
## Trapdoor Function
Is the concept of the easy encryption using a public key, but reversing the process (decryption) without the private key is challenging.
RSA's and ECC principle is that certain mathematical operations are easy to perform, but their inverse operations are difficult without specific knowledge.