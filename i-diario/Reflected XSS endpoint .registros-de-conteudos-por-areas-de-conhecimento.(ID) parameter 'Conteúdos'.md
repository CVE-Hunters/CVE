# Cross-Site Scripting (XSS) Reflected endpoint  /registros-de-conteudos-por-areas-de-conhecimento/[ID] parameter 'Conteúdos'

### Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the `/registros-de-conteudos-por-areas-de-conhecimento/[ID]` endpoint of the i-diario application. This vulnerability allows attackers to inject malicious scripts in `'Conteúdos'` parameter.

### Details

Vulnerable Endpoint: `/registros-de-conteudos-por-areas-de-conhecimento/[ID]`  
Parameter: `'Conteúdos'`

The application fails to validate and sanitize user inputs in the `'Conteúdos'` parameter. This lack of validation permits the injection of malicious payloads, which are reflected back to the user's browser in the server's response and executed within the context of the victim's browser.

### PoC

Payload  
`<script>alert('PoC-XXS3')</script>`

![[Pasted image 20250702161303.png]]

### Impact

Reflected cross-site scripting (XSS) attacks can have serious consequences, including:

- User actions: Attackers can perform any action the user can, such as viewing, modifying, or initiating interactions with other users
- Data theft: Attackers can exfiltrate data or install malware on the user's machine
- Account compromise: Attackers can manipulate or steal cookies, or compromise confidential information
- Malicious code: Attackers can execute malicious code on the user's system
- Business reputation damage: Attackers can deface a corporate website or spread misinformation
- Misdirection: Attackers can change the instructions given to users, which can be dangerous if the target is a government website or provides vital resources

# References

[i-diario – Official Repository](https://github.com/portabilis/i-diario)

## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr) 

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)