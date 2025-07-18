# Cross-Site Scripting (XSS) Reflected endpoint `/intranet/pesquisa_pessoa_lst.php` parameters `campo_busca` and `cpf`

---

## Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the `intranet/pesquisa_pessoa_lst.php` endpoint of the _i-educar_ application. This vulnerability allows attackers to inject malicious scripts into the `campo_busca` and `cpf` parameters.

---

## Details

**Vulnerable Endpoint:** `GET /intranet/pesquisa_pessoa_lst.php`  
**Parameters:** `campo_busca`, `cpf`

The application fails to validate and sanitize user inputs in the `campo_busca` and `cpf` parameters. This lack of validation permits the injection of malicious payloads, which are reflected back to the user's browser in the server's response and executed within the context of the victim's browser session.

---

## PoC

Payload:
`%22%3E%3Cscript%3Ealert%28%27XSS-PoC%27%29%3C%2Fscript%3E`
![[Pasted image 20250704010103.png]]


This payload can be injected into either of the two parameters. Example attack URLs:

`/intranet/pesquisa_pessoa_lst.php?campo_busca=%22%3E%3Cscript%3Ealert%28%27XSS-PoC%27%29%3C%2Fscript%3E`

`/intranet/pesquisa_pessoa_lst.php?cpf=%22%3E%3Cscript%3Ealert%28%27XSS-PoC%27%29%3C%2Fscript%3E`

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