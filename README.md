# 🔐 Web Application Security Testing using DVWA

This project demonstrates practical web application security testing using **DVWA (Damn Vulnerable Web Application)** in a controlled lab environment.

The project includes exploitation and mitigation of common vulnerabilities such as:

- SQL Injection (SQLi)
- Cross-Site Scripting (XSS)
- Cross-Site Request Forgery (CSRF)
- File Inclusion
- Burp Suite Request Interception & Intruder Attack
- Security Headers Configuration

---

# 🎯 Objectives

- Understand common web vulnerabilities
- Perform practical exploitation in DVWA
- Analyze security impact
- Learn mitigation techniques
- Gain hands-on experience with Burp Suite

---

# 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| Kali Linux | Testing Environment |
| DVWA | Vulnerable Web Application |
| Burp Suite | Request Interception & Testing |
| Apache2 | Web Server |
| MySQL/MariaDB | Database |
| Firefox / Burp Browser | Web Testing |

---

# 🔍 Vulnerabilities Demonstrated

---

## 1️⃣ SQL Injection (SQLi)

### Payload Used

```sql
1' OR '1'='1
```

<img width="1919" height="884" alt="Screenshot 2026-04-26 230859" src="https://github.com/user-attachments/assets/7b27aa9b-06e7-48a6-9a5f-4e6c4864d983" />

---
### Data Extraction Payload

```sql
1' UNION SELECT user, password FROM users#
```

<img width="1915" height="881" alt="Screenshot 2026-04-26 230843" src="https://github.com/user-attachments/assets/6c5b044d-0eb0-46c9-872e-5d30060e4b00" />

---
### Description

SQL Injection occurs when user input is directly inserted into SQL queries without proper sanitization.

### Impact

- Authentication bypass
- Database disclosure
- Unauthorized access

---

## 2️⃣ Cross-Site Scripting (XSS)

### Stored XSS Payload

```html
<script>alert('XSS')</script>
```

<img width="1908" height="752" alt="image" src="https://github.com/user-attachments/assets/15f148cf-5e6f-46dd-a6ba-6e5d96870f3b" />

---

### Reflected XSS Payload

```html
<script>alert('Reflected XSS')</script>
```

<img width="1916" height="868" alt="image" src="https://github.com/user-attachments/assets/1d26f94b-e024-437c-98f4-f378302df145" />

---

### Description

XSS allows attackers to inject malicious scripts into webpages viewed by other users.

### Impact

- Session hijacking
- Cookie theft
- Malicious redirects

---

## 3️⃣ Cross-Site Request Forgery (CSRF)

### Malicious HTML Payload

```html
<script>
window.location="http://localhost/dvwa/vulnerabilities/csrf/?password_new=password123&password_conf=password123&Change=Change";
</script>
```

<img width="898" height="766" alt="image" src="https://github.com/user-attachments/assets/a4853be0-be8d-4c05-853d-58430b32ec27" />

---

### Description

CSRF forces authenticated users to perform actions without their consent.

### Impact

- Unauthorized password changes
- Account compromise

---

## 4️⃣ File Inclusion (LFI)

### Payload Used

```text
?page=../../../../etc/passwd
```

<img width="1916" height="838" alt="image" src="https://github.com/user-attachments/assets/8e9fcc6f-23cd-4def-980d-eef9249c4b1b" />

---
### Description

Local File Inclusion allows attackers to access sensitive server files using directory traversal.

### Impact

- Sensitive file disclosure
- Information leakage

---

## 5️⃣ Burp Suite Interception & Intruder

### Description

Burp Suite was used to:
- Intercept HTTP requests
- Modify requests
- Perform brute-force testing using Intruder

<img width="1918" height="915" alt="image" src="https://github.com/user-attachments/assets/7c6b5ca5-eb5e-455e-8d70-71d7f5059a1b" />

---

## 6️⃣ Security Headers Configuration

### Apache Security Headers Added

```apache
Header set X-Content-Type-Options "nosniff"
Header set X-Frame-Options "DENY"
Header set X-XSS-Protection "1; mode=block"
```

<img width="1077" height="712" alt="image" src="https://github.com/user-attachments/assets/2a49ea87-8507-4adf-9837-99135ae24e2e" />

---

### Description

Security headers help mitigate browser-based attacks such as:
- Clickjacking
- MIME sniffing
- Cross-Site Scripting

---

# 🛡️ Mitigation Techniques

| Vulnerability | Mitigation |
|---|---|
| SQL Injection | Prepared Statements, Parameterized Queries |
| XSS | Input Sanitization, Output Encoding, CSP |
| CSRF | CSRF Tokens, SameSite Cookies |
| File Inclusion | Validate File Paths, Restrict Includes |
| Brute Force | Rate Limiting, MFA |
| Clickjacking | X-Frame-Options Header |

---

# 📌 Conclusion

This project demonstrates how insecure coding practices can introduce serious web vulnerabilities. Proper input validation, secure session handling, and defensive security controls are essential for building secure web applications.

---
