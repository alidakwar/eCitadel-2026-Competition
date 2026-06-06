# Attack Summary

## Executive Summary

During the competition, multiple credential-focused persistence mechanisms and Active Directory abuses were identified on the Windows Server 2022 Domain Controller.

The adversary's activities primarily targeted authentication systems and credential access pathways.

All identified findings were investigated and remediated.

---

# Finding 1 – LSA Notification Package Credential Harvester

## MITRE ATT&CK

- T1547.002 – Authentication Package

## Description

An unauthorized LSA Notification Package named `msv1_0aux` was configured on the domain controller.

The package was capable of loading into the Local Security Authority process and potentially capturing credentials during password changes.

## Impact

Potential credential harvesting of domain users.

## Remediation

- Removed malicious notification package registration.
- Rebooted system to unload the DLL.

---

# Finding 2 – Unauthorized DCSync Permissions

## MITRE ATT&CK

- T1003.006 – DCSync

## Description

The account `mmalik` possessed unauthorized directory replication permissions on the domain object.

These permissions allowed credential replication operations without requiring Domain Administrator membership.

## Impact

Potential extraction of Active Directory credential material.

## Remediation

Removed all unauthorized replication permissions assigned to the account.

---

# Finding 3 – Password Rotation Bypass

## MITRE ATT&CK

- T1556 – Modify Authentication Process

## Description

The `OldPasswordAllowedPeriod` registry value permitted previously-used passwords to remain valid after password changes.

## Impact

Compromised credentials could continue functioning after password rotation.

## Remediation

Set the value to `0` to eliminate the password reuse window.

---

# Overall Assessment

The adversary relied heavily on credential-focused persistence and abuse of Active Directory authentication mechanisms.

Common themes included:

- Credential Access
- Persistence
- Authentication Abuse
- Privilege Escalation Preparation

All identified findings were successfully remediated during the competition.
