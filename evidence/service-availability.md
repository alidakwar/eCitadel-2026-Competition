# Service Availability

## Overview

Critical services were monitored continuously to ensure uptime while performing remediation and defensive actions.

---

## Services Monitored

| Service | Target System | Notes |
|---------|---------------|-------|
| SSH | All servers | Maintained external accessibility during defensive actions |
| DNS | cabal (Windows Server 2022) | Validated connectivity for domain services |
| HTTP / Ecom | concierge (Fedora 43) | Checked with internal and external IPs |
| Tickets | concierge (Fedora 43) | Verified portal accessibility |

---

## Monitoring Process

- Services were checked every 2–3 minutes via the team portal.
- All remediation steps were planned to avoid disrupting service availability.
- Any service impact during remediation was immediately addressed.

---

## Results

- SSH and DNS services maintained with 90%+ uptime.
- HTTP and ticketing services remained accessible externally throughout competition.
- Service continuity was preserved while executing all incident response and security remediation activities.
