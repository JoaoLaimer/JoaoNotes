Netcat is the most basic tool in a pentester's toolkit when it comes to any kind of networking.
**Reverse Shells**
The syntax for starting a netcat listener using Linux is this:
`nc -lvnp <port>`
Where:
- **-l** is used to tell netcat that this will be a listenet
- **-v** is used to request a verbose output
- **-n** tells netcat not to resolve host names or use DNS. 
- **-p** indicates that the post specification will follow.

**Bind Shells**
The syntax to connect to a listener is as follows:
`nc <target-ip> <chosen-port>`

### Netcat [[Shell]] Stabilization
Simple netcat shells are often unstable, Ctrl+C kills the whole thing, they are non-interactive and often have strange formatting erros. This is due to netcat "shells" really being processes running inside a terminal, rather than being bonafide terminals in their own right.

**Technique 1: Python**
Make sure to have python installed.
1. `python -c 'import pty; pty.spawn("/bin/bash")'`
2. `export TERM=xterm`. This will give us access to term commands such as clear.
3. Finally we will background the shell using Ctrl+Z. Back in our own terminal we use `stty raw -echo; fg`. This turn off our own terminal echo (which gives us access to tab autocompletes, the arrow keys, and Ctrl+C to kill processes), then foregrounds the shell, thus completing the process. 
Note that if the shell dies, any input in your own terminal will not be visible (as a result of having disabled terminal echo). To fix this, type `reset` and press enter.

**Technique 2: rlwrap**
This program gives us access to history, tab autocompletion and arrow keys immediately upon receiving a shell. Make sure to check if `rlwrap` is installed. To use rlwrap:
`rlwrap nc -lvnp <port>`

It's possible to completely stabilize, by using: `stty raw -echo; fg`.

**Technique 3: Socat**
This technique is limited to Linux targets, as a Socat shell on Windows will be no more stable than a netcat shell. To ccomplish this method of stabilisation we would first transfer a [socat static compiled binary](https://github.com/andrew-d/static-binaries/blob/master/binaries/linux/x86_64/socat?raw=true).

### Changing terminal tty size
With any of the above techniques, it's useful to be able to change your terminal tty size. This is something that your terminal will do automatically when using a regular shell; however, it must be done manually in a reverse or bind shell if you want to use something like a text editor which overwrites everything on the screen.

First, open another terminal and run `stty -a`. This will give you a large stream of output. Note down the values for "rows" and columns. Next, in your reverse/bind shell, type in:
`stty rows <number>`  

and
`stty cols <number>`  

Filling in the numbers you got from running the command in your own terminal. This will change the registered width and height of the terminal, thus allowing programs such as text editors which rely on such information being accurate to correctly open.
