Endpoint Detection and Response (EDR) is a security solution that offers deep-level protection for endpoints. No matter where the endpoints are, the will make sure they are monitored constantly and threats are detected.

Below are some of the solutions in the market:

- [**CrowdStrike Falcon** (opens in new tab)](https://www.crowdstrike.com/wp-content/uploads/2022/03/crowdstrike-falcon-insight-data-sheet.pdf)
- [**SentinelOne ActiveEDR** (opens in new tab)](https://sentinelone.com/resources/datasheets/assets/usecase/sentinel-one-active-#page=1)
- [**Microsoft Defender for Endpoint** (opens in new tab)](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)
- [**OpenEDR** (opens in new tab)](https://www.openedr.com/)
- [**Symantec** (opens in new tab)](https://docs.broadcom.com/doc/endpoint-detection-and-response-atp-endpoint-en)

Several other solutions are available in the market. Their underlying architecture is mostly similar, but the features may vary.

# Features of EDR
## Visibility
 It collects detailed data from the endpoints, which includes process modifications, registry modifications, file and folder modifications, user actions, and much more. It then presents this information in a very structured format to the analyst. The analyst can see the whole process tree with a complete activity timeline of the sequence of actions.
## Detection
It incorporates signature-based detections as well as behavior-based detections, such as unexpected user activities. With modern machine learning capabilities, it identifies any deviation from the baseline behavior and instantly flags it. It can also detect fileless malware that resides in memory. It also allows us to feed custom IOCs for threat detections.
Based on the telemetry received from the endpoints, some advanced detection techniques are applied to this data. Some of these techniques include:
- **Behavioral Detection**
- **Anomaly Detection**
- **IOC matching**
- **MITRE ATT&CK Mapping**
- **Machine Learning Algorithms**
## Response
These actions can be taken at any endpoint within the central EDR console. Imagine getting a detection on the EDR with full-fledged details on when, where, and what happened, and you have to opt for the best possible action for that detection. As an analyst, you may decide to isolate a complete endpoint, terminate a process, or quarantine some files. You can also connect to the host remotely and execute actions independently. You can do this all from within the EDR console.
- **Isolate Host**
- **Terminate Process**
- **Quarantine**
- **Remote Access**
- **Artefacts Collection**
# Agents
We can integrate multiple endpoints with our EDR and manage them through a centralized console. There are EDR agents that we have to deploy inside those endpoints. These agents are also sometimes referred to as sensors.
# EDR Console
All the detailed data sent by the EDR agents is correlated and analyzed through complex logic and machine learning algorithms. The threat intelligence information is matched with the collected data. The EDR is just like the brain connecting all the dots. These dots connect to form a detection, often called an alert.

# EDR with Other Tools
Within a network, you will see Firewalls, DLPs, Email Security Gateways, IAMs, EDRs, and other security solutions protecting the different components of the network. To minimize the effort and maximize the efficiency, all these security solutions are integrated with a SIEM solution that becomes the central point of investigation for the analysts.

# Collected Telemetry
- **Process Executions and Terminations**  
    It keeps track of all the running and idle processes, which helps to identify suspicious child-parent process relationships, suspicious executables initiating a process, malware payload, etc.
- **Network Connections**  
    All the endpoints' network connections are monitored, which helps identify any connection to a C2 server, unusual port usage, data exfiltration, or lateral movement within the network.
- **Command Line Activity**  
    It captures all the commands executed on the endpoints in CMD, PowerShell, etc., which helps to identify malicious command execution, obfuscated PowerShell script executions, which are often missed by a traditional antivirus.
- **Files and Folders Modifications**  
    Threat actors modify different files and folders during data staging, ransomware executions, and malicious file dropping. The EDR tracks this.
- **Registry Modifications**  
    The registry is a goldmine of information about the configurations in a Windows system. There are many registry modifications that occur during a malicious activity, and most of these are monitored by the EDR.