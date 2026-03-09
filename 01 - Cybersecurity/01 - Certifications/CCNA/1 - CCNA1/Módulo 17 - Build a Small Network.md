## 17.1 Devices in a Small Network
### 17.1.1 Small Network Topologies

The majority of businesses are small; therefore, it is not surprising that the majority of business networks are also small.

A small network design is usually simple. The number and type of devices included are significantly reduced compared to that of a larger network.

### 17.1.2 Device Selection for a Small Network
**Cost**
The cost of a switch or router is determined by its capacity and features. This includes the number and types of ports available and the backplane speed. Other factors that influence the cost are network management capabilities, embedded security technologies, and optional advanced switching technologies. The expense of cable runs required to connect every device on the network must also be considered. Another key element affecting cost considerations is the amount of redundancy to incorporate into the network.

**Speed and Types of Ports/Interfaces**
Choosing the number and type of ports on a router or switch is a critical decision. Newer computers have built-in 1 Gbps NICs. Some servers may even have 10 Gbps ports. Although it is more expensive, choosing Layer 2 devices that can accommodate increased speeds allows the network to evolve without replacing central devices.

**Expandability**
Networking devices are available in fixed and modular physical configurations. Fixed configuration devices have a specific number and type of ports or interfaces and cannot be expanded. Modular devices have expansion slots to add new modules as requirements evolve. Switches are available with additional ports for high-speed uplinks. Routers can be used to connect different types of networks. Care must be taken to select the appropriate modules and interfaces for the specific media.

**Operating System Features and Services**
Network devices must have operating systems that can support the organizations requirements such as the following:
- Layer 3 switching
- Network Address Translation (NAT)
- Dynamic Host Configuration Protocol (DHCP)
- Security
- Quality of service (QoS)
- Voice over IP (VoIP)
### 17.1.3 IP Addressing for a Small Network
When implementing a network, create an IP addressing scheme and use it. All hosts and devices within an internetwork must have a unique address.
Devices that will factor into the IP addressing scheme include the following:
- End user devices - The number and type of connection (i.e., wired, wireless, remote access)
- Servers and peripherals devices (e.g., printers and security cameras)
- Intermediary devices including switches and access points
It is recommended that you plan, document, and maintain an IP addressing scheme based on device type.

### 17.1.4 Redundancy in a Small Network
Another important part of network design is reliability. Even small businesses often rely heavily on their network for business operation. A failure of the network can be very costly.

In order to maintain a high degree of reliability, _redundancy_ is required in the network design. Redundancy helps to eliminate single points of failure.

There are many ways to accomplish redundancy in a network. Redundancy can be accomplished by installing duplicate equipment, but it can also be accomplished by supplying duplicate network links for critical areas.

Small networks typically provide a single exit point toward the internet via one or more default gateways. If the router fails, the entire network loses connectivity to the internet. For this reason, it may be advisable for a small business to pay for a second service provider as backup.

### 17.1.5 Traffic Management
The routers and switches in a small network should be configured to support real-time traffic, such as voice and video, in an appropriate manner relative to other data traffic. In fact, a good network design will implement quality of service (QoS) to classify traffic carefully according to priority during times of congestion.

## 17.2 Small Network Applications and Protocols
### 17.2.1 Common Applications
The network is only as useful as the applications that are on it. There are two forms of software programs or processes that provide access to the network: network applications and application layer services.

**Network Applications**

Applications are the software programs used to communicate over the network. Some end-user applications are network-aware, meaning that they implement application layer protocols and are able to communicate directly with the lower layers of the protocol stack. Email clients and web browsers are examples of this type of application.

**Application Layer Services**

Other programs may need the assistance of application layer services to use network resources like file transfer or network print spooling. Though transparent to an employee, these services are the programs that interface with the network and prepare the data for transfer. Different types of data, whether text, graphics or video, require different network services to ensure that they are properly prepared for processing by the functions occurring at the lower layers of the OSI model.

### 17.2.2 Common Protocols
**Web Server**
- Web clients and web servers exchange web traffic using the Hypertext Transfer Protocol (HTTP).
- Hypertext Transfer Protocol Secure (HTTPS) is used for secure web communication.
 **Email Server**
- Email servers and clients use Simple Mail Transfer Protocol (SMTP) to send emails.
- Email clients use Post Office Protocol (POP3) or Internet Message Access Protocol (IMAP) to retrieve email.
- Recipients are specified using the [user@xyz.xxx](mailto:user@xyz.xxx) format.
**FTP Server**
- File Transfer Protocol (FTP) service allows files to be downloaded and uploaded between a client and FTP server.
- FTP Secure (FTPS) and Secure FTP (SFTP) are used to secure FTP file exchange.
**DHCP Server**
Dynamic Host Configuration Protocol (DHCP) is used by clients to acquire an IP configuration (i.e., IP address, subnet mask, default gateway and more) from a DHCP server.
**DNS Server**
- Domain Name System (DNS) resolves a domain name to an IP address (e.g., [cisco.com](http://cisco.com) = 72.163.4.185)
- DNS provides the IP address of a web site (i.e., domain name) to a requesting host.

These network protocols comprise the fundamental toolset of a network professional. Each of these network protocols define:
- Processes on either end of a communication session
- Types of messages
- Syntax of the messages
- Meaning of informational fields
- How messages are sent and the expected response
- Interaction with the next lower layer

Many companies have established a policy of using secure versions (e.g., SSH, SFTP, and HTTPS) of these protocols whenever possible.
### 17.2.3 Voice and Video Applications
The network administrator must ensure the proper equipment is installed in the network and that the network devices are configured to ensure priority delivery.
**Infrastructure**
- The network infrastructure must support the real-time applications.
- Existing devices and cabling must be tested and validated.
- Newer networking products may be required.
**VoIP**
- VoIP devices convert analog telephone signals into digital IP packets.
- Typically, VOIP is less expensive than an IP telephony solution, but the quality of communications does not meet the same standards.
- Small network voice and video over IP can be solved using Skype and non-enterprise versions of Cisco WebEx.
**IP Telephony**
- An IP phone performs voice-to-IP conversion with the use of a dedicated server for call control and signaling.
- Many vendors provide small business IP telephony solutions such as the Cisco Business Edition 4000 Series products.
**Real-Time Applications**
- The network must support quality of service (QoS) mechanisms to minimize latency issues for real-time streaming applications.
- Real-Time Transport Protocol (RTP) and Real-Time Transport Control Protocol (RTCP) are two protocols that support this requirement.
## 17.3 Scale to Larger Networks
### 17.3.1 Small Network Growth
To scale a network, several elements are required:

- **Network documentation** - Physical and logical topology
- **Device inventory** - List of devices that use or comprise the network
- **Budget** - Itemized IT budget, including fiscal year equipment purchasing budget
- **Traffic analysis** - Protocols, applications, and services and their respective traffic requirements should be documented

### 17.3.2 Protocol Analysis
To determine traffic flow patterns, it is important to do the following:

- Capture traffic during peak utilization times to get a good representation of the different traffic types.
- Perform the capture on different network segments and devices as some traffic will be local to a particular segment.

Information gathered by the protocol analyzer is evaluated based on the source and destination of the traffic, as well as the type of traffic being sent. This analysis can be used to make decisions on how to manage the traffic more efficiently.

### 17.3.3 Employee Network Utilization
In addition to understanding changing traffic trends, a network administrator must be aware of how network use is changing. Many operating systems provide built-in tools to display such information. For example, a Windows host provides tools such as the Task Manager, Event Viewer, and Data Usage tools.

These tools can be used to capture a “snapshot” of information such as the following:

- OS and OS Version
- CPU utilization
- RAM utilization
- Drive utilization
- Non-Network applications
- Network applications
## 17.4 Verify Connectivity
### 17.4.1 Verify Connectivity with Ping
The **ping** command is the most effective way to quickly test Layer 3 connectivity between a source and destination IP address. The command also displays various round-trip time statistics.

Specifically, the **ping** command uses the Internet Control Message Protocol (ICMP) echo request (ICMP Type 8) and echo reply (ICMP Type 0) messages. The **ping** command is available in most operating systems including Windows, Linux, macOS, and Cisco IOS.

On a Windows 10 host, the **ping** command sends four consecutive ICMP echo request messages and expects four consecutive ICMP echo replies from the destination.

**IOS Ping Indicators**
 

| Element | Description                                                                                                                                                                                                                                                                  |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| !       | Exclamation mark indicates successful receipt of an echo reply message.<br>It validates a Layer 3 connection between source and destination.                                                                                                                                 |
| .       | A period means that time expired waiting for an echo reply message.<br>This indicates a connectivity problem occurred somewhere along the path.                                                                                                                              |
| U       | Uppercase U indicates a router along the path responded with an ICMP Type 3 "destination unreachable" error message.<br>Possible reasons include the router does not know the direction to the destination network or it could not find the host on the destination network. |

**Note:** Other possible ping replies include Q, M, ?, or &.
### 17.4.2 Extended Ping
A standard **ping** uses the IP address of the interface closest to the destination network as the source of the **ping**.
The Cisco IOS offers an "extended" mode of the **ping** command. This mode enables the user to create special type of pings by adjusting parameters related to the command operation.

Extended ping is entered in privileged EXEC mode by typing **ping** without a destination IP address. You will then be given several prompts to customize the extended **ping**.
**Note:** The **ping ipv6** command is used for IPv6 extended pings.
### 17.4.3 Verify Connectivity with Traceroute
Traceroute can help locate Layer 3 problem areas in a network. A trace returns a list of hops as a packet is routed through a network. It could be used to identify the point along the path where the problem can be found.

### 17.4.4 Extended Traceroute
Like the extended **ping** command, there is also an extended **traceroute** command. It allows the administrator to adjust parameters related to the command operation. This is helpful in locating the problem when troubleshooting routing loops, determining the exact next-hop router, or determining where packets are getting dropped or denied by a router or firewall.

The Windows **tracert** command allows the input of several parameters through options in the command line. However, it is not guided like the extended traceroute IOS command.

### 17.4.5 Network Baseline
One of the most effective tools for monitoring and troubleshooting network performance is to establish a network baseline. Creating an effective network performance baseline is accomplished over a period of time. Measuring performance at varying times and loads will assist in creating a better picture of overall network performance.
Corporate networks should have extensive baselines; Professional-grade software tools are available for storing and maintaining baseline information.
Cisco’s best practices for baseline processes can be found by searching the internet for “Baseline Process Best Practices”.

## 17.5 Host and IOS Commands
### 17.5.1 IP Configuration on a Windows Host
Checking the IP addressing on host devices is a common practice in networking for verifying and troubleshooting end-to-end connectivity. In Windows 10, you can access the IP address details from the **Network and Sharing Center**.
However, network administrators typically view the IP addressing information on a Windows host by issuing the **ipconfig** command at the command line of a Windows computer.
Use the **ipconfig /all** command to view the MAC address, as well as a number of details regarding the Layer 3 addressing of the device.
If a host is configured as a DHCP client, the IP address configuration can be renewed using the **ipconfig /release** and **ipconfig /renew** commands.
The **ipconfig /displaydns** command displays all of the cached DNS entries on a Windows computer system.
### 17.5.2 IP Configuration on a Linux Host
On the command line, network administrators use the **ifconfig** command to display the status of the currently active interfaces and their IP configuration.
The Linux **ip address** command is used to display addresses and their properties. It can also be used to add or delete IP addresses.
### 17.5.3 IP Configuration on a macOS Hos
n the GUI of a Mac host, open **Network Preferences > Advanced** to get the IP addressing information.
However, the **ifconfig** command can also be used to verify the interface IP configuration.
Other useful macOS commands to verify the host IP settings include **networksetup -listallnetworkservices** and the **networksetup -getinfo <**_network service_**>**.

### 17.5.4 The arp Command
The **arp** command is executed from the Windows, Linux, or Mac command prompt. The command lists all devices currently in the ARP cache of the host, which includes the IPv4 address, physical address, and the type of addressing (static/dynamic), for each device.
The cache can be cleared by using the **netsh interface ip delete arpcache** command in the event the network administrator wants to repopulate the cache with updated information.

**Note:** You may need administrator access on the host to be able to use the **netsh interface ip delete arpcache** command.
### 17.5.5 Common show Commands Revisited
Commonly used **show** commands and when to use them are listed in the table.

| Command                 | Useful for..                                                           |
| ----------------------- | ---------------------------------------------------------------------- |
| **show running-config** | To verify the current configuration and settings                       |
| **show interfaces**     | To verify the interface status and see if there are any error messages |
| **show ip interface**   | To verify the Layer 3 information of an interface                      |
| **show arp**            | To verify the list of known hosts on the local Ethernet LANs           |
| **show ip route**       | To verify the Layer 3 routing information                              |
| **show protocols**      | To verify which protocols are operational<br>                          |
| **show version**        | To verify the memory, interfaces, and licences of the device           |
### 17.5.6 The show cdp neighbors Command
The Cisco Discovery Protocol (CDP) is a Cisco proprietary protocol that runs at the data link layer. Because CDP operates at the data link layer, two or more Cisco network devices, such as routers that support different network layer protocols, can learn about each other even if Layer 3 connectivity has not been established.

When a Cisco device boots, CDP starts by default. CDP automatically discovers neighboring Cisco devices running CDP, regardless of which Layer 3 protocol or suites are running. CDP exchanges hardware and software device information with its directly connected CDP neighbors.

CDP provides the following information about each CDP neighbor device:

- **Device identifiers** - The configured host name of a switch, router, or other device
- **Address list** - Up to one network layer address for each protocol supported
- **Port identifier** - The name of the local and remote port in the form of an ASCII character string, such as FastEthernet 0/0
- **Capabilities list** - For example, whether a specific device is a Layer 2 switch or a Layer 3 switch
- **Platform** - The hardware platform of the device--for example, a Cisco 1841 series router.
The **show cdp neighbors detail** command reveals the IP address of a neighboring device, as shown in the output. CDP will reveal the IP address of the neighbor regardless of whether or not you can ping that neighbor. This command is very helpful when two Cisco routers cannot route across their shared data link. The **show cdp neighbors detail** command will help determine if one of the CDP neighbors has an IP configuration error.
As helpful as CDP is, it can also be a security risk because it can provide useful network infrastructure information to threat actors. For example, by default many IOS versions send CDP advertisements out all enabled ports. However, best practices suggest that CDP should be enabled only on interfaces that are connecting to other infrastructure Cisco devices. CDP advertisements should be disabled on user-facing ports.

Because some IOS versions send out CDP advertisements by default, it is important to know how to disable CDP. To disable CDP globally, use the global configuration command **no cdp run**. To disable CDP on an interface, use the interface command **no cdp enable**.
### 17.5.7 The show ip interface brief Command
One of the most frequently used commands is the **show ip interface brief** command. This command provides a more abbreviated output than the **show ip interface** command.

## 17.6 Troubleshooting Methodologies
### 17.6.1 Basic Troubleshooting Approaches

| Step                                                              | **Description**                                                                                                                                                                                                                                                                                                                            |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Step 1. Identify the Problem**                                  | - This is the first step in the troubleshooting process.<br>- Although tools can be used in this step, a conversation with the user is often very helpful.                                                                                                                                                                                 |
| **Step 2. Establish a Theory of Probable Causes**                 | - After the problem is identified, try to establish a theory of probable causes.<br>- This step often yields more than a few probable causes to the problem.                                                                                                                                                                               |
| **Step 3. Test the Theory to Determine Cause**                    | - Based on the probable causes, test your theories to determine which one is the cause of the problem.<br>- A technician will often apply a quick procedure to test and see if it solves the problem.<br>- If a quick procedure does not correct the problem, you might need to research the problem further to establish the exact cause. |
| **Step 4. Establish a Plan of Action and Implement the Solution** | - After you have determined the exact cause of the problem, establish a plan of action to resolve the problem and implement the solution.                                                                                                                                                                                                  |
| **Step 5. Verify Solution and Implement Preventive Measures**     | - After you have corrected the problem, verify full functionality.<br>- If applicable, implement preventive measures.                                                                                                                                                                                                                      |
| **Step 6. Document Findings, Actions, and Outcomes**              | - In the final step of the troubleshooting process, document your findings, actions, and outcomes.<br>- This is very important for future reference.                                                                                                                                                                                       |
### 17.6.2 Resolve or Escalate?
In some situations, it may not be possible to resolve the problem immediately. A problem should be escalated when it requires a manager decision, some specific expertise, or network access level unavailable to the troubleshooting technician.

For example, after troubleshooting, the technician concludes a router module should be replaced. This problem should be escalated for manager approval. The manager may have to escalate the problem again as it may require the approval of the financial department before a new module can be purchased.

A company policy should clearly state when and how a technician should escalate a problem.
### 17.6.3 The debug Command
OS processes, protocols, mechanisms and events generate messages to communicate their status. These messages can provide valuable information when troubleshooting or verifying system operations. The IOS **debug** command allows the administrator to display these messages in real-time for analysis. It is a very important tool for monitoring events on a Cisco IOS device.

All **debug** commands are entered in privileged EXEC mode. The Cisco IOS allows for narrowing the output of **debug** to include only the relevant feature or subfeature. This is important because debugging output is assigned high priority in the CPU process and it can render the system unusable. For this reason, use **debug** commands only to troubleshoot specific problems.
To list a brief description of all the debugging command options, use the **debug ?** command in privileged EXEC mode at the command line.

To turn off a specific debugging feature, add the **no** keyword in front of the **debug** command:
```
Router# no debug ip icmp
```
Alternatively, you can enter the **undebug** form of the command in privileged EXEC mode:
```
Router# undebug ip icmp
```
To turn off all active debug commands at once, use the **undebug all** command:
```
Router# undebug all
```
Be cautious using some **debug** command. Commands such as **debug all** and **debug ip packet** generate a substantial amount of output and can use a large portion of system resources. The router could get so busy displaying **debug** messages that it would not have enough processing power to perform its network functions, or even listen to commands to turn off debugging. For this reason, using these command options is not recommended and should be avoided.

### 17.6.4 The terminal monitor Command
To display log messages on a terminal (virtual console), use the **terminal monitor** privileged EXEC command. To stop logging messages on a terminal, use the **terminal no monitor** privileged EXEC command.
**Note:** The intent of the **debug** command is to capture live output for a short period of time (i.e., a few seconds to a minute or so). Always disable **debug** when not required.

## 17.1 Troubleshooting Scenarios
### 17.7.1 Duplex Operation and Mismatch Issues
Interconnecting Ethernet interfaces must operate in the same duplex mode for best communication performance and to avoid inefficiency and latency on the link.

The Ethernet autonegotiation feature facilitates configuration, minimizes problems and maximizes link performance between two interconnecting Ethernet links. The connected devices first announce their supported capabilities and then choose the highest performance mode supported by both ends. For example, the switch and router in the figure have successfully autonegotiated full-duplex mode.
### 17.7.2 IP Addressing Issues on IOS Devices
Two common causes of incorrect IPv4 assignment are manual assignment mistakes or DHCP-related issues.

Network administrators often have to manually assign IP addresses to devices such as servers and routers. If a mistake is made during the assignment, then communications issues with the device are very likely to occur.

### 17.7.3 IP Addressing Issues on End Devices
Often, a computer with an APIPA address will not be able to communicate with other devices in the network because those devices will most likely not belong to the 169.254.0.0/16 network. This situation indicates an automatic IPv4 address assignment problem that should be fixed.

**Note:** Other operating systems, such Linux and OS X, will not assign an IPv4 address to the network interface if communication with a DHCP server fails.

Most end devices are configured to rely on a DHCP server for automatic IPv4 address assignment. If the device is unable to communicate with the DHCP server, then the server cannot assign an IPv4 address for the specific network and the device will not be able to communicate.

### 17.7.4 Default Gateway Issues
To solve misconfigured default gateway issues, ensure that the device has the correct default gateway configured. If the default address was manually set but is incorrect, simply replace it with the proper address. If the default gateway address was automatically set, ensure the device can communicate with the DHCP server. It is also important to verify that the proper IPv4 address and subnet mask were configured on the interface of the router and that the interface is active.

On a router, use the **show ip route** command to list the routing table and verify that the default gateway, known as a default route, has been set. This route is used when the destination address of the packet does not match any other routes in its routing table.
### 17.7.5 Troubleshooting DNS Issues
Domain Name System (DNS) defines an automated service that matches names, such as [www.cisco.com](http://www.cisco.com), with the IP address. Although DNS resolution is not crucial to device communication, it is very important to the end user.

It is common for users to mistakenly relate the operation of an internet link to the availability of the DNS. User complaints such as “the network is down” or “the internet is down” are often caused by an unreachable DNS server.
Although it is common for companies and organizations to manage their own DNS servers, any reachable DNS server can be used to resolve names. Small office and home office (SOHO) users often rely on the DNS server maintained by their ISP for name resolution. ISP-maintained DNS servers are assigned to SOHO customers via DHCP. Additionally, Google maintains a public DNS server that can be used by anyone and it is very useful for testing. The IPv4 address of Google’s public DNS server is 8.8.8.8 and 2001:4860:4860::8888 for its IPv6 DNS address.
Use the **ipconfig /all** as shown to verify which DNS server is in use by the Windows computer. The **nslookup** command is another useful DNS troubleshooting tool for PCs.
