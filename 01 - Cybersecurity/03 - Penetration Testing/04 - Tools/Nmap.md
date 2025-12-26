Nmap was created by Gordon Lyon (Fyodor), a network security expert and open source programmer. It was released in 1997. Nmap, short for Network Mapper, is free, open-source software released under GPL license. Nmap is an industry-standard tool for mapping networks, identifying live hosts, and discovering running services. Nmap’s scripting engine can further extend its functionality, from fingerprinting services to exploiting vulnerabilities.

## Host Discovery
The '-sn' flag disables port scanning.

### Scan IP List
You can use a file with an IP list with the hosts you need to test.
Flag: `-iL`

### Scan IP Range
An range of IPs can be scanned using this notation:
```bash
$ nmap -sn 10.129.2.18-20
```
Where nmap is going to scan the .18, .19 and .20 IPs.

**Nmap Host Discovery Using ARP**
When a privileged user tries to scan targets on a local network (Ethernet), Nmap uses ARP Requests. When a privileged user tries to scan targets outside the local network, Nmap uses ICMP echo requests, TCP ACK to port 80, TCP SYN to port 443, and ICMP timestamp requests.  When an unprivileged user tries to scan targets outside the local network, Nmap uses TCP 3-way handshake by sending SYN packets to ports 80 and 443.

ARP scan: `-PR`


**Nmap Host Discorvery Using ICMP**
Ping every IP address on a target network and see who would respond to our ping request (ICMP Type 8/Echo) with a ping replyu (ICMP Type 0). Many firewalls block ICMP echo.

ICMP echo: `-PE`

You might also consider ICMP Timestamp (ICMP Type 13) or ICMP Address Mask (ICMP Type 14) requests.

ICMP Timestamp: `-PP`

Nmap uses address mask queries (ICMP Type 17) and checks whether it gets an address mask reply (ICMP Type 18).

ICMP Address Mask: `-PM`

We can use the flag `--packet-trace`, to show all packets sent and received.
We can use the flag `--reason` to determine why a host is alive.
We can use the flag `--disable-arp-ping` to disable ARP pings.

**Nmap Host Discovery Using TCP and UDP**
We can send a packet with the SYN (Synchronize) flag set to a TCP port, 80 by default, and wait for a response. An open port should reply with a SYN/ACK (Acknowledge); a closed port would result in an RST (Reset).

TCP SYN Ping: `-PS<port range>`

TCP ACK Ping: `-PA<port range>`

Sending a UDP packet to an open port is not expected to lead to any reply. However, if we send a UDP packet to a closed UDP port, we expect to get an ICMP port unreachable packet; this indicates that the target system is up and available.

UDP scan: `-PU<port range>`

**Reverse-DNS Lookup**

no DNS lookup: `-n`
reverse-DNS lkookup for all hosts: `-R`
host discovery only: `-sn`


Nmap considers the following six states:

1. **Open**: indicates that a service is listening on the specified port.
2. **Closed**: indicates that no service is listening on the specified port, although the port is accessible. By accessible, we mean that it is reachable and is not blocked by a firewall or other security appliances/programs.
3. **Filtered**: means that Nmap cannot determine if the port is open or closed because the port is not accessible. This state is usually due to a firewall preventing Nmap from reaching that port. Nmap’s packets may be blocked from reaching the port; alternatively, the responses are blocked from reaching Nmap’s host.
4. **Unfiltered**: means that Nmap cannot determine if the port is open or closed, although the port is accessible. This state is encountered when using an ACK scan `-sA`.
5. **Open|Filtered**: This means that Nmap cannot determine whether the port is open or filtered.
6. **Closed|Filtered**: This means that Nmap cannot decide whether a port is closed or filtered.

## Nmap Scans

TCP Connect Scan: `-sT` (SYN)(SYN-ACK)(ACK)(RST-ACK) 
TCP SYN Scan: `-sS` (SYN)(SYN-ACK)(RST)
UDP Scan: `-sU`
- port list: `-p22,80,443` will scan ports 22, 80 and 443.
- port range: `-p1-1023` will scan all ports between 1 and 1023 inclusive, while `-p20-25` will scan ports between 20 and 25 inclusive.
Scan Timing: `-T<0-5>`
- paranoid (0)
- sneaky (1)
- polite (2)
- normal (3)
- aggressive (4)
- insane (5)
Packet Rate: `--min-rate=<num> --max-rate=<num>` packets per minute.
Parallelization: `--min-parallelism=<numprobes> --max-parallelism=<numprobes>`

**Null Scan**
Does not set any TCP flag. -(null)->  if open: nothing; if closed: (RST,ACK)
TCP Null Scan: `-sN`

**Fin Scan**
Same as null scan but sending a FIN flag.
TCP Fin Scan: `-sF`

**Xmas Scan**
Sends FIN, PSH, and URG flags simultaneously, if an RST packet is received, it means that the port is closed.
TCP Xmas Scan: `-sX`

**Maimon Scan**
Named after Uriel Maimon, the FIN and ACK bits are set. The target should send an RST packet as a response. However, certain BSD-derived systems drop the packet if is an open port exposing the open ports.
TCP Maimon Scan: `-sM`

**ACK Scan**
Sends an ACK flag, the host responds with RST regardless if it is open or closed. Is helpful if there is a firewall to discover the rules.
TCP ACK Scan: `-sA`

**Window Scan**
Almost the same as ACK scan but it examines the TCP Window field of the RST packets returned, on specific systems, this may reveal open ports.
Window Scan: `-sW`

**Custom Scan**
You can set custom flags in TCP scans.
Custom Scan: `--scanflags <flags>` 
Example: `--scanflags RSTSYNFIN`

# Spoofing

Beneficial in a situation where you can guarantee the capture of responses.
Nmap will craft all packets with the provided IP address. The target machine will respond to the incoming packets sending the replies to the spoofed address.
1. Attacker sends a packet with a spoofed source IP address to the target machine.
2. Target machine replies to the spoofed IP address as the destination.
3. Attacker captures the replies to figure out open ports.

Spoofing scan: `nmap -e NET_INTERFACE -Pn -S SPOOFED_IP TARGET_IP`
Where `-Pn` specifies to Nmap not expect ping replies.

# Decoying

Sends the target a series of different IPs to respond too, trying to mask the real attacker IP.
Decoy Scan: `nmap -D DECOY_IP,ME,RND TARGET_IP`
Where, ME indicate your IP, RND is a random IP address, and DECOY_IP can be specified.
Decoy scans execute IP addresses in order.

# Fragmented Packets

You can fragment packets in multiples of 8 bytes.
`-f` will split into fragments of 8 bytes.
`-ff`will split into fragments of 16 bytes.

`--mtu` will split into fragments of n bytes. (multiple of 8).

To aid in the reassembly on the recipient side, IP Header (RFC 791) uses the ID and fragment offset fields.

You can also use the option `--data-length NUM` to increase the size of packets.

# Idle/Zombie Scan 

Requires an idle system connected to the network that you can communicate with. Nmap will make each probe appear as if coming from the idle (zombie) host, than will check if it has receive any response.

Idle Scan: `-sI ZOMBIE_IP`

The idle (zombie) scan requires the following three steps to discover whether a port is open:

1. Trigger the idle host to respond so that you can record the current IP ID on the idle host.
2. Send a SYN packet to a TCP port on the target. The packet should be spoofed to appear as if it was coming from the idle host (zombie) IP address.
3. Trigger the idle machine again to respond so that you can compare the new IP ID with the one received earlier.

# More Details

You can use `--reason`to get more details about Nmap results.
Verbosity: `-v or -vv`
Debugging: `-d or -dd`
Specify the source port: `--source-port PORT_NUM`

# Services

Nmap can collect and determine services and version information for open ports.
You can control the intensity of discovery.

Service Scan: `-sV`
Intensity: `--version-intensity LEVEL`
Intensity level 2: `--version-light`
Intensity level 9: `--version-all`

# OS Detection
`-O`, Nmap tries to identify the host OS.

# Traceroute

Finds routers between you and the target.
`--traceroute`

# Nmap Scripting Engine (NSE)

NSE is a Lua interpreter that allows Nmap to execute scripts.
You can find more than 600 scripts in `/usr/share/nmap/scripts`.
You can choose scripts in the default category using `--scripts=default`or `-sC`, also, there are the following categories:

| Script Category | Description                                                            |
| --------------- | ---------------------------------------------------------------------- |
| `auth`          | Authentication related scripts                                         |
| `broadcast`     | Discover hosts by sending broadcast messages                           |
| `brute`         | Performs brute-force password auditing against logins                  |
| `default`       | Default scripts, same as `-sC`                                         |
| `discovery`     | Retrieve accessible information, such as database tables and DNS names |
| `dos`           | Detects servers vulnerable to Denial of Service (DoS)                  |
| `exploit`       | Attempts to exploit various vulnerable services                        |
| `external`      | Checks using a third-party service, such as Geoplugin and Virustotal   |
| `fuzzer`        | Launch fuzzing attacks                                                 |
| `intrusive`     | Intrusive scripts such as brute-force attacks and exploitation         |
| `malware`       | Scans for backdoors                                                    |
| `safe`          | Safe scripts that won’t crash the target                               |
| `version`       | Retrieve service versions                                              |
| `vuln`          | Checks for vulnerabilities or exploit vulnerable services              |
You can also specify the script by name using `--script "SCRIPT-NAME"` or a pattern such as `--script "ftp*"`, which would include `ftp-brute`.

# Outputs

| Flag  | Description                                      |
| ----- | ------------------------------------------------ |
| `-oN` | Save output in normal format (.nmap)             |
| `-oG` | Save output in grepable format (.gnmap)          |
| `-oX` | Save output in XML format (.xml)                 |
| `-oA` | Ssave output in normal, XML and Grepable formats |
To convert stored results to XML format to HTML, we can use the tool `xsltproc`:
```bash
$ xsltproc target.xml -o target.html
```

# Extra 

| `-A`  | equivalent to `-sV -O -sC --traceroute`         |
| ----- | ----------------------------------------------- |
Press SPACE to view status during the scan or set the flag `--stats-every=<num><s|m>.`

