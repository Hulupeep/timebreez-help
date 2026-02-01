# Demo Mode - Getting Started with Timebreez

## Who This Is For
**Managers and Administrators** evaluating Timebreez for their childcare facility

## What You'll Learn
- How to access the demo organization
- Understanding the demo data structure
- Navigating key features safely
- Exploring without breaking anything
- What happens to demo data

## Prerequisites
- None! Demo mode is instant-access
- No signup required
- No credit card needed

---

## Quick Start (TL;DR)

1. Visit `www.timebreez.com/login`
2. Auto-login as Sandra Murphy (Demo Manager)
3. Explore the **Sunshine Early Learning Centre** demo org
4. Try Control Desk, Leave Requests, Settings
5. All changes reset daily at midnight

---

## Understanding Demo Mode

### What is Demo Mode?

Demo mode gives you instant access to a **fully populated childcare organization** called **Sunshine Early Learning Centre**. You'll see:

- **7 rooms:** Baby Room, Baby Steps, Wobblers, Toddlers, Preschool, ECC, Afterschool
- **10 employees:** Sandra Murphy, Emma Murphy, Lisa O'Brien, Aoife O'Brien, and more
- **Sample data:** Leave requests, shifts, sessions, dispatches
- **Real features:** Everything works exactly like production

### Demo Organization Details

**Organization Name:** Sunshine Early Learning Centre
**Demo Manager:** Sandra Murphy (demo@timebreez.com)
**Organization ID:** `00000000-0000-0000-0000-000000000001`
**Location:** Ireland (Irish childcare compliance enabled)

### What's Different in Demo Mode?

| Feature | Demo Mode | Production |
|---------|-----------|------------|
| Login | Auto-login (no password) | Email + password required |
| Data | Shared demo data | Your private organization data |
| Persistence | Resets daily | Permanent storage |
| Users | 10 demo employees | Your real staff |
| Rooms | 7 pre-configured rooms | Your actual rooms |

---

## Step-by-Step Guides

### Scenario 1: First Time Login

**When to use this:** You're trying Timebreez for the first time

**Gherkin Scenario:**
```gherkin
Given I visit www.timebreez.com/login
When the page loads
Then I am automatically logged in as Sandra Murphy
And I see the Sunshine Early Learning Centre dashboard
```

**Steps:**

1. **Open your web browser**
   - **Enter:** `www.timebreez.com/login` in the address bar
   - **Expected:** Page loads and auto-logs you in

2. **Verify you're in demo mode**
   - **Look for:** Organization name "Sunshine Early Learning Centre" in the top left
   - **Look for:** Your name "Sandra Murphy" in the top right corner
   - **Expected:** Both visible, confirming demo mode active

3. **Check the demo org ID** (optional)
   - **Click:** Your profile icon (top right)
   - **Expected:** You see "Demo Organization" badge

**Screenshots:** [Screenshot: Demo login screen]

**Common Issues:**
- ❌ Problem: Page asks for login credentials
  ✅ Solution: Make sure you're on `/login` not `/signup`. Demo mode only works on the login page.

- ❌ Problem: I see a different organization
  ✅ Solution: Clear your browser cache and cookies, then refresh the page.

---

### Scenario 2: Navigating the Dashboard

**When to use this:** You want to explore what Timebreez offers

**Gherkin Scenario:**
```gherkin
Given I am logged in as Sandra Murphy
When I view the dashboard
Then I see navigation links for Control Desk, Leave Requests, Settings
And I see 7 room cards showing current status
```

**Steps:**

1. **View the main dashboard**
   - **Look for:** Dashboard navigation menu on the left sidebar
   - **Expected:** Menu items: Control Desk, Leave Requests, Employees, Rooms, Settings, etc.

2. **Open Control Desk**
   - **Click:** "Control Desk" in the left sidebar
   - **Look for:** 7 room tiles (Baby Room, Baby Steps, Wobblers, Toddlers, Preschool, ECC, Afterschool)
   - **Expected:** Each room shows required/planned/present staff counts

3. **Check room status colors**
   - **Look for:** Room tiles with colored badges
   - **Green badge:** Room is properly staffed
   - **Amber badge:** Room is constrained (close to minimum ratio)
   - **Red badge:** Room is understaffed (below required ratio)
   - **Expected:** At least one room showing each status

4. **View Leave Requests**
   - **Click:** "Leave Requests" in the sidebar
   - **Look for:** List of pending/approved leave requests
   - **Expected:** You see employees' names, dates, leave types (Annual, Sick, etc.)

**Screenshots:** [Screenshot: Dashboard with sidebar navigation]

**Common Issues:**
- ❌ Problem: Control Desk shows "No rooms configured"
  ✅ Solution: This was fixed in Wave 31. Refresh the page. If it persists, the `get_room_snapshots()` RPC may have permission issues.

- ❌ Problem: Leave Requests page shows "No room assignment found"
  ✅ Solution: This was fixed in Wave 31. Verify all demo employees have room assignments by checking Employee page.

---

### Scenario 3: Exploring Rooms

**When to use this:** You want to understand room-based scheduling

**Gherkin Scenario:**
```gherkin
Given I am on the Control Desk page
When I view the Baby Room tile
Then I see required staff count (e.g., "3 required")
And I see planned staff count (e.g., "3 planned")
And I see present staff count (e.g., "2 present")
And I see room status badge (GREEN/AMBER/RED)
```

**Steps:**

1. **Navigate to Control Desk**
   - **Click:** "Control Desk" in sidebar
   - **Expected:** 7 room tiles visible

2. **Examine Baby Room tile**
   - **Look for:** Room tile labeled "Baby Room"
   - **Expected:** You see:
     - **Required:** Number based on child ratio (e.g., "3 required")
     - **Planned:** Staff scheduled for this room today (e.g., "3 planned")
     - **Present:** Staff who have badged in (e.g., "2 present")
     - **Status Badge:** Color-coded indicator

3. **Understand the status badges**
   - **GREEN badge:** present ≥ required (room is safe)
   - **AMBER badge:** present = required - 1 (close to minimum)
   - **RED badge:** present < required - 1 (understaffed, urgent)

4. **Click a room tile to see details**
   - **Click:** Any room tile
   - **Expected:** Modal opens showing staff list, session info, coverage details

**Screenshots:** [Screenshot: Control Desk with room tiles]

**Common Issues:**
- ❌ Problem: Required count shows "0"
  ✅ Solution: Room may not have child_count set. Go to Admin > Rooms and ensure each room has a child count configured.

---

### Scenario 4: Viewing Employee Schedules

**When to use this:** You want to see who's working today

**Gherkin Scenario:**
```gherkin
Given I am logged in as Sandra Murphy
When I navigate to the Employees page
Then I see a list of all 10 demo employees
And I can click an employee to see their schedule
```

**Steps:**

1. **Navigate to Employees**
   - **Click:** "Employees" in sidebar
   - **Expected:** List of 10 employees

2. **Click on Emma Murphy**
   - **Click:** Emma Murphy's row
   - **Expected:** Employee detail page opens

3. **View Emma's schedule**
   - **Look for:** Weekly schedule grid
   - **Expected:** You see shifts assigned to rooms (e.g., "Baby Room 09:00 - 17:00")

4. **Check leave balance**
   - **Look for:** "Leave Balance" section
   - **Expected:** Shows Annual Leave, Sick Leave, etc. with remaining days

**Screenshots:** [Screenshot: Employee list and detail view]

---

### Scenario 5: Testing Leave Requests

**When to use this:** You want to see how leave management works

**Gherkin Scenario:**
```gherkin
Given I am viewing Leave Requests
When I click "Request Leave"
Then I see a form to enter dates and leave type
And I can submit a leave request for Emma Murphy
```

**Steps:**

1. **Navigate to Leave Requests**
   - **Click:** "Leave Requests" in sidebar
   - **Expected:** Leave request list page

2. **Click "Request Leave"**
   - **Click:** Blue "Request Leave" button (top right)
   - **Expected:** Leave request modal opens

3. **Fill in the form**
   - **Select Employee:** Emma Murphy
   - **Select Dates:** Pick a date range (e.g., next Monday-Wednesday)
   - **Select Leave Type:** Annual Leave
   - **Enter Note:** "Family vacation"
   - **Expected:** Form fields accept your input

4. **Submit the request**
   - **Click:** "Submit" button
   - **Expected:** Success toast appears, modal closes, new request appears in list

5. **Approve the request** (manager view)
   - **Click:** "Approve" button on the new request
   - **Expected:** Request status changes to "Approved"
   - **Expected:** Emma's leave balance decreases by the number of days

**Screenshots:** [Screenshot: Leave request form]

**Common Issues:**
- ❌ Problem: Submit button is disabled
  ✅ Solution: Ensure all required fields are filled (employee, dates, leave type)

- ❌ Problem: "Insufficient balance" error
  ✅ Solution: Check Emma's leave balance. Demo employees have limited leave days. Choose a different employee or shorter date range.

---

### Scenario 6: Exploring Settings Pages

**When to use this:** You want to configure organization settings

**Gherkin Scenario:**
```gherkin
Given I am logged in as Sandra Murphy
When I navigate to Settings > Org Notifications
Then the page loads without errors
And I see notification rules I can toggle ON/OFF
```

**Steps:**

1. **Navigate to Settings**
   - **Click:** "Settings" in sidebar
   - **Expected:** Settings submenu expands

2. **Open Org Notifications**
   - **Click:** "Org Notifications" submenu item
   - **Expected:** Page loads showing notification rules

3. **View notification rules**
   - **Look for:** Toggle switches for rules like:
     - "Leave request submitted"
     - "Shift cancelled"
     - "No-show alert"
   - **Expected:** At least 4 notification rules visible

4. **Toggle a rule ON/OFF**
   - **Click:** Toggle switch for "Leave request submitted"
   - **Expected:** Toggle changes state, save button appears

5. **Save changes**
   - **Click:** "Save" button
   - **Expected:** Success toast appears

**Screenshots:** [Screenshot: Org Notifications settings]

**Common Issues:**
- ❌ Problem: Page shows "RLS policy violation" or "permission denied"
  ✅ Solution: This was fixed in Wave 31 (Fix #3 and #4). Refresh the page. If it persists, contact support.

---

### Scenario 7: Generating Calendar Feeds

**When to use this:** You want to sync your schedule to Google Calendar or Outlook

**Gherkin Scenario:**
```gherkin
Given I am on Settings > Calendar Feeds
When I click "Generate Feed"
Then a unique calendar feed URL is created
And I can copy the URL to add to my calendar app
```

**Steps:**

1. **Navigate to Calendar Feeds**
   - **Click:** Settings > Calendar Feeds
   - **Expected:** Calendar feed settings page loads

2. **Click "Generate Feed"**
   - **Click:** Blue "Generate Feed" button
   - **Expected:** Loading spinner appears briefly

3. **Copy the feed URL**
   - **Look for:** A long URL starting with `webcal://` or `https://`
   - **Click:** "Copy" button next to the URL
   - **Expected:** "Copied!" toast appears

4. **Add to Google Calendar** (external step)
   - Open Google Calendar
   - Click Settings > Add calendar > From URL
   - Paste the copied URL
   - **Expected:** Your Timebreez schedule appears in Google Calendar

**Screenshots:** [Screenshot: Calendar feed generation]

**Common Issues:**
- ❌ Problem: "Generate Feed" button does nothing
  ✅ Solution: This was fixed in Wave 32 (Fix #6). Ensure the `generate_calendar_feed_token` RPC exists and has proper permissions.

---

### Scenario 8: Understanding Demo Data Reset

**When to use this:** You made changes and want to start fresh

**Gherkin Scenario:**
```gherkin
Given I have created test leave requests in demo mode
When I wait until midnight (UTC)
Then all my test data is reset to the original demo template
And I can start fresh the next day
```

**Steps:**

1. **Create some test data**
   - Add a leave request
   - Edit an employee
   - Change a room setting
   - **Expected:** Your changes are saved

2. **Wait until midnight (or come back tomorrow)**
   - Demo data resets at **00:00 UTC**
   - **Expected:** All your test changes are gone, replaced with fresh demo data

3. **Verify reset occurred**
   - **Look for:** Original demo leave requests (your test requests are gone)
   - **Look for:** Original employee names and settings
   - **Expected:** Everything back to default template

**Screenshots:** [Screenshot: Demo data reset notice]

**Common Issues:**
- ❌ Problem: My changes are still there the next day
  ✅ Solution: Demo mode currently shares data across all users. For a personal sandbox, sign up for a free trial account.

---

### Scenario 9: What NOT to Do in Demo Mode

**When to use this:** You want to avoid breaking the demo for others

**Gherkin Scenario:**
```gherkin
Given demo mode is shared across all visitors
When I delete employees or rooms
Then other users may see errors
And the demo experience is degraded for everyone
```

**⚠️ DO NOT:**
- ❌ Delete employees (others may be testing with that employee)
- ❌ Delete rooms (this breaks Control Desk for all users)
- ❌ Delete all leave types (blocks leave requests)
- ❌ Change organization name to offensive text
- ❌ Upload large files (demo has storage limits)

**✅ DO:**
- ✅ Add leave requests (test the workflow)
- ✅ Approve/deny requests (see manager flow)
- ✅ View reports (read-only, safe)
- ✅ Toggle settings (changes reset daily)
- ✅ Explore navigation (can't break anything)

---

## Troubleshooting

### Issue: Auto-login doesn't work
**Symptoms:** Page shows email/password login form
**Cause:** You're on `/signup` instead of `/login`
**Solution:**
1. Check the URL - ensure it's `www.timebreez.com/login`
2. If on `/signup`, click "Sign in" link at the bottom
3. Clear browser cache if issue persists

---

### Issue: Control Desk shows "No rooms configured"
**Symptoms:** Empty Control Desk page with error message
**Cause:** RLS (Row Level Security) policy on `get_room_snapshots()` RPC
**Solution:**
1. This was fixed in Wave 31 - refresh the page
2. If still broken, report as a bug (include screenshot)
3. Expected: 7 room tiles should always appear

---

### Issue: Leave requests show "No room assignment found"
**Symptoms:** Leave request cards show error instead of room name
**Cause:** Employee missing primary room assignment
**Solution:**
1. This was fixed in Wave 31 - refresh the page
2. If still broken, check Employees page
3. Verify demo employees all have `is_primary = true` room assignment

---

### Issue: Settings pages crash or show "Permission denied"
**Symptoms:** White screen or error message on Org Notifications, My Notifications, Leave Types
**Cause:** RLS policies missing or incorrect on `notification_rules`, `notification_preferences`, `leave_types` tables
**Solution:**
1. These were fixed in Wave 31 (Fix #3, #4, #5) - refresh the page
2. If still broken, report as a critical bug
3. Expected: All settings pages should load without errors

---

### Issue: "Demo has expired" message
**Symptoms:** Cannot access dashboard, see expiry notice
**Cause:** Your personal demo org expired (30 days)
**Solution:**
1. Demo mode (shared) never expires - use `/login`
2. If you created a personal trial, contact support to extend
3. Or sign up for a paid subscription to keep your data

---

## Related Guides
- [Session Scheduling (ECCE/AIMS)](./02-session-scheduling-ecce-aims.md)
- [Cover Staff Dispatch](./03-cover-staff-dispatch.md)
- [Daily Reconciliation](./04-daily-reconciliation.md)
- [Settings and Configuration](./07-settings-and-configuration.md)

## Need More Help?
- **Contact:** support@timebreez.com
- **Demo mode:** www.timebreez.com/login (instant access, no signup)
- **Documentation:** https://help.timebreez.com
- **Book a call:** Schedule a 15-min walkthrough with our team
