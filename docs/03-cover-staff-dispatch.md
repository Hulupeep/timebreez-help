# Cover Staff Dispatch - Floater Management

## Who This Is For
**Childcare Managers** who need to deploy cover staff (floaters) to rooms for breaks, sick cover, and ratio gaps.

## What You'll Learn
- What cover staff are and how they differ from room-assigned staff
- Flagging employees as cover staff
- Viewing the cover pool availability
- Dispatching cover staff to rooms
- Cancelling dispatches
- Break coverage planning

## Prerequisites
- Manager or Admin role in Timebreez
- At least one employee to designate as cover staff
- Understanding of your facility's staffing ratios

---

## Quick Start (TL;DR)

1. Go to **Employees** > Select employee > Check **"Cover Staff"**
2. Schedule a shift for them (**no room assignment required**)
3. View **Cover Pool** panel on Control Desk
4. Click **"Dispatch"** next to cover staff name
5. Select **room** + **reason** (Break coverage, Sick cover, Ratio gap, Other)
6. Click **"Confirm Dispatch"**
7. End dispatch when coverage complete

---

## Understanding Cover Staff

### What is Cover Staff?

**Cover staff** (also called floaters or relief staff) are employees who:

- **NOT assigned to a specific room** permanently
- **Deployed on-demand** to cover breaks, absences, or ratio gaps
- **Paid for their full shift** regardless of where/how long they're deployed
- **Flexible** - can move between rooms throughout the day

**Difference from room-assigned staff:**

| Aspect | Room-Assigned Staff | Cover Staff |
|--------|---------------------|-------------|
| **Primary Room** | Yes (e.g., Baby Room) | No |
| **Shift Room Assignment** | Required | Optional (NULL allowed) |
| **Payment** | Hours worked in room | Full shift hours (regardless of deployment) |
| **Deployment** | Fixed to one room | Can dispatch to any room |
| **Usage** | Regular daily staffing | Break coverage, sick cover, ratio gaps |

### When to Use Cover Staff

**Cover staff are ideal for:**
- **Break coverage:** When room staff take lunch/tea breaks
- **Sick cover:** Last-minute callouts, cover needed immediately
- **Ratio gaps:** Room over capacity, need +1 staff temporarily
- **Lunch overlaps:** Multiple staff in same room on lunch at once
- **Compliance:** Tusla inspector visit, need extra staff visible

**NOT ideal for:**
- Permanent room assignments (use regular room staff instead)
- Long-term placements (if >2 weeks, consider reassigning to room)

---

## Step-by-Step Guides

### Scenario 1: Flag an Employee as Cover Staff

**When to use this:** You have a new floater employee or want to change an existing employee to cover role

**Gherkin Scenario:**
```gherkin
Given I have an employee "Lisa O'Brien"
When I edit her profile
And I check the "Cover Staff (Floater)" checkbox
And I save
Then Lisa is marked as cover staff
And I can schedule her without a room assignment
```

**Steps:**

1. **Navigate to Employees**
   - **Click:** "Employees" in the sidebar
   - **Expected:** List of all employees appears

2. **Find the employee to flag**
   - **Look for:** Employee name (e.g., "Lisa O'Brien")
   - **Click:** The employee row to open their profile

3. **Click Edit or Settings**
   - **Look for:** "Edit" button or pencil icon
   - **Click:** Edit button
   - **Expected:** Employee edit form opens

4. **Find the Cover Staff checkbox**
   - **Scroll down:** To employment details or role section
   - **Look for:** Checkbox labeled "Cover Staff (Floater)" with help text:
     - "This employee can be deployed to any room for coverage"
   - **Expected:** Checkbox is visible and unchecked

5. **Check the Cover Staff box**
   - **Click:** The checkbox
   - **Expected:** Checkbox shows blue checkmark

6. **Save the changes**
   - **Click:** "Save" or "Update Employee" button
   - **Expected:** Success toast appears "Employee updated successfully"

7. **Verify cover staff status**
   - **Look for:** Badge or indicator on employee profile showing "Cover Staff"
   - **Expected:** Employee now has cover staff designation

**Screenshots:** [Screenshot: Employee form with Cover Staff checkbox]

**Common Issues:**
- ❌ Problem: Cover Staff checkbox is grayed out or disabled
  ✅ Solution: You may not have admin permissions. Contact your organization admin.

- ❌ Problem: I checked the box but it unchecks after save
  ✅ Solution: Ensure you clicked Save AFTER checking the box. If issue persists, check browser console for errors.

---

### Scenario 2: Schedule a Cover Shift (No Room Assignment)

**When to use this:** You want to put a cover staff member on the roster

**Gherkin Scenario:**
```gherkin
Given Lisa O'Brien is flagged as cover staff
When I create a shift for her
And I leave "Room" field empty (NULL)
Then the shift is saved successfully
And Lisa appears in the Cover Pool
```

**Steps:**

1. **Navigate to Roster/Schedule page**
   - **Click:** "Roster" or "Schedule" in sidebar
   - **Expected:** Weekly schedule grid appears

2. **Find the day and employee**
   - **Look for:** Lisa O'Brien's row in the schedule
   - **Select:** The day you want to schedule (e.g., Monday)

3. **Click to add a shift**
   - **Click:** Empty cell for Lisa on Monday
   - **Expected:** Shift creation modal opens

4. **Fill shift details**
   - **Start Time:** 09:00
   - **End Time:** 17:00
   - **Room:** Leave empty (or select "Cover Pool")
   - **Is Cover Shift:** Check this box (if present)
   - **Expected:** Form accepts NULL room for cover staff

5. **Save the shift**
   - **Click:** "Save" or "Create Shift" button
   - **Expected:** Success toast, modal closes

6. **Verify shift appears**
   - **Look for:** Shift cell shows "09:00 - 17:00" in Lisa's row
   - **Badge:** May show "Cover Pool" or "Floater" badge
   - **Expected:** Shift is visible on roster

**Screenshots:** [Screenshot: Cover shift in roster with no room assignment]

**Common Issues:**
- ❌ Problem: "Room is required" validation error
  ✅ Solution:
    1. Verify employee is flagged as Cover Staff first (Scenario 1)
    2. Check the "Is Cover Shift" checkbox if available
    3. If error persists, the database constraint may need fixing (contact support)

---

### Scenario 3: View Cover Pool on Control Desk

**When to use this:** You want to see which cover staff are available right now

**Gherkin Scenario:**
```gherkin
Given Lisa O'Brien has a cover shift today (09:00 - 17:00)
When I view Control Desk at 10:00 AM
Then I see a "Cover Pool" panel
And Lisa appears in the panel
And her status shows "Available" or "{Room Name} - {reason}"
```

**Steps:**

1. **Navigate to Control Desk**
   - **Click:** "Control Desk" in sidebar
   - **Expected:** Room tiles appear

2. **Find the Cover Pool panel**
   - **Look for:** Section labeled "Cover Staff" or "Cover Pool"
   - **Location:** Usually on the right side or bottom of the page
   - **Expected:** Panel is visible

3. **View available cover staff**
   - **Look for:** Cards/rows for each cover staff member with shift today
   - **Expected:** You see:
     - **Employee Name:** Lisa O'Brien
     - **Shift Hours:** 09:00 - 17:00
     - **Current Status:** "Available" (not dispatched)
     - **Hours Remaining:** e.g., "7h remaining"

4. **Understand status indicators**
   - **Green badge "Available":** Not currently dispatched, ready to assign
   - **Blue badge "{Room Name} - Break coverage":** Currently dispatched to a room
   - **Gray badge "Off shift":** Shift hasn't started yet or already ended

5. **Check dispatch action button**
   - **Look for:** "Dispatch" button next to each available cover staff
   - **Expected:** Button is enabled for available staff, disabled for already-dispatched

**Screenshots:** [Screenshot: Cover Pool panel on Control Desk]

**Common Issues:**
- ❌ Problem: Cover Pool panel is empty
  ✅ Solution:
    1. Verify cover staff have shifts scheduled for today
    2. Check current time - are you viewing during their shift hours?
    3. Refresh the page

- ❌ Problem: Cover Pool panel doesn't appear at all
  ✅ Solution:
    1. Ensure at least one employee is flagged as cover staff
    2. Ensure at least one cover shift exists for today
    3. If both true and panel still missing, report as a bug

---

### Scenario 4: Dispatch Cover Staff to a Room

**When to use this:** Room staff is on break and you need coverage

**Gherkin Scenario:**
```gherkin
Given Lisa O'Brien is available in Cover Pool
And Baby Room needs break coverage
When I click "Dispatch" next to Lisa
And I select Baby Room and reason "Break coverage"
And I click "Confirm Dispatch"
Then Lisa is dispatched to Baby Room
And Baby Room's present count increases by 1
And Lisa's status shows "Baby Room - Break coverage"
```

**Steps:**

1. **View Cover Pool panel**
   - **Ensure:** Lisa O'Brien shows "Available" status

2. **Click Dispatch button**
   - **Click:** "Dispatch" button next to Lisa's name
   - **Expected:** Dispatch modal opens

3. **Select the destination room**
   - **Look for:** "Room" dropdown in modal
   - **Click:** Dropdown and select "Baby Room"
   - **Expected:** Room selected, dropdown closes

4. **Select dispatch reason**
   - **Look for:** "Reason" dropdown with options:
     - **Break coverage** ← Most common
     - **Sick cover**
     - **Ratio gap**
     - **Other**
   - **Click:** "Break coverage"
   - **Expected:** Reason selected

5. **Add optional notes** (optional)
   - **Look for:** "Notes" text field
   - **Enter:** "Covering Emma's lunch break 12:00 - 12:30"
   - **Expected:** Notes saved (optional, can leave blank)

6. **Confirm the dispatch**
   - **Click:** "Confirm Dispatch" button in modal
   - **Expected:**
     - Modal closes
     - Success toast appears "Lisa O'Brien dispatched to Baby Room"

7. **Verify dispatch on Control Desk**
   - **Check Cover Pool:** Lisa's status now shows "Baby Room - Break coverage"
   - **Check Baby Room tile:** Present count increased by 1
   - **Expected:** Both updated in real-time

8. **Verify dispatch log recorded**
   - **Database:** `room_dispatch_log` table has new entry with:
     - `shift_instance_id` (Lisa's shift)
     - `room_id` (Baby Room)
     - `dispatch_reason` ('break_coverage')
     - `dispatched_at` (current timestamp)
     - `dispatched_until` (NULL - ongoing)

**Screenshots:** [Screenshot: Dispatch modal with room and reason selected]

**Common Issues:**
- ❌ Problem: "Dispatch" button is disabled
  ✅ Solution:
    1. Cover staff may already be dispatched (check status)
    2. Cover staff may not be on shift yet (check shift hours)
    3. Refresh the page and try again

- ❌ Problem: "Staff already dispatched" error
  ✅ Solution: Only one active dispatch allowed at a time. End the current dispatch first (Scenario 5), then dispatch to new room.

- ❌ Problem: Room dropdown is empty
  ✅ Solution: Ensure you have rooms configured (Admin > Rooms). At least one active room must exist.

---

### Scenario 5: End a Cover Dispatch

**When to use this:** Break is over, staff member returned, coverage no longer needed

**Gherkin Scenario:**
```gherkin
Given Lisa is currently dispatched to Baby Room
When I click "End Dispatch" next to her status
Then Lisa's status returns to "Available"
And Baby Room's present count decreases by 1
And dispatch_log.dispatched_until is set to current timestamp
```

**Steps:**

1. **View Cover Pool panel**
   - **Look for:** Lisa O'Brien with status "Baby Room - Break coverage"

2. **Click End Dispatch button**
   - **Look for:** "End Dispatch" button next to Lisa's current status
   - **Click:** End Dispatch button
   - **Expected:** Confirmation modal may appear

3. **Confirm ending the dispatch** (if modal appears)
   - **Question:** "End dispatch for Lisa O'Brien?"
   - **Click:** "Yes, End Dispatch" or "Confirm"
   - **Expected:** Modal closes

4. **Verify dispatch ended**
   - **Check Cover Pool:** Lisa's status returns to "Available"
   - **Check Baby Room tile:** Present count decreased by 1
   - **Expected:** Both updated

5. **Verify dispatch log updated**
   - **Database:** `room_dispatch_log` entry updated:
     - `dispatched_until` now has timestamp (no longer NULL)
     - **Duration:** `dispatched_until - dispatched_at` = total dispatch time

**Screenshots:** [Screenshot: End Dispatch button, status returns to Available]

**Common Issues:**
- ❌ Problem: "End Dispatch" button doesn't appear
  ✅ Solution: Button only shows when staff is actively dispatched. If status shows "Available", dispatch is already ended.

- ❌ Problem: Ending dispatch doesn't update room present count
  ✅ Solution: Refresh the Control Desk page. Real-time updates may take a few seconds.

---

### Scenario 6: Dispatch for Sick Cover

**When to use this:** Regular room staff called in sick, need emergency coverage

**Gherkin Scenario:**
```gherkin
Given Emma Murphy called in sick for Baby Room
And Lisa O'Brien is available
When I dispatch Lisa to Baby Room with reason "Sick cover"
And I add note "Covering Emma Murphy (sick call at 8:45 AM)"
Then Lisa covers Emma's shift for the day
And dispatch log records the sick cover reason
```

**Steps:**

1. **Identify the coverage need**
   - **Scenario:** Emma Murphy (Baby Room staff) called in sick
   - **Result:** Baby Room shows RED status (understaffed)

2. **Open dispatch modal**
   - **Click:** "Dispatch" next to Lisa O'Brien in Cover Pool

3. **Select room and reason**
   - **Room:** Baby Room
   - **Reason:** Sick cover ← Select this option
   - **Expected:** Sick cover selected

4. **Add detailed notes**
   - **Notes field:** "Covering Emma Murphy (sick call at 8:45 AM, expected full day absence)"
   - **Why:** Notes help with payroll reconciliation and compliance audits

5. **Confirm dispatch**
   - **Click:** Confirm Dispatch
   - **Expected:** Lisa dispatched to Baby Room

6. **Understand the difference**
   - **Break coverage:** Short duration (30 min - 1 hour)
   - **Sick cover:** Usually full day, end dispatch when Lisa's shift ends
   - **Payroll:** Lisa is paid for her full shift (not per dispatch hour)

**Screenshots:** [Screenshot: Dispatch modal with "Sick cover" reason]

**Common Issues:**
- ❌ Problem: Should I end dispatch at end of day?
  ✅ Solution: Yes, when Lisa's shift ends (e.g., 17:00), end the dispatch. This closes the dispatch log entry.

---

### Scenario 7: Dispatch for Ratio Gap

**When to use this:** Room capacity increased temporarily, need +1 staff to maintain ratio

**Gherkin Scenario:**
```gherkin
Given Toddlers room has 12 children (ratio 1:6, requires 2 staff)
When 2 extra children arrive (emergency drop-offs)
Then room now has 14 children, requires 3 staff (ratio gap)
When I dispatch Lisa to Toddlers with reason "Ratio gap"
Then room ratio is compliant again
```

**Steps:**

1. **Identify the ratio gap**
   - **Check Control Desk:** Toddlers room shows AMBER or RED (understaffed)
   - **Reason:** Child count temporarily increased beyond planned capacity

2. **Dispatch cover staff**
   - **Click:** Dispatch next to available cover staff
   - **Room:** Toddlers
   - **Reason:** Ratio gap ← Select this option
   - **Notes:** "2 emergency drop-offs, 14 children total (requires 3 staff for 1:6 ratio)"

3. **Confirm dispatch**
   - **Click:** Confirm Dispatch
   - **Expected:** Toddlers room status changes to GREEN (compliant)

4. **End dispatch when children leave**
   - **When:** Emergency drop-offs depart (child count back to 12)
   - **Action:** End dispatch (room back to 2 staff requirement)

**Screenshots:** [Screenshot: Ratio gap dispatch, room status GREEN after]

---

### Scenario 8: Break Coverage Planning

**When to use this:** You want to plan break coverage for the whole day

**Gherkin Scenario:**
```gherkin
Given I have 2 cover staff and 20 room staff
When I calculate total break hours (20 staff × 30 min = 10 hours)
And I check available cover hours (2 cover staff × 8 hours = 16 hours)
Then I have sufficient coverage capacity
And I can dispatch cover staff to handle all breaks
```

**Steps:**

1. **Calculate break coverage demand**
   - **Formula:** Total staff × break duration = total break hours
   - **Example:** 20 staff × 30 min = 10 hours of break coverage needed

2. **Calculate cover capacity**
   - **Formula:** Cover staff count × shift hours = available cover hours
   - **Example:** 2 cover staff × 8 hours = 16 hours capacity

3. **Check capacity status**
   - **Look for:** "Break Coverage Estimate" panel (if available)
   - **Status:**
     - **GREEN "OK":** Capacity > demand (e.g., 16 hours > 10 hours)
     - **AMBER "Constrained":** Capacity ≈ demand (tight but doable)
     - **RED "Critical":** Capacity < demand (not enough cover staff)

4. **Plan dispatch schedule** (manual or tool-assisted)
   - **Morning breaks:** 10:00 - 11:00 (dispatch cover to rooms as staff take breaks)
   - **Lunch breaks:** 12:00 - 14:00 (peak dispatch period)
   - **Afternoon breaks:** 15:00 - 16:00 (dispatch again)

5. **Execute dispatches throughout the day**
   - **As staff take breaks:** Dispatch cover to fill gap
   - **When break ends:** End dispatch, cover returns to pool

**Screenshots:** [Screenshot: Break coverage estimate panel]

**Common Issues:**
- ❌ Problem: Not enough cover staff for all breaks
  ✅ Solution:
    1. Stagger break times (don't let everyone break at once)
    2. Schedule additional cover staff shifts
    3. Use room staff to cover each other (cross-room coverage)

---

## Troubleshooting

### Issue: Cover Staff checkbox missing
**Symptoms:** Can't find "Cover Staff (Floater)" checkbox on employee form
**Cause:** Checkbox may be hidden or permissions issue
**Solution:**
1. Ensure you have Admin role
2. Check employee form settings section
3. If still missing, contact support (may be a feature flag)

---

### Issue: Can't save shift without room
**Symptoms:** "Room is required" error when saving cover shift
**Cause:** Employee not flagged as cover staff, or database constraint issue
**Solution:**
1. **First:** Flag employee as cover staff (Scenario 1)
2. **Then:** Try creating shift again
3. **If still fails:** Check database constraint `chk_cover_shift_room` exists and is correct

---

### Issue: Cover Pool panel empty
**Symptoms:** No cover staff appear in Cover Pool
**Cause:** No cover shifts scheduled for today, or no employees flagged as cover
**Solution:**
1. Verify at least one employee has `is_cover_staff = true`
2. Verify that employee has a shift scheduled for today
3. Check shift start/end times - are you viewing during shift hours?
4. Refresh the page

---

### Issue: "Staff already dispatched" error
**Symptoms:** Can't dispatch cover staff, error message appears
**Cause:** Staff is already actively dispatched to another room
**Solution:**
1. Check Cover Pool - does status show a room name?
2. End the current dispatch first (Scenario 5)
3. Then dispatch to new room
4. **Note:** Only ONE active dispatch per cover staff at a time

---

### Issue: Dispatch doesn't update room present count
**Symptoms:** Dispatched cover staff but room tile doesn't show +1 present
**Cause:** UI not refreshed, or dispatch log not created
**Solution:**
1. Refresh Control Desk page
2. Check `room_dispatch_log` table - verify entry exists with `dispatched_until = NULL`
3. If no entry, dispatch failed silently - check browser console for errors
4. Re-dispatch if needed

---

### Issue: Can't end dispatch
**Symptoms:** "End Dispatch" button missing or disabled
**Cause:** Dispatch already ended, or UI issue
**Solution:**
1. Check `room_dispatch_log` - does entry have `dispatched_until` timestamp?
2. If timestamp exists, dispatch is already ended (success)
3. If NULL, refresh page and try again
4. If button still missing, report as bug

---

### Issue: Cover staff payroll calculation wrong
**Symptoms:** Payroll shows dispatch hours instead of shift hours
**Cause:** Payroll RPC using wrong table (`room_dispatch_log` instead of `shift_instances`)
**Solution:**
1. **CRITICAL:** Cover staff are paid for FULL SHIFT HOURS, not dispatch hours
2. Payroll query must use `shift_instances.start_time` and `end_time`
3. **Do NOT use:** `room_dispatch_log` for payroll (that's for compliance audits only)
4. If payroll is wrong, check the payroll export RPC and fix query

---

## Related Guides
- [Demo Mode - Getting Started](./01-demo-mode-onboarding.md)
- [Control Desk Operations](./05-control-desk-operations.md)
- [Daily Reconciliation](./04-daily-reconciliation.md)
- [Troubleshooting Guide](./08-troubleshooting.md)

## Need More Help?
- **Timebreez Support:** support@timebreez.com
- **Demo mode:** www.timebreez.com/login (try cover staff dispatch with Lisa O'Brien)
- **Book a call:** Schedule a 15-min walkthrough of cover staff management
