# Cross-Site Scripting (XSS) Stored endpoint `/usuarios/tipos/(ID)` parameters `"Tipos de Usuário"`, `"Descrição"`

---

## Summary

A Stored Cross-Site Scripting (XSS) vulnerability was identified in the `/usuarios/tipos/(ID)` endpoint of the _i-educar_ application. This vulnerability allows attackers to inject malicious scripts into the **"Tipos de Usuário"** and **"Descrição"** fields. The injected payload is stored on the server and is automatically executed in the browser of any user who accesses the affected user type entry, creating a persistent attack vector.

---

## Details

App: i-educar v 2.10
**Vulnerable Endpoint:** `POST /usuarios/tipos/(ID)`  
**Parameters:** `"Tipos de Usuário"`, `"Descrição"`

The application fails to properly validate and sanitize user input in the `"Tipos de Usuário"` and `"Descrição"` fields. As a result, attackers can inject arbitrary JavaScript code which is stored in the database and executed when the stored content is viewed through the application’s interface.

---

## PoC

**Payload:**

`"><script>alert('XSS-PoC-Tipo')</script>`

### Steps to Reproduce:

1. Log in to the _i-educar_ application using an account with permissions to create or edit user types.
    
2. Navigate to **Configurações > Permissões > Tipos de Usuário** and click **"Edit"** on an existing user type or **"Add"** to create a new one.
    
3. In the **"Tipos de Usuário"** and/or **"Descrição"** fields, insert the payload above:
          
    `"><script>alert('XSS-PoC-Tipo')</script>`

<img width="1179" height="801" alt="Pasted image 20250809201533" src="https://github.com/user-attachments/assets/9618089c-5f27-48b3-a436-fde691ea07ba" />


4. Click **Save**.
    
       
5. The stored payload is executed immediately in the browser, confirming the Stored XSS vulnerability.

<img width="968" height="556" alt="Pasted image 20250809201623" src="https://github.com/user-attachments/assets/e7bbacf8-bf6f-4b1f-b49e-15540bedb09a" />



---

## Impact

Stored XSS vulnerabilities can lead to:

- **Session hijacking:** Stealing cookies or authentication tokens to impersonate users
    
- **Credential theft:** Capturing usernames and passwords through injected scripts
    
- **Malware delivery:** Serving malicious code to application users
    
- **Privilege escalation:** Exploiting admin accounts via persistent scripts
    
- **Content manipulation:** Altering displayed application data
    
- **Reputation damage:** Eroding trust among users and stakeholders


## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr)

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)
