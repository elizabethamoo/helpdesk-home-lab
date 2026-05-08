# 📖 KB-001 — How to Reset a Windows / Azure AD Password

**Knowledge Base ID:** KB-001  
**Category:** Account Management  
**Last Updated:** April 2026  
**Author:** Elizabeth Amoo, Tier 1 Support

---

## 🎯 Purpose

This guide is for IT Support Technicians performing password resets for end users who are locked out of their Windows accounts managed through **Azure Active Directory (Azure AD)**.

---

## ⚠️ Before You Start — Security Checks

> **Never skip identity verification.** Resetting a password for an unverified user is a security incident.

Verify the user's identity by confirming **at least 2 of the following**:
- [ ] Full legal name
- [ ] Employee ID / Staff number
- [ ] Department and manager's name
- [ ] Last 4 digits of employee number
- [ ] Security question (if configured)

---

## 🔧 Method 1 — Azure AD Admin Center (Most Common)

**Use when:** User is managed through Microsoft 365 / Azure AD

### Steps:

**1. Log in to Azure AD**
```
URL: https://aad.portal.azure.com
Sign in with your IT Admin credentials
```

**2. Find the User**
```
Left sidebar → Azure Active Directory → Users → All Users
Search bar: type the user's full name or email
Click on the user profile
```

**3. Check Account Status**
```
Under "Properties" tab, check:
- Account enabled: Yes/No
- Sign-in blocked: Yes/No

Under "Sign-in logs" tab, check:
- Number of failed attempts
- Last sign-in location (flag anything unusual)
```

**4. Reset the Password**
```
Click "Reset password" button (top menu bar)
Options:
  ✅ Auto-generate password → ON (recommended)
  ✅ Require user to change on next sign-in → ON (always enable this)
Click "Reset"
Copy the temporary password shown on screen
```

**5. Unlock the Account (if locked)**
```
Properties tab → scroll to "Account status"
If showing "Blocked" → toggle to "Not blocked"
Save changes
```

**6. Deliver the Temporary Password**
```
✅ Deliver verbally over phone
✅ Via secure IT portal message
❌ NEVER send via regular email
❌ NEVER send via SMS unless encrypted
```

---

## 🔧 Method 2 — Local Windows Account Reset

**Use when:** Computer is NOT joined to a domain / Azure AD

### Steps:

**1. Open Computer Management**
```
Right-click "This PC" → Manage
OR
Press Windows + X → Computer Management
```

**2. Navigate to Local Users**
```
Local Users and Groups → Users
Right-click the affected user → Set Password
```

**3. Set Temporary Password**
```
Enter a temporary password
Click OK
Instruct user to change it immediately after logging in
```

---

## ✅ Post-Reset Checklist

- [ ] User confirmed successful login
- [ ] User changed password on first sign-in
- [ ] Ticket updated with resolution notes
- [ ] If account was locked 5+ times, flag for security review

---

## 🚨 When to Escalate

Escalate to Tier 2 / Security team if:
- Account keeps locking within hours of reset (possible credential stuffing attack)
- Sign-in logs show logins from unusual countries/IPs
- User denies making the failed login attempts (possible account compromise)

---

*Related Ticket: [TKT-001 — Password Reset](../tickets/Ticket-001-Password-Reset.md)*
