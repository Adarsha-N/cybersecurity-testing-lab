# Week 4 – Module 1: Mediroza Reconnaissance

## Overview

This module documents reconnaissance and authentication-surface assessment performed against the authorized Mediroza General Hospital training environment.

**Target:** `https://medirozahospital.com`

**Module:** Week 4 – Module 1
**Assessment Type:** Authorized security testing

---

## Objectives

The objectives of this module were:

* Identify technologies used by the web application.
* Identify interesting application paths.
* Analyze the patient authentication interface.
* Identify protected patient endpoints.
* Review session-cookie attributes.
* Review HTTP security headers.
* Test application responses to malformed input.
* Document security observations and supporting evidence.

---

## Tools Used

* Kali Linux
* curl
* grep
* WhatWeb
* wafw00f
* nslookup
* Git
* GitHub

---

## 1. Technology Discovery

The following technologies were identified during reconnaissance:

* Web Server: LiteSpeed
* PHP: 8.2.33
* CMS: Mediroza CMS 1.4.2
* WAF: LiteSpeed WAF

Evidence:

```text
01-http-headers.txt
02-dns.txt
03-whatweb.txt
04-waf.txt
```

---

## 2. Interesting Application Paths

The following paths were identified:

```text
/patient/
/staff/
/old/
/patient/reports/
```

Evidence:

```text
08-old-directory.html
09-staff-login.html
09-staff-directory.html
10-patient-directory.html
12-reports-directory.html
```

---

## 3. Patient Authentication

The patient login endpoint was identified as:

```text
POST /patient/login.php
```

Parameters:

```text
username
password
```

The login form did not contain a visible CSRF token.

Evidence:

```text
14-patient-login-form.txt
21-login-form-analysis.txt
```

---

## 4. Invalid Login Testing

An invalid test account was submitted to the patient login endpoint.

Observed response:

```text
HTTP 200
Username not found
```

The distinct response may indicate potential username enumeration.

This was not fully confirmed because an authorized valid test account was not available.

Evidence:

```text
16-invalid-login-response.txt
17-login-test-summary.txt
```

---

## 5. Protected Endpoints

The following endpoints were tested without an authenticated session:

```text
/patient/portal.php
/patient/download.php
/patient/logout.php
```

The application redirected requests to:

```text
login.php
```

Observed status:

```text
HTTP 302
```

Evidence:

```text
14-portal-headers.txt
15-download-headers.txt
18-logout-headers.txt
```

Session invalidation could not be independently verified because an authenticated test session was unavailable.

---

## 6. Session Cookie Review

The application issued:

```text
PHPSESSID
```

The following attribute was observed:

```text
Secure
```

The following attributes were not observed:

```text
HttpOnly
SameSite
```

Evidence:

```text
19-patient-security-headers.txt
20-security-header-summary.txt
```

These observations represent security-hardening considerations and do not by themselves establish exploitability.

---

## 7. Security Header Review

Observed:

```text
X-Powered-By: PHP/8.2.33
Server: LiteSpeed
```

The following common security headers were not observed:

```text
Content-Security-Policy
Strict-Transport-Security
X-Frame-Options
X-Content-Type-Options
Referrer-Policy
Permissions-Policy
```

These observations should be treated as configuration findings rather than confirmed vulnerabilities.

---

## 8. SQL Input Testing

A malformed single-quote input supplied to the username parameter produced a MySQL `mysqli_query()` SQL syntax error.

Evidence:

```text
22-input-test-results.txt
23-sqli-error-evidence.txt
```

The result demonstrates that malformed user-controlled input reaches database-related processing and that database error information can be exposed to the client.

---

## 9. Boolean Testing

Boolean comparison tests were performed.

### FALSE condition

```text
Username not found
HTTP 200
Size: 2281 bytes
```

### TRUE condition

```text
Username not found
HTTP 200
Size: 2281 bytes
```

The responses were identical.

Therefore:

* Boolean-based SQL injection was not demonstrated.
* Authentication bypass was not demonstrated.
* No data extraction was performed.

Evidence:

```text
24-sqli-false.html
25-sqli-true.html
26-sqli-auth-test.txt
27-sqli-assessment.txt
29-sqli-final-assessment.txt
```

---

## 10. Security Observations

The module identified:

1. Technology disclosure.
2. Potential username enumeration.
3. No visible CSRF token in the patient login form.
4. Missing common security headers.
5. Session-cookie attribute observations.
6. SQL error disclosure.

---

## 11. Limitations

The following were not established:

* Authentication bypass.
* Boolean-based SQL injection.
* Unauthorized patient-record access.
* Patient data extraction.
* Session invalidation behavior using an authenticated account.

Testing was limited to the authorized assessment scope.

---

## 12. Evidence

The `recon/` directory contains the original reconnaissance artifacts.

The `evidence/` directory contains the later authentication and input-testing evidence.

The `screenshots/` directory contains visual evidence of the main reconnaissance activities.

---

## Conclusion

Week 4 Module 1 established the external application surface and documented authentication-related security observations.

The most significant observation from the input-testing phase was the disclosure of a MySQL database error when malformed input was supplied to the patient login username parameter.

The TRUE/FALSE tests did not demonstrate Boolean SQL injection, and authentication bypass was not established.

No unauthorized patient-record access or data extraction was performed.
