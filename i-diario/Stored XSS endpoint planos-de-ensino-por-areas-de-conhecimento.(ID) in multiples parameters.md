## Cross-Site Scripting (XSS) Stored endpoint '/planos-de-ensino-por-areas-de-conhecimento/[ID]' in multiples parameters

### Summary

A Stored Cross-Site Scripting (XSS) vulnerability was identified in the `/planos-de-ensino-por-areas-de-conhecimento[ID]` endpoint of the i-diario application. This vulnerability allows attackers to inject malicious scripts into `multiples parameters`. The injected scripts are stored on the server and executed automatically whenever the affected page is accessed by users, posing a significant security risk.

### Details

Vulnerable Endpoint: `POST /planos-de-ensino-por-areas-de-conhecimento[ID] `  
Parameter: `Parecer, Conteúdos, Objetivos`

The application fails to properly validate and sanitize user inputs in the `Parecer, Conteúdos, Objetivos` parameters. This lack of validation allows attackers to inject malicious scripts, which are then stored on the server. Whenever the affected page is accessed, the malicious payload is executed in the victim's browser, potentially compromising the user's data and system.

### PoC

Payload: `"><script>alert('XSS-PoC')</script>`

1 - Insert the payload in the Parecer parameter.
2 - Save it
3 - Go to the option "Histórico"

![[Pasted image 20250702011855.png]]

The result:
![[Pasted image 20250702012009.png]]

### Impact

- Stealing session cookies: Attackers can use stolen session cookies to hijack a user's session and perform actions on their behalf.
- Downloading malware: Attackers can trick users into downloading and installing malware on their computers.
- Hijacking browsers: Attackers can hijack a user's browser or deliver browser-based exploits.
- Stealing credentials: Attackers can steal a user's credentials.
- Obtaining sensitive information: Attackers can obtain sensitive information stored in a user's account or in their browser.
- Defacing websites: Attackers can deface a website by altering its content.
- Misdirecting users: Attackers can change the instructions given to users who visit the target website, misdirecting their behavior.
- Damaging a business's reputation: Attackers can damage a business's image or spread misinformation by defacing a corporate website.

# References

[i-diario – Official Repository](https://github.com/portabilis/i-diario)

## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr) 

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)