# Timebreez Help Documentation - Waves 24-33

**Complete help documentation covering all features from Waves 24-33 (Demo Mode, Sessions, Cover Staff, Reconciliation)**

---

## 📚 Table of Contents

### Getting Started
1. **[Demo Mode - Getting Started](./01-demo-mode-onboarding.md)**
   - Auto-login as Sandra Murphy
   - Understanding demo organization (Sunshine Early Learning Centre)
   - Exploring features safely
   - Demo data structure (7 rooms, 10 employees)

### Core Features
2. **[Session Scheduling - ECCE & AIMS](./02-session-scheduling-ecce-aims.md)**
   - Configuring ECCE session templates
   - Enabling AIMS grant (+1 staff requirement)
   - Viewing session indicators on Control Desk
   - Irish childcare compliance

3. **[Cover Staff Dispatch - Floater Management](./03-cover-staff-dispatch.md)**
   - Flagging employees as cover staff
   - Viewing cover pool availability
   - Dispatching cover to rooms (break, sick, ratio gap)
   - Ending dispatches

4. **[Daily Reconciliation - Plan vs Reality](./04-daily-reconciliation.md)**
   - Understanding Plan vs Reality
   - Resolving discrepancies (early departure, no badge)
   - Operational decisions (confirm present, apply leave)
   - Unlocking payroll approval

5. **[Control Desk Operations](./05-control-desk-operations.md)**
   - Reading room status (GREEN/AMBER/RED)
   - Required vs Planned vs Present counts
   - Session indicators
   - Who's In panel

### Configuration & Support
6. **[Settings and Configuration](./07-settings-and-configuration.md)** *(Coming Soon)*
   - Organization settings
   - Notification preferences
   - Calendar feed generation
   - Vocabulary customization

7. **[Troubleshooting Guide](./08-troubleshooting.md)** *(Coming Soon)*
   - Common issues from Waves 31-32
   - RLS policy violations
   - Control Desk errors
   - Notification page crashes

---

## 🚀 Quick Start Paths

### For New Users (Evaluating Timebreez)
1. Start with **[Demo Mode](./01-demo-mode-onboarding.md)** - Get instant access, no signup
2. Explore **[Control Desk](./05-control-desk-operations.md)** - See real-time room status
3. Try **[Daily Reconciliation](./04-daily-reconciliation.md)** - Understand attendance workflow

### For Irish Childcare Providers
1. **[Session Scheduling](./02-session-scheduling-ecce-aims.md)** - Configure ECCE/AIMS
2. **[Control Desk](./05-control-desk-operations.md)** - Monitor session compliance
3. **[Cover Staff](./03-cover-staff-dispatch.md)** - Manage floaters for breaks

### For Managers Setting Up Operations
1. **[Cover Staff](./03-cover-staff-dispatch.md)** - Designate floaters
2. **[Control Desk](./05-control-desk-operations.md)** - Monitor staffing
3. **[Daily Reconciliation](./04-daily-reconciliation.md)** - Approve payroll

---

## 🎯 Common Scenarios

### I want to...
- **Try Timebreez without signing up** → [Demo Mode](./01-demo-mode-onboarding.md)
- **Set up ECCE sessions for my preschool** → [Session Scheduling](./02-session-scheduling-ecce-aims.md)
- **Deploy cover staff for breaks** → [Cover Staff Dispatch](./03-cover-staff-dispatch.md)
- **Reconcile attendance vs schedule** → [Daily Reconciliation](./04-daily-reconciliation.md)
- **Monitor room staffing in real-time** → [Control Desk](./05-control-desk-operations.md)
- **Fix "No rooms configured" error** → [Troubleshooting](./08-troubleshooting.md) *(Coming Soon)*

---

## 🔍 Feature Coverage Matrix

| Feature | Guide | Waves | Demo Fixes |
|---------|-------|-------|------------|
| **Demo Mode Auto-Login** | [Demo Mode](./01-demo-mode-onboarding.md) | 31-33 | Fix #1-8, I-DEMO-001 through I-DEMO-007 |
| **ECCE Session Templates** | [Session Scheduling](./02-session-scheduling-ecce-aims.md) | 26 | - |
| **AIMS Grant Tracking** | [Session Scheduling](./02-session-scheduling-ecce-aims.md) | 26 | - |
| **Cover Staff Flagging** | [Cover Staff](./03-cover-staff-dispatch.md) | 27 | - |
| **Room Dispatch Log** | [Cover Staff](./03-cover-staff-dispatch.md) | 27 | - |
| **Reconciliation UI** | [Daily Reconciliation](./04-daily-reconciliation.md) | 28-30 | - |
| **Operational Decisions** | [Daily Reconciliation](./04-daily-reconciliation.md) | 28-30 | I-RECON-001 through I-RECON-007 |
| **Control Desk Monitoring** | [Control Desk](./05-control-desk-operations.md) | 24-25 | Fix #1, I-DEMO-005 |
| **Room Status Indicators** | [Control Desk](./05-control-desk-operations.md) | 24-25 | - |
| **Who's In Panel** | [Control Desk](./05-control-desk-operations.md) | 28 | - |

---

## 📖 How to Use These Guides

### Format Conventions

**Gherkin Scenarios:**
All guides include Gherkin-style scenarios that map directly to our E2E tests. These describe the exact behavior you can expect.

**Step-by-Step Instructions:**
Each scenario has numbered steps with:
- **Look for:** What UI element to find
- **Click/Enter:** What action to take
- **Expected:** What should happen

**Common Issues:**
Every guide includes troubleshooting for common problems with ❌ Problem / ✅ Solution format.

**Screenshots:**
Placeholders for screenshots (to be added) are marked with `[Screenshot: Description]`.

### Navigation

**Links:**
All guides cross-reference related topics. Click links to jump between guides.

**Table of Contents:**
Each guide has a "Quick Start (TL;DR)" section at the top for experienced users.

**Glossary:**
Key terms are explained in context. Hover for definitions in the web version.

---

## 🧪 Demo Mode Testing

All guides can be tested in **Demo Mode** at `www.timebreez.com/login`:

- **Demo Organization:** Sunshine Early Learning Centre
- **Demo Manager:** Sandra Murphy (demo@timebreez.com)
- **7 Rooms:** Baby Room, Baby Steps, Wobblers, Toddlers, Preschool, ECC, Afterschool
- **10 Employees:** Emma, Lisa, Aoife, and more
- **Sample Data:** Leave requests, shifts, sessions, dispatches
- **Reset:** Daily at midnight UTC

**What works in Demo Mode:**
- ✅ All Control Desk features
- ✅ All Session Scheduling features
- ✅ All Cover Staff Dispatch features
- ✅ All Daily Reconciliation features
- ✅ All Settings pages (Notifications, Calendar Feeds, etc.)

**What doesn't work:**
- ❌ Personal data persistence (resets daily)
- ❌ WhatsApp notifications (requires business account)
- ❌ Real Paxton integration (uses demo attendance data)

---

## 🛠️ Troubleshooting

### All 8 Demo Fixes (Waves 31-32)

| Fix | Issue | Solution | Guide |
|-----|-------|----------|-------|
| #1 | Control Desk shows "No rooms" | RLS on `get_room_snapshots()` | [Control Desk](./05-control-desk-operations.md#troubleshooting) |
| #2 | Leave Coverage shows "No room assignment" | Employee room assignments | [Demo Mode](./01-demo-mode-onboarding.md#troubleshooting) |
| #3 | Org Notifications crashes | RLS on `notification_rules` | [Settings](./07-settings-and-configuration.md) *(Coming Soon)* |
| #4 | My Notifications crashes | RLS on `notification_preferences` | [Settings](./07-settings-and-configuration.md) *(Coming Soon)* |
| #5 | Leave Types not editable | UUID validation | [Demo Mode](./01-demo-mode-onboarding.md#troubleshooting) |
| #6 | Calendar Feed doesn't generate | `generate_calendar_feed_token` RPC | [Settings](./07-settings-and-configuration.md) *(Coming Soon)* |
| #7 | Burnout Board empty | Demo data seeding | [Demo Mode](./01-demo-mode-onboarding.md) |
| #8 | Vocabulary shows placeholders | `get_vocabulary_defaults()` | [Demo Mode](./01-demo-mode-onboarding.md) |

### All 7 Invariants (Demo Mode)

| Invariant | Description | Validated By |
|-----------|-------------|--------------|
| **I-DEMO-001** | Demo org ID is `00...001` | E2E comprehensive test |
| **I-DEMO-002** | Relative dates (CURRENT_DATE) | E2E comprehensive test |
| **I-DEMO-003** | No RLS violations | E2E comprehensive test |
| **I-DEMO-004** | All employees have room assignments | E2E comprehensive test |
| **I-DEMO-005** | Control Desk shows 7 rooms | E2E comprehensive test |
| **I-DEMO-006** | Leave requests show coverage | E2E comprehensive test |
| **I-DEMO-007** | No unfinished features exposed | E2E comprehensive test |

---

## 📞 Support

### Self-Service
1. Check the [Troubleshooting Guide](./08-troubleshooting.md) *(Coming Soon)*
2. Search this documentation (Ctrl+F)
3. Try the feature in [Demo Mode](./01-demo-mode-onboarding.md)

### Contact Support
- **Email:** support@timebreez.com
- **Live Demo:** www.timebreez.com/login
- **Book a Call:** Schedule a 15-min walkthrough
- **GitHub Issues:** Report bugs at github.com/Hulupeep/timebreez/issues

### Community
- **Irish Childcare:** Join our ECCE provider community
- **Feature Requests:** Vote on roadmap items
- **Feedback:** Help us improve these guides

---

## 📝 Contributing to Docs

Found an error? Want to add screenshots? Help improve these guides:

1. **Report Issues:** support@timebreez.com with subject "Help Docs Feedback"
2. **Suggest Edits:** Submit suggestions for clarity improvements
3. **Add Screenshots:** Send annotated screenshots for any scenario
4. **Request Topics:** Tell us what's missing

---

## 🚧 Coming Soon

Guides currently in development:

6. **Settings and Configuration** - Org settings, notifications, calendar feeds
7. **Troubleshooting Guide** - Comprehensive troubleshooting for all 8 fixes
8. **Leave Management** - Full leave request workflow
9. **WhatsApp Integration** - Staff notifications (when available)
10. **Payroll Export** - Collsoft integration for Irish payroll

---

## 📊 Version History

- **v1.0.0** (2026-02-01) - Initial release
  - Covers Waves 24-33
  - 5 complete guides
  - All 8 demo fixes documented
  - All 7 invariants validated

---

**Last Updated:** 2026-02-01
**Covers:** Waves 24-33
**Status:** Production Ready ✅
