
### 📝 Summary

Write the description of your vulnerability

---

### 🔎 Details
Here provide more details such as parameters, endpoint, etc...

➤ Vulnerable Endpoint: `/intranet/public_uf_cad.php`

➤ Parameter: `nome`

➤ Trigger Page: `/intranet/public_uf_lst.php`

<p align="justify">The application fails to properly validate and sanitize user inputs in the <code>nome</code> parameter. This lack of validation allows attackers to inject malicious scripts, which are then stored on the server. Whenever the affected page is accessed, the malicious payload is executed in the victim's browser, potentially compromising the user's data and system.</p>

---

### 📚 PoC

#### ➤ Step by Step:

Show a step-by-step guide on how to trigger the vulnerability

##

#### ➤ Payload:

Provide the payload used in the PoC

##

#### ➤ Screenshots:

Insert images or video of the exploitation.

----

### ⚠️ Impact

##

List the impacts based on OWASP TOP 10.
If unsure, refer to past reports.

---

### 🔗 References

This field should be updated only after CVE publication with the CVE link and VulnDB link

---

### 🕵🏻‍♀️ Finder

*Discovered by [XXX().* 

Add the link to your social networks

##

*Official Member of [CVE-Hunters](https://www.cvehunters.com/)🏹*
