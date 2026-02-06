# Compliance Trail & Room Audit Report - Tusla Inspection Evidence

## Who This Is For
**Childcare Managers and Compliance Officers** who need to produce audit evidence for Tusla inspections, track room-level staffing events, and export compliance reports.

## What You'll Learn
- What the compliance trail is (append-only audit log)
- Understanding event types: enter, exit, break, cover
- Viewing per-room timeline of staffing events
- Reading compliance summary cards with percentages
- Exporting CSV reports for inspector evidence

## Prerequisites
- Manager or Admin role in Timebreez
- Rooms configured with capacity and ratios
- Attendance tracking active (Paxton, NFC, manual, or kiosk)
- Staff shifts and dispatches occurring (data to audit)

---

## Quick Start (TL;DR)

1. Go to **Compliance > Audit Trail** in sidebar
2. Select a **room** and **date range**
3. View the **per-room timeline** of enter/exit/break/cover events
4. Check **Compliance Summary** cards for ratio percentages
5. Click **"Export CSV"** to generate evidence for Tusla inspectors

---

## Understanding the Compliance Trail

### What is the Compliance Trail?

The **compliance trail** is an **append-only audit log** that records every staffing event in every room. It is designed to provide irrefutable evidence for Tusla Early Years inspections.

**Key properties:**
- **Append-only:** Events cannot be edited or deleted (immutable audit trail)
- **Timestamped:** Every event has a precise timestamp
- **Source-tagged:** Each event records how it was captured (NFC, Paxton, manual, etc.)
- **Per-room:** Events are scoped to specific rooms
- **Per-employee:** Events are linked to individual staff members

**Why it matters:**
- Tusla inspectors require evidence that rooms were properly staffed
- The compliance trail proves who was in which room, when, and why
- Export-ready CSV reports can be handed directly to inspectors
- Historical data supports trend analysis and pattern identification

### Event Types

Every event in the compliance trail has one of four types:

| Event Type | Code | Description | Example |
|------------|------|-------------|---------|
| **Enter** | `room_enter` | Staff member enters a room | Emma enters Baby Room at 09:00 |
| **Exit** | `room_exit` | Staff member leaves a room | Emma exits Baby Room at 17:00 |
| **Break** | `break_start` / `break_end` | Staff member starts or ends a break | Emma starts lunch break at 12:00, ends at 12:30 |
| **Cover** | `cover_start` / `cover_end` | Cover staff deployed to or recalled from a room | Lisa covers Baby Room at 12:00, ends at 12:30 |

**Additional metadata per event:**
- **Employee name and ID**
- **Room name and ID**
- **Timestamp** (ISO 8601 format)
- **Source** (nfc, paxton, manual, kiosk, system)
- **Triggered by** (employee scan, manager dispatch, system auto-close)
- **Notes** (optional, added by manager)

### How Events Build the Timeline

```
09:00  room_enter   Emma Murphy      Baby Room    source: paxton
09:02  room_enter   Lisa O'Brien     Baby Room    source: nfc
09:05  room_enter   Aoife O'Brien    Baby Room    source: nfc
12:00  break_start  Emma Murphy      Baby Room    source: system
12:00  cover_start  Sarah Doyle      Baby Room    source: dispatch (break coverage)
12:30  break_end    Emma Murphy      Baby Room    source: system
12:30  cover_end    Sarah Doyle      Baby Room    source: dispatch
17:00  room_exit    Emma Murphy      Baby Room    source: paxton
17:00  room_exit    Lisa O'Brien     Baby Room    source: paxton
17:02  room_exit    Aoife O'Brien    Baby Room    source: nfc
```

At any point, the **effective staff count** = entered - exited - on_break + covering.

---

## Step-by-Step Guides

### Scenario 1: View Room Audit Trail

**When to use this:** Review staffing history for a specific room on a specific date

**Gherkin Scenario:**
```gherkin
Given I am logged in as a manager
When I navigate to Compliance > Audit Trail
And I select room "Baby Room" and date "2026-02-06"
Then I see a chronological timeline of all staffing events
And each event shows time, employee, event type, and source
And the timeline highlights periods where the room was below required ratio
```

**Steps:**

1. **Navigate to Compliance**
   - **Click:** "Compliance" in the sidebar
   - **Expected:** Compliance section loads

2. **Open Audit Trail**
   - **Click:** "Audit Trail" tab
   - **Expected:** Audit trail page with filter controls

3. **Select filters**
   - **Room:** Select "Baby Room" from dropdown
   - **Date:** Select "2026-02-06" from date picker (or date range)
   - **Click:** "Apply" or filters auto-apply
   - **Expected:** Timeline populates with events

4. **Read the timeline**
   - **Layout:** Vertical timeline, newest events at top (or chronological toggle)
   - **Each event shows:**
     - **Time:** 09:00
     - **Event:** room_enter
     - **Employee:** Emma Murphy
     - **Source:** paxton (icon or badge)
     - **Notes:** (if any)
   - **Expected:** All events for Baby Room on Feb 6 displayed

5. **Identify compliance gaps**
   - **Look for:** Red-highlighted periods on the timeline
   - **Red band:** Time period where effective staff < required
   - **Example:** 12:00-12:05 (Emma on break, cover not yet arrived - 5 min gap)
   - **Hover:** Shows details "Below ratio: 2 present, 3 required"

6. **View event details**
   - **Click:** Any event row to expand details
   - **Shows:**
     - Full employee profile link
     - Source device details
     - Triggered by (who initiated)
     - Notes and context
   - **Expected:** Detailed event information available

7. **Navigate between rooms**
   - **Change:** Room dropdown to view another room's trail
   - **Expected:** Timeline refreshes for selected room

**Screenshots:** [Screenshot: Room audit trail timeline with events and compliance gap highlighted]

**Common Issues:**
- ❌ Problem: Timeline shows "No events found"
  ✅ Solution: Verify attendance tracking is active for the selected date. Check that the room has had staff badge in. Try a different date range.

- ❌ Problem: Events appear out of order
  ✅ Solution: Toggle sort order (chronological vs reverse-chronological). Events are sorted by timestamp. If timestamps seem wrong, check device clock accuracy for NFC/kiosk sources.

---

### Scenario 2: Check Compliance Summary Cards

**When to use this:** Quick overview of compliance metrics for a room or the entire facility

**Gherkin Scenario:**
```gherkin
Given I am viewing the Compliance dashboard
When I look at the summary cards for today
Then I see:
  - "Overall Compliance: 94.2%"
  - "Baby Room: 91.7% (2 gaps totaling 25 min)"
  - "Toddlers: 100% (no gaps)"
  - "Preschool: 88.3% (1 gap during ECCE session)"
And rooms below 90% are highlighted in amber/red
```

**Steps:**

1. **Navigate to Compliance dashboard**
   - **Click:** "Compliance" in sidebar
   - **Click:** "Summary" or "Dashboard" tab
   - **Expected:** Summary cards displayed

2. **View overall compliance card**
   - **Look for:** Large card at top showing:
     - **Percentage:** "94.2% compliant"
     - **Time period:** Today (or selected date range)
     - **Meaning:** Percentage of operational minutes where all rooms met required ratios
   - **Expected:** Percentage prominently displayed

3. **View per-room cards**
   - **Look for:** Card for each room showing:
     - **Room name:** Baby Room
     - **Compliance %:** 91.7%
     - **Gap count:** 2 gaps
     - **Gap duration:** 25 minutes total
     - **Status color:**
       - GREEN (95%+): Excellent compliance
       - AMBER (85-94%): Acceptable but needs attention
       - RED (<85%): Below standard, action required
   - **Expected:** All rooms displayed with metrics

4. **Understand the percentage calculation**
   - **Formula:** `(operational_minutes - gap_minutes) / operational_minutes * 100`
   - **Operational minutes:** Total minutes the room was in session (e.g., 09:00-17:00 = 480 min)
   - **Gap minutes:** Total minutes where present < required
   - **Example:** 480 min total, 25 min gaps → (480-25)/480 = 94.8%

5. **Drill into a room**
   - **Click:** Room card (e.g., Baby Room: 91.7%)
   - **Expected:** Navigates to that room's audit trail with gaps highlighted

6. **Compare across date ranges**
   - **Change:** Date range to "This Week" or "This Month"
   - **Expected:** Summary cards update with aggregated metrics
   - **Trend:** Look for improving or declining compliance percentages

**Screenshots:** [Screenshot: Compliance summary cards with percentages and room-level breakdown]

**Common Issues:**
- ❌ Problem: Compliance shows 0% even though staff were present
  ✅ Solution: Verify attendance events exist for the date. If no events are recorded, compliance cannot be calculated. Check attendance source configuration.

- ❌ Problem: Compliance percentage seems too low
  ✅ Solution: Check for common causes: transition gaps (staff moving between rooms), break gaps (cover not arriving on time), early morning before all staff arrive. Short gaps during transitions are normal.

---

### Scenario 3: Export CSV for Tusla Inspector

**When to use this:** Tusla inspector is on-site or has requested compliance evidence

**Gherkin Scenario:**
```gherkin
Given a Tusla inspector requests compliance evidence for the past 30 days
When I navigate to Compliance > Audit Trail
And I select date range "2026-01-06 to 2026-02-06"
And I select "All Rooms"
And I click "Export CSV"
Then a CSV file downloads containing all events across all rooms
And the CSV includes: date, time, room, employee, event_type, source, staff_count, required_count
And the file is ready to hand to the inspector
```

**Steps:**

1. **Navigate to Audit Trail**
   - **Click:** Compliance > Audit Trail
   - **Expected:** Audit trail page loads

2. **Set export filters**
   - **Room:** Select "All Rooms" (or specific room if requested)
   - **Date Range:** Set start date and end date
     - **Example:** 2026-01-06 to 2026-02-06 (30 days)
   - **Expected:** Filters applied, timeline preview shows data

3. **Click Export CSV**
   - **Click:** "Export CSV" button (usually top-right of the page)
   - **Expected:** Loading spinner appears briefly
   - **Expected:** CSV file downloads to your device

4. **Verify CSV filename**
   - **Format:** `compliance-trail-all-rooms-2026-01-06-to-2026-02-06.csv`
   - **Expected:** Descriptive filename with date range

5. **Review CSV contents**
   - **Open:** CSV in Excel, Google Sheets, or text editor
   - **Columns:**
     - **date:** 2026-02-06
     - **time:** 09:00:00
     - **room:** Baby Room
     - **employee:** Emma Murphy
     - **employee_id:** (UUID)
     - **event_type:** room_enter
     - **source:** paxton
     - **staff_count:** 3 (effective count at this moment)
     - **required_count:** 3
     - **compliant:** true
     - **notes:** (any manager notes)
   - **Expected:** All columns present with accurate data

6. **Present to inspector**
   - **Option A:** Email the CSV file
   - **Option B:** Print the CSV (format in Excel first)
   - **Option C:** Show the live dashboard on screen
   - **Expected:** Inspector has the evidence they need

7. **Export compliance summary** (optional companion report)
   - **Click:** Compliance > Summary > "Export Summary PDF"
   - **Contents:** Room-by-room compliance percentages, gap analysis, trend charts
   - **Purpose:** Executive summary to accompany the detailed CSV

**Screenshots:** [Screenshot: Export CSV button and downloaded file preview]

**Common Issues:**
- ❌ Problem: CSV export takes too long or times out
  ✅ Solution: Reduce the date range (try 7 days instead of 30). Large date ranges with many rooms generate substantial data. Export in chunks if needed.

- ❌ Problem: CSV is empty or has only headers
  ✅ Solution: Verify events exist for the selected date range and rooms. If no attendance data was recorded, the export will be empty. Check attendance source configuration.

- ❌ Problem: Inspector wants a specific format
  ✅ Solution: The CSV contains raw data that can be reformatted in Excel. Use pivot tables or filters to create the specific view the inspector needs. Timebreez provides the data; presentation can be customized.

---

### Scenario 4: Understand Event Types in Context

**When to use this:** You see events in the trail and need to understand what happened

**Gherkin Scenario:**
```gherkin
Given I am reading the Baby Room audit trail for today
When I see the sequence:
  09:00  room_enter   Emma Murphy    (paxton)
  12:00  break_start  Emma Murphy    (system)
  12:00  cover_start  Sarah Doyle    (dispatch)
  12:30  cover_end    Sarah Doyle    (dispatch)
  12:30  break_end    Emma Murphy    (system)
  17:00  room_exit    Emma Murphy    (paxton)
Then I understand:
  - Emma worked 09:00-17:00 in Baby Room
  - She took a 30-minute lunch break at 12:00
  - Sarah covered Baby Room during Emma's break
  - Room was continuously staffed (no compliance gap)
```

**Steps:**

1. **Read event pairs**
   - **Enter/Exit pair:** Staff's total time in the room
     - `room_enter` at 09:00 + `room_exit` at 17:00 = 8 hours in room
   - **Break pair:** Staff's time away from the room
     - `break_start` at 12:00 + `break_end` at 12:30 = 30 min break
   - **Cover pair:** Cover staff's time deployed to the room
     - `cover_start` at 12:00 + `cover_end` at 12:30 = 30 min coverage

2. **Calculate effective staff at any moment**
   - **At 11:59 (before break):**
     - Emma (entered, not on break) = present
     - Lisa (entered, not on break) = present
     - Aoife (entered, not on break) = present
     - **Effective:** 3 staff, **Required:** 3 → Compliant
   - **At 12:05 (during break):**
     - Emma (on break) = absent from count
     - Lisa (present) = present
     - Aoife (present) = present
     - Sarah (covering) = present
     - **Effective:** 3 staff, **Required:** 3 → Compliant

3. **Identify gap events**
   - **Gap:** When `break_start` has no matching `cover_start` at the same time
   - **Example gap:** Emma starts break at 12:00, Sarah doesn't arrive until 12:05
   - **Result:** 5 minutes where effective = 2, required = 3
   - **Trail shows:** Red-highlighted 5-minute window

4. **Understand source labels**
   - **paxton:** Automatic from Paxton Net2 badge reader
   - **nfc:** Staff scanned NFC tag
   - **manual:** Manager entered event manually
   - **kiosk:** Staff used shared kiosk tablet
   - **system:** Auto-generated (break schedules, end-of-day auto-close)
   - **dispatch:** Generated by cover staff dispatch action

5. **Use for investigation**
   - **Question:** "Was Baby Room compliant during ECCE session yesterday?"
   - **Action:** Filter trail by room + date, check 09:30-12:30 window
   - **Answer:** Read effective staff count during session hours
   - **Expected:** Clear evidence for compliance verification

**Screenshots:** [Screenshot: Event sequence showing enter, break, cover, exit with annotations]

**Common Issues:**
- ❌ Problem: Missing exit events (staff entered but no exit recorded)
  ✅ Solution: Staff may have left without scanning. System auto-closes open sessions at shift end (generates `room_exit` with source "system"). Check for "system" source exits.

- ❌ Problem: Break events don't have matching cover events
  ✅ Solution: This indicates the break was uncovered. The compliance trail correctly shows a gap during this period. Review break coverage planning to prevent future gaps.

---

## Troubleshooting

### Issue: Compliance trail missing events
**Symptoms:** Known attendance (e.g., Paxton badge) not appearing in trail
**Cause:** Integration delay, data sync issue, or source not enabled
**Solution:**
1. Check Settings > Attendance to verify the source is enabled
2. For Paxton: check integration status (Settings > Integrations > Paxton)
3. Allow 1-2 minutes for events to propagate from source to trail
4. For manual entries: verify the manager saved the event (not just opened the form)
5. Check date filter matches the expected date

---

### Issue: Compliance percentage incorrect
**Symptoms:** Manual calculation of gaps differs from displayed percentage
**Cause:** Operational hours definition or gap calculation difference
**Solution:**
1. Verify "operational hours" setting (e.g., 08:00-18:00 vs 09:00-17:00)
2. Gaps outside operational hours are excluded from calculation
3. Transition gaps under 5 minutes may be excluded (configurable threshold)
4. Check Settings > Compliance > Gap Threshold to adjust minimum gap duration
5. Recalculate manually using the formula in Scenario 2

---

### Issue: CSV export encoding issues
**Symptoms:** Special characters (e.g., Irish names like O'Brien) appear garbled
**Cause:** UTF-8 encoding not recognized by spreadsheet application
**Solution:**
1. When opening in Excel: use Data > Import From CSV and select "UTF-8" encoding
2. Google Sheets handles UTF-8 automatically
3. If using text editor: ensure it's set to UTF-8 encoding
4. Re-export if file was corrupted during download

---

### Issue: Inspector wants real-time view, not just CSV
**Symptoms:** Tusla inspector wants to see live compliance data during visit
**Cause:** Standard request during on-site inspections
**Solution:**
1. Open Compliance > Summary on a laptop or tablet
2. Show the per-room compliance cards with current percentages
3. Click into specific rooms to show the live audit trail
4. Offer to export CSV during the visit as supplementary evidence
5. Who's Where dashboard shows real-time room presence for immediate verification

---

## Related Guides
- [Control Desk Operations](./05-control-desk-operations.md)
- [Attendance & Presence](./09-attendance-presence.md)
- [Break Coverage Calculator](./10-break-coverage-calculator.md)
- [Credentials & Qualifications](./07-credentials-qualifications.md)
- [Troubleshooting Guide](./08-troubleshooting.md)

## Need More Help?
- **Timebreez Support:** support@timebreez.com
- **Demo mode:** www.timebreez.com/login (explore compliance trail in the demo org)
- **Tusla guidance:** www.tusla.ie (Early Years Inspectorate requirements)
- **Book a call:** Schedule a 15-min walkthrough of compliance reporting
