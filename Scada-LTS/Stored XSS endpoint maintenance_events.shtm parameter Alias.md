# Cross-Site Scripting (XSS) Stored endpoint `maintenance_events.shtm` parameter `Alias`

---

## Summary

A Stored Cross-Site Scripting (XSS) vulnerability was identified in the `maintenance_events.shtm` endpoint of the _SCADA-LTS_ application. This vulnerability allows attackers to inject malicious scripts into the `Alias` parameter. The injected payload is stored on the server and executed automatically in the browser of any user who accesses the affected data source entry, creating a persistent attack vector.

---

## Details

**Vulnerable Endpoint:** `POST /maintenance_events.shtm`  
**Parameter:** `Alias`

The application does not properly validate or sanitize input in the `Alias` field. As a result, an attacker can inject JavaScript code, which is stored in the system and later rendered in the application’s interface, leading to automatic execution in the user's browser.

---

## PoC

**Payload:**

`<img src=x onerror=alert("Maintenance")>`

### Steps to Reproduce:

1. Log in to the _SCADA-LTS_ application with an account that has permission to create or edit maintenance events.
    
2. Navigate to the **Maintenance vents** section and select **Add new event** or edit an existing entry.

![[Pasted image 20250722191532.png]]

1. In the **Alias** field, insert the payload above:
          
    `<img src=x onerror=alert("Maintenance")>`
    
2. Fill in any other required fields and click **Save**.

![[Pasted image 20250722191636.png]]

5. The stored payload is executed immediately in the browser, confirming the Stored XSS vulnerability.
    
    ![[Pasted image 20250722191655.png]]
    
---

## Impact

Stored XSS attacks can lead to severe consequences, including:

- **Session hijacking:** Stealing cookies or authentication tokens to impersonate users
    
- **Credential theft:** Capturing usernames and passwords through malicious scripts
    
- **Malware delivery:** Distributing harmful code to application users
    
- **Privilege escalation:** Compromising higher-privilege accounts via persistent scripts
    
- **Data manipulation or defacement:** Altering displayed content in the application
    
- **Reputation damage:** Eroding trust among system users and stakeholders