- **Who**: Which user logs in, runs the command, or downloads the file
- **What**: What exact action or event sequence was performed
- **When**: When exactly did the suspicious activity start and ended
- **Where**: Which device, IP, or website was involved in the alert
- **Why**: The most important W, the reasoning for your final verdict.

| **Alert Report Purpose**       | **Explanation**                                                                                                                                              |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Provide context for escalation | - A well-written report saves lots of time for L2 analysts<br>- Also, it helps them quickly understand what happened                                         |
| Save findings for the records  | - Raw logs are stored for 3-12 months, but alerts are kept indefinitely<br>- As a result, it's better to keep all the context inside the alert, just in case |
| Improve investigation skills   | - If you can't explain it simply, you don't understand it well enough<br>- Report writing is a great way to boost L1 skills by summarising alerts            |

Example:
```
At 13:56 UTC, the user S.Conway (Susan Conway, HR Coordinator) accessed the phishing website freecatvideoshd[.]monster from their LP-HR-009 Windows laptop. At 13:58 UTC, the user downloaded a file from there named cats2025.mp4.exe, likely mistaking it for a legitimate video.

VirusTotal reports confirm that the file is LummaStealer malware, aimed to exfiltrate sensitive data and establish a C2 channel. Further malware actions require deeper investigation, so escalating the alert to L2 and sharing the SIEM findings:

> <SIEM Link>
``` 
- The **Who**: `the user S.Conway (Susan Conway, HR Coordinator)`
- The **What**: `accessed the phishing website freecatvideoshd[.]monster from their LP-HR-009 Windows laptop | the user downloaded a file from there named cats2025.mp4.exe, likely mistaking it for a legitimate video.`
- The **When**: At 13:56 UTC | At 13:58 UTC
- The **Where**: `from their LP-HR-009 Windows laptop`
- The **Why**: `VirusTotal reports confirm that the file is LummaStealer malware, aimed to exfiltrate sensitive data and establish a C2 channel. Further malware actions require deeper investigation, so escalating the alert to L2 and sharing the SIEM findings: > <SIEM Link>` 