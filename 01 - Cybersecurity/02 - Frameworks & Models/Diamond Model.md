**The Diamond Model of Intrusion Analysis** was developed by cybersecurity professionals - Sergio Caltagirone, Andrew Pendergast, and Christopher Betz in 2013.

The Diamond Model is composed of four core features: adversary, infrastructure, capability, and victim, and establishes the fundamental atomic element of any intrusion activity.

- **Adversary** is the person who stands behind the cyberattack, can be an actor or organization.
	There is a distinction between adversary operator and adversary customer, this will help understand intent, attribution, adaptability and persistence.
- **Victim** is the adversary target, can be an organization, person, target email address, IP address, domain, etc.
	- Victim Personae are the people and organizations being targeted and whose asstes are being attacked.
	- Victim Assets are the attack surface and include the set of systems, networks, email, hosts, etc., to which the adversary will direct their capabilities.
- **Capability** is the skills, tools, and techniques used by the adversary (TTPs)
	- Capability Capacity is all the vulnerabilities and exposures that it can use.
	- Adversary Arsenal is a set of capabilities that belong to an adversary.
- **Infrastructure** is also known as the software or hardware  that an adversary uses to deliver a capability or maintain control of capabilities.
	- Type 1 Infrastructure: owned by the adversary
	- Type 2 Infrastructure: controlled by an intermediary. Sometimes the intermediary might or might not be aware of it. This is the infrastructure that a victim will see as the adversary
	- Service Providers are organizations that provide services critical for the adversary availability of Type 1 and 2. (ISPs, Domain Registrars, etc).
**Event Meta Features**
Meta-Features can be added to the Diamond Model, they are not required, but add value.
- Timestamp: when the event occured.
- Phase
- Result: can be labeled as "success", "failure", "unknown", and can be related to de CIA triad.
- Direction: host-based and network-based events. Can be seven values: Victim-to-Infrastructure, Infrastructure-to-Victim, Infrastructure-to-Infrastructure, Adversary-to-Infrastructure, Infrastructure-to-Adversary, Bidirectional or Unknown.
- Methodology: general classification of intrusion: DDos, breach, port scan, etc.
- Resources
**Social-Political Component**: financial gain, gaining acceptance in the hacker community, hacktivism, or espionage.
**Technology Component**: relationship between the core features: capability and infrastructure.