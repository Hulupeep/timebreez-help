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

## Approving a request

Each request is a card. Approval is two steps on purpose: first you look at the calculation, then you approve.

1. Press **Open the calculation to review**. The card shows how the cost was worked out: the days, the hours the person was scheduled, and any public holidays or closure days inside the booking.
2. Read it, then press **Review calculation**. The button changes to **Calculation reviewed**.
3. Press **Approve**.

If approving would leave a room short of staff, the button reads **Review & Approve** and is amber or red. You are shown which days are short. To go ahead you press **Approve Anyway** and give a reason. The reason is kept in the audit log.

**Example.** Mary Murphy books Monday to Wednesday. She is rostered 8h 15m (495 minutes) each day. The calculation shows 3 days, 1,485 minutes. You review it, approve it, and her balance drops by 1,485 minutes.

## Denying a request

Press **Deny** and type the reason. The person sees it with the request.

## Messages you may see

| Message | What it means | What to do |
|---|---|---|
| Calculation reviewed. You can now approve this request. | Your review is recorded | Press Approve |
| A refusal saying the calculation changed since you reviewed it | Something the cost depends on changed (dates, roster, a rule) | The review button resets. Open the new calculation and review it again |
| Your account is not linked to an employee record | Your login has no staff record, so the approval cannot be put in your name | Ask an admin to link your login to your staff record |
| No calculation to review | The cost could not be worked out yet | Check the person's work pattern and the calculation rules in [Settings]({{ site.baseurl }}/docs/app/settings/) |

A refusal stays on screen until you close it, so you can read it.

## Common questions

**Why can't I approve straight away?**
Because leave is pay. Timebreez shows you the figure it will deduct and records that you looked at it before you approve.

**Can I cancel leave that is already approved?**
Yes. The days go back on the person's balance.

**Where do I import balances from a spreadsheet?**
Use the [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/) instead. It checks every balance against Timetastic before you sign it off.
