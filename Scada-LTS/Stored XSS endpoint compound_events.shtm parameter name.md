# oss-Site Scripting (XSS) Stored endpoint `compound_events.shtm` parameter `name`

---

## Summary

A Stored Cross-Site Scripting (XSS) vulnerability was identified in the `compound_events.shtm` endpoint of the _SCADA-LTS_ application. This vulnerability allows attackers to inject malicious scripts into the `name` parameter. The injected payload is stored on the server and executed automatically in the browser of any user who accesses the affected compound event entry, creating a persistent attack vector.

---

## Details

**Vulnerable Endpoint:** `POST /compound_events.shtm`  
**Parameter:** `name`

The application does not properly validate or sanitize input in the `name` field. As a result, an attacker can inject JavaScript code, which is stored in the system and later rendered in the application’s interface, causing automatic execution in the user's browser.

---

## PoC

**Payload:**

`<img src=x onerror=alert('Compound-PoC-XSS')>`

### Steps to Reproduce:

1. Log in to the _SCADA-LTS_ application with an account that has permission to create or edit compound events.
    
2. Navigate to the **Compound Events** section and select **Add Compound Event** or edit an existing entry.
    
3. In the **Name** field, insert the payload above:
          
    `<img src=x onerror=alert('Compound-PoC-XSS')>`
    
4. Complete any required fields and click **Save**.
    
![[Pasted image 20250724000222.png]]
    
5. The stored payload is executed immediately in the browser, confirming the Stored XSS vulnerability.

![[Pasted image 20250724000245.png]]
---

## Impact

Stored XSS attacks can lead to severe consequences, including:

- **Session hijacking:** Stealing cookies or authentication tokens to impersonate users
    
- **Credential theft:** Capturing usernames and passwords through malicious scripts
    
- **Malware delivery:** Distributing harmful code to application users
    
- **Privilege escalation:** Compromising higher-privilege accounts via persistent scripts
    
- **Data manipulation or defacement:** Altering displayed content in the application
    
- **Reputation damage:** Eroding trust among system users and stakeholders