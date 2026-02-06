# Break Coverage Calculator - Managing Staff Breaks

## Who This Is For
**Childcare Managers** who need to plan and manage staff break coverage so that rooms maintain compliance ratios while staff take lunch and tea breaks.

## What You'll Learn
- What break coverage means and why it matters
- Understanding break windows (30-minute slots)
- Finding available cover staff for each break window
- Reading coverage status indicators (covered/partial/uncovered)
- Assigning cover staff to break windows
- Handling partial coverage scenarios

## Prerequisites
- Manager or Admin role in Timebreez
- Rooms configured with staffing ratios
- Staff schedules and shifts created for today
- At least one cover staff member flagged and scheduled (see [Cover Staff Dispatch](./03-cover-staff-dispatch.md))

---

## Quick Start (TL;DR)

1. Go to **Control Desk > Break Coverage** tab
2. View **break windows** for each room (12:00-12:30, 12:30-13:00, etc.)
3. Check **coverage status**: GREEN = covered, AMBER = partial, RED = uncovered
4. Click a window to see **available cover staff**
5. Click **"Assign"** to allocate cover staff to the break window
6. Monitor throughout the day as breaks occur

---

## Understanding Break Coverage

### What is Break Coverage?

**Break coverage** is the practice of deploying cover staff (floaters) to relieve room-assigned staff during their lunch and tea breaks. Without break coverage, rooms drop below required staffing ratios when staff leave for breaks, which is a **Tusla compliance violation**.

**The problem:**
- Baby Room has 3 staff (required for ratio compliance)
- At 12:00, one staff member takes a 30-minute lunch break
- Baby Room drops to 2 staff (below required = RED status)
- A cover staff member must fill the gap during the break

**The solution:**
- Break Coverage Calculator shows all break windows across all rooms
- Identifies which windows need coverage
- Shows available cover staff for each window
- Allows you to pre-assign or on-demand assign cover

### Break Windows Explained

A **break window** is a 30-minute time slot during which one or more staff members take their break. Standard break windows:

| Window | Time | Typical Use |
|--------|------|-------------|
| **Morning Tea** | 10:30 - 11:00 | Short tea/coffee break |
| **Lunch 1** | 12:00 - 12:30 | First lunch rotation |
| **Lunch 2** | 12:30 - 13:00 | Second lunch rotation |
| **Lunch 3** | 13:00 - 13:30 | Third lunch rotation (if needed) |
| **Afternoon Tea** | 15:00 - 15:30 | Short tea/coffee break |

**Staggering breaks** is critical: If all staff in a room take lunch at 12:00, the room has zero staff. Instead, staff rotate through break windows so only one person is on break at a time per room.

### Coverage Math

**For each break window, the calculator checks:**
```
Staff on break in room = N
Room drops from [planned] to [planned - N] staff
If (planned - N) < required → Coverage needed
Cover staff needed = required - (planned - N)
```

**Example:**
- Baby Room: 3 planned, 3 required (1:3 ratio, 9 children)
- 12:00-12:30: Emma takes lunch → 2 remaining
- 2 < 3 required → 1 cover staff needed
- Lisa (cover) assigned to Baby Room 12:00-12:30

---

## Step-by-Step Guides

### Scenario 1: View Break Windows for Rooms

**When to use this:** Start of day planning, or checking coverage status mid-day

**Gherkin Scenario:**
```gherkin
Given I am logged in as a manager
When I navigate to Control Desk > Break Coverage
Then I see a grid of rooms (rows) x break windows (columns)
And each cell shows coverage status (covered/partial/uncovered)
And I see a summary bar showing "4 of 6 windows fully covered"
```

**Steps:**

1. **Navigate to Break Coverage**
   - **Click:** "Control Desk" in sidebar
   - **Click:** "Break Coverage" tab (next to Room Status, Who's In tabs)
   - **Expected:** Break coverage grid loads

2. **View the grid layout**
   - **Rows:** Each room (Baby Room, Baby Steps, Wobblers, Toddlers, Preschool, ECC, Afterschool)
   - **Columns:** Break windows (10:30, 12:00, 12:30, 13:00, 15:00)
   - **Cells:** Coverage status indicator for each room/window combination
   - **Expected:** Grid visible with all rooms and windows

3. **Read the summary bar**
   - **Look for:** Top summary showing:
     - "14 break slots today"
     - "10 fully covered" (GREEN count)
     - "2 partially covered" (AMBER count)
     - "2 uncovered" (RED count)
   - **Expected:** Summary counts match grid

4. **Understand cell indicators**
   - **GREEN cell "Covered":** Cover staff assigned, room stays at or above required
   - **AMBER cell "Partial":** Cover staff assigned but room still below required by 1
   - **RED cell "Uncovered":** No cover staff assigned, room will drop below required
   - **GRAY cell "N/A":** No break scheduled in this window for this room
   - **Expected:** Colors clearly indicate status

5. **Check today's date**
   - **Look for:** Date selector at top of page
   - **Default:** Today's date
   - **Future planning:** Select a future date to plan coverage in advance
   - **Expected:** Grid updates for selected date

**Screenshots:** [Screenshot: Break coverage grid with rooms x windows]

**Common Issues:**
- ❌ Problem: Grid shows "No breaks scheduled"
  ✅ Solution: Break windows are generated from staff shift schedules. Verify shifts are created for today in the Roster. Break times may need to be configured per employee or per room.

- ❌ Problem: All cells show GRAY "N/A"
  ✅ Solution: Break windows may not be configured. Go to Settings > Break Policy to set up standard break windows for your facility.

---

### Scenario 2: Check Available Cover Staff for a Window

**When to use this:** A break window is RED (uncovered) and you need to find someone to cover

**Gherkin Scenario:**
```gherkin
Given Baby Room 12:00-12:30 window shows RED "Uncovered"
When I click the RED cell
Then a panel opens showing available cover staff for that window
And I see Lisa O'Brien (available, no conflicts)
And I see Sarah Doyle (available, already covering Toddlers 12:30-13:00)
And each staff member shows their current commitments
```

**Steps:**

1. **Click the uncovered cell**
   - **Click:** RED "Uncovered" cell for Baby Room 12:00-12:30
   - **Expected:** Cover staff panel opens (slide-out or modal)

2. **View available cover staff**
   - **Look for:** List of cover staff with availability for this window:
     - **Name:** Lisa O'Brien
     - **Shift:** 09:00 - 17:00
     - **Status:** Available (no conflicts in 12:00-12:30)
     - **Other commitments:** None
   - **Second entry:**
     - **Name:** Sarah Doyle
     - **Shift:** 09:00 - 17:00
     - **Status:** Available (but covering Toddlers 12:30-13:00)
     - **Other commitments:** "Toddlers 12:30-13:00"
   - **Expected:** All eligible cover staff listed

3. **Understand availability indicators**
   - **Green "Available":** No conflicts, can be assigned
   - **Amber "Busy Adjacent":** Available for this window but has adjacent commitments (tight timing)
   - **Red "Unavailable":** Already assigned to another room in this window
   - **Gray "Off Shift":** Not working during this window
   - **Expected:** Indicators help you choose the best person

4. **Review workload balance**
   - **Look for:** "Assignments today" count next to each cover staff
   - **Example:** Lisa O'Brien (1 assignment), Sarah Doyle (2 assignments)
   - **Purpose:** Distribute coverage evenly, avoid overloading one person
   - **Expected:** Counts visible for fair distribution

5. **Close panel** (if not assigning now)
   - **Click:** X button or click outside panel
   - **Expected:** Panel closes, return to grid

**Screenshots:** [Screenshot: Available cover staff panel for a break window]

**Common Issues:**
- ❌ Problem: "No cover staff available" for a window
  ✅ Solution:
    1. Check if cover staff are scheduled for today
    2. They may all be assigned to other windows already
    3. Consider reassigning from less critical windows
    4. As a last resort, use room-to-room coverage (senior room staff covers adjacent room)

---

### Scenario 3: Assign Cover Staff to a Break Window

**When to use this:** You've found an available cover staff member and want to assign them

**Gherkin Scenario:**
```gherkin
Given Baby Room 12:00-12:30 is uncovered
And Lisa O'Brien is available
When I click "Assign" next to Lisa's name
Then Lisa is assigned to cover Baby Room 12:00-12:30
And the grid cell changes from RED "Uncovered" to GREEN "Covered"
And Lisa's availability updates (she's now busy 12:00-12:30)
```

**Steps:**

1. **Open the cover staff panel**
   - **Click:** RED cell for Baby Room 12:00-12:30
   - **Expected:** Available cover staff list appears

2. **Click Assign**
   - **Click:** "Assign" button next to Lisa O'Brien
   - **Expected:** Confirmation prompt may appear

3. **Confirm assignment** (if prompted)
   - **Message:** "Assign Lisa O'Brien to Baby Room 12:00-12:30?"
   - **Click:** "Confirm" or "Yes, Assign"
   - **Expected:** Assignment recorded

4. **Verify grid update**
   - **Check cell:** Baby Room 12:00-12:30 now shows GREEN "Covered"
   - **Cell detail:** "Lisa O'Brien" name shown in cell (or on hover)
   - **Expected:** Status changed from RED to GREEN

5. **Verify Lisa's availability updated**
   - **Click:** Another uncovered window (e.g., Toddlers 12:00-12:30)
   - **Check:** Lisa O'Brien now shows RED "Unavailable" for 12:00-12:30
   - **Expected:** Lisa blocked from double-booking in same window

6. **Check summary bar update**
   - **Before:** "2 uncovered"
   - **After:** "1 uncovered" (decreased by 1)
   - **Expected:** Summary counts updated

**Screenshots:** [Screenshot: Grid showing cell changed from RED to GREEN after assignment]

**Common Issues:**
- ❌ Problem: "Staff already assigned" error
  ✅ Solution: Lisa may already be assigned to another room in this window. Check her commitments in the cover staff panel. A cover staff member can only be in one room per window.

- ❌ Problem: Assignment saved but cell still shows RED
  ✅ Solution: Refresh the page. The grid should update immediately, but if caching occurs, a refresh resolves it.

---

### Scenario 4: Handle Partial Coverage

**When to use this:** A room needs 2 cover staff during a window but you only have 1 available

**Gherkin Scenario:**
```gherkin
Given Preschool has 4 planned staff, 4 required
And during 12:00-12:30, TWO staff take lunch simultaneously
Then Preschool drops to 2 staff (needs 2 cover)
When I assign Lisa O'Brien (1 cover)
Then Preschool has 3 staff (still 1 short)
And the cell shows AMBER "Partial" (not fully covered)
And I see a note "1 more cover staff needed"
```

**Steps:**

1. **Identify partial coverage scenario**
   - **Cell:** Preschool 12:00-12:30 shows RED "Uncovered - 2 needed"
   - **Reason:** Two staff on break simultaneously
   - **Cover available:** Only 1 cover staff free

2. **Assign the available cover staff**
   - **Click:** RED cell for Preschool 12:00-12:30
   - **Assign:** Lisa O'Brien
   - **Expected:** Cell changes from RED to AMBER "Partial"

3. **Understand partial coverage**
   - **AMBER "Partial"** means:
     - Some coverage assigned, but not enough
     - Room will be below required ratio during this window
     - Better than no coverage, but still a compliance risk
   - **Cell note:** "1 more cover staff needed" or "3 of 4 required"

4. **Attempt to resolve**
   - **Option A:** Check if another cover staff can be freed from a less critical window
   - **Option B:** Stagger the breaks (move one break to 12:30-13:00 window instead)
   - **Option C:** Accept partial coverage (document the reason)
   - **Option D:** Call in additional staff (if available)

5. **If staggering breaks:**
   - **Edit:** One staff member's break time to 12:30-13:00
   - **Result:** Only 1 on break at 12:00-12:30 (needs 1 cover) and 1 on break at 12:30-13:00 (needs 1 cover)
   - **Assign:** Lisa covers 12:00-12:30, Sarah covers 12:30-13:00
   - **Expected:** Both windows now GREEN "Covered"

6. **Document partial coverage** (if accepting)
   - **Notes:** Click AMBER cell and add note: "Only 1 cover available. Ratio dips to 3:22 for 30 min. Low risk - no session active."
   - **Purpose:** Audit trail for compliance reporting
   - **Expected:** Note saved with timestamp

**Screenshots:** [Screenshot: AMBER partial coverage cell with "1 more needed" note]

**Common Issues:**
- ❌ Problem: Cannot stagger breaks due to staff preferences
  ✅ Solution: Break times should be set by management, not individual preference, to maintain compliance. Update the break policy if needed. Communicate the staggered schedule to staff.

- ❌ Problem: Partial coverage not visible enough on dashboard
  ✅ Solution: AMBER cells should stand out between GREEN and RED. If color distinction is unclear, check accessibility settings or report a UI improvement request.

---

## Troubleshooting

### Issue: Break windows don't appear for some rooms
**Symptoms:** Grid shows rooms but some have all GRAY cells
**Cause:** No staff scheduled with breaks in those rooms, or break policy not applied
**Solution:**
1. Verify staff in that room have shifts with break entitlements
2. Check Settings > Break Policy applies to all room types
3. Rooms with only 1 staff may not generate break windows (no coverage possible)
4. Afterschool rooms may have different break schedules

---

### Issue: Cover staff shows as available but assignment fails
**Symptoms:** Click "Assign" but get an error
**Cause:** Race condition (someone else assigned them) or data conflict
**Solution:**
1. Refresh the page to get latest availability
2. Another manager may have assigned the same cover staff moments ago
3. Try assigning a different available cover staff member
4. If persistent, check browser console for specific error message

---

### Issue: Break coverage doesn't match actual dispatches
**Symptoms:** Calculator shows "Covered" but cover staff didn't actually go to the room
**Cause:** Break coverage assignments are pre-planned; actual dispatches are separate
**Solution:**
1. Break coverage calculator is a **planning tool** (pre-assignment)
2. Actual cover dispatch happens via Control Desk > Dispatch (see [Cover Staff Dispatch](./03-cover-staff-dispatch.md))
3. The plan informs the dispatch, but dispatch must still be executed
4. Some facilities use the plan as auto-dispatch; check Settings > Break Coverage > Auto-Dispatch toggle

---

### Issue: Too many break windows to manage
**Symptoms:** Grid has dozens of cells, overwhelming to track
**Cause:** Large facility with many rooms and break rotations
**Solution:**
1. Filter by priority: Focus on RED cells first, then AMBER
2. Use "Auto-Assign" feature (if available) to let the system optimally distribute cover staff
3. Group rooms by area (e.g., "Ground Floor" filter, "First Floor" filter)
4. Delegate: Assign a senior staff member as break coordinator for each floor/area

---

## Related Guides
- [Cover Staff Dispatch](./03-cover-staff-dispatch.md)
- [Control Desk Operations](./05-control-desk-operations.md)
- [Attendance & Presence](./09-attendance-presence.md)
- [Compliance Trail & Audit](./11-compliance-trail-audit.md)

## Need More Help?
- **Timebreez Support:** support@timebreez.com
- **Demo mode:** www.timebreez.com/login (explore break coverage in the demo org)
- **Book a call:** Schedule a 15-min walkthrough of break coverage planning
