Created in 2015, Wazuh is an open-source, freely available and extensive [[Endpoint Security]] tool or Endpoint detection and response (EDR) solution. Wazuh operates on a management and agent module. Simpy, a device is dedicated to running Wazuh named a **manager**, where Wazuh operates on a management and agent mode where the manager is responsible for managing agents installed on the devices you'd like to monitor.

**Agents**
Devices that record the events and processes of a system.
In order for Wazuh to be populated, agents need to be installed onto devices to log such events. Wazuh can guide you through the agent deployment process provided you fill out some pre-requisites such as:

- Operating System
- The address of the Wazuh server that the agent should send logs to (this can be a DNS entry or an IP address)
- What group the agent will be under - you can sort agents into groups within Wazuh if you wish

**Vulnerability Assessment & Security Events**
Wazuh’s Vulnerability Assessment module is a powerful tool that can be used to periodically scan an agent's operating system for installed applications and their version numbers.
Once this information has been gathered, it is sent back to the Wazuh server and compared against a database of CVEs to discover potential vulnerabilities.
The vulnerability scanner module will perform a full scan when the Wazuh agent is first installed on a device and **must** be configured to run at a set interval then after (by default, this is set to 5 minute intervals when enabled).

**Policy Auditing**

Wazuh is capable of auditing and monitoring an agent's configuration whilst proactively recording event logs. When the Wazuh agent is installed, an audit is performed where a metric is given using multiple frameworks and legislations such as NIST, MITRE and GDPR.

**Monitoring Logs**

Wazuh's security event monitor is capable to actively record both successful and unsuccessful authentication attempts. The rule with an id of 5710 detects attempted connections that are unsuccessful for the SSH protocol.

**Wazuh API**
The Wazuh management server features a rich and extensive API to allow the Wazuh management server to be interacted with using the command line.

**Generating Reports**
Wazuh features a reporting module that allows you to view a summarised breakdown of events that have occurred on an agent.

**Loading Sample Data**
The Wazuh management server comes with sample data bundled with the installation that can be loaded at your convenience.