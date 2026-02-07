## Boot Integrity 
Verify the integrity of the operating system and boot loading systems.
## Boot Security
Newer systems use Unified Extensible Firmware Interface (UEFI) instead of Basic Input/Output System (BIOS). UEFI can boot from larger disks, and is CPU-independent.
## Trusted Platform Module (TPM) 
Dedicated microcontroller designed to secure hardware through integrated cryptographic key.
**Trusted Platform Module (TPM)**: is a hardware chip on the motherboard that stores cryptographic keys used for encryption. Comes with a burned-in key providing a hardware root of trust.

TPM provides full disk encryption. TPM supports secure boot attestation processes. When the system boots, the ensure boot process checks the files against the stored signatures to ensure they haven't changed.

**Remote Attestation**: Uses a separate system to check boot files.
## Hardware Security Module (HSM)
Physical device that safeguards and manages digital keys, primarily used for mission-critical situations like financial transactions.
Not only does an HSM securely generate cryptographic keys, but it also provides accelerated cryptographic operations.
> MicroSDs HSM exists.
>The difference between a HSM and a TPM is that a HSM is removable, and often portable.


## Key Management System
Integrated approach for generating, distributing and managing cryptographic keys for devices and application.
## Secure Enclave
Sometimes known as trusted execution environment (TEE).
Co-processor integrated into the main processor of some devices, designed with the sole purpose of ensuring data protection.
By keeping this data separate from the main processor, even if a device gets compromised, the data within the Secure Enclave remains untouched.

## Perfect Forward Secrecy (PFS)
Indicates that a cryptographic system generates random public keys to each session, and it doesn't use a deterministic algorithm to do so. The result is that the compromise of a key does not compromise any past key.
## Homomorphic Cryptographic
Allows for data operations on encrypted data. 