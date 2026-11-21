---
layout: default
title: Payroll
parent: Page by page
nav_order: 8
permalink: /docs/app/payroll/
---

# Payroll

**Who uses it:** admins. In the menu: **Payroll**.

## What it does

Shows, for one pay period, each person's hours and leave, lists the exceptions to resolve, and lets you download the figures. Gross pay is only worked out if you choose it in [Settings]({{ site.baseurl }}/docs/app/settings/), **Gross pay in the payroll file**, and never for salaried staff.

## Breaks and public holidays

A box above the table says how breaks and public holidays are paid this period, from your settings (**Breaks in paid hours** and **Public holidays in the payroll file**):

- With a break rule, it reads for example "Breaks: Over 6h00 worked: 45 min. Unpaid: taken off paid hours." An unpaid break comes off hours worked. Scheduled hours stay as rostered.
- With no break rule: "each shift is paid from start to end".
- If a public holiday falls in the period, it is named, with how it is paid. With no rule set, this line is amber and the file has no bank holiday hours.
- Anyone with no confirmed working week is named, with no bank holiday hours: their weekly hours are unknown, so nothing is guessed.

**Example.** The rule is weekly contracted hours divided by 5. Mary Murphy is contracted 30 hours a week, so a public holiday in the period puts 6 bank holiday hours on her line, paid.

## When a period is a draft

An amber banner at the top says why the period is a draft. You will see one of these:

| Banner | What it means |
|---|---|
| Draft, not for payroll: this organisation has no pay basis set. | Timebreez does not know whether pay follows the roster or a clock |
| Draft, not for payroll: N hours have no complete clock-in and clock-out record. | Some shifts are missing a clock-in or clock-out |
| Draft, not for payroll: these are rostered hours, not hours anyone measured. | Pay follows the roster. Check every line |
| Draft, not for payroll: N leave days are priced from the working week, not a recorded calculation. | Hours are measured, but some leave days have no recorded calculation. Check those leave lines |

While a period is a draft, **Certify & Export** is switched off. Use **Download draft CSV** to get the figures and check them against your payroll system. A clock-based period where every leave day has a recorded calculation is not a draft.

## Leave lines

Every day of approved leave in the period gets a leave line, even when the person had no shift that day. Leave imported from Timetastic counts too. On a day with a shift, the leave hours come off the shift and the rest is paid as worked. A whole-day booking takes the whole shift; a half day takes only its hours.

Press **Why** under a person's leave to see each day: the date, the leave type, the hours, and where the hours came from:

- **from the leave calculation**: the cost recorded when the leave was booked;
- **hours booked in Timetastic**: a one-day booking made in hours in Timetastic;
- **from the confirmed working week**: no recorded calculation, so the person's working week was used.

A Timetastic booking imported twice is paid once.

**Example.** Mary Murphy is rostered 8 hours on Thursday and has a half day of annual leave that costs 4 hours. Her line shows 4 hours worked and 4 hours of Annual Leave, and **Why** says "from the leave calculation".

## When export is stopped

These stop **Certify & Export** and **Download draft CSV** until they are fixed. A red box says which:

| Message | What to do |
|---|---|
| Payroll can't be exported until these are confirmed: Confirm whether ... is paid | Someone took that leave this period and nobody has said whether it is paid. Press **Paid** or **Unpaid** on [Leave Types]({{ site.baseurl }}/docs/app/leave-types/) |
| Payroll can't be exported: N leave days have no hours yet | Confirm the person's working week on [Employees]({{ site.baseurl }}/docs/app/employees/), or type the hours on the booking in [Leave Requests]({{ site.baseurl }}/docs/app/leave-requests/) |
| Payroll can't be exported: these imported bookings differ from what Timetastic ... | Timetastic's figure and the working week disagree. Check the person's working week, or type the hours on the booking |

The export from the quick actions on Employees is stopped the same way.

## How to use it

1. Pick the pay period with the arrows.
2. Read the banner.
3. Check the **Payroll Table** line by line: scheduled hours, actual hours and leave.
4. Resolve anything listed under **Reconciliation Gate**.
5. Press **Download draft CSV**.

## What is in the CSV

- The first two columns are **Works No.** (the person's payroll ID) and **Name**. These are the two fields Collsoft needs to match each person.
- Then the hours, rate, gross pay, period dates and leave totals, in the same order as before. Gross pay is blank unless you chose to include it.
- Then **pay_type** and **pay_frequency** from the person's pay record on [Employees]({{ site.baseurl }}/docs/app/employees/) (blank if none), **bank_holiday_hours** and **unpaid_break_hours** (blank when no rule puts any in the file). Hours worked already have the unpaid break taken off.
- Last, one **"&lt;leave type&gt; hours"** column for each leave type on your [Leave Types]({{ site.baseurl }}/docs/app/leave-types/) list (archived types left out), in that list's order. For example **Annual Leave hours** and **Sick Leave hours**. If someone has leave of a type that is not on the list, its column is added at the end, so no hours are dropped.
- In Collsoft's import wizard, map each column once (for example Annual Leave hours to annual leave). Collsoft only imports the columns you map.
- A name that starts with = + - or @ gets a ' in front, so a spreadsheet shows it as text.

## Common questions

**Can I import the CSV into Collsoft?**
The file is laid out for Collsoft's wage data import wizard, but while the period is a draft it is for checking, not for paying anyone. See [What is in the CSV](#what-is-in-the-csv).

**Why is there a column for a leave type nobody took this period?**
The file always has one column for every leave type you use, so the layout is the same every week and Collsoft's column mapping keeps working.

**Why does it say "Not measured"?**
Pay follows the roster, so nothing was measured by a clock.
