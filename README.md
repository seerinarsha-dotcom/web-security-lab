# web-security-lab
### Lab 01 – SQL Injection Authentication Bypass

* Learned the basics of SQL Injection and authentication bypass.
* Practiced tautology-based SQL injection and SQL comment syntax.
* Explored how incorrect payloads and HTTP 500 errors help with debugging.
* Successfully bypassed login and accessed the `administrator` account.
* Learned that parameterized queries/prepared statements prevent SQL injection.
  
### Lab 02 – SQL Injection in WHERE Clause
* Learned how SQL injection can manipulate WHERE clauses to bypass data filtering.
* Practiced tautology-based SQL injection using OR+1=1 and SQL comments.
* Used URL parameters to inject SQL directly through the browser.
* Successfully retrieved hidden/filtered data from the application.
* Learned that parameterized queries/prepared statements prevent SQL injection.

###### Lab 03 – SQL Injection UNION Attack

* Learned how **UNION-based SQL injection** attacks work.
* Used `UNION+SELECT+NULL` to determine the number of columns returned by the query.
* Practiced intercepting and modifying requests using **Burp Suite Repeater**.
* Successfully determined that the vulnerable query returned **3 columns**.
* Learned why correct column count and **parameterized queries** are important for SQL injection security.
