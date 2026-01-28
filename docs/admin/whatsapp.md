---
layout: default
title: WhatsApp Setup
parent: Admin Guide
nav_order: 3
permalink: /docs/admin/whatsapp/
---

# WhatsApp Setup Guide
{: .fs-9 }

How to configure WhatsApp notifications for your staff.
{: .fs-6 .fw-300 }

---

## Overview

WhatsApp is the primary way Timebreez communicates with your staff. Through WhatsApp, staff receive:

- Weekly schedule summaries
- Morning shift reminders
- Leave approval/denial notifications
- No-show alerts
- Schedule change notifications

Staff can also:

- Request leave by messaging
- Check their balance
- View their schedule

{: .note }
WhatsApp is used because it's already on everyone's phones, requires no app download, and messages actually get read.

---

## Setting Up WhatsApp for Your Centre

### Requirements

Before you begin, you'll need:

1. **Meta Business Account** - Your business account with Meta (Facebook's parent company)
2. **WhatsApp Business API Access** - Through the Meta Business platform
3. **Verified Phone Number** - A phone number dedicated to your Timebreez messages
4. **Approved Message Templates** - Pre-approved by Meta (we provide these)

{: .important }
WhatsApp Business API setup requires approval from Meta. Allow 1-2 weeks for the verification process.

### Step 1: Create a Meta Business Account

If you don't already have one:

1. Go to [business.facebook.com](https://business.facebook.com)
2. Click **Create Account**
3. Enter your business details:
   - Business name (your centre's name)
   - Your name and email
   - Business address
4. Verify your account via email

### Step 2: Apply for WhatsApp Business API

1. In Meta Business Suite, go to **Settings > Business Settings**
2. Click **WhatsApp Accounts**
3. Click **Add WhatsApp Account**
4. Follow the prompts to:
   - Provide business verification documents
   - Link a phone number
   - Accept terms and conditions

### Step 3: Verify Your Business

Meta requires business verification to use the WhatsApp Business API:

1. Upload business documents (registration certificate, utility bill, etc.)
2. Wait for Meta review (usually 1-7 days)
3. You'll receive email confirmation when approved

### Step 4: Connect to Timebreez

Once your WhatsApp Business API is ready:

1. In Timebreez, go to **Settings > Integrations > WhatsApp**
2. Click **Connect WhatsApp**
3. Enter your:
   - WhatsApp Business Account ID
   - Phone Number ID
   - Access Token
4. Click **Verify Connection**
5. Send a test message to confirm it's working

![WhatsApp Settings](../assets/images/placeholder.png)
*The WhatsApp integration settings screen*

---

## Message Templates

WhatsApp Business API requires pre-approved message templates for outgoing messages. Timebreez includes standard templates that work for most centres.

### Included Templates

| Template | Purpose | Example |
|----------|---------|---------|
| **shift_reminder** | Morning reminders | "Good morning! You're on at 8:30 today in Baby Room..." |
| **weekly_schedule** | Sunday schedule push | "Here's your week ahead..." |
| **no_show_alert** | When staff hasn't clocked in | "You were due at 8:30 but we don't see you clocked in..." |
| **leave_approved** | When leave is approved | "Good news! Your time off has been approved..." |
| **leave_denied** | When leave is denied | "Unfortunately your leave request couldn't be approved..." |
| **schedule_changed** | When roster is updated | "Your shift on Thursday has been updated..." |

### Submitting Templates for Approval

Templates must be approved by Meta before use:

1. Go to **Settings > WhatsApp > Templates**
2. Review the default templates
3. Click **Submit for Approval**
4. Wait for Meta review (usually 24-48 hours)
5. Status will change to "Approved" when ready

{: .warning }
Don't modify templates without resubmitting for approval. Unapproved templates won't work.

### Custom Templates

If you need custom message wording:

1. Go to **Settings > WhatsApp > Templates**
2. Click **Create Custom Template**
3. Choose a category (Utility, Marketing, Authentication)
4. Write your template with placeholders:
   ```
   Good morning {{1}}! You're on at {{2}} today in {{3}}.
   ```
5. Submit for Meta approval

---

## Configuring Staff for WhatsApp

### Adding Phone Numbers

For each staff member:

1. Go to **Staff > All Staff**
2. Click on the employee
3. Ensure **Phone (WhatsApp)** is filled in
4. Use international format: +353 87 123 4567

{: .important }
The phone number must be able to receive WhatsApp messages. Staff should have WhatsApp installed on this number.

### Enabling Notifications

For each staff member, you can control which notifications they receive:

1. Go to the employee's profile
2. Click **Notification Preferences**
3. Enable/disable:
   - Weekly schedule push
   - Morning reminders
   - Leave notifications
   - Schedule changes

### Bulk Enabling

To turn on WhatsApp for everyone:

1. Go to **Settings > WhatsApp > Staff Settings**
2. Click **Enable for All Staff**
3. Review the list
4. Confirm

---

## Notification Settings

### Timing Configuration

Configure when notifications are sent:

| Setting | Description | Default |
|---------|-------------|---------|
| **Weekly Schedule Day** | Which day to send the weekly summary | Sunday |
| **Weekly Schedule Time** | What time on that day | 6:00 PM |
| **Morning Reminder Time** | When to send shift reminders | 7:00 AM |
| **Reminder Window** | How far before shift start | 1.5 hours |

To change these:

1. Go to **Settings > WhatsApp > Timing**
2. Adjust the times
3. Click **Save**

### No-Show Alert Timing

Configure when no-show alerts are sent:

| Setting | Description | Default |
|---------|-------------|---------|
| **Grace Period** | How long after shift start before alerting | 15 minutes |
| **Alert Staff** | Send alert to the missing staff member | Yes |
| **Alert Manager** | Send alert to administrator | Yes |

---

## Testing Your Setup

### Sending a Test Message

Before going live:

1. Go to **Settings > WhatsApp > Test**
2. Enter your own phone number
3. Select a template to test
4. Click **Send Test**
5. Verify you receive the message

### Testing with a Single Employee

Start with one employee before rolling out:

1. Choose a tech-savvy staff member
2. Enable WhatsApp notifications for them only
3. Publish a roster
4. Confirm they receive their schedule
5. Collect feedback

---

## Understanding Costs

WhatsApp Business API has per-message costs:

### Pricing Structure

| Category | Description | Approximate Cost |
|----------|-------------|------------------|
| **Utility** | Shift reminders, schedule updates | ~EUR 0.02-0.03/message |
| **Service** | Staff-initiated (balance queries, etc.) | FREE |
| **Marketing** | Promotional (not used by Timebreez) | Higher rates |

### Monthly Cost Estimate

For a centre with ~40 staff:

| Message Type | Volume/Month | Cost |
|--------------|--------------|------|
| Morning reminders | 40 × 22 days = 880 | ~EUR 22 |
| Weekly schedules | 40 × 4 weeks = 160 | ~EUR 4 |
| No-show alerts | ~110 | ~EUR 3 |
| Leave notifications | ~20 | ~EUR 0.50 |
| **Total** | | **~EUR 30/month** |

{: .note }
Staff-initiated messages (checking balance, requesting leave) are free under the Service category.

---

## Handling Staff Responses

### Automatic Response Handling

Timebreez automatically handles common staff responses:

| Staff Sends | System Action |
|-------------|---------------|
| "SICK" (to no-show alert) | Marks them as sick for the day, notifies manager |
| "LATE" (to no-show alert) | Logs that they're running late |
| "balance" | Sends their leave balance |
| "schedule" | Sends their upcoming shifts |
| Leave request | Creates pending leave request |

### Manual Review

Some responses may need your attention:

1. Check **Dashboard > WhatsApp Inbox** regularly
2. Review any unhandled messages
3. Respond or take action as needed

---

## Troubleshooting WhatsApp

### Staff Not Receiving Messages

1. **Check phone number** - Is it correct and in international format?
2. **Check WhatsApp status** - Is WhatsApp installed and working?
3. **Check notification settings** - Are notifications enabled for this staff member?
4. **Check message delivery** - Go to **WhatsApp > Delivery Log** to see status

### Message Delivery Status

| Status | Meaning |
|--------|---------|
| **Sent** | Message sent to WhatsApp servers |
| **Delivered** | Message reached the user's phone |
| **Read** | User opened the message |
| **Failed** | Delivery failed (check error message) |

### Common Errors

| Error | Solution |
|-------|----------|
| "Phone number not on WhatsApp" | User needs to install WhatsApp or number is wrong |
| "Template not approved" | Wait for Meta approval or use approved template |
| "Rate limited" | Slow down sending; try again later |
| "Invalid phone format" | Use international format with country code |

---

## Best Practices

### For Better Delivery Rates

1. **Verify phone numbers** when adding staff
2. **Ask staff to save the number** as a contact
3. **Send during appropriate hours** (not middle of night)
4. **Keep messages concise** and useful

### For Staff Adoption

1. **Explain the benefits** - "You'll know your schedule before Sunday night"
2. **Demonstrate how to respond** - Show them the SICK, balance commands
3. **Be responsive** - Act on their messages quickly
4. **Respect preferences** - Turn off optional notifications if asked

### For Cost Management

1. **Avoid unnecessary messages** - Only send what's useful
2. **Batch where possible** - Weekly schedule vs. daily schedule
3. **Monitor usage** - Check **Settings > WhatsApp > Usage** monthly

---

## Privacy and Compliance

### Data Protection

- Phone numbers are stored securely
- Messages are encrypted in transit
- Timebreez doesn't store message content long-term
- Comply with your local data protection laws (GDPR in Ireland/EU)

### Staff Consent

Ensure you have:

1. Informed staff about WhatsApp notifications during onboarding
2. Documented consent in employment records
3. Provided opt-out option for non-essential notifications

### Retention

Message delivery logs are retained for 30 days for troubleshooting, then deleted.

---

## Need Help?

WhatsApp setup can be technical. We're here to help:

- **Email**: support@timebreez.com (include "WhatsApp setup" in subject)
- **Onboarding call**: Request a guided setup session

{: .note }
For new centres, Timebreez support can walk you through the entire WhatsApp setup process.

---

## Next Steps

[Back to Admin Guide](/docs/admin/){: .btn .btn-primary .mr-2 }
[Roster Management](/docs/admin/roster/){: .btn }
