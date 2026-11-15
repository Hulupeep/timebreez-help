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

## Common questions

**Can I import the CSV straight into my payroll system?**
Not yet. It is a draft for checking. A file in your payroll system's own format is a separate piece of work and is not available yet.

**Why does it say "Not measured"?**
Pay follows the roster, so nothing was measured by a clock.
