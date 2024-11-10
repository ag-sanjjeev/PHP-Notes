## &#10162; Security Best Practices:
When comes into web application development, The important thing is providing security to the application and data.

### &#9780; Overview:
1. [Common Web Attacks](#-common-web-attacks),
2. [Protecting Applications](#-protecting-applications)

### &#10022; Common Web Attacks:
- Cross-Site Request Forgery (CSRF): Attackers perform actions on a web application without user knowledge.
- Cross-Site Scripting (XSS): Attackers inject malicious scripts into the web pages, which allows to steal user data or hijack their sessions.
- Session Hijacking: Attackers steal a user session ID to gain unauthorized access to their account.
- SQL Injection: Attackers inject malicious SQL code during form or data submission to manipulate or steal data from a database.

### &#10022; Protecting Applications:
- Input Validation and Sanitization:
Validate all user input as per the requirement of the application logic and Sanitize user input before process that. Use prepared statements and parameterized queries to prevent SQL injection attacks.

- Output Escaping:
Escape output before displaying it by using `htmlspecialchars()` to escape HTML entities and prevent XSS attacks.

- Secure Session Management:
Use strong session IDs by generating strong, random session IDs that unable to predict in default session id generators. And set appropriate session expiration times to reduce the risk of unauthorized access by session hijacking.

- Strong Password Hashing:
Use strong password hashing algorithms to hash passwords securely. And salt passwords by adding a random salt to each password before hashing.

- Secure File Uploads:
Validate file types and sizes to prevent malicious file uploads. Sanitize file names to remove special characters by sanitize file names to prevent security vulnerabilities. And store files in secure locations to avoid storing files in publicly accessible directories on the server.

- Regular Security Audits:
Need to conduct regular security audits to Identify and fix vulnerabilities if exist. Keep software up-to-date and add or install security patches to known vulnerabilities.

---
[&#8682; To Top](#-security-best-practices)

[&#10094; Previous Topic](./mvc-architecture.md) &emsp; [Next Topic &#10095;](./regular-expressions.md)

[&#8962; Goto Home Page](../README.md)