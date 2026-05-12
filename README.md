# PostgreSQL Security Analysis & Machine Learning-Based Webshell Detection  
### A Case Study on CVE-2019-9193 and Unix-Domain Socket Exploitation

---

## 1. Project Overview

This project investigates the intersection of database security and system-level attack surfaces in PostgreSQL, focusing on CVE-2019-9193 and Unix-domain socket communication. It combines a machine learning-based webshell detection system with a practical demonstration of PostgreSQL misuse for operating system command execution.

The study highlights how attackers can bypass traditional network monitoring tools by leveraging local inter-process communication (IPC) mechanisms and database-level functionalities.

---

## 2. Objectives

- Analyze PostgreSQL communication mechanisms (TCP vs Unix-domain sockets)
- Demonstrate exploitation of CVE-2019-9193 (`COPY TO/FROM PROGRAM`)
- Show how local database access can be abused for OS command execution
- Build a machine learning model to detect malicious webshells
- Compare different ML models for detection accuracy
- Propose mitigation strategies for database security hardening

---

## 3. Technologies Used

### Database
- PostgreSQL (v12+)

### Programming Language
- Python 3.10+

### Machine Learning Libraries
- NumPy
- Pandas
- Scikit-learn
- XGBoost

### Visualization
- Matplotlib

### Monitoring Tools
- Wireshark
- PostgreSQL logging system

---

## 4. CVE Analysis (CVE-2019-9193)

CVE-2019-9193 is a vulnerability in PostgreSQL that allows users with sufficient privileges to execute operating system commands using the `COPY TO/FROM PROGRAM` feature.

### Key Issue:
If improperly restricted, PostgreSQL allows execution of system-level commands directly from SQL queries.

### Example Exploitation:
```sql
COPY (SELECT 'test') TO PROGRAM 'sh -c "echo hacked > /tmp/output.txt"';
