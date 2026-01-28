---
layout: default
title: Leave Management
parent: Admin Guide
nav_order: 2
permalink: /docs/admin/leave/
---

# Leave Management
{: .fs-9 }

How to review, approve, and manage staff time-off requests.
{: .fs-6 .fw-300 }

---

## Overview

Timebreez handles leave requests from start to finish:

1. Staff request leave (via WhatsApp or the app)
2. You receive a notification
3. You review the request with full context
4. You approve or deny with one click
5. Staff get notified automatically
6. Balances update automatically

---

## Reviewing Leave Requests

### Accessing Pending Requests

1. Go to **Leave** in the main navigation
2. The **Pending** tab shows all requests waiting for your decision
3. You'll also see a badge on the Leave menu when requests are pending

![Pending Leave Requests](../assets/images/placeholder.png)
*The Leave Requests screen showing pending requests*

### Understanding the Request Details

Each request shows you everything you need to decide:

| Information | What It Shows |
|-------------|---------------|
| **Employee** | Who is requesting leave |
| **Dates** | Start and end date |
| **Duration** | Number of days (or hours for hourly staff) |
| **Leave Type** | Annual Leave, Sick Leave, Unpaid, etc. |
| **Current Balance** | Their remaining allowance |
| **Balance After** | What their balance will be if approved |
| **Schedule Impact** | Which rostered shifts are affected |
| **Requested** | When they submitted the request |

### Checking Schedule Impact

Before approving, review the schedule impact section:

```
SCHEDULE IMPACT

Wed 15 Jan: Baby Room 8:30-4:30 (8 hours)
    → Mary is scheduled for this shift
    → Will need cover

Thu 16 Jan: Baby Room 8:30-4:30 (8 hours)
    → Mary is scheduled for this shift
    → Will need cover
```

{: .important }
If the staff member has rostered shifts during their requested leave, you'll need to arrange cover before or after approving.

---

## Approving Leave

### Quick Approval

If everything looks good:

1. Click **Approve** on the request
2. The request is approved immediately
3. Staff receives a WhatsApp notification
4. Their balance is automatically deducted

### Approval with Notes

To add context to your decision:

1. Click the **...** menu on the request
2. Select **Approve with Note**
3. Add your message (e.g., "Approved - please remind Sarah about the handover")
4. Click **Confirm**
5. The note is saved with the request and included in the notification

---

## Denying Leave

### When to Deny

Common reasons for denial:

- Insufficient balance remaining
- Critical staffing period (e.g., inspection week)
- Too many staff already off that day
- Request doesn't comply with policy (e.g., minimum notice)

### How to Deny

1. Click **Deny** on the request
2. Select a reason or enter a custom explanation
3. Click **Confirm**
4. Staff receives notification with your reason

{: .note }
Always provide a clear reason when denying. Staff appreciate understanding why, and it may help them adjust their request.

### Suggested Alternatives

When denying, you can suggest alternative dates:

1. Click **Deny with Alternative**
2. Select dates that would work
3. Add any notes
4. Staff sees: "Your request for Jan 15-16 was denied (staffing shortage). Jan 20-21 would work if you'd like to resubmit."

---

## Understanding Leave Types

### Annual Leave

- **What it is**: Paid holiday entitlement
- **How it's tracked**: Days deducted from annual allowance
- **Typical allowance**: 20 days per year (varies by contract)

### Sick Leave

When a staff member is ill:

- **Logged by staff**: They reply "SICK" to a no-show alert, or contact you
- **Logged by admin**: You can add sick days directly
- **Balance impact**: Deducted from sick leave allowance (if you track this separately)

### Unpaid Leave

For time off beyond their allowance:

- **When used**: Staff has exhausted annual leave, or special circumstances
- **Balance impact**: No deduction (no pay for those days)
- **Payroll impact**: Marked as unpaid in export

### Other Leave Types

You can configure additional types in Settings:

- Compassionate Leave
- Parental Leave
- Training Days
- TOIL (Time Off In Lieu)

---

## Managing Leave Balances

### Viewing an Employee's Balance

1. Go to **Staff > All Staff**
2. Click on the employee
3. Go to the **Leave** tab
4. See their current balances and history

### Balance Details

For each leave type, you'll see:

| Field | Meaning |
|-------|---------|
| **Allowance** | Total days for the leave year |
| **Used** | Days already taken |
| **Pending** | Days requested but not yet decided |
| **Remaining** | Allowance minus Used |

### Adjusting Balances

Sometimes you need to manually adjust:

1. Go to the employee's Leave tab
2. Click **Adjust Balance**
3. Enter the adjustment (positive or negative)
4. Add a reason (required for audit)
5. Click **Save**

**Example adjustments:**

- +3 days: "Carried over from last year per contract"
- -1 day: "Correction - day logged twice"
- +5 days: "Service anniversary bonus"

{: .warning }
Manual adjustments should be rare. Use notes to document why you made them.

---

## The Leave Calendar (Wallchart)

### What It Shows

The wallchart gives you a visual overview of who's off when:

```
             JAN                              FEB
         27  28  29  30  31   1   2   3   4   5   6
Mary        [──AL──]                     [──AL──]
Sarah              [──AL──]
Jane                       [─SICK─]
Emma                                         [AL]
Lisa                                    Weekend
```

### Using the Wallchart

1. Go to **Leave > Calendar**
2. Select the date range
3. See all approved leave at a glance
4. Click on any entry for details

### Spotting Conflicts

The wallchart helps you see:

- Days when multiple people are off
- Coverage gaps before they happen
- Popular leave periods (holidays, school breaks)

{: .note }
When many staff request the same dates, consider first-come-first-served or rotation policies.

---

## Leave Policies and Settings

### Configuring Leave Policies

Go to **Settings > Leave Policies** to configure:

#### Notice Requirements

Set minimum notice for leave requests:

- Annual leave: e.g., 2 weeks notice
- Short notice allowed: e.g., up to 2 days per year

#### Blackout Dates

Block requests during critical periods:

1. Go to **Settings > Leave Policies > Blackout Dates**
2. Add dates (e.g., "December 20-31 - Holiday closure prep")
3. Staff see a warning when requesting these dates
4. You can still approve if truly necessary

#### Maximum Concurrent Leave

Limit how many staff can be off at once:

- Per room: e.g., max 1 person from Baby Room
- Centre-wide: e.g., max 3 staff total

---

## Processing Sick Leave

### When Staff Call In Sick

**Method 1: No-Show Alert Response**

If staff reply "SICK" to a no-show alert:

1. The system automatically creates a sick leave record
2. You receive a notification
3. You can add notes or adjust if needed

**Method 2: Staff Contacts You Directly**

If staff calls or messages you:

1. Go to **Leave > Add Leave**
2. Select the employee
3. Choose "Sick Leave"
4. Enter the date(s)
5. Add any notes
6. Click **Save**

### Tracking Patterns

The employee's leave history shows:

- Total sick days this year
- Dates of each sick day
- Any patterns (e.g., frequent Mondays)

---

## Leave Requests via WhatsApp

Staff can request leave by messaging:

**Staff sends:** "I need December 15-16 off"

**System responds:**
> Got it! Checking your balance... You have 18 days remaining.
>
> I'll send this to your manager for approval. You'll hear back soon.

**Manager sees:** New leave request with all details

**After approval:**
> Good news! Your time off has been approved.
>
> December 15-16 (2 days Annual Leave)
>
> You now have 16 days remaining this year.

---

## Common Scenarios

### Staff Requests More Days Than They Have

1. The request shows "Insufficient balance" warning
2. You can:
   - Deny with explanation
   - Partially approve (fewer days)
   - Approve as unpaid leave
   - Adjust their balance first (if appropriate)

### Staff Is Already Rostered

1. The request shows schedule impact
2. Before approving, ensure cover is arranged
3. After approval, update the roster

### Cancelling Approved Leave

If staff no longer needs their approved leave:

1. Go to **Leave > Approved**
2. Find the request
3. Click **Cancel Leave**
4. Choose to:
   - Restore balance (they changed their mind)
   - Keep deducted (administrative correction)

### Last-Minute Requests

If someone requests leave for tomorrow or today:

1. The request is flagged as "Short notice"
2. Review against your policy
3. Decide based on circumstances and coverage

---

## Reports

### Leave Summary Report

Shows leave usage across your team:

1. Go to **Leave > Reports > Summary**
2. Select date range
3. See: Total days taken, by employee, by type
4. Export to PDF or CSV

### Balance Report

Shows current balances for all staff:

1. Go to **Leave > Reports > Balances**
2. See: Allowance, used, remaining for each person
3. Good for leave year renewals

---

## Tips for Effective Leave Management

1. **Respond quickly**: Staff appreciate knowing their plans are confirmed
2. **Be consistent**: Apply policies fairly to everyone
3. **Plan ahead**: Encourage early requests for holidays
4. **Communicate**: If you deny, explain why and suggest alternatives
5. **Review balances**: Before leave year ends, remind staff of remaining days

---

## Next Steps

[Roster Management](/docs/admin/roster/){: .btn .btn-primary .mr-2 }
[WhatsApp Setup](/docs/admin/whatsapp/){: .btn }
