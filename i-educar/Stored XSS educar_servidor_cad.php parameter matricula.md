# Cross-Site Scripting (XSS) Stored endpoint `/intranet/educar_servidor_cad.php` parameter `matricula`

---

## Summary

A Stored Cross-Site Scripting (XSS) vulnerability was identified in the `/intranet/educar_servidor_cad.php` endpoint of the _i-educar_ application. This vulnerability allows attackers to inject malicious scripts into the `matricula` parameter. The injected script is stored on the server and executed automatically whenever the affected page is accessed by users, posing a significant security risk.

---

## Details

**Vulnerable Endpoint:** `POST /intranet/educar_servidor_cad.php`  
**Parameter:** `matricula`

The application does not properly validate or sanitize user input in the `matricula` parameter. As a result, an attacker can submit a specially crafted payload that is saved in the system and later executed in the browser of any user who views the content.

---

## PoC

**Encoded Payload:**

`%22%3E%3Csvg+onload%3Dalert%2812%29%3E`

**Decoded Payload:**

`"><svg onload=alert(12)>`

<img width="854" height="673" alt="image" src="https://github.com/user-attachments/assets/31716b07-6983-4555-bfa5-690bc86a8656" />


On /intranet/educar_servidor_det.php?cod_servidor=28915&ref_cod_instituicao=1 page click on "Editar" button.

<img width="1092" height="730" alt="image" src="https://github.com/user-attachments/assets/4bf685cb-8410-45a0-84be-0ba24a2960d2" />


<img width="846" height="354" alt="image" src="https://github.com/user-attachments/assets/a34777ba-9806-4f08-a393-8493a1af1cc9" />


This payload was submitted through the `matricula` field and successfully stored. Upon accessing the affected content, the JavaScript executes immediately in the context of the victim’s browser.

---

## Impact

Stored XSS vulnerabilities can lead to a range of serious consequences, including:

- **Session hijacking:** Stealing cookies or tokens to impersonate users
    
- **Malware delivery:** Inserting scripts that download malicious content
    
- **Credential theft:** Capturing usernames and passwords through fake forms
    
- **Sensitive data exposure:** Accessing protected application data
    
- **Browser takeover:** Running arbitrary commands within the user’s browser session
    
- **Phishing attacks:** Redirecting users to malicious or fake login pages
    
- **Website defacement:** Altering visible content on the platform
    
- **Reputational damage:** Undermining trust in the affected platform

- 

## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr) 

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)
