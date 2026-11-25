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

Each request is a card. Approval is two steps on purpose: first you look at the calculation, then you approve.

1. Press **Open the calculation to review**. The card shows how the cost was worked out: the days, the hours the person was scheduled, and any public holidays or closure days inside the booking.
2. Read it, then press **Review calculation**. The button changes to **Calculation reviewed**.
3. Press **Approve**.

If approving would leave a room short of staff, the button reads **Review & Approve** and is amber or red. You are shown which days are short. To go ahead you press **Approve Anyway** and give a reason. The reason is kept in the audit log.

**Example.** Mary Murphy books Monday to Wednesday. She is rostered 8h 15m (495 minutes) each day. The calculation shows 3 days, 1,485 minutes. You review it, approve it, and her balance drops by 1,485 minutes.

## Someone with no working week: enter the hours

If the person has no confirmed working week for the dates, Timebreez cannot work out what the leave costs. The card says so and shows **Enter hours**.

1. Press **Enter hours**.
2. Type the hours for each day from their rota, for example `7.5` or `7:30`.
3. Under **Where these hours come from**, say where you got them, for example "Rota for week of 7 Dec" (at least 10 characters).
4. Press **Save hours**. The typed hours become the calculation.
5. Review the calculation again, then approve as usual.

**Example.** Mary Murphy has no working week yet and asks for Thursday off. Her rota has her on 6 hours. You enter `6`, write "Rota for week of 7 Dec", save, review, and approve. 360 minutes come off her balance.

## Denying a request

Press **Deny** and type the reason. The person sees it with the request.

## Messages you may see

| Message | What it means | What to do |
|---|---|---|
| Calculation reviewed. You can now approve this request. | Your review is recorded | Press Approve |
| A refusal saying the calculation changed since you reviewed it | Something the cost depends on changed (dates, roster, a rule) | The review button resets. Open the new calculation and review it again |
| Your account is not linked to an employee record | Your login has no staff record, so the approval cannot be put in your name | Ask an admin to link your login to your staff record |
| No calculation to review | The cost could not be worked out yet | Check the person's work pattern and the calculation rules in [Settings]({{ site.baseurl }}/docs/app/settings/) |

| Days not calculated | Timebreez could not work out what this request costs. The **Why** line says what is missing | Do what the **Fix** line says |
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
