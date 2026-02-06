# Navigation & Vocabulary Settings - Multi-Vertical Support

## Who This Is For
**Managers and Administrators** who want to customize Timebreez terminology and navigation labels to match their business type (childcare, hospitality, or other).

## What You'll Learn
- What vocabulary settings are and why they matter
- Default terminology for childcare vs hospitality
- How to change navigation labels in the sidebar
- Customizing entity names across the application
- How vocabulary changes propagate through the UI

## Prerequisites
- Admin role in Timebreez (vocabulary settings require admin permissions)
- Understanding of your business type and preferred terminology
- Access to Settings page

---

## Quick Start (TL;DR)

1. Go to **Settings > Vocabulary**
2. Select your **business type** (Childcare, Hospitality, or Custom)
3. Review the **term mappings** (e.g., "Rooms" becomes "Sections")
4. Adjust any **individual terms** you want to customize
5. Click **Save** - navigation labels and UI text update immediately
6. Verify changes in the **sidebar** and throughout the app

---

## Understanding Vocabulary Settings

### What Are Vocabulary Settings?

Timebreez is designed for **multiple business verticals** (childcare, hospitality, healthcare, etc.). Different industries use different words for the same concepts:

| Concept | Childcare Term | Hospitality Term |
|---------|---------------|-----------------|
| Work areas | **Rooms** | **Sections** |
| Work periods | **Sessions** | **Shifts** |
| Staffing rules | **Ratios** | **Covers** |
| Staff assignments | **Room Assignments** | **Section Assignments** |
| Child/guest count | **Child Count** | **Cover Count** |
| Compliance body | **Tusla** | **Health & Safety** |
| Schedule view | **Roster** | **Rota** |

Vocabulary settings let you change these terms so the entire application speaks your language.

### Why This Matters

- **Staff adoption:** Employees recognize familiar terminology immediately
- **Training:** Reduced confusion during onboarding
- **Multi-site:** Organizations with mixed verticals can customize per location
- **Professionalism:** UI matches your industry standards

### How It Works

When you change vocabulary settings:

1. **Sidebar navigation** labels update (e.g., "Rooms" becomes "Sections")
2. **Page headings** update across all features
3. **Form labels** update (e.g., "Select Room" becomes "Select Section")
4. **Toast messages** update (e.g., "Room created" becomes "Section created")
5. **Help text** and tooltips update where applicable

**What does NOT change:**
- Database column names (internal, invisible to users)
- API endpoints (developer-facing, unchanged)
- URL paths (remain consistent regardless of vocabulary)

---

## Step-by-Step Guides

### Scenario 1: Change from "Rooms" to "Sections" (Hospitality Setup)

**When to use this:** You are a hospitality business (restaurant, hotel) and want the UI to use hospitality terminology

**Gherkin Scenario:**
```gherkin
Given I am an admin of a hospitality organization
And the sidebar currently shows "Rooms"
When I go to Settings > Vocabulary
And I select "Hospitality" as my business type
And I save
Then the sidebar shows "Sections" instead of "Rooms"
And all pages referencing "Rooms" now show "Sections"
And the Control Desk shows "Section" tiles instead of "Room" tiles
```

**Steps:**

1. **Navigate to Vocabulary settings**
   - **Click:** Settings in the sidebar
   - **Click:** "Vocabulary" or "Terminology" submenu item
   - **Expected:** Vocabulary configuration page loads

2. **Select your business type**
   - **Look for:** "Business Type" dropdown or radio buttons
   - **Options:**
     - **Childcare** (default) - Rooms, Sessions, Ratios, Roster
     - **Hospitality** - Sections, Shifts, Covers, Rota
     - **Custom** - Define your own terms
   - **Click:** "Hospitality"
   - **Expected:** Term preview table updates to show hospitality terms

3. **Review the term mappings**
   - **Preview table shows:**
     - Rooms -> **Sections**
     - Sessions -> **Shifts**
     - Ratios -> **Covers**
     - Roster -> **Rota**
     - Child Count -> **Cover Count**
     - Room Assignment -> **Section Assignment**
   - **Expected:** All term changes visible in preview

4. **Save the vocabulary**
   - **Click:** "Save" button
   - **Expected:** Success toast "Vocabulary settings updated"

5. **Verify sidebar navigation**
   - **Look at:** Sidebar navigation menu
   - **Expected changes:**
     - "Rooms" is now "Sections"
     - "Roster" is now "Rota"
   - **Expected:** All navigation labels updated

6. **Verify feature pages**
   - **Click:** "Sections" in sidebar (formerly "Rooms")
   - **Expected:** Page heading says "Sections" not "Rooms"
   - **Expected:** "Add Section" button (not "Add Room")
   - **Click:** Control Desk
   - **Expected:** Tiles labeled "Bar Section", "Restaurant Floor" (not "Baby Room", etc.)

**Screenshots:** [Screenshot: Vocabulary settings with Hospitality selected]

**Common Issues:**
- Problem: Some pages still show "Rooms" after changing vocabulary
  Solution: Hard refresh the browser (Ctrl+Shift+R). Vocabulary changes require a page reload to take effect on all components.

- Problem: Demo org still shows childcare terms after changing to Hospitality
  Solution: The demo organization uses childcare data. Vocabulary changes the labels but not the demo data content (room names remain "Baby Room", etc.). In your own organization, you would name sections appropriately.

---

### Scenario 2: Customize Navigation for Hospitality

**When to use this:** You want to adjust which navigation items appear and how they are labeled for a hospitality context

**Gherkin Scenario:**
```gherkin
Given I have selected "Hospitality" vocabulary
When I go to Settings > Navigation
Then I see a list of sidebar navigation items
And I can toggle items ON/OFF
And I can rename items to match my business
When I rename "Control Desk" to "Floor View"
And I hide "Session Scheduling" (not relevant for hospitality)
And I save
Then the sidebar shows "Floor View" instead of "Control Desk"
And "Session Scheduling" no longer appears in the sidebar
```

**Steps:**

1. **Navigate to Navigation settings**
   - **Click:** Settings > Navigation (or Settings > Sidebar Configuration)
   - **Expected:** Navigation configuration page loads

2. **View current navigation items**
   - **Look for:** List of sidebar items with toggle switches and rename fields
   - **Default items:**
     - Dashboard (always visible)
     - Control Desk
     - Sections (was "Rooms")
     - Rota (was "Roster")
     - Leave Requests
     - Employees
     - Session Scheduling
     - Settings
   - **Expected:** All items listed with current labels

3. **Hide irrelevant items**
   - **Find:** "Session Scheduling" row
   - **Click:** Toggle switch to OFF
   - **Expected:** Item will be hidden from sidebar
   - **Other items to consider hiding for hospitality:**
     - "Session Scheduling" (ECCE-specific, not relevant)
     - Any childcare-specific features

4. **Rename items**
   - **Find:** "Control Desk" row
   - **Click:** The label text field
   - **Change:** "Control Desk" to "Floor View"
   - **Expected:** New label entered

5. **Reorder items** (if supported)
   - **Drag:** Items up or down to change sidebar order
   - **Expected:** Order reflects your workflow priority

6. **Save navigation settings**
   - **Click:** "Save" button
   - **Expected:** Success toast "Navigation settings updated"

7. **Verify the sidebar**
   - **Look at:** Sidebar navigation
   - **Expected:**
     - "Floor View" appears (was "Control Desk")
     - "Session Scheduling" is gone (hidden)
     - Order matches your configuration
   - **Expected:** Clean sidebar for hospitality workflow

**Screenshots:** [Screenshot: Navigation settings with renamed and hidden items]

**Common Issues:**
- Problem: Cannot hide "Dashboard" or "Settings"
  Solution: These are protected navigation items and cannot be hidden. They are required for core functionality.

- Problem: Hidden items still appear for some users
  Solution: Navigation settings apply organization-wide. Ask affected users to refresh their browser. If they have a different role (e.g., staff vs manager), they may see a different navigation set.

---

### Scenario 3: Set Up Custom Vocabulary

**When to use this:** Neither "Childcare" nor "Hospitality" presets match your business, and you want to define your own terms

**Gherkin Scenario:**
```gherkin
Given I run a healthcare staffing organization
When I go to Settings > Vocabulary
And I select "Custom" business type
And I set "Rooms" to "Wards"
And I set "Sessions" to "Rounds"
And I set "Roster" to "Duty Schedule"
And I save
Then the entire application uses my custom terms
And the sidebar shows "Wards", "Duty Schedule", etc.
```

**Steps:**

1. **Navigate to Vocabulary settings**
   - **Click:** Settings > Vocabulary
   - **Expected:** Vocabulary configuration page loads

2. **Select "Custom" business type**
   - **Click:** "Custom" option
   - **Expected:** All term fields become editable text inputs

3. **Define your custom terms**
   - **For each row, enter your preferred term:**
     - Rooms -> **Wards**
     - Sessions -> **Rounds**
     - Ratios -> **Staffing Levels**
     - Roster -> **Duty Schedule**
     - Child Count -> **Patient Count**
     - Room Assignment -> **Ward Assignment**
     - Cover Staff -> **Relief Staff**
   - **Expected:** Each field accepts your custom text

4. **Preview the changes**
   - **Look for:** Preview panel showing how the UI will look
   - **Expected:** Sidebar and page headings reflect your custom terms

5. **Save custom vocabulary**
   - **Click:** "Save" button
   - **Expected:** Success toast "Custom vocabulary saved"

6. **Verify across the application**
   - **Sidebar:** Shows "Wards", "Duty Schedule"
   - **Control Desk:** Tile labels say "Ward" instead of "Room"
   - **Forms:** Dropdowns say "Select Ward" instead of "Select Room"
   - **Expected:** Consistent terminology throughout

**Screenshots:** [Screenshot: Custom vocabulary with healthcare terms]

**Common Issues:**
- Problem: Custom term is too long and gets truncated in the sidebar
  Solution: Keep sidebar labels short (under 15 characters). Use abbreviations if needed (e.g., "Duty Sched." instead of "Duty Schedule").

- Problem: I want to reset to default terminology
  Solution: Go to Settings > Vocabulary, select "Childcare" (the default preset), and save. All terms revert to defaults.

---

### Scenario 4: Verify Vocabulary Across Features

**When to use this:** After changing vocabulary, verify the changes propagated to all features

**Gherkin Scenario:**
```gherkin
Given I changed vocabulary from Childcare to Hospitality
When I visit each major feature page
Then I see hospitality terminology everywhere
And no pages still show childcare terminology
```

**Steps:**

1. **Check the sidebar**
   - **Expected:** "Sections" (not "Rooms"), "Rota" (not "Roster")

2. **Check Control Desk**
   - **Navigate to:** Control Desk
   - **Expected:** Tiles labeled "Section" (not "Room")
   - **Expected:** "Cover Count" (not "Child Count")

3. **Check the Scheduler / Rota**
   - **Navigate to:** Rota (or Scheduler)
   - **Expected:** Page heading says "Rota" or "Schedule"
   - **Expected:** Row labels say "Section" names

4. **Check Employees page**
   - **Navigate to:** Employees
   - **Click:** Any employee profile
   - **Expected:** "Section Assignment" (not "Room Assignment")

5. **Check Leave Requests**
   - **Navigate to:** Leave Requests
   - **Expected:** Leave cards show "Section" not "Room" in impact context

6. **Check Settings pages**
   - **Navigate to:** Settings > Sections (was "Rooms")
   - **Expected:** Page heading says "Sections"
   - **Expected:** "Add Section" button

7. **Report any inconsistencies**
   - **If you find:** Any page still using old terminology
   - **Report:** Email support@timebreez.com with the page URL and screenshot
   - **Expected:** Timebreez team will fix the missed translation

**Screenshots:** [Screenshot: Side-by-side of childcare vs hospitality vocabulary across pages]

**Common Issues:**
- Problem: Export PDFs still show old terminology
  Solution: PDF templates may cache vocabulary. After changing vocabulary, generate a new export. If still wrong, contact support.

- Problem: Email notifications use old terms
  Solution: Email templates update on the next scheduled send. Previously queued emails may still use old terminology.

---

## Troubleshooting

### Issue: Vocabulary changes not visible after save
**Symptoms:** Saved new vocabulary but sidebar and pages still show old terms
**Cause:** Browser cache serving old page content
**Solution:**
1. Hard refresh the page (Ctrl+Shift+R)
2. If still showing old terms, clear browser cache
3. Try in an incognito/private window
4. Verify the save was successful (go back to Settings > Vocabulary and check current values)

---

### Issue: Some users see old vocabulary, others see new
**Symptoms:** Manager sees "Sections" but staff sees "Rooms"
**Cause:** Different browser cache states, or per-role vocabulary not implemented
**Solution:**
1. Ask affected users to hard refresh their browser
2. Vocabulary settings are organization-wide (all users should see the same terms)
3. If issue persists after refresh, report as a bug

---

### Issue: Custom term causes layout issues
**Symptoms:** Long custom term overflows sidebar or form labels
**Cause:** Term is too long for the UI element
**Solution:**
1. Use shorter terms (under 15 characters for sidebar, under 25 for page headings)
2. Use abbreviations where appropriate
3. Test on mobile view (smallest viewport) to ensure fit

---

### Issue: Cannot find Vocabulary settings
**Symptoms:** No "Vocabulary" or "Terminology" option in Settings
**Cause:** Feature may require Admin role, or may be under a different menu name
**Solution:**
1. Verify you have Admin role (not just Manager)
2. Check Settings > Organization for a "Terminology" or "Vocabulary" subsection
3. If not present, the feature may not be enabled for your subscription tier
4. Contact support to enable vocabulary settings

---

## Related Guides
- [Demo Mode - Getting Started](./01-demo-mode-onboarding.md)
- [Control Desk Operations](./05-control-desk-operations.md)
- [Session Scheduling (ECCE/AIMS)](./02-session-scheduling-ecce-aims.md)
- [Troubleshooting Guide](./08-troubleshooting.md)

## Need More Help?
- **Timebreez Support:** support@timebreez.com
- **Demo mode:** www.timebreez.com/login (demo uses childcare vocabulary by default)
- **Book a call:** Schedule a 15-min walkthrough of vocabulary customization
