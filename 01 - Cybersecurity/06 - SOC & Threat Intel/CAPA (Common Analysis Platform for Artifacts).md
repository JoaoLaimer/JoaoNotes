Developed by FireEye Mandiant.
Identify capabilities in PE, ELF, .NET, [[Shell]] 
Describe common behaviours.
determine what a program is capable of doing.

exec: capa.exe <program> <switch>
	-h or --help :  help
	-v or --verbose : verbose
	-vv or --vverbose: more verbose
	-j : output to json

The first block contains:
- The cryptographic algorithms, such as the `md5`, and `sha1/256`.
- The `static` field tells us how CAPA performed its analysis on the file.
- The `os` field reveals the operating system (OS) context for which the identified capabilities apply.
- The `arch` field allows us to determine whether we are dealing with a binary related to x86 architecture.
- The `path` where the analyzed file was located.

The second block includes MITRE ATT&CK framework information.
The third block includes MAEC(Malware Attribute Enumeration and Characterization) which is a specialized language design to encode and communicate information about malware.
The fourth block includes MBC(Malware Behavior Catalogue)
The fifth block includes Capabilities and Namespaces
	-Namespaces: Format
		Capability(Rule Name)::TLN(Top-Level Namespace)/Namespace
