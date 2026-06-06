# Incident Report 02 - Unauthorized DCSync Permissions

## Incident Information

| Field | Value |
|---------|---------|
| Incident ID | 02 |
| Detection Time | During Competition |
| Remediation Time | 4:19 PM CST |
| Target System | rrintel.internal Domain |
| Affected Account | mmalik |
| Persistence Mechanism | Unauthorized Active Directory ACE |
| Severity | Critical |

---

## Summary

An unauthorized access control entry (ACE) was discovered on the Active Directory domain object granting replication privileges directly to the standard user account `mmalik`.

These permissions would allow the account to perform DCSync operations and retrieve sensitive credential material from Active Directory.

---

## Indicators of Compromise

### Affected Account

```text
mmalik
```

### Unauthorized Permissions

```text
Replicating Directory Changes
Replicating Directory Changes All
Replicating Directory Changes In Filtered Set
```

---

## Impact

The assigned permissions effectively granted DCSync capability to a standard user account.

An attacker with access to this account could:

- Replicate Active Directory secrets
- Extract password hashes
- Obtain credential material
- Facilitate privilege escalation

---

## Investigation

A review of Active Directory permissions identified replication-related ACEs directly assigned to the account `mmalik`.

The permissions were not consistent with the user's authorized role and represented an unauthorized elevation of privileges.

---

## Remediation

1. Reviewed domain object permissions.
2. Located unauthorized ACEs assigned to `mmalik`.
3. Removed all replication-related permissions.
4. Verified removal of DCSync capability.

---

## Result

- Unauthorized replication permissions removed.
- DCSync capability eliminated.
- Active Directory permissions restored to approved state.
- Credential replication abuse prevented.

---

## MITRE ATT&CK Mapping

| Tactic | Technique |
|----------|----------|
| Credential Access | T1003.006 - DCSync |
