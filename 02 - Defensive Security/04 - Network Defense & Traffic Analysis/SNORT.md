SNORT is an **open-source, rule-based** Network Intrusion Detection and Prevention System **(NIDS/NIPS)**. It was developed and still maintained by Martin Roesch, open-source contributors, and the Cisco Talos team.
**[The official description](https://www.snort.org/):** _"Snort is the foremost Open Source Intrusion Prevention System (IPS) in the world. Snort IPS uses a series of rules that help define malicious network activity and uses those rules to find packets that match against them and generate alerts for users."_


| Parameter    | Description                                                            |
| ------------ | ---------------------------------------------------------------------- |
| -V/--version | provides information about instance version                            |
| -c           | identifying conf file                                                  |
| -T           | Snort's self-test                                                      |
| -q           | Quiet mode prevents snort from displaying the banner and initial info. |

**Sniffer Mode**

| Parameter | Description                                          |
| --------- | ---------------------------------------------------- |
| -v        | Verbose. Display TCP/IP.                             |
| -d        | Display packet data (payload).                       |
| -e        | Display link-layer headers.                          |
| -X        | Display the packet details in HEX.                   |
| -i        | Define a specific network interface to listen/sniff. |
**Packet Logger Mode**

| Parameter | Description                                                                                                    |
| --------- | -------------------------------------------------------------------------------------------------------------- |
| -l        | Logger mode, target log and alert output directory. Default output folder is /var/log/snort as tcpdump format. |
| -K ASCII  | Log packets in ASCII format                                                                                    |
| -r        | Reading option, read the dumped logs in Snort.                                                                 |
| -n        | Specify the number of packets that will process/read.                                                          |
"_The one who logs is the owner of the logs_".
The -r command also allows users to filter the binary log files in the Berkeley Packet Filters (BPF).
**IDS/IPS Mode**

| Parameter         | Description                                                                                                                                                                                                                                                             |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -c                | Defining configuration file                                                                                                                                                                                                                                             |
| -T                | Testing configuration file                                                                                                                                                                                                                                              |
| -N                | Disable logging                                                                                                                                                                                                                                                         |
| -D                | Background mode                                                                                                                                                                                                                                                         |
| -A                | Alert Modes;<br>full: Provides all possible info about the alert, also the default mode.<br>fast: shows the alert message, timestamp, src and dst ip and port numbers.<br>cmg: CMG style.<br>none: no alerts.<br>console: provides fast style alerts on console screen. |
| -Q --daq afpacket | Activate IPS mode, can be also activated by editing snort.conf file                                                                                                                                                                                                     |

**PCAP Investigation Mode**


| Parameter           | Description                                  |
| ------------------- | -------------------------------------------- |
| -r / --pcap-single= | Read a single pcap                           |
| --pcap-list=""      | Read pcaps provided (space separated).       |
| --pcap-show         | Show pcap name on console during processing. |
