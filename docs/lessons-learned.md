# Lessons Learned

## Security Must Be Balanced With Availability

One of the most valuable lessons from the competition was balancing defensive actions with operational requirements.

Security changes frequently affected critical services such as DNS and SSH, requiring careful validation before and after remediation activities.

---

## Active Directory Permissions Can Be More Dangerous Than Group Membership

The DCSync finding demonstrated that dangerous privileges can exist outside traditional administrative groups.

A standard user account possessed replication permissions capable of exposing Active Directory credential material.

This reinforced the importance of reviewing effective permissions rather than relying solely on group membership.

---

## Persistence Often Hides Within Legitimate Functionality

The LSA Notification Package finding leveraged legitimate Windows authentication mechanisms.

Malicious persistence may appear similar to normal operating system functionality and requires detailed investigation to identify.

---

## Incident Response Requires Prioritization

Multiple security findings, service outages, and operational injects occurred simultaneously throughout the competition.

Prioritizing remediation activities while maintaining service availability was often more challenging than identifying the vulnerability itself.

---

## Documentation Matters

Technical remediation alone was not sufficient.

Incident reports, attack summaries, and remediation documentation were required to communicate findings and demonstrate defensive actions.

Clear documentation improved situational awareness and supported decision making throughout the competition.

---

## Key Technical Skills Developed

- Windows Server Administration
- Active Directory Security
- Incident Response
- Account Auditing
- Privileged Access Management
- Service Availability Management
- System Hardening
- Security Documentation
- Authentication Security
- Persistence Analysis
