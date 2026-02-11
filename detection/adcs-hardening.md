# ADCS Hardening and ESC1 Mitigation

This document describes best practices to secure Active Directory Certificate Services and prevent ESC1 certificate-based privilege escalation.

---

## 1. Restrict Certificate Template Permissions

- Remove **Authenticated Users** from enrollment on sensitive templates
- Only allow required accounts/groups to enroll
- Regularly audit template permissions

---

## 2. Disable “Enrollee Supplies Subject”

- Ensure templates do **not allow users to supply subject name** unless strictly necessary
- This prevents attackers from impersonating high-privilege accounts

---

## 3. Limit Extended Key Usages (EKUs)

- Only enable EKUs required for the intended purpose
- For sensitive templates, avoid Client Authentication if not needed

---

## 4. Monitor Certificate Requests

- Monitor who requests certificates for sensitive templates
- Alert on requests for Domain Admin or other privileged accounts
- Integrate with SIEM for real-time monitoring

---

## 5. General ADCS Security Best Practices

- Keep CA servers isolated and patched
- Implement strong authentication for CA administrators
- Regularly review and audit all certificate templates and enrollment permissions
- Use PKI policies to enforce compliance
