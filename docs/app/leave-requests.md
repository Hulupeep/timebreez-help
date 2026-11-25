---
layout: default
title: Leave Requests
parent: Page by page
nav_order: 6
permalink: /docs/app/leave-requests/
---

# Leave Requests

**Who uses it:** admins and managers approve here. Staff request leave on [My Leave]({{ site.baseurl }}/docs/app/my-leave/), on the [staff app]({{ site.baseurl }}/docs/app/staff-app/) or on [Telegram]({{ site.baseurl }}/docs/app/my-settings/).

## What it does

Lists every time-off request for your organisation. You check what each request costs, then approve or deny it. Approving takes the time off the person's balance.

## Finding requests

The filters under **Show leave for** narrow the list (and the downloads below) to the people, dates and status you pick.

The requests are grouped as **Pending**, **Approved**, **Denied** and **Canceled**. Each group shows 20 at a time. At the bottom of a group it says, for example, "Showing 20 of 85". Press **Show 20 more (65 left)** to see the next ones.

For managers and admins, the requests waiting for a decision come first, at the top of the page under **Waiting for you (N)**, above the filters, downloads and carry-over. When nothing is waiting it says so. **Request Leave** (top right) is an outline button for managers, because the page's main job for them is deciding.

## Approving a request

Each request is a card. The card shows what the leave takes from the person's allowance, right above the buttons. Press **Approve** once: that records the figure you were shown and approves the request in one go.

**How was this worked out?** opens the full calculation: the days, the hours the person was scheduled, and any public holidays or closure days in the booking. Use it when you want to check a figure. It is never a required step.

If approving would leave a room short of staff, the Approve button is amber or red. You are shown which days are short. To go ahead you press **Approve Anyway** and give a reason. The reason is kept in the audit log.

If the figure changes between the card loading and your press (someone edited the person's terms or the rota), nothing is approved. The card shows the new figure and you press Approve again.

**Example.** Mary Murphy books Monday to Wednesday. She is rostered 8h 15m (495 minutes) each day. The card says the leave takes 3 days, 24h 45m. You press Approve and her balance drops by 1,485 minutes.

## Leave for someone with no employment terms

**Employment terms** are a person's contract details in Timebreez: the date they start from, their employment status, how many days a week they work and how many hours a day. You set them on the person's card on the **Staff** page. Timebreez uses them to work out exactly what each day of leave costs.

When someone has no employment terms (or no confirmed working week) for the dates, the card shows an amber box labelled **Estimated** instead of an exact figure. The estimate is worked out like this, day by day:

| Day | Counts as |
|---|---|
| They are on the rota that day | Their shift, less any unpaid break your break rule gives |
| There is a rota that day but they are not on it | 0 |
| No rota has been made that far ahead | Your organisation's full-time day (set in [Settings]({{ site.baseurl }}/docs/app/settings/)) |
| Saturday, Sunday or a public holiday | 0 |

**What to do, in order of preference:**

1. **Best: set their employment terms.** Press **Set Mary Murphy's employment terms** in the box. It opens their Staff card. After that every leave for them is worked out exactly and the box goes away.
2. **For this request, Approve is fine.** The estimate is saved with your name and how it was worked out, so anyone can see later where the figure came from.
3. **Only if you know their real hours differ on these days,** press the small **Change the hours** link under the card. Type the hours for each day (`7.5`, `7,5` or `7:30`; a blank day counts as 0), keep or edit the reason, and press **Save hours**. Then approve.

Press **Why an estimate, and what should I do?** in the box for the same advice on the card itself.

**Example.** Mary Murphy has no employment terms and books Wednesday 30 December to Monday 4 January. She is on the rota Wednesday (8:00 to 17:00, with an unpaid 45-minute break, so 8h 15m) and not on it Thursday. Friday 1 January is a public holiday. The rota stops at Sunday, so Monday uses your full-time day of 8h 15m. The card says **Takes about 16h 30m**. You approve, and then set her employment terms so her next leave is exact.

If your organisation has no full-time day set and there is no rota for some of the dates, Timebreez cannot estimate those days. The hours box opens on its own, and Approve waits until you type the hours or set the full-time day.

## Denying a request

Press **Deny** and type the reason. The person sees it with the request.

## Messages you may see

| Message | What it means | What to do |
|---|---|---|
| The figure changed since this card loaded | Something the cost depends on changed (dates, terms, rota, a rule) | Check the new figure on the card and press Approve again |
| Your account is not linked to an employee record | Your login has no staff record, so the approval cannot be put in your name | Ask an admin to link your login to your staff record |
| Estimated: no employment terms | The person has no employment terms for these dates, so the figure is an estimate | See [Leave for someone with no employment terms](#leave-for-someone-with-no-employment-terms) |
| Days not calculated | Timebreez could not work out or estimate what this request costs. The **Why** line says what is missing | Do what the **Fix** line says |
| Cover check is off: Mary Murphy has no home room | The person has no home room, so Timebreez cannot check room cover for this request | Give them a home room so cover is checked |

A refusal stays on screen until you close it, so you can read it.

## Downloads

Under **Download a spreadsheet (CSV)**:

- **Download leave list (n)**: the requests the filters show, one row each. Every booking is loaded, however many there are, so a date range far in the past is complete.
- **Download balances**: each person's balance today, per leave type. After the first six columns come **Balance Hours**, **Leave Year Start** and **Leave Year End**, the year's **Allowance** in working days and hours, what has been **Used, Booked or Adjusted** since, in days and hours, and **Next Leave Year Start** with next year's balance once it is open. When a balance has no leave-year record those columns are blank, not 0.

**Example.** Mary Murphy has 20 days for 2026 and has used 6. Her row shows Allowance 20.00, Used, Booked or Adjusted 6.00 and Balance 14.00 working days, with the same figures in hours beside them.

Neither is the payroll file. For pay, use [Payroll]({{ site.baseurl }}/docs/app/payroll/).

## Carry-over requests

Above the list, **Carry-over requests** shows the organisation's rule, requests waiting for a decision, and recent decisions. See [Carry-over]({{ site.baseurl }}/docs/app/carry-over/).

## Common questions

**Why can't I approve straight away?**
Because leave is pay. Timebreez shows you the figure it will deduct and records that you looked at it before you approve.

**Can I cancel leave that is already approved?**
Yes. The days go back on the person's balance.

**Where do I import balances from a spreadsheet?**
Use the [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/) instead. It checks every balance against Timetastic before you sign it off.
