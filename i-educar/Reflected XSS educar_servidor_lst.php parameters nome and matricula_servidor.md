# Cross-Site Scripting (XSS) Reflected endpoint `/intranet/educar_servidor_lst.php` parameters `nome` and `matricula_servidor`

---

## Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the `/intranet/educar_servidor_lst.php` endpoint of the _i-educar_ application. This vulnerability allows attackers to inject malicious scripts into the `nome` and `matricula_servidor` parameters.

---

## Details

**Vulnerable Endpoint:** `GET /intranet/educar_servidor_lst.php`  
**Parameters:** `nome`, `matricula_servidor`

The application fails to validate and sanitize user inputs in the `nome` and `matricula_servidor` parameters. This lack of validation permits the injection of malicious payloads, which are reflected back to the user's browser in the server's response and executed within the context of the victim's browser.

---

## PoC

**Payload:**

`"><script>alert('XSS-PoC')</script>`

This payload can be injected into either the `nome` or `matricula_servidor` parameter. For example:


![[Pasted image 20250704003941.png]]

---

## Impact

Reflected cross-site scripting (XSS) attacks can have serious consequences, including:

- **User actions:** Attackers can perform any action the user can, such as viewing, modifying, or initiating interactions with other users
    
- **Data theft:** Attackers can exfiltrate data or install malware on the user's machine
    
- **Account compromise:** Attackers can manipulate or steal cookies, or compromise confidential information
    
- **Malicious code:** Attackers can execute malicious code on the user's system
    
- **Business reputation damage:** Attackers can deface a corporate website or spread misinformation
    
- **Misdirection:** Attackers can change the instructions given to users, which can be dangerous if the target is a government website or provides vital resources

## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr) 

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)