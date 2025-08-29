Broken Object Level Authorization (BOLA) Broken Object Level Authorization (BOLA) allows enumeration of classes data via /module/Api/turma
### Summary

A **Broken Object Level Authorization (BOLA)** vulnerability was identified in the `turma` API of the **i-Educar** application. This flaw allows a user without proper permissions to query the endpoint and retrieve ** class information**  by manipulating request parameters.

Although this vulnerability does not directly expose individual student data, it still constitutes an **unauthorized disclosure of academic structure information**, which can be leveraged for enumeration or as a stepping stone for further attacks.

---

### Details

**Vulnerable Endpoint:**  
`GET /module/Api/turma`

The application fails to enforce **object-level authorization** when handling this endpoint. As a result, any authenticated user can manipulate the request values to access data that they shouldn't.

**Expected behavior:**

- Only authorized roles (e.g., administrators, coordinators, teachers linked to the class) should be able to access this data.
    
- Unauthorized users should receive **403 Forbidden** or an empty response.
    

**Observed behavior:**

- Any authenticated user (even low-privilege accounts) can access this endpoint and retrieve sensitive information about academic classes.

---
### Proof of Concept (PoC)

1. Authenticate as a non-privileged user.

![[Pasted image 20250821225155.png]]
![[Pasted image 20250821225232.png]]
2. Send the following request:

```
GET /module/Api/turma?&oper=get&resource=turma&id=14 HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br, zstd
X-Requested-With: XMLHttpRequest
Connection: keep-alive
Referer: http://localhost/intranet/educar_turma_det.php?cod_turma=14
Cookie: i_educar_session=[low-privileged-session]
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin
Priority: u=0

```

![[Pasted image 20250823181900.png]]

3. We could observe that informations about classes were returned.


---

### Impact

- **Information Disclosure:** Even though student data is not included, sensitive details about the institution’s internal structure (classes, courses, schedules) are exposed.
    
- **Reconnaissance Vector:** An attacker could use this endpoint to map out the entire academic structure, identifying valid IDs.
    
- **Chaining attacks:** Combined with other vulnerabilities (e.g., BOLA on enrollment endpoints), this facilitates enumeration and targeted exploitation of student records.
    
- **Compliance Risk:** Exposure of institutional metadata to unauthorized users can still represent a data governance issue.
    

---
