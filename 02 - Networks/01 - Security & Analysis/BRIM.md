BrIm is an open-source desktop application that processes pcap files and log files. Its primary focus is providing search and analytics.
It uses Zeek log processing format. It also supports Zeek signatures and Suricata Rules for detection.

It can handle two types of data as an input;

- Packet Capture Files: Pcap files created with tcpdump, tshark and Wireshark like applications.
- Log Files: Structured log files like Zeek logs.
Brim is built on opne-source platforms:
- Zeek: Log generating engine
- Zed Language: Log querying language that allows performing keyword searches with filters and pipelines
- ZNG Data Format: Data storage format that supports saving data streams.
- Electron and React: Cross-platform UI.

**Landing Page**  

Once you open the application, the landing page loads up. The landing page has three sections and a file importing window. It also provides quick info on supported file formats.

- **Pools:** Data resources, investigated pcap and log files.
- **Queries:** List of available queries.
- **History:** List of launched queries.

**Default Queries**

Brim provides pre-made queries, here are some:

Activity Overview: ```count() by _path | sort -r```

Windows Specific Networking Activity : ```_path matcher smb* OR _path=="dce_rpc" | sort -r _path```

**Brim Query Reference**

| **Purpose**                        | **Syntax**                                   | **Example Query**                                                                                                                                      |
| ---------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Basic search                       | You can search any string and numeric value. | Find logs containing an IP address or any value.<br><br>`10.0.0.1`                                                                                     |
| Logical operators                  | Or, And, Not.                                | Find logs contain three digits of an IP AND NTP keyword.<br><br>`192 and NTP`                                                                          |
| Filter values                      | "field name" == "value"                      | Filter source IP.<br><br>`id.orig_h==192.168.121.40`                                                                                                   |
| List specific log file contents    | _path=="log name"                            | List the contents of the conn log file.<br><br>`_path=="conn"`                                                                                         |
| Count field values                 | count () by "field"                          | Count the number of the available log files.<br><br>`count () by _path`                                                                                |
| Sort findings                      | sort                                         | Count the number of the available log files and sort recursively.<br><br>`count () by _path \| sort -r`                                                |
| Cut specific field from a log file | _path=="conn" \| cut "field name"            | Cut the source IP, destination port and destination IP addresses from the conn log file.<br><br>`_path=="conn" \| cut id.orig_h, id.resp_p, id.resp_h` |
| List unique values                 | uniq                                         | Show the unique network connections. <br><br>`_path=="conn" \| cut id.orig_h, id.resp_p, id.resp_h \| sort \| uniq`                                    |

