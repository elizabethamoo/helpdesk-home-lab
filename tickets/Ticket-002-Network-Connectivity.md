# 🎫 Ticket #002 — Network Connectivity Issue

---

## Ticket Details

| Field | Info |
|-------|------|
| **Ticket ID** | TKT-002 |
| **Date Opened** | 2026-04-16 02:35 PM |
| **Date Closed** | 2026-04-16 03:10 PM |
| **Priority** | High |
| **Category** | Network / Connectivity |
| **Status** | ✅ Resolved |
| **Resolution Time** | 35 minutes |

---

## 📋 User Request

> *"My internet has been cutting in and out all afternoon. I can't access any of our internal systems or the internet. It's affecting my whole team — 4 of us are having the same problem."*  
> — **James T., Finance Department**

---

## 🔍 Step-by-Step Resolution

### Step 1 — Receive & Log the Ticket
- Ticket received via **phone call**
- Logged into **ServiceDesk Plus**:
  - Category: `Network > Connectivity`
  - Priority upgraded to `High` — multiple users affected (4 users = business impact)
  - Assigned to: `Elizabeth Amoo (Tier 1 Technician)`
  - Note added: *"Potential floor/switch level issue — monitor for wider impact"*

### Step 2 — Gather Information
Asked the user the following questions:
- When did it start? → *"About 2 hours ago"*
- How many users affected? → *"4 people on the same floor"*
- Are they all on the same physical area? → *"Yes, east wing, 3rd floor"*
- Any recent changes? → *"No, nothing changed"*
- Can they access anything at all? → *"No internet AND no internal systems"*

> **Key observation:** Multiple users on the same floor = likely a switch, patch panel, or VLAN issue — not individual machine issue

### Step 3 — Remote Diagnostic on User's Machine
Connected via **Remote Desktop** and ran the following CLI commands:

```bash
# Check IP address assignment
ipconfig /all

# Result showed:
# IPv4 Address: 169.254.x.x   ← APIPA address — means DHCP server NOT reached
# Default Gateway: blank
# DNS Servers: blank

# Test local connectivity
ping 127.0.0.1
# Result: Success ← NIC is working

# Test gateway
ping 192.168.1.1
# Result: Request timed out ← Cannot reach router

# Test DNS
nslookup google.com
# Result: DNS request timed out
```

### Step 4 — Diagnose Root Cause
- **APIPA address (169.254.x.x)** = machine could not reach DHCP server
- Ping to gateway failed = no Layer 3 connectivity
- Multiple users on same floor affected = **upstream network device** (switch or router) is the likely cause
- This is **beyond Tier 1 scope** — requires Tier 2 / Network team

### Step 5 — Temporary Workaround (While Escalating)
Attempted a quick fix first:
```bash
# Release and renew IP address
ipconfig /release
ipconfig /renew

# Result: Still showing 169.254.x.x — DHCP unreachable confirmed
```

No improvement — confirmed escalation needed.

### Step 6 — Escalate to Tier 2
- Updated ticket with all diagnostics performed
- Added escalation note:
  > *"DHCP failure confirmed on 4 machines, 3rd floor east wing. APIPA addresses assigned. Gateway unreachable. Suspected floor switch issue. Escalating to Network Team."*
- Changed ticket status to: **Escalated → Tier 2 Network Team**
- Called James back to inform him of escalation and expected timeline

### Step 7 — Tier 2 Resolution (Documented for learning)
- Network team identified a **faulty patch panel port** on the 3rd floor switch
- Port was remapped to a working port
- DHCP leases renewed automatically
- All 4 users confirmed connectivity restored at 3:10 PM

---

## ✅ Resolution

Root cause: Faulty patch panel port on 3rd floor network switch. Resolved by Tier 2 Network Team (port remapping). All affected users confirmed restoration of connectivity.

---

## 📚 Lessons Learned

- **APIPA address (169.254.x.x) = DHCP unreachable** — always a red flag
- Multiple users on same floor = think infrastructure first, not individual machines
- Document ALL CLI output before escalating — it saves the Tier 2 team time
- Always call the user back after escalation — they deserve to know what's happening

---

## 🔗 Related Knowledge Base Article
→ [KB-002: Network Troubleshooting Steps](../knowledge-base/KB-002-Network-Troubleshooting-Steps.md)
