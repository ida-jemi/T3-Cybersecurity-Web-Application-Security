# 📝 Attack Scenarios & Mitigation Notes

---

| Vulnerability | Payload / Attack | Observation | Risks | Prevention |
|---|---|---|---|---|
| **SQL Injection (SQLi)** | ```sql 1' OR '1'='1 ``` | SQL query manipulated and database records displayed | Authentication bypass, data leakage | Prepared statements, parameterized queries, input validation |
| **SQL Injection (Data Extraction)** | ```sql 1' UNION SELECT user, password FROM users# ``` | Usernames and password hashes extracted | Unauthorized database access | Use secure database queries |
| **Stored XSS** | ```html <script>alert('XSS')</script> ``` | Script stored and executed whenever page loads | Cookie theft, session hijacking | Input sanitization, output encoding |
| **Reflected XSS** | ```html <script>alert('Reflected XSS')</script> ``` | Script executed immediately in browser | Malicious redirects, browser manipulation | CSP headers, escape special characters |
| **CSRF** | ```html <script> window.location="http://localhost/dvwa/vulnerabilities/csrf/?password_new=password123&password_conf=password123&Change=Change"; </script> ``` | Password changed without user consent | Unauthorized account actions | CSRF tokens, SameSite cookies, POST requests |
| **File Inclusion (LFI)** | ```text ?page=../../../../etc/passwd ``` | Sensitive system files became accessible | Information disclosure, server reconnaissance | Validate file paths, restrict includes |
| **Burp Suite Interception** | Captured and modified HTTP requests | Requests intercepted successfully | Request tampering | HTTPS, input validation |
| **Burp Intruder Attack** | Automated password attempts using payload list | Different responses identified valid credentials | Brute-force attacks | MFA, rate limiting, account lockout |
| **Security Headers** | ```apache Header set X-Content-Type-Options "nosniff" Header set X-Frame-Options "DENY" Header set X-XSS-Protection "1; mode=block" ``` | Browser protections enabled | Clickjacking, MIME sniffing, XSS risks | Configure secure HTTP headers |

---

# 📌 Quick Security Concepts

| Concept | Meaning |
|---|---|
| **Prepared Statements** | Separate SQL query from user input |
| **Input Validation** | Reject malicious or unexpected input |
| **Output Encoding** | Prevent browser from executing scripts |
| **CSRF Token** | Unique token to verify valid requests |
| **CSP (Content Security Policy)** | Restricts malicious script execution |
| **SameSite Cookies** | Prevents cross-site request abuse |
| **MFA** | Adds extra authentication layer |
| **Rate Limiting** | Restricts repeated login attempts |

---

# 🎯 Key Learning Outcomes

| Topic | Learning |
|---|---|
| SQL Injection | Unsanitized SQL queries are dangerous |
| XSS | Browser-executed scripts can compromise users |
| CSRF | Authenticated sessions can be abused |
| File Inclusion | Improper file handling leaks data |
| Burp Suite | HTTP traffic can be intercepted and manipulated |
| Security Headers | Browser protections reduce attack surface |
