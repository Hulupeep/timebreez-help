# Credentials & Qualifications - Compliance Management

## Who This Is For
**Childcare Administrators and Compliance Officers** who need to track staff credentials, qualifications, and expiry dates for regulatory compliance.

## What You'll Learn
- What credentials are and why they matter (Garda Vetting, First Aid, FETAC, manual handling, fire safety)
- Setting up credential types as an admin
- Adding employee credentials with evidence upload
- Using the expiry tracking dashboard (30/60/90 day warnings)
- Understanding jurisdiction-specific requirements (Ireland/Tusla)
- Running qualification status checks across your team

## Prerequisites
- Admin role in Timebreez
- Knowledge of your regulatory requirements (Tusla, HSE, etc.)
- Digital copies of certificates for upload (PDF, JPG, PNG)
- Employee profiles already created

---

## Quick Start (TL;DR)

1. Go to **Settings > Credential Types** and add your required credentials
2. Navigate to **Employees > [Name] > Credentials** tab
3. Click **"Add Credential"** and fill in type, issue date, expiry date
4. **Upload evidence** (certificate PDF or photo)
5. Check the **Expiry Dashboard** for upcoming renewals (30/60/90 day warnings)
6. Run **Qualification Status** report to see team-wide compliance

---

## Understanding Credentials & Qualifications

### What are Credentials?

**Credentials** are verified qualifications, certifications, and clearances that staff must hold to work in regulated environments. In Irish childcare, these include:

| Credential | Description | Typical Validity | Regulatory Body |
|------------|-------------|------------------|-----------------|
| **Garda Vetting** | Police background check | 3 years (re-vetting) | National Vetting Bureau |
| **First Aid (QQI)** | Occupational first aid certificate | 2 years | QQI/PHECC |
| **FETAC Level 5/6** | Childcare qualification (minimum requirement) | Permanent | QQI (formerly FETAC) |
| **Manual Handling** | Safe lifting and handling training | 3 years | HSA |
| **Fire Safety** | Fire warden/marshal training | 1 year | Local fire service |
| **Child Protection** | Children First training | 3 years | Tusla |
| **Food Hygiene** | HACCP/food safety certification | 3 years | FSAI |
| **Tusla Registration** | Early Years Service registration | Annual | Tusla |

### Why Track Credentials?

**Compliance reasons:**
- **Tusla inspections:** Inspectors verify all staff credentials are current
- **Insurance requirements:** Lapsed credentials may void liability cover
- **Legal obligation:** Children First Act 2015 mandates certain checks
- **Parent confidence:** Families expect qualified, vetted staff

**Operational reasons:**
- **Avoid last-minute scrambles** when credentials expire
- **Maintain staffing ratios** (unqualified staff cannot count for ratios)
- **Audit trail** for regulatory evidence
- **Automated reminders** before expiry dates

---

## Step-by-Step Guides

### Scenario 1: Set Up Credential Types

**When to use this:** First-time setup, or adding a new credential category for your organization

**Gherkin Scenario:**
```gherkin
Given I am logged in as an admin
When I navigate to Settings > Credential Types
And I click "Add Credential Type"
And I enter name "Garda Vetting", validity "3 years", required "true"
And I click "Save"
Then the credential type is created
And it appears in the dropdown when adding employee credentials
```

**Steps:**

1. **Navigate to Settings**
   - **Click:** "Settings" in the sidebar
   - **Expected:** Settings submenu expands

2. **Open Credential Types**
   - **Click:** "Credential Types" submenu item
   - **Expected:** List of existing credential types (may be empty on first setup)

3. **Click Add Credential Type**
   - **Click:** Blue "Add Credential Type" button
   - **Expected:** Creation form opens

4. **Fill in credential type details**
   - **Name:** Garda Vetting
   - **Description:** National Vetting Bureau police background check
   - **Default Validity Period:** 3 years
   - **Required:** Check this box (mandatory for all staff)
   - **Evidence Required:** Check this box (certificate upload mandatory)
   - **Jurisdiction:** Ireland
   - **Expected:** All fields accept input

5. **Set warning thresholds**
   - **90-day warning:** Check (sends alert 90 days before expiry)
   - **60-day warning:** Check (sends alert 60 days before expiry)
   - **30-day warning:** Check (sends urgent alert 30 days before expiry)
   - **Expected:** Warning checkboxes selected

6. **Save the credential type**
   - **Click:** "Save" button
   - **Expected:** Success toast "Credential type created"
   - **Expected:** "Garda Vetting" appears in the credential types list

7. **Repeat for other types**
   - Add: First Aid (QQI), FETAC Level 5/6, Manual Handling, Fire Safety, Child Protection
   - **Expected:** All credential types appear in the list

**Screenshots:** [Screenshot: Credential Types settings with list of types]

**Common Issues:**
- ❌ Problem: "Credential type already exists" error
  ✅ Solution: A type with that name already exists. Check the list or use a more specific name (e.g., "First Aid - QQI Level 5" vs "First Aid - PHECC").

- ❌ Problem: Validity period field won't accept value
  ✅ Solution: Enter the number and select the unit (years, months, days) from the dropdown. Do not type "3 years" as text.

---

### Scenario 2: Add an Employee Credential

**When to use this:** A staff member has obtained or renewed a credential and you need to record it

**Gherkin Scenario:**
```gherkin
Given I am viewing Emma Murphy's employee profile
When I click the "Credentials" tab
And I click "Add Credential"
And I select type "Garda Vetting", issue date "2025-03-15", expiry date "2028-03-15"
And I enter reference number "NVB-2025-12345"
And I click "Save"
Then the credential is added to Emma's profile
And the expiry date triggers future warnings
```

**Steps:**

1. **Navigate to the employee**
   - **Click:** "Employees" in sidebar
   - **Click:** Emma Murphy's row
   - **Expected:** Employee profile page loads

2. **Open Credentials tab**
   - **Click:** "Credentials" tab (next to Profile, Schedule, Leave tabs)
   - **Expected:** List of existing credentials (may be empty)

3. **Click Add Credential**
   - **Click:** "Add Credential" button
   - **Expected:** Credential form modal opens

4. **Fill in credential details**
   - **Credential Type:** Select "Garda Vetting" from dropdown
   - **Reference Number:** NVB-2025-12345
   - **Issue Date:** 2025-03-15
   - **Expiry Date:** 2028-03-15 (auto-calculated from validity period, editable)
   - **Issuing Authority:** National Vetting Bureau
   - **Status:** Active
   - **Expected:** All fields filled, expiry auto-calculated

5. **Add notes** (optional)
   - **Notes:** "Re-vetting completed March 2025. Previous vetting NVB-2022-98765."
   - **Expected:** Notes saved for audit reference

6. **Save the credential**
   - **Click:** "Save" button
   - **Expected:** Success toast "Credential added"
   - **Expected:** Credential appears in Emma's credentials list

7. **Verify credential in list**
   - **Look for:** Row showing:
     - **Type:** Garda Vetting
     - **Issue Date:** 2025-03-15
     - **Expiry Date:** 2028-03-15
     - **Status:** Active (green badge)
     - **Evidence:** "No file" (upload next - see Scenario 3)
   - **Expected:** Credential visible with correct details

**Screenshots:** [Screenshot: Add Credential form with fields populated]

**Common Issues:**
- ❌ Problem: Expiry date auto-calculates incorrectly
  ✅ Solution: The auto-calculation uses the default validity period from the credential type. Override it manually if the actual certificate has a different expiry.

- ❌ Problem: "Duplicate credential" warning
  ✅ Solution: The employee may already have this credential type. Check existing credentials. If renewing, update the existing record or add a new one with the latest dates.

---

### Scenario 3: Upload Evidence (Certificate)

**When to use this:** You have a digital copy of the certificate to attach as proof

**Gherkin Scenario:**
```gherkin
Given Emma Murphy has a "Garda Vetting" credential without evidence
When I click "Upload Evidence" on her credential row
And I select a PDF file "emma-garda-vetting-2025.pdf"
And the file uploads successfully
Then the evidence is attached to the credential
And the evidence column shows a file icon with "View" link
```

**Steps:**

1. **Find the credential**
   - **Navigate:** Employees > Emma Murphy > Credentials tab
   - **Look for:** "Garda Vetting" row
   - **Expected:** Evidence column shows "No file" or upload icon

2. **Click Upload Evidence**
   - **Click:** Upload icon or "Upload" link in the evidence column
   - **Expected:** File picker dialog opens

3. **Select the file**
   - **Browse:** Find certificate file on your device
   - **Accepted formats:** PDF, JPG, JPEG, PNG (max 10 MB)
   - **Select:** "emma-garda-vetting-2025.pdf"
   - **Expected:** File selected, name shown in dialog

4. **Upload the file**
   - **Click:** "Upload" or "Confirm" button
   - **Expected:** Upload progress bar appears briefly
   - **Expected:** Success toast "Evidence uploaded"

5. **Verify upload**
   - **Look for:** File icon in evidence column
   - **Hover:** Shows filename "emma-garda-vetting-2025.pdf"
   - **Click:** "View" link to preview the certificate
   - **Expected:** PDF opens in new tab or preview modal

6. **Replace evidence** (if needed)
   - **Click:** "Replace" or upload icon again
   - **Select:** New file
   - **Expected:** Previous file replaced with new one
   - **Note:** Previous version is kept in audit log

**Screenshots:** [Screenshot: Credential row with uploaded evidence file icon]

**Common Issues:**
- ❌ Problem: "File too large" error
  ✅ Solution: Maximum file size is 10 MB. Compress the PDF or reduce image resolution before uploading.

- ❌ Problem: Upload fails with network error
  ✅ Solution: Check your internet connection. Try a smaller file. If persistent, check that Supabase storage bucket has available space.

- ❌ Problem: Wrong file uploaded
  ✅ Solution: Click "Replace" to upload the correct file. The old file is archived but the active evidence is updated.

---

### Scenario 4: Check Expiry Dashboard

**When to use this:** Monthly review of upcoming credential renewals, or before a Tusla inspection

**Gherkin Scenario:**
```gherkin
Given today is 2026-01-15
And Emma Murphy's First Aid expires on 2026-03-15 (60 days)
And Lisa O'Brien's Fire Safety expires on 2026-02-14 (30 days)
When I navigate to the Expiry Dashboard
Then I see Lisa O'Brien flagged RED (30-day warning)
And I see Emma Murphy flagged AMBER (60-day warning)
And I see a summary card showing "2 credentials expiring soon"
```

**Steps:**

1. **Navigate to Expiry Dashboard**
   - **Click:** "Credentials" or "Compliance" in sidebar
   - **Click:** "Expiry Dashboard" tab
   - **Expected:** Dashboard loads with credential status overview

2. **View summary cards**
   - **Look for:** Top-level summary cards:
     - **Expired:** Count of credentials past expiry (RED)
     - **30-day warning:** Expiring within 30 days (RED)
     - **60-day warning:** Expiring within 60 days (AMBER)
     - **90-day warning:** Expiring within 90 days (YELLOW)
     - **Current:** Valid credentials with no warnings (GREEN)
   - **Expected:** Cards show counts and colors

3. **Review the warning list**
   - **Look for:** Table sorted by urgency (expired first, then 30-day, etc.)
   - **Columns:**
     - **Employee:** Name
     - **Credential:** Type
     - **Expiry Date:** When it expires
     - **Days Remaining:** Countdown
     - **Status:** Color-coded badge (RED/AMBER/YELLOW/GREEN)
   - **Expected:** Lisa O'Brien shows RED, Emma Murphy shows AMBER

4. **Filter by warning level** (optional)
   - **Click:** "30-day" card to filter to urgent only
   - **Expected:** List shows only credentials expiring within 30 days

5. **Take action**
   - **Click:** Employee name to go to their credential page
   - **Action:** Contact employee to renew credential
   - **Update:** Add new credential with renewed dates once obtained
   - **Expected:** Warning clears after renewal is recorded

6. **Set up email reminders** (optional)
   - **Click:** Settings > Notifications > Credential Expiry
   - **Enable:** Automatic email reminders at 90, 60, 30 days
   - **Expected:** System sends reminders automatically

**Screenshots:** [Screenshot: Expiry Dashboard with summary cards and warning list]

**Common Issues:**
- ❌ Problem: Dashboard shows "No credentials found"
  ✅ Solution: Credentials must be added to employee profiles first. The dashboard aggregates across all employees. Add credentials (Scenario 2) before checking the dashboard.

- ❌ Problem: Expired credential not showing as RED
  ✅ Solution: Verify the expiry date is correct on the credential. Check that the credential type has warning thresholds enabled. Refresh the page.

---

### Scenario 5: View Qualification Status (Team-Wide)

**When to use this:** Pre-inspection review to verify all staff meet minimum qualification requirements

**Gherkin Scenario:**
```gherkin
Given my facility has 10 employees
And Tusla requires all staff to have Garda Vetting and First Aid
When I navigate to Qualification Status
Then I see a matrix of employees vs required credential types
And I see green checkmarks for valid credentials
And I see red X marks for missing or expired credentials
And a summary shows "8/10 fully compliant"
```

**Steps:**

1. **Navigate to Qualification Status**
   - **Click:** "Credentials" or "Compliance" in sidebar
   - **Click:** "Qualification Status" tab
   - **Expected:** Qualification matrix loads

2. **View the compliance matrix**
   - **Layout:** Rows = employees, Columns = required credential types
   - **Cells:**
     - **Green checkmark:** Valid credential on file
     - **Amber clock:** Expiring within 90 days
     - **Red X:** Missing or expired credential
     - **Gray dash:** Not required for this employee's role
   - **Expected:** Matrix shows status for all employees

3. **Read the summary bar**
   - **Look for:** Top summary showing:
     - "8 of 10 employees fully compliant (80%)"
     - "2 employees have gaps"
   - **Expected:** Percentage and counts displayed

4. **Identify gaps**
   - **Filter:** Click a RED cell to see details
   - **Example:** Aoife O'Brien is missing "Fire Safety" credential
   - **Action needed:** Aoife must complete Fire Safety training
   - **Expected:** Gap details shown with recommended action

5. **Export for Tusla**
   - **Click:** "Export" button
   - **Format:** CSV or PDF
   - **Contents:** Full qualification matrix with dates, statuses, evidence references
   - **Expected:** File downloads for inspector presentation

6. **Track progress**
   - **Revisit:** After employees complete training and credentials are updated
   - **Expected:** Matrix updates, compliance percentage increases
   - **Goal:** 100% compliance across all required credential types

**Screenshots:** [Screenshot: Qualification status matrix with checkmarks and gaps]

**Common Issues:**
- ❌ Problem: Matrix shows all RED even though credentials exist
  ✅ Solution: Verify credential types marked as "Required" in Settings match the types added to employee profiles. Names must match exactly.

- ❌ Problem: An employee role doesn't need certain credentials
  ✅ Solution: Mark credentials as "not required" for specific roles in Settings > Credential Types > Role Applicability. Administrative staff may not need childcare-specific credentials.

---

## Troubleshooting

### Issue: Credential types dropdown empty
**Symptoms:** "Add Credential" form shows no types in dropdown
**Cause:** No credential types configured
**Solution:**
1. Go to Settings > Credential Types first (Scenario 1)
2. Add at least one credential type
3. Return to employee credentials and try again

---

### Issue: Evidence upload fails repeatedly
**Symptoms:** Upload progress starts but then shows error
**Cause:** File too large, unsupported format, or storage quota exceeded
**Solution:**
1. Check file size (max 10 MB)
2. Check file format (PDF, JPG, JPEG, PNG only)
3. Try compressing the file
4. Check organization storage quota in Settings
5. If all else fails, contact support

---

### Issue: Expiry warnings not triggering
**Symptoms:** Credential expires tomorrow but no warning emails received
**Cause:** Notification settings disabled or email not configured
**Solution:**
1. Check Settings > Notifications > Credential Expiry is enabled
2. Verify email addresses are correct for administrators
3. Check spam/junk folder for Timebreez notification emails
4. Verify credential has correct expiry date entered
5. Warning thresholds must be enabled on the credential type

---

### Issue: Qualification matrix shows wrong compliance percentage
**Symptoms:** Matrix says 80% but manual count shows different
**Cause:** Calculation includes expired credentials as non-compliant
**Solution:**
1. Expired credentials count as non-compliant (same as missing)
2. Renew expired credentials to increase the percentage
3. Check that "Required" flag is correct on credential types
4. Remove non-applicable credential types from required list for roles that do not need them

---

## Related Guides
- [Programs & Events](./06-programs-events.md)
- [Attendance & Presence](./09-attendance-presence.md)
- [Compliance Trail & Audit](./11-compliance-trail-audit.md)
- [Troubleshooting Guide](./08-troubleshooting.md)

## Need More Help?
- **Timebreez Support:** support@timebreez.com
- **Demo mode:** www.timebreez.com/login (explore credential management in the demo org)
- **Tusla guidance:** www.tusla.ie (Early Years Inspectorate)
- **Book a call:** Schedule a 15-min walkthrough of compliance tracking
