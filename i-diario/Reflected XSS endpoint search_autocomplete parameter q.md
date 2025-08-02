## Cross-Site Scripting (XSS) Reflected endpoint search_autocomplete parameter q

### Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the `/alunos/search_autocomplete` endpoint of the i-diario application. This vulnerability allows attackers to inject malicious scripts in the `q` parameter.

### Details

Vulnerable Endpoint: `/alunos/search_autocomplete`  
Parameter: `q`

The application fails to validate and sanitize user inputs in the `q` parameter. This lack of validation permits the injection of malicious payloads, which are reflected back to the user's browser in the server's response and executed within the context of the victim's browser.

### PoC

Payload  
`"><script>alert('XSS-PoC')</script>`

<img width="861" height="1054" alt="Pasted image 20250701185709" src="https://github.com/user-attachments/assets/571aefdb-7ee5-4745-b99a-78d83f406e98" />


### Impact

Reflected cross-site scripting (XSS) attacks can have serious consequences, including:

- User actions: Attackers can perform any action the user can, such as viewing, modifying, or initiating interactions with other users
- Data theft: Attackers can exfiltrate data or install malware on the user's machine
- Account compromise: Attackers can manipulate or steal cookies, or compromise confidential information
- Malicious code: Attackers can execute malicious code on the user's system
- Business reputation damage: Attackers can deface a corporate website or spread misinformation
- Misdirection: Attackers can change the instructions given to users, which can be dangerous if the target is a government website or provides vital resources
