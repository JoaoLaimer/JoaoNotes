This attack takes advantage of how certain hash functions process data. Specifically, it works on hash functions like MD5, SHA-1, and SHA-256, which are built using something called the **Merkle-Damgård construction**. These hash functions let an attacker take an existing hash and add extra data onto the message that the hash represents without even needing to know the original message or the secret key used to create it. This works because these hash functions process data in chunks or blocks, with each block's hash influencing the next blocks's processing. 

For a length extension attack to be possible, the attacker needs a few things: they must have the **hash** of the original message, they need to know the **length** of the original message (or be able to guess it), and they need to **understand how the padding rules work** for that specific hash function.

This attack works because of how the internal state of the hash function is carried over between data blocks. After processing the original message, the hash function leaves off in a specific internal state (represented by the hash). The attacker can take that state, add more data, and keep going. The function doesn't "finalize" the process after the original message, so it can be tricked into continuing the hashing with the new data.

## Vulnerable Hash Functions

Many commonly used hash functions are vulnerable to length extension attacks, especially those based on the Merkle-Damgård construction:

- **MD5**: Once popular but now considered weak due to vulnerabilities like length extension attacks. MD5 processes data in 512-bit blocks, making it an easy target for these attacks.
    
- **SHA-1**: Like MD5, SHA-1 uses block-by-block processing and suffers from similar weaknesses. It has been phased out of most security-critical systems because of these vulnerabilities.
    
- **SHA-256**: While stronger than MD5 and SHA-1, SHA-256 can still be exploited in a length extension attack if used without additional protections like HMAC (a key-based hashing method).

#### How it works
Merkle–Damgård hashes process messages in fixed-size blocks and carry over an **internal state** (the hash so far).
When you get the hash of `secret || message`, you’re effectively seeing that internal state **after processing the first part of the input**.
If you can **resume** hashing from that state, you can append extra data exactly as if you knew the secret, because the compression function doesn’t “rewind” to check the original input.
Let’s say a vulnerable API works like this:
`MAC = MD5(secret || message)`

You know `message` and `MAC`, but not `secret`.
You want to forge a valid MAC for:
`message || padding || extra_data`
Where `padding` is the exact padding MD5 would have added internally.

**Attack process:**

1. **Guess the secret length** — try common lengths (8, 12, 16 bytes, etc.).
2. **Recreate the padding** — same as the hash algorithm does before finalization (e.g., a `0x80` byte, then zeros, then the length in bits at the end).
3. **Resume the hash** — treat the known hash as the new “IV” (initial state) and feed in your `extra_data`.
4. **Get the forged hash** — now you have a valid `MAC` for the extended message.