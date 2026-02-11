# Active Directory Attack Lab – AS-REP Roasting, Kerberoasting, ADCS ESC1

## Overview

This repository documents a hands-on Active Directory attack lab built to simulate real-world enterprise misconfigurations and demonstrate how multiple weaknesses can be chained together to achieve full domain compromise.

The lab environment was built from scratch using Windows Server and Kali Linux in an isolated VirtualBox network.

This project demonstrates:

- Kerberos abuse techniques
- Service account exploitation
- ADCS misconfiguration (ESC1)
- Certificate-based authentication abuse
- Privilege escalation to Domain Administrator

---

## Lab Objectives

- Build a functional Windows Active Directory environment
- Deploy and configure Active Directory Certificate Services (ADCS)
- Introduce intentional security misconfigurations
- Perform offensive security attacks from Kali Linux
- Escalate privileges to Domain Admin
- Document detection and mitigation strategies

---

## Lab Environment

Component: Domain Controller  
Description: Windows Server  

Component: Domain  
Description: corp.local  

Component: AD CS  
Description: Installed and configured  

Component: Users  
Description: Standard user, Service account, Domain Admin  

Component: Attacker Machine  
Description: Kali Linux  

Component: Network  
Description: VirtualBox Host-Only (isolated internal network)

---

## Introduced Misconfigurations

1. Kerberos pre-authentication disabled for a domain user (AS-REP Roasting)
2. Service account with SPN and weak password (Kerberoasting)
3. Vulnerable ADCS certificate template (ESC1):
   - Enrollee supplies subject enabled
   - Client Authentication EKU enabled
   - Smart Card Logon EKU enabled
   - Authenticated Users allowed to enroll

These weaknesses simulate common enterprise security misconfigurations.

---

## Attack Chain

Low-Privilege User  
→ AS-REP Roasting  
→ Offline Password Cracking  
→ Kerberoasting (svc_sql)  
→ Service Account Compromise  
→ ADCS Template Enumeration  
→ ESC1 Exploitation  
→ Certificate Request as Domain Admin  
→ PKINIT Authentication  
→ Kerberos TGT Issued  
→ Full Domain Compromise  

---

## Tools Used

- Impacket
- CrackMapExec
- Certipy
- Hashcat
- VirtualBox
- Windows Server AD DS / ADCS

---

## Repository Structure

lab-setup/     – Domain setup and misconfiguration  
attacks/       – Step-by-step attack execution  
detection/     – Detection and mitigation strategies  
diagrams/      – Network and attack flow diagrams  
screenshots/   – Screenshots referenced in documentation  

---

## Skills Demonstrated

- Active Directory administration
- Kerberos attack techniques
- Service Principal Name (SPN) abuse
- ADCS exploitation (ESC1)
- Certificate-based authentication abuse
- Privilege escalation methodology
- Offensive lab design
- Security documentation

---

## Final Outcome

- Domain Administrator authentication achieved
- Kerberos TGT obtained
- NTLM hash extracted
- Full Active Directory compromise

---

## Disclaimer

This project was conducted in a fully isolated lab environment for educational and defensive security research purposes only.

No production systems were targeted.
