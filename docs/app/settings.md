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
| Public holidays in the payroll file | When a public holiday falls in a pay period, how many hours go in the file's bank holiday column? | None, your payroll system works it out. Or each person's weekly contracted hours divided by a number you choose, for example 5. With that choice, also pick who qualifies: everyone with a working week on the day, or only people who worked enough hours in the weeks before the holiday |

A rule shown as "Not decided yet" stops any booking that needs it until you set it. The three payroll rules work differently: until you set them, the payroll file has hours only (no gross pay), takes no break off, and has no bank holiday hours. The [Payroll]({{ site.baseurl }}/docs/app/payroll/) page says so.

**Why the three payroll rules start off:**

- **Gross pay in the payroll file** is off so Timebreez never sends a money figure your payroll system did not work out. Your payroll system applies its own rates until you choose otherwise.
- **Breaks in paid hours** is off because break rules differ from place to place (some pay lunch, some do not). Nothing is taken off until you say how long the break is and whether it is paid.
- **Public holidays in the payroll file** is off because your payroll system usually works out bank holiday pay itself. Putting hours in the file as well could pay the day twice.

Each rule is your organisation's own, so two organisations can answer differently.

**Who qualifies for public holiday hours.** If you choose **Only people who worked enough hours in the weeks before the holiday**, fill in **At least this many hours** and **In this many weeks before the holiday** (for example 40 and 5), and tick **Full-time staff qualify without the hours test** if that applies. There is no built-in number. Put where the rule comes from in the **Why** box. Hours come from the rota or clock records in Timebreez. When those do not cover every week, the person is listed on [Payroll]({{ site.baseurl }}/docs/app/payroll/#who-qualifies-for-bank-holiday-hours) for you to confirm, with no bank holiday hours until you decide.

For breaks, the longest band a day's worked time is over decides the break. On a part day of leave, only the worked part counts. There is no built-in break length.

There is no built-in rate for leave earned from hours. Until you set it, people on the **Hours staff** page earn nothing and recording their hours is refused.

**Example.** Your full-time day is 495 minutes and half days round up. A half day costs 248 minutes, so two half days cost 496 minutes: one minute more than a full day. The booking's calculation shows that minute and why.

**Before a Timetastic import:** set the full-time day and the half-day rule with an **Applies from** date on or before the start of the leave year you are importing. Otherwise the balances step will not use them.

### Payroll system

Under **Leave Setup**, choose **Payroll system**: Collsoft, BrightPay, Thesaurus Payroll Manager, Sage 50 Payroll, Xero Payroll, another system, or none. Staff records then name each person's payroll number the way your payroll does: **Works No.** for Collsoft, **Works number** for BrightPay, and **Payroll ID** otherwise. To use your own wording, fill in **Name for the payroll number**. Press **Save**.

### Templates

**Choose a template** for your kind of business and press **Apply template**. It only fills rules you have not decided yet. Anything you already set is kept.

## Leave Types

The kinds of leave your organisation uses (Annual Leave, Sick, Unpaid and so on), their colours and their rules. See [Leave Types]({{ site.baseurl }}/docs/app/leave-types/).

## Messaging

Choose which messaging apps your team uses. Sharing the rota, cover requests and other sends only offer the apps you switch on here. Only an admin can change these; managers can see them.

| App | What it needs |
|---|---|
| **Telegram** | Each person links their own Telegram once, in [My Settings]({{ site.baseurl }}/docs/app/my-settings/#link-telegram). Managers can send the rota to the staff group |
| **Slack** | Paste the incoming-webhook link for your staff channel (Slack: Apps, Incoming Webhooks) |
| **Microsoft Teams** | Paste the webhook link for your staff channel (Teams: channel, Workflows, "Post to a channel when a webhook request is received") |
| **WhatsApp** | Needs a WhatsApp Business account. Contact Timebreez support to set it up |
| **Email** | Uses each person's email address on their profile |

Slack and Teams show **Needs webhook link** until a link is saved, then **Ready**. Saved links are never shown to staff.

## Scheduler

### Close week

**Close the week automatically when the new week starts.** Off unless an admin turns it on. When on, at midnight on Monday last week's roster closes itself if nobody closed it, and payroll sees **Closed automatically**. A week someone reopened stays open until a person closes it. Set the time zone for "midnight on Monday" in the box below it (Europe/Dublin unless you change it), then press **Save**. Only admins can change it. See [Close the week]({{ site.baseurl }}/docs/app/roster/#close-the-week).

## Features

Admins choose which parts of the app appear in the menu. **Leave Management** is always on. The others can be switched off:

| Feature | Screens |
|---|---|
| **Scheduler / Roster** | Roster, My Schedule |
| **Payroll** | Payroll |
| **Live floor (rooms, check-in, attendance)** | Control Desk, Headcount, Reality Panel, Compliance, Children, Attendance, Ops Inbox, and the reconciliation screens |
| **Insights (analytics, staff care)** | Analytics, Staff Care |

Live floor and Insights are on for every organisation until an admin switches them off. Switching a feature off removes it from the menu, and its screens say "This screen is switched off for your organisation". Nothing is deleted. Switch it back on here and everything is as it was.
