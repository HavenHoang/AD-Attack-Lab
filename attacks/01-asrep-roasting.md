# AS-REP Roasting

## Objective

Identify domain users with Kerberos pre-authentication disabled and retrieve their AS-REP hash for offline password cracking.

---

## Retrieve AS-REP Hash (No Pre-Authentication)

The attacker identified a domain user configured with Kerberos pre-authentication disabled.

Because pre-authentication was not required, an unauthenticated AS-REP request was sent to the Domain Controller.

The DC responded with an AS-REP message encrypted using the user’s password hash, allowing the attacker to obtain a crackable Kerberos hash without valid credentials.

![AS-REP Hash Retrieved](../screenshots/14.%20asrep_no_preauth_hash_retrieved.png)

---

## Offline Password Cracking

The retrieved AS-REP hash was cracked offline using Hashcat.

Since this attack does not require valid authentication, it generates minimal logging and can bypass traditional login monitoring mechanisms.

![AS-REP Hash Cracking Process](../screenshots/15.1.%20asrep_hash_cracked.png)

![AS-REP Password Recovered](../screenshots/15.2.%20asrep_hash_cracked.png)

---

## Why This Works

When Kerberos pre-authentication is disabled:

- The Domain Controller does not validate the requester before issuing an AS-REP.
- The AS-REP is encrypted with the user’s password hash.
- An attacker can retrieve the encrypted blob anonymously and perform offline brute-force cracking.

This exposes password material without triggering authentication failures.

---

## Mitigation

- Ensure Kerberos pre-authentication is enabled for all user accounts.
- Monitor Event ID 4768 for unusual AS-REP requests.
- Enforce strong password policies to prevent successful offline cracking.

---

## Result

The password for user `john` was successfully recovered.

This provided valid domain credentials, enabling the next attack phase: **Kerberoasting**.
