# Kerberoasting

## Objective

Use valid domain credentials to enumerate Service Principal Names (SPNs), request Kerberos service tickets, and crack the associated service account password offline.

---

## 1. SPN Enumeration

Using valid domain credentials obtained from AS-REP Roasting, the attacker enumerated Service Principal Names (SPNs) in the domain.

Service accounts with registered SPNs are potential Kerberoasting targets because Kerberos allows authenticated users to request service tickets for them.

The enumeration revealed a service account `svc_sql` associated with the SPN:

HTTP/web.corp.local

This indicates the account is running a Kerberos-authenticated service.

![SPN Enumeration](../screenshots/lab/16.%20kerberoast_spn_enumeration.png)

---

## 2. Retrieve Service Ticket (TGS)

After identifying a valid SPN, the attacker requested a Kerberos Ticket Granting Service (TGS) ticket for the service account.

The returned service ticket is encrypted using the service account’s NTLM hash.  
Although the ticket can be requested legitimately, it can also be extracted and cracked offline.

![TGS Retrieved](../screenshots/lab/17.%20kerberoast_ticket_retrieved.png)

---

## 3. Offline Password Cracking

The extracted TGS hash was cracked offline using Hashcat.

Because the encryption key is derived from the service account password, weak passwords can be recovered through brute-force or dictionary attacks.

![Kerberoast Hash Cracking](../screenshots/lab/18.1.%20kerberoast_hash_cracked.png)

![Service Account Password Recovered](../screenshots/lab/18.2.%20kerberoast_hash_cracked.png)

---

## Why This Works

Kerberos allows any authenticated domain user to request service tickets for accounts with SPNs.

The TGS ticket is encrypted with the service account’s password hash.  
If the password is weak, it can be cracked offline without interacting further with the Domain Controller.

This makes service accounts high-value targets in Active Directory environments.

---

## Mitigation

- Use long, complex passwords for service accounts.
- Prefer Group Managed Service Accounts (gMSA).
- Monitor for excessive TGS requests (Event ID 4769).
- Restrict SPN assignment to necessary accounts only.

---

## Result

The password for the service account `svc_sql` was successfully recovered.

This provided elevated access within the domain and enabled further privilege escalation through ADCS exploitation.
