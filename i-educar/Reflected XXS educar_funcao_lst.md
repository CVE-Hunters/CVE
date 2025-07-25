# Cross-Site Scripting (XSS) Reflected /intranet/educar_funcao_lst.php parameters nm_funcao and abreviatura

### Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the `/intranet/educar_funcao_lst.php` endpoint of the i-educar application. This vulnerability allows attackers to inject malicious scripts in `nm_funcao` parameters.

### Details

Vulnerable Endpoint: `/intranet/educar_funcao_lst.php`  
Parameter: `nm_funcao`

The application fails to validate and sanitize user inputs in the `'nm_funcao' and 'abreviatura` parameter. This lack of validation permits the injection of malicious payloads, which are reflected back to the user's browser in the server's response and executed within the context of the victim's browser.

### PoC

Payload  
`"><script>alert('XSS-PoC')</script>`

<img width="963" height="838" alt="image" src="https://github.com/user-attachments/assets/876a5ffd-40fc-46b8-9803-34d247f850be" />

The same issue happens to "abreviatura" parameter.
### Impact

Reflected cross-site scripting (XSS) attacks can have serious consequences, including:

- User actions: Attackers can perform any action the user can, such as viewing, modifying, or initiating interactions with other users
- Data theft: Attackers can exfiltrate data or install malware on the user's machine
- Account compromise: Attackers can manipulate or steal cookies, or compromise confidential information
- Malicious code: Attackers can execute malicious code on the user's system
- Business reputation damage: Attackers can deface a corporate website or spread misinformation
- Misdirection: Attackers can change the instructions given to users, which can be dangerous if the target is a government website or provides vital resources

### Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr) 

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)

