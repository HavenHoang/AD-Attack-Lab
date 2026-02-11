# Active Directory Attack Lab – AS-REP Roasting, Kerberoasting, ADCS ESC1

This repository documents a hands-on Active Directory attack lab designed to simulate real-world enterprise misconfigurations and demonstrate common privilege escalation techniques.

## Lab Objectives
- Build a Windows Active Directory environment
- Introduce intentional AD misconfigurations
- Exploit Kerberos and ADCS vulnerabilities
- Demonstrate full domain compromise

## Lab Environment
- Windows Server (Domain Controller)
- Active Directory Domain: corp.local
- ADCS (Certificate Authority)
- Kali Linux (Attacker)
- VirtualBox Host-Only Network

## Attack Chain
1. AS-REP Roasting → Obtain initial credentials
2. Kerberoasting → Compromise service account
3. ADCS ESC1 → Certificate-based privilege escalation
4. Domain Admin compromise

## Repository Structure
- lab-setup/ – Domain setup & misconfiguration
- attacks/ – Step-by-step attack execution
- detection/ – Detection & mitigation ideas
- diagrams/ – Network & attack flow diagrams
- screenshots/ – Screenshots referenced in documentation

## Disclaimer
This lab is for educational and defensive security research purposes only.
