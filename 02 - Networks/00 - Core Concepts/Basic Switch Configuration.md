Before configuring a switch, review the following initial switch configuration tasks:
Configure the device name.
- **hostname** _name_
Secure user EXEC mode.
- **line console 0**
- **password** _password_
- **login**
Secure remote Telnet / SSH access.
- **line vty 0 15**
- **password** _password_
- **login**
Secure privileged EXEC mode.
- **enable secret** _password_
Secure all passwords in the config file.
- **service password-encryption**
Provide legal notification.
- **banner motd** _delimiter message delimiter_
Configure the management SVI.
- **interface vlan 1**
- **ip address** _ip-address subnet-mask_
- **no shutdown**
Save the configuration.
- **copy running-config startup-config**
```
Switch> enable
Switch# configure terminal
Switch(config)# hostname S1
S1(config)# enable secret class
S1(config)# line console 0
S1(config-line)# password cisco
S1(config-line)# login
S1(config-line)# line vty 0 15
S1(config-line)# password cisco
S1(config-line)# login
S1(config-line)# exit
S1(config)# service password-encryption
S1(config)# banner motd #No unauthorized access allowed!#
S1(config)# interface vlan1
S1(config-if)# ip address 192.168.1.20 255.255.255.0
S1(config-if)# no shutdown
S1(config-if)# end 
S1# copy running-config startup-config
Destination filename [startup-config]?
Building configuration... 
[OK]
S1#
```
