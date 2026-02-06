# Paxton Net2 Integration - Automatic Attendance Tracking

## Who This Is For
**Childcare Managers and IT Administrators** who need to set up and use Paxton Net2 badge readers for real-time staff attendance tracking.

## What You'll Learn
- What Paxton Net2 is and how it connects to Timebreez
- Mapping physical badge readers to rooms (site discovery)
- Viewing real-time presence on the Reality Panel
- Handling Shift End Nudge alerts (forgot to clock out)
- Using the compliance audit trail
- Troubleshooting badge events

## Prerequisites
- Manager or Admin role in Timebreez
- Paxton Net2 server installed on-site with network access
- Badge readers physically installed at entry/exit points
- Employees issued Paxton key fobs or cards
- IT administrator has Paxton Net2 server credentials

---

## Quick Start (TL;DR)

1. Go to **Settings > Paxton Integration**
2. Enter your Paxton Net2 **server address** and **API key**
3. Click **"Discover Readers"** to detect all badge readers on the network
4. **Map each reader** to a room (e.g., "Front Door Reader" -> "Baby Room entrance")
5. Staff badge IN/OUT events flow to **Control Desk** in real-time
6. View the **Reality Panel** for live presence across all rooms
7. Respond to **Shift End Nudge** alerts when staff forget to badge OUT

---

## Understanding Paxton Net2

### What is Paxton Net2?

**Paxton Net2** is a building access control system that uses badge readers (key fobs, cards, or PIN pads) to track who enters and exits your facility. Timebreez integrates with Paxton to:

- **Automatically track attendance** - No manual clock-in needed
- **Update room presence counts** - Control Desk shows real-time present counts
- **Generate audit trails** - Compliance-ready logs of who was where and when
- **Trigger alerts** - Shift End Nudge when staff forget to badge OUT

**How it works:**

| Step | What Happens |
|------|-------------|
| 1. Badge IN | Staff taps key fob on reader at building entrance |
| 2. Event sent | Paxton Net2 server records the event |
| 3. Timebreez syncs | Timebreez polls Paxton for new events (every 30 seconds) |
| 4. Presence updated | Control Desk "Present" count increases by 1 |
| 5. Badge OUT | Staff taps key fob when leaving |
| 6. Presence updated | Control Desk "Present" count decreases by 1 |

### Reader Types

| Reader Location | Purpose | Mapping |
|----------------|---------|---------|
| **Front Door** | Building entry/exit | Maps to "On Site" status |
| **Room Door** | Room entry/exit | Maps to specific room presence |
| **Staff Area** | Break room, office | Maps to "On Break" status |
| **External Gate** | Car park, garden | Maps to "Off Site" status |

---

## Step-by-Step Guides

### Scenario 1: Map Paxton Readers to Rooms

**When to use this:** Initial setup or when you install new badge readers

**Gherkin Scenario:**
```gherkin
Given I have 4 Paxton readers installed in my facility
When I go to Settings > Paxton Integration
And I click "Discover Readers"
Then I see all 4 readers listed with their hardware IDs
When I map "Reader A" to "Baby Room"
And I map "Reader B" to "Toddlers"
And I save the mapping
Then badge events from Reader A update Baby Room presence
And badge events from Reader B update Toddlers presence
```

**Steps:**

1. **Navigate to Paxton Integration settings**
   - **Click:** Settings > Paxton Integration in the sidebar
   - **Expected:** Paxton configuration page loads

2. **Enter Paxton server details** (first time only)
   - **Server Address:** Enter your Paxton Net2 server IP or hostname (e.g., `192.168.1.100`)
   - **API Key:** Enter the API key from your Paxton Net2 configuration
   - **Click:** "Test Connection"
   - **Expected:** Green checkmark with "Connected to Paxton Net2 server"

3. **Click "Discover Readers"**
   - **Click:** Blue "Discover Readers" button
   - **Expected:** Loading spinner, then a list of detected readers appears
   - **Example output:**
     - Reader 1: "Front Door" (Hardware ID: PX-001)
     - Reader 2: "Baby Room Door" (Hardware ID: PX-002)
     - Reader 3: "Toddlers Door" (Hardware ID: PX-003)
     - Reader 4: "Staff Room" (Hardware ID: PX-004)

4. **Map each reader to a room**
   - **For each reader row:**
     - **Click:** Room dropdown next to the reader name
     - **Select:** The corresponding Timebreez room
     - **Example:** "Baby Room Door" -> "Baby Room"
   - **Special mappings:**
     - "Front Door" -> "Building Entry" (tracks on-site status)
     - "Staff Room" -> "Break Area" (tracks break status)
   - **Expected:** Each reader has a room assignment

5. **Save the mapping**
   - **Click:** "Save Reader Mapping" button
   - **Expected:** Success toast "Reader mapping saved successfully"

6. **Verify events are flowing**
   - **Ask a staff member** to badge IN at a mapped reader
   - **Check Control Desk:** Present count should increase within 30 seconds
   - **Expected:** Badge event reflected on Control Desk

**Screenshots:** [Screenshot: Reader discovery and mapping interface]

**Common Issues:**
- Problem: "Discover Readers" finds 0 readers
  Solution: Verify Paxton Net2 server is running and the server address is correct. Check network connectivity between Timebreez and the Paxton server.

- Problem: "Connection refused" error
  Solution: Verify the API key is correct. Check that the Paxton Net2 server has API access enabled. Confirm no firewall is blocking the connection.

---

### Scenario 2: View Live Presence on the Reality Panel

**When to use this:** Monitor who is on-site and in which rooms right now

**Gherkin Scenario:**
```gherkin
Given Paxton readers are mapped to rooms
And 8 staff have badged IN today
When I view the Reality Panel on Control Desk
Then I see 8 staff listed with their current location
And each entry shows badge IN time, room assignment, and shift status
```

**Steps:**

1. **Navigate to Control Desk**
   - **Click:** "Control Desk" in the sidebar
   - **Expected:** Room tiles and panels load

2. **Find the Reality Panel**
   - **Look for:** Panel labeled "Reality Panel" or "Live Presence"
   - **Location:** Usually on the right side of Control Desk
   - **Expected:** Panel visible with staff entries

3. **Read the presence data**
   - **Each row shows:**
     - **Employee Name:** Emma Murphy
     - **Current Location:** Baby Room
     - **Badge IN Time:** 08:58
     - **Shift Hours:** 09:00 - 17:00
     - **Status Indicator:**
       - Green dot: On-site, in assigned room
       - Blue dot: On-site, in different room (dispatched)
       - Orange dot: On break (in break area)
       - Gray dot: Badge OUT recorded
   - **Expected:** All badged-in staff visible

4. **Filter by status** (if available)
   - **Look for:** Filter buttons: "All", "Present", "On Break", "Left"
   - **Click:** Filter to narrow the list
   - **Expected:** List updates to show filtered staff only

5. **Check the summary counts**
   - **Look for:** Summary bar at top of panel
   - **Example:** "8 on site | 6 in rooms | 1 on break | 1 in transit"
   - **Expected:** Counts match the detail list

**Screenshots:** [Screenshot: Reality Panel showing live presence data]

**Common Issues:**
- Problem: Reality Panel shows stale data
  Solution: Click the Refresh button on the panel. Verify Paxton sync is running (check Settings > Paxton Integration for last sync timestamp).

- Problem: Staff shows "Unknown Location"
  Solution: The badge reader they used is not mapped to a room. Go to Settings > Paxton Integration and map the unassigned reader.

---

### Scenario 3: Handle Shift End Nudge

**When to use this:** Staff forgot to badge OUT at end of shift

**Gherkin Scenario:**
```gherkin
Given Emma Murphy's shift ends at 17:00
And it is now 17:15
And Emma has not badged OUT
When the system detects this
Then a "Shift End Nudge" alert appears on Control Desk
And the alert shows "Emma Murphy - shift ended 15 min ago, no badge OUT"
When I click "Resolve" on the alert
Then I can mark her as "Left at shift end" or "Still on site"
```

**Steps:**

1. **Identify Shift End Nudge alerts**
   - **Look for:** Alert banner or badge on Control Desk
   - **Label:** "Shift End Nudge" or "Overdue Badge OUT"
   - **Color:** Orange or amber alert
   - **Expected:** Alert appears 15 minutes after shift end time if no badge OUT

2. **View the alert details**
   - **Click:** The alert to expand details
   - **Expected:** You see:
     - **Employee Name:** Emma Murphy
     - **Shift End:** 17:00
     - **Current Time:** 17:15
     - **Last Badge Event:** Badge IN at 08:58 (no OUT recorded)
     - **Overdue By:** 15 minutes

3. **Resolve the alert**
   - **Option A - "Left at shift end":**
     - Staff actually left but forgot to badge OUT
     - **Action:** Click "Left at Shift End"
     - **Result:** System records badge OUT at 17:00 (shift end time)
   - **Option B - "Still on site":**
     - Staff is still working (overtime or delayed departure)
     - **Action:** Click "Still On Site"
     - **Result:** Alert is snoozed for 30 minutes, then re-alerts
   - **Option C - "Custom time":**
     - You know when they left
     - **Action:** Enter the actual departure time (e.g., 17:10)
     - **Result:** System records badge OUT at entered time

4. **Verify resolution**
   - **Check Reality Panel:** Employee should show correct status
   - **Check attendance log:** Badge OUT event recorded with resolution method
   - **Expected:** Alert clears, attendance data is accurate

**Screenshots:** [Screenshot: Shift End Nudge alert with resolution options]

**Common Issues:**
- Problem: Nudge alerts appear for staff who are still working
  Solution: Click "Still On Site" to snooze. If this happens often, consider adjusting the nudge delay in Settings > Paxton Integration > Alert Timing (default: 15 minutes after shift end).

- Problem: Too many nudge alerts every day
  Solution: Common with staff who use external exits without readers. Map all exit points to readers, or increase the nudge delay to 30 minutes.

---

### Scenario 4: Check the Compliance Audit Trail

**When to use this:** Preparing for a Tusla inspection or reviewing attendance records

**Gherkin Scenario:**
```gherkin
Given I need to prove staffing ratios were maintained on January 15th
When I go to Reports > Attendance Audit Trail
And I filter by date "2026-01-15"
Then I see a timeline of all badge events for every staff member
And I see room presence periods (who was in which room, when)
And I can export the report as PDF for Tusla
```

**Steps:**

1. **Navigate to Attendance Audit Trail**
   - **Click:** Reports > Attendance Audit Trail (or Settings > Paxton Integration > Audit Log)
   - **Expected:** Audit trail page loads with date filter

2. **Select the date range**
   - **Date From:** Select start date (e.g., 2026-01-15)
   - **Date To:** Select end date (e.g., 2026-01-15 for single day)
   - **Click:** "Search" or "Filter"
   - **Expected:** Timeline of events loads

3. **Review the audit timeline**
   - **Format:** Chronological list of badge events
   - **Each entry shows:**
     - **Timestamp:** 08:58:23
     - **Employee:** Emma Murphy
     - **Event:** Badge IN
     - **Reader:** "Front Door" (PX-001)
     - **Room Mapped:** Building Entry
     - **Source:** Paxton Net2 (automatic)
   - **Expected:** Complete timeline for selected date

4. **Check room presence periods**
   - **Look for:** "Room Presence" tab or section
   - **Format:** Per-employee timeline showing room assignments:
     - Emma Murphy: Baby Room 09:00 - 12:00, Break 12:00 - 12:30, Baby Room 12:30 - 17:00
   - **Expected:** Continuous timeline with no gaps (or gaps flagged)

5. **Export for compliance**
   - **Click:** "Export PDF" or "Export CSV" button
   - **Expected:** File downloads with full audit trail
   - **Use for:** Tusla inspections, internal audits, payroll verification

6. **Verify ratio compliance** (optional)
   - **Look for:** "Ratio Check" column or section
   - **Shows:** Whether required ratio was met at each point in time
   - **GREEN entries:** Ratio maintained
   - **RED entries:** Ratio breach detected (with duration)
   - **Expected:** Compliance status for each room at each time interval

**Screenshots:** [Screenshot: Attendance audit trail with timeline view]

**Common Issues:**
- Problem: Gaps in the audit trail (missing badge events)
  Solution: Check if the Paxton server had downtime during the gap. Missing events cannot be recovered from Paxton after 24 hours. Use manual attendance entries to fill gaps.

- Problem: Export PDF is blank or incomplete
  Solution: Ensure the date range is correct and events exist. Large date ranges (over 30 days) may time out. Export in smaller chunks.

---

## Troubleshooting

### Issue: Paxton connection lost
**Symptoms:** Control Desk present counts stop updating, "Paxton Offline" indicator appears
**Cause:** Network issue between Timebreez and Paxton Net2 server
**Solution:**
1. Check Paxton Net2 server is running (ping the server address)
2. Verify network connectivity (firewall rules, VPN, etc.)
3. Go to Settings > Paxton Integration and click "Test Connection"
4. If connection fails, contact your IT administrator
5. Badge events will backfill once connection is restored

---

### Issue: Badge events delayed by more than 2 minutes
**Symptoms:** Staff badges IN but present count updates slowly
**Cause:** Polling interval too long, or Paxton server under load
**Solution:**
1. Check Settings > Paxton Integration > Sync Interval (default: 30 seconds)
2. Reduce interval to 15 seconds if needed (increases server load)
3. Check Paxton Net2 server performance (CPU, memory)
4. If delays persist, contact Paxton support

---

### Issue: Wrong room assigned to badge event
**Symptoms:** Staff badges IN at Baby Room door but appears in Toddlers
**Cause:** Reader-to-room mapping is incorrect
**Solution:**
1. Go to Settings > Paxton Integration > Reader Mapping
2. Verify which hardware ID corresponds to which physical reader
3. Correct the room mapping
4. Save and test with a fresh badge event

---

### Issue: Staff shows as present after leaving
**Symptoms:** Employee badged OUT but still appears in Reality Panel
**Cause:** Badge OUT event not received, or reader malfunction
**Solution:**
1. Check if the exit reader is mapped (unrecognized readers are ignored)
2. Verify badge OUT event exists in Paxton Net2 logs
3. If event missing in Paxton, the reader may have a hardware issue
4. Manually resolve via Shift End Nudge or Daily Reconciliation

---

### Issue: Shift End Nudge not appearing
**Symptoms:** Staff overdue but no nudge alert
**Cause:** Nudge feature disabled, or alert timing misconfigured
**Solution:**
1. Go to Settings > Paxton Integration > Alert Timing
2. Verify "Shift End Nudge" is enabled
3. Check the delay setting (default: 15 minutes after shift end)
4. Ensure staff has an active shift for today (no shift = no nudge)

---

## Related Guides
- [Control Desk Operations](./05-control-desk-operations.md)
- [Daily Reconciliation](./04-daily-reconciliation.md)
- [Cover Staff Dispatch](./03-cover-staff-dispatch.md)
- [Troubleshooting Guide](./08-troubleshooting.md)

## Need More Help?
- **Timebreez Support:** support@timebreez.com
- **Paxton Net2 Support:** www.paxton-access.com/support
- **Demo mode:** www.timebreez.com/login (see simulated Paxton events in demo org)
- **Book a call:** Schedule a 15-min walkthrough of Paxton integration setup
