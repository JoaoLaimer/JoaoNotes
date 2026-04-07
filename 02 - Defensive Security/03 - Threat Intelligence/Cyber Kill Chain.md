Developed by Lockheed Martin, The Cyber Kill Chain framework will help you understand and protect against ransomware attacks, security breaches as well as Advanced Persistent Threats (APTs). You can use the Cyber Kill Chain to assess your network and system security by identifying missing security controls and closing certain security gaps based on your company's infrastructure. 

- **Reconnaissance** is discovering and collecting information.
	OSINT (Open-Source Intelligence).
	The attacker will have a big arsenal of tools available for reconnaissance purposes. Here are some of them:
	- [theHarvester](https://github.com/laramies/theHarvester) - other than gathering emails, this tool is also capable of gathering names, subdomains, IPs, and URLs using multiple public data sources 
	- [Hunter.io](https://hunter.io/) - this is  an email hunting tool that will let you obtain contact information associated with the domain
	- [OSINT Framework](https://osintframework.com/) - OSINT Framework provides the collection of OSINT tools based on various categories
- **Weaponization** is combining malware and exploit into a deliverable payload according to what was found in the reconnaissance phase.
- **Delivery** is when the attacker decides to choose the method for transmitting the payload or malware.
- **Exploitation** is the phase after a successful delivery, gaining access to the system.
- **Installation** is having persistence in the affected system. 
	Can be achieved: Installing a web shell to the webserver, Installing a backdoor, adding the entry to the "run keys".
- **Command and Control** is connecting the infected host to a C2 Server, this is known as C2 Beaconing.
- **Actions On Objectives (Exfiltration)** is when the attacker can finally achieve his goals, meaning it can take action on the original objectives.
	Some objectives might be: Collecting credentials, privilege escalation, internal reconnaissance, exfiltrate sensitive data, deleting data and backups,...

**The Unified Kill Chain**
Some large benefits of the UKC over traditional cybersecurity kill chain frameworks include the fact that it is modern and extremely detailed (**reminder**: it has 18 phases officially, whereas other frameworks may have a small handful)
![[Unified Cyber Kill Chain IMG.png]]