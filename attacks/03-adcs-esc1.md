# ADCS ESC1 – Certificate-Based Privilege Escalation

## Objective

Exploit a vulnerable ADCS certificate template (ESC1) to impersonate a Domain Administrator and obtain full domain compromise.

---

## 1. Enumerate Vulnerable Certificate Templates

Using Certipy and valid domain credentials, certificate templates were enumerated from the Enterprise Certificate Authority.

The following misconfiguration was identified:

- Enrollment rights granted to low-privileged users
- Client Authentication EKU enabled
- Enrollee supplies subject enabled

This combination allows a user to request a certificate on behalf of another account, including privileged accounts.

![Vulnerable Template Enumeration 1](../screenshots/lab/19.1.%20adcs_vulnerable_template_enumeration.png)

![Vulnerable Template Enumeration 2](../screenshots/lab/19.2.%20adcs_vulnerable_template_enumeration.png)

![Vulnerable Template Enumeration 3](../screenshots/lab/19.3.%20adcs_vulnerable_template_enumeration.png)

---

## 2. Request Certificate as Administrator

After identifying the vulnerable template, a certificate request was submitted impersonating the Domain Administrator account.

Because the template allows the requester to supply the subject name, the attacker specified:

administrator@corp.local

The Certificate Authority issued a valid certificate for the Administrator account.

![Certificate Request as Administrator](../screenshots/lab/20.%20adcs_certificate_request_admin.png)

---

## 3. Authenticate via PKINIT and Obtain TGT

The issued certificate was used to authenticate via Kerberos PKINIT.

During PKINIT:

- The Domain Controller validates the certificate.
- The certificate maps to the Administrator account.
- A valid Kerberos TGT is issued.

Certipy was then used to retrieve:

- Kerberos TGT
- NTLM hash of the Administrator account

![PKINIT TGT and NTLM Obtained](../screenshots/lab/21.%20adcs_pkinit_tgt_nt%7Cm_obtained.png.png)

---

## Why This Works

ESC1 occurs when:

- A certificate template allows enrollee-supplied subject names
- Client Authentication EKU is enabled
- Low-privileged users have enrollment permissions

This enables certificate-based impersonation of privileged users.

Because Kerberos trusts certificates mapped to domain identities, the attacker can obtain a TGT without knowing the target’s password.

---

## Mitigation

- Disable “Enrollee supplies subject” unless strictly required.
- Restrict enrollment permissions on certificate templates.
- Monitor certificate requests for privileged accounts.
- Regularly audit ADCS configurations for ESC misconfigurations.

---

## Result

A certificate was successfully obtained for the Domain Administrator account.

Using PKINIT authentication, a valid TGT and NTLM hash were retrieved, resulting in full domain compromise.
