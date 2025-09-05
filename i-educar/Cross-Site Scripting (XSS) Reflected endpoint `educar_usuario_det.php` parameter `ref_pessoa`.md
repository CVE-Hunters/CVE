# Cross-Site Scripting (XSS) Reflected endpoint `educar_usuario_det.php` parameter `ref_pessoa`

---

## Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the `educar_usuario_det.php` endpoint of the _i-educar_ application. This vulnerability allows attackers to inject malicious scripts into the `ref_pessoa` parameter. The payload is reflected in the application’s HTTP response without proper sanitization, leading to immediate execution in the victim’s browser.

---

## Details

**Vulnerable Endpoint:** `GET /educar_usuario_det.php`  
**Parameter:** `ref_pessoa`

The application fails to properly validate and sanitize user input in the `ref_pessoa` parameter. An attacker can craft a malicious URL containing a JavaScript payload, which is reflected back in the server’s response and executed when a victim accesses the crafted link.

---

## PoC

**Payload (decoded):**
`';alert(String.fromCharCode(88,83,83))//';alert(String.fromCharCode(88,83,83))//";alert(String.fromCharCode(88,No known CVE></SCRIPT>">'><SCRIPT>alert(String.fromCharCode(88,83,83))</SCRIPT>`
### Steps to Reproduce:

1. Log in to the _i-educar_ application using an account with permissions to create or edit users.
    
2. Identify a location where the `educar_usuario_det.php` endpoint is called with the `ref_pessoa` parameter. (Configurações > Permissões > Usuários)

<img width="1260" height="638" alt="Pasted image 20250810010015" src="https://github.com/user-attachments/assets/40395103-f895-4a7c-82a9-9f9c735a1aad" />


3. Modify the URL to include the payload above. For example:    
        
    `/educar_usuario_det.php?ref_pessoa=';alert(String.fromCharCode(88,83,83))//';alert(String.fromCharCode(88,83,83))//";alert(String.fromCharCode(88,No known CVE></SCRIPT>">'><SCRIPT>alert(String.fromCharCode(88,83,83))</SCRIPT>`

<img width="1478" height="652" alt="Pasted image 20250810010104" src="https://github.com/user-attachments/assets/cce9e5f3-9ff3-4417-b1d3-65557f744296" />


4. Load the crafted URL in a browser. The injected script is executed immediately, confirming the presence of the reflected XSS vulnerability.

<img width="1021" height="565" alt="Pasted image 20250810010126" src="https://github.com/user-attachments/assets/cf590090-c2c6-4520-b4cb-aeaa919649b2" />


---

## Impact

Reflected XSS vulnerabilities can result in severe consequences, including:

- **Session hijacking:** Theft of cookies or authentication tokens
    
- **Credential theft:** Capturing sensitive user credentials via injected scripts
    
- **Malware delivery:** Redirecting victims to malicious downloads or exploit pages
    
- **Phishing attacks:** Displaying deceptive forms or content to steal user data
    
- **Reputation damage:** Exploiting trust between the application and its users
    
- **Client-side manipulation:** Altering the application’s content and behavior dynamically


## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr)

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)
