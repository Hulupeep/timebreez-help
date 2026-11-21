---
layout: default
title: Carry-over
parent: Page by page
nav_order: 19
permalink: /docs/app/carry-over/
---

# Carry-over

**Who uses it:** staff ask on [My Leave]({{ site.baseurl }}/docs/app/my-leave/), the [staff app]({{ site.baseurl }}/docs/app/staff-app/) or [Telegram]({{ site.baseurl }}/docs/app/my-settings/). Admins (or managers, if the rule says so) decide on [Leave Requests]({{ site.baseurl }}/docs/app/leave-requests/).

## What it does

Unused leave does not move into next year on its own. A person asks to carry some of it, and an admin approves all of it, part of it, or declines, always with a reason. Days not carried with approval expire at the end of the leave year.

**Why it needs approval:** whether unused leave expires or moves on is a decision under the person's contract and your policy, not something software should assume. So the person asks, someone with authority decides, and the reason is on record. Decide within the deadline your rule sets (**Days after year end to still decide**): anything not carried by then expires.

## The rule

Your organisation sets the rule once, on **Leave Requests**, under **Carry-over requests**. Press **Change the carry-over rule**.

| Setting | What it means |
|---|---|
| **Most days a person can carry** | The limit for people whose allowance is in days |
| **Most hours (hours-allowance staff)** | The limit for people whose allowance is in hours. Use 0 for "nothing can be carried" |
| **Days after year end to still decide** | 0 means every decision is made by the last day of the leave year |
| **Who decides** | An admin, or an admin or manager |
| **Where does this rule come from?** | Required. For example: staff handbook, Nov 2026 |

Until a rule is saved, nobody can ask, and the card says your organisation has not set a carry-over rule. A new rule applies from today. Earlier decisions keep the rule they were made under.

## Asking (staff)

The **Carry days into next year** card says what you have unused this year, after the leave already approved, the limit, and the last day to ask.

1. Type how many days (or hours, if your allowance is in hours).
2. Add a note for your manager if you like.
3. Press **Ask to carry**.

Asking moves nothing. Your balance only changes if the request is approved. You can **Withdraw this request** while it is waiting. You can have one request per leave year; withdraw it to ask for a different amount.

You are told plainly if you can't ask, for example "The carry-over limit is 10 days." or "You have 6.5 days unused in 2026, after the leave already approved."

On Telegram, send `/carry` to see your position, `/carry 2` to ask for 2, `/carry 2 saving for a trip` to add a note, and `/carry withdraw` to take back a request that is waiting.

## Deciding (admin)

Each waiting request shows who asked, how much, their note and what they have unused.

1. Change **Approve how many** if you are approving less.
2. Write a **Reason (the person sees it)**. A reason is needed for both approve and decline.
3. Press **Approve** or **Decline**.

Approving above the limit needs the **Exception** box, and the request stays labelled as an exception.

The unused amount is checked again when you approve, so days already booked since the ask can't be carried twice.

**Record a request someone made by email, phone or in person** lets you enter an ask for someone. The same checks apply.

## What approval does

Approval moves time, it never adds it. Two lines are written: the days come out of this year on its last day, and go into next year on its first day. They add up to zero, and each line says who approved it, when and why. This year's balance drops straight away, so the same days can't also be booked in December.

**Undo** on a decided request puts the days back into this year. It needs a reason too.

## At the year end

Requests close at the end of the leave year, in your organisation's time zone. A request nobody decided by then is not carried. Days not carried simply aren't in next year's balance. Nothing is written off your record, and the card shows what expired.

## Common questions

**Does carry-over change the Timetastic import check?**
No. Carried days are left out of the import comparison, so a December approval can't move a figure you already signed off.

**Can carried days expire later in the new year?**
Not yet. There is no "use by" date on carried days.
