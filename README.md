PortSwigger Web Security Academy – Lab Notes

Lab 1: SQL Injection – Retrieving Hidden Data

Objective: Retrieve hidden products.

Steps:

1. Open the product category page.
2. Intercept the request in Burp Proxy.
3. Send it to Repeater.
4. Find the "category" parameter.
5. Modify the value:

' OR 1=1--

6. Click Send.
7. Check the response for hidden products.

Key concept: OR-based SQL Injection.

---

Lab 2: SQL Injection – Login Bypass

Objective: Bypass login authentication.

Steps:

1. Open the login page.
2. Enter any username and password.
3. Intercept the POST request using Burp.
4. Send the request to Repeater.
5. Modify the username:

administrator'--

6. Enter any password.
7. Send the request.
8. Check the response and follow the redirect.

Key concept: Commenting out the remaining SQL query.

---

Lab 3: SQL Injection – Database Version on Oracle

Objective: Retrieve Oracle database version information.

Steps:

1. Open the product category page.
2. Intercept the category request.
3. Send it to Repeater.
4. Test the number of columns using "ORDER BY 1", "ORDER BY 2", etc.
5. Use "UNION SELECT" with the Oracle "dual" table.
6. Retrieve the database version string.
7. Check the response.

Key concept: Oracle requires "FROM dual" for this type of SELECT query.

---

Lab 4: SQL Injection – Database Version on MySQL and Microsoft

Objective: Retrieve the database version.

Steps:

1. Open the product category page.
2. Intercept the request.
3. Send it to Repeater.
4. Identify the number of columns.
5. Use a UNION-based SQL injection payload.
6. Retrieve the version using "@@version".
7. Check the response.

Payload used:

' UNION SELECT @@version,NULL-- -

Expected version:

8.0.42-0ubuntu0.20.04.1

Key concept: MySQL database version identification.

---

Common Burp Suite Workflow

1. Open the lab.
2. Browse the target application.
3. Intercept the request in Proxy.
4. Send to Repeater.
5. Modify the vulnerable parameter.
6. Click Send.
7. Analyze the response.
8. Verify the lab status.

Important Terms

- Proxy – Intercept HTTP requests.
- Repeater – Modify and resend requests.
- UNION SELECT – Combine query results.
- ORDER BY – Test column count.
- SQL Comment ("--") – Ignore remaining query text.
- "@@version" – Retrieve MySQL version.
- "dual" – Oracle built-in table.

---

Practice rule: Always verify the response and lab status before marking a lab completed.
