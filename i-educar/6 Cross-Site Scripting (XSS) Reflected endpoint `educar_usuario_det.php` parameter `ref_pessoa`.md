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

![[Pasted image 20250810010015.png]]

3. Modify the URL to include the payload above. For example:    
        
    `/educar_usuario_det.php?ref_pessoa=';alert(String.fromCharCode(88,83,83))//';alert(String.fromCharCode(88,83,83))//";alert(String.fromCharCode(88,No known CVE></SCRIPT>">'><SCRIPT>alert(String.fromCharCode(88,83,83))</SCRIPT>`

![[Pasted image 20250810010104.png]]

4. Load the crafted URL in a browser. The injected script is executed immediately, confirming the presence of the reflected XSS vulnerability.

![[Pasted image 20250810010126.png]]

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