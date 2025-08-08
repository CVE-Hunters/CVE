# Cross-Site Scripting (XSS) Stored endpoint `watch_list.shtm` parameter `name`

---

## Summary

A Stored Cross-Site Scripting (XSS) vulnerability was identified in the `watch_list.shtm` endpoint of the _SCADA-LTS_ application. This vulnerability allows attackers to inject malicious scripts into the `name` parameter. The injected payload is stored on the server and executed automatically in the browser of any user who accesses the affected data source entry, creating a persistent attack vector.

---

## Details

**Vulnerable Endpoint:** `POST /watch_list.shtm`  
**Parameter:** `name`

The application does not properly validate or sanitize input in the `name` field. As a result, an attacker can inject JavaScript code, which is stored in the system and later rendered in the application’s interface, leading to automatic execution in the user's browser.

---

## PoC

**Payload:**

`<img src=x onerror=alert("Watchlist")>`

### Steps to Reproduce:

1. Log in to the _SCADA-LTS_ application with an account that has permission to create or edit Watchlists.
    
2. Navigate to the pencil button on the top right of the application to add/edit a watchlist .
    
3. ClickIn the **Name** field, insert the payload:
          
    `<img src=x onerror=alert("Watchlist")>`
    
4. Fill in any other required fields and click **Save**.

![[Pasted image 20250722183746.png]]

5. The stored payload is executed when the user access the User Profile menu immediately in the browser, confirming the Stored XSS vulnerability.
    
    ![[Pasted image 20250722190626.png]]
    
---

## Impact

Stored XSS attacks can lead to severe consequences, including:

- **Session hijacking:** Stealing cookies or authentication tokens to impersonate users
    
- **Credential theft:** Capturing usernames and passwords through malicious scripts
    
- **Malware delivery:** Distributing harmful code to application users
    
- **Privilege escalation:** Compromising higher-privilege accounts via persistent scripts
    
- **Data manipulation or defacement:** Altering displayed content in the application
    
- **Reputation damage:** Eroding trust among system users and stakeholders

## References

[SCADA-LTS – Official Repository](https://github.com/SCADA-LTS/Scada-LTS)

## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr) 

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)