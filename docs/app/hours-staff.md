---
layout: default
title: Hours staff
parent: Page by page
nav_order: 36
permalink: /docs/app/hours-staff/
---

# Hours staff

**Who uses it:** admins and managers. Open it from [Leave Admin]({{ site.baseurl }}/docs/app/leave-admin/), **Hours staff**. Managers record hours; only admins add people.

## What it does

Some staff earn leave as they work instead of having a fixed allowance, for example relief staff paid by the hour. This page lists them and records each week's hours once. Timebreez works out the leave each week earns and shows the working, so anyone can see where a balance came from.

**Why it exists:** an hourly person's leave is a share of the hours they actually worked. If a week is missed, their balance is short; if a week is recorded twice, it is too high. Recording each week in one place, with its source, is what keeps the balance right.

## The rule

The top of the page shows the rule in force, for example "8% of hours worked, capped at 4 working weeks of the person's hours; paid leave hours count as hours worked". Your organisation sets it in [Settings]({{ site.baseurl }}/docs/app/settings/), **Leave earned from hours worked**. Timebreez has no built-in rate: until the rule is set, nobody earns anything and recording hours is refused.

## Adding someone (admin)

Under **Add someone who earns leave from hours**, choose the **Person**, the **Leave type credited**, **From** (moves to its Monday), optionally **To**, the **Weekly hours for the cap**, and **Why**. Press **Save**.

Without weekly hours, the cap in the rule is not checked for that person, and the working says so. To change someone, add them again with the new dates. Every change is kept with who made it and why.

## Recording a week

Pick the **Payroll week**. Any date you pick moves to its Monday. Then use one of three sources, in this order:

1. **From the rota.** Press **Week and working** on a person. Their shifts for the week are listed, with paid leave marked and unpaid leave not counted. Press **Confirm these hours**.
2. **The payroll Hours Report.** For weeks not on the rota, upload the report from your payroll system (for example Collsoft's Hours Report) under **Upload the payroll Hours Report**. It needs a column for the person (Works No. or Name) and one for hours worked. Each row shows who it matched and how ("by works number" or "by name"). People who do not earn leave from hours are skipped. Nothing is recorded until you confirm.
3. **Typed for one person.** Only when the week is on neither. Under **Type one person's hours**, choose the person, enter **Hours worked** and **Paid leave hours**, and say **Where the figure comes from**, for example "the timesheet for week 45".

**Why Works No. matters here:** the report is matched on Works No. first, then on the exact name. A person with no Works No. only matches if their name is spelled exactly as in the report. See [Works No.]({{ site.baseurl }}/docs/app/employees/#works-no).

## The working

After each week, the page shows what was credited now and the total earned this leave year, for example "Recorded. +96 min now; 480 min earned this leave year". **Week and working** shows the full working for a person: the hours used, the rule, and whether the cap applied.

**Example.** The rule is 8% of hours worked. Tom Byrne works 20 hours in the week of 2 March. 8% of 20 hours is 1.6 hours, so 96 minutes are credited to his Annual Leave.

## Common questions

**Why was nothing credited?**
Either the rule is not set yet, or the cap was reached. The working says which.

**The report row says "Not earning leave from hours: skipped".**
That person is not on this page. An admin adds them first, then the report is uploaded again.
