# Demo Description

This demonstration showcases the abuse of PostgreSQL’s `COPY TO/FROM PROGRAM` feature, related to CVE-2019-9193, to execute operating system–level commands through the database server.

In the video, PostgreSQL is accessed locally through Unix-domain socket communication, allowing command execution without generating visible TCP network traffic. Using SQL queries, a file is created inside the system `/tmp` directory to demonstrate how attackers with database access can leverage PostgreSQL for covert OS command execution and persistence.

The demo highlights:
- Execution of OS commands through PostgreSQL
- Use of `COPY TO/FROM PROGRAM`
- File creation in `/tmp`
- Local Unix socket communication
- Evasion of network-based monitoring tools such as Wireshark

This project is intended strictly for educational and cybersecurity research purposes.