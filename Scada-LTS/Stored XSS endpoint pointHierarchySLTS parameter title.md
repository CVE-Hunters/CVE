Storage Cross-Site Scripting (XSS) in endpoint pointHIerarchySLTS parameter title 

### Summary
Stored Cross-Site Scripting (XSS) vulnerability was identified in the `pointHIerarchySLTS` endpoint. This vulnerability allows attackers to inject malicious scripts into the username parameter. The injected scripts are stored on the server and executed automatically whenever the page pointHIerarchySLTS  is accessed by users, posing a significant security risk.

### Details
- Vulnerable Endpoint: `pointHIerarchySLTS `
- Parameter: `title`
- Payload:` <img src=x onerror=alert('CVEHunters-PoC-XSS')>`

The application fails to properly validate and sanitize user inputs in the `userprofilename` parameter. This lack of validation allows attackers to inject malicious scripts, which are then stored on the server. Whenever the affected page is accessed, the malicious payload is executed in the victim's browser, potentially compromising the user's data and system.

### PoC
Register the payload in the `title` field at the `pointHIerarchySLTS` endpoint. After that, the XSS can be triggered by opening the pointHIerarchySLTS page.


![XSS PoC](/images/xss020.png)


![XSS PoC](/images/xss-021.png)


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


[SCADA-LTS – Official Repository](https://github.com/SCADA-LTS/Scada-LTS)

# Discoverer

[Natan Maia Morette](https://nmmorette.github.io) 

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)

