# Programs & Events - Activity Management

## Who This Is For
**Childcare and Hospitality Managers** who need to create programs (e.g., Summer Camp, After School Club) and schedule recurring events with staff assignments.

## What You'll Learn
- Creating programs for your facility
- Adding events with recurrence patterns (weekly, daily)
- Detecting and resolving event conflicts
- Managing staff availability and RSVP
- Running event check-in via the PWA
- Generating program reports and CSV exports

## Prerequisites
- Manager or Admin role in Timebreez
- At least one room configured
- Staff members created with availability set
- Understanding of your facility's program calendar

---

## Quick Start (TL;DR)

1. Go to **Programs** in sidebar
2. Click **"New Program"** and fill in name, date range, rooms
3. Click **"Add Event"** within a program
4. Set **recurrence** (weekly on Mondays, daily, etc.)
5. Check **Conflict Detection** panel for overlaps
6. Assign staff and send **RSVP requests**
7. On event day, use **Check-In** from PWA
8. Export **Program Report** as CSV

---

## Understanding Programs & Events

### What is a Program?

A **program** is a container for a series of related events. Examples:

- **Summer Camp** (June 1 - August 31, daily activities)
- **After School Club** (Mon-Fri, 15:00 - 17:30 during term)
- **Parent & Toddler Group** (Tuesdays, 10:00 - 12:00)
- **Holiday Camp** (bank holiday weeks, full day)
- **Weekend Enrichment** (Saturdays, art/music/sport rotation)

**Program vs Event:**

| Concept | Program | Event |
|---------|---------|-------|
| **Scope** | Container (many events) | Single occurrence |
| **Duration** | Weeks or months | Hours |
| **Staff** | Pool of eligible staff | Specific assigned staff |
| **Recurrence** | Date range | Repeating pattern within range |
| **Billing** | Linked to subscription tier | Free within program limits |

### When to Use Programs

**Programs are ideal for:**
- Structured activities that repeat on a schedule
- Activities requiring specific staff qualifications
- Events that need attendance tracking and reporting
- Activities spanning multiple rooms or mixed age groups

**NOT ideal for:**
- One-off meetings (use calendar instead)
- Regular room shifts (use Roster/Schedule)
- Leave or absence tracking (use Leave Management)

---

## Step-by-Step Guides

### Scenario 1: Create a Program

**When to use this:** You are setting up a new recurring activity for your facility

**Gherkin Scenario:**
```gherkin
Given I am logged in as a manager
When I navigate to Programs
And I click "New Program"
And I fill in name "Summer Camp 2026", start date "2026-06-01", end date "2026-08-31"
And I select rooms "Preschool" and "ECC"
And I click "Save Program"
Then the program is created
And I see it in the programs list
```

**Steps:**

1. **Navigate to Programs**
   - **Click:** "Programs" in the sidebar
   - **Expected:** Programs list page loads

2. **Click New Program**
   - **Click:** Blue "New Program" button (top right)
   - **Expected:** Program creation form opens

3. **Fill in program details**
   - **Program Name:** Summer Camp 2026
   - **Description:** Full-day summer camp for ages 3-6 with outdoor activities, arts, and sports
   - **Start Date:** 2026-06-01
   - **End Date:** 2026-08-31
   - **Rooms:** Select "Preschool" and "ECC" from multi-select dropdown
   - **Expected:** All fields accept input

4. **Set program capacity** (optional)
   - **Max Participants:** 30
   - **Min Staff Required:** 3
   - **Expected:** Capacity fields saved

5. **Save the program**
   - **Click:** "Save Program" button
   - **Expected:** Success toast "Program created successfully"
   - **Expected:** Redirected to program detail page

6. **Verify program in list**
   - **Navigate:** Back to Programs list
   - **Look for:** "Summer Camp 2026" with date range and room badges
   - **Expected:** Program appears in the list

**Screenshots:** [Screenshot: New Program form with fields filled]

**Common Issues:**
- ❌ Problem: "End date must be after start date" error
  ✅ Solution: Verify start date is before end date. Dates must be in the future or current.

- ❌ Problem: No rooms appear in dropdown
  ✅ Solution: Rooms must be configured first. Go to Admin > Rooms and create rooms before setting up programs.

---

### Scenario 2: Add a Recurring Event to a Program

**When to use this:** You want to schedule repeating activities within a program

**Gherkin Scenario:**
```gherkin
Given I have a program "After School Club"
When I click "Add Event"
And I set title "Art Workshop", time 15:30-17:00
And I set recurrence to "Weekly on Monday, Wednesday, Friday"
And I click "Save Event"
Then events are generated for each Mon/Wed/Fri within the program date range
And I see them on the program calendar
```

**Steps:**

1. **Open the program**
   - **Click:** Program name in the list (e.g., "After School Club")
   - **Expected:** Program detail page with calendar view

2. **Click Add Event**
   - **Click:** "Add Event" button
   - **Expected:** Event creation modal opens

3. **Fill in event details**
   - **Event Title:** Art Workshop
   - **Start Time:** 15:30
   - **End Time:** 17:00
   - **Room:** Preschool (select from dropdown)
   - **Expected:** Fields accept input

4. **Set recurrence pattern**
   - **Click:** "Recurrence" section to expand
   - **Pattern:** Weekly
   - **Days:** Check Monday, Wednesday, Friday
   - **End:** "End with program" (uses program end date)
   - **Expected:** Recurrence summary shows "Every Mon, Wed, Fri"

5. **Preview generated events**
   - **Look for:** "Preview" section showing list of generated dates
   - **Expected:** Dates listed for all Mon/Wed/Fri within program range
   - **Count:** Displays total number of events (e.g., "36 events")

6. **Save the event**
   - **Click:** "Save Event" button
   - **Expected:** Success toast "36 events created"
   - **Expected:** Calendar view shows event dots on relevant days

7. **Verify on calendar**
   - **Look for:** Colored dots on Monday, Wednesday, Friday
   - **Click:** Any date to see event details
   - **Expected:** "Art Workshop 15:30 - 17:00" displayed

**Screenshots:** [Screenshot: Event creation modal with recurrence options]

**Common Issues:**
- ❌ Problem: Recurrence generates too many or too few events
  ✅ Solution: Check the program start/end dates. Events only generate within the program date range.

- ❌ Problem: "Daily" recurrence includes weekends
  ✅ Solution: Use "Weekly" recurrence and check only weekday boxes (Mon-Fri) instead of "Daily".

---

### Scenario 3: Check for Event Conflicts

**When to use this:** You suspect two events overlap in time, room, or staff

**Gherkin Scenario:**
```gherkin
Given "Art Workshop" runs Mon/Wed/Fri 15:30-17:00 in Preschool
When I try to add "Music Class" on Wednesday 16:00-17:30 in Preschool
Then the conflict detection panel shows a warning
And it lists the overlapping event "Art Workshop - Wed 15:30-17:00"
And I can choose to proceed or adjust the time
```

**Steps:**

1. **Add a new event that may conflict**
   - **Click:** "Add Event" in the program
   - **Fill in:** "Music Class", Wednesday, 16:00 - 17:30, Preschool
   - **Expected:** Form accepts input

2. **Check conflict detection panel**
   - **Look for:** Yellow warning banner or "Conflicts Detected" section
   - **Expected:** Panel appears automatically after entering time and room
   - **Warning text:** "Overlaps with Art Workshop (Wed 15:30 - 17:00) in Preschool"

3. **Review conflict details**
   - **Overlap window:** 16:00 - 17:00 (60 minutes)
   - **Room:** Preschool (same room = hard conflict)
   - **Staff:** Any shared staff assignments shown
   - **Expected:** Clear description of what overlaps

4. **Resolve the conflict**
   - **Option A:** Change Music Class time to 17:00 - 18:30 (after Art Workshop)
   - **Option B:** Change Music Class room to ECC (different room)
   - **Option C:** Click "Save Anyway" to allow overlap (if rooms can share)
   - **Expected:** Conflict warning disappears after adjustment

5. **Save the adjusted event**
   - **Click:** "Save Event" after resolving
   - **Expected:** Success toast, no conflict warnings

**Screenshots:** [Screenshot: Conflict detection panel with overlapping events highlighted]

**Common Issues:**
- ❌ Problem: Conflict detection doesn't trigger
  ✅ Solution: Conflict detection requires both room and time to be filled in. Enter all fields before checking.

- ❌ Problem: False positive conflict (events in different rooms)
  ✅ Solution: Verify both events have the correct room selected. Same-room conflicts are hard conflicts; cross-room are soft warnings for shared staff only.

---

### Scenario 4: View Staff Availability and RSVP

**When to use this:** You need to assign staff to events and confirm their availability

**Gherkin Scenario:**
```gherkin
Given "Summer Camp" has an event on Monday June 1st
When I open the event and click "Assign Staff"
Then I see a list of eligible staff with availability indicators
And I can send RSVP requests to selected staff
And staff receive a notification to confirm or decline
```

**Steps:**

1. **Open the event**
   - **Click:** Event on program calendar (e.g., "Summer Camp - June 1st")
   - **Expected:** Event detail view opens

2. **Click Assign Staff**
   - **Click:** "Assign Staff" button
   - **Expected:** Staff assignment panel opens

3. **View eligible staff**
   - **Look for:** List of staff members with availability status:
     - **Green "Available":** No conflicting shifts or leave
     - **Amber "Partial":** Has a shift but gap available
     - **Red "Unavailable":** On leave or fully booked
     - **Gray "Not Qualified":** Missing required qualification
   - **Expected:** Staff sorted by availability (available first)

4. **Select staff to assign**
   - **Check:** Checkboxes next to available staff names
   - **Example:** Select Emma Murphy, Lisa O'Brien, Aoife O'Brien
   - **Expected:** Selected staff highlighted

5. **Send RSVP requests**
   - **Click:** "Send RSVP" button
   - **Expected:** Success toast "RSVP sent to 3 staff members"
   - **Staff receive:** Push notification or WhatsApp message (if configured)

6. **Track RSVP responses**
   - **Look for:** RSVP status column updates:
     - **Pending:** RSVP sent, awaiting response
     - **Confirmed:** Staff accepted
     - **Declined:** Staff declined (with optional reason)
   - **Expected:** Status updates as staff respond

7. **Finalize assignments**
   - **After RSVPs received:** Review confirmed staff
   - **If short-staffed:** Send additional RSVPs or assign from cover pool
   - **Click:** "Confirm Assignments" to lock in staff
   - **Expected:** Event shows confirmed staff list

**Screenshots:** [Screenshot: Staff assignment panel with RSVP statuses]

**Common Issues:**
- ❌ Problem: All staff show "Unavailable"
  ✅ Solution: Check event time against staff shift schedules. Staff must have availability during the event window. Also verify leave calendar.

- ❌ Problem: RSVP notification not received
  ✅ Solution: Verify push notifications or WhatsApp are enabled in Settings > Notifications. Check staff have valid contact details.

---

### Scenario 5: Run Event Check-In via PWA

**When to use this:** Event day has arrived and you need to track attendee presence

**Gherkin Scenario:**
```gherkin
Given "Art Workshop" is happening today at 15:30
When I open the Timebreez PWA on my phone
And I navigate to "Today's Events"
And I tap "Art Workshop"
And I tap "Start Check-In"
Then I see a list of expected attendees
And I can tap each name to mark them present
And the attendance count updates in real-time
```

**Steps:**

1. **Open Timebreez PWA on your device**
   - **Open:** Timebreez app or browser at `app.timebreez.com`
   - **Expected:** Dashboard loads

2. **Navigate to Today's Events**
   - **Tap:** "Events" or "Today" section
   - **Expected:** List of today's events appears

3. **Select the event**
   - **Tap:** "Art Workshop - 15:30"
   - **Expected:** Event detail screen opens

4. **Start Check-In mode**
   - **Tap:** "Start Check-In" button
   - **Expected:** Check-in screen shows attendee list

5. **Mark attendees present**
   - **Tap:** Each attendee name to toggle check-in
   - **Green checkmark:** Present
   - **Gray dash:** Not yet arrived
   - **Red X:** Absent (tap twice)
   - **Expected:** Counter updates (e.g., "8/12 checked in")

6. **View real-time count**
   - **Look for:** Progress bar or counter at top
   - **Example:** "8 of 12 checked in (67%)"
   - **Expected:** Updates as you check in attendees

7. **End Check-In**
   - **Tap:** "End Check-In" when event starts or all present
   - **Expected:** Check-in summary saved
   - **Late arrivals:** Can still be marked after end

**Screenshots:** [Screenshot: PWA check-in screen with attendee list]

**Common Issues:**
- ❌ Problem: "No events today" even though events are scheduled
  ✅ Solution: Verify the event recurrence includes today's date. Check you are viewing the correct program.

- ❌ Problem: Check-in button is disabled
  ✅ Solution: Check-in only activates within 30 minutes of event start time. Wait until the check-in window opens.

---

### Scenario 6: Export Program Report as CSV

**When to use this:** You need attendance data, staff hours, or program summary for reporting

**Gherkin Scenario:**
```gherkin
Given "Summer Camp 2026" has completed 4 weeks of events
When I navigate to Programs > Summer Camp 2026
And I click "Reports"
And I select "Attendance Summary" report
And I click "Export CSV"
Then a CSV file downloads with event dates, attendee counts, staff assigned, and hours
```

**Steps:**

1. **Navigate to the program**
   - **Click:** Programs > Summer Camp 2026
   - **Expected:** Program detail page loads

2. **Open Reports tab**
   - **Click:** "Reports" tab (next to Calendar, Events, Staff tabs)
   - **Expected:** Report options displayed

3. **Select report type**
   - **Options:**
     - **Attendance Summary:** Event-by-event attendance counts
     - **Staff Hours:** Total hours per staff member across all events
     - **Program Overview:** High-level metrics (total events, average attendance, completion rate)
   - **Click:** "Attendance Summary"
   - **Expected:** Report preview loads

4. **Set date range** (optional)
   - **Default:** Full program date range
   - **Custom:** Adjust start/end dates for partial report
   - **Expected:** Report data filters to selected range

5. **Preview the report**
   - **Look for:** Table with columns:
     - **Date:** Event date
     - **Event:** Event title
     - **Expected:** Registered attendee count
     - **Present:** Checked-in count
     - **Staff:** Assigned staff count
     - **Rate:** Attendance percentage
   - **Expected:** Data matches your records

6. **Export as CSV**
   - **Click:** "Export CSV" button
   - **Expected:** CSV file downloads to your device
   - **Filename:** `summer-camp-2026-attendance-2026-07-01.csv`

7. **Verify CSV contents**
   - **Open:** CSV in Excel, Google Sheets, or similar
   - **Expected:** All report columns present with correct data
   - **Use for:** Board reports, Tusla compliance, internal review

**Screenshots:** [Screenshot: Program report with Export CSV button]

**Common Issues:**
- ❌ Problem: Report shows "No data" even though events ran
  ✅ Solution: Verify check-in was completed for events (Scenario 5). Reports only include events with attendance data.

- ❌ Problem: CSV export fails or downloads empty file
  ✅ Solution: Check your browser allows downloads from Timebreez. Try a different browser. If report preview shows data but CSV is empty, report as a bug.

---

## Troubleshooting

### Issue: Programs page is empty
**Symptoms:** "No programs found" message
**Cause:** No programs created yet, or permissions issue
**Solution:**
1. Click "New Program" to create your first program
2. Verify you have Manager or Admin role
3. Check organization context is correct (not viewing wrong org)

---

### Issue: Recurring events not generating correctly
**Symptoms:** Missing dates or extra events in the series
**Cause:** Recurrence pattern or date range mismatch
**Solution:**
1. Edit the event and check recurrence settings
2. Verify program start/end dates encompass all expected dates
3. Check "exclude dates" list for accidentally skipped days
4. Delete and recreate the event series if pattern is wrong

---

### Issue: Staff RSVP stuck on "Pending"
**Symptoms:** Staff say they responded but status still shows Pending
**Cause:** Notification delivery failure or response not recorded
**Solution:**
1. Ask staff to check their Timebreez app for the RSVP notification
2. Staff can RSVP directly from the Events section in the app
3. Manager can manually update RSVP status from the event detail page
4. Check notification settings in Settings > Notifications

---

### Issue: Check-in not saving
**Symptoms:** Checked in attendees but data lost on refresh
**Cause:** Offline mode without sync, or network issue
**Solution:**
1. Verify internet connection on your device
2. Check for "Offline" indicator in PWA header
3. If offline, check-in data queues locally and syncs when reconnected
4. Force sync by pulling down to refresh once back online

---

## Related Guides
- [Session Scheduling (ECCE/AIMS)](./02-session-scheduling-ecce-aims.md)
- [Control Desk Operations](./05-control-desk-operations.md)
- [Credentials & Qualifications](./07-credentials-qualifications.md)
- [Troubleshooting Guide](./08-troubleshooting.md)

## Need More Help?
- **Timebreez Support:** support@timebreez.com
- **Demo mode:** www.timebreez.com/login (explore programs in the demo org)
- **Book a call:** Schedule a 15-min walkthrough of program management
