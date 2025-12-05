## Bug Bounty Programs
A bug bounty program (also called a vulnerability rewards program - VRP) is continuous and proactive security testing that supplements internal code audits and penetration tests and completes an organization's vulnerability management strategy.
## Bug Bounty Program Types

A bug bounty program can be `private` or `public`.

- `Private bug bounty programs` are not publicly available. Bug bounty hunters can only participate in a private bug bounty program upon receiving specific invitations. The vast majority of bug bounty programs start as private ones and become public after getting the hang of receiving and triaging vulnerability reports.
    
    - Most of the time, bug bounty hunters receive invitations to private bug bounty programs based on their track record, valid finding consistency, and violation record. A representative example of this is how `HackerOne` deals with [invitations](https://docs.hackerone.com/hackers/invitations.html) based on specific criteria. Please note that certain bug bounty programs may even require a background check.
- `Public bug bounty programs` are accessible by the entire hacking community.
    
- [Parent/Child Programs](https://docs.hackerone.com/en/articles/8368957-parent-child-programs) also exist where a bounty pool and a single cyber security team are shared between a parent company and its subsidiaries. If a subsidiary launches a bug bounty program (child program), this program will be linked to the parent one.
    

Something important to note is that the terms `Bug Bounty Program (BBP)` and `Vulnerability Disclosure Program (VDP)` should not be used interchangeably.

A vulnerability disclosure program only provides guidance on how an organization prefers receiving information on identified vulnerabilities by third parties. A bug bounty program incentivizes third parties to discover and report software bugs, and bug bounty hunters receive monetary rewards in return.

If you want to study the anatomy of a vulnerability disclosure program, refer to the following resource. [VDP vs. BBP](https://docs.hackerone.com/organizations/vdp-vs-bbp.html#gatsby-focus-wrapper)

## Bug Bounty Program Code of Conduct
The violation record of a bug bounty hunter is always taken into consideration.
## Bug Bounty Program Structure
| `Vendor Response SLAs`          | Defines when and how the vendor will reply                                                                        |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `Access`                        | Defines how to create or obtain accounts for research purposes                                                    |
| `Eligibility Criteria`          | For example, be the first reporter of a vulnerability to be eligible, etc.                                        |
| `Responsible Disclosure Policy` | Defines disclosure timelines, coordination actions to safely disclose a vulnerability, increase user safety, etc. |
| `Rules of Engagement`           |                                                                                                                   |
| `Scope`                         | In-scope IP Ranges, domains, vulnerabilities, etc.                                                                |
| `Out of Scope`                  | Out-of-scope IP Ranges, domains, vulnerabilities, etc.                                                            |
| `Reporting Format`              |                                                                                                                   |
| `Rewards`                       |                                                                                                                   |
| `Safe Harbor`                   |                                                                                                                   |
| `Legal Terms and Conditions`    |                                                                                                                   |
| `Contact Information`           |                                                                                                                   |
## Writing a Good Report
The essential elements of a good bug report are (the element order can vary):

|   |   |
|---|---|
|`Vulnerability Title`|Including vulnerability type, affected domain/parameter/endpoint, impact etc.|
|`CWE & CVSS score`|For communicating the characteristics and severity of the vulnerability.|
|`Vulnerability Description`|Better understanding of the vulnerability cause.|
|`Proof of Concept (POC)`|Steps to reproduce exploiting the identified vulnerability clearly and concisely.|
|`Impact`|Elaborate more on what an attacker can achieve by fully exploiting the vulnerability. Business impact and maximum damage should be included in the impact statement.|
|`Remediation`|Optional in bug bounty programs, but good to have.|
Readable and well-formatted bug reports can drastically minimize both vulnerability reproduction time and time to triage.
## Using CVSS Calculator

Let us now see how we can use the [CVSS v3.1 Calculator](https://www.first.org/cvss/calculator/3.1) identify the severity of an identified vulnerability.

We will focus on the `Base Score` area only.
#### Attack Vector

Shows how the vulnerability can be exploited.
- `Network (N):` Attackers can only exploit this vulnerability through the network layer (remotely exploitable).
- `Adjacent (A):` Attackers can exploit this vulnerability only if they reside in the same physical or logical network (secure VPN included).
- `Local (L):` Attackers can exploit this vulnerability only by accessing the target system locally (e.g., keyboard, terminal, etc.) or remotely (e.g., SSH) or through user interaction.
- `Physical (P):` Attackers can exploit this vulnerability through physical interaction/manipulation.

#### Attack Complexity

Depicts the conditions beyond the attackers' control and must be present to exploit the vulnerability successfully.
- `Low (L):` No special preparations should take place to exploit the vulnerability successfully. The attackers can exploit the vulnerability repeatedly without any issue.
- `High (H):` Special preparations and information gathering should take place to exploit the vulnerability successfully.

#### Privileges Required

Show the level of privileges the attacker must have to exploit the vulnerability successfully.
- `None (N):` No special access related to settings or files is required to exploit the vulnerability successfully. The vulnerability can be exploited from an unauthorized perspective.
- `Low (L):` Attackers should possess standard user privileges to exploit the vulnerability successfully. The exploitation in this case usually affects files and settings owned by a user or non-sensitive assets.
- `High (H):` Attackers should possess admin-level privileges to exploit the vulnerability successfully. The exploitation in this case usually affects the entire vulnerable system.

#### User Interaction
Shows if attackers can successfully exploit the vulnerability on their own or user interaction is required.
- `None (N):` Attackers can successfully exploit the vulnerability independently.
- `Required (R):` A user should take some action before the attackers can successfully exploit the vulnerability.
#### Scope
Shows if successful exploitation of the vulnerability can affect components other than the affected one.
- `Unchanged (U):` Successful exploitation of the vulnerability affects the vulnerable component or affects resources managed by the same security authority.
- `Changed (C):` Successful exploitation of the vulnerability can affect components other than the affected one or resources beyond the scope of the affected component's security authority.

#### Confidentiality
Shows how much the vulnerable component's confidentiality is affected upon successfully exploiting the vulnerability. Confidentiality limits information access and disclosure to authorized users only and prevents unauthorized users from accessing information.
- `None (N):` The confidentiality of the vulnerable component does not get impacted.
- `Low (L):` The vulnerable component will experience some loss of confidentiality upon successful exploitation of the vulnerability. In this case, the attackers do not have control over what information is obtained.
- `High (H):` The vulnerable component will experience total (or serious) loss of confidentiality upon successfully exploiting the vulnerability. In this case, the attackers have total (or some) control over what information is obtained.
#### Integrity
Shows how much the vulnerable component's integrity is affected upon successfully exploiting the vulnerability. Integrity refers to the trustworthiness and veracity of information.
- `None (N):` The integrity of the vulnerable component does not get impacted.
- `Low (L):` Attackers can modify data in a limited manner on the vulnerable component upon successfully exploiting the vulnerability. Attackers do not have control over the consequence of a modification, and the vulnerable component does not get seriously affected in this case.
- `High (H):` Attackers can modify all or critical data on the vulnerable component upon successfully exploiting the vulnerability. Attackers have control over the consequence of a modification, and the vulnerable component will experience a total loss of integrity.
#### Availability
Shows how much the vulnerable component's availability is affected upon successfully exploiting the vulnerability. Availability refers to the accessibility of information resources in terms of network bandwidth, disk space, processor cycles, etc.
- `None (N):` The availability of the vulnerable component does not get impacted.
- `Low (L):` The vulnerable component will experience some loss of availability upon successfully exploiting the vulnerability. The attacker does not have complete control over the vulnerable component's availability and cannot deny the service to users, and performance is just reduced.
- `High (H):` The vulnerable component will experience total (or severe) availability loss upon successfully exploiting the vulnerability. The attacker has complete (or significant) control over the vulnerable component's availability and can deny the service to users. Performance is significantly reduced.
## Good Report Examples

Find below some good report examples selected by HackerOne:

- [SSRF in Exchange leads to ROOT access in all instances](https://hackerone.com/reports/341876)
- [Remote Code Execution in Slack desktop apps + bonus](https://hackerone.com/reports/783877)
- [Full name of other accounts exposed through NR API Explorer (another workaround of #476958)](https://hackerone.com/reports/520518)
- [A staff member with no permissions can edit Store Customer Email](https://hackerone.com/reports/980511)
- [XSS while logging in using Google](https://hackerone.com/reports/691611)
- [Cross-site Scripting (XSS) on HackerOne careers page](https://hackerone.com/reports/474656)

Please refer to the [Submitting Reports](https://docs.hackerone.com/hackers/submitting-reports.html) section of HackerOne's docs portal for the actual process a bug bounty hunter has to follow to submit a bug report.