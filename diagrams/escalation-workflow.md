# IT Support Escalation Workflow

Document ID: DIAG-001
Category: Process Documentation
Author: Elizabeth Amoo

---

## Tier 1 Decision Flow

User Reports Issue
- LOG TICKET in ServiceNow
- Category, Priority, User details

- GATHER INFORMATION
- What happened?
- When did it start?
- How many affected?

- CAN TIER 1 RESOLVE THIS?
- YES: Resolve and close, document solution
- NO: Continue below

- DOCUMENT ALL STEPS TAKEN
- CLI outputs
- Error messages
- Things tried

- ESCALATE TO TIER 2
- Update ticket
- Add full notes
- Notify user

- FOLLOW UP WITH USER
- Every 30 minutes until resolved

---

## Priority Matrix

| Priority | Definition | Response Time | Example |
|----------|-----------|--------------|---------|
| Critical | Full business outage | 15 minutes | Server down, entire office offline |
| High | Multiple users affected | 1 hour | 4 or more users cannot work |
| Medium | Single user blocked | 4 hours | Account lockout |
| Low | Minor inconvenience | Next business day | Software install request |

---

## Escalation Matrix

| Issue Type | Escalate To | When |
|-----------|------------|------|
| Network or switch failure | Tier 2 Network Team | After CLI diagnosis fails |
| Server or AD issues | Tier 2 Sysadmin | When AD admin access needed |
| Security incident | Security Team and Manager | Immediately |
| Hardware failure | Hardware and Procurement | After confirming hardware is faulty |
| Vendor software bug | Tier 2 and Vendor ticket | After reinstall fails |
