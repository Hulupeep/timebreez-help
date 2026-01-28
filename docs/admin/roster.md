---
layout: default
title: Roster Management
parent: Admin Guide
nav_order: 1
permalink: /docs/admin/roster/
---

# Roster Management
{: .fs-9 }

How to build, edit, and publish weekly schedules for your team.
{: .fs-6 .fw-300 }

---

## The Roster Builder

The Roster Builder is where you create and manage your weekly schedules. It shows all rooms as rows and days as columns, letting you see your entire week at a glance.

![Roster Builder Overview](../assets/images/placeholder.png)
*The Roster Builder showing a typical week with staff assigned to rooms*

---

## Building a New Roster

### Step 1: Select the Week

1. Go to **Roster** in the main navigation
2. Use the date picker to select the week you want to build
3. If this is a new week, you'll see an empty grid

{: .note }
You can build rosters up to 4 weeks in advance. Staff will receive their schedule via WhatsApp on the Sunday before the week starts.

### Step 2: Understand the Grid

The roster grid shows:

| Column | What It Shows |
|--------|---------------|
| **Room** | Each room in your centre (Baby Room, Toddlers, etc.) |
| **Day columns** | Monday through Friday (or your operating days) |
| **Staff cells** | Who is assigned to each room each day |
| **Coverage indicator** | Green = adequately staffed, Yellow = review needed, Red = understaffed |

### Step 3: Add Staff to Shifts

**Method 1: Click to Add**

1. Click on an empty cell (intersection of room and day)
2. A panel opens showing available staff
3. Click a staff member to add them
4. Set their shift times (or use the room's default)
5. Click **Save**

**Method 2: Drag and Drop**

1. From the staff panel on the right, drag a staff member
2. Drop them onto the desired room and day
3. Adjust shift times if needed

![Adding a Shift](../assets/images/placeholder.png)
*The shift assignment panel showing available staff and time selection*

### Step 4: Set Shift Times

When adding or editing a shift:

1. **Start time**: When the shift begins (e.g., 8:30 AM)
2. **End time**: When the shift ends (e.g., 4:30 PM)
3. **Break duration**: Unpaid break time (e.g., 30 minutes)

{: .important }
Shift times are important for payroll calculations and morning reminders. Make sure they're accurate.

### Step 5: Check for Gaps

Timebreez highlights potential issues:

- **Red cells**: Room is understaffed for that day
- **Yellow warning icon**: Staff member has a conflict (e.g., leave approved)
- **Grey cells**: Days outside your operating hours

---

## Working with Approved Leave

When building the roster, you'll see approved leave displayed:

- Staff on leave appear greyed out in the available list
- Their leave dates show a badge: "AL" (Annual Leave) or "SICK"
- Hovering shows the leave details

### Example

If Mary has approved leave on Wednesday:

```
             MON    TUE    WED    THU    FRI
Baby Room   Mary   Mary    -     Mary   Mary
                          ⚠️ Mary is on Annual Leave
```

{: .warning }
Don't assign staff to shifts on days they have approved leave. Timebreez will warn you, but the system will prevent this conflict.

---

## Handling Coverage

### Understanding Ratios

Each room has a capacity and typical ratio requirement:

- **Baby Room**: 1:3 (one staff per three babies)
- **Toddlers**: 1:5 (one staff per five toddlers)
- **Preschool**: 1:8 (one staff per eight children)

Timebreez shows you at a glance whether each room appears adequately staffed.

{: .note }
These coverage indicators are for planning guidance only. Official compliance tracking should continue in your compliance system (like TeachKloud).

### Handling Gaps

When a room shows as understaffed:

1. Check if there's staff available to cover
2. Consider if someone can split their time between rooms
3. If no coverage is available, you may need to arrange a replacement or adjust capacity

---

## Editing Existing Shifts

### To Change Shift Times

1. Click on the staff member's name in the roster grid
2. The shift details panel opens
3. Adjust start time, end time, or break
4. Click **Save**

### To Move a Shift

1. Drag the staff member from one cell to another
2. Confirm the move
3. Times will carry over unless you edit them

### To Remove a Shift

1. Click on the staff member's name
2. Click **Remove from Roster**
3. Confirm the removal

---

## Copying Rosters

If your schedule is similar week to week:

### Copy from Previous Week

1. Navigate to the week you want to build
2. Click **Copy from...** at the top of the roster
3. Select the source week
4. Review the copied roster
5. Make adjustments as needed (accounting for leave, etc.)

### Save as Template

For rosters you use regularly:

1. Build your ideal roster
2. Click **Save as Template**
3. Give it a name (e.g., "Standard Week")
4. Apply this template to future weeks

{: .note }
Templates copy the structure (who works where) but you'll still need to adjust for leave and specific dates.

---

## Publishing the Roster

### Draft vs Published

- **Draft**: You're still working on it; staff cannot see it yet
- **Published**: Final; staff will receive notifications

### How to Publish

1. Review your roster for completeness
2. Click **Publish Roster** at the top
3. Choose notification options:
   - Send WhatsApp notifications now
   - Send with Sunday evening batch
4. Confirm publication

{: .important }
Once published, changes will trigger update notifications to affected staff. Try to finalise the roster before publishing.

### What Happens When You Publish

1. The roster status changes to "Published"
2. Staff can see their shifts in My Schedule
3. WhatsApp notifications are queued (based on your setting)
4. Morning reminders are scheduled

---

## Making Changes After Publishing

Sometimes you need to make changes after publishing:

### Minor Changes

1. Make the edit as normal
2. System automatically notifies affected staff
3. Staff receive: "Your shift on [day] has been updated"

### Major Changes

For significant changes (cancelling shifts, major time changes):

1. Consider contacting staff directly first
2. Make the changes in the roster
3. Add a note explaining the change
4. Staff will receive automatic notification

---

## Viewing the Roster

### Different Views

| View | Best For |
|------|----------|
| **By Room** | See all staff in each room (default view) |
| **By Staff** | See one person's full week |
| **Day View** | See all rooms and staff for a single day |

### Filtering

Use the filter options to:

- Show only certain rooms
- Show only certain staff
- Hide published/draft rosters

---

## Roster Reports

### Coverage Report

Shows staffing levels across the week:

1. Go to **Roster > Reports > Coverage**
2. Select the week
3. See each room's staffing level by day
4. Export to PDF if needed

### Hours Summary

Shows total hours scheduled:

1. Go to **Roster > Reports > Hours**
2. Select the date range
3. See scheduled hours per employee
4. Compare with contracted hours

---

## Common Issues

### "Staff member unavailable"

This means they have approved leave for that date. Check the leave calendar and assign someone else.

### "Overlapping shifts"

A staff member is already rostered elsewhere at that time. Choose one location or adjust times.

### "Room understaffed"

Add more staff to meet your coverage requirements. Check who's available in the staff panel.

### Changes not appearing for staff

Make sure the roster is **Published**, not still in Draft mode.

---

## Tips for Efficient Rostering

1. **Build a week ahead**: Give yourself time to handle leave requests
2. **Check leave first**: Review approved leave before starting
3. **Use templates**: If your weeks are similar, templates save time
4. **Publish early**: Staff appreciate knowing their schedule in advance
5. **Communicate big changes**: For major changes, a personal message helps

---

## Next Steps

[Leave Management](/docs/admin/leave/){: .btn .btn-primary .mr-2 }
[WhatsApp Setup](/docs/admin/whatsapp/){: .btn }
