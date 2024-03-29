# Linux Compliance Playbook

This playbook (in development) is intended to set up our Linux workstations
for compliance with Cyber Essentials Plus (as detailed 
  [here](https://docs.google.com/document/d/13_Je82eCpPU2qZgYINxDYX9OxRrVemdixj8yD4IFH8s)
), as far as possible.

## Requirements

| Requirement | Ubuntu 20.04 | Ubuntu 22.04 | Fedora
|-|-|-|-
| Full Disk Encryption
| Automatic Updates (security) | D | D | D
| Password Policy
| Account Lockout
| Firewall
| Disable Autorun | | | D
| VPN
| Antivirus
| DriveStrike

|Level | Description | Code
|-|-|-
|Compliant by default | This item just needs you to not turn it off during install | D
|Verified | This item is verified to be compliant by the Ansible playbook | V
|Installed/Configured | This item is actually installed or configured by the Ansible playbook | C
|Planned | We plan to do this | [empty cell]
|Not Planned | We have decided this is too much trouble for now | NP

Ideally we should be able to fill the whole table with `VC`.

Practically : we presently have less than 20 Linux users. It would be best to
identify the most time-consuming and error prone aspects of the setup required,
and sort those out first.

Config changes should not be disturbed by package updates (if possible, avoid
touching config files provided as part of the package, e.g. use config.d/ folders
to supplment config, or where softlinks are used, supply new config and relink
to them).

## Priority

- Most of our users are on Ubuntu (Debian), so prioritise that first
- Prioritise things that are important
- Prioritise things that are fiddly to set up (and thus error prone)

### 1. Full Disk Encryption

Since this is "the most important step", and relatively easy to verify, this
should be done early.

### 2. Password Policy

Another important one that is relatively easy to configure.

### 3. Account Lockout

The instructions as presented in the guide will disable your system if you don't
have the (deprecated) `pam_tally2` module, so anyone upgrading from 20.04 or
following the instructions for 22.04 will find themselves unable to log in.

Fixing this would be nice.

### 4. Antivirus

Currently : SentinelOne
