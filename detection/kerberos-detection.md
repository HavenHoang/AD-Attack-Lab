# Kerberos Attack Detection

This document describes how to detect common Kerberos abuse in Active Directory environments, including AS-REP Roasting and Kerberoasting.

---

## 1. AS-REP Roasting Detection

AS-REP Roasting targets accounts with Kerberos pre-authentication disabled.

**Detection Methods:**

- Monitor **Event ID 4768** (Kerberos authentication ticket requested):
  - Look for users with **“Pre-authentication failed”** or unusual ticket requests
  - Look for repeated AS-REP requests for accounts without password entry
- Alert on **high frequency of AS-REP requests** from a single host
- Identify accounts with pre-authentication disabled and review necessity

**Mitigation:**

- Enable Kerberos pre-authentication for all user accounts
- Implement strong password policies
- Regular auditing of accounts with pre-authentication disabled

---

## 2. Kerberoasting Detection

Kerberoasting abuses service accounts with SPNs to request TGS tickets.

**Detection Methods:**

- Monitor **Event ID 4769** (Kerberos Service Ticket request)
  - Look for abnormal request patterns
  - Detect high volume TGS requests from a single user
- Alert on requests for service accounts with weak or default passwords
- Monitor for unusual activity on accounts with SPNs

**Mitigation:**

- Use long, complex passwords for service accounts
- Prefer **Group Managed Service Accounts (gMSA)**
- Limit SPN assignment to necessary accounts only
- Implement logging and SIEM alerting for TGS requests
