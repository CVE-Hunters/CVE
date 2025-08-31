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
<img width="1612" height="852" alt="Pasted image 20250810002335" src="https://github.com/user-attachments/assets/bf973ea4-a50e-4ad2-8015-ff6438e77312" />

 
5. The reflected payload is executed immediately in the browser, confirming the XSS vulnerability.

<img width="1222" height="534" alt="Pasted image 20250810002436" src="https://github.com/user-attachments/assets/493874d9-3904-425e-9067-de39d7b9701e" />


6. To trigger the XSS in the `data_inicial`, and `data_expiracao` the tester must change the fileds directly in de request. And send it to trigger the reflected XSS.

<img width="734" height="650" alt="Pasted image 20250810004505" src="https://github.com/user-attachments/assets/63a03974-581e-4853-8ec7-5da02b46b294" />


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
