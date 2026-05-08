# 📖 KB-002 — Network Troubleshooting Steps (Tier 1)

**Knowledge Base ID:** KB-002  
**Category:** Network / Connectivity  
**Last Updated:** April 2026  
**Author:** Elizabeth Amoo, Tier 1 Support

---

##  Purpose

A step-by-step guide for diagnosing and resolving common network connectivity issues at the Tier 1 support level.

---

##  Quick Diagnosis — Ask These First

Before touching any settings, ask the user:

| Question | Why It Matters |
|----------|---------------|
| Is it affecting one person or multiple? | Multiple = infrastructure issue |
| Can you access internal systems but not internet? | Narrows to DNS or firewall |
| Did anything change recently? | New software, moved desk, Windows update |
| When exactly did it start? | Correlate with any known outages |
| What does it say when you try to connect? | Error messages are clues |

---

##  Step-by-Step CLI Diagnostic

Run these commands **in order** on the user's machine via Remote Desktop or in person:

### Step 1 — Check IP Address
```bash
ipconfig /all
```
**What to look for:**

| Result | Meaning |
|--------|---------|
| `192.168.x.x` or `10.x.x.x` | ✅ Normal — DHCP working |
| `169.254.x.x` | ❌ APIPA — DHCP server unreachable |
| `0.0.0.0` | ❌ No IP assigned at all |

---

### Step 2 — Test the NIC (Network Card)
```bash
ping 127.0.0.1
```
- ✅ Success = NIC is physically working
- ❌ Fail = NIC issue or TCP/IP stack corrupted → escalate

---

### Step 3 — Test Local Gateway
```bash
ping [default gateway IP]
# Example: ping 192.168.1.1
```
- ✅ Success = Connected to local network
- ❌ Fail = Cannot reach router → switch/cable issue

---

### Step 4 — Test External Connectivity
```bash
ping 8.8.8.8
# (Google's public DNS — always works if internet is up)
```
- ✅ Success = Internet works but DNS may be broken
- ❌ Fail = No internet connectivity beyond local network

---

### Step 5 — Test DNS Resolution
```bash
nslookup google.com
```
- ✅ Returns IP address = DNS working fine
- ❌ "Request timed out" = DNS server issue

---

### Step 6 — Trace the Route
```bash
tracert google.com
```
- Shows every hop from user's machine to destination
- Look for where packets stop (that's where the problem is)

---

##  Common Fixes

### Fix 1 — Release and Renew IP (DHCP Issues)
```bash
ipconfig /release
ipconfig /renew
```
Use when: APIPA address (169.254.x.x) or "No internet" after the gateway pings fine

---

### Fix 2 — Flush DNS Cache
```bash
ipconfig /flushdns
```
Use when: User can reach some sites but not others, or gets "server not found" errors

---

### Fix 3 — Reset Network Stack (Windows 10/11)
```bash
# Run as Administrator
netsh int ip reset
netsh winsock reset
# Restart computer after running both
```
Use when: All above fixes failed and connectivity is still broken

---

### Fix 4 — Disable/Re-enable Network Adapter
```
Settings → Network & Internet → Change adapter options
Right-click the adapter → Disable
Wait 10 seconds
Right-click → Enable
```

---

##  When to Escalate to Tier 2

| Situation | Action |
|-----------|--------|
| Multiple users on same floor/area affected | Escalate → Network Team (switch issue) |
| DHCP not responding after release/renew | Escalate → Network Team (DHCP server) |
| VPN connectivity issues | Escalate → Network/Security Team |
| Physical cable or switch port suspected | Escalate → On-site Network Team |
| Tracert shows packet loss at ISP level | Escalate → ISP ticket + Tier 2 |

---

*Related Ticket: [TKT-002 — Network Connectivity Issue](../tickets/Ticket-002-Network-Connectivity.md)*
