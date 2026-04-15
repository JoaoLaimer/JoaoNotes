The Cisco IOS (Internetwork Operating System) command line interface (CLI) is a text-based program that enables entering and executing Cisco IOS commands to configure, monitor, and maintain Cisco devices. The Cisco CLI can be used with either in-band or out-of-band management tasks.

# Primary Command Modes
As a security feature, the Cisco IOS software separates management access into the following two command modes:

- **User EXEC Mode** - This mode has limited capabilities but is useful for basic operations. It allows only a limited number of basic monitoring commands but does not allow the execution of any commands that might change the configuration of the device. The user EXEC mode is identified by the CLI prompt that ends with the > symbol.
- **Privileged EXEC Mode** - To execute configuration commands, a network administrator must access privileged EXEC mode. Higher configuration modes, like global configuration mode, can only be reached from privileged EXEC mode. The privileged EXEC mode can be identified by the prompt ending with the # symbol.

| Command Mode         | Description                                                                                                                                        | Default Device Prompt |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| User EXEC Mode       | - Mode allows access to only a limited number of basic monitoring commands.<br>- It is often referred to as "view-only" mode.                      | Switch><br>Router>    |
| Privileged EXEC Mode | - Mode allows access to all commands and features.<br>- The user can use any monitoring commands an execute configuration and management commands. | Switch#<br>Router#    |
# Commands

| Command              | Description                                                                                       |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| enable               | Enter Privileged EXEC Mode.                                                                       |
| disable              | Go back to User EXEC Mode.                                                                        |
| configure terminal   | Go to global configuration mode. Makes the default device prompt appear as Switch/Router#(config) |
| exit                 | Go back from global configuration mode to privileged EXEC mode.                                   |
| line </device/>      | Management interface of specified port. (config-line)                                             |
| interface </device/> | Interface configuration mode. (config-if)                                                         |
| end or CTRL+Z        | Returns from configuration mode to privileged EXEC mode.                                          |

# Basic IOS Command Structure

| Prompt  | Command | Space | Keyword(s) or Argument(s) |
| ------- | ------- | ----- | ------------------------- |
| Switch> | show    |       | ip protocols              |
| Switch> | ping    |       | 192.168.10.5              |
- **Keyword** - This is a specific parameter defined in the operating system (in the table, **ip protocols**).
- **Argument** - This is not predefined; it is a value or variable defined by the user (in the table, **192.168.10.5**).
# IOS Command Syntax

| Convention   | Description                                                                                                                                                        |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **boldface** | Boldface text indicates commands and keywords that you enter literally as shown.                                                                                   |
| _italics_    | Italic text indicates arguments for which you supply values.                                                                                                       |
| [x]          | Square brackets indicate an optional element (keyword or argument).                                                                                                |
| {x}          | Braces indicate a required element (keyword or argument).                                                                                                          |
| [x { y\| z}] | Braces and vertical lines within square brackets indicate a required choice within an optional element. Spaces are used to clearly delineate parts of the command. |
Using the '?' on the command prompt you can see a list of commands available on the current mode, finish a command (Example: `int?` for interface and available commands that start with int). And finally, for completing commands after the start of commands.
# Hotkeys and Shortcuts

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
# Show Commands
Used for displaying relevant information about the configuration and operation of device.

| Command                                          | Used To                                                                                                                                          |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| `show running-config`                            | Verify the current configuration and settings.                                                                                                   |
| `show interfaces`                                | Verify the interface status and see if there are any error messages.                                                                             |
| `show ip interface`                              | Verify layer 3 information of an interface.                                                                                                      |
| `show arp`                                       | Verify the list of known hosts on the local Ethernet LANs.                                                                                       |
| `show ip route`                                  | Verify layer 3 routing information.                                                                                                              |
| `show protocols`                                 | Verify which protocols are operational.                                                                                                          |
| `show version`                                   | Verify the memory, interfaces, and licenses of the device.                                                                                       |
| `show history`                                   | Display recently used commands                                                                                                                   |
| `show interface {interface} switchport`          | Verify trunk configuration                                                                                                                       |
| `show interfaces trunk`                          | Verify trunk configuration                                                                                                                       |
| `show vlan [brief]`                              | Verify configured VLANs.                                                                                                                         |
| `show interfaces switchport`                     | Verify switchport configuration.                                                                                                                 |
| `show interfaces port-channel {channel-number}`  | Verify the general status of the port channel interface.                                                                                         |
| `show etherchannel summary`                      | Verify several port channel interfaces.                                                                                                          |
| `show etherchannel port-channel`                 | Display information about a specific port channel interface.                                                                                     |
| `show interfaces etherchannel`                   | On any physical interface member of an EtherChannel bundle, the command provide information about the role of the interface in the EtherChannel. |
| `show ip dhcp binding`                           | Display a list of all IPv4 address to MAC address bindings provided by the DHCPv4 service.                                                       |
| `show ip dhcp server statistics`                 | Display count information regarding the number of DHCPv4 messages that have been sent and received.                                              |
| `show run interface {interface}`                 | Display running-config of a single interface.                                                                                                    |
| `show port-security address`                     | Display all secure MAC addresses that are manually configured or dynamically learned on all switch interfaces.                                   |
| `show controllers ethernet-controller fa0/1 phy` | To examine the auto-MDIX setting for a specific interface.                                                                                       |
| `show flash`                                     | Display information about flash file system.                                                                                                     |
| `show mac address-table`                         | Show MAC address table.                                                                                                                          |
| `show ip ssh`                                    | Display SSH information.                                                                                                                         |
# Filter Outputs
**terminal history size** user EXEC command to increase or decrease the size of the buffer.

There are four filtering parameters that can be used after the pipe.
**section**
	Shows the entire section that starts with the filtering expression.
**include**
	Includes all output lines that match the filtering expression
**exclude**
	Excludes all output lines that match the filtering expression.
**begin**
	Shows all the output lines from a certain point, starting with the line that matches the filtering expression.

```
R1# show run | include something
```

# Boot System Command
```
S1(config)# boot system flash:/c2960-lanbasek9-mz.150-2.SE/c2960-lanbasek9-mz.150-2.SE.bin
```

# Switch Configuration
## Duplex and Interface Speed
```
S1# configure terminal
S1(config)# interface FastEthernet 0/1
S1(config-if)# duplex full
S1(config-if)# speed 100
```
## Auto-MDIX
```
S1(config-if)# mdix auto
```

## Switch Virtual Interface Configuration (SVI)
```
S1# configure terminal
S1(config)# interface vlan 99
S1(config-if)# ip address 172.17.99.11 255.255.255.00
S1(config-if)# ipv6 address 2011:db8:acad:99::11/64
S1(config-if)# no shutdown
S1(config-if)# end
S1# copy running-config startup-config
S1# configure terminal
S1(config)# ip default-gateway 172.17.99.1
S1(config)# end
S1# copy running-config startup-config
```


# Router Configuration
## Router Interface Configuration
```
R1(config)# interface gigabitethernet 0/0/0
R1(config-if)# ip address 192.168.10.1 255.255.255.0 
R1(config-if)# ipv6 address 2001:db8:acad:1::1/64 
R1(config-if)# description Link to LAN 1
R1(config-if)# no shutdown
R1(config-if)# exit
```
## IPv4 Loopback Interfaces
```
Router(config)# interface loopback <number>
Router(config-if)# ip address <ip> <subnet>
```
# Configure SSH
```
S1# show ip ssh
S1# conf t
S1(config)# ip domain-name <name>
S1(config)# crypto key generate rsa
S1(config)# username admin secret ccna
S1(config)# line vty 0 15
S1(config-line)# transport input ssh
S1(config-line)# login local
S1(config-line)# exit
S1(config)# ip ssh version 2
```

hostname

# VLAN Configuration
### VLAN Creation
```
Switch# configure terminal
Switch(config)# vlan <vlan-id>
Switch(config-vlan)# name <vlan-name>
```
### VLAN Port Assignment
```
Switch# configure terminal
Switch(config)# interface <interface-id>
Switch(config-if)# switchport mode access
Switch(config-if)# switchmode access vlan <vlan-id>
```
### Data and Voice VLAN
```
S3(config)# vlan 20
S3(config-vlan)# name student
S3(config-vlan)# vlan 150
S3(config-vlan)# name VOICE
S3(config-vlan)# exit
S3(config)# interface fa0/18
S3(config-if)# switchport mode access
S3(config-if)# switchport access vlan 20
S3(config-if)# mls qos trust cos
S3(config-if)# switchport voice vlan 150
S3(config-if)# end
S3#
``` 
### Trunk Creation and Configuration
```
Switch# configure terminal
Switch(config)# interface <interface-id>
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk native vlan <vlan-id>
Switch(config-if)# switchport trunk allowed vlan <vlan-list>
```
### Reset the Trunk to Default
```
S1(config)# interface fa0/1
S1(config-if)# no switchport trunk allowed vlan
S1(config-if)# no switchport trunk native vlan
S1(config-if)# end
```
### Dynamic Trunking (DTP)
```
S1(config-if)# switchport mode  access | dynamic { auto | desirable } | trunk }
```
### Subinterface Configuration
```
S1(config)# interface {interface_id.subinterface_id}
S1(config-if)# encapsulation dot1q {vlan_id} [native]
S1(config-if)# ip address {ip-address}{subnet mask}
```
### Inter-VLAN Routing using L3 Switches
```
D1(config)# vlan 10
D1(config-vlan)# name LAN10
D1(config-vlan)# exit
D1(config)# interface vlan 10
D1(config-if)# description Default Gateway SVI for 192.168.10.0/24
D1(config-if)# ip add 192.168.10.1 255.255.255.0
D1(config-if)# no shut
D1(config-if)# exit
D1(config)#
D1(config)# interface GigabitEthernet1/0/6
D1(config-if)# description Access port to PC1
D1(config-if)# switchport mode access
D1(config-if)# switchport access vlan 10
D1(config-if)# exit
D1(config)# ip routing
```
### Routing Configuration on a Layer 3 Switch
```
D1(config)# interface GigabitEthernet0/0/1
D1(config-if)# description routed Port Link to R1
D1(config-if)# no switchport
D1(config-if)# ip address 10.10.10.2 255.255.255.0
D1(config-if)# no shut
D1(config-if)# exit
D1(config)#
D1(config)# ip routing
D1(config)#
D1(config)# router ospf 10
D1(config-router)# network 192.168.10.0 0.0.0.255 area 0
D1(config-router)# network 192.168.20.0 0.0.0.255 area 0
D1(config-router)# network 10.10.10.0 0.0.0.3 area 0
D1(config-router)# ^Z
D1#
*Sep 17 13:52:51.163: %OSPF-5-ADJCHG: Process 10, Nbr 10.20.20.1 on GigabitEthernet0/0/1 from LOADING to FULL, Loading Done
D1#
```
# Etherchannel
## Modes
**PAgP Modes**

| S1        | S2             | Channel Establishment |
| --------- | -------------- | --------------------- |
| On        | On             | Yes                   |
| On        | Desirable/Auto | No                    |
| Desirable | Desirable      | Yes                   |
| Desirable | Auto           | Yes                   |
| Auto      | Desirable      | Yes                   |
| Auto      | Auto           | No                    |
**LACP Modes**

| S1      | S2             | Channel Establishment |
| ------- | -------------- | --------------------- |
| On      | On             | Yes                   |
| On      | Active/Passive | No                    |
| Active  | Active         | Yes                   |
| Active  | Passive        | Yes                   |
| Passive | Active         | Yes                   |
| Passive | Passive        | No                    |
## LACP
```
S1(config)# interface range FastEthernet 0/1 - 2
S1(config-if-range)# shutdown
S1(config-if-range)# channel-group 1 mode active
Creating a port-channel interface Port-channel 1
S1(config-if-range)# no shutdown
S1(config-if-range)# exit
S1(config)# interface port-channel 1
S1(config-if)# switchport mode trunk
S1(config-if)# switchport trunk allowed vlan 1,2,20
``` 

# DHCPv4
## Server
```
Router(config)# ip dhcp excluded-address <low-address> [high-address]
Router(config)# ip dhcp pool pool-name
Router(dhcp-config)#
```
**Define the address pool**
	`network <network-number> [mask | /prefix-length]`
	**Define the default gateway**
	`default-router <address> [address2...address8]`
	**Define a DNS server**
	`dns-server address [address2...address8]`
	**Define the domain name**
	`domain-name <domain>`
	**Define the duration of the DHCP lease**
	`lease {days [hours [minutes]] | infinite}`
	**Define the NetBIOS WINS server**
	`netbios-name-server address [address2...address8]`
## Client
```
SOHO(config)# interface G0/0/1
SOHO(config-if)# ip address dhcp
SOHO(config-if)# no shutdown
Sep 12 10:01:25.773: %DHCP-6-ADDRESS_ASSIGN: Interface GigabitEthernet0/0/1 assigned DHCP address 209.165.201.12, mask 255.255.255.224, hostname SOHO
```
## DHCPv4 Relay
```
R1(config)# ip helper-address {address} {interface}
```

# SLAAC

### Client
```
R1(config)# ipv6 unicast-routing
R1(config)# exit
R1# show ipv6 interface G0/0/1 | section Joined
  Joined group address(es):
    FF02::1
    FF02::2
    FF02::1:FF00:1
R1#
``` 
# DHCPv6 Stateless
### Server
```
R1(config)# ipv6 unicast-routing
R1(config)#
R1(config)# ipv6 dhcp pool IPV6-STATELESS
R1(config-dhcpv6)#
R1(config-dhcpv6)# dns-server 2001:db8:acad:1::254
R1(config-dhcpv6)# domain-name example.com
R1(config-dhcpv6)# exit
R1(config)#
R1(config)# interface G0/0/1
R1(config-if)# description Link to LAN
R1(config-if)# ipv6 address fe80::1 link-local
R1(config-if)# ipv6 address 2001:db8:acad:1::1/64
R1(config-if)# ipv6 nd other-config-flag
R1(config-if)# ipv6 dhcp server IPV6-STATELESS
R1(config-if)# no shutdown
R1(config-if)# end
R1#
```
### Client
```
R1(config)# ipv6 unicast-routing
R1(config)# int g0/0/0/1
R1(config-if)# ipv6 enable
R1(config-if)#
R1(config-if)# ipv6 address autoconfig
```
# DHCPv6 Stateful
### Server
```
R1(config)# ipv6 unicast-routing
R1(config)#
R1(config)# ipv6 dhcp pool IPV6-STATEFUL
R1(config-dhcpv6)#
R1(config-dhcpv6)# address prefix 2001:db8:acad:1::/64
R1(config-dhcpv6)# dns-server 2001:4860:4860::8888
R1(config-dhcpv6)# domain-name example.com
R1(config-dhcpv6)#
R1(config)# int g0/0/1
R1(config-if)# description Link to LAN
R1(config-if)# ipv6 address fe80::1 link-local
R1(config-if)# ipv6 address 2001:db8:acad:1::1/64
R1(config-if)# ipv6 nd managed-config-flag
R1(config-if)# ipv6 nd prefix default no-autoconfig
R1(config-if)# ipv6 dhcp server IPV6-STATEFUL
R1(config-if)# no shutdown
```
### Enable Stateful DHCPv6 on an Interface
```
R1(config)# int g0/0/1
R1(config-if)# ipv6 nd managed-config-flag
R1(config-if)# ipv6 nd prefix default no-autoconfig
R1(config-if)# end
R1#
``` 
### Client
```
R1(config)# ipv6 unicast-routing
R1(config)# interface g0/0/1
R1(config-if)# ipv6 enable
R1(config-if)# ipv6 address dhcp
```
# DHCPv6 Relay
### Agent
```
Router(config-if)# ipv6 dhcp relay destination <ipv6-address> [interface-type interface-number]
```

