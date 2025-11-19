The CGI (Common Gateway Interfaces) Servlet is a vital component of Apache Tomcat that enables web servers to communicate with external applications beyond the Tomcat JVM. These external applications are typically CGI scripts written in languages like Perl, Python, or Bash. The CGI Servlet receives requests from web browsers and forwards them to CGI scripts for processing.
CGI scripts are utilized in websites for several reasons, but there are also some pretty big disadvantages to using them:


| Advantages                                                                                   | Disadvantages                                                              |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| It is simple and effective for generating dynamic web content.                               | Incurs overhead by having to load programs into memory for each request.   |
| Use any programming language that can read from standard input and write to standard output. | Cannot easily cache data in memory between page requests.                  |
| Can reuse existing code and avoid writing new code.                                          | It reduces the server's performance and consumes a lot of processing time. |
## Enumeration
Scan the target using `nmap`, this will help to pinpoint active services currently operating on the system. 
#### Finding a CGI script
One way to uncover web server content is by utilizing the `ffuf` web enumeration tool along with the `dirb common.txt` wordlist.
Knowing that the default directory for CGI scripts is `/cgi`, either through prior knowledge or by researching the vulnerability, we can use the URL `http://10.129.204.227:8080/cgi/FUZZ.cmd` or `http://10.129.204.227:8080/cgi/FUZZ.bat` to perform fuzzing.
## Exploitation
We can exploit `CVE-2019-0232` by appending our own commands through the use of the batch command separator `&`.