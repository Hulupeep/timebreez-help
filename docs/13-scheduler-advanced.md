# Advanced Scheduler Features - Beyond Basic Rostering

## Who This Is For
**Childcare Managers and Administrators** who want to use advanced scheduler features like schedule duplication, sharing, cover staff grid rows, and operating day configuration.

## What You'll Learn
- Copying last week's schedule in one click
- Sharing and exporting schedules (PDF, Excel, WhatsApp, QR code)
- Understanding the Cover Staff Grid Row (purple row with compliance indicators)
- Configuring scheduler preferences (cover requirements, validation modes)
- Setting operating days (which days your facility is open)
- Using the Cover Pool Layout Toggle

## Prerequisites
- Manager or Admin role in Timebreez
- Basic familiarity with the Scheduler page (creating shifts, assigning rooms)
- At least one week of schedule data already entered
- Rooms and employees configured

---

## Quick Start (TL;DR)

1. Go to **Scheduler** in sidebar
2. Click **"Copy Last Week"** to duplicate the previous week's shifts
3. Click **"Share"** to export as PDF, Excel, or send via WhatsApp
4. Check the **purple Cover Staff row** at the bottom of the grid for compliance
5. Go to **Settings > Scheduler Preferences** for validation and cover rules
6. Go to **Settings > Operating Days** to configure which days you are open
7. Toggle **"Show Cover Pool"** to expand or collapse the cover row

---

## Understanding Advanced Scheduler

### Beyond Basic Shifts

The Timebreez Scheduler is more than a simple shift planner. Advanced features help you:

- **Save time** - Copy entire weeks instead of rebuilding schedules from scratch
- **Communicate** - Share schedules with staff via WhatsApp, PDF, or QR code
- **Stay compliant** - Cover Staff Grid Row shows real-time compliance indicators
- **Customize** - Set validation modes, cover requirements, and operating days

### Scheduler Layout

| Section | Description |
|---------|------------|
| **Week Navigation** | Arrows to move between weeks, "Today" button |
| **Room Rows** | One row per room, showing assigned staff per day |
| **Employee Cells** | Individual shift blocks with times and room |
| **Cover Staff Row** | Purple row at bottom showing cover pool availability |
| **Action Bar** | Copy, Share, Export, Preferences buttons |
| **Validation Panel** | Warnings and errors for the current week |

---

## Step-by-Step Guides

### Scenario 1: Copy Last Week's Schedule

**When to use this:** Your schedule is similar week to week and you want to avoid re-entering shifts manually

**Gherkin Scenario:**
```gherkin
Given I have a completed schedule for the week of January 5th
And I am viewing the empty week of January 12th
When I click "Copy Last Week"
Then all shifts from January 5th are duplicated to January 12th
And shift times, room assignments, and employee assignments are preserved
And I can make adjustments to the copied schedule
```

**Steps:**

1. **Navigate to the target week**
   - **Click:** Scheduler in the sidebar
   - **Navigate:** Use the week arrows to go to the week you want to fill
   - **Expected:** Empty or partially filled schedule grid for the target week

2. **Click "Copy Last Week"**
   - **Look for:** "Copy Last Week" button in the action bar (top of scheduler)
   - **Click:** The button
   - **Expected:** Confirmation dialog appears: "Copy all shifts from [previous week dates] to [current week dates]?"

3. **Confirm the copy**
   - **Read:** The confirmation message carefully
   - **Note:** This will NOT overwrite existing shifts (only fills empty slots)
   - **Click:** "Confirm" or "Copy"
   - **Expected:** Loading spinner, then schedule populates with copied shifts

4. **Review the copied schedule**
   - **Check:** Each room row to verify shifts copied correctly
   - **Verify:** Employee names, shift times, and room assignments match last week
   - **Expected:** Schedule mirrors the previous week

5. **Make adjustments**
   - **Edit:** Click any shift cell to modify times, room, or employee
   - **Add:** Click empty cells to add new shifts
   - **Remove:** Click a shift and press Delete to remove individual shifts
   - **Expected:** Adjustments saved as you make them

6. **Save the week** (if manual save required)
   - **Click:** "Save" or changes auto-save
   - **Expected:** Schedule for the new week is finalized

**Screenshots:** [Screenshot: Copy Last Week button and confirmation dialog]

**Common Issues:**
- Problem: "Copy Last Week" button is grayed out
  Solution: The previous week has no shifts to copy. Navigate back one week and verify it has a completed schedule.

- Problem: Copied shifts overlap with existing shifts
  Solution: The copy only fills empty slots. If you want to replace the entire week, clear the current week first (Action Bar > "Clear Week"), then copy.

---

### Scenario 2: Share Schedule via WhatsApp

**When to use this:** You want to send this week's schedule to staff via WhatsApp

**Gherkin Scenario:**
```gherkin
Given I have a completed schedule for the current week
When I click "Share" on the Scheduler
And I select "WhatsApp"
Then a formatted schedule message is generated
And the WhatsApp share dialog opens
And I can send the schedule to individual staff or a group chat
```

**Steps:**

1. **Verify the schedule is complete**
   - **Check:** All rooms have staff assigned for each day
   - **Check:** No validation warnings (red badges in validation panel)
   - **Expected:** Complete, error-free schedule

2. **Click the "Share" button**
   - **Look for:** "Share" button in the action bar
   - **Click:** Share button
   - **Expected:** Share menu opens with export options

3. **Select the share method**
   - **Options available:**
     - **PDF** - Download a formatted PDF of the schedule
     - **Excel** - Download an Excel spreadsheet
     - **WhatsApp** - Generate a text message for WhatsApp
     - **QR Code** - Generate a QR code linking to the schedule
   - **Click:** "WhatsApp"
   - **Expected:** WhatsApp share dialog or formatted text appears

4. **Review the generated message**
   - **Format:** Text-based schedule with:
     - Week dates (e.g., "Week of 12 Jan - 16 Jan 2026")
     - Per-day breakdown of rooms and staff
     - Shift times for each employee
   - **Expected:** Readable, accurate schedule summary

5. **Send via WhatsApp**
   - **Option A - Direct share:** If on mobile, WhatsApp opens with pre-filled message
   - **Option B - Copy text:** Click "Copy" and paste into WhatsApp manually
   - **Select:** Recipient (individual staff member or staff group chat)
   - **Click:** Send
   - **Expected:** Staff receive the schedule on WhatsApp

6. **Alternative: Share as PDF**
   - **Click:** "PDF" in the share menu
   - **Expected:** PDF downloads with formatted schedule grid
   - **Use:** Print for notice board, email as attachment, or share via any app

7. **Alternative: Generate QR Code**
   - **Click:** "QR Code" in the share menu
   - **Expected:** QR code image appears
   - **Print:** Post on staff notice board
   - **Staff scan:** Opens schedule in their browser
   - **Expected:** Schedule viewable on any phone via QR scan

**Screenshots:** [Screenshot: Share menu with WhatsApp, PDF, Excel, QR Code options]

**Common Issues:**
- Problem: WhatsApp share doesn't open on desktop
  Solution: WhatsApp share works best on mobile devices. On desktop, use "Copy" to copy the formatted text, then paste into WhatsApp Web manually.

- Problem: PDF layout is cut off or misaligned
  Solution: Try landscape orientation. If the schedule has many rooms, use the "Compact" layout option in Scheduler Preferences before exporting.

---

### Scenario 3: Check Cover Compliance on the Cover Staff Grid Row

**When to use this:** Verify that you have enough cover staff scheduled to handle breaks and absences

**Gherkin Scenario:**
```gherkin
Given I am viewing the Scheduler for the current week
When I look at the purple Cover Staff row at the bottom of the grid
Then I see cover staff names, shift times, and compliance indicators
And GREEN indicators mean sufficient cover for that day
And RED indicators mean insufficient cover for that day
```

**Steps:**

1. **Locate the Cover Staff Grid Row**
   - **Look for:** A purple-colored row at the bottom of the schedule grid
   - **Label:** "Cover Staff" or "Cover Pool"
   - **Expected:** Purple row visible below all room rows

2. **Read the cover staff entries**
   - **Each cell (per day) shows:**
     - Cover staff name(s) scheduled for that day
     - Shift times (e.g., "Lisa O'Brien 09:00 - 17:00")
     - Compliance indicator (color-coded)
   - **Expected:** Cover staff visible for each day they are scheduled

3. **Understand the compliance indicators**
   - **GREEN checkmark:** Sufficient cover capacity for the day
     - Meaning: Cover hours >= estimated break hours needed
   - **AMBER warning:** Tight cover capacity
     - Meaning: Cover hours are close to (but meet) minimum requirements
   - **RED alert:** Insufficient cover capacity
     - Meaning: Cover hours < estimated break hours needed
   - **Expected:** Color indicators on each day

4. **Investigate a RED day**
   - **Click:** The RED cell in the Cover Staff row
   - **Expected:** Detail panel shows:
     - Total cover hours available: e.g., 8 hours
     - Total break hours needed: e.g., 12 hours
     - Shortfall: 4 hours
     - **Suggestion:** "Schedule 1 additional cover staff"

5. **Resolve the shortfall**
   - **Option A:** Schedule an additional cover staff member for that day
   - **Option B:** Stagger break times to reduce peak demand
   - **Option C:** Use cross-room coverage (room staff cover each other)
   - **Expected:** After adding cover, indicator changes to GREEN or AMBER

**Screenshots:** [Screenshot: Purple cover staff row with compliance indicators]

**Common Issues:**
- Problem: Cover Staff row is not visible
  Solution: The row may be collapsed. Look for a "Show Cover Pool" toggle at the bottom of the scheduler and click it to expand.

- Problem: Compliance indicator always shows RED
  Solution: Verify the cover requirement settings (Settings > Scheduler Preferences). If break hours are overestimated, the indicator will always show RED. Adjust the break duration setting.

---

### Scenario 4: Configure Operating Days

**When to use this:** Your facility is not open 7 days a week and you want the scheduler to reflect your actual operating days

**Gherkin Scenario:**
```gherkin
Given my facility operates Monday through Friday
When I go to Settings > Operating Days
And I uncheck Saturday and Sunday
And I save
Then the Scheduler only shows Monday through Friday columns
And I cannot schedule shifts on Saturday or Sunday
```

**Steps:**

1. **Navigate to Operating Days settings**
   - **Click:** Settings > Operating Days (or Settings > Organization > Operating Days)
   - **Expected:** Operating days configuration page loads

2. **View current operating days**
   - **Look for:** 7 day checkboxes (Monday through Sunday)
   - **Default:** All 7 days checked (open every day)
   - **Expected:** Current configuration displayed

3. **Uncheck non-operating days**
   - **Example:** Uncheck Saturday and Sunday
   - **Click:** Saturday checkbox to uncheck
   - **Click:** Sunday checkbox to uncheck
   - **Expected:** Saturday and Sunday are unchecked

4. **Save the configuration**
   - **Click:** "Save" button
   - **Expected:** Success toast "Operating days updated"

5. **Verify the Scheduler updated**
   - **Navigate to:** Scheduler page
   - **Expected:** Only Monday-Friday columns appear in the grid
   - **Saturday/Sunday:** No longer visible or grayed out
   - **Expected:** Scheduler reflects operating days

6. **Handle exceptions** (e.g., open on a holiday Saturday)
   - **Check:** Operating days apply as the default schedule
   - **Override:** Individual shifts can still be created on non-operating days if needed (some systems allow exceptions)
   - **Expected:** Default is Mon-Fri, but exceptions are possible

**Screenshots:** [Screenshot: Operating Days settings with Mon-Fri checked]

**Common Issues:**
- Problem: Scheduler still shows 7 days after changing operating days
  Solution: Refresh the Scheduler page. If still showing 7 days, clear browser cache. The change applies to the current and future weeks.

- Problem: I need to open on a Saturday for a special event
  Solution: Operating days are the default. Check if your system supports per-week overrides, or temporarily re-enable Saturday, schedule the shifts, then disable it again.

---

### Scenario 5: Configure Scheduler Preferences

**When to use this:** Customize how the scheduler validates shifts and calculates cover requirements

**Gherkin Scenario:**
```gherkin
Given I want stricter validation on my schedule
When I go to Settings > Scheduler Preferences
And I set validation mode to "Strict"
And I set cover requirement to "1 cover per 10 room staff"
And I save
Then the Scheduler shows warnings for any day without sufficient cover
And shifts that violate ratio rules are flagged in red
```

**Steps:**

1. **Navigate to Scheduler Preferences**
   - **Click:** Settings > Scheduler Preferences
   - **Expected:** Preferences page loads with current settings

2. **Set validation mode**
   - **Look for:** "Validation Mode" dropdown
   - **Options:**
     - **Off:** No validation warnings (not recommended)
     - **Warn:** Yellow warnings for issues, but allows saving
     - **Strict:** Red errors that block saving until resolved
   - **Select:** Your preferred mode
   - **Expected:** Dropdown updated

3. **Set cover requirement rule**
   - **Look for:** "Cover Staff Requirement" section
   - **Options:**
     - **None:** No cover requirement enforced
     - **1 per 10:** One cover staff per 10 room staff scheduled
     - **1 per room:** One cover staff for every room open
     - **Custom:** Enter your own formula
   - **Select:** Your preferred rule
   - **Expected:** Rule selected

4. **Configure break duration estimate**
   - **Look for:** "Break Duration" field
   - **Default:** 30 minutes
   - **Adjust:** If your breaks are longer (e.g., 45 minutes), update the value
   - **Impact:** Affects cover compliance calculation on the Cover Staff Grid Row

5. **Save preferences**
   - **Click:** "Save Preferences" button
   - **Expected:** Success toast "Scheduler preferences saved"

6. **Verify validation on Scheduler**
   - **Navigate to:** Scheduler page
   - **Expected:** Validation warnings/errors now reflect your settings
   - **Look for:** Warning badges on days that violate the new rules

**Screenshots:** [Screenshot: Scheduler Preferences with validation mode and cover rules]

**Common Issues:**
- Problem: Strict mode blocks saving even for minor issues
  Solution: Switch to "Warn" mode while building the initial schedule, then switch to "Strict" once the schedule is finalized.

- Problem: Cover requirement formula seems wrong
  Solution: The formula uses the total number of room staff scheduled for the day, not the number of rooms. Verify by checking the calculation on the Cover Staff Grid Row detail panel.

---

### Scenario 6: Toggle Cover Pool Layout

**When to use this:** Show or hide the cover staff details on the scheduler grid

**Gherkin Scenario:**
```gherkin
Given I am viewing the Scheduler
When I click the "Show Cover Pool" toggle
Then the purple Cover Staff row expands to show full details
When I click the toggle again
Then the Cover Staff row collapses to a compact summary
```

**Steps:**

1. **Find the Cover Pool toggle**
   - **Look for:** Toggle button or switch labeled "Show Cover Pool"
   - **Location:** Bottom of the scheduler grid or in the action bar
   - **Expected:** Toggle is visible

2. **Expand the Cover Pool**
   - **Click:** Toggle to "ON" or "Show"
   - **Expected:** Purple Cover Staff row expands showing:
     - Individual cover staff names per day
     - Shift times for each cover staff
     - Compliance indicators (GREEN/AMBER/RED)
     - Total cover hours available

3. **Collapse the Cover Pool**
   - **Click:** Toggle to "OFF" or "Hide"
   - **Expected:** Cover Staff row collapses to a single summary line:
     - "2 cover staff | 16h available | Sufficient"
   - **Expected:** More screen space for room rows

4. **Choose your preferred view**
   - **Expanded:** Best for planning and verifying cover compliance
   - **Collapsed:** Best for day-to-day use when cover is already planned
   - **Expected:** Preference persists between sessions

**Screenshots:** [Screenshot: Cover Pool toggle expanded vs collapsed]

**Common Issues:**
- Problem: Toggle doesn't appear
  Solution: The Cover Pool toggle only appears when at least one employee is flagged as cover staff. Verify you have cover staff configured (see [Cover Staff Dispatch](./03-cover-staff-dispatch.md)).

---

## Troubleshooting

### Issue: "Copy Last Week" creates duplicate shifts
**Symptoms:** After copying, some employees have two shifts on the same day
**Cause:** Shifts already existed for some days before copying
**Solution:**
1. The copy only fills empty slots; it does not overwrite existing shifts
2. Delete the duplicate shifts manually
3. For a clean copy, use "Clear Week" first, then "Copy Last Week"

---

### Issue: WhatsApp share shows wrong dates
**Symptoms:** Shared schedule has incorrect week dates
**Cause:** Timezone mismatch between browser and server
**Solution:**
1. Verify your browser timezone matches your facility location
2. Check Settings > Organization > Timezone is correct
3. Refresh the Scheduler and try sharing again

---

### Issue: Cover Staff Grid Row missing
**Symptoms:** No purple row at bottom of scheduler
**Cause:** No employees flagged as cover staff, or toggle is collapsed
**Solution:**
1. Check "Show Cover Pool" toggle (expand it)
2. Verify at least one employee has `is_cover_staff = true`
3. Verify cover staff have shifts scheduled for the visible week
4. If still missing, refresh the page

---

### Issue: Validation warnings appear but schedule looks correct
**Symptoms:** Yellow or red warnings on days that seem properly staffed
**Cause:** Validation rules may be stricter than expected
**Solution:**
1. Click the warning to see the specific issue
2. Check Settings > Scheduler Preferences for validation rules
3. Adjust rules if they are too strict for your situation
4. Common false positives: ratio rounding, session-time ratio changes

---

### Issue: Operating days change not reflected
**Symptoms:** Scheduler still shows 7 days after disabling weekends
**Cause:** Browser cache or page not refreshed
**Solution:**
1. Hard refresh the Scheduler page (Ctrl+Shift+R)
2. Clear browser cache if needed
3. Verify the change saved in Settings > Operating Days
4. Change applies to current and future weeks (past weeks remain unchanged)

---

## Related Guides
- [Session Scheduling (ECCE/AIMS)](./02-session-scheduling-ecce-aims.md)
- [Cover Staff Dispatch](./03-cover-staff-dispatch.md)
- [Control Desk Operations](./05-control-desk-operations.md)
- [Daily Reconciliation](./04-daily-reconciliation.md)

## Need More Help?
- **Timebreez Support:** support@timebreez.com
- **Demo mode:** www.timebreez.com/login (try advanced scheduler features with demo data)
- **Book a call:** Schedule a 15-min walkthrough of advanced scheduler features
