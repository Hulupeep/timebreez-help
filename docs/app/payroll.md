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

Shows, for one pay period, each person's hours and leave, lists the exceptions to resolve, and lets you download the figures. Gross pay is only worked out if you choose it in [Settings]({{ site.baseurl }}/docs/app/settings/), **Gross pay in the payroll file**, and never for salaried staff.

## Breaks and public holidays

A box above the table says how breaks and public holidays are paid this period, from your settings (**Breaks in paid hours** and **Public holidays in the payroll file**):

- With a break rule, it reads for example "Breaks: Over 6h00 worked: 45 min. Unpaid: taken off paid hours." An unpaid break comes off hours worked. Scheduled hours stay as rostered.
- With no break rule: "each shift is paid from start to end".
- If a public holiday falls in the period, it is named, with how it is paid. With no rule set, this line is amber and the file has no bank holiday hours.
- Anyone with no confirmed working week is named, with no bank holiday hours: their weekly hours are unknown, so nothing is guessed.

- Each public holiday uses the person's employment terms in force on that day. Someone who started after the holiday gets no bank holiday hours for it.
- Someone whose pay record says **Salaried** is not paid by the hour. Their hours-worked and bank holiday columns are 0, and their worked and bank holiday hours go in **salaried_hours** for information. The page names them: "Salaried, so no hours are paid by the hour". To change it, change the person's pay record on [Employees]({{ site.baseurl }}/docs/app/employees/#payroll-tab).

**Example.** The rule is weekly contracted hours divided by 5. Mary Murphy is contracted 30 hours a week, so a public holiday in the period puts 6 bank holiday hours on her line, paid.

## Who qualifies for bank holiday hours

If your rule for **Public holidays in the payroll file** has a qualifying test (set in [Settings]({{ site.baseurl }}/docs/app/settings/#leave-calculation-rules)), a table lists each person and each public holiday in the period: the hours counted, whether they qualify, their bank holiday hours, and the reason.

| Qualifies column | Means |
|---|---|
| **qualifies** | They worked at least the hours your test needs in the weeks before the holiday |
| **qualifies (full-time)** | Full-time staff skip the test, because you ticked that |
| **does not qualify** | Every week is recorded and they worked fewer hours than needed. No bank holiday hours |
| **payroll to confirm** | Timebreez can't be sure: some weeks have no rota or clock record yet, or some hours are on days that also have approved leave |
| **not employed then** | They started after the holiday, or had no working week in force that day |
| **no test set** | Your rule has no qualifying test, so everyone with a working week that day gets the hours |

Hours come from the rota or clock records in Timebreez, after any unpaid break. They are never read from contracted hours.

Anyone marked **payroll to confirm** is named above the table. No bank holiday hours go in the file for them until you decide. **Download bank holiday check** gives this table as its own file; the Collsoft file is not changed.

The page also says the qualifying rule is your organisation's setting and has not yet been checked by a named payroll reviewer.

**Example.** The test is 40 hours in the 5 weeks before the holiday. Mary Murphy worked 42 hours in those weeks, so the reason reads "42 h worked ..., at least 40 needed: qualifies".

## When a period is a draft

An amber banner at the top says why the period is a draft. You will see one of these:

| Banner | What it means |
|---|---|
| Draft, not for payroll: this organisation has no pay basis set. | Timebreez does not know whether pay follows the roster or a clock |
| Draft, not for payroll: N hours have no complete clock-in and clock-out record. | Some shifts are missing a clock-in or clock-out |
| Draft, not for payroll: these are rostered hours, not hours anyone measured. | Pay follows the roster. Check every line |
| Draft, not for payroll: N leave days are priced from the working week, not a recorded calculation. | Hours are measured, but some leave days have no recorded calculation. Check those leave lines |

While a period is a draft, **Certify & Export** is switched off and says why underneath. **Download draft CSV** is then the filled blue button: use it to get the figures and check them against your payroll system. A clock-based period where every leave day has a recorded calculation is not a draft.

## Leave lines

Every day of approved leave in the period gets a leave line, even when the person had no shift that day. Leave imported from Timetastic counts too. On a day with a shift, the leave hours come off the shift and the rest is paid as worked. A whole-day booking takes the whole shift; a half day takes only its hours.

Press **Why** under a person's leave to see each day: the date, the leave type, the hours, and where the hours came from:

- **from the leave calculation**: the cost recorded when the leave was booked;
- **hours booked in Timetastic**: a one-day booking made in hours in Timetastic;
- **from the confirmed working week**: no recorded calculation, so the person's working week was used.

A Timetastic booking imported twice is paid once.

**Example.** Mary Murphy is rostered 8 hours on Thursday and has a half day of annual leave that costs 4 hours. Her line shows 4 hours worked and 4 hours of Annual Leave, and **Why** says "from the leave calculation".

## When export is stopped

These stop **Certify & Export** and **Download draft CSV** until they are fixed. A red box says which:

| Message | What to do |
|---|---|
| Payroll can't be exported until these are confirmed: ... | Someone took that leave this period and nobody has said whether it is paid. Each type is listed with its hours this period, any days with no hours yet, and whether those hours count as paid, unpaid or neither for now, for example "Training: 7.5 hours this period, counted as unpaid for now". Press **Paid** or **Unpaid** on [Leave Types]({{ site.baseurl }}/docs/app/leave-types/) |
| Payroll can't be exported: N leave days have no hours yet | Confirm the person's working week on [Employees]({{ site.baseurl }}/docs/app/employees/), or type the hours on the booking in [Leave Requests]({{ site.baseurl }}/docs/app/leave-requests/) |
| Payroll can't be exported: these imported bookings differ from what Timetastic ... | Timetastic's figure and the working week disagree. Check the person's working week, or type the hours on the booking |

The export from the quick actions on Employees is stopped the same way.

## Is the roster week closed?

The first box on the page says whether the manager has closed the roster for that week:

| Box | Means |
|---|---|
| Green, **Roster week: Closed by Mary Murphy, Fri 11 Dec 15:42** | The roster is final. Go ahead |
| Green, **Closed automatically** | Nobody closed it, so it closed itself at midnight on Monday (only if your admin turned that on) |
| Amber, **Not closed yet** | The manager has not closed it yet. The roster may still change. Wait before you download |
| Amber, **Reopened by ... : reason** | The manager is changing it. Wait until it is closed again |
| Red, **N shift changes made while the week was closed** | Something changed after it closed, for example a leave approval. Each change is listed with who, when, the person and the day. The hours below already include it; check those people before you download |

Every earlier reopen is listed under a closed week too, with its reason. See [Close the week]({{ site.baseurl }}/docs/app/roster/#close-the-week).

## How to use it

1. Pick the pay period with the arrows.
2. Check the roster week is **Closed** (the first box).
3. Work down the **Before you export** box: read the amber draft line at its foot and clear any red box.
4. Check the **Payroll Table** line by line: scheduled hours, actual hours and leave. Tick **Approved** for each person once their line is right.
5. Resolve anything listed under the **Checks** tab (it used to be called Reconciliation Gate).
6. Press **Download draft CSV**.
7. Once the file is imported into your payroll system and staff are paid, press **Mark done: imported and paid**. See [Close off the pay week](#close-off-the-pay-week).

See [Who does what each week]({{ site.baseurl }}/docs/app/weekly-jobs/).

## Close off the pay week

Under the roster week box, **Pay week** says whether payroll for this week is finished:

| Pay week | Means |
|---|---|
| **Open: not yet marked as imported and paid** | Payroll for this week is not done yet |
| **Closed off by Mary Murphy** (with the date) | Someone marked it done |
| **Closed off automatically** | It closed itself, because your admin set automatic close-off |
| **Reopened by ...: reason** | It was closed, then opened again for that reason |

**To close it off:** press **Mark done: imported and paid**. The page says when the file was certified, and by whom. If no certified file was downloaded for the week, it says so: close it off only if payroll was done another way. Add a note if you like, for example "Imported Thu, paid Fri", then press **Yes, it is imported and paid**.

**Changes after close-off.** Nothing is blocked. Any shift or leave change in a closed-off week is listed on that week, with when, who, what and for whom, for example "2 changes since this week was closed off. Pay them as an adjustment, or reopen the week." Closing it off again clears the list. Just above the Pay week box, a red box lists any other closed-off week that has changed since, with a link to open it.

**To reopen:** press **Reopen**, say why, and press **Reopen** again. The reason is kept.

**Automatic close-off.** At the bottom of the box, set **Close an exported week this many days after it ends** (1 to 60, empty for off) and the time zone (Europe/Dublin unless you change it), then press **Save**. Only a week whose file was certified closes itself, and never one a person has closed or reopened.

Only admins can close off, reopen or change the automatic setting.

## Works No. check before you download

Above the figures, an amber box lists:

- people with hours in this period and **no Works No.** Collsoft won't import their hours. Each name opens their record so you can add it;
- any **Works No. on more than one person**, with both names. Collsoft would put one person's hours on the other;
- other active people with no Works No. who have no hours this period.

It does not stop the download, but fix it before you send the file. See [Works No.]({{ site.baseurl }}/docs/app/employees/#works-no).

## What is in the CSV

- The first two columns are **Works No.** (the person's payroll ID) and **Name**. These are the two fields Collsoft needs to match each person.
- Then the hours, rate, gross pay, period dates and leave totals, in the same order as before. Gross pay is blank unless you chose to include it.
- Then **pay_type** and **pay_frequency** from the person's pay record on [Employees]({{ site.baseurl }}/docs/app/employees/) (blank if none), **bank_holiday_hours** and **unpaid_break_hours** (blank when no rule puts any in the file). Then **salaried_hours**, filled only for salaried staff. Hours worked already have the unpaid break taken off.
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
