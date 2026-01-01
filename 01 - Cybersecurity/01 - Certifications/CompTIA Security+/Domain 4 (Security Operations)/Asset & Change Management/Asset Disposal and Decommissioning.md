Special Publication 800-88 commonly referred as the "Guidelines for Media Sanitization"
## Sanitization
The thorough process of making data inaccessible and irretrievable from a storage medium using traditional forensic methods
### Overwriting data 
Replacing the existing data on a storage device with random bits of information to ensure that the original data is obscured 
- Single pass
- 7 passes
- 35 passes
Each overwrite makes it increasingly difficult for potential adversaries to retrieve any meaningful data using forensic tools
### Degaussing
Involves using a machine called a degausser to produce a strong magnetic field that can disrupt the magnetic domains on storage devices like hard drives or tapes.
After degaussing, a device loses its data storage capability.
### Secure Erase
Completely deletes data from a storage device while ensuring that it can't be recovered using traditional recovery tools.
Cryptographic Erase (CE) was introduced to replace the Secure Erase technique in most modern storage devices.
One significant advantage of cryptographic erase over traditional erasure methods is speed.
## Destruction
Ensures the physical device itself is beyond recovery or reuse
- Shredding 
- Pulverizing
- Melting
- Incinerating
## Certification
An act of proof that the data or hardware has been security disposed of.
Organization should prioritize data security by documenting the sanitization, disposal, or destruction of data.

Data retention is focused on strategically deciding that to keep and for how long.

Regulations may require specific data, such as financial transactions or medical records, to be retained for a set duration.
