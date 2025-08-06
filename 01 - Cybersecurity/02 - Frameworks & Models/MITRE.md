From [**Mitre.org**](https://www.mitre.org/about/corporate-overview): "_At MITRE, we solve problems for a safer world. Through our federally funded R&D centers and public-private partnerships, we work across government to tackle challenges to the safety, stability, and well-being of our nation._"

Basic Terminology:
	-APT (Advanced Persistent Threat): Team/Group/Country that engages in long-term attacks.
	-TTP( Tactics, Techniques, and Procedures): 
		-Tactics: Adversary goal or objective.
		-Techniques: How an adversary achieves this goal.
		-Procedures: How the technique is executed.

**ATT&CK**:

What is the ATT&CK® framework? According to the [website](https://attack.mitre.org/), "_MITRE ATT&CK® is a globally-accessible knowledge base of adversary tactics and techniques based on real-world observations._"
	MITRE ATT&CK® Navigator: "_The ATT&CK® Navigator is designed to provide basic navigation and annotation of ATT&CK® matrices, something that people are already doing today in tools like Excel. We've designed it to be simple and generic - you can use the Navigator to visualize your defensive coverage, your red/blue team planning, the frequency of detected techniques, or anything else you want to do_."

the MITRE ATT&CK framework is composed of 14 steps, where each step possesses several techniques which it can be employed.
	- Reconnaissance (TA0043): The adversary is truing to gather information they can use to plan future operations.
	- Resource Development (TA0042): The adversary is trying to establish resources they can use to support operations.
	- Initial Access (TA001): The adversary is trying to get into the your network (initial foothold).
	-  Execution (TA0002): The adversary is trying to run malicious code.
	- Persistence (TA0003): The adversary is trying to maintain their foothold.
	- Privilege Escalation (TA0004): The adversary is trying to gain higher-level permissions.
	- Defense Evasion (TA005): The adversary is trying to avoid being detected.
	- Credential Access (TA0006): The adversary is trying to steal account names and passwords.
	- Discovery (TA0007): The adversary is trying to figure out your environment.
	- Lateral Movement (TA0008):  The adversary is trying to move through your environment.
	- Collection (TA0009): The adversary is trying to gather data of interest to their goal.
	- Command and Control (TA0011): The adversary is trying to communicate with compromised systems to control them.
	- Exfiltration (TA0010): The adversary is trying to steal data.
	- Impact (TA0040): The adversary is trying to manipulate, interrupt or destroy your systems and data.
Inside each one of those steps there are numerous techniques, for example, to gain initial access the adversary might try a phishing campaign. And inside each technique, it is listed software, groups, procedures and mitigations related to it.

**CAR** (Cyber Analytics Repository)

The official definition of **CAR** is "_The MITRE Cyber Analytics Repository (CAR) is a knowledge base of analytics developed by MITRE based on the MITRE ATT&CK_® _adversary model. CAR defines a data model that is leveraged in its pseudocode representations but also includes implementations directly targeted at specific tools (e.g., Splunk, EQL) in its analytics. With respect to coverage, CAR is focused on providing a set of validated and well-explained analytics, in particular with regards to their operating theory and rationale._"

To summarize, CAR is a great place for finding analytics that takes us further than the Mitigation and Detection summaries in the ATT&CK® framework. This tool is not a replacement for ATT&CK® but an added resource.

**MITRE ENGAGE**

Per the website, "_MITRE Engage is a framework for planning and discussing adversary engagement operations that empowers you to engage your adversaries and achieve your cybersecurity goals._"

MITRE Engage is considered an Adversary Engagement Approach.
With Cyber Denial we prevent adversary's ability to conduct their operations.
With Cyber Deception we intentionally plant artifacts to mislead the adversary.

MITRE Engage has its own matrix:
	- **Prepare** the set of operational actions that will lead to your desired outcome(input)
	- **Expose** adversaries when they trigger your deployed deception activities
	- **Affect** adversaries by performing actions that will have a negative impact on their operations
	- **Elicit** information by observing the adversary and learn more about their modus operandi(TTPs)
	- **Understand** the outcomes of the operational actions (output)

**D3FEND**

What is this MITRE resource? Per the [D3FEND](https://d3fend.mitre.org/) website, this resource is "_A knowledge graph of cybersecurity countermeasures._"

D3FEND stands for **D**etection, **D**enial and **D**isruption **F**ramework **E**mpowering **N**etwork **D**efense.

**MITRE ENGENUITY**
Under MITRE ENGENUITY we have
	**CTID**
		Center of Threat-Informed Defense is an organization that consists of various companies and vendors, their objective is to conduct resarch on cyber threats and their TTPs.
		Some of the companies and vendors are: Microsoft, Verizon, Red Canary, Splunk, AttackIQ.
		Per the website, "_Together with Participant organizations, we cultivate solutions for a safer world and advance threat-informed defense with open-source software, methodologies, and frameworks. By expanding upon the MITRE ATT&CK knowledge base, our work expands the global understanding of cyber adversaries and their tradecraft with the public release of data sets critical to better understanding adversarial behavior and their movements._"
		**ATT&CK Emulation Plans.**
		Is a public library making adversary emulations plans a free resource for blue/red teamers. The library and the emulations are a contribution from CTID.
		