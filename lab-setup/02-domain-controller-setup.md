# Domain Controller Setup

## Install AD DS + DNS Server Roles

Active Directory Domain Services (AD DS) and DNS Server roles were installed using Server Manager → Add Roles and Features.

![AD DS + DNS Installation](../screenshots/lab/5.%20dc_adds_dns_role_install.png)

---

## Promote Server to Domain Controller

The server was promoted to a Domain Controller. A new domain `corp.local` was created.

![Promote to DC](../screenshots/lab/6.1.%20dc_promote_to_domain_controller.png)

---

## Domain Login Verification

After promotion, the administrator logged into the new domain to verify the Domain Controller setup.

![Domain Login](../screenshots/lab/6.2.%20dc_domain_login_corp_administrator.png)
