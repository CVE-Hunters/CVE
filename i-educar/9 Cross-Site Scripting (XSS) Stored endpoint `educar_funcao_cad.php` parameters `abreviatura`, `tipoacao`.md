# Cross-Site Scripting (XSS) Stored endpoint `educar_funcao_cad.php` parameters `abreviatura`, `tipoacao`

---

## Summary

A Stored Cross-Site Scripting (XSS) vulnerability was identified in the `educar_funcao_cad.php` endpoint of the _i-educar_ application. This vulnerability allows attackers to inject malicious scripts into the `abreviatura` and `tipoacao` parameters. The injected payloads are stored on the server and are automatically executed in the browser of any user who accesses the affected function entry, creating a persistent attack vector.

---

## Details

**Vulnerable Endpoint:** `POST /educar_funcao_cad.php`  
**Parameters:** `abreviatura`, `tipoacao`

The application fails to properly validate and sanitize user input in the `abreviatura` and `tipoacao` fields. As a result, attackers can inject arbitrary JavaScript code, which is stored in the system and executed when the affected record is viewed in the application interface.

---

## PoC

**Payload 1:**

`"><svg onload=alert(15888888)>`

**Payload 2:**

`"><script>alert('XSS-PoC')</script>`

### Steps to Reproduce:

1. Log in to the _i-educar_ application using an account with permissions to create or edit function entries.
    
2. Navigate to **Servidores > Cadastros > Tipos > Funções** and click **"Add"** to create a new function or **"Edit"** to modify an existing one.
    
3. In the **Abreviatura** and/or **Tipo Ação** fields (which map to the `abreviatura` and `tipoacao` parameters), insert one of the payloads above.
    
4. Fill in the remaining required fields and click **Save**.

![[Pasted image 20250810021445.png]]    

5. The stored payload is executed immediately in the browser, confirming the Stored XSS vulnerability.
    
    ![[Pasted image 20250810021508.png]]
    
6. To trigger the XSS in the `tipoacao` parameter, the tester must change the fileds directly in de request. And send it to trigger the XSS. This is a reflected XSS.

![[Pasted image 20250810023823.png]]

![[Pasted image 20250810023921.png]]

---

## Impact

Stored XSS vulnerabilities can lead to severe consequences, including:

- **Session hijacking:** Stealing cookies or authentication tokens to impersonate users
    
- **Credential theft:** Capturing usernames and passwords through malicious scripts
    
- **Malware delivery:** Distributing harmful code to legitimate users
    
- **Privilege escalation:** Exploiting administrative accounts via persistent scripts
    
- **Content manipulation:** Altering displayed application data
    
- **Reputation damage:** Eroding trust among system users and stakeholders


## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr)

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)