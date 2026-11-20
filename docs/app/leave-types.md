---
layout: default
title: Leave Types
parent: Page by page
nav_order: 12
permalink: /docs/app/leave-types/
---

# Leave Types Help

{: .note }
This page has not been checked against the current app yet. The pages listed under [Page by page]({{ site.baseurl }}/docs/app/) as checked are up to date.


## What It Does

Set up and configure the types of leave your organization uses - Annual, Sick, Unpaid, and custom types.

## Why It Matters

Different leave types can have different rules. Track them separately for accurate reporting and compliance.

## How To Use It

1. View existing **leave types** in the list
2. Click **"+ Add Leave Type"** to create a new one
3. Set the **name and code**
4. Choose a **color** for the wallchart
5. Configure if it **deducts from entitlement**
6. **Save** the leave type

## Paid or unpaid: confirm each type

A leave type the [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/) creates is **unpaid** until a person says otherwise, and nobody has confirmed it yet. In the list it shows an amber line: "Nobody has confirmed whether this leave is paid", with **Paid** and **Unpaid** buttons.

1. Press **Paid** or **Unpaid** for each amber line.
2. The line changes to, for example, "Unpaid, confirmed by an admin on 19 Nov 2026".

Changing the **Paid leave** switch when you edit a type also confirms it. A type you create yourself here is confirmed when you save it.

This matters for payroll: paid and unpaid leave hours go to different columns in the payroll CSV.

## Comes off the allowance: confirm each type

A leave type the Timetastic import creates does **not** come off anyone's allowance until a person confirms it. Types imported before this change are also marked as not confirmed. The list shows a line: "Nobody has confirmed whether this leave comes off the allowance", with **Comes off the allowance** and **Does not** buttons. The line also says what happens until you confirm.

Requests of a type that comes off the allowance are checked against the person's balance. Other types are not. The import screen has the same step, with what Timetastic did as a suggestion: see [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/).

## Common Questions

### What's the difference between paid and unpaid leave?

Paid leave (like Annual) deducts from your entitlement balance. Unpaid leave doesn't use your balance but may affect pay.

## Tips

- Use clear, recognizable names
- Choose distinct colors for each type
