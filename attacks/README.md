# Attack Techniques

## AS-REP Roasting
A domain user was configured without Kerberos pre-authentication, allowing the extraction
of an AS-REP hash which can be cracked offline.

## Kerberoasting
A service account with an SPN was identified. A service ticket encrypted with the service
account password was requested and extracted for offline cracking.

## ADCS ESC1
A misconfigured certificate template allowed any authenticated user to request a certificate
with an arbitrary UPN. This was abused to impersonate a Domain Admin account and achieve
full domain compromise.
