The Cisco IOS (Internetwork Operating System) command line interface (CLI) is a text-based program that enables entering and executing Cisco IOS commands to configure, monitor, and maintain Cisco devices. The Cisco CLI can be used with either in-band or out-of-band management tasks.

## Primary Command Modes
As a security feature, the Cisco IOS software separates management access into the following two command modes:

- **User EXEC Mode** - This mode has limited capabilities but is useful for basic operations. It allows only a limited number of basic monitoring commands but does not allow the execution of any commands that might change the configuration of the device. The user EXEC mode is identified by the CLI prompt that ends with the > symbol.
- **Privileged EXEC Mode** - To execute configuration commands, a network administrator must access privileged EXEC mode. Higher configuration modes, like global configuration mode, can only be reached from privileged EXEC mode. The privileged EXEC mode can be identified by the prompt ending with the # symbol.

| Command Mode         | Description                                                                                                                                        | Default Device Prompt |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| User EXEC Mode       | - Mode allows access to only a limited number of basic monitoring commands.<br>- It is often referred to as "view-only" mode.                      | Switch><br>Router>    |
| Privileged EXEC Mode | - Mode allows access to all commands and features.<br>- The user can use any monitoring commands an execute configuration and management commands. | Switch#<br>Router#    |
## Commands

| Command              | Description                                                                                       |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| enable               | Enter Privileged EXEC Mode.                                                                       |
| disable              | Go back to User EXEC Mode.                                                                        |
| configure terminal   | Go to global configuration mode. Makes the default device prompt appear as Switch/Router#(config) |
| exit                 | Go back from global configuration mode to privileged EXEC mode.                                   |
| line </device/>      | Management interface of specified port. (config-line)                                             |
| interface </device/> | Interface configuration mode. (config-if)                                                         |
| end or CTRL+Z        | Returns from configuration mode to privileged EXEC mode.                                          |

## Basic IOS Command Structure

| Prompt  | Command | Space | Keyword(s) or Argument(s) |
| ------- | ------- | ----- | ------------------------- |
| Switch> | show    |       | ip protocols              |
| Switch> | ping    |       | 192.168.10.5              |
- **Keyword** - This is a specific parameter defined in the operating system (in the table, **ip protocols**).
- **Argument** - This is not predefined; it is a value or variable defined by the user (in the table, **192.168.10.5**).
## IOS Command Syntax

| Convention   | Description                                                                                                                                                        |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **boldface** | Boldface text indicates commands and keywords that you enter literally as shown.                                                                                   |
| _italics_    | Italic text indicates arguments for which you supply values.                                                                                                       |
| [x]          | Square brackets indicate an optional element (keyword or argument).                                                                                                |
| {x}          | Braces indicate a required element (keyword or argument).                                                                                                          |
| [x { y\| z}] | Braces and vertical lines within square brackets indicate a required choice within an optional element. Spaces are used to clearly delineate parts of the command. |
Using the '?' on the command prompt you can see a list of commands available on the current mode, finish a command (Example: `int?` for interface and available commands that start with int). And finally, for completing commands after the start of commands.
## Hotkeys and Shortcuts

| Keystroke                  | Description                                                                                                                                            |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Tab                        | Completes a partial command name entry.                                                                                                                |
| Backspace                  | Erases the character to the left of the cursor.                                                                                                        |
| Ctrl+D                     | Erases the character at the cursor.                                                                                                                    |
| Ctrl+K                     | Erases all characters from the cursor to the end of the command line.                                                                                  |
| Esc D                      | Erases all characters from the cursor to the end of the word.                                                                                          |
| Ctrl+U or Ctrl+X           | Erases all characters from the cursor to the beginning of the command line.                                                                            |
| Ctrl+W                     | Erases the word to the left of the cursor.                                                                                                             |
| Ctrl+A                     | Moves the cursor to the beginning of the line.                                                                                                         |
| Left Arrow or Ctrl+B       | Moves the cursor one character to the left.                                                                                                            |
| Esc B                      | Moves the cursor back one word to the left.                                                                                                            |
| Esc F                      | Moves the cursor forward one word to the right.                                                                                                        |
| Right Arrow or Ctrl+F      | Moves the cursor one character to the right.                                                                                                           |
| Ctrl+E                     | Moves the cursor to the end of command line.                                                                                                           |
| Up Arrow or Ctrl+P         | Recalls the previous command in the history buffer, beginning with the most recent command.                                                            |
| Down Arrow or Ctrl+N       | Goes to the next line in the history buffer.                                                                                                           |
| Ctrl+R or Ctrl+I or Ctrl+L | Redisplays the system prompt and command line after a console message is received.                                                                     |
| Enter                      | Display the next line.                                                                                                                                 |
| Space                      | Displays the next screen.                                                                                                                              |
| Any other key*             | Ends the display string, returning to previous prompt. *Except "y", which answers "yes" to the --More-- prompt, and acts like the Space*.              |
| Ctrl+C                     | When in any configuration mode, end the configuration mode and returns to privileged EXEC mode. When in setup mode, aborts back to the command prompt. |
| Ctrl+Z                     | When in any configuration mode, ends the configuration mode and returns to privileged EXEC mode.                                                       |
| Ctrl+Shift+6               | All-purpose break sequence used to abort DNS lookups, traceroutes, pings, and to interrupt an IOS process.                                             |
## Show Commands
Used for displaying relevant information about the configuration and operation of device.

| Command               | Used To                                                              |
| --------------------- | -------------------------------------------------------------------- |
| `show running-config` | Verify the current configuration and settings.                       |
| `show interfaces`     | Verify the interface status and see if there are any error messages. |
| `show ip interface`   | Verify layer 3 information of an interface.                          |
| `show arp`            | Verify the list of known hosts on the local Ethernet LANs.           |
| `show ip route`       | Verify layer 3 routing information.                                  |
| `show protocols`      | Verify which protocols are operational.                              |
| `show version`        | Verify the memory, interfaces, and licenses of the device.           |
