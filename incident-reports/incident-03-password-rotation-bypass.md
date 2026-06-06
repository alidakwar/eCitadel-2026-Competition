# Incident Report 03 - Password Rotation Bypass

## Incident Information

| Field | Value |
|---------|---------|
| Incident ID | 03 |
| Detection Time | During Competition |
| Remediation Time | 4:25 PM CST |
| Target System | cabal (Windows Server 2022 Domain Controller) |
| Persistence Mechanism | Authentication Configuration Modification |
| Severity | High |

---

## Summary

A registry modification was discovered that allowed previously-used passwords to remain valid after password changes.

This configuration weakened password rotation effectiveness and allowed compromised credentials to continue functioning after users updated their passwords.

---

## Indicators of Compromise

### Registry Artifact

```text
HKLM\SYSTEM\CurrentControlSet\Control\Lsa\OldPasswordAllowedPeriod
```

### Configuration

```text
OldPasswordAllowedPeriod > 0
```

---

## Impact

The configuration permitted old passwords to remain valid after password changes.

Potential consequences included:

- Continued attacker access after password rotation
- Extended credential compromise window
- Delayed containment of compromised accounts

---

## Investigation

Registry review identified the `OldPasswordAllowedPeriod` value configured to permit continued authentication using previous passwords.

This behavior was inconsistent with secure password management practices and represented a persistence opportunity for an attacker already in possession of valid credentials.

---

## Remediation

1. Located the registry value:

```text
HKLM\SYSTEM\CurrentControlSet\Control\Lsa\OldPasswordAllowedPeriod
```

2. Set the value to:

```text
0
```

3. Verified the configuration was applied successfully.

---

## Result

- Old passwords no longer accepted after password changes.
- Credential reuse window eliminated.
- Password rotation effectiveness restored.
- Authentication configuration returned to approved state.

---

## MITRE ATT&CK Mapping

| Tactic | Technique |
|----------|----------|
| Credential Access | T1556 - Modify Authentication Process |
| Persistence | T1556 - Modify Authentication Process |
