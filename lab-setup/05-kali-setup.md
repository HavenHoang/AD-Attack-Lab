# Kali Linux Setup (Attacker Machine)

## Host-Only Network Configuration

The Kali Linux virtual machine was configured using VirtualBox Host-Only networking.

This ensures:

- Direct communication with the Domain Controller  
- Isolation from the external network  
- A controlled environment for simulating real-world attack scenarios  

Proper network configuration is critical for Active Directory attack simulations, as Kerberos and LDAP communication must function correctly within the same subnet.

![Host-Only Network Setup](../screenshots/lab/12.%20kali_hostonly_network_setup.png)

---

## Offensive Tools Installation

The following offensive security tools were installed and verified on Kali:

- Impacket  
- CrackMapExec  
- Certipy  
- Hashcat  

These tools will be used throughout the lab to perform:

- AS-REP Roasting  
- Kerberoasting  
- ADCS ESC1 exploitation  
- Privilege escalation  

![Offensive Tools Installed](../screenshots/lab/13.%20kali_offensive_tools_installed.png)
