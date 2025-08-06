Redline is a [[Digital Forensics]] tools that will essentially give an analyst a 30,000-foot view (10 kilometers high view) of a Windows, Linux, or macOS endpoint. Using Redline, you can analyze a potentially compromised endpoint through the memory dump, including various file structures.
Here is what you can do using Redline:

- Collect registry data (Windows hosts only)
- Collect running processes
- Collect memory images (before Windows 10)
- Collect Browser History
- Look for suspicious strings


There are three ways or options to collect data using Redline:

1. Standard Collector - this method configures the script to gather a minimum amount of data for the analysis. This is going to be our preferred method to collect data in this room. It is also usually the fastest method to collect the data you need. It takes only a few minutes to complete.
2. Comprehensive Collector - this method configures the script to gather the most data from your host for further analysis. This method takes up to an hour or more. You will choose this method if you prefer the full analysis of the system.
3. IOC Search Collector (Windows only) - this method collects data that matches with the [Indicators of Compromise (IOCs)](https://www.crowdstrike.com/cybersecurity-101/indicators-of-compromise/) that you created with the help of [IOC Editor](https://fireeye.market/apps/S7cWpi9W). You will choose this method if you want to run the data collection against known IOCs that you have gathered either through threat intelligence (data feed or narrative report), incident response, or malware analysis. You imported them into [IOC Editor](https://fireeye.market/apps/S7cWpi9W).

IOC stands for **Indicators of Compromise**; they are artifacts of the potential compromise and host intrusion on the system or network that you need to look for when conducting threat hunting or performing incident response. IOCs can be MD5, SHA1, SHA256 hashes, IP address, C2 domain, file size, filename, file path, a registry key, etc.

One of the great tools you can use is [IOC Editor,](https://fireeye.market/apps/S7cWpi9W) created by FireEye, to create IOC files. You can refer to this link to learn how to use the IOC Editor: [https://fireeye.market/assets/apps/S7cWpi9W//9cb9857f/ug-ioc-editor.pdf](https://fireeye.market/assets/apps/S7cWpi9W//9cb9857f/ug-ioc-editor.pdf). 

**Note**: According to the [IOC Editor](https://fireeye.market/apps/S7cWpi9W) download page Windows 7 is the latest operating system officially supported. It is the same version installed in the attached VM. There is another tool called [OpenIOC Editor](https://fireeye.market/apps/211404) by FireEye, which supports Windows 10 that is worth taking a look at.

