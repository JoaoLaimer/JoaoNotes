The goal here is that we test what an attacker could do within the entire network. After all, the main goal is not only to successfully exploit a publicly available system but also to get sensitive data or find all ways that an attacker could render the network unusable.
In this stage, we want to test how far we can move manually in the entire network and what vulnerabilities we can find from the internal perspective that might be exploited. In doing so, we will again run through several phases:
1. Pivoting
2. Evasive Testing
3. Information Gathering
4. Vulnerability Assessment
5. (Privilege) Exploitation
6. Post-Exploitation
## Pivoting

In most cases, the system we use will not have the tools to enumerate the internal network efficiently. Some techniques allow us to use the exploited host as a proxy and perform all the scans from our attack machine or VM. In doing so, the exploited system represents and routes all our network requests sent from our attack machine to the internal network and its network components.

In this way, we make sure that non-routable networks (and therefore publicly unreachable) can still be reached. This allows us to scan them for vulnerabilities and penetrate deeper into the network. This process is also known as `Pivoting` or `Tunneling`.

## Evasive Testing

Also, at this stage, we should consider whether evasive testing is part of the assessment scope. There are different procedures for each tactic, which support us in disguising these requests to not trigger an internal alarm among the administrators and the blue team.

There are many ways to protect against lateral movement, including network (micro) `segmentation`, `threat monitoring`, `IPS`/`IDS`, `EDR`, etc. To bypass these efficiently, we need to understand how they work and what they respond to. Then we can adapt and apply methods and strategies that help avoid detection.
## Information Gathering

Before we target the internal network, we must first get an `overview` of which systems and how many can be reached from our system. This information may already be available to us from the last post-exploitation stage, where we took a closer look at the settings and configurations of the system.
## Vulnerability Assessment

Vulnerability assessment from the inside of the network differs from the previous procedures. This is because far more errors occur inside a network than on hosts and servers exposed to the Internet. Here, the `groups` to which one has been assigned and the `rights` to different system components play an essential role. In addition, it is common for users to share information and documents and work on them together.

This type of information is of particular interest to us when planning our attacks.

## (Privilege) Exploitation

Once we have found and prioritized these paths, we can jump to the step where we use these to access the other systems. We often find ways to crack passwords and hashes and gain higher privileges. Another standard method is to use our existing credentials on other systems. There will also be situations where we do not even have to crack the hashes but can use them directly.

## Post-Exploitation

Once we have reached one or more hosts or servers, we go through the steps of the post-exploitation stage again for each system. Here we again collect system information, data from created users, and business information that can be presented as evidence. However, we must again consider how this different information must be handled and the rules defined around sensitive data in the contract.