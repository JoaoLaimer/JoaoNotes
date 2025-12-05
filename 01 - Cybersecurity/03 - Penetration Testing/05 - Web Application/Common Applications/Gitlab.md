## Footprinting & Discovery
The only way to footprint the GitLab version number in use is by browsing to the `/help` page when logged in.
If we cannot register an account, we may have to try a low-risk exploit such as [this](https://www.exploit-db.com/exploits/49821).
## Enumeration
There's not much we can do against GitLab without knowing the version number or being logged in. The first thing we should try is browsing to `/explore` and see if there are any public projects that may contain something interesting.
## Attacking GitLab
## Username Enumeration
We can enumerate user using this tool found [here](https://github.com/dpgg101/GitLabUserEnum).
## Authenticated Remote Code Execution
GitLab Community Edition version 13.10.2 and lower suffered from an authenticated remote code execution [vulnerability](https://hackerone.com/reports/1154542) due to an issue with ExifTool handling metadata in uploaded image files. This issue was fixed by GitLab rather quickly, but some companies are still likely using a vulnerable version. We can use this [exploit](https://www.exploit-db.com/exploits/49951) to achieve RCE.