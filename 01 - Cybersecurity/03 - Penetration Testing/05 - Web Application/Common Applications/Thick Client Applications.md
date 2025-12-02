Thick client applications are the applications that are installed locally on our computers. Unlike thin client applications that run on a remote server and can be accessed through the web browser, these applications do not require internet access to run, and they perform better in processing power, memory, and storage capacity. Thick client applications are usually applications used in enterprise environments created to serve specific purposes. Such applications include project management systems, customer relationship management systems, inventory management tools, and other productivity software. These applications are usually developed using Java, C++, .NET, or Microsoft Silverlight.

Some examples of thick client applications are web browsers, media players, chatting software, and video games. Some thick client applications are usually available to purchase or download for free through their official website or third-party application stores, while other custom applications that have been created for a specific company, can be delivered directly from the IT department that has developed the software.

Some characteristics of thick client applications are:

- Independent software.
- Working without internet access.
- Storing data locally.
- Less secure.
- Consuming more resources.
- More expensive.
Thick client applications can be categorized into two-tier and three-tier architecture. In two-tier architecture, the application is installed locally on the computer and communicates directly with the database. In the three-tier architecture, applications are also installed locally on the computer, but in order to interact with the databases, they first communicate with an application server, usually using the HTTP/HTTPS protocol. In this case, the application server and the database might be located on the same network or over the internet. This is something that makes three-tier architecture more secure since attackers won't be able to communicate directly with the database.
Since a large portion of thick client applications are downloaded from the internet, there is no sufficient way to ensure that users will download the official application, and that raises security concerns. Web-specific vulnerabilities like XSS, CSRF, and Clickjacking, do not apply to thick client applications. However, thick client applications are considered less secure than web applications with many attacks being applicable, including:

- Improper Error Handling.
- Hardcoded sensitive data.
- DLL Hijacking.
- Buffer Overflow.
- SQL Injection.
- Insecure Storage.
- Session Management.