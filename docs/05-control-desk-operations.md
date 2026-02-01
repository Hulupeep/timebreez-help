# Control Desk Operations - Real-Time Room Management

## Who This Is For
**Childcare Managers** who need to monitor room status, staffing ratios, and deployment in real-time.

## What You'll Learn
- Reading room status indicators (GREEN/AMBER/RED)
- Understanding required vs planned vs present counts
- Viewing staff assignments
- Session indicators for ECCE/AIMS rooms
- Coverage warnings
- Who's In panel for attendance

## Prerequisites
- Manager or Admin role in Timebreez
- Rooms configured with capacity and ratios
- Paxton Net2 integration for attendance data

---

## Quick Start (TL;DR)

1. Go to **Control Desk** in sidebar
2. View **7 room tiles** (in demo org)
3. Check **status badges**: GREEN = safe, AMBER = tight, RED = understaffed
4. View **required/planned/present** counts on each tile
5. Click room tile for **staff list** and details
6. Check **Cover Pool panel** for available floaters
7. Use **Who's In panel** to see all badged-in staff

---

## Understanding Control Desk

### What is Control Desk?

The **Control Desk** is your **real-time command center** for monitoring room status and staffing across your entire facility.

**Key Features:**
- **Room tiles** showing status for each room
- **Staff counts** (required, planned, present)
- **Session indicators** (ECCE active/inactive)
- **Cover pool** availability
- **Who's In** attendance panel
- **Color-coded alerts** for understaffing

**Real-time updates:**
- Refreshes every 60 seconds
- Badge IN/OUT events update present count
- Leave approvals update planned count
- Session times update required count

### The 3 Counts Explained

| Count | Meaning | Source |
|-------|---------|--------|
| **Required** | Minimum staff needed for compliance | Child count ÷ ratio (e.g., 12 children ÷ 1:6 = 2 staff) |
| **Planned** | Staff scheduled to work (from roster) | Shift instances for today |
| **Present** | Staff who have badged IN and not OUT | Attendance events from Paxton |

**Example:**
- **Required: 3** (based on 18 children, 1:6 ratio)
- **Planned: 3** (Emma, Lisa, Aoife scheduled)
- **Present: 2** (Emma and Lisa badged in, Aoife not yet arrived)
- **Status: RED** (present < required)

### Status Badge Colors

| Color | Condition | Action |
|-------|-----------|--------|
| **GREEN** | present ≥ required | No action needed |
| **AMBER** | present = required - 1 | Watch closely, dispatch cover if possible |
| **RED** | present < required - 1 | URGENT: Dispatch cover staff immediately |

---

## Step-by-Step Guides

### Scenario 1: View Control Desk

**When to use this:** Start of day, throughout the day for monitoring

**Gherkin Scenario:**
```gherkin
Given I am logged in as a manager
When I navigate to Control Desk
Then I see 7 room tiles (in demo org)
And each tile shows room name, required/planned/present, and status badge
```

**Steps:**

1. **Navigate to Control Desk**
   - **Click:** "Control Desk" in the sidebar
   - **Expected:** Page loads showing room tiles

2. **Verify room tiles appear**
   - **Look for:** 7 tiles (Demo org: Baby Room, Baby Steps, Wobblers, Toddlers, Preschool, ECC, Afterschool)
   - **Expected:** All rooms visible (I-DEMO-005 invariant)

3. **Check tile components**
   - **Each tile shows:**
     - **Room Name** (e.g., "Baby Room")
     - **Required count** (e.g., "3 required")
     - **Planned count** (e.g., "3 planned")
     - **Present count** (e.g., "2 present")
     - **Status badge** (GREEN/AMBER/RED)
     - **Session indicator** (if ECCE session active)
   - **Expected:** All counts visible

4. **Understand the layout**
   - **Grid view:** Tiles arranged in rows (responsive to screen size)
   - **Order:** Usually alphabetical or by room type
   - **Size:** Tiles resize based on viewport

**Screenshots:** [Screenshot: Control Desk with 7 room tiles]

**Common Issues:**
- ❌ Problem: Control Desk shows "No rooms configured"
  ✅ Solution: This was fixed in Wave 31 (I-DEMO-005). Refresh the page. If still broken, verify `get_room_snapshots()` RPC has proper permissions.

---

### Scenario 2: Read Room Status Indicators

**When to use this:** Identify which rooms need attention

**Gherkin Scenario:**
```gherkin
Given Baby Room has required=3, planned=3, present=2
When I view the Baby Room tile
Then I see RED status badge
And the badge shows "Understaffed"
And I know to dispatch cover staff urgently
```

**Steps:**

1. **Find Baby Room tile**
   - **Look for:** Tile labeled "Baby Room"
   - **Expected:** Tile visible

2. **Read the counts**
   - **Required:** 3 (based on 9 children, 1:3 ratio for babies)
   - **Planned:** 3 (Emma, Lisa, Aoife scheduled)
   - **Present:** 2 (Emma and Lisa badged in)
   - **Expected:** Counts displayed clearly

3. **Check the status badge**
   - **Color:** RED
   - **Label:** "Understaffed" or "Critical"
   - **Reason:** present (2) < required (3)
   - **Expected:** Red badge visible

4. **Understand the urgency**
   - **GREEN (present ≥ required):** All good, no action
   - **AMBER (present = required - 1):** Tight, watch for breaks
   - **RED (present < required - 1):** URGENT, compliance risk
   - **Example:** Required 3, Present 2 → RED (1 short)

5. **Take action** (covered in Scenario 6)

**Screenshots:** [Screenshot: Room tile with RED status badge]

**Common Issues:**
- ❌ Problem: Status badge color doesn't match counts
  ✅ Solution:
    1. Refresh the page (data may be stale)
    2. Check calculation: RED if present < required - 1
    3. Verify required count is correct (based on child_count and ratio)

---

### Scenario 3: View Staff Assignments in a Room

**When to use this:** See who's scheduled and who's present

**Gherkin Scenario:**
```gherkin
Given I want to see who's working in Baby Room
When I click the Baby Room tile
Then a modal opens showing:
  - Scheduled staff (Emma, Lisa, Aoife)
  - Present staff (Emma, Lisa) with green checkmarks
  - Absent staff (Aoife) with red X or warning icon
```

**Steps:**

1. **Click a room tile**
   - **Click:** Baby Room tile
   - **Expected:** Room detail modal opens

2. **Review modal contents**
   - **Header:** "Baby Room" with status badge
   - **Staff List Section:**
     - **Scheduled Staff:** List of employees with shifts today
     - **Presence Indicators:**
       - Green checkmark: Badged IN, currently present
       - Gray clock: Shift not started yet
       - Red X: Scheduled but no badge IN
   - **Expected:** All scheduled staff visible

3. **Check individual staff rows**
   - **Example row - Emma Murphy:**
     - **Name:** Emma Murphy
     - **Shift:** 09:00 - 17:00
     - **Status:** ✓ Present (green)
     - **Badge IN:** 08:58
   - **Example row - Aoife O'Brien:**
     - **Name:** Aoife O'Brien
     - **Shift:** 09:00 - 17:00
     - **Status:** ✗ Not present (red)
     - **Badge IN:** (none)

4. **View session info** (if applicable)
   - **Session Hours:** 09:30 - 12:30 (if ECCE session configured)
   - **Ratio:** 1:11
   - **AIMS:** Yes/No
   - **Expected:** Session details visible if room has sessions

5. **Close modal**
   - **Click:** X button or click outside modal
   - **Expected:** Modal closes, return to Control Desk

**Screenshots:** [Screenshot: Room detail modal with staff list]

**Common Issues:**
- ❌ Problem: Modal doesn't open when clicking tile
  ✅ Solution:
    1. Try clicking the tile name (not the counts)
    2. Check browser console for errors
    3. Refresh the page and try again

---

### Scenario 4: Understand Session Indicators

**When to use this:** Verify ECCE sessions are active during correct hours

**Gherkin Scenario:**
```gherkin
Given Preschool room has ECCE Midday session (09:30 - 12:30)
When I view Control Desk at 10:00 AM
Then the Preschool tile shows a "SESSION" indicator badge
And required count includes 1:11 ratio (not normal ratio)
When I view at 1:00 PM (after session)
Then the SESSION indicator is gone
And required count reverts to normal ratio
```

**Steps:**

1. **Find room with session configured**
   - **Example:** Preschool or ECC room
   - **Expected:** Room tile visible

2. **Check current time vs session hours**
   - **ECCE Midday session:** 09:30 - 12:30
   - **Current time:** 10:00 AM (within session hours)
   - **Expected:** Inside session time window

3. **Look for SESSION indicator**
   - **Location:** Badge or icon on room tile
   - **Label:** "SESSION" or "ECCE"
   - **Color:** Often blue or purple
   - **Expected:** SESSION badge visible during session hours

4. **Verify required count uses session ratio**
   - **During session (10:00 AM):**
     - Child count: 22
     - Ratio: 1:11 (ECCE ratio)
     - Required: 22 ÷ 11 = 2 staff
     - **If AIMS enabled:** 2 + 1 = 3 staff
   - **Outside session (1:00 PM):**
     - Child count: 22
     - Ratio: 1:8 (normal preschool ratio)
     - Required: 22 ÷ 8 = 3 staff (rounded up)

5. **Understand the timing**
   - **Before session start:** No indicator, normal ratio
   - **During session:** SESSION badge, 1:11 ratio
   - **After session end:** No indicator, normal ratio

**Screenshots:** [Screenshot: Room tile with SESSION indicator]

**Common Issues:**
- ❌ Problem: SESSION indicator doesn't appear during session hours
  ✅ Solution:
    1. Verify session is configured (Admin > Rooms > Session Scheduling)
    2. Check current time matches session hours
    3. Refresh the page
    4. Verify session template is saved correctly

---

### Scenario 5: Use Who's In Panel

**When to use this:** Quick view of all staff currently on-site

**Gherkin Scenario:**
```gherkin
Given it's 10:00 AM
When I view the "Who's In" panel on Control Desk
Then I see a list of all employees who have badged IN today
And I see their badge IN time and current room assignment
```

**Steps:**

1. **Find Who's In panel**
   - **Location:** Usually right side or bottom of Control Desk page
   - **Label:** "Who's In" or "On Site" or "Present Staff"
   - **Expected:** Panel visible

2. **View present staff list**
   - **Look for:** List of employees currently badged IN
   - **Columns:**
     - **Employee Name:** Emma Murphy
     - **Badge IN:** 08:58
     - **Room:** Baby Room
     - **Shift End:** 17:00
   - **Expected:** All badged-in staff listed

3. **Check real-time updates**
   - **When staff badges IN:** Name appears in panel
   - **When staff badges OUT:** Name disappears from panel
   - **Update frequency:** Every 60 seconds (or real-time if WebSocket enabled)

4. **Use for attendance**
   - **Total count:** "12 staff on site"
   - **Quick scan:** Who's here, who's missing
   - **Shift coverage:** See which rooms are covered

**Screenshots:** [Screenshot: Who's In panel with staff list]

**Common Issues:**
- ❌ Problem: Who's In panel is empty
  ✅ Solution:
    1. Verify Paxton attendance data is syncing
    2. Check if any staff have badged IN today
    3. Refresh the page
    4. Verify current time is during shift hours

---

### Scenario 6: Dispatch Cover Staff from Control Desk

**When to use this:** Room is RED/AMBER, need to deploy cover staff

**Gherkin Scenario:**
```gherkin
Given Baby Room status is RED (present=2, required=3)
And Lisa O'Brien is available in Cover Pool
When I dispatch Lisa to Baby Room
Then Baby Room present count increases to 3
And status changes to GREEN
And Lisa's status shows "Baby Room - {reason}"
```

**Steps:**

1. **Identify understaffed room**
   - **Check tiles:** Look for RED or AMBER badges
   - **Example:** Baby Room (2 present, 3 required)

2. **View Cover Pool panel**
   - **Look for:** "Cover Staff" or "Cover Pool" panel on Control Desk
   - **Expected:** Panel shows available cover staff

3. **Check available cover staff**
   - **Look for:** Lisa O'Brien with "Available" status
   - **Shift hours:** 09:00 - 17:00
   - **Expected:** Dispatch button enabled

4. **Click Dispatch**
   - **Click:** "Dispatch" button next to Lisa
   - **Expected:** Dispatch modal opens

5. **Fill dispatch details**
   - **Room:** Baby Room (select from dropdown)
   - **Reason:** Break coverage / Sick cover / Ratio gap / Other
   - **Notes:** (optional) "Aoife running late, covering until arrival"
   - **Expected:** All fields filled

6. **Confirm dispatch**
   - **Click:** "Confirm Dispatch" button
   - **Expected:**
     - Modal closes
     - Success toast appears
     - Baby Room present count increases to 3
     - Baby Room status changes to GREEN
     - Lisa's status shows "Baby Room - {reason}"

7. **Verify on room tile**
   - **Check Baby Room tile:**
     - **Present:** Now shows 3
     - **Status:** GREEN badge
   - **Expected:** Room now compliant

**Screenshots:** [Screenshot: Dispatching cover staff from Control Desk]

**Common Issues:**
- ❌ Problem: Cover Pool panel is empty
  ✅ Solution: See [Cover Staff Dispatch Guide](./03-cover-staff-dispatch.md) - Ensure cover staff are scheduled and flagged.

---

### Scenario 7: Monitor Throughout the Day

**When to use this:** Continuous monitoring for compliance

**Gherkin Scenario:**
```gherkin
Given I keep Control Desk open all day
When staff badge IN/OUT throughout the day
Then present counts update automatically
And status badges change based on new counts
And I receive visual alerts for RED rooms
```

**Steps:**

1. **Keep Control Desk open**
   - **Browser tab:** Leave Control Desk page open
   - **Expected:** Page refreshes data every 60 seconds

2. **Watch for real-time updates**
   - **09:00 AM:** Staff start arriving, present counts increase
   - **12:00 PM:** Lunch breaks begin, present counts decrease
   - **12:30 PM:** Staff return from lunch, present counts increase
   - **17:00 PM:** Staff badge OUT, present counts decrease

3. **Respond to status changes**
   - **GREEN → AMBER:** Be aware, monitor breaks
   - **AMBER → RED:** URGENT, dispatch cover or call extra staff
   - **RED → GREEN:** Issue resolved, continue monitoring

4. **Use refresh button** (if needed)
   - **Click:** Refresh button to force immediate data update
   - **When:** After resolving an issue, want instant confirmation

**Screenshots:** [Screenshot: Control Desk timeline throughout day]

**Common Issues:**
- ❌ Problem: Counts don't update in real-time
  ✅ Solution:
    1. Manually click Refresh button
    2. Check browser console for errors
    3. Verify Paxton integration is active
    4. Check network connectivity

---

## Troubleshooting

### Issue: Control Desk shows "No rooms configured"
**Symptoms:** Empty page or error message
**Cause:** RLS policy on `get_room_snapshots()` RPC missing or incorrect
**Solution:**
1. **Wave 31 Fix #1** - This should be fixed
2. Refresh the page
3. Verify rooms exist (Admin > Rooms)
4. Check browser console for RPC errors
5. Verify `get_room_snapshots()` has `SECURITY DEFINER` and grants permissions

---

### Issue: Required count seems wrong
**Symptoms:** Required count doesn't match child count ÷ ratio
**Cause:** Multiple factors affect required count
**Solution:**
1. **Check child_count:** Admin > Rooms > verify child count is set
2. **Check ratio:** Ratio varies by room type (1:3 babies, 1:6 toddlers, 1:8 preschool)
3. **During ECCE session:** Required uses 1:11 ratio
4. **AIMS enabled:** Required + 1 during session hours
5. **Formula:** `CEIL(child_count / ratio)` + AIMS_bonus

---

### Issue: Present count doesn't match reality
**Symptoms:** Staff is here but present count is wrong
**Cause:** Badge data not synced, or staff didn't badge IN
**Solution:**
1. Verify staff badged IN (check Who's In panel)
2. Check Paxton integration status
3. Refresh Control Desk page
4. Verify attendance events in database (`attendance_events` table)
5. If badge malfunction, use Daily Reconciliation to confirm present

---

### Issue: Status badge color wrong
**Symptoms:** Room shows GREEN but is actually understaffed
**Cause:** Calculation error or stale data
**Solution:**
1. Refresh the page
2. Manually calculate: present vs required
3. Check grace period (status may update in 1-2 min)
4. Verify badge events are recent
5. Report as bug if calculation is consistently wrong

---

### Issue: SESSION indicator doesn't appear
**Symptoms:** Room has ECCE session but no indicator shows
**Cause:** Session not configured, or viewing outside session hours
**Solution:**
1. Check current time vs session hours (e.g., 09:30 - 12:30)
2. Verify session is configured (Admin > Rooms > Session Scheduling)
3. Refresh the page
4. Check session template is saved correctly
5. If during session hours and still missing, report as bug

---

### Issue: Who's In panel empty
**Symptoms:** No staff appear in Who's In panel
**Cause:** No badge events today, or Paxton integration offline
**Solution:**
1. Verify Paxton integration is active
2. Check if any staff have badged IN today (check attendance logs)
3. Verify current time is during shift hours
4. Refresh the page
5. Check Paxton server connectivity

---

### Issue: Cover Pool panel missing
**Symptoms:** Can't find Cover Pool panel on Control Desk
**Cause:** No cover staff configured, or feature disabled
**Solution:**
1. Verify at least one employee is flagged as cover staff
2. Verify cover staff have shifts scheduled for today
3. Refresh the page
4. Check feature flag (may be disabled in your org)
5. See [Cover Staff Dispatch Guide](./03-cover-staff-dispatch.md)

---

## Related Guides
- [Demo Mode - Getting Started](./01-demo-mode-onboarding.md)
- [Cover Staff Dispatch](./03-cover-staff-dispatch.md)
- [Session Scheduling (ECCE/AIMS)](./02-session-scheduling-ecce-aims.md)
- [Daily Reconciliation](./04-daily-reconciliation.md)
- [Troubleshooting Guide](./08-troubleshooting.md)

## Need More Help?
- **Timebreez Support:** support@timebreez.com
- **Demo mode:** www.timebreez.com/login (explore Control Desk with 7 demo rooms)
- **Book a call:** Schedule a 15-min walkthrough of Control Desk
- **Paxton Integration:** Help with real-time attendance data
