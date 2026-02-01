# Session Scheduling - ECCE & AIMS Compliance

## Who This Is For
**Childcare Managers in Ireland** who need to configure ECCE (Early Childhood Care and Education) sessions and AIMS (Access and Inclusion Model) grant compliance.

## What You'll Learn
- What ECCE sessions are and why they matter
- How to configure session templates for rooms
- Enabling AIMS grant tracking (+1 staff requirement)
- Viewing session indicators on Control Desk
- Irish childcare compliance requirements

## Prerequisites
- Admin or Manager role in Timebreez
- At least one Preschool room configured
- Understanding of Irish ECCE program requirements

---

## Quick Start (TL;DR)

1. Go to **Admin > Rooms**
2. Click **Edit** on a Preschool room
3. Toggle **Session Scheduling** ON
4. Select **ECCE Midday** template
5. Check **AIMS Grant** if applicable
6. Click **Save**
7. Session indicator appears on Control Desk

---

## Understanding ECCE & AIMS

### What is ECCE?

The **Early Childhood Care and Education (ECCE) Scheme** is an Irish government program providing free preschool for children aged 3-5 years. Key details:

- **Duration:** 3 hours per day, 5 days per week
- **Term:** September to June (38 weeks)
- **Staff Ratio:** 1:11 (one educator per 11 children)
- **Purpose:** Prepare children for primary school

**Why it matters in Timebreez:**
- You need to track **which rooms run ECCE sessions**
- Staff scheduling must account for **1:11 ratio during session hours**
- Grant funding requires **accurate session attendance tracking**

### What is AIMS?

The **Access and Inclusion Model (AIMS)** provides additional support for children with disabilities in ECCE settings. Key requirements:

- **+1 additional staff member** during ECCE session hours
- **Enhanced ratio:** 1:11 becomes effectively 1:5-6 with AIMS support
- **Grant tracking:** Must document AIMS-supported sessions for funding

**Why it matters in Timebreez:**
- Control Desk shows **+1 required staff** for AIMS rooms
- Scheduling automatically accounts for extra coverage
- Compliance reports include AIMS session hours

---

## Step-by-Step Guides

### Scenario 1: Enable ECCE Session for a Preschool Room

**When to use this:** You have a Preschool room that runs ECCE sessions

**Gherkin Scenario:**
```gherkin
Given I am on the Admin > Rooms page
And I have a Preschool room configured
When I click "Edit" on the Preschool room
And I toggle "Session Scheduling" ON
Then the session configuration panel appears
And I can select an ECCE session template
```

**Steps:**

1. **Navigate to Room Management**
   - **Click:** Settings > Admin > Rooms (or Admin > Rooms in sidebar)
   - **Look for:** List of all rooms in your organization
   - **Expected:** You see your Preschool room (e.g., "Preschool Room" or "ECC")

2. **Click Edit on the Preschool room**
   - **Click:** Pencil icon or "Edit" button next to your Preschool room
   - **Look for:** Room edit form/modal opens
   - **Expected:** Form shows room name, capacity, age range, etc.

3. **Find the Session Scheduling toggle**
   - **Scroll down:** To "Session Scheduling" section
   - **Look for:** Toggle switch labeled "Enable Session Scheduling"
   - **Expected:** Toggle is currently OFF (gray)

4. **Toggle Session Scheduling ON**
   - **Click:** The toggle switch
   - **Expected:**
     - Toggle turns blue/green (active state)
     - Session configuration panel appears below

5. **Verify session panel is visible**
   - **Look for:**
     - "Session Template" dropdown
     - "Preview" card showing session details
   - **Expected:** Both elements now visible

**Screenshots:** [Screenshot: Session toggle enabled, panel appears]

**Common Issues:**
- ❌ Problem: Toggle doesn't stay ON after clicking
  ✅ Solution: You may need to save the form first. Try toggling ON, then immediately clicking "Save" at the bottom.

- ❌ Problem: Session panel doesn't appear
  ✅ Solution: Ensure you're editing a Preschool or ECC room type. Session scheduling is only available for eligible room types.

---

### Scenario 2: Select ECCE Midday Template

**When to use this:** Your ECCE session runs from 09:30 to 12:30 (most common)

**Gherkin Scenario:**
```gherkin
Given session scheduling is enabled for my room
When I open the "Session Template" dropdown
Then I see ECCE Morning, ECCE Midday, ECCE Afternoon options
When I select "ECCE Midday"
Then the preview shows 09:30 - 12:30, 1:11 ratio, September - June
```

**Steps:**

1. **Ensure session scheduling is ON**
   - **Verify:** Session configuration panel is visible
   - **Look for:** "Session Template" dropdown

2. **Click the Session Template dropdown**
   - **Click:** "Session Template" dropdown menu
   - **Expected:** List of templates appears

3. **View available templates**
   - **Look for:**
     - **ECCE Morning** (09:00 - 12:00)
     - **ECCE Midday** (09:30 - 12:30) ← Most common
     - **ECCE Afternoon** (12:30 - 15:15)
     - **Wrap-around Care** (07:00 - 18:00)
   - **Expected:** At least 4 template options visible

4. **Select ECCE Midday**
   - **Click:** "ECCE Midday" option
   - **Expected:** Dropdown closes, selection confirmed

5. **Review the preview card**
   - **Look for:** Preview card below the dropdown showing:
     - **Session Hours:** 09:30 - 12:30
     - **Staff Ratio:** 1:11 (1 educator per 11 children)
     - **Term Dates:** September - June
     - **Total Hours:** 3 hours per day
   - **Expected:** All details match your ECCE program requirements

**Screenshots:** [Screenshot: Template dropdown with ECCE Midday selected, preview visible]

**Common Issues:**
- ❌ Problem: Preview doesn't update after selecting template
  ✅ Solution: Wait 1-2 seconds for the UI to refresh. If still not updating, refresh the page and try again.

- ❌ Problem: "ECCE Midday" not in the dropdown
  ✅ Solution: Ensure session templates are configured in your organization settings. Contact support if templates are missing.

---

### Scenario 3: Enable AIMS Grant for Enhanced Support

**When to use this:** Your room receives AIMS funding and requires +1 additional staff

**Gherkin Scenario:**
```gherkin
Given I have selected an ECCE template
When I check the "AIMS Grant" checkbox
Then I see helper text "+1 additional staff during this session"
And the required staff count increases by 1
```

**Steps:**

1. **Select an ECCE template** (as in Scenario 2)
   - **Ensure:** ECCE Morning, Midday, or Afternoon is selected
   - **Expected:** Preview card is visible

2. **Find the AIMS Grant checkbox**
   - **Look for:** Checkbox labeled "AIMS Grant" or "Access and Inclusion Model"
   - **Location:** Below the session template dropdown
   - **Expected:** Checkbox is visible and unchecked

3. **Check the AIMS Grant box**
   - **Click:** The AIMS Grant checkbox
   - **Expected:** Checkbox becomes checked (blue checkmark)

4. **Verify helper text appears**
   - **Look for:** Text below checkbox:
     - "+1 additional staff during this session"
     - "Enhanced support for children with disabilities"
   - **Expected:** Helper text is visible

5. **Understand the impact**
   - **During session hours (e.g., 09:30 - 12:30):**
     - Control Desk will show **required staff + 1**
     - Example: If ratio requires 2 staff, AIMS makes it 3 required
   - **Outside session hours:**
     - Normal staffing ratios apply (AIMS doesn't affect)

**Screenshots:** [Screenshot: AIMS checkbox checked, helper text visible]

**Common Issues:**
- ❌ Problem: AIMS checkbox is not visible
  ✅ Solution: AIMS is only available for ECCE templates. If you selected "Wrap-around Care" (non-ECCE), AIMS won't appear. Select an ECCE template first.

- ❌ Problem: I checked AIMS but required staff didn't increase
  ✅ Solution: The +1 only applies **during session hours**. Check Control Desk during the session time (e.g., 10:00 AM) to see the increased requirement.

---

### Scenario 4: Save Session Configuration

**When to use this:** You've configured your session and want to apply the changes

**Gherkin Scenario:**
```gherkin
Given I have configured session scheduling and AIMS
When I click the "Save" button
Then I see a success toast "Room updated successfully"
And the session configuration is persisted
```

**Steps:**

1. **Review your configuration**
   - **Verify:**
     - Session Scheduling toggle is ON
     - ECCE template is selected
     - AIMS checkbox matches your needs (checked or unchecked)
   - **Expected:** All settings look correct

2. **Click the Save button**
   - **Look for:** Blue "Save" or "Update Room" button at bottom of form
   - **Click:** Save button
   - **Expected:** Button shows loading spinner briefly

3. **Wait for success confirmation**
   - **Look for:** Green success toast appears (top right or bottom)
   - **Message:** "Room updated successfully" or similar
   - **Expected:** Toast appears within 2-3 seconds

4. **Close the form**
   - **Expected:** Form/modal closes automatically, or
   - **Click:** "Close" or X button if form stays open

5. **Verify changes persisted**
   - **Click:** Edit button on the same room again
   - **Verify:**
     - Session toggle is still ON
     - Selected template still shows
     - AIMS checkbox matches what you saved
   - **Expected:** All your changes are saved

**Screenshots:** [Screenshot: Save button, success toast]

**Common Issues:**
- ❌ Problem: Save button is disabled (grayed out)
  ✅ Solution: Ensure all required fields are filled. Room name, capacity, and age range are usually required.

- ❌ Problem: "Error saving room" toast appears
  ✅ Solution: Check the error message. Common causes:
    - Room name already exists
    - Invalid capacity (must be > 0)
    - Network error (check internet connection)

---

### Scenario 5: View Session Indicators on Control Desk

**When to use this:** You want to see which rooms are currently in ECCE session

**Gherkin Scenario:**
```gherkin
Given I have configured ECCE session for Preschool room
When I view Control Desk during session hours (e.g., 10:00 AM)
Then the Preschool room tile shows a "SESSION" indicator
And the required staff count includes the 1:11 ratio
```

**Steps:**

1. **Navigate to Control Desk**
   - **Click:** "Control Desk" in the sidebar
   - **Expected:** Room tiles appear for all rooms

2. **Find your Preschool room tile**
   - **Look for:** Room tile labeled "Preschool" or "ECC"
   - **Expected:** Room tile is visible

3. **Check for SESSION indicator**
   - **Look for:** Badge or icon labeled "SESSION" on the room tile
   - **Color:** Often blue or purple to indicate session active
   - **Expected:**
     - **During session hours (e.g., 09:30 - 12:30):** SESSION badge visible
     - **Outside session hours:** No SESSION badge

4. **Verify required staff count**
   - **Look for:** "Required" count on room tile
   - **Expected:**
     - **ECCE without AIMS:** Required = child_count / 11 (rounded up)
     - **ECCE with AIMS:** Required = (child_count / 11) + 1
   - **Example:** 22 children → 2 required → 3 required with AIMS

5. **Click the room tile for details**
   - **Click:** Preschool room tile
   - **Expected:** Modal shows:
     - Session hours (09:30 - 12:30)
     - Ratio (1:11)
     - AIMS status (Yes/No)
     - Staff currently assigned

**Screenshots:** [Screenshot: Control Desk with SESSION indicator on Preschool tile]

**Common Issues:**
- ❌ Problem: SESSION indicator doesn't appear
  ✅ Solution:
    1. Check the current time - are you viewing during session hours?
    2. Refresh the page (data may be cached)
    3. Verify the session is saved correctly (edit room and check)

- ❌ Problem: Required staff count doesn't match expected ratio
  ✅ Solution:
    1. Verify child_count is set on the room (Admin > Rooms > child count field)
    2. Check if AIMS is enabled (adds +1)
    3. Outside session hours, normal ratios apply (not 1:11)

---

### Scenario 6: Disable Session Scheduling

**When to use this:** The room no longer runs ECCE sessions

**Gherkin Scenario:**
```gherkin
Given session scheduling is currently enabled
When I toggle Session Scheduling OFF
Then the session configuration panel disappears
And I click Save
Then the room reverts to normal staffing ratios
```

**Steps:**

1. **Open the room edit form**
   - **Navigate:** Admin > Rooms
   - **Click:** Edit on the room with sessions enabled

2. **Find the Session Scheduling toggle**
   - **Look for:** Toggle switch labeled "Enable Session Scheduling"
   - **Current state:** ON (blue/green)

3. **Toggle OFF**
   - **Click:** The toggle switch
   - **Expected:**
     - Toggle turns gray (inactive)
     - Session configuration panel disappears immediately

4. **Verify panel is hidden**
   - **Look for:** Session template dropdown should no longer be visible
   - **Expected:** Session configuration section collapsed or hidden

5. **Save the changes**
   - **Click:** Save button at bottom of form
   - **Expected:** Success toast appears

6. **Verify on Control Desk**
   - **Navigate:** Control Desk
   - **Check:** Room tile no longer shows SESSION indicator
   - **Expected:** Required staff reverts to normal room-based ratio

**Screenshots:** [Screenshot: Session toggle OFF, panel hidden]

**Common Issues:**
- ❌ Problem: Toggle turns OFF but panel doesn't hide
  ✅ Solution: Wait 1-2 seconds for UI to update. If still visible, refresh the page.

---

### Scenario 7: Switch Between ECCE Templates

**When to use this:** You need to change session hours (e.g., Morning to Midday)

**Gherkin Scenario:**
```gherkin
Given I have ECCE Morning selected
When I change the template to ECCE Afternoon
Then the preview updates to show 12:30 - 15:15
And I save the changes
Then the new session hours apply
```

**Steps:**

1. **Edit the room with sessions enabled**
   - **Navigate:** Admin > Rooms > Edit room
   - **Verify:** Session scheduling is ON

2. **View current template**
   - **Look for:** Session Template dropdown shows current selection (e.g., "ECCE Morning")
   - **Preview shows:** 09:00 - 12:00

3. **Open the dropdown**
   - **Click:** Session Template dropdown
   - **Expected:** All templates visible

4. **Select a different ECCE template**
   - **Click:** "ECCE Afternoon"
   - **Expected:** Dropdown closes, selection changes

5. **Verify preview updates**
   - **Look for:** Preview card now shows:
     - **Session Hours:** 12:30 - 15:15
     - **Ratio:** Still 1:11
     - **Term:** September - June
   - **Expected:** Preview updates immediately

6. **Save the changes**
   - **Click:** Save button
   - **Expected:** Success toast appears

7. **Verify on Control Desk**
   - **Navigate:** Control Desk
   - **Check timing:**
     - At 10:00 AM: No SESSION indicator (before new session hours)
     - At 1:00 PM: SESSION indicator appears (during 12:30 - 15:15)
   - **Expected:** SESSION indicator matches new hours

**Screenshots:** [Screenshot: Switching templates, preview updates]

**Common Issues:**
- ❌ Problem: Changes don't appear on Control Desk
  ✅ Solution: Refresh the Control Desk page. Real-time updates may take a few seconds.

---

### Scenario 8: Understand Non-ECCE Templates

**When to use this:** You have wrap-around care or extended hours

**Gherkin Scenario:**
```gherkin
Given I select "Wrap-around Care" template
Then the preview shows 07:00 - 18:00 (11 hours)
And the AIMS checkbox is NOT visible
And the ratio is based on room type (not 1:11)
```

**Steps:**

1. **Select Wrap-around Care template**
   - **Open:** Session Template dropdown
   - **Click:** "Wrap-around Care"
   - **Expected:** Preview updates to 07:00 - 18:00

2. **Verify AIMS checkbox is hidden**
   - **Look for:** AIMS Grant checkbox
   - **Expected:** Checkbox is NOT visible (AIMS only for ECCE programs)

3. **Understand the difference**
   - **ECCE templates:**
     - 1:11 ratio during session hours
     - AIMS eligible
     - September - June term
   - **Wrap-around Care:**
     - Normal room ratios apply (e.g., 1:3 for babies, 1:6 for toddlers)
     - No AIMS
     - Year-round

4. **Use cases for Wrap-around:**
   - Before/after ECCE session care
   - Full-day childcare for working parents
   - Summer camps (outside September - June)

**Screenshots:** [Screenshot: Wrap-around template, no AIMS checkbox]

---

## Troubleshooting

### Issue: Session toggle doesn't appear
**Symptoms:** Edit room form has no "Session Scheduling" section
**Cause:** Room type is not eligible for sessions (e.g., Baby Room)
**Solution:**
1. Sessions are only available for Preschool and ECC room types
2. Check room type field in the form
3. If you need sessions, change room type to "Preschool"

---

### Issue: AIMS checkbox invisible
**Symptoms:** AIMS checkbox doesn't show even with ECCE template selected
**Cause:** Non-ECCE template selected
**Solution:**
1. Verify you selected ECCE Morning, Midday, or Afternoon
2. If "Wrap-around Care" is selected, AIMS won't appear (by design)
3. Switch to an ECCE template to enable AIMS

---

### Issue: Required staff count seems wrong
**Symptoms:** Control Desk shows different required count than expected
**Cause:** Multiple factors affect required count
**Solution:**
1. **During session hours:** Required = (child_count / 11) rounded up
2. **With AIMS:** Add +1 to the above
3. **Outside session hours:** Normal ratios apply (check room type)
4. **Verify:** child_count is set on the room (not 0 or NULL)

---

### Issue: SESSION indicator doesn't appear
**Symptoms:** Control Desk doesn't show SESSION badge during session hours
**Cause:** Session not saved, or viewing outside session hours
**Solution:**
1. Check current time vs. session hours (e.g., 09:30 - 12:30)
2. Refresh Control Desk page
3. Re-edit room and verify session template is saved
4. Check browser console for errors (F12)

---

### Issue: Can't save session configuration
**Symptoms:** Save button fails or shows error
**Cause:** Validation error or database issue
**Solution:**
1. Ensure all required fields filled (room name, capacity, age range)
2. Capacity must be > 0
3. Age range format: "3-5 years" (text field, any format accepted)
4. If error persists, check error message or contact support

---

## Related Guides
- [Demo Mode - Getting Started](./01-demo-mode-onboarding.md)
- [Control Desk Operations](./05-control-desk-operations.md)
- [Settings and Configuration](./07-settings-and-configuration.md)
- [Troubleshooting Guide](./08-troubleshooting.md)

## Need More Help?
- **ECCE Program Details:** [dcya.gov.ie/ecce](https://www.dcya.gov.ie)
- **AIMS Grant Info:** [DCYA AIMS Resources](https://www.dcya.gov.ie)
- **Timebreez Support:** support@timebreez.com
- **Book a call:** Schedule a 15-min walkthrough of session scheduling
