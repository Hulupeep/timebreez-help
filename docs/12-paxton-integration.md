# Entrance Security & Paxton Net2 - Automatic Attendance Tracking

## Who This Is For
**Childcare Managers and IT Administrators** who need to set up and use Paxton Net2 badge readers for real-time staff attendance tracking, and understand how entrance security feeds into Timebreez.

## What You'll Learn
- What Paxton Net2 is and how it connects to Timebreez
- How the on-premises connector bridges Paxton events into Timebreez
- Setting up reader mappings (which reader controls which door)
- Linking badge cards to employees
- Monitoring connector health
- Using the Live Entry Feed to spot mismatches and unknown badges
- How Paxton works alongside NFC scanning
- Resolving feed alerts as a manager
- Troubleshooting common issues

## Prerequisites
- Manager or Admin role in Timebreez
- Paxton Net2 system installed on-site
- Badge readers physically installed at entry/exit points
- Employees issued Paxton key fobs or cards
- On-premises connector software installed (provided by Timebreez)

---

## Quick Start (TL;DR)

1. Install the **Timebreez connector** on a machine that can reach your Paxton Net2 server
2. The connector sends badge events and heartbeats to Timebreez automatically
3. Go to **Attendance > Reader Mappings** to map each reader to a role (building entry, room entry, etc.)
4. Go to **Attendance > Card Mappings** to link each badge card number to an employee
5. Badge events now flow to the **Live Entry Feed** on Control Desk in real-time
6. The system automatically detects **mismatches** (wrong room), **unknown badges**, and **unscheduled** staff
7. Managers resolve alerts directly from the Live Entry Feed panel

---

## Understanding the Architecture

### What is Paxton Net2?

**Paxton Net2** is a building access control system that uses badge readers (key fobs, cards, or PIN pads) to track who enters and exits your facility. Timebreez integrates with Paxton to:

- **Automatically track attendance** - No manual clock-in needed
- **Update room presence** - Control Desk shows who is where, right now
- **Detect problems** - Wrong room, unknown badge, unscheduled staff flagged instantly
- **Generate audit trails** - Compliance-ready logs of who was where and when

### How Events Flow

| Step | What Happens | Where |
|------|-------------|-------|
| 1. Badge tap | Staff taps key fob on a reader | Physical reader |
| 2. Paxton records | Net2 server logs the access event | On-premises |
| 3. Connector syncs | Timebreez connector picks up the event and sends it | On-premises → Cloud |
| 4. Raw event stored | Event saved to `paxton_events` with reader ID, card number, timestamp | Timebreez backend |
| 5. Bridge resolves | System maps reader → role, card → employee, and creates an attendance event | Timebreez backend |
| 6. Feed detects | Live Entry Feed compares the event against today's schedule | Timebreez backend |
| 7. Manager sees | Event appears on Control Desk with status: OK, Mismatch, Unknown, or Unscheduled | Control Desk UI |

### Paxton Event Types

Not all badge events mean the same thing. Timebreez records five event types from Paxton:

| Event Type | Meaning | What Timebreez Does |
|-----------|---------|-------------------|
| **Access Granted** | Badge accepted, door opened | Creates attendance event (clock in/out or room entry/exit) |
| **Access Denied** | Badge rejected | Logged but no attendance event created |
| **Door Forced** | Door opened without a badge | Logged as security alert |
| **Door Held Open** | Door left open too long | Logged as security alert |
| **Anti-Passback** | Badge used twice without exiting | Logged, may indicate tailgating |

Only **Access Granted** events create attendance records. All others are stored for security auditing.

### Reader Roles

Each physical reader is assigned a **semantic role** that tells Timebreez what kind of event it represents:

| Role | What It Means | Attendance Event Created |
|------|-------------|------------------------|
| **Building Entry** | Front door, main entrance | Clock In |
| **Building Exit** | Front door (exit side), car park exit | Clock Out |
| **Room Entry** | Door into Baby Room, Toddlers, etc. | Room Entry |
| **Room Exit** | Door leaving a specific room | Room Exit |
| **Zone Entry** | Garden gate, outdoor area | Logged only (no attendance event) |
| **Zone Exit** | Leaving a zone area | Logged only (no attendance event) |

---

## Setting Up Paxton Integration

### Step 1: Install the On-Premises Connector

The Timebreez connector is a lightweight service that runs on a Windows or Linux machine in your facility. It reads events from your Paxton Net2 server and sends them to Timebreez.

**What the connector does:**
- Polls your Paxton Net2 server for new events
- Sends each event to Timebreez via secure HTTPS
- Sends a heartbeat every 60 seconds so Timebreez knows the connector is alive
- Works offline — queues events if internet drops, sends them when connectivity returns

**After installation:**
- The connector appears on the **Connector Status** panel in Timebreez
- Status shows **Online** (green), **Degraded** (amber), or **Offline** (red)
- You can see the connector version, total events synced, and last sync time

---

### Step 2: Map Readers to Roles

**When to use this:** Initial setup, or when you install new badge readers.

```gherkin
Scenario: Map Paxton readers to rooms
  Given I have 5 Paxton readers installed in my facility
  When I go to Attendance > Reader Mappings
  And I add reader "PAX-READER-001" with role "Building Entry"
  And I add reader "PAX-READER-003" with role "Room Entry" for Baby Room
  Then badge events from PAX-READER-001 create Clock In events
  And badge events from PAX-READER-003 create Room Entry events for Baby Room
```

**Steps:**

1. **Navigate to Reader Mappings**
   - **Click:** Attendance > Reader Mappings in the sidebar
   - **Expected:** The Reader Mapping Manager loads with a table of existing mappings

2. **Add a new reader**
   - **Click:** the "Add Reader" button
   - **Fill in the form:**
     - **Reader ID:** The hardware identifier from your Paxton system (e.g., `PAX-READER-001`). This is shown in monospace font for clarity
     - **Reader Name:** A friendly name (e.g., "Front Door In", "Baby Room Door")
     - **Semantic Role:** Choose from the dropdown — Building Entry, Building Exit, Room Entry, Room Exit, Zone Entry, or Zone Exit
     - **Room:** If you selected Room Entry or Room Exit, a room picker appears. Select the corresponding Timebreez room (e.g., Baby Room)
   - **Click:** Submit
   - **Expected:** The reader appears in the table with its role and room assignment

3. **Repeat for all readers**
   - A typical facility has:
     - 1-2 building entry/exit readers (front door)
     - 1 reader per room (Baby Room, Toddlers, Preschool, etc.)
     - Optional: break room, garden gate readers

4. **Search and filter**
   - Use the search box to find readers by ID, name, or role
   - **Expected:** Table filters as you type

5. **Edit or delete a mapping**
   - **Edit:** Click the edit button on any row to change the role or room
   - **Delete:** Click delete, then confirm in the 2-step confirmation dialog

**Common Issues:**
- ❌ Problem: You don't know the reader IDs
  ✅ Solution: Check your Paxton Net2 administration software. Reader IDs are listed under Doors > Properties. They match the hardware serial number.

- ❌ Problem: Room picker doesn't appear
  ✅ Solution: The room picker only shows for Room Entry and Room Exit roles. Building-level readers don't need a room assignment.

---

### Step 3: Link Badge Cards to Employees

**When to use this:** When issuing new key fobs, or onboarding new staff.

```gherkin
Scenario: Link a badge card to an employee
  Given Sandra has issued card number "CARD-1001" to Emma Murphy
  When I go to Attendance > Card Mappings
  And I add card "CARD-1001" mapped to Emma Murphy
  Then badge events with card "CARD-1001" are attributed to Emma Murphy
```

**Steps:**

1. **Navigate to Card Mappings**
   - **Click:** Attendance > Card Mappings in the sidebar
   - **Expected:** Card Mapping Manager loads with a table of linked cards

2. **Add a new card**
   - **Click:** the "Add Card" button
   - **Fill in the form:**
     - **Card Number:** The number printed on or programmed into the key fob (e.g., `CARD-1001` or `12345678`)
     - **Employee:** Select the employee from the dropdown
   - **Click:** Submit
   - **Expected:** The card appears in the table linked to the employee

3. **Deactivate a card** (lost fob, staff leaving)
   - **Click:** the toggle button on the card's row
   - **Expected:** Status changes from Active to Inactive
   - The card is not deleted — its history is preserved for audit purposes, but new events from this card will appear as "unknown badge" on the Live Entry Feed

4. **Delete a card** (if added in error)
   - **Click:** Delete, then confirm
   - **Expected:** Card removed permanently

**Common Issues:**
- ❌ Problem: Badge events show "Unknown Badge" even after linking
  ✅ Solution: Verify the card number matches exactly. Card numbers are case-sensitive. Check for leading zeros.

- ❌ Problem: Same card number linked to two employees
  ✅ Solution: Each card number must be unique per organization. Deactivate the old mapping before creating a new one.

---

### Step 4: Monitor Connector Health

**When to use this:** Daily check, or when badge events stop appearing.

The **Connector Status Panel** shows the health of your on-premises connector.

**What you'll see for each connector:**

| Field | Meaning |
|-------|---------|
| **Connector ID** | Unique identifier for the connector instance |
| **Status** | Online (green with animated dot), Offline (red), or Degraded (amber) |
| **Version** | Software version of the connector |
| **Last Heartbeat** | How long ago the connector last checked in (e.g., "2 minutes ago") |
| **Events Synced** | Total number of events sent to Timebreez (e.g., "1,247") |
| **Last Sync** | When the last batch of events was sent |

**The panel auto-refreshes every 60 seconds.**

**When to worry:**
- **Last Heartbeat > 5 minutes:** The connector may have stopped. Check the machine it runs on.
- **Status: Degraded:** The connector is running but experiencing errors (e.g., Paxton server not responding).
- **Status: Offline:** No heartbeat received. The connector process has likely stopped.

---

## Using the Live Entry Feed

The **Live Entry Feed** is the right-hand panel on the Control Desk. It shows every badge event as it happens, with automatic mismatch detection.

### Feed Status Colours

Every event in the feed gets one of four statuses:

| Status | Colour | Meaning | Example |
|--------|--------|---------|---------|
| **OK** | Green | Employee badged in at expected location | Emma badged into Baby Room, she's scheduled there today |
| **Mismatch** | Amber | Employee badged into a room they're NOT scheduled for | Mary badged into Toddlers but she's rostered for Baby Room |
| **Unknown Badge** | Red | Badge card has no employee linked | Card "CARD-9999" tapped — no one is mapped to it |
| **Unscheduled** | Yellow | Employee badged in but has no shift today | Sarah badged in at the building entrance on her day off |

### Resolving Feed Alerts

As a manager, you can take action on any non-OK event directly from the feed.

```gherkin
Scenario: Resolve a room mismatch
  Given Mary is scheduled for Baby Room today
  And Mary badges into Toddlers at 10:30
  When I see the mismatch alert on the Live Entry Feed
  And I click "Assign to Room" and select Toddlers
  Then the event is marked as resolved
  And the reason is recorded for compliance
```

**Available resolution actions by status:**

| Feed Status | Available Actions |
|-------------|------------------|
| **Mismatch** | Assign to Room (update their schedule), Ignore (with reason) |
| **Unknown Badge** | Mark as Visitor, Link Badge to Staff, Ignore (with reason) |
| **Unscheduled** | Assign to Room (give them a shift), Note as Overtime, Ignore (with reason) |

**Steps to resolve:**

1. **Find the alert** in the Live Entry Feed (amber/red/yellow rows stand out)
2. **Click** the event row to expand it
3. **Choose** a resolution action from the buttons
4. **Enter a reason** if required (mandatory for "Ignore" actions)
5. **Expected:** The event shows "Resolved" with your name and timestamp

### Feed Filters

- **Time window:** Show events from the last 15, 30, 60, or 120 minutes
- **Alerts only:** Toggle to hide OK events and show only problems
- **Paxton status indicator:** WiFi icon shows whether the connector is connected (last event < 5 minutes ago) or disconnected

---

## Paxton + NFC: Working Together

Timebreez supports **multiple attendance sources** that work together. Paxton and NFC scanning serve different purposes:

| Feature | Paxton Net2 | NFC Scanning |
|---------|------------|-------------|
| **How it works** | Badge readers at doors (automatic) | Staff taps phone on NFC tag (manual) |
| **Best for** | Building entry/exit, room tracking | Break rooms, outdoor areas, mobile check-in |
| **Infrastructure** | Requires Paxton hardware + on-prem connector | Requires NFC tags (stickers) + staff smartphones |
| **Data source** | `paxton` in attendance events | `nfc` in attendance events |
| **Priority** | Highest (overrides NFC and manual entries) | Medium (overrides manual, but not Paxton) |

**Priority resolution:** If both Paxton and NFC record an event for the same employee at the same time, Paxton wins. The NFC event is marked as "superseded" to avoid double-counting. The priority order is:

1. **Paxton** (highest — automatic, hardware-backed)
2. **NFC** (medium — staff-initiated, phone-based)
3. **Manual** (lowest — manager override)

This means you can use NFC tags in areas without Paxton readers (garden, break room) and the data merges seamlessly in the attendance log.

---

## Understanding the Control Desk Integration

Paxton events flow directly into the Control Desk, powering several features:

### Room Tiles
Each room tile on the Control Desk shows a **present count** — the number of staff currently in that room based on badge events. When a staff member badges into a room, the count updates in real-time via Supabase Realtime subscriptions (no polling delay).

### Alert Summary Bar
The header bar shows colour-coded counts:
- **RED** count: Rooms with staffing breaches or unknown badges
- **AMBER** count: Rooms with mismatches or warnings
- **GREEN** count: Rooms with correct staffing

Click any count to filter the room grid to only rooms with that status.

### Dispatch + Paxton
When you dispatch a cover staff member to a room, the system tracks whether they actually arrive by watching for their badge event at the room reader. The Dispatch Status Tracker shows a live countdown, and the status updates from "Sent" to "Acknowledged" to "Arrived" when the badge event confirms they entered the room.

### Who's In
The **Who's In** panel shows all staff currently on site (based on building entry events without a matching exit). Each entry shows the employee name, how long they've been on site, and their entry location.

---

## Troubleshooting

### Issue: Connector shows Offline
**Symptoms:** Connector Status Panel shows red "Offline" badge, last heartbeat was more than 5 minutes ago.
**Cause:** The connector process has stopped, or the machine has lost internet connectivity.
**Solution:**
1. Check the machine running the connector — is it powered on?
2. Verify internet connectivity from that machine
3. Restart the connector service
4. Check the connector logs for error messages
5. Events will backfill automatically once the connector reconnects

---

### Issue: Badge events show "Unknown Badge"
**Symptoms:** Events appear in the Live Entry Feed with red "Unknown Badge" status.
**Cause:** The card number in the event has no mapping to an employee.
**Solution:**
1. Note the card number from the feed event details
2. Go to **Attendance > Card Mappings**
3. Add a new mapping: enter the card number and select the employee
4. Future events from that card will now be attributed correctly
5. Alternatively, use the "Link Badge to Staff" resolution action directly from the feed

---

### Issue: Wrong room assigned to badge event
**Symptoms:** Staff badges in at Baby Room door but the event shows them in Toddlers.
**Cause:** The reader-to-room mapping is incorrect.
**Solution:**
1. Go to **Attendance > Reader Mappings**
2. Search for the reader ID shown in the event details
3. Click Edit and correct the room assignment
4. Save and verify with a fresh badge event

---

### Issue: Events appear with long delay
**Symptoms:** Staff badges in but the event doesn't appear on Control Desk for several minutes.
**Cause:** Connector sync delay, or the connector is in degraded state.
**Solution:**
1. Check the Connector Status Panel — is the status "Degraded"?
2. Check the "Last Sync" timestamp — if it's old, the connector may be struggling
3. Verify the Paxton Net2 server is responsive
4. The Control Desk uses Supabase Realtime, so once events reach the database, they appear instantly. The delay is between Paxton and the connector.

---

### Issue: Staff shows as present after leaving
**Symptoms:** Employee left the building but still shows in the "Who's In" panel.
**Cause:** They used an exit without a badge reader, or the exit reader isn't mapped.
**Solution:**
1. Check if the exit point has a reader — if not, staff must badge out at the main entrance
2. Verify the exit reader is mapped with role "Building Exit"
3. Use the Daily Reconciliation to manually record the clock-out time
4. Consider adding readers to all exit points used by staff

---

### Issue: Mismatch alerts for legitimately moved staff
**Symptoms:** Feed shows "Mismatch" for a staff member who was asked to help in another room.
**Cause:** Their schedule shows them in Room A, but they badged into Room B.
**Solution:**
1. Click the mismatch event in the Live Entry Feed
2. Click **"Assign to Room"** and select the room they're actually in
3. This updates the record and clears the alert
4. For recurring moves, consider updating the roster to reflect the change

---

## Related Guides
- [Control Desk Operations](./05-control-desk-operations.md) - Full guide to the room grid, alert filters, and kiosk mode
- [Attendance & Presence](./09-attendance-presence.md) - Multi-source attendance tracking (Paxton + NFC + manual)
- [Daily Reconciliation](./04-daily-reconciliation.md) - Resolving attendance discrepancies at end of day
- [Cover Staff Dispatch](./03-cover-staff-dispatch.md) - Dispatching staff to cover gaps detected by the feed
- [Compliance Trail & Audit](./11-compliance-trail-audit.md) - Using attendance data for Tusla compliance
- [Troubleshooting Guide](./08-troubleshooting.md) - General troubleshooting

## Need More Help?
- **Timebreez Support:** support@timebreez.com
- **Paxton Net2 Support:** www.paxton-access.com/support
- **Demo mode:** www.timebreez.com/login (the demo org includes simulated Paxton events so you can explore the full flow)
- **Book a call:** Schedule a 15-minute walkthrough of your Paxton integration setup
