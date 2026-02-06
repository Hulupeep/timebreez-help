# Credential Expiry Dashboard - Managing Staff Credentials

## Who This Is For
**Childcare Managers and HR Administrators** who need to track staff credential expirations (Garda vetting, first aid, manual handling, etc.) and take action before they lapse.

## What You'll Learn
- What the Credential Expiry Dashboard shows
- Understanding the traffic light countdown (30/60/90 day warnings)
- Expanding categories to see individual credentials
- Taking action on expiring credentials
- Notifying staff about upcoming renewals

## Prerequisites
- Manager or Admin role in Timebreez
- Employees with credentials entered (via Employee Profile > Credentials)
- At least one credential with an expiry date set

---

## Quick Start (TL;DR)

1. Go to **Dashboard** or **Employees > Credential Expiry**
2. View the **traffic light summary** (RED/AMBER/GREEN counts)
3. RED = expires within 30 days, AMBER = 30-60 days, GREEN = 60-90 days
4. Click a **category card** to expand and see individual credentials
5. Click **"Notify"** to send a renewal reminder to the staff member
6. Track renewals until credentials are updated

---

## Understanding the Credential Expiry Dashboard

### What Does It Show?

The Credential Expiry Dashboard gives you a **single-screen overview** of all staff credentials approaching expiration. It answers three questions:

1. **How many credentials are expiring soon?** (summary counts)
2. **Which credentials are they?** (individual entries)
3. **Who needs to act?** (staff members requiring renewal)

### Credential Types Tracked

| Credential | Typical Validity | Renewal Process |
|-----------|-----------------|-----------------|
| **Garda Vetting** | 3 years | Reapply through employer |
| **First Aid Certificate** | 2 years | Attend refresher course |
| **Manual Handling** | 3 years | Attend refresher course |
| **Child Protection Training** | 2 years | Tusla eLearning module |
| **FETAC/QQI Level 5/6** | No expiry (qualification) | Not tracked for expiry |
| **Food Safety (HACCP)** | 3 years | Attend refresher course |
| **Fire Safety Certificate** | 1 year | Annual training required |

### The Traffic Light System

| Color | Time Until Expiry | Urgency | Action Required |
|-------|------------------|---------|----------------|
| **RED** | 0-30 days | Critical | Immediate action - credential expires this month |
| **AMBER** | 31-60 days | Warning | Plan renewal - schedule training or application |
| **GREEN** | 61-90 days | Awareness | Upcoming - add to next month's planning |
| **No color** | 90+ days | Safe | No action needed, credential is current |

**Expired credentials** (past expiry date) appear in a separate **EXPIRED** section with a dark red indicator.

---

## Step-by-Step Guides

### Scenario 1: Check the Credential Expiry Dashboard

**When to use this:** Start of week, monthly compliance review, or before a Tusla inspection

**Gherkin Scenario:**
```gherkin
Given I am logged in as a manager
When I navigate to the Credential Expiry Dashboard
Then I see traffic light summary cards showing:
  - RED count (expiring within 30 days)
  - AMBER count (expiring within 31-60 days)
  - GREEN count (expiring within 61-90 days)
And each card shows the number of credentials in that category
```

**Steps:**

1. **Navigate to the Credential Expiry Dashboard**
   - **Option A:** Click "Dashboard" in sidebar, then find the "Credential Expiry" widget
   - **Option B:** Click "Employees" > "Credential Expiry" in the sidebar
   - **Expected:** Dashboard loads with traffic light summary

2. **Read the traffic light summary**
   - **Look for:** Three colored summary cards at the top of the page
   - **RED card:** Shows count of credentials expiring within 30 days
     - Example: "3 credentials expiring within 30 days"
   - **AMBER card:** Shows count expiring within 31-60 days
     - Example: "5 credentials expiring within 60 days"
   - **GREEN card:** Shows count expiring within 61-90 days
     - Example: "2 credentials expiring within 90 days"
   - **Expected:** All three cards visible with counts

3. **Check the total overview**
   - **Look for:** Total credentials tracked (e.g., "42 credentials tracked across 10 employees")
   - **Look for:** Compliance percentage (e.g., "92% current, 8% expiring soon")
   - **Expected:** Summary statistics visible

4. **Identify the most urgent items**
   - **Focus on:** RED card count first
   - **If RED count > 0:** These need immediate attention
   - **If RED count = 0:** Check AMBER for upcoming renewals to plan
   - **Expected:** Clear priority ordering

**Screenshots:** [Screenshot: Credential Expiry Dashboard with traffic light cards]

**Common Issues:**
- Problem: Dashboard shows 0 for all counts
  Solution: No credentials have expiry dates within 90 days. This is good - all credentials are current. Alternatively, verify that employees have credentials entered (Employees > [Employee] > Credentials).

- Problem: Dashboard shows "No credentials found"
  Solution: No employees have credentials entered. Go to Employees, select an employee, and add their credentials with expiry dates.

---

### Scenario 2: Identify Expiring Credentials by Category

**When to use this:** Drill into a traffic light category to see which specific credentials are expiring

**Gherkin Scenario:**
```gherkin
Given the RED card shows "3 credentials expiring within 30 days"
When I click the RED card
Then it expands to show the 3 individual credentials:
  - Emma Murphy - First Aid Certificate (expires Jan 28)
  - Lisa O'Brien - Garda Vetting (expires Feb 5)
  - Aoife O'Brien - Manual Handling (expires Feb 12)
And each entry shows employee name, credential type, and expiry date
```

**Steps:**

1. **Click a traffic light card to expand**
   - **Click:** The RED card (or AMBER or GREEN)
   - **Expected:** Card expands to show individual credential entries

2. **Review individual entries**
   - **Each entry shows:**
     - **Employee Name:** Emma Murphy
     - **Credential Type:** First Aid Certificate
     - **Expiry Date:** 28 January 2026
     - **Days Until Expiry:** 5 days
     - **Status Badge:** RED (critical)
   - **Expected:** All credentials in that category listed

3. **Sort the entries** (if available)
   - **Default sort:** By expiry date (soonest first)
   - **Alternative:** Sort by employee name or credential type
   - **Expected:** Most urgent entries at the top

4. **View credential details**
   - **Click:** An individual credential entry
   - **Expected:** Detail panel shows:
     - Full credential name and issuing body
     - Original issue date
     - Expiry date
     - Renewal instructions or notes
     - Employee contact information

5. **Repeat for other categories**
   - **Click:** AMBER card to see 31-60 day credentials
   - **Click:** GREEN card to see 61-90 day credentials
   - **Expected:** Each category shows its own list of credentials

**Screenshots:** [Screenshot: Expanded RED category showing individual expiring credentials]

**Common Issues:**
- Problem: Clicking the card doesn't expand
  Solution: Try clicking the count number or the "View Details" link on the card. Some layouts use an expand arrow icon on the right side of the card.

- Problem: A credential shows wrong expiry date
  Solution: The expiry date is set on the employee's credential record. Go to Employees > [Employee Name] > Credentials and update the expiry date.

---

### Scenario 3: Notify Staff About Upcoming Renewals

**When to use this:** Send a reminder to a staff member that their credential is expiring and needs renewal

**Gherkin Scenario:**
```gherkin
Given Emma Murphy's First Aid Certificate expires in 5 days
When I view her entry on the Credential Expiry Dashboard
And I click "Notify" next to her credential
Then a notification is sent to Emma (via email or WhatsApp)
And the notification includes the credential type, expiry date, and renewal instructions
And the credential entry shows "Notified on [date]"
```

**Steps:**

1. **Find the credential entry to notify about**
   - **Expand:** The appropriate traffic light card (e.g., RED)
   - **Find:** Emma Murphy - First Aid Certificate
   - **Expected:** Entry visible with action buttons

2. **Click "Notify" button**
   - **Look for:** "Notify" or "Send Reminder" button next to the credential entry
   - **Click:** The Notify button
   - **Expected:** Notification dialog opens

3. **Configure the notification**
   - **Recipient:** Emma Murphy (pre-filled)
   - **Channel:** Select delivery method:
     - **Email** - Sends to employee's email address
     - **WhatsApp** - Sends via WhatsApp Business API (if configured)
     - **Both** - Sends via both channels
   - **Message:** Pre-populated template:
     - "Hi Emma, your First Aid Certificate expires on 28 January 2026. Please arrange renewal before this date. Contact HR if you need assistance."
   - **Edit:** Customize the message if needed
   - **Expected:** Notification ready to send

4. **Send the notification**
   - **Click:** "Send" button
   - **Expected:** Success toast "Reminder sent to Emma Murphy"

5. **Verify notification status**
   - **Look for:** "Notified" badge on the credential entry
   - **Date:** Shows when the notification was sent (e.g., "Notified 23 Jan 2026")
   - **Expected:** Badge confirms notification was sent

6. **Follow up if no action taken**
   - **Check back:** In 7 days, if credential still expiring
   - **Re-notify:** Click "Notify" again to send a follow-up reminder
   - **Expected:** Multiple notifications can be sent for the same credential

**Screenshots:** [Screenshot: Notify dialog with email/WhatsApp options]

**Common Issues:**
- Problem: "Notify" button is grayed out
  Solution: The employee may not have an email address or phone number on file. Go to Employees > [Employee] and add their contact details.

- Problem: WhatsApp notification fails
  Solution: WhatsApp Business API integration must be configured (see Settings > WhatsApp). If not configured, use email notifications instead.

- Problem: Employee says they didn't receive the notification
  Solution: Check the notification log (Settings > Notifications > Sent). Verify the email/phone number is correct. Check spam folders for email notifications.

---

### Scenario 4: Track Credential Renewals

**When to use this:** Staff has renewed a credential and you need to update the record

**Gherkin Scenario:**
```gherkin
Given Emma Murphy has completed her First Aid refresher course
And she provides her new certificate (valid until Jan 2028)
When I go to her employee profile
And I update the First Aid Certificate expiry date to January 2028
And I save
Then the credential disappears from the RED expiry list
And the Credential Expiry Dashboard counts update
```

**Steps:**

1. **Receive proof of renewal**
   - **Example:** Emma provides a scanned copy of her new First Aid certificate
   - **Verify:** New expiry date (e.g., 28 January 2028)
   - **Expected:** Valid proof of renewal

2. **Navigate to the employee's credential record**
   - **Option A:** Click the employee name on the Expiry Dashboard entry
   - **Option B:** Go to Employees > Emma Murphy > Credentials
   - **Expected:** Employee credential page loads

3. **Update the credential expiry date**
   - **Find:** First Aid Certificate entry
   - **Click:** "Edit" or pencil icon
   - **Update Expiry Date:** Change to 28 January 2028
   - **Upload:** Attach scanned certificate (if upload feature available)
   - **Notes:** "Renewed - refresher course completed 20 Jan 2026"
   - **Expected:** Form updated with new date

4. **Save the update**
   - **Click:** "Save" button
   - **Expected:** Success toast "Credential updated"

5. **Verify the Expiry Dashboard updated**
   - **Navigate back:** Credential Expiry Dashboard
   - **Expected:**
     - RED count decreased by 1
     - Emma's First Aid Certificate no longer appears in RED category
     - Credential now has 90+ days until expiry (not shown on dashboard)
   - **Expected:** Dashboard reflects the renewal

**Screenshots:** [Screenshot: Employee credential edit form with updated expiry date]

**Common Issues:**
- Problem: Updated credential still shows in expiry list
  Solution: Refresh the Credential Expiry Dashboard page. The update should reflect immediately. If not, verify the new expiry date was saved correctly on the employee profile.

- Problem: Cannot upload certificate scan
  Solution: File upload may not be available for all credential types. Save the scan locally and reference it in the Notes field. File upload support may be added in a future update.

---

## Troubleshooting

### Issue: Credential Expiry Dashboard not visible
**Symptoms:** Cannot find the dashboard in navigation or on the main Dashboard page
**Cause:** Feature may require specific role or subscription tier
**Solution:**
1. Verify you have Manager or Admin role
2. Check if the widget is on the main Dashboard page (may be a collapsible section)
3. Check Employees section for a "Credential Expiry" submenu
4. If not found, the feature may not be enabled for your organization - contact support

---

### Issue: Expiry dates are wrong
**Symptoms:** Credential shows as expiring but the actual certificate is still valid
**Cause:** Expiry date was entered incorrectly when the credential was added
**Solution:**
1. Go to Employees > [Employee Name] > Credentials
2. Find the credential with the wrong date
3. Click Edit and correct the expiry date
4. Save - the dashboard will update immediately

---

### Issue: Expired credentials not showing
**Symptoms:** Know a credential is expired but it doesn't appear on the dashboard
**Cause:** Credential may not have an expiry date entered, or may be in a separate "Expired" section
**Solution:**
1. Check for an "Expired" tab or section on the dashboard (separate from the traffic light)
2. Verify the credential has an expiry date set on the employee profile
3. Credentials without expiry dates (e.g., qualifications) are not tracked for expiry

---

### Issue: Notification not received by staff
**Symptoms:** Clicked "Notify" but employee says they didn't get the reminder
**Cause:** Email delivery issue, wrong contact details, or WhatsApp not configured
**Solution:**
1. Check the employee's email address is correct (Employees > [Employee] > Contact)
2. Ask the employee to check spam/junk folder
3. Check Settings > Notifications > Sent Log for delivery status
4. If using WhatsApp, verify WhatsApp integration is active (Settings > WhatsApp)
5. Try resending the notification

---

### Issue: Traffic light counts don't add up
**Symptoms:** Individual entries in a category don't match the count on the card
**Cause:** Credentials may have been updated between page load and card expansion
**Solution:**
1. Refresh the entire page to get current counts
2. The counts are calculated in real-time - updates by other admins may change them
3. If consistently wrong, report as a bug with screenshots

---

### Issue: Cannot edit credential expiry date
**Symptoms:** Edit button is disabled or expiry date field is read-only
**Cause:** Insufficient permissions or credential type configured as non-editable
**Solution:**
1. Verify you have Admin role (Managers may have read-only access to credentials)
2. Some credential types (e.g., Garda Vetting) may require admin override to edit
3. Contact your organization admin if permissions are insufficient

---

## Related Guides
- [Demo Mode - Getting Started](./01-demo-mode-onboarding.md)
- [Control Desk Operations](./05-control-desk-operations.md)
- [Daily Reconciliation](./04-daily-reconciliation.md)
- [Troubleshooting Guide](./08-troubleshooting.md)

## Need More Help?
- **Timebreez Support:** support@timebreez.com
- **Demo mode:** www.timebreez.com/login (demo org includes sample credentials with various expiry dates)
- **Book a call:** Schedule a 15-min walkthrough of credential management
- **Tusla compliance:** help.timebreez.com/compliance for regulatory guidance
