# Cross-Site Scripting (XSS) Reflected endpoint `educar_funcao_lst.php` parameter `professor`

---

## Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the `educar_funcao_lst.php` endpoint of the _i-educar_ application. This vulnerability allows attackers to inject malicious scripts into the `professor` parameter. The payload is reflected in the application’s HTTP response without proper sanitization, leading to immediate execution in the victim’s browser.

---

## Details

**Vulnerable Endpoint:** `GET /educar_funcao_lst.php`  
**Parameter:** `professor`

The application fails to properly validate and sanitize user input in the `professor` parameter. An attacker can craft a malicious URL containing a JavaScript payload, which is reflected back in the server’s response and executed when a victim accesses the crafted link.

---

## PoC

**Payload:**

`"><script>alert('XSS-PoC')</script>`

### Steps to Reproduce:

1. Log in to the _i-educar_ application.
    
2. Locate a page or functionality that uses the `educar_funcao_lst.php` endpoint and processes the `professor` parameter. (Servidores > Cadastros > Tipos > Funções)
    
3. Modify the URL to include the payload above. For example:
    
    `/educar_funcao_lst.php?professor="><script>alert('XSS-PoC')</script>`

![[Pasted image 20250810021926.png]]

4. Load the crafted URL in a browser. The injected script is executed immediately, confirming the presence of the reflected XSS vulnerability.

![[Pasted image 20250810021946.png]]


---

## Impact

Reflected XSS vulnerabilities can lead to severe consequences, including:

- **Session hijacking:** Theft of cookies or authentication tokens
    
- **Credential theft:** Capturing sensitive user credentials via injected scripts
    
- **Malware delivery:** Redirecting victims to malicious downloads or exploit pages
    
- **Phishing attacks:** Displaying deceptive forms or content to steal user data
    
- **Reputation damage:** Exploiting trust between the application and its users
    
- **Client-side manipulation:** Altering the application’s content and behavior dynamically


## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr)

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)