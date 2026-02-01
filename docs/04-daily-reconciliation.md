# Daily Reconciliation - Plan vs Reality

## Who This Is For
**Childcare Managers** who need to reconcile attendance (badge data) with scheduled shifts and resolve discrepancies.

## What You'll Learn
- Understanding Plan vs Reality
- Viewing attendance logs
- Identifying discrepancies (early departure, late arrival, no badge)
- Resolving discrepancies with operational decisions
- Self-service reconciliation for staff
- Unlocking payroll approval after reconciliation

## Prerequisites
- Manager or Admin role in Timebreez
- Paxton Net2 integration active (for badge data)
- Understanding of your facility's attendance policies

---

## Quick Start (TL;DR)

1. Go to **Reconciliation > Daily**
2. Select date to reconcile
3. View **3 sections:** Confirmed, Partial, Needs Attention
4. Click **"Resolve"** on any discrepancy
5. Choose resolution: **Confirm present** / **Apply leave** / **Log absence**
6. Enter **reason** (required)
7. Click **"Confirm"**
8. When all resolved → **"Proceed to Payroll"** button enabled

---

## Understanding Reconciliation

### What is Daily Reconciliation?

**Daily Reconciliation** compares:
- **PLAN:** Who was scheduled to work (from your roster)
- **REALITY:** Who actually showed up (from badge/attendance data)

**Why it matters:**
- **Payroll accuracy:** Pay staff for actual hours worked, not just scheduled
- **Compliance:** Tusla audits require proof of who was present
- **Leave tracking:** Late arrivals/early departures may need leave applied
- **No-show detection:** Identify staff who didn't badge in

### The 3 Reconciliation States

| State | Meaning | Action Required |
|-------|---------|-----------------|
| **CONFIRMED** | Badge matches schedule exactly | None - all good |
| **PARTIAL** | Badge + leave covers gap (e.g., left early but has leave request) | None - resolved automatically |
| **NEEDS ATTENTION** | Discrepancy with no coverage (early departure, no badge, etc.) | Resolve manually |

### Invariants (Rules Always True)

- **I-RECON-001:** Badge matches schedule = CONFIRMED (green)
- **I-RECON-002:** Early departure without leave = NEEDS ATTENTION (red)
- **I-RECON-003:** Badge + approved leave = PARTIAL (yellow, auto-resolved)
- **I-RECON-004:** No badge data = NEEDS ATTENTION (red)
- **I-RECON-005:** Unresolved items block payroll approval
- **I-RECON-006:** Every resolution creates an `operational_decision` audit record
- **I-RECON-007:** 15-minute grace period (badge at 09:05 for 09:00 shift = OK)

---

## Step-by-Step Guides

### Scenario 1: View Daily Reconciliation Page

**When to use this:** Start of your daily workflow

**Gherkin Scenario:**
```gherkin
Given I am logged in as a manager
When I navigate to Reconciliation > Daily
Then I see the daily reconciliation page
And I see date selector, navigation buttons, and summary counts
```

**Steps:**

1. **Navigate to Reconciliation**
   - **Click:** "Reconciliation" in the sidebar
   - **Sub-menu:** Click "Daily"
   - **Expected:** Daily reconciliation page loads

2. **Verify page components**
   - **Look for:**
     - **Date Selector:** Shows today's date by default
     - **Previous/Next Day buttons:** Arrow buttons to navigate dates
     - **Summary counts:** 3 boxes showing Confirmed, Partial, Attention
   - **Expected:** All components visible

3. **Check summary counts**
   - **Confirmed (green):** Number of staff with badge matching schedule
   - **Partial (yellow):** Staff with badge + leave covering gap
   - **Needs Attention (red):** Discrepancies requiring resolution
   - **Expected:** Counts reflect current reconciliation status

4. **Understand the sections below**
   - **Confirmed Section:** List of employees with perfect attendance
   - **Partial Section:** Employees with leave-covered gaps
   - **Needs Attention Section:** Employees with unresolved discrepancies
   - **Expected:** 3 collapsible sections visible

**Screenshots:** [Screenshot: Daily Reconciliation page layout]

**Common Issues:**
- ❌ Problem: Page shows "No data for this date"
  ✅ Solution:
    1. Check if any shifts are scheduled for the selected date
    2. Check if attendance data has been synced from Paxton
    3. Click "Refresh" or "Generate" to re-run reconciliation

---

### Scenario 2: Generate Reconciliation Data

**When to use this:** First time viewing a date, or data needs refreshing

**Gherkin Scenario:**
```gherkin
Given I am on the Daily Reconciliation page
When I click the "Refresh" or "Generate" button
Then the system fetches latest attendance data
And re-calculates reconciliation for all employees
And summary counts update
```

**Steps:**

1. **Find the Refresh button**
   - **Look for:** Button labeled "Refresh", "Generate", or circular refresh icon
   - **Location:** Usually top right of page near date selector
   - **Expected:** Button is visible and enabled

2. **Click Refresh**
   - **Click:** Refresh button
   - **Expected:** Button shows loading spinner

3. **Wait for data generation**
   - **Duration:** 2-5 seconds typically
   - **Expected:** Loading indicator appears

4. **Verify data loaded**
   - **Check:**
     - Summary counts populated (not 0-0-0)
     - Employee rows appear in sections
     - No error alerts
   - **Expected:** Reconciliation data visible

5. **Understand what happens**
   - **System queries:**
     1. All shifts scheduled for the date
     2. All attendance events (badge IN/OUT) for those employees
     3. All approved leave requests for the date
   - **System calculates:** Confirmed, Partial, Attention categorization
   - **System displays:** Results in 3 sections

**Screenshots:** [Screenshot: Refresh button, loading state]

**Common Issues:**
- ❌ Problem: Refresh button missing
  ✅ Solution: Data may auto-generate on page load. If sections are empty, check that shifts and attendance data exist for the date.

- ❌ Problem: "Error loading data" after refresh
  ✅ Solution:
    1. Check network connection
    2. Verify RPC `generate_reconciliation` exists and has permissions
    3. Check browser console for detailed error
    4. Contact support if issue persists

---

### Scenario 3: View Confirmed Employees (Perfect Attendance)

**When to use this:** Verify which employees need no action

**Gherkin Scenario:**
```gherkin
Given Emma Murphy was scheduled 09:00 - 17:00
And she badged IN at 08:58 and OUT at 17:02
When I view the Confirmed section
Then Emma appears in this section
And her row shows scheduled 09:00-17:00, badged 08:58-17:02
And her status is GREEN "Confirmed"
```

**Steps:**

1. **Scroll to Confirmed section**
   - **Look for:** Section header "Confirmed" with green background
   - **Expected:** Section visible (may be collapsed)

2. **Expand if collapsed**
   - **Click:** Section header to expand
   - **Expected:** Employee rows appear

3. **Review a confirmed employee**
   - **Look for:** Employee row (e.g., Emma Murphy)
   - **Columns:**
     - **Employee Name:** Emma Murphy
     - **Scheduled:** 09:00 - 17:00
     - **Badge IN:** 08:58 (within 15-min grace)
     - **Badge OUT:** 17:02 (within 15-min grace)
     - **Status:** Green checkmark or "Confirmed"
   - **Expected:** All confirmed employees listed here

4. **Understand the rule (I-RECON-001)**
   - **Confirmed if:**
     - Badge IN within 15 min of scheduled start
     - Badge OUT within 15 min of scheduled end
     - No gaps in coverage
   - **Example:**
     - Scheduled 09:00, badge IN 09:05 = Confirmed (5 min late, within grace)
     - Scheduled 17:00, badge OUT 17:12 = Confirmed (12 min over, within grace)

5. **No action required**
   - **Confirmed employees:** Need no resolution
   - **Payroll:** Will be paid for scheduled hours (or badge hours if longer)

**Screenshots:** [Screenshot: Confirmed section with employee rows]

**Common Issues:**
- ❌ Problem: Confirmed section is empty but staff did show up
  ✅ Solution:
    1. Verify attendance data synced from Paxton
    2. Check grace period (15 min) - if late > 15 min, goes to Attention
    3. Refresh the page

---

### Scenario 4: View Partial Section (Leave-Covered Gaps)

**When to use this:** Verify employees with approved leave covering discrepancies

**Gherkin Scenario:**
```gherkin
Given Lisa O'Brien was scheduled 09:00 - 17:00
And she badged IN at 09:00 and OUT at 14:30 (left early)
And she has approved leave request for 14:30 - 17:00
When I view the Partial section
Then Lisa appears with status "Partial (Leave)"
And her row shows badge 09:00-14:30, leave 14:30-17:00
And no action required (automatically resolved)
```

**Steps:**

1. **Scroll to Partial section**
   - **Look for:** Section header "Partial" with yellow/amber background
   - **Expected:** Section visible

2. **Expand and review**
   - **Click:** Section header to expand
   - **Look for:** Employees with partial attendance

3. **Examine a partial entry**
   - **Example:** Lisa O'Brien
   - **Scheduled:** 09:00 - 17:00
   - **Badge IN:** 09:00
   - **Badge OUT:** 14:30 (2.5 hours early)
   - **Leave Coverage:** 14:30 - 17:00 (Annual Leave)
   - **Status:** Yellow badge "Leave covers gap"

4. **Understand the rule (I-RECON-003)**
   - **Partial if:**
     - Badge OUT early OR Badge IN late
     - Approved leave request covers the gap
   - **No action needed:** Leave automatically resolves the discrepancy

5. **Why this matters**
   - **Payroll:** Staff paid for badge hours + leave hours
   - **Compliance:** Leave request provides audit trail
   - **Example:** Lisa gets 5.5h worked (09:00-14:30) + 2.5h leave (14:30-17:00) = 8h total

**Screenshots:** [Screenshot: Partial section with leave coverage]

**Common Issues:**
- ❌ Problem: Employee in Partial but leave is NOT approved
  ✅ Solution: Employee should be in "Needs Attention" instead. Check leave request status - may be pending. Approve the leave request first.

- ❌ Problem: Employee left early with leave, but appears in Needs Attention
  ✅ Solution:
    1. Verify leave request dates/times exactly match the gap
    2. Verify leave request is APPROVED (not pending/denied)
    3. Refresh reconciliation data

---

### Scenario 5: Identify Discrepancies in Needs Attention

**When to use this:** Find employees with unresolved issues

**Gherkin Scenario:**
```gherkin
Given Aoife O'Brien was scheduled 09:00 - 17:00
And she badged IN at 09:00 and OUT at 14:00 (3 hours early)
And she has NO leave request for 14:00 - 17:00
When I view the Needs Attention section
Then Aoife appears with RED status "Early departure"
And her row shows variance: -3 hours
And a "Resolve" button is visible
```

**Steps:**

1. **Scroll to Needs Attention section**
   - **Look for:** Section header "Needs Attention" with red background
   - **Expected:** Section visible

2. **Expand and review**
   - **Click:** Section header to expand
   - **Look for:** Employees needing resolution

3. **Examine discrepancy types**
   - **Early Departure:**
     - Badge OUT before scheduled end, no leave coverage
     - Example: Scheduled until 17:00, badged OUT 14:00
   - **Late Arrival:**
     - Badge IN more than 15 min after scheduled start, no leave
     - Example: Scheduled 09:00, badged IN 10:00
   - **No Badge Data:**
     - Scheduled shift but no badge IN/OUT events
     - Example: Scheduled all day, no attendance records
   - **Missing Badge IN:**
     - Badge OUT exists but no badge IN
     - Example: OUT at 17:00, but no IN event
   - **Missing Badge OUT:**
     - Badge IN exists but no badge OUT
     - Example: IN at 09:00, but no OUT event

4. **Check variance column**
   - **Variance:** Difference between scheduled and badge hours
   - **Negative variance:** Left early or arrived late (e.g., "-3h")
   - **Zero variance:** Time matches but other issue (e.g., no badge data)

5. **Identify action needed**
   - **Look for:** "Resolve" button on each row
   - **Expected:** Button enabled, ready to click

**Screenshots:** [Screenshot: Needs Attention section with discrepancies]

**Common Issues:**
- ❌ Problem: Needs Attention section empty but I know someone left early
  ✅ Solution:
    1. Check if they have approved leave covering the gap (would be in Partial)
    2. Verify attendance data synced
    3. Check grace period (15 min) - small gaps auto-resolved

---

### Scenario 6: Resolve Discrepancy by Confirming Present

**When to use this:** Badge data is wrong but employee was actually present (e.g., badge reader malfunction)

**Gherkin Scenario:**
```gherkin
Given Aoife shows "No badge data" (scheduled but no attendance)
And I verified in person that Aoife worked the full shift
When I click "Resolve" on Aoife's row
And I select "Confirm was present"
And I enter reason "Badge reader malfunction, confirmed with supervisor"
And I click "Confirm"
Then the discrepancy is resolved
And Aoife moves to Confirmed section
And operational_decision record is created for audit
```

**Steps:**

1. **Click Resolve button**
   - **Find:** Aoife O'Brien in Needs Attention section
   - **Click:** "Resolve" button on her row
   - **Expected:** Resolution modal opens

2. **Review modal contents**
   - **Look for:**
     - Employee name: Aoife O'Brien
     - Discrepancy details: "No badge data" or variance shown
     - Resolution options (radio buttons or dropdown)
     - Reason text field
   - **Expected:** All elements visible

3. **Select resolution option**
   - **Click:** "Confirm was present" radio button/option
   - **Use case:** Badge data is incorrect, but employee was actually present
   - **Expected:** Option selected

4. **Enter reason (REQUIRED)**
   - **Click:** "Reason" text field
   - **Enter:** "Badge reader malfunction. Confirmed with Emma (supervisor) that Aoife worked 09:00 - 17:00. Saw her in Baby Room all day."
   - **Why detailed:** Audit trail for compliance and payroll disputes
   - **Expected:** Reason text entered

5. **Confirm the resolution**
   - **Click:** "Confirm" or "Submit" button in modal
   - **Expected:**
     - Modal closes
     - Success toast appears "Discrepancy resolved"

6. **Verify resolution**
   - **Check Needs Attention:** Aoife's row removed
   - **Check Confirmed:** Aoife now appears here
   - **Check Attention Count:** Decreased by 1
   - **Expected:** Employee moved to Confirmed section

7. **Understand what happened**
   - **Database:** `operational_decision` table entry created:
     - `decision_type`: 'confirm_present'
     - `reason`: Your entered text
     - `decided_by`: Your employee ID
     - `decided_at`: Current timestamp
   - **Payroll:** Aoife paid for scheduled hours
   - **Compliance:** Decision documented for Tusla audit

**Screenshots:** [Screenshot: Resolution modal with "Confirm was present" selected]

**Common Issues:**
- ❌ Problem: "Confirm" button is disabled
  ✅ Solution: Reason field is required. Enter a detailed reason explaining why you're confirming presence despite missing badge data.

- ❌ Problem: Resolution doesn't save, error appears
  ✅ Solution:
    1. Check error message for details
    2. Verify you have manager permissions
    3. Ensure reason is filled (minimum 10 characters)
    4. Try again or contact support

---

### Scenario 7: Resolve Discrepancy by Applying Leave

**When to use this:** Employee left early or arrived late, and it should be recorded as leave

**Gherkin Scenario:**
```gherkin
Given Emma Murphy left at 14:00 (3 hours early)
And she has no leave request for 14:00 - 17:00
When I click "Resolve" on Emma's row
And I select "Apply leave"
And I select leave type "Sick Leave"
And I enter reason "Emma called in sick at 2pm and went home"
And I click "Confirm"
Then a leave request is created for 14:00 - 17:00
And Emma's leave balance is debited by 3 hours
And Emma moves to Partial section
```

**Steps:**

1. **Click Resolve on Emma's row**
   - **Find:** Emma Murphy in Needs Attention
   - **Discrepancy:** Early departure at 14:00 (scheduled until 17:00)
   - **Click:** Resolve button
   - **Expected:** Resolution modal opens

2. **Select "Apply leave" option**
   - **Click:** "Apply leave" radio button
   - **Expected:** Leave type dropdown appears

3. **Select leave type**
   - **Look for:** "Leave Type" dropdown (appears after selecting "Apply leave")
   - **Options:**
     - Sick Leave
     - Annual Leave
     - Emergency Leave
     - Unpaid Leave
     - (Other leave types configured in your org)
   - **Click:** "Sick Leave" (for this example)
   - **Expected:** Sick Leave selected

4. **Enter reason**
   - **Reason field:** "Emma called at 14:05 to say she felt unwell. Manager approved early departure. Left at 14:00."
   - **Why:** Explains the leave application for payroll and HR records

5. **Confirm the resolution**
   - **Click:** "Confirm" button
   - **Expected:**
     - Modal closes
     - Success toast "Leave applied and discrepancy resolved"

6. **Verify resolution**
   - **Check Needs Attention:** Emma's row removed
   - **Check Partial:** Emma now appears here with "Sick Leave 14:00-17:00"
   - **Check Emma's leave balance:**
     - Navigate to Employees > Emma Murphy
     - Sick Leave balance decreased by 3 hours (or 0.375 days)
   - **Expected:** All updated correctly

7. **Understand what happened**
   - **Database actions:**
     1. `leave_requests` entry created (status: approved, type: sick)
     2. `leave_entitlements` debited (balance -= 3 hours)
     3. `operational_decision` created (decision_type: 'apply_leave')
   - **Payroll:** Emma paid for 5h worked (09:00-14:00) + 3h sick leave = 8h total
   - **Compliance:** Leave request provides audit trail

**Screenshots:** [Screenshot: Resolution modal with "Apply leave" and leave type dropdown]

**Common Issues:**
- ❌ Problem: Leave type dropdown doesn't appear
  ✅ Solution: Ensure you selected "Apply leave" option first. Dropdown only appears after this selection.

- ❌ Problem: "Insufficient leave balance" error
  ✅ Solution:
    1. Check employee's leave balance (may be 0 hours remaining)
    2. Options:
       - Select different leave type (e.g., Unpaid Leave)
       - Request leave balance adjustment (if policy allows)
       - Apply partial leave + partial unpaid

- ❌ Problem: Leave is applied but employee still in Needs Attention
  ✅ Solution:
    1. Refresh the page
    2. Verify leave request was created (check Leave Requests page)
    3. Verify leave request is APPROVED
    4. Re-run reconciliation

---

### Scenario 8: Resolve No Badge Data Issue

**When to use this:** Employee was scheduled but no attendance records exist

**Gherkin Scenario:**
```gherkin
Given Lisa O'Brien was scheduled 09:00 - 17:00
And attendance shows NO badge IN or OUT events
When I click "Resolve" on Lisa's row
Then I have 3 options:
  - "Confirm was present" (badge malfunction)
  - "Apply leave" (forgot to badge, taking leave)
  - "Log absence" (no-show, unauthorized absence)
```

**Steps:**

1. **Identify no badge data**
   - **Look for:** Lisa O'Brien in Needs Attention
   - **Discrepancy:** "No badge data" or "Missing attendance"
   - **Scheduled:** 09:00 - 17:00
   - **Badge IN:** (none)
   - **Badge OUT:** (none)

2. **Click Resolve**
   - **Click:** Resolve button on Lisa's row
   - **Expected:** Modal opens with 3 resolution options

3. **Choose appropriate option:**

   **Option A: Confirm was present**
   - **When:** Badge reader broken, but Lisa was definitely there
   - **Reason:** "Badge server offline 09:00-10:00. Lisa confirmed present via WhatsApp photo in Baby Room."
   - **Result:** Paid for full shift

   **Option B: Apply leave**
   - **When:** Lisa forgot to badge in/out, and is taking the day as leave
   - **Reason:** "Lisa took the day off (forgot to submit leave request). Applying Annual Leave retroactively."
   - **Result:** Leave deducted, paid as leave day

   **Option C: Log absence** (if this option exists)
   - **When:** Lisa didn't show up, no communication
   - **Reason:** "No-show. Manager attempted contact at 09:15, 10:00 (no response)."
   - **Result:** Unpaid absence, triggers disciplinary process

4. **Complete resolution**
   - **Select:** Appropriate option
   - **Fill:** Reason (detailed)
   - **Click:** Confirm
   - **Expected:** Discrepancy resolved

**Screenshots:** [Screenshot: No badge data resolution options]

**Common Issues:**
- ❌ Problem: All options seem wrong (e.g., Lisa called in sick but no badge data)
  ✅ Solution: Use "Apply leave" + Sick Leave type. This creates a leave request covering the full shift.

---

### Scenario 9: All Resolved - Proceed to Payroll

**When to use this:** All discrepancies resolved, ready to approve payroll

**Gherkin Scenario:**
```gherkin
Given the Needs Attention count is 0
When all discrepancies are resolved
Then the "Proceed to Payroll" button is enabled
When I click "Proceed to Payroll"
Then I am redirected to Payroll Approval page
And the reconciliation is locked (cannot edit)
```

**Steps:**

1. **Check Attention count**
   - **Look for:** "Needs Attention" summary box
   - **Count:** Should show "0"
   - **Expected:** No unresolved discrepancies

2. **Find Proceed to Payroll button**
   - **Location:** Usually bottom right of page or in header
   - **Look for:** Button labeled "Proceed to Payroll" or "Approve for Payroll"
   - **State:** Should be ENABLED (not grayed out)
   - **Expected:** Button is clickable

3. **Click Proceed to Payroll**
   - **Click:** Proceed to Payroll button
   - **Expected:** Navigation to Payroll Approval page

4. **Verify payroll page loads**
   - **Look for:**
     - Payroll summary for the date
     - Total hours, total cost
     - Export to Collsoft button (Irish payroll)
   - **Expected:** Payroll ready for final approval

5. **Understand the lock**
   - **After "Proceed to Payroll":**
     - Reconciliation data is locked
     - Cannot re-resolve discrepancies without un-approving payroll
   - **Why:** Prevents payroll tampering after approval

**Screenshots:** [Screenshot: Proceed to Payroll button enabled]

**Common Issues:**
- ❌ Problem: Proceed to Payroll button is disabled
  ✅ Solution:
    1. Check Attention count - must be 0
    2. Resolve all remaining discrepancies first
    3. Refresh the page if count is 0 but button still disabled

- ❌ Problem: Button missing entirely
  ✅ Solution: Payroll approval may be on a separate page. Look for "Payroll" menu item or contact support.

---

### Scenario 10: Navigate Between Dates

**When to use this:** Reconcile multiple days

**Gherkin Scenario:**
```gherkin
Given I am viewing reconciliation for Monday (Feb 3)
When I click "Next Day" button
Then the page updates to show Tuesday (Feb 4) data
And summary counts reflect Tuesday's status
```

**Steps:**

1. **View current date**
   - **Look for:** Date selector showing current date (e.g., "Monday, Feb 3, 2026")

2. **Click Previous Day button**
   - **Click:** Left arrow or "Previous Day" button
   - **Expected:**
     - Date changes to Feb 2
     - URL updates (e.g., `?date=2026-02-02`)
     - Page reloads with Feb 2 data

3. **Click Next Day button**
   - **Click:** Right arrow or "Next Day" button
   - **Expected:**
     - Date changes to Feb 3
     - URL updates
     - Page reloads with Feb 3 data

4. **Use date picker** (if available)
   - **Click:** Date selector (calendar icon or date text)
   - **Select:** Any date from calendar
   - **Expected:** Jump directly to that date

**Screenshots:** [Screenshot: Date navigation controls]

**Common Issues:**
- ❌ Problem: Next Day button goes to wrong date
  ✅ Solution: Check URL for date parameter. May be a timezone issue. Ensure date is in YYYY-MM-DD format.

---

## Troubleshooting

### Issue: Reconciliation page shows "No data"
**Symptoms:** Empty page or "No shifts scheduled" message
**Cause:** No shifts for selected date, or attendance data not synced
**Solution:**
1. Verify shifts exist for the date (check Roster page)
2. Check if Paxton attendance data has synced
3. Click Refresh/Generate to re-run reconciliation
4. If still empty, select a different date

---

### Issue: Employee in wrong section
**Symptoms:** Confirmed employee appears in Needs Attention (or vice versa)
**Cause:** Reconciliation calculation error, or badge/leave data changed
**Solution:**
1. Refresh the page (data may be stale)
2. Verify badge IN/OUT times in attendance log
3. Verify leave request status (approved vs pending)
4. Check grace period (15 min) - 16 min late = Needs Attention
5. Re-run reconciliation

---

### Issue: Can't resolve discrepancy - button disabled
**Symptoms:** "Resolve" button is grayed out or missing
**Cause:** Permissions issue or already resolved
**Solution:**
1. Check you have Manager role
2. Verify employee is actually in Needs Attention section
3. Refresh the page
4. If still disabled, check browser console for errors

---

### Issue: Reason field won't accept text
**Symptoms:** Can't type in reason field
**Cause:** Field disabled or UI bug
**Solution:**
1. Click directly in the text area (not the label)
2. Try tabbing to the field with keyboard
3. Refresh the modal (close and reopen)
4. Use different browser if issue persists

---

### Issue: Resolution doesn't save
**Symptoms:** Click Confirm but modal doesn't close, or error appears
**Cause:** Validation error, permissions, or database issue
**Solution:**
1. Check error message for details
2. Ensure reason is filled (minimum 10 characters)
3. Ensure leave type selected (if "Apply leave" chosen)
4. Verify you have manager permissions
5. Check browser console for RPC errors
6. Try again or contact support

---

### Issue: Proceed to Payroll button stays disabled
**Symptoms:** All discrepancies resolved but button still grayed out
**Cause:** UI not refreshed, or hidden unresolved item
**Solution:**
1. Refresh the entire page
2. Check Attention count - must be exactly 0
3. Scroll through all sections - ensure no hidden rows
4. Re-run reconciliation (Refresh button)
5. If persists, check `reconciliation_status` table directly

---

### Issue: Employee appears in both Confirmed and Attention
**Symptoms:** Same employee in multiple sections
**Cause:** Database sync issue or multiple shift records
**Solution:**
1. This should never happen (data integrity bug)
2. Refresh the page
3. Check if employee has multiple shifts on same day
4. Report as critical bug with screenshot

---

### Issue: Leave balance not debited after "Apply leave" resolution
**Symptoms:** Leave applied but balance unchanged
**Cause:** Leave entitlement not deducted, or transaction failed
**Solution:**
1. Check `leave_requests` table - verify entry created
2. Check `leave_entitlements` table - verify balance changed
3. If leave request exists but balance unchanged:
   - Re-run leave deduction RPC manually
   - Or report as bug (LEAVE-001 invariant violation)

---

## Related Guides
- [Demo Mode - Getting Started](./01-demo-mode-onboarding.md)
- [Leave Management](./06-leave-management.md)
- [Control Desk Operations](./05-control-desk-operations.md)
- [Troubleshooting Guide](./08-troubleshooting.md)

## Need More Help?
- **Timebreez Support:** support@timebreez.com
- **Demo mode:** www.timebreez.com/login (try reconciliation with demo data)
- **Book a call:** Schedule a 15-min walkthrough of daily reconciliation
- **Paxton Integration:** Help with attendance data sync
