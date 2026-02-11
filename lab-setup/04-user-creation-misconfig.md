# User Creation & AD Misconfigurations

## 1️⃣ Create Active Directory Users

Three domain users were created to simulate different privilege levels:

- Standard user  
- Service account (`svc_sql`)  
- Domain Administrator  

These accounts will be used for attack and privilege escalation testing.

![AD Users Created](../screenshots/lab/8.%20ad_users_created.png)

---

## 2️⃣ AS-REP Roasting Preparation

Kerberos pre-authentication was disabled for specific users to allow AS-REP roasting attacks.

![Pre-auth Disabled](../screenshots/lab/9.%20asrep_pre_authentication_disabled.png)

---

## 3️⃣ Kerberoasting Preparation

A Service Principal Name (SPN) was assigned to the service account `svc_sql`:

- SPN: `HTTP/web.corp.local`  
- This allows Kerberos service ticket generation, which can later be abused in Kerberoasting attacks.

![SPN Assigned](../screenshots/lab/10.%20kerberoast_spn_assigned.png)

---

## 4️⃣ Create Vulnerable ADCS Certificate Template

A vulnerable ADCS certificate template was created by duplicating the default User template and modifying:

- Security and enrollment permissions  
- Allowing “Subject Name supplied by requestor”  
- Client Authentication & Smart Card Logon EKUs  

This misconfiguration enables low-privileged users to request certificates impersonating high-privileged accounts, facilitating **ADCS ESC1 privilege escalation**.

![Vuln Template Configuration](../screenshots/lab/11.1.%20adcs_vuln_template_configuration.png)
![Vuln Template Published](../screenshots/lab/11.2.%20adcs_vuln_template_published.png)
