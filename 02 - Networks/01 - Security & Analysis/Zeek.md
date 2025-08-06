Zeek (formerly Bro) is an open-source and commercial network monitoring tool (traffic analyser).

[The official description;](https://docs.zeek.org/en/master/about.html) "Zeek (formerly Bro) is the world's leading platform for network security monitoring. Flexible, open-source, and powered by defenders." "Zeek is a passive, open-source network traffic analyser. Many operators use Zeek as a network security monitor (NSM) to support suspicious or malicious activity investigations. Zeek also supports a wide range of traffic analysis tasks beyond the security domain, including performance measurement and troubleshooting."
**Capabilites**: NSM and IDS framework. It is heavily focused on network analysis. It is more focused on specific threats to trigger alerts. The detection mechanism is focused on events.
**Cons**: Hard to use, The analysis is done out of the Zeek, manually or by automation.
**Pros**: It provides in-depth traffic visibility. Useful for threat hunting. Ability to detect complex threats. It has a scripting language and supports event correlation. Easy to read logs.
**Common Use Case**:Network monitoring. In-depth traffic investigation. Intrusion detecting in chained events.

**Zeek Frameworks**

|   |   |   |   |   |
|---|---|---|---|---|
|Logging|Notice|Input|Configuration|Intelligence|
|Cluster|Broker Communication|Supervisor|GeoLocation|File Analysis|
|Signature|Summary|NetControl|Packet Analysis|TLS Decryption|

**Zeek Outputs**

Zeek provides 50+ log files under seven different categories. Once you process a pcap with Zeek, it will create the logs in the working directory. If you run as a service, your logs will be located in the default log path ```/opt/zeek/logs/```

**Check version**
```sh
zeek -v
```

**First Steps**
Switch to superuser account and execute the following command:
```zeekctl```

You can use the "ZeekControl" mode with the following commands as well;
- ```zeekctl status```
- ```zeekctl start```
- ```zeekctl stop```

Or you can use the main Zeek command:

| Parameter | Description              |
| --------- | ------------------------ |
| -r        | Read/Process a pcap      |
| -C        | Ignoring checksum errors |
| -v        | Version information.     |
| zeekctl   | ZeekControl module.      |
| -s        | Use signature.           |
Investigating logs will require command-line tools (cat, cut, grep, sort, and uniq).

**Zeek Logs**

| Category             | Description                                                              | **Log Files**                                                                                                                                                                                                                                                                                                                      |
| -------------------- | ------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Network              | Network protocol logs.                                                   | _conn.log, dce_rpc.log, dhcp.log, dnp3.log, dns.log, ftp.log, http.log, irc.log, kerberos.log, modbus.log, modbus_register_change.log, mysql.log, ntlm.log, ntp.log, radius.log, rdp.log, rfb.log, sip.log, smb_cmd.log, smb_files.log, smb_mapping.log, smtp.log, snmp.log, socks.log, ssh.log, ssl.log, syslog.log, tunnel.log._ |
| Files                | File analysis result logs.                                               | _files.log, ocsp.log, pe.log, x509.log._                                                                                                                                                                                                                                                                                           |
| NetControl           | Network control and flow logs.                                           | _netcontrol.log, netcontrol_drop.log, netcontrol_shunt.log, netcontrol_catch_release.log, openflow.log._                                                                                                                                                                                                                           |
| Detection            | Detection and possible indicator logs.                                   | _intel.log, notice.log, notice_alarm.log, signatures.log, traceroute.log._                                                                                                                                                                                                                                                         |
| Network Observations | Network flow logs.                                                       | _known_certs.log, known_hosts.log, known_modbus.log, known_services.log, software.log._                                                                                                                                                                                                                                            |
| Miscellaneous        | Additional logs cover external alerts, inputs and failures.              | _barnyard2.log, dpd.log, unified2.log, unknown_protocols.log, weird.log, weird_stats.log._                                                                                                                                                                                                                                         |
| Zeek Diagnostic      | Zeek diagnostic logs cover system messages, actions and some statistics. | _broker.log, capture_loss.log, cluster.log, config.log, loaded_scripts.log, packet_filter.log, print.log, prof.log, reporter.log, stats.log, stderr.log, stdout.log._                                                                                                                                                              |
Although there are multiple log files, some logs are updated daily, or updated in each session. Some of the most commonly used logs are explained below.

| Update Frequency | Log Name           | Description                                     |
| ---------------- | ------------------ | ----------------------------------------------- |
| **Daily**        | known_hosts.log    | List of hosts that completed TCP handshakes.    |
| **Daily**        | known_services.log | List of services used by hosts.                 |
| **Daily**        | known_certs.log    | List of SSL certificates.                       |
| **Daily**        | software.log       | List of software used on the network.           |
| **Per Session**  | notice.log         | Anomalies detected by Zeek.                     |
| **Per Session**  | intel.log          | Traffic contains malicious patterns/indicators. |
| **Per Session**  | signature.log      |  List of triggered signatures.                  |
**Brief log usage primer table;**

| **Overall Info**     | **Protocol Based** | **Detection**    | **Observation**      |
| -------------------- | ------------------ | ---------------- | -------------------- |
| _conn.log_           | _http.log_         | _notice.log_     | _known_host.log_     |
| _files.log_          | _dns.log_          | _signatures.log_ | _known_services.log_ |
| _intel.log_          | _ftp.log_          | _pe.log_         | _software.log_       |
| _loaded_scripts.log_ | _ssh.log_          | _traceroute.log_ | _weird.log_          |
**Zeek Cut**

```zeek-cut```helps extracting information from the logs generated, based on the fields provided by each log.

**Zeek Signatures**

Zeek signatures use low-level pattern matching and cover conditions similar to Snort rules. Unlike Snort rules, Zeek rules are not the primary event detection point. Zeek has a scripting language and can chain multiple events to find an event of interest.

Zeek signatures are composed of three logical paths; signature id, conditions and action.

| **Signature id** | **Unique** signature name.                                                                                                                                                                              |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Conditions**   | **Header:** Filtering the packet headers for specific source and destination addresses, protocol and port numbers.<br><br><br>**Content:** Filtering the packet payload for specific value/pattern.<br> |
| **Action**       | **Default action:** Create the "signatures.log" file in case of a signature match.<br><br>**Additional action:** Trigger a Zeek script.                                                                 |
Filters are based on Berkeley Packet Filters (BPF).

Example: Simple HTTP password filter.
```zeek
signature http-password {
     ip-proto == tcp
     dst-port == 80
     payload /.*password.*/
     event "Cleartext Password Found!"
}

# signature: Signature name.
# ip-proto: Filtering TCP connection.
# dst-port: Filtering destination port 80.
# payload: Filtering the "password" phrase.
# event: Signature match message.
```

**Zeek Scripts**

Zeek has base scripts installed by default, and these are not intended to be modified.
- These scripts are located in **"/opt/zeek/share/zeek/base".**
User-generated or modified scripts should be located in a specific path.
- These scripts are located in  **"/opt/zeek/share/zeek/site".**
Policy scripts are located in a specific path.
- These scripts are located in **"/opt/zeek/share/zeek/policy"**.
Like Snort, to automatically load/use a script in live sniffing mode, you must identify the script in the Zeek configuration file. You can also use a script for a single run, just like the signatures.
- The configuration file is located in **"/opt/zeek/share/zeek/site/local.zeek"**.

You can call scripts in live monitoring mode by loading them with the command `load @/script/path` or `load @script-name` in local.zeek file.

Here's a Zeek Script for extracting hostnames:
```zeekScript
event dhcp_message (c: connection, is_orig: bool, msg: DHCP::Msg, options: DHCP::Options)
{
print options$host_name;
}
```


**Events**

```markdown
# zeek_init: Do actions once Zeek starts its process.
# zeek_done: Do activities once Zeek finishes its process.
# print: Prompt a message on the terminal.

event zeek_init()
    {
     print ("Started Zeek!");
    }
event zeek_done()
    {
    print ("Stopped Zeek!");
    }
```


```markdown
event new_connection(c: connection)
{
	print c;
}

#Prints bulk information about a new connection
```

```markdown
event new_connection(c: connection)
{
	print ("###########################################################");
	print ("");
	print ("New Connection Found!");
	print ("");
	print fmt ("Source Host: %s # %s --->", c$id$orig_h, c$id$orig_p);
	print fmt ("Destination Host: resp: %s # %s <---", c$id$resp_h, c$id$resp_p);
	print ("");
}

# %s: Identifies string output for the source.
# c$id: Source reference field for the identifier.
```

**Scripts and Signatures Together**

```markdown
event signature_match (state: signature_state, msg: string, data: string)
{
if (state$sig_id == "ftp-admin")
    {
    print ("Signature hit! --> #FTP-Admin ");
    }
}
```

In the command-line: ```zeek -C -r ftp.pcap -s ftp-admin.sig 201.zeek```

**Loading local scripts** 
Can be achieved by using the ```local``` command.
- ```zeek -C -r ftp.pcap local```

**Frameworks**
Not all framework functionalities are intended to be used in CLI mode. The majority of them are used in scripting. You can easily see the usage of frameworks in scripts by calling a specific framework as `load @ $PATH/base/frameworks/framework-name`

```markdown
# Enable MD5, SHA1 and SHA256 hashing for all files.

@load base/files/hash
event file_new(f: fa_file)
	{
	Files::add_analyzer(f, Files::ANALYZER_MD5);
	Files::add_analyzer(f, Files::ANALYZER_SHA1);
	Files::add_analyzer(f, Files::ANALYZER_SHA256);
	}
```

**Zeek Packages**

The package manager is installed with Zeek and available with the `zkg` command.

**Basic usage of zkg;**

| **Command**                | **Description**                                                             |
| -------------------------- | --------------------------------------------------------------------------- |
| `zkg install package_path` | Install a package. Example (zkg install zeek/j-gras/zeek-af_packet-plugin). |
| `zkg install git_url`      | Install package. Example (zkg install https://github.com/corelight/ztest).  |
| `zkg list`                 | List installed package.                                                     |
| `zkg remove`               | Remove installed package.                                                   |
| `zkg refresh`              | Check version updates for installed packages.                               |
| `zkg upgrade`              | Update installed packages.                                                  |
```markdown
### Calling with script
ubuntu@ubuntu$ zeek -Cr http.pcap sniff-demo.zeek 

### View script contents
ubuntu@ubuntu$ cat sniff-demo.zeek 
@load /opt/zeek/share/zeek/site/zeek-sniffpass

### Calling from path
ubuntu@ubuntu$ zeek -Cr http.pcap /opt/zeek/share/zeek/site/zeek-sniffpass

### Calling with package name
ubuntu@ubuntu$ zeek -Cr http.pcap zeek-sniffpass 
```

