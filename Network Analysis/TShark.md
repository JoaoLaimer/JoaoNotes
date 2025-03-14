 TShark is an open-source cli alternative to Wireshark, it was developed by the same people behind Wireshark too.

**Command-Line Packet Analysis**
- ```capinfos```: provides details of a specified pcap file. Suggested to view before starting investigation.
The most common parameters are explained in the given table below. Not that TShark requires superuser privileges to sniff live traffic and list all available interfaces.

| **Parameter**    | **Purpose**                                                                                                                                                       |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -h               | - Display the help page with the most common features.<br>- `tshark -h`                                                                                           |
| -v               | - Show version info.<br>- `tshark -v`                                                                                                                             |
| -D               | - List available sniffing interfaces.<br>- `tshark -D`                                                                                                            |
| -i               | - Choose an interface to capture live traffic.<br>- `tshark -i 1`<br>- `tshark -i ens55`                                                                          |
| **No Parameter** | - Sniff the traffic like tcpdump.<br>- `tshark`                                                                                                                   |
| -r               | - Read/input function. Read a capture file.<br>- `tshark -r demo.pcapng`                                                                                          |
| -c               | - Packet count. Stop after capturing a specified number of packets.<br>- E.g. stop after capturing/filtering/reading 10 packets.<br>- `tshark -c 10`              |
| -w               | - Write/output function. Write the sniffed traffic to a file.<br>- `tshark -w sample-capture.pcap`                                                                |
| -V               | - Verbose.<br>- Provide detailed information **for each packet**. This option will provide details similar to Wireshark's "Packet Details Pane".<br>- `tshark -V` |
| -q               | - Silent mode.<br>- Suspress the packet outputs on the terminal.<br>- `tshark -q`                                                                                 |
| -x               | - Display packet bytes.<br>- Show packet details in hex and ASCII dump for each packet.<br>- `tshark -x`                                                          |
**Capture Condition Parameters**
As a network sniffer and packet analyser, TShark can be configured to count packets and stop at a specific point or run in a loop structure. The most common parameters are explained below.


| Parameter | Purpose                                                                                                                                                                                                                                                                     |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|           | Define Capture conditions for a single run/loop. Stop after completing the condition.                                                                                                                                                                                       |
| -a        | - **Duration**: Stop after X Seconds.<br>`tshark -w test.pcap -a duration:1`<br>- **Filesize**: Stop after reaching X file size (KB).<br>`tshark -w test.pcap -a filesize:10`<br>- **Files**: Stop after X files.<br>`tshark -w test.pcap -a filesize:10 -a files:3<br><br> |
|           | Ring buffer control options. Define capture conditions for multiple runs/loops. (Infinite loop)                                                                                                                                                                             |
| -b        |  Same as before but with the -b flag instead of -a.                                                                                                                                                                                                                         |
**Capture & Display Filters**
There are two dimensions of packet filtering in TShark; live (capture) and post-capture (display) filtering.

| Parameter | Purpose                                                              |
| --------- | -------------------------------------------------------------------- |
| -f        | Capture Filters. Same as BPF syntax and Wireshark's capture filters. |
| -Y        | Display filters. Same as Wireshark's display filters.                |

**Capture Filters**

| **Qualifier** | **Details and Available Options**                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Type**      | Target match type. You can filter IP addresses, hostnames, IP ranges, and port numbers. Note that if you don't set a qualifier, the "host" qualifier will be used by default.<br><br>- host \| net \| port \| portrange<br>- Filtering a host<br><br>- `tshark -f "host 10.10.10.10"`<br><br>- Filtering a network range <br><br>- `tshark -f "net 10.10.10.0/24"`<br><br>- Filtering a Port<br><br>- `tshark -f "port 80"`<br><br>- Filtering a port range<br><br>- `tshark -f "portrange 80-100"` |
| **Direction** | Target direction/flow. Note that if you don't use the direction operator, it will be equal to "either" and cover both directions.<br><br>- src \| dst<br>- Filtering source address<br><br>- `tshark -f "src host 10.10.10.10"`<br><br>- Filtering destination address<br><br>- `tshark -f "dst host 10.10.10.10"`                                                                                                                                                                                  |
| **Protocol**  | Target protocol.<br><br>- arp \| ether \| icmp \| ip \| ip6 \| tcp \| udp<br>- Filtering TCP<br><br>- `tshark -f "tcp"`<br><br>- Filtering MAC address<br><br>- `tshark -f "ether host F8:DB:C5:A2:5D:81"`<br><br>- You can also filter protocols with IP Protocol numbers assigned by IANA.<br>- Filtering IP Protocols 1 (ICMP)<br><br>- `tshark -f "ip proto 1"`<br>- [**Assigned Internet Protocol Numbers**](https://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml)         |

**Display Filters**

| **Qualifier** | **Details and Available Options**                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Type**      | Target match type. You can filter IP addresses, hostnames, IP ranges, and port numbers. Note that if you don't set a qualifier, the "host" qualifier will be used by default.<br><br>- host \| net \| port \| portrange<br>- Filtering a host<br><br>- `tshark -f "host 10.10.10.10"`<br><br>- Filtering a network range <br><br>- `tshark -f "net 10.10.10.0/24"`<br><br>- Filtering a Port<br><br>- `tshark -f "port 80"`<br><br>- Filtering a port range<br><br>- `tshark -f "portrange 80-100"` |
| **Direction** | Target direction/flow. Note that if you don't use the direction operator, it will be equal to "either" and cover both directions.<br><br>- src \| dst<br>- Filtering source address<br><br>- `tshark -f "src host 10.10.10.10"`<br><br>- Filtering destination address<br><br>- `tshark -f "dst host 10.10.10.10"`                                                                                                                                                                                  |
| **Protocol**  | Target protocol.<br><br>- arp \| ether \| icmp \| ip \| ip6 \| tcp \| udp<br>- Filtering TCP<br><br>- `tshark -f "tcp"`<br><br>- Filtering MAC address<br><br>- `tshark -f "ether host F8:DB:C5:A2:5D:81"`<br><br>- You can also filter protocols with IP Protocol numbers assigned by IANA.<br>- Filtering IP Protocols 1 (ICMP)<br><br>- `tshark -f "ip proto 1"`<br>- [**Assigned Internet Protocol Numbers**](https://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml)         |

**Statistics**
TShark is considered a command line version of Wireshark. In addition to sharing the same display filters, TShark can accomplish several features of Wireshark explained below.

| **Parameter** | **Purpose**                                                                                                                                                                                                                                                                                                                                                                                                    |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| --color       | - Wireshark-like colourised output.<br>- `tshark --color`                                                                                                                                                                                                                                                                                                                                                      |
| -z            | - Statistics<br>- There are multiple options available under this parameter. You can view the available filters under this parameter with:<br><br>- `tshark -z help`<br><br>- Sample usage.<br><br>- `tshark -z filter`<br><br>- Each time you filter the statistics, packets are shown first, then the statistics provided. You can suppress packets and focus on the statistics by using the `-q` parameter. |
	**Protocol Hierarchy**
	Protocol hierarchy helps analysts to see the protocols used, frame numbers, and size of packets in a tree view based on packet numbers. As it provides a summary of the capture, it can help analysts decide the focus point for an event of interest. Use the `-z io,phs -q` parameters to view the protocol hierarchy.
	You can focus on a specific protocol as shown below. Add the `udp` keyword to the filter to focus on the UDP protocol.
	**Packet Lengths Tree**
	Gives an overview of the feneral distribution of packets by size in a tree view. Use the `-z plen,tree -q` parameters to view the packet lengths tree.
	**Endpoints**
	It shows the number of packets associated with each endpoint. Similar to Wireshark, TShark supports multiple source filtering options for endpoint identification. Use the `-z endpoints,ip -q` parameters to view IP endpoints. Note that you can choose other available protocols as well.

| **Filter** | **Purpose**                                       |
| ---------- | ------------------------------------------------- |
| eth        | - Ethernet addresses                              |
| ip         | - IPv4 addresses                                  |
| ipv6       | - IPv6 addresses                                  |
| tcp        | - TCP addresses<br>- Valid for both IPv4 and IPv6 |
| udp        | - UDP addresses<br>- Valid for both IPv4 and IPv6 |
| wlan       | - IEEE 802.11 addresses                           |
	**Conversations**
	Use `-z conv,ip -q`
	**Expert Info**
	Use `-z expert -1`
	**IPv4 and IPv6**
	You can filter the available protocol types and view the details using `-z ptype, tree -q`.
	You can filter all IP addresses using:
	- IPv4:`-z ip_hosts, tree -q`
	- IPv6: `-z ipv6_hosts,tree -q`
	Or focusing by source or destination:
	`ip_srcdst or ipv6_srdst`
	`dests or ipv6_dests`
	**DNS**
	Use `-z dns,tree -q`
	**HTTP**
	- **Packet and status counter for HTTP:** `-z http,tree -q`
	- **Packet and status counter for HTTP2:** `-z http2,tree -q`
	- **Load distribution:** `-z http_srv,tree -q`
	- **Requests:** `-z http_req,tree -q`
	- **Requests and responses:** `-z http_seq,tree -q`
	**Follow Stream**

| **Main Parameter** | **Protocol**                        | **View Mode**    | **Stream Number**    | **Additional Parameter** |
| ------------------ | ----------------------------------- | ---------------- | -------------------- | ------------------------ |
| -z follow          | - TCP<br>- UDP<br>- HTTP<br>- HTTP2 | - HEX<br>- ASCII | 0 \| 1 \| 2 \| 3 ... | -q                       |
	**Export Objects**

| **Main Parameter** | **Protocol**                                  | **Target Folder**                | **Additional Parameter** |
| ------------------ | --------------------------------------------- | -------------------------------- | ------------------------ |
| --export-objects   | - DICOM<br>- HTTP<br>- IMF<br>- SMB<br>- TFTP | Target folder to save the files. | -q                       |
	**Credentials**
	Use `-z credentials -q`
	**Extract Fields**
	This option allows extraction of specific pats of data from the packets.

| **Main Filter** | **Target Field** | **Show Field Name** |
| --------------- | ---------------- | ------------------- |
| -T fields       | -e <field name>  | -E header=y         |
