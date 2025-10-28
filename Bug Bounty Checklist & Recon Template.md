# Bug Bounty Checklist & Recon Template
The complete free resource mentioned in the video - everything you need to structure your workflow and turn chaos into strategy.
## 🎯 Pre-Hunt Preparation Checklist
### ✅ Program Research
- [ ] Read program rules completely (twice!)
- [ ] Identify in-scope assets and domains
- [ ] Note out-of-scope restrictions
- [ ] Check forbidden endpoints/actions
- [ ] Understand acceptable testing methods
- [ ] Review past disclosed reports for patterns
- [ ] Join program's communication channels
- [ ] Set up proper testing environment
## ✅ Tool Preparation
- [ ] Burp Suite configured and ready
- [ ] Custom wordlists prepared
- [ ] VPN/proxy setup verified
- [ ] Screenshot tools ready
- [ ] Note-taking system established
- [ ] Backup documentation method ready
---
## 🔍 Systematic Recon Template
### Phase 1: Information Gathering 🕵
#### Subdomain Discovery
- [ ] Certificate transparency logs (crt.sh)
- [ ] DNS brute forcing with quality wordlists
- [ ] Search engine dorking ( site:target.com )
- [ ] GitHub/GitLab repository searches
- [ ] Social media and public documents
- [ ] Third-party service integrations
- [ ] Historical DNS data (SecurityTrails, etc.)
##### Documentation Template:
```
Target: [TARGET_NAME]
Date: [DATE]
Subdomains Found:
- subdomain1.target.com [STATUS_CODE]
- subdomain2.target.com [STATUS_CODE]
Interesting Findings:
-
```
#### Port & Service Enumeration
- [ ] Nmap comprehensive scan
- [ ] Service version identification
- [ ] Banner grabbing
- [ ] SSL/TLS configuration review
- [ ] Uncommon port discovery
- [ ] Service-specific vulnerability checks
##### Documentation Template:
```
Port Scan Results:
- Port 80: HTTP [Server Info]
- Port 443: HTTPS [SSL Details]
- Port 8080: HTTP [Additional Service]
Service Versions:
-
Security Observations:
-
```

### Phase 2: Web Application Analysis 🌐
#### Technology Stack Identification
- [ ] HTTP response headers analysis
- [ ] JavaScript framework detection
- [ ] CMS/platform identification (Wappalyzer)
- [ ] Third-party service integration mapping
- [ ] CDN and hosting provider identification
- [ ] Database technology indicators
##### Technology Stack Template
```
Web Server: [Apache/Nginx/IIS]
Framework: [React/Angular/Vue/PHP/etc.]
CMS: [WordPress/Drupal/Custom]
Database: [MySQL/PostgreSQL/MongoDB]
CDN: [Cloudflare/AWS/etc.]
Security: [WAF detected/Headers present]
Interesting Technologies:
-
```
#### Content Discovery
- [ ] Directory brute forcing (common paths)
- [ ] File extension discovery
- [ ] Backup file hunting (.bak, .old, .tmp)
- [ ] Configuration file searches
- [ ] API endpoint discovery
- [ ] Admin panel location
- [ ] Development/staging environment detection

##### Content Discovery Template
```
Directories Found:
- /admin [STATUS] - [DESCRIPTION]
- /api [STATUS] - [DESCRIPTION]
- /backup [STATUS] - [DESCRIPTION]
Files of Interest:
- /robots.txt - [FINDINGS]
- /sitemap.xml - [ENDPOINTS]
- /.env - [ACCESSIBLE Y/N]
API Endpoints:
- /api/v1/users
- /api/v1/auth
```

### Phase 3: Parameter Discovery 🔗
#### Parameter Enumeration
- [ ] URL parameter discovery
- [ ] POST parameter identification
- [ ] Hidden form field analysis
- [ ] Cookie parameter review
- [ ] Header parameter testing
- [ ] JSON/API parameter mapping
##### Parameter Template:
```
GET Parameters:
- id: [INTEGER] - User/object identifier
- search: [STRING] - Search functionality
- redirect: [URL] - Redirect parameter
POST Parameters:
- username: [STRING]
- password: [STRING]
- csrf_token: [TOKEN]
Interesting Parameters:
- debug: [BOOLEAN] - Debug mode toggle
- admin: [BOOLEAN] - Admin access flag
```
### Phase 4: Vulnerability Assessment 🔓
#### Input Validation Testing
- [ ] Cross-Site Scripting (XSS)
	- [ ] Reflected XSS in parameters
	- [ ] Stored XSS in user inputs
	- [ ] DOM-based XSS
- [ ] SQL Injection
	- [ ] Error-based injection
	- [ ] Boolean-based blind injection
	- [ ] Time-based blind injection
- [ ] Command Injection
- [ ] Path Traversal
- [ ] File Upload vulnerabilities
- [ ] XXE (XML External Entity)
#### Authentication & Session Management
- [ ] Weak password policies
- [ ] Session fixation
- [ ] Session hijacking possibilities
- [ ] Brute force protection
- [ ] Password reset vulnerabilities
- [ ] Multi-factor authentication bypass
### Business Logic Testing
- [ ] Race conditions
- [ ] Price manipulation
- [ ] Privilege escalation
- [ ] Workflow bypass
- [ ] Rate limiting bypass
- [ ] Payment processing flaws
#### Vulnerability Testing Template:
