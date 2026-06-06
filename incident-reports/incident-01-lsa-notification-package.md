# Incident Report 01 - LSA Notification Package Credential Harvester

## Incident Information

| Field | Value |
|---------|---------|
| Incident ID | 01 |
| Detection Time | During Competition |
| Remediation Time | 4:00 PM CST |
| Target System | cabal (Windows Server 2022 Domain Controller) |
| Persistence Mechanism | LSA Notification Package |
| Severity | High |

---

## Summary

An unauthorized LSA Notification Package was discovered on the domain controller. The package was configured to load through the Local Security Authority (LSA) process and could potentially capture user credentials during password change operations.

Investigation revealed a suspicious DLL registered as an LSA notification package, indicating an attempt to maintain persistence and harvest credentials.

---

## Indicators of Compromise

### Registry Artifact

```text
HKLM\SYSTEM\CurrentControlSet\Control\Lsa\Notification Packages
```

### Suspicious Entry

```text
msv1_0aux
```

### Associated File

```text
C:\Windows\System32\msv1_0aux.dll
```

---

## Impact

If left in place, the malicious authentication package could capture credentials as users changed passwords on the domain controller.

Potential attacker objectives included:

- Credential theft
- Privilege escalation
- Persistence
- Lateral movement

---

## Investigation

Review of LSA authentication components identified an unexpected entry within the Notification Packages registry value.

The associated DLL did not correspond to a legitimate operating system component and was determined to be unauthorized.

---

## Remediation

1. Removed the `msv1_0aux` entry from:

```text
HKLM\SYSTEM\CurrentControlSet\Control\Lsa\Notification Packages
```

2. Rebooted the domain controller to unload the malicious DLL.

3. Verified the package was no longer present after restart.

---

## Result

- Unauthorized persistence mechanism removed.
- Credential harvesting capability eliminated.
- Domain controller returned to approved configuration.
- CCS remediation points awarded.

---

## MITRE ATT&CK Mapping

| Tactic | Technique |
|----------|----------|
| Persistence | T1547.002 - Authentication Package |
| Credential Access | T1547.002 - Authentication Package |
