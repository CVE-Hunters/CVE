# Broken Object Level Authorization (BOLA) allows enumeration of students via /module/HistoricoEscolar/processamentoApi

### Summary

A Broken Object Level Authorization (BOLA) vulnerability was identified in the `/module/HistoricoEscolar/processamentoApi` endpoint of the **i-Educar** application.  
This flaw allows low-privileged users (e.g., standard student/responsible accounts) to retrieve enrollment (`matriculas`) information of students outside their scope, exposing Personally Identifiable Information (PII) without proper authorization checks.

---

### Details

**Vulnerable Endpoint:**  
`GET /module/HistoricoEscolar/processamentoApi`

The application fails to enforce **object-level authorization** when handling this endpoint. As a result, any authenticated user can manipulate the request values to access sensitive information (names, IDs, enrollment status) of students.

---
### Proof of Concept (PoC)

1. Authenticate as a non-privileged user.

![[Pasted image 20250818200456.png]]

2. Send the following request:

```
GET /module/HistoricoEscolar/processamentoApi?att=matriculas&oper=get&instituicao_id=1&escola_id=4&curso_id=3&serie_id=5&turma_id=23&ano=2025&busca=S HTTP/1.1 
Cookie: i_educar_session=<low-privileged-session>
```

![[Pasted image 20250818201357.png]]

3. We could observe that information about the students were returned.

---

### Impact

This vulnerability exposes **Personally Identifiable Information (PII)** of students, including:

- Names
    
- Class, course, and enrollment status
    
- Institutional relationships
    

**Potential risks include:**

- Unauthorized data harvesting of all students across institutions
    
- Privacy violations (LGPD compliance risk)
    
- Social engineering opportunities by attackers
    
- Reputational damage for the institution
    

**Severity:** High

- Low privileges required
    
- High impact (sensitive data exposure)
    
- Easy to exploit with parameter tampering
    

---
