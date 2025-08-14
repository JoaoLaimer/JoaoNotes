This attack takes advantage of how certain hash functions process data. Specifically, it works on hash functions like MD5, SHA-1, and SHA-256, which are built using something called the **Merkle-Damgård construction**. These hash functions let an attacker take an existing hash and add extra data onto the message that the hash represents without even needing to know the original message or the secret key used to create it. This works because these hash functions process data in chunks or blocks, with each block's hash influencing the next blocks's processing. 

For a length extension attack to be possible, the attacker needs a few things: they must have the **hash** of the original message, they need to know the **length** of the original message (or be able to guess it), and they need to **understand how the padding rules work** for that specific hash function.

This attack works because of how the internal state of the hash function is carried over between data blocks. After processing the original message, the hash function leaves off in a specific internal state (represented by the hash). The attacker can take that state, add more data, and keep going. The function doesn't "finalize" the process after the original message, so it can be tricked into continuing the hashing with the new data.

## Vulnerable Hash Functions

Many commonly used hash functions are vulnerable to length extension attacks, especially those based on the Merkle-Damgård construction:

- **MD5**: Once popular but now considered weak due to vulnerabilities like length extension attacks. MD5 processes data in 512-bit blocks, making it an easy target for these attacks.
    
- **SHA-1**: Like MD5, SHA-1 uses block-by-block processing and suffers from similar weaknesses. It has been phased out of most security-critical systems because of these vulnerabilities.
    
- **SHA-256**: While stronger than MD5 and SHA-1, SHA-256 can still be exploited in a length extension attack if used without additional protections like HMAC (a key-based hashing method).
