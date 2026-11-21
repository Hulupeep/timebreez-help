---
layout: default
title: Settings
parent: Page by page
nav_order: 3
permalink: /docs/app/settings/
---

# Settings

**Who uses it:** admins. In the menu: **Settings**. Settings has many tabs. Before go-live, the ones that matter most are **Leave Setup** and **Leave Types**.

## Leave Setup

### Leave defaults

These apply to everyone you invite.

| Field | What it means |
|---|---|
| Default annual allowance (days) | The starting allowance for a new person. Must be more than zero |
| Leave year starts on | The day and month your leave year resets |
| Default leave type | The type that comes off each person's allowance, usually Annual Leave. Created if it does not exist |

Press **Save leave defaults**. "Saved — your org is leave-ready" confirms it.

### Leave calculation rules

How Timebreez works out what a booking costs. Each rule applies **from a date you choose** and never changes leave that is already approved. Press **Change** next to a rule, pick the answer, set **Applies from**, write **Why** (kept with the change), and save.

| Rule | The question it answers | Answers |
|---|---|---|
| Full-time working day | How many paid minutes are in a full-time day? | A number of minutes, for example 495 for 8h 15m |
| What a half day costs | Half of 8h 15m is 4h 07½m. What happens to the half minute? | Round down (4h 07m), round up (4h 08m), never round (refuse), or a fixed length |
| Public holidays inside a booking | Does a public holiday inside a booking come off the allowance? | No, it costs nothing. Or yes, it costs the hours they were scheduled |
| Closure days inside a booking | Does a day you are closed come off the allowance? | Same two answers |
| Who may take a balance below zero | When a booking would take someone below zero, who may allow it? | Admins only, any admin or manager, only the people you choose, or nobody |
| Leave earned from hours worked | For staff who earn leave as they work, what share of their hours becomes leave, is it capped, and do paid leave hours count as hours worked? | A percent of hours worked, an optional cap in working weeks of the person's hours, and a tick for whether paid leave hours count |

| Gross pay in the payroll file | Should the payroll file work out gross pay (paid hours x rate), or carry hours only so your payroll system applies its own rates? | No, hours only. Or yes, paid hours x rate, for hourly staff only |
| Breaks in paid hours | How long is the break on a shift of a given length, and is it paid? | One or more bands, for example "worked longer than 360 minutes: 45 minute break", and a tick if the break is paid |
| Public holidays in the payroll file | When a public holiday falls in a pay period, how many hours go in the file's bank holiday column? | None, your payroll system works it out. Or each person's weekly contracted hours divided by a number you choose, for example 5 |

A rule shown as "Not decided yet" stops any booking that needs it until you set it. The three payroll rules work differently: until you set them, the payroll file has hours only (no gross pay), takes no break off, and has no bank holiday hours. The [Payroll]({{ site.baseurl }}/docs/app/payroll/) page says so.

**Why the three payroll rules start off:**

- **Gross pay in the payroll file** is off so Timebreez never sends a money figure your payroll system did not work out. Your payroll system applies its own rates until you choose otherwise.
- **Breaks in paid hours** is off because break rules differ from place to place (some pay lunch, some do not). Nothing is taken off until you say how long the break is and whether it is paid.
- **Public holidays in the payroll file** is off because your payroll system usually works out bank holiday pay itself. Putting hours in the file as well could pay the day twice.

Each rule is your organisation's own, so two organisations can answer differently.

For breaks, the longest band a day's worked time is over decides the break. On a part day of leave, only the worked part counts. There is no built-in break length.

There is no built-in rate for leave earned from hours. Until you set it, people on the **Hours staff** page earn nothing and recording their hours is refused.

**Example.** Your full-time day is 495 minutes and half days round up. A half day costs 248 minutes, so two half days cost 496 minutes: one minute more than a full day. The booking's calculation shows that minute and why.

**Before a Timetastic import:** set the full-time day and the half-day rule with an **Applies from** date on or before the start of the leave year you are importing. Otherwise the balances step will not use them.

### Templates

**Choose a template** for your kind of business and press **Apply template**. It only fills rules you have not decided yet. Anything you already set is kept.

## Leave Types

The kinds of leave your organisation uses (Annual Leave, Sick, Unpaid and so on), their colours and their rules. See [Leave Types]({{ site.baseurl }}/docs/app/leave-types/).
