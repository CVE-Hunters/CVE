# Cross-Site Scripting (XSS) Reflected endpoint `educar_usuario_cad.php` parameters `email`, `data_inicial`, `data_expiracao`

---

## Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the `educar_usuario_cad.php` endpoint of the _i-educar_ application. This vulnerability allows attackers to inject malicious scripts into the `email`, `data_inicial`, and `data_expiracao` parameters. The payload is reflected in the application’s HTTP response without proper sanitization, leading to script execution in the victim’s browser.

---

## Details

**Vulnerable Endpoint:** `GET /educar_usuario_cad.php`  
**Parameters:** `email`, `data_inicial`, `data_expiracao`

The application fails to validate and sanitize user input in the `email`, `data_inicial`, and `data_expiracao` parameters. An attacker can craft a malicious URL containing a JavaScript payload that will be reflected back in the response and executed when the victim accesses the link.

---

## PoC

**Payload 1 (email):**

`"><img src=x onerror=alert('XSS-PoC-Email')>`

**Payload 2 (`data_inicial`, and `data_expiracao`):**

`3E%3Cimg%20src%3Dx%20onerror%3Dalert('XSS-PoC3')%3E`

### Steps to Reproduce:

1. Log in to the _i-educar_ application using an account with permissions to create or edit users.

2. Navigate to **Configurações > Permissões > Usuários** and click **"Add"** to create a new user or **"Edit"** to modify an existing one.

3. In the **Email** field insert the payload:
	`"><img src=x onerror=alert('XSS-PoC-Email')>`
	
4. Fill in the remaining required fields and click **Save**.
![[Pasted image 20250810002335.png]]
 
5. The reflected payload is executed immediately in the browser, confirming the XSS vulnerability.

![[Pasted image 20250810002436.png]]

6. To trigger the XSS in the `data_inicial`, and `data_expiracao` the tester must change the fileds directly in de request. And send it to trigger the reflected XSS.

![[Pasted image 20250810004505.png]]

---

## Impact

Reflected XSS vulnerabilities can have severe consequences, including:

- **Session hijacking:** Stealing cookies or session tokens to impersonate users
    
- **Credential theft:** Capturing login credentials via injected scripts
    
- **Malware delivery:** Redirecting victims to malicious downloads or scripts
    
- **Phishing:** Injecting fake login forms or deceptive content
    
- **Reputation damage:** Exploiting trust between users and the application
    
- **Client-side manipulation:** Altering application behavior and content in real time

## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr)

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)