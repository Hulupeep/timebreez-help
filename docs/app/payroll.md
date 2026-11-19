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

Shows, for one pay period, each person's hours, leave and gross pay, lists the exceptions to resolve, and lets you download the figures.

## Every period is a draft for now

An amber banner at the top says why the period is a draft. You will see one of these:

| Banner | What it means |
|---|---|
| Draft, not for payroll: this organisation has no pay basis set. | Timebreez does not know whether pay follows the roster or a clock |
| Draft, not for payroll: N hours have no complete clock-in and clock-out record. | Some shifts are missing a clock-in or clock-out |
| Draft, not for payroll: these are rostered hours, not hours anyone measured, and leave comes from leave requests, not the leave ledger. | Pay follows the roster. Check every line |
| Draft, not for payroll: leave comes from leave requests, not the leave ledger. | Hours are measured, but check every leave line |

While a period is a draft, **Certify & Export** is switched off. Use **Download draft CSV** to get the figures and check them against your payroll system.

## How to use it

1. Pick the pay period with the arrows.
2. Read the banner.
3. Check the **Payroll Table** line by line: scheduled hours, actual hours, leave and gross pay.
4. Resolve anything listed under **Reconciliation Gate**.
5. Press **Download draft CSV**.

## What is in the CSV

- The first two columns are **Works No.** (the person's payroll ID) and **Name**. These are the two fields Collsoft needs to match each person.
- Then the hours, rate, gross pay, period dates and leave totals, in the same order as before.
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
