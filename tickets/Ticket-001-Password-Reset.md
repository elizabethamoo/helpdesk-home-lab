# 🎫 Ticket #001 — Password Reset Request

---

## Ticket Details

| Field | Info |
|-------|------|
| **Ticket ID** | TKT-001 |
| **Date Opened** | 2026-04-15 09:12 AM |
| **Date Closed** | 2026-04-15 09:21 AM |
| **Priority** | Medium |
| **Category** | Account Management |
| **Status** | ✅ Resolved |
| **Resolution Time** | 9 minutes |

---

## 📋 User Request

> *"Hi, I've been locked out of my Windows account since this morning. I tried entering my password multiple times and now it says my account is locked. I have a meeting in 30 minutes. Please help!"*  
> — **Sarah M., Marketing Department**

---

## 🔍 Step-by-Step Resolution

### Step 1 — Receive & Log the Ticket
- Ticket received via **email** to the helpdesk inbox
- Logged into **ServiceDesk** with the following details:
  - Category: `Account Management > Password Reset`
  - Priority set to `Medium` (user has time-sensitive meeting)
  - Assigned to: `Elizabeth Amoo (Tier 1 Technician)`

### Step 2 — Verify User Identity
- Confirmed caller identity by asking:
  - Full name ✅
  - Employee ID ✅
  - Department ✅
- **Never reset a password without verifying identity first** — this is a security best practice

### Step 3 — Check Account Status in Azure AD
- Logged into **Azure Active Directory Admin Center**
- Navigated to: `Users > All Users > Search: Sarah M.`
- Observed: Account showed **"Sign-in blocked: Yes"** and **failed login attempts: 5**
- Confirmed: Account was locked due to too many failed attempts (policy threshold = 5)

### Step 4 — Unlock the Account
```
Azure AD Steps:
1. Select user → Properties tab
2. Click "Reset password"
3. Enable "Auto-generate password" → ON
4. Enable "Require user to change password on first sign-in" → ON
5. Click Reset
6. Copy the temporary password
```

### Step 5 — Communicate Resolution to User
- Called Sarah back within 2 minutes
- Provided temporary password verbally (never via email)
- Confirmed she could log in successfully
- Reminded her to change password immediately after login

### Step 6 — Close & Document the Ticket
- Updated ServiceDesk ticket with resolution notes
- Marked status: **Resolved**
- Added to Knowledge Base for future reference

---

## ✅ Resolution

Account unlocked via Azure Active Directory. Temporary password issued. User confirmed successful login at 9:21 AM. Password change completed by user at 9:23 AM.

---

## 📚 Lessons Learned

- Always verify identity **before** any account action
- Temporary passwords should never be sent via email — always verbal or secure portal
- Escalate to Tier 2 if account keeps locking repeatedly (may indicate a compromised account or misconfigured device caching old credentials)

---

## 🔗 Related Knowledge Base Article
→ [KB-001: How to Reset a Windows Password](../knowledge-base/KB-001-How-to-Reset-Windows-Password.md)
