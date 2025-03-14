Splunk is one of the leading [[SIEM]] solutions in the market that provides the ability to collect, analyze and correlate the network and machine logs in real-time.
Splunk has three main components.

**Splunk Forwarder**
Forwarder is a lightweight agent installed on the endpoint intended to be monitored.
It's main task is to collect the data and send it to the Splunk instance.
Some of the key data sources are:

- Web server generating web traffic.
- Windows machine generating Windows Event Logs, PowerShell, and Sysmon data.
- Linux host generating host-centric logs.
- Database generating DB connection requests, responses, and errors.

**Splunk Indexer**
The indexer takes the data, normalize it, determines the datatype, and stores it as events.

**Splunk Head**
The head is the place within the Search & Reporting App where users can search the indexed logs. It also gives the user ability to transform the results into presentable tables, pie-charts, bar-charts and column-charts.

