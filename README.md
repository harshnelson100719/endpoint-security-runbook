# Endpoint Security Runbook

A self-contained, interactive security runbook for Microsoft 365 enterprise environments. Built for IT and security teams managing Windows endpoints through Intune, with SentinelOne EDR, Qualys vulnerability management, and Horizon VDI.

No backend. No login. No dependencies. One HTML file — open it in any browser.

---

## What this is

Most endpoint security checklists are static documents that go stale the moment you close them. This runbook is different — it's a living operational tool with two distinct tracks that reflect how security work actually happens.

**Setup controls** are one-time configuration tasks. Deploy BitLocker, configure LAPS, enforce MFA, enable ASR rules. You do it once, verify it, and mark it done. 31 controls across 6 phases.

**Operational tasks** recur on a schedule. Triage SentinelOne alerts, run Qualys scans, review Conditional Access policies. These never stay "done" — they need to happen again next week, next month, next quarter. 10 tasks with cadence tracking, a completion log, and overdue indicators.

---

## Stack coverage

| Tool | Coverage |
|---|---|
| **Microsoft Intune** | Settings Catalog, Compliance Policies, Endpoint Security, Update Rings, EPM, LAPS |
| **Entra ID** | Conditional Access, FIDO2/Passwordless, Break-glass accounts, Device compliance |
| **SentinelOne** | Agent deployment, Protect mode, Tamper Protection, Alert triage, EDR co-existence |
| **Qualys** | Cloud Agent deployment, Authenticated scanning, CVE prioritization, VDI scanning |
| **Microsoft Defender** | ASR rules, BitLocker, Firewall baseline, Security Baseline |
| **VMware Horizon** | VDI gold image patching, Cloud Agent persistence, Pool recompose |
| **Duo** | Passwordless MFA, Verified Push, Entra integration |

---

## Features

### Two-track system
- **Setup track** — 31 controls, 6 phases (Scope, Identity, Hardening, Threat Detection, Vulnerability Management, Compliance)
- **Operations track** — 10 recurring tasks with daily, weekly, monthly, quarterly, and annual cadences

### Three status states (setup controls)
- **To do** — not yet addressed
- **In place** — you believe it exists; use the runbook steps to verify
- **Verified** — confirmed correct and evidence collected

### Operational cadence tracking
- Calculates next due date from last completion
- Visual status: on track (green), due soon (amber), overdue (red), never run (grey)
- Completion log with optional notes — your audit trail
- Last 5 completions visible per task

### Navigation
- Sidebar filter bar — show only To do, In place, Verified, or all
- Text search — filter items by name or ID in the sidebar
- Quick jump — press `/` to open a floating search across both tracks
- Keyboard shortcuts — `←` `→` to navigate, `1` `2` `3` to set status, `ESC` to close
- Previous / Next buttons on every item

### Summary report
- Phase-by-phase breakdown of setup control statuses
- Operations task table with cadence, last run date, and current status
- One-click copy to plain text for pasting into emails or Teams

### Persistent state
- All statuses, completion logs, and notes are saved to `localStorage`
- Reopen the file in the same browser and everything is exactly where you left it
- Each user/device gets their own independent state

---

## Getting started

### Option A — GitHub Pages (recommended)

1. Fork or clone this repository
2. Rename `endpoint_security_runbook_v3.html` to `index.html`
3. Go to **Settings → Pages**
4. Set source to **Deploy from a branch → main → / (root)**
5. Your runbook is live at `https://yourusername.github.io/your-repo-name`

### Option B — Local use

Download `index.html` and open it directly in any modern browser. No server required.

---

## How to use it

### First time

1. Open the runbook and read the welcome screen — it explains both tracks
2. Switch to the **Setup track** (default)
3. Work through items top to bottom, or use the filter to jump to a specific phase
4. For each item: read the "Why this matters" card, work through the steps, then set the status
5. Use **In place** for controls you believe already exist — then verify them before marking Verified
6. Switch to the **Operations track** and log your first completion for each recurring task

### Ongoing

- Check the Operations track regularly — the welcome screen shows overdue tasks with a direct jump button
- Use the sidebar filter to focus on what needs attention — filter by "To do" to see only open items
- Open the Summary report before stakeholder meetings — use "Copy as text" for a quick status update

### Keyboard shortcuts

| Key | Action |
|---|---|
| `→` or `]` | Next item |
| `←` or `[` | Previous item |
| `/` | Open quick search |
| `1` | Set status: To do |
| `2` | Set status: In place |
| `3` | Set status: Verified |
| `ESC` | Close search / modal |

---

## Setup controls — full list

**Phase 1 — Scope & Inventory**
- S1 · Confirm Intune enrollment status for all devices
- S2 · List all endpoint types in scope
- S3 · Identify unmanaged or non-compliant devices
- S4 · Document out-of-scope endpoints

**Phase 2 — Identity & Access**
- I1 · Enforce MFA via Conditional Access
- I2 · Configure Duo passwordless / phishing-resistant MFA
- I3 · Enable Windows LAPS
- I4 · Restrict local admin rights via EPM
- I5 · Verify break-glass accounts

**Phase 3 — Endpoint Hardening**
- H1 · Deploy BitLocker with XTS-AES 256 + TPM 2.0
- H2 · Deploy Windows 11 Security Baseline
- H3 · Apply Windows Firewall baseline
- H4 · Configure auto-lock: 5 min inactivity timeout
- H5 · Enable Dynamic Lock
- H6 · Enable ASR rules — audit mode first, then enforce
- H7 · Disable USB/removable storage where not required

**Phase 4 — Threat Detection**
- T1 · Confirm SentinelOne agent coverage on all endpoints
- T2 · Validate S1 protect mode is active
- T3 · Enable S1 Tamper Protection
- T4 · Confirm S1 is sole EDR — no dual-agent conflicts
- T5 · Triage S1 alerts older than 48 hours

**Phase 5 — Vulnerability Management**
- V1 · Run authenticated Qualys scan across all endpoints
- V2 · Identify and prioritize critical/high CVEs
- V3 · Configure Windows Update for Business rings
- V4 · Audit third-party software patch status
- V5 · Verify Horizon VDI gold image is patched

**Phase 6 — Compliance & Documentation**
- C1 · Build Intune compliance policy aligned to baseline
- C2 · Wire compliance policy to Conditional Access
- C3 · Run MDM Diagnostic Report on sample devices
- C4 · Document gaps with risk ratings
- C5 · Create ongoing assessment process document

---

## Operational tasks — full list

| ID | Task | Cadence |
|---|---|---|
| OP1 | Triage S1 alerts older than 48 hours | Every 2 days |
| OP2 | Review S1 threat dashboard — weekly sweep | Weekly |
| OP3 | Run Qualys vulnerability scan | Monthly |
| OP4 | Review and remediate open CVEs | Monthly |
| OP5 | Audit third-party software patch status | Monthly |
| OP6 | Verify Horizon VDI gold image is patched | Monthly (post Patch Tuesday) |
| OP7 | Review Intune non-compliant devices | Weekly |
| OP8 | MDM Diagnostic spot checks on sample devices | Quarterly |
| OP9 | Review Conditional Access policies | Quarterly |
| OP10 | Full endpoint security assessment | Annually |

---

## Customising the runbook

All content lives in two JavaScript arrays near the top of `index.html`:

- `RUNBOOK` — the 31 setup controls with phases, steps, tips, and warnings
- `OPS_TASKS` — the 10 operational tasks with cadence and procedure steps

**To remove an item** — find the object by its `id` (e.g. `id:"H7"`) and delete it along with its surrounding `{}` and trailing comma.

**To add an item** — copy an existing object in the relevant array, change the `id`, `title`, `steps`, and other fields, and paste it where you want it to appear.

**To change a cadence** — update `cadenceDays` (number of days) and `cadenceLabel` (display string) on any ops task.

---

## Important notes on localStorage

Progress and completion logs are stored in `localStorage` — meaning they're saved per browser, per device. This is intentional for personal use.

If you want shared team state (everyone sees the same progress), that requires a backend and is outside the scope of this tool. For team use, the recommended approach is: one person owns the runbook instance, uses the Summary Report to share status, and copies the text output into a shared document or Teams channel.

---

## Browser support

Tested in Chrome, Firefox, Edge, and Safari. Requires a modern browser with ES6 support — any browser released after 2017 works fine.

---

## Acknowledgements

Built for Microsoft 365 enterprise environments using guidance from:
- Microsoft Intune documentation
- Microsoft Entra ID Conditional Access documentation
- CIS Benchmarks for Windows
- NIST SP 800-53 and NIST CSF
- SentinelOne deployment best practices
- Qualys Cloud Agent documentation
