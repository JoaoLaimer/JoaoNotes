## 10.1 Configure initial Router Settings
### 10.1.1 Basic Router Configuration Steps
The following tasks should be completed when configuring initial settings on a router.

1. Configure the device name.
```
Router(config)# hostname hostname
```
2. Secure privileged EXEC mode.
```
Router(config)# enable secret password
```
3. Secure user EXEC mode.
```
  Router(config)# line console 0    
  Router(config-line)# password password    
  Router(config-line)# login
```
4. Secure remote Telnet / SSH access.
```
Router(config-line)# line vty 0 4    
Router(config-line)# password   password    
Router(config-line)# login    
Router(config-line)# transport input {    ssh   | telnet}
```
5. Secure all passwords in the config file.
```
  Router(config-line)# exit    
  Router(config)# service password-encryption
```
6. Provide legal notification.
```
Router(config)# banner motd delimiter message delimiter
```
7. Save the configuration.
```
  Router(config)# end    
  Router# copy running-config startup-config
```
## 10.2 Configure Interfaces
### 10.2.1 Configure Router Interfaces
The next step is to configure their interfaces. This is because routers are not reachable by end devices until the interfaces are configured
The task to configure a router interface is very similar to a management SVI on a switch. Specifically, it includes issuing the following commands:
```
  Router(config)# interface type-and-number    
  Router(config-if)# description description-text    
  Router(config-if)# ip address  ipv4-address subnet-mask    
  Router(config-if)# ipv6 address  ipv6-address/prefix-length    
  Router(config-if)# no shutdown
```
**Note:** When a router interface is enabled, information messages should be displayed confirming the enabled link.
Although the **description** command is not required to enable an interface, it is good practice to use it. It can be helpful in troubleshooting on production networks by providing information about the type of network connected. For example, if the interface connects to an ISP or service carrier, the **description** command would be helpful to enter the third-party connection and contact information.
**Note:** The _description-text_ is limited to 240 characters.

Using the **no shutdown** command activates the interface and is similar to powering on the interface. The interface must also be connected to another device, such as a switch or a router, for the physical layer to be active.

**Note:** On inter-router connections where there is no Ethernet switch, both interconnecting interfaces must be configured and enabled.

### 10.2.3 Verify Interface Configuration
There are several commands that can be used to verify interface configuration. The most useful of these is the **show ip interface brief** and **show ipv6 interface brief** commands.
### 10.2.4 Configuration Verification Commands
The table summarizes the more popular **show** commands used to verify interface configuration.

| Commands                                                   | Description                                                                                                                                                                                                                                               |
| ---------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `show ip interface brief`<br>`show ipv 6 interface brief ` | Displays all interfaces, their IP addresses, and their current status. The configured and connected interfaces should display a status of "up" and protocol of "up". Anything else would indicate a problem with either the configuration or the cabling. |
| `show ip route`<br>`show ipv6 route`                       | Displays the contents of the IP routing tables stored in RAM.                                                                                                                                                                                             |
| `show interfaces`                                          | Displays statistics for all interfaces on the device. However, this command will only display the IPv4 addressing information.                                                                                                                            |
| `show ip interface`                                        | Displays the IPv4 statistics for all interfaces on a router.                                                                                                                                                                                              |
| `show ipv6 interface`                                      | Displays the IPv6 statistics for all interfaces on a router.                                                                                                                                                                                              |

## 10.3 Configure the Default Gateway
### 10.3.1 Default Gateway on a Host
If your local network has only one router, it will be the gateway router and all hosts and switches on your network must be configured with this information. If your local network has multiple routers, you must select one of them to be the default gateway router.

The default gateway is only used when the host wants to send a packet to a device on another network. The default gateway address is generally the router interface address attached to the local network of the host.

### 10.3.2 Default Gateway on a Switch
A switch that interconnects client computers is typically a Layer 2 device. As such, a Layer 2 switch does not require an IP address to function properly. However, an IP configuration can be configured on a switch to give an administrator remote access to the switch.

To connect to and manage a switch over a local IP network, it must have a switch virtual interface (SVI) configured. The SVI is configured with an IPv4 address and subnet mask on the local LAN. The switch must also have a default gateway address configured to remotely manage the switch from another network.

To configure an IPv4 default gateway on a switch, use the **ip default-gateway** _ip-address_ global configuration command. The _ip-address_ that is configured is the IPv4 address of the local router interface connected to the switch. 