Wazuh rules help the system detect attacks in the early stages, such as intrusions, software misuse, configuration issues, application errors, malware, rootkits, systems anomalies, and security policy violations. Wazuh comes with several prebuild rules and decoders but also allows you to add custom rules. Let's take a sample Wazuh rule:
```XML
<rule id="200101" level="1">
	<if_sid>60009</if_sid>
	<field name="win.system.providerName">^PowerShell$</field>
	<mitre>
		<id>T1086</id>
	</mitre>
	<options>no_full_log</options>
	<description>Powershell Information EventLog</description>
```
- **`rule_id`**: This represents the unique identifier for Wazuh rule.
- **`level`**: The rule's classification level ranges between 0 and 15. According to the rule categories page in the Wazuh documentation, each number indicates a distinct value and severity.
- **`if_sid`**: This specifies the ID of another rule (in our case, it's 60009), which triggers the current rule. The "if" condition is considered as the "parent" rule that must be checked first.
- **`field name`**: This specifies the name of the field extracted form the decoder. The value is matched by a regular expression.
- **`group`**: This is used to organize the Wazuh rules.
# CDB lists
The Constant Database (CDB) list enable the categorization and management of IP addresses and domain based on their characteristics.
# Groups 
Agents can be grouped based on their OS or functionalities using groups.
# Configuration
This helps security teams to fine-tune Wazuh's main configurations such as cluster configuration, alert and output management, log data analysis, cloud security, vulnerabilities, inventory data, active response, commands, Docker listeners, and monitoring (Amazon S3, Azure logs, Google Cloud, GitHub, Office 365, etc.). 
You need to locate the `ossec.conf` file in your Wazuh manager or Wazuh agent at the `/var/ossec/etc`directory.