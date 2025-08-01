## Broken Function Level Authorization (BFLA) allows unauthorized users to alter student grades

## **Summary**

An API endpoint in i-Educar 2.9.0 is vulnerable to Broken Function Level Authorization (BFLA). An unauthorized user is able to modify student grades by directly accessing the `/module/Api/Diario` endpoint, bypassing permission controls. This leads to severe integrity issues, where anyone with access to the API format can tamper with academic records.

## **Details**

The endpoint `/module/Api/Diario`  does not enforce proper authorization checks to validate whether the calling user has the right to alter student grades. Even a user without any profile or assigned permissions can successfully submit a request and change the grades of students in the system.

There is no validation of session roles or associated permissions before executing sensitive academic actions.


## **PoC**

1 - Create a new user with no privileges.

![BFLA](/images/bfla001.png)

2 - Prepare a request to the `/module/Api/Diario` endpoint with the data to submit a student grade, using the low privillege user cookie then send the request.

![BFLA](/images/bfla002.png)

Translated result from pt-br to en:

````
{
  "oper": "post",
  "resource": "grades",
  "msgs": [{
    "msg": "Grades successfully posted!",
    "type": "success"
  }],
  "any_error_msg": false
}
````

## **Impact**

This is a Broken Function Level Authorization (BFLA) vulnerability, as categorized by OWASP API Security Top 10 (2023) - API4. The consequences include:

- Tampering with academic data without authorization.
- Loss of data integrity in school records.
- Potential legal and reputational damage for educational institutions.

# References

[I-Educar – Official Repository](https://github.com/portabilis/i-educar)

# Discoverer

[Natan Maia Morette](https://nmmorette.github.io) 

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)

