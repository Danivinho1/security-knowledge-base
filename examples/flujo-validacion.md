# How a context gets validated

1. **Alert arrives** from the EDR or SIEM.
2. **Analyst reviews** the alert and checks the account, host and resource.
3. **Context is confirmed with the client** (owner of the account, process or project).
4. **Record is created** in Casos with the validated context and a recommendation.
5. **Validity is set** to the end of the review window, usually one week.
6. **Record is published** in the weekly view, so the next analyst can find it before escalating.
7. **Renewal or expiry** happens at the end of the window: renew with a new record, or keep the old one as history.

Indicators found during triage go to the IOCs list, linked to the same incident.
