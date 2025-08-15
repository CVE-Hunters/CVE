# 📤 Mini Tutorial – Submitting a Vulnerability to Fluid Attacks

## 1️⃣ Verify the software meets the filters
Before starting, confirm:
- It is **open-source** or has a **demo/free version**
- It is **not** in any bug bounty program
- It was **not** created solely for academic purposes
- It is **not** under the scope of another CNA (check the vendor’s `security.md`)
- It is used in **Western countries**
- Preferably has **1,000+ GitHub stars**
- Runs on **Linux, Windows, macOS, Android, or iOS**

---

## 2️⃣ Prepare the information
Fill out the [Markdown template](/Report%20Template%20and%20Instructions/Fluid_Attacks_Report_Template.md) with:
- Link to the repository on GitHub/GitLab
- Vulnerable version
- **CVSS v4.0** score
- Vendor website
- Advisory name (1 word, band/artist names allowed) + link to the artist on Wikipedia or Last.fm
- Discovery date
- **CWE** and **CAPEC** IDs of the vulnerability
- Vulnerability category according to [Fluid Attacks’ criteria](https://help.fluidattacks.com/portal/en/kb/articles/criteria-vulnerabilities-intro)
- Vendor contact (email)
- Steps to install and run locally
- Link to the vendor’s security policy (`security.md`)
- Technical description, PoC, evidence, and recommendations

---

## 3️⃣ Gather the evidence
- Screenshots showing the exploitation
- Vulnerable source code (if public)
- Video demonstrating the PoC execution

---

## 4️⃣ Send to Fluid Attacks
- Address the email to:  
  `scorrea@fluidattacks.com` **(CC: `research@fluidattacks.com`)**
- Subject:
  ```
  Vulnerability Submission – <Software Name> – <Vulnerability Type>
  ```
- Attach:
  - The completed **.md** report
  - All exploitation images and videos
- In the email body, include:
  ```
  Hi Sebastián,

  Please find attached the vulnerability report following the required format.
  All filters were checked and met.

  Best regards,
  <Your Name>
  ```

---

## 5️⃣ Wait for triage
- Fluid Attacks will perform the triage
- If approved, they will contact the vendor and CC you
- The process will follow their [Disclosure Policy](https://fluidattacks.com/advisories/policy)
