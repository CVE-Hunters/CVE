# Cross-Site Scripting (XSS) Reflected endpoint `educar_escolaridade_lst.php` parameter `busca`

---

## Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the `educar_escolaridade_lst.php` endpoint of the _i-educar_ application. This vulnerability allows attackers to inject malicious scripts into the `busca` parameter. The payload is reflected in the application’s HTTP response without proper sanitization, leading to immediate execution in the victim’s browser.

---

## Details

**Vulnerable Endpoint:** `GET /educar_escolaridade_lst.php`  
**Parameter:** `busca`

The application fails to properly validate and sanitize user input in the `busca` parameter. An attacker can craft a malicious URL containing a JavaScript payload, which is reflected back in the server’s response and executed when a victim accesses the crafted link.

---

## PoC

**Payload:**

`"><script>alert('XSS-PoC')</script>`

### Steps to Reproduce:

1. Log in to the _i-educar_ application using an account with permissions to access 'Servidores' Menu
    
2. Locate a page or feature that uses the `educar_escolaridade_lst.php` endpoint and processes the `busca` parameter. (Servidores > Cadastros > Tipos > Escolaridade)
	
3. Modify the URL to include the payload above. For example:
    
    `/educar_escolaridade_lst.php?busca="><script>alert('XSS-PoC')</script>`
    
<img width="1276" height="672" alt="Pasted image 20250810014353" src="https://github.com/user-attachments/assets/ea6eba9e-1656-4fa1-a847-93db3ec7ef84" />


4. Load the crafted URL in a browser. The injected script is executed immediately, confirming the presence of the reflected XSS vulnerability.

<img width="1214" height="588" alt="Pasted image 20250810014420" src="https://github.com/user-attachments/assets/e822a678-e7c1-4095-a399-58913d8a6a30" />


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
