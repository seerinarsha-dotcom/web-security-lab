# Lab 01 – Introduction to Cybersecurity

## Objective

This lab introduced the fundamentals of **web application security**, specifically how **SQL injection** vulnerabilities can be exploited to bypass authentication mechanisms. The goal was to understand how untrusted user input, when concatenated directly into SQL queries, can allow an attacker to manipulate the backend database and gain unauthorized access.

The specific objective of this lab was to **log in as the `administrator` user** without knowing the password, by exploiting a SQL injection vulnerability in the login form.

## What I Learned

- **SQL Injection (SQLi)** — how user-supplied input, if not properly handled, can be injected into SQL queries and alter their logic.
- **Authentication bypass** — using SQL injection to log in as any user (including `administrator`) without knowing the actual password.
- **Tautologies** — how expressions like `OR 1=1` or `OR '1'='1'` can make a SQL `WHERE` clause always evaluate to true, bypassing login checks.
- **SQL comment syntax** — using `--` or `#` to truncate the rest of a query (e.g., to remove the password check from the query).
- **The importance of exact syntax** — closing quotes correctly, spacing around comments, and understanding how the backend query is structured.
- **Debugging through errors** — internal server errors (HTTP 500) can serve as clues that a payload is reaching the database and breaking the query syntax, even when it doesn't yet achieve the goal.
- **Remediation** — the correct fix for SQL injection is to use **parameterized queries / prepared statements**, so user input is never interpolated directly into SQL. Input validation and escaping alone are not sufficient defense.

## Topics Covered

- SQL Injection (authentication bypass)
- Tautology-based SQL injection
- SQL comment syntax (`--`, `#`)
- Interpreting HTTP 500 / internal server errors as debugging clues
- Authentication mechanisms and their weaknesses
- Secure coding practices: parameterized queries / prepared statements

## Practical Work

### Lab Environment

- **Platform:** PortSwigger Web Security Academy (intentionally vulnerable labs)
- **Lab:** SQL injection vulnerability allowing login bypass
- **Difficulty:** Apprentice

### Steps Completed

1. Navigated to the **Web Security Academy dashboard** and selected the **SQL Injection** topic.
2. Launched the lab **"SQL injection vulnerability allowing login bypass"**.
3. Explored the vulnerable **SHOP application**, which included a login page with username and password fields.
4. Experimented with multiple SQL injection payloads to understand how the backend query behaved:

   - `admin'--` → returned "fill the field in password" (password field was required)
   - `'OR '1'='1` → returned "incorrect username or password" (payload did not correctly manipulate the query)
   - `admin' - -` combined with `'OR '1'='1` → returned an **Internal Server Error (HTTP 500)**, indicating the payload was reaching the database and breaking the query syntax — a useful diagnostic clue

5. Iterated on the payload syntax (quote handling, comment spacing, tautology placement) until a successful payload was found.
6. Successfully logged in as the **`administrator`** user without knowing the password.
7. Confirmed completion via the green **"LAB Solved"** badge and "Congratulations" message.

### Final Outcome

The successful payload manipulated the backend SQL query so that the authentication check was bypassed, granting access to the `administrator` account. After logging in, the application displayed an account page (including an "Update email" form), confirming authenticated access.

## Tools Used

| Tool | Purpose |
|---|---|
| PortSwigger Web Security Academy | Intentionally vulnerable web security labs (browser-based, no installation required) |
| Microsoft Edge | Web browser used to access and interact with the labs |


## Key Takeaways

1. **SQL injection is a serious vulnerability** — it can allow an attacker to bypass authentication, access unauthorized data, and in some cases modify or delete data.
2. **Small syntax details matter** — closing quotes, comment spacing, and the structure of the tautology all determined whether a payload failed, errored, or succeeded.
3. **Error messages are useful** — the internal server error was not a dead end; it told me the payload was interacting with the database, which narrowed down the debugging path.
4. **Defense is straightforward** — the root cause is string concatenation in SQL queries. The fix (parameterized queries) is well-established and should be the default in any application that uses a database.
5. **Hands-on practice cements understanding** — reading about SQL injection is different from actually exploiting it in a controlled lab environment and seeing how each payload behaves.


## Conclusion

In this lab, I successfully exploited a **SQL injection vulnerability** to bypass authentication and log in as the `administrator` user without knowing the password. This hands-on exercise built foundational understanding of how SQL injection works, how to debug payloads through trial and error, and why parameterized queries are the correct defense. This lab is the first step in a broader cybersecurity learning path focused on web application security.

---

*Documented as part of the `web-security-lab` repository.*
