# Windows Server & Active Directory Defense

## Overview

The Windows Server 2022 Domain Controller served as the central authentication and authorization system for the competition environment.

Primary defensive responsibilities included:

- Active Directory administration
- Account auditing
- Privilege management
- Service availability
- Incident response
- Persistence removal

---

## Account Audit

### Disabled Accounts

The following unauthorized accounts were disabled:

- svc_ldap
- msolomon
- pkotsiopulos

---

## Enterprise Admins Review

### Unauthorized Membership Removed

| User | Action |
|--------|--------|
| mxiu | Removed from Enterprise Admins |

---

## Domain Admins Review

### Unauthorized Membership Removed

| User | Action |
|--------|--------|
| pkotsiopulos | Removed |
| tkeen | Removed |
| svc_ldap | Removed |

---

## Administrative Password Remediation

Administrative account passwords were rotated in accordance with competition requirements.

Affected accounts included:

- rreddington
- hcooper
- dressler
- amojtabai
- ekeen
- dzuma
- mgerard
- kkaplan

Passwords are intentionally omitted from this repository.

---

## Service Availability

Critical services maintained:

- DNS
- OpenSSH

Services were continuously monitored while security remediation activities were performed.

---

## Security Findings

Major findings included:

1. LSA Notification Package Credential Harvester
2. Unauthorized DCSync Permissions
3. Password Rotation Bypass Configuration

Detailed analysis can be found in the Incident Reports and Attack Summary sections.
