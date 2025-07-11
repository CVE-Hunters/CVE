## Cross-Site Scripting (XSS) Reflected endpoint: /intranet/educar_escolaridade_lst.php parameters: descricao

### Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the `/intranet/educar_escolaridade_lst.php` endpoint of the i-educar application. This vulnerability allows attackers to inject malicious scripts in `descricao` parameters.

### Details

Vulnerable Endpoint: `/intranet/educar_escolaridade_lst.php`  
Parameter: `descricao`

The application fails to validate and sanitize user inputs in the `'descricao'`  parameter. This lack of validation permits the injection of malicious payloads, which are reflected back to the user's browser in the server's response and executed within the context of the victim's browser.

### PoC

Payload  
`"><script>alert('XSS-PoC')</script>`

<img width="877" height="800" alt="image" src="https://github.com/user-attachments/assets/382624c4-515e-470f-abff-a3d4df5c22cc" />

### Impact

Reflected cross-site scripting (XSS) attacks can have serious consequences, including:

- User actions: Attackers can perform any action the user can, such as viewing, modifying, or initiating interactions with other users
- Data theft: Attackers can exfiltrate data or install malware on the user's machine
- Account compromise: Attackers can manipulate or steal cookies, or compromise confidential information
- Malicious code: Attackers can execute malicious code on the user's system
- Business reputation damage: Attackers can deface a corporate website or spread misinformation
- Misdirection: Attackers can change the instructions given to users, which can be dangerous if the target is a government website or provides vital resources
