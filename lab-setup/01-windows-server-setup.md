# Windows Server Installation

## Create Windows Server VM

A Windows Server virtual machine was created in VirtualBox to serve as the Domain Controller.

![Create Windows Server VM](../screenshots/lab/1.%20dc_windows_server_install.png)

---

## Initial Domain Controller Setup

The Windows Server was configured as a Domain Controller, including installation of necessary roles and basic configuration.

![Initial Configuration](../screenshots/lab/2.%20dc_windows_initial_configuration.png)

---

## Domain Controller Setup Completed

The Domain Controller installation and initial configuration were verified to be successful.

![DC Setup Completed](../screenshots/lab/3.%20dc_setup_completed.png)

---

## Static IP & DNS Configuration

A static IP address was configured for the Domain Controller, and the DNS server was set to point to itself.

This ensures reliable name resolution for Active Directory services, which depend heavily on DNS for authentication and service discovery.

The subnet mask `255.255.255.0` was used to place all lab machines in the same local network, allowing direct communication without routing while keeping the network simple and isolated.

![Static IP Configuration](../screenshots/lab/4.%20dc_static_ip_dns_config.png)
