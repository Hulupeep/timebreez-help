# Attendance & Presence - Multi-Source Tracking

## Who This Is For
**Childcare and Hospitality Managers** who need to track staff attendance using multiple sources including Paxton Net2, NFC tags, manual entry, geofence, and kiosk mode.

## What You'll Learn
- Configuring multiple attendance sources (Paxton, NFC, manual, geofence)
- NFC tag scanning for tap-to-clock-in/out
- Room entry/exit tracking with NFC
- Using the real-time "Who's Where" compliance dashboard
- Setting up kiosk mode for tablet clock-in
- Handling offline scanning and sync queues

## Prerequisites
- Admin role in Timebreez
- Paxton Net2 integration configured (for Paxton source)
- NFC-capable device (for NFC scanning)
- Staff profiles with shift assignments
- Rooms configured with capacity and ratios

---

## Quick Start (TL;DR)

1. Go to **Settings > Attendance** and enable your sources (Paxton, NFC, Manual, Geofence)
2. Assign **NFC tags** to employees (Settings > NFC Tags)
3. Staff **tap phone to NFC tag** at facility entrance to clock in
4. Staff **tap NFC tag at room door** to register room entry
5. View **Who's Where** dashboard for real-time compliance status
6. Use **Kiosk Mode** on a shared tablet for manual clock-in
7. Offline scans **queue locally** and sync when reconnected

---

## Understanding Attendance Sources

### Multi-Source Architecture

Timebreez supports **multiple attendance sources** simultaneously. Each source feeds into the same unified attendance record:

| Source | How It Works | Best For |
|--------|-------------|----------|
| **Paxton Net2** | Automatic badge reader at doors | Facilities with existing access control |
| **NFC Tag** | Tap phone to NFC sticker/card | Low-cost, flexible clock-in |
| **Manual Entry** | Manager marks attendance in app | Backup, corrections, late entries |
| **Geofence** | GPS checks if staff is on-site | Mobile workers, multiple sites |
| **Kiosk** | Shared tablet at entrance | Single device for all staff |

**Priority order:** When multiple sources report for the same employee, the earliest clock-in and latest clock-out are used.

### How Attendance Feeds the System

```
Attendance Event → Unified Record → Control Desk (present count)
                                  → Payroll (hours worked)
                                  → Compliance Trail (audit log)
                                  → Who's Where (room presence)
```

Every attendance event includes:
- **Employee ID:** Who
- **Timestamp:** When
- **Event Type:** clock_in, clock_out, room_enter, room_exit
- **Source:** paxton, nfc, manual, geofence, kiosk
- **Location:** Facility entrance, room name, or GPS coordinates

---

## Step-by-Step Guides

### Scenario 1: Configure Attendance Sources

**When to use this:** Initial setup or adding a new attendance source to your facility

**Gherkin Scenario:**
```gherkin
Given I am logged in as an admin
When I navigate to Settings > Attendance
Then I see a list of attendance sources with toggle switches
When I enable "NFC Tag" and "Manual Entry"
And I click "Save"
Then those sources are active
And staff can use NFC tags and manual entry to clock in
```

**Steps:**

1. **Navigate to Settings**
   - **Click:** "Settings" in the sidebar
   - **Expected:** Settings submenu expands

2. **Open Attendance settings**
   - **Click:** "Attendance" submenu item
   - **Expected:** Attendance configuration page loads

3. **View available sources**
   - **Look for:** List of attendance sources with toggle switches:
     - **Paxton Net2:** Toggle ON/OFF
     - **NFC Tag:** Toggle ON/OFF
     - **Manual Entry:** Toggle ON/OFF
     - **Geofence:** Toggle ON/OFF
     - **Kiosk Mode:** Toggle ON/OFF
   - **Expected:** All sources visible

4. **Enable desired sources**
   - **Toggle ON:** NFC Tag
   - **Toggle ON:** Manual Entry
   - **Leave OFF:** Paxton Net2 (if not installed)
   - **Expected:** Toggles change to blue/active state

5. **Configure source-specific settings** (if applicable)
   - **NFC Tag settings:**
     - Tag format: NTAG213 / NTAG215
     - Read range: Standard
   - **Geofence settings:**
     - Facility coordinates: (auto-detected or manual entry)
     - Radius: 100 meters
   - **Expected:** Sub-settings appear when source is enabled

6. **Save configuration**
   - **Click:** "Save" button
   - **Expected:** Success toast "Attendance settings updated"

7. **Verify sources are active**
   - **Look for:** Active badge next to enabled sources
   - **Test:** Try a clock-in using the enabled source (see following scenarios)

**Screenshots:** [Screenshot: Attendance settings with source toggles]

**Common Issues:**
- ❌ Problem: Paxton toggle is grayed out
  ✅ Solution: Paxton Net2 integration must be configured separately. Go to Settings > Integrations > Paxton and enter your server details first.

- ❌ Problem: Geofence requires location permission
  ✅ Solution: Staff must grant location permission on their devices. The app prompts for permission on first use. Denied permission means geofence cannot work.

---

### Scenario 2: Scan NFC Tag to Clock In

**When to use this:** Staff arrives at the facility and needs to register attendance

**Gherkin Scenario:**
```gherkin
Given NFC attendance source is enabled
And Emma Murphy has an NFC tag assigned (tag ID "NFC-001")
When Emma holds her phone near the NFC tag at the entrance
Then her phone reads the tag
And the Timebreez PWA registers a clock-in event
And a success notification shows "Clocked in at 08:58"
And Control Desk present count updates
```

**Steps:**

1. **Ensure NFC tag is assigned to employee**
   - **Admin:** Go to Settings > NFC Tags
   - **Assign:** Tag "NFC-001" to Emma Murphy
   - **Expected:** Tag mapped to employee in system

2. **Staff approaches facility entrance**
   - **Location:** NFC tag sticker is placed at the entrance door or reception
   - **Device:** Staff has Timebreez PWA open on phone (or phone with NFC enabled)

3. **Tap phone to NFC tag**
   - **Action:** Hold phone within 2-4 cm of the NFC tag sticker
   - **Expected:** Phone vibrates or beeps
   - **Expected:** Timebreez PWA opens (if not already open) with clock-in confirmation

4. **Confirm clock-in**
   - **Look for:** Notification or toast message:
     - "Emma Murphy - Clocked in at 08:58"
     - Green checkmark animation
   - **Expected:** Clock-in recorded successfully

5. **Verify in system**
   - **Control Desk:** Emma's present count updates on her assigned room tile
   - **Who's Where:** Emma appears in the present staff list
   - **Attendance log:** New entry with source "nfc", type "clock_in"

6. **Clock out at end of day** (same process)
   - **Tap:** Phone to NFC tag when leaving
   - **Expected:** "Clocked out at 17:02" notification
   - **Expected:** Present count decreases

**Screenshots:** [Screenshot: Phone held near NFC tag with clock-in confirmation]

**Common Issues:**
- ❌ Problem: Phone doesn't read the NFC tag
  ✅ Solution:
    1. Ensure NFC is enabled in phone settings (Settings > NFC on Android, always-on for iPhone)
    2. Hold phone closer (within 2 cm) and keep still for 1-2 seconds
    3. Remove phone case if it is thick or metallic
    4. Verify the NFC tag is not damaged or demagnetized

- ❌ Problem: Tag reads but clock-in fails
  ✅ Solution: Verify the tag is assigned to the correct employee in Settings > NFC Tags. Check internet connectivity. If offline, the event queues locally (see Scenario 6).

---

### Scenario 3: Enter Room via NFC

**When to use this:** Staff moves from the entrance to a specific room and needs to register room presence

**Gherkin Scenario:**
```gherkin
Given Emma Murphy has clocked in at the facility entrance
When she walks to Baby Room
And taps her phone on the Baby Room NFC tag
Then a "room_enter" event is recorded for Baby Room
And the Who's Where dashboard shows Emma in Baby Room
And Baby Room's present count increases
```

**Steps:**

1. **Ensure room NFC tags are installed**
   - **Admin:** Place NFC tag stickers at each room entrance
   - **Map:** In Settings > NFC Tags > Room Tags, assign tag IDs to rooms
     - Tag "NFC-ROOM-001" = Baby Room
     - Tag "NFC-ROOM-002" = Baby Steps
     - etc.
   - **Expected:** Each room has a mapped NFC tag

2. **Staff approaches room door**
   - **Context:** Emma has already clocked in at the facility entrance
   - **Location:** Baby Room door with NFC tag sticker

3. **Tap phone to room NFC tag**
   - **Action:** Hold phone near the room's NFC tag
   - **Expected:** Phone vibrates/beeps
   - **Notification:** "Entered Baby Room at 09:02"

4. **Room entry recorded**
   - **Event type:** room_enter
   - **Room:** Baby Room
   - **Employee:** Emma Murphy
   - **Timestamp:** 09:02
   - **Source:** nfc

5. **Verify on Who's Where dashboard**
   - **Navigate:** Control Desk > Who's Where panel
   - **Look for:** Emma Murphy listed under "Baby Room"
   - **Expected:** Emma's current location shows Baby Room

6. **Exit room** (when leaving for break, moving to another room, etc.)
   - **Tap:** Phone to Baby Room NFC tag again (or new room's tag)
   - **Expected:** "Exited Baby Room at 12:00" (if same tag)
   - **Expected:** "Entered Toddlers at 12:02" (if different room tag)

**Screenshots:** [Screenshot: Room NFC tag with phone tap and room entry confirmation]

**Common Issues:**
- ❌ Problem: Room entry registers but room count doesn't update
  ✅ Solution: Refresh Control Desk. Room presence count pulls from the latest room_enter/room_exit events. If stale, force refresh.

- ❌ Problem: Staff forgot to tap room tag
  ✅ Solution: Use manual entry (manager can add room_enter event from dashboard) or remind staff. NFC adoption improves with habit.

---

### Scenario 4: View Who's Where Dashboard

**When to use this:** Real-time monitoring of which staff are in which rooms for compliance

**Gherkin Scenario:**
```gherkin
Given it is 10:00 AM on a weekday
And 8 staff have clocked in
When I navigate to Control Desk > Who's Where
Then I see a real-time map of staff locations:
  - Baby Room: Emma Murphy, Lisa O'Brien
  - Toddlers: Aoife O'Brien, Ciara Walsh
  - Preschool: Niamh Kelly, Sinead Ryan
  - Cover Pool: Sarah Doyle (available)
  - Unknown: Roisin O'Neill (clocked in, no room scan)
And each room shows compliance status (ratio check)
```

**Steps:**

1. **Navigate to Who's Where**
   - **Click:** "Control Desk" in sidebar
   - **Look for:** "Who's Where" tab or panel
   - **Expected:** Real-time location dashboard loads

2. **View room breakdown**
   - **Look for:** Room cards showing:
     - **Room name:** Baby Room
     - **Staff present:** Emma Murphy, Lisa O'Brien
     - **Count:** 2 staff
     - **Required:** 3 (based on child count and ratio)
     - **Status:** AMBER (2 of 3 required present)
   - **Expected:** All rooms displayed with staff lists

3. **Check compliance indicators**
   - **Green room card:** Present >= required (compliant)
   - **Amber room card:** Present = required - 1 (close to minimum)
   - **Red room card:** Present < required - 1 (non-compliant)
   - **Expected:** Colors match actual staffing levels

4. **View unassigned staff**
   - **Look for:** "Cover Pool" or "Unassigned" section
   - **Shows:** Staff who clocked in but are not in any room
   - **Example:** Sarah Doyle (cover staff, available for dispatch)
   - **Expected:** Unassigned staff visible for deployment

5. **Check last-seen timestamps**
   - **Look for:** "Last scan" time next to each staff member
   - **Example:** "Emma Murphy - Baby Room (last scan: 09:02)"
   - **Purpose:** Verify data freshness, identify stale entries
   - **Expected:** Timestamps recent (within last hour)

6. **Use real-time updates**
   - **Auto-refresh:** Dashboard updates every 30-60 seconds
   - **Manual refresh:** Click refresh button for immediate update
   - **Expected:** Staff movements reflected within refresh interval

**Screenshots:** [Screenshot: Who's Where dashboard with room cards and staff lists]

**Common Issues:**
- ❌ Problem: Staff shows in wrong room
  ✅ Solution: Staff may have entered a new room without scanning out of the previous one. The system uses the latest room_enter event. Ask staff to scan the correct room tag.

- ❌ Problem: "Unknown" location for clocked-in staff
  ✅ Solution: Staff clocked in at facility entrance but has not scanned any room NFC tag. This is normal for cover staff or staff in transit. Ask them to scan their room tag.

---

### Scenario 5: Use Kiosk Mode for Tablet Clock-In

**When to use this:** You want a shared tablet at the entrance for all staff to clock in/out

**Gherkin Scenario:**
```gherkin
Given I have a tablet mounted at the facility entrance
When I enable Kiosk Mode in Settings > Attendance
And I set the tablet to kiosk URL
Then staff see a clock-in screen with their names
When Emma taps her name and enters her PIN
Then she is clocked in
And the tablet returns to the staff list for the next person
```

**Steps:**

1. **Enable Kiosk Mode**
   - **Navigate:** Settings > Attendance
   - **Toggle ON:** Kiosk Mode
   - **Expected:** Kiosk configuration options appear

2. **Configure Kiosk settings**
   - **PIN required:** Yes (recommended for security)
   - **Auto-logout timeout:** 30 seconds (returns to staff list after inactivity)
   - **Show clock:** Yes (display current time prominently)
   - **Photo capture:** Optional (take photo on clock-in for verification)
   - **Expected:** Settings saved

3. **Set up the tablet**
   - **Open:** Browser on the tablet
   - **Navigate:** `app.timebreez.com/kiosk` (or dedicated kiosk URL)
   - **Enable:** Guided Access (iOS) or Screen Pinning (Android) to lock to this app
   - **Mount:** Tablet at facility entrance using a wall mount or stand
   - **Expected:** Kiosk clock-in screen displays

4. **Staff clocks in via kiosk**
   - **View:** Staff list showing all scheduled employees for today
   - **Tap:** Emma Murphy's name
   - **Enter:** 4-digit PIN (e.g., 1234)
   - **Expected:** "Emma Murphy clocked in at 08:58" confirmation
   - **Screen:** Returns to staff list after 5 seconds

5. **Staff clocks out via kiosk**
   - **Tap:** Emma Murphy's name (now shows "Clock Out" button)
   - **Enter:** PIN
   - **Expected:** "Emma Murphy clocked out at 17:03" confirmation

6. **Verify kiosk events**
   - **Source:** Events recorded with source "kiosk"
   - **Control Desk:** Present counts update as staff clock in/out
   - **Expected:** Same behavior as NFC or Paxton events

**Screenshots:** [Screenshot: Kiosk mode on tablet showing staff list and clock-in confirmation]

**Common Issues:**
- ❌ Problem: Kiosk screen goes to sleep
  ✅ Solution: Disable screen timeout on the tablet (Settings > Display > Screen timeout > Never). Keep the tablet plugged in to a power source.

- ❌ Problem: Staff forgot their PIN
  ✅ Solution: Admin can reset PINs in Employees > [Name] > Security > Reset Kiosk PIN. Default PIN can be set in Kiosk settings.

- ❌ Problem: Multiple staff trying to clock in at same time
  ✅ Solution: Kiosk handles one person at a time. The 30-second auto-timeout keeps the queue moving. Consider adding a second kiosk tablet if queues are long.

---

### Scenario 6: Handle Offline Scanning and Sync Queue

**When to use this:** Internet connection drops but staff still need to clock in/out via NFC or kiosk

**Gherkin Scenario:**
```gherkin
Given the facility internet is down
When Emma taps her phone on the entrance NFC tag
Then the clock-in event is saved locally on her phone
And she sees "Clocked in (offline - will sync)"
When the internet connection restores
Then the queued event syncs to the server
And Control Desk updates with the correct timestamp
```

**Steps:**

1. **Offline detection**
   - **Automatic:** Timebreez PWA detects loss of connectivity
   - **Indicator:** Orange "Offline" banner at top of app
   - **Expected:** App continues to function in limited mode

2. **Clock in while offline**
   - **Action:** Tap NFC tag as normal
   - **Result:** Clock-in event stored in local device storage
   - **Notification:** "Clocked in at 08:58 (offline - will sync when connected)"
   - **Expected:** Event queued locally

3. **View offline queue**
   - **Look for:** "Pending Sync" indicator in app
   - **Shows:** Number of queued events (e.g., "3 events pending sync")
   - **Expected:** Queue visible to staff

4. **Automatic sync on reconnection**
   - **When:** Internet connection restores
   - **Action:** Queued events automatically upload to server
   - **Notification:** "3 events synced successfully"
   - **Timestamps:** Original timestamps preserved (not sync time)
   - **Expected:** All events appear in attendance log with correct times

5. **Manual sync** (if auto-sync fails)
   - **Open:** Timebreez PWA
   - **Pull down:** To refresh, or tap "Sync Now" button
   - **Expected:** Queued events upload
   - **If fails:** Check connection, try again

6. **Verify synced events**
   - **Control Desk:** Present counts update after sync
   - **Attendance log:** Events show original timestamps with "synced" flag
   - **Expected:** No data loss from offline period

**Screenshots:** [Screenshot: Offline banner and pending sync indicator]

**Common Issues:**
- ❌ Problem: Events lost after sync
  ✅ Solution: Events are stored in browser local storage (PWA) or device storage (native). Clearing browser data will delete queued events. Do not clear browser data while events are pending.

- ❌ Problem: Duplicate events after sync
  ✅ Solution: The system de-duplicates based on employee ID + timestamp + event type. If duplicates appear, they can be cleaned up in the attendance log by an admin.

- ❌ Problem: Offline clock-in timestamps are wrong
  ✅ Solution: Timestamps come from the device clock. Ensure staff devices have correct time settings (auto-set from network recommended).

---

## Troubleshooting

### Issue: NFC tag not recognized
**Symptoms:** Phone doesn't respond when held near NFC tag
**Cause:** NFC disabled, tag damaged, or phone incompatible
**Solution:**
1. Enable NFC in phone settings (Android: Settings > Connected devices > NFC)
2. iPhone 7+ supports NFC natively with Timebreez PWA
3. Hold phone within 2 cm of tag, keep still for 1-2 seconds
4. Try a different NFC tag to rule out damage
5. Remove thick or metallic phone case

---

### Issue: Kiosk tablet locks up or freezes
**Symptoms:** Kiosk screen unresponsive, cannot clock in
**Cause:** Browser memory issue, tablet overheating, or power loss
**Solution:**
1. Force-restart the tablet (hold power button 10 seconds)
2. Re-open the kiosk URL in browser
3. Clear browser cache if persistent
4. Ensure tablet is connected to power and not overheating
5. Consider restarting tablet daily (schedule auto-restart if supported)

---

### Issue: Who's Where shows stale data
**Symptoms:** Staff left a room hours ago but still shows as present
**Cause:** Staff did not scan room exit NFC tag
**Solution:**
1. Manual correction: Admin can edit room_exit event in attendance log
2. Automatic timeout: Configure "stale presence timeout" (e.g., 4 hours) in Settings
3. Remind staff to scan room tags when moving between rooms
4. End-of-day cleanup: System auto-closes open room sessions at shift end

---

### Issue: Geofence clock-in fails
**Symptoms:** Staff is on-site but geofence doesn't register
**Cause:** GPS accuracy, location permissions, or building interference
**Solution:**
1. Check location permissions (must be "Always Allow" or "While Using App")
2. Step outside briefly (buildings can block GPS signal)
3. Increase geofence radius in Settings (try 150m instead of 100m)
4. Use NFC or kiosk as backup if geofence is unreliable at your location

---

## Related Guides
- [Control Desk Operations](./05-control-desk-operations.md)
- [Break Coverage Calculator](./10-break-coverage-calculator.md)
- [Compliance Trail & Audit](./11-compliance-trail-audit.md)
- [Troubleshooting Guide](./08-troubleshooting.md)

## Need More Help?
- **Timebreez Support:** support@timebreez.com
- **Demo mode:** www.timebreez.com/login (explore attendance features in the demo org)
- **Paxton Integration:** help@paxton-access.com (Net2 server configuration)
- **Book a call:** Schedule a 15-min walkthrough of attendance setup
