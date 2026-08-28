# Web Application Security Testing using DVWA

## Overview

This project focuses on practical web application security testing using **Damn Vulnerable Web Application (DVWA)** in a controlled local environment on **Kali Linux**.

DVWA is an intentionally vulnerable web application designed for security education and penetration-testing practice. The project demonstrates common web application vulnerabilities, their security impact, and recommended mitigation techniques.

All testing was performed locally against the authorized DVWA environment.

---

## Objectives

* Understand common web application vulnerabilities.
* Configure DVWA on Kali Linux.
* Perform controlled SQL Injection testing.
* Demonstrate Stored and Reflected Cross-Site Scripting (XSS).
* Demonstrate Cross-Site Request Forgery (CSRF).
* Demonstrate Local File Inclusion (LFI).
* Inspect HTTP security response headers.
* Understand security impacts and appropriate mitigation techniques.
* Gain practical experience in web application security testing.

---

## Environment and Tools

| Component             | Details                      |
| --------------------- | ---------------------------- |
| Operating System      | Kali Linux                   |
| Web Application       | DVWA                         |
| Web Server            | Apache2                      |
| Database              | MariaDB                      |
| Programming Language  | PHP                          |
| Browser               | Firefox                      |
| Security Testing Tool | Burp Suite Community Edition |
| Target                | Localhost (`127.0.0.1`)      |
| DVWA Security Level   | Low                          |

---

## Vulnerabilities Tested

### 1. SQL Injection

SQL Injection occurs when user-supplied input is incorporated into SQL queries without proper validation or parameterization.

A normal input was first tested and then a controlled SQL Injection payload was used:

```text
1' OR '1'='1
```

The application returned multiple records, demonstrating the impact of improper SQL query handling.

**Mitigation:**

* Use prepared statements and parameterized queries.
* Validate user input.
* Apply least-privilege database permissions.
* Avoid exposing detailed database errors.

---

### 2. Stored Cross-Site Scripting (XSS)

Stored XSS occurs when malicious input is permanently stored by an application and later executed in a user's browser.

A controlled JavaScript payload was used:

```html
<script>alert('XSS Test')</script>
```

The payload executed when the stored content was displayed.

**Mitigation:**

* Apply proper output encoding.
* Validate and sanitize user input.
* Use secure templating.
* Implement Content Security Policy (CSP).

---

### 3. Reflected Cross-Site Scripting (XSS)

Reflected XSS occurs when user input is immediately reflected in an application's response without proper encoding or sanitization.

A controlled JavaScript payload was submitted and the application reflected the input, resulting in JavaScript execution.

**Mitigation:**

* Perform server-side input validation.
* Apply context-aware output encoding.
* Sanitize untrusted input.
* Implement Content Security Policy.

---

### 4. Cross-Site Request Forgery (CSRF)

CSRF is a vulnerability where an attacker may cause an authenticated user's browser to perform an unintended state-changing action.

The DVWA CSRF functionality was tested through its password-change operation in the controlled environment.

**Mitigation:**

* Use unpredictable anti-CSRF tokens.
* Validate tokens on state-changing requests.
* Configure appropriate SameSite cookie attributes.
* Validate request origin where appropriate.

---

### 5. Local File Inclusion (LFI)

Local File Inclusion occurs when an application allows user-controlled input to determine a local file that is included or displayed.

The vulnerable `page` parameter was tested using:

```text
/etc/passwd
```

The contents of the local system file were successfully displayed, demonstrating the vulnerability.

**Mitigation:**

* Use strict allowlists for permitted files.
* Never directly trust user-controlled file paths.
* Validate and canonicalize file paths.
* Apply appropriate file-system permissions.

---

### 6. Security Headers

HTTP response headers were inspected using browser developer tools.

Security headers provide browser-level protections against several classes of web attacks.

Important security headers include:

* Content-Security-Policy
* X-Content-Type-Options
* X-Frame-Options
* Strict-Transport-Security
* Referrer-Policy
* Permissions-Policy

Properly configured security headers can reduce risks such as XSS, clickjacking, MIME-type sniffing, and information leakage.

---

## Testing Methodology

The following methodology was followed:

1. Configure the local DVWA environment.
2. Set the DVWA security level to Low for educational testing.
3. Identify the vulnerable functionality.
4. Submit controlled test inputs.
5. Observe the application response.
6. Record the security impact.
7. Identify appropriate mitigation techniques.
8. Capture screenshots as evidence.
9. Document the findings.

---

## Evidence

Screenshots demonstrating the practical work are included in the project documentation.

The evidence covers:

* DVWA configuration
* SQL Injection
* Stored XSS
* Reflected XSS
* CSRF
* Local File Inclusion
* HTTP security headers

---

## Security Recommendations

The following practices are recommended for securing web applications:

* Use prepared statements for database queries.
* Validate and sanitize all user-controlled input.
* Apply context-aware output encoding.
* Implement CSRF protection for state-changing requests.
* Avoid user-controlled file inclusion.
* Use allowlists for permitted resources.
* Configure appropriate HTTP security headers.
* Apply secure cookie attributes.
* Follow the principle of least privilege.
* Perform regular vulnerability assessments.
* Follow secure software development practices.

---

## Ethical and Legal Notice

This project was performed strictly for educational and authorized security testing purposes.

Testing was conducted against a deliberately vulnerable DVWA instance hosted locally on Kali Linux. No unauthorized systems, websites, networks, or third-party applications were targeted.

---

## Conclusion

This project provided practical experience in web application security testing using DVWA. Several common vulnerabilities were demonstrated in a controlled environment, including SQL Injection, Stored XSS, Reflected XSS, CSRF, and Local File Inclusion.

The project also emphasized the importance of secure coding practices, input validation, output encoding, parameterized queries, CSRF protection, secure file handling, and HTTP security headers.

The practical exercises strengthened understanding of web application attack surfaces, vulnerability identification, security impact, and defensive security measures.

---

## Author

**Gandla Amulya**

B.Tech – Cyber Security
Mallareddy Engineering College for Women
