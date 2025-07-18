# Cross-Site Scripting (XSS) Stored endpoint `/intranet/funcionario_vinculo_cad.php` parameter `nome`

---

## Summary

A Stored Cross-Site Scripting (XSS) vulnerability was identified in the `/intranet/funcionario_vinculo_cad.php` endpoint of the _i-educar_ application. This vulnerability allows attackers to inject malicious scripts into the `nome` parameter. The injected scripts are stored on the server and executed automatically whenever the affected page is accessed by users, posing a significant security risk.

---

## Details

**Vulnerable Endpoint:** `POST /intranet/funcionario_vinculo_cad.php`  
**Parameter:** `nome`

The application fails to properly validate and sanitize user input in the `nome` parameter. This lack of validation allows attackers to inject malicious scripts, which are then stored on the server. Whenever the affected page is accessed, the malicious payload is executed in the victim's browser, potentially compromising the user's data and system.

---

## PoC

**Payload:**

`<script>alert('PoC-XXS2')</script>`



This payload was submitted through the `nome` parameter and persisted in the application's interface. Upon visiting the affected page, the payload is rendered and executed in the browser, confirming the stored XSS vulnerability.

---

## Impact

Stored XSS attacks can have severe consequences, including:

- **Stealing session cookies:** Attackers can hijack user sessions and perform actions on their behalf
    
- **Delivering malware:** Users can be tricked into downloading and executing malicious software
    
- **Hijacking browsers:** Full control over the user’s browser through JavaScript execution
    
- **Credential theft:** Capturing usernames, passwords, and other sensitive information
    
- **Exposing sensitive data:** Accessing data stored in the application or browser
    
- **Website defacement:** Altering the content of web pages viewed by users
    
- **User redirection:** Redirecting victims to phishing or malicious websites
    
- **Damaging business reputation:** Loss of trust if users are affected by attacks originating from the application

## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr) 

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)