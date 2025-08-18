# Broken Access Control – Missing Function-Level Access Control in `/educacenso/consulta` Endpoint

## Summary

A Broken Access Control vulnerability was identified in the `/educacenso/consulta` endpoint of the i-Educar application. This issue allows authenticated users without the required role to access functionalities or data that should be restricted, resulting in an elevation of privilege and unauthorized access.

## Details

**Vulnerable Endpoint:** `GET /educacenso/consulta`  
**Authentication:** Required (but insufficient authorization checks)  
**Role required:** Just app access 
**Affected scenario:** A user without the required role is still able to directly access the endpoint.

The application fails to enforce proper role-based access control (RBAC) on the `/educacenso/consulta` endpoint. As a result, users with lower privilege levels can access sensitive data and functionalities that should be restricted to higher-privileged roles.

## PoC

Request using a session from a user without the Educacenso role:

`GET /educacenso/consulta HTTP/1.1 Host: <target> Cookie: PHPSESSID=<low_privileged_session>`

<img width="1575" height="708" alt="image" src="https://github.com/user-attachments/assets/acb8179e-b4ed-4954-8d8b-5e5f6a14aae5" />


**Observed Result:** The server responds with HTTP 200 and returns restricted content.  
**Expected Result:** The server should respond with HTTP 403 (Forbidden).

## Impact

The impact of this vulnerability depends on the nature of the data and functionality exposed by the Educacenso module, but may include:

- Unauthorized access to sensitive educational census data.
    
- Elevation of privilege from a basic user to roles with access to restricted modules.
    
- Potential manipulation of sensitive data if write operations are accessible.
    
- Breach of confidentiality and integrity of protected information.
    
- Compliance violations if sensitive personal data is exposed to unauthorized users.
    

## Classification

- **OWASP Top 10 (2021):** A01 – Broken Access Control
    
- **CWE:** CWE-285 (Improper Authorization), CWE-862 (Missing Authorization)
    
- **CVSS v4.0 (suggested):** 7.7 (High), depending on whether the endpoint exposes only read access or also allows modification of sensitive data.

CVSS:4.0/AV:N/AC:L/AT:N/PR:L/UI:N/VC:H/VI:L/VA:N/SC:U


## Discoverer

[Marcelo Queiroz](www.linkedin.com/in/marceloqueirozjr)

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)
