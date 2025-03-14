Osquery is an open-source [[Endpoint Security]] agent created by Facebook in 2014. It converts the operating system into a relational database. It allow us to ask questions from the tables using [[SQL]] queries. It is widely used by Security Analysts, Incident Responders, Threat Hunters, etc. Osquery can be installed on multiple platforms:[[Windows]], [[Linux]], [[macOS]] and FreeBSD.

Open terminal and run `osqueryi`.

To understand the tool, run the `.help` command.

**List the tables**: `.tables`
	To list tables with the term *user* in them, use `.tables user`.
**Table schema**: `.schema table_name`
	We can list a table's schema.

You can also view tables information on osquery schema documentation online:
https://osquery.io/schema/5.14.1

The SQL language implemented in Osquery is not an entire SQL language that you might be accustomed to, but rather it's a superset of SQLite.