## CVE-2026-####:Stored Cross-Site Scripting (XSS) in new educar_servidor_curso_lst param name

### Summary

A stored Cross-Site Scripting (XSS) vulnerability has been identified in the `educar_servidor_curso_lst.php` endpoint of the I-educar 2.11 application. This vulnerability allows attackers to inject malicious scripts into the `name` parameter. The injected scripts are stored on the server and executed automatically whenever the `ComponenteCurricular/view` page is accessed by users, representing a significant security risk.

### Details
Vulnerable Endpoint: `/intranet/educar_servidor_curso_lst.php `
Parameters: `name`

The application fails to properly validate and sanitize user inputs in the `name` parameters. This lack of validation allows attackers to inject malicious scripts, which are then stored on the server. Whenever the affected page is accessed, the malicious payload is executed in the victim's browser, potentially compromising the user's data and system.

### PoC
Register the payload in the `name` field at the `educar_servidor_curso_lst.php`endpoint. 

![image](/images/xss021.png)
![image](/images/xss022.png)
After that, the XSS can be triggered by opening the `educar_servidor_curso_lst.php endpoint` corresponding to the edited ID.
![image](/images/xss023.png)


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

[CVE-2026-####](https://cve.mitre.org/)

[VulnDB](https://vuldb.com/)

[I-Educar – Official Repository](https://github.com/portabilis/i-educar)

# Discoverer

[Saipe](https://github.com/Saiipe) 

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)

