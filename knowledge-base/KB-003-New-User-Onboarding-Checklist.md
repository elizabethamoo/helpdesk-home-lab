#  KB-003 — New User IT Onboarding Checklist

**Knowledge Base ID:** KB-003  
**Category:** User Management / Onboarding  
**Last Updated:** April 2026  
**Author:** Elizabeth Amoo, Tier 1 Support

---

##  Purpose

This checklist ensures every new employee receives consistent, complete IT setup on their first day. Complete every item and check it off in the ticket before closing.

---

##  Pre-Arrival (1–2 Days Before Start Date)

- [ ] Receive new hire request from HR (name, department, manager, start date, role)
- [ ] Create user account in **Azure Active Directory**
  - Username format: `firstname.lastname@company.com`
  - Set temporary password (must change on first login)
  - Assign correct department and manager
- [ ] Assign appropriate **security group / permissions** based on role
- [ ] Set up **Microsoft 365 license** (email, Teams, OneDrive)
- [ ] Add user to relevant **distribution lists** and **Teams channels**
- [ ] Prepare physical hardware:
  - [ ] Laptop imaged with standard OS (Windows 11 Pro)
  - [ ] Laptop joined to Azure AD domain
  - [ ] Standard software installed (see software list below)

---

##  Standard Software Install List

| Software | Purpose | Source |
|----------|---------|--------|
| Microsoft 365 (Office) | Productivity suite | Microsoft portal |
| Microsoft Teams | Communication | Microsoft portal |
| Adobe Acrobat Reader | PDF viewing | adobe.com |
| VPN Client | Remote access | Internal IT portal |
| Antivirus (e.g. Defender) | Security | Pre-installed/Windows |
| Company intranet browser bookmark | Internal systems | Manual setup |

---

##  Day 1 — Hardware Setup

- [ ] Laptop powered on and domain-joined confirmed
- [ ] User logged in with temporary credentials
- [ ] Password changed successfully on first login
- [ ] MFA (Multi-Factor Authentication) enrolled:
  - [ ] Microsoft Authenticator app installed on mobile
  - [ ] MFA verified with test sign-in
- [ ] Network connectivity confirmed (ping test)
- [ ] Mapped network drives (if applicable)
- [ ] Printer added and test page printed

---

##  Day 1 — Account & Access Setup

- [ ] Microsoft 365 email working (send/receive test)
- [ ] Microsoft Teams installed and user can join a channel
- [ ] OneDrive syncing correctly
- [ ] VPN access configured and tested
- [ ] Access to required internal systems confirmed with user
- [ ] Shared mailboxes added (if applicable)

---

##  Day 1 — User Handover

- [ ] Walk user through logging in and changing password
- [ ] Show user how to submit IT helpdesk tickets (ServiceDesk portal URL)
- [ ] Show user how to connect to VPN
- [ ] Provide IT Support contact information:
  - Helpdesk email: `helpdesk@company.com`
  - Phone: ext. 100
  - Portal: `https://helpdesk.company.com`
- [ ] User signs IT Acceptable Use Policy (AUP)
- [ ] User confirms all accounts working

---

##  Ticket Closure

- [ ] All checklist items completed
- [ ] Asset register updated (laptop serial number, assigned user, date)
- [ ] Software license register updated
- [ ] Onboarding ticket closed in ServiceDesk Plus
- [ ] Welcome email sent to new user with IT contacts and resources

---

##  Common Onboarding Issues & Quick Fixes

| Issue | Quick Fix |
|-------|----------|
| MFA not working | Re-enroll Authenticator app |
| Cannot access shared drive | Check security group membership in Azure AD |
| Email not syncing | Re-add account in Outlook → File → Add Account |
| VPN failing | Check credentials, reinstall VPN client |
| Laptop not domain-joining | Check network, re-run domain join command |

---

*Related Ticket: [TKT-003 — Software Installation](../tickets/Ticket-003-Software-Installation.md)*
