---
layout: default
title: What's new
parent: Page by page
nav_order: 0
permalink: /docs/app/whats-new/
---

# What's new

Changes to the app that you will notice, newest first.

## 23 November 2026

- **Employees:** a login can be marked **AI Agent** (robot or test login). It is never counted as staff, rostered, paid or notified. [Employees]({{ site.baseurl }}/docs/app/employees/#ai-agents-robot-and-test-logins)
- **Employees:** admin-only **Notes** on each person, and the start date is read back in words. [Employees]({{ site.baseurl }}/docs/app/employees/#notes)
- **Settings:** new **Payroll system**. The payroll number is named the way your payroll names it, not always "Works No.". [Settings]({{ site.baseurl }}/docs/app/settings/#payroll-system)
- **Roster:** new **Close week**. Close the roster when it matches what happened; reopening needs a reason, and payroll sees both. An admin can have weeks close themselves when the new week starts. [Roster]({{ site.baseurl }}/docs/app/roster/#close-the-week)
- **Payroll:** the first box says whether the roster week is closed, and lists any shift changed after it closed. [Payroll]({{ site.baseurl }}/docs/app/payroll/#is-the-roster-week-closed)
- **New page:** [Who does what each week]({{ site.baseurl }}/docs/app/weekly-jobs/).
- **Timetastic import:** when a booking is split across leave years, the balance history now reads "(2 days)" or "(1.5 days)", not "(2. days)". [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/)

## 22 November 2026

- **Leave Types:** a type can now come out of another type's balance (or none), and you choose who can book it. [Leave Types]({{ site.baseurl }}/docs/app/leave-types/)
- **Leave Requests:** the leave list loads every booking, not just the newest 1,000. The balances download adds hours, the leave year, its allowance and what has been used. [Leave Requests]({{ site.baseurl }}/docs/app/leave-requests/)
- **Payroll:** a leave type not yet confirmed as paid now shows its hours this period and how they count for now. [Payroll]({{ site.baseurl }}/docs/app/payroll/)
- **Payroll:** salaried staff are not paid by the hour; their hours go in a new **salaried_hours** column. A public holiday before someone started gives them no bank holiday hours. [Payroll]({{ site.baseurl }}/docs/app/payroll/)
- **Employees:** a person's pay history is listed, and a pay record that has not started can be withdrawn. A PPS number can be removed with a reason, and its view log is shown. [Employees]({{ site.baseurl }}/docs/app/employees/)
- **Invites:** only the invited email address can accept an invite, and it must be confirmed. [Employees]({{ site.baseurl }}/docs/app/employees/)
- **Leave Admin:** new link, **Open next leave year**. [Leave Admin]({{ site.baseurl }}/docs/app/leave-admin/)

## 21 November 2026

- **Employees:** a person's Payroll tab records how they are paid (hourly or salaried, rate, how often) from a date, keeping every earlier record. The payroll file uses the one in force for the period. [Employees]({{ site.baseurl }}/docs/app/employees/)
- **Employees:** admins can record a PPS number. It shows masked, and every full view needs a reason and is logged. [Employees]({{ site.baseurl }}/docs/app/employees/)
- **Employees:** admins see which login is on a person's record, and can disconnect it if the wrong account joined. [Employees]({{ site.baseurl }}/docs/app/employees/)
- **Invites:** the invite page says who the invite is for. A different signed-in account gets no Join button, and the page explains when only an admin can fix it. [Employees]({{ site.baseurl }}/docs/app/employees/)
- **Settings, Payroll:** three new rules: gross pay in the file (off until you choose), breaks in paid hours, and bank holiday hours for public holidays. The payroll page says which apply. [Settings]({{ site.baseurl }}/docs/app/settings/), [Payroll]({{ site.baseurl }}/docs/app/payroll/)
- **Payroll:** the CSV adds pay type, pay frequency, bank holiday hours and unpaid break hours at the end of the existing columns. [Payroll]({{ site.baseurl }}/docs/app/payroll/)
- **Roster:** Edit Shift and Add Cover now say when the leave check failed, instead of looking like no leave. [Roster]({{ site.baseurl }}/docs/app/roster/)

## 20 November 2026

- **Carry-over:** staff can ask to carry unused leave into next year, on My Leave or with `/carry` on Telegram. An admin approves all, part or declines with a reason on Leave Requests, against the organisation's limit. Days not carried with approval expire at the year end. [Carry-over]({{ site.baseurl }}/docs/app/carry-over/)
- **Payroll:** every day of approved leave now has a leave line, even with no shift that day, and imported leave counts. Press **Why** to see where each day's hours came from. [Payroll]({{ site.baseurl }}/docs/app/payroll/)
- **Payroll:** export (and the draft CSV) is stopped while a leave type used in the period is not confirmed as paid or unpaid, a leave day has no hours, or an imported booking differs from Timetastic. A red box says which. [Payroll]({{ site.baseurl }}/docs/app/payroll/)
- **Leave Types, Timetastic import:** imported leave types no longer come off the allowance until an admin confirms each one. [Leave Types]({{ site.baseurl }}/docs/app/leave-types/)
- **Timetastic import:** each person's card on the opening balances stage starts with its next step, and shows how days were turned into minutes. A new **Working weeks** step confirms each person's working days from Timetastic. [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/)
- **Timetastic import:** for someone whose allowance is in hours, bookings are read in hours. A booking across the leave-year end is split between the two years once next year is open. [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/)
- **Leave Requests:** for someone with no confirmed working week, a manager can press **Enter hours** and type each day's hours from the rota, with where they came from. [Leave Requests]({{ site.baseurl }}/docs/app/leave-requests/)
- **Employees, Staff app:** balances say which leave year they are for. Once next year is open, its balance shows on a separate line. [Employees]({{ site.baseurl }}/docs/app/employees/)
- **Employees:** invites are not emailed. Copy the invite link and send it yourself. The invite page sends a sign-in link, can send it again, change the email, or use Google. [Employees]({{ site.baseurl }}/docs/app/employees/)
- **Roster:** Fill from Last Week brings back shifts cancelled by last week's leave, skips people on leave this week, closed days and public holidays, and lists what it left out. A shift on someone's leave day needs a tick to save. [Roster]({{ site.baseurl }}/docs/app/roster/)
- **Settings:** new rule, **Leave earned from hours worked**, used by the Hours staff page (from Leave Admin). [Settings]({{ site.baseurl }}/docs/app/settings/)
- **Telegram:** staff can cancel leave with `/cancel`; `/help` lists the commands; hours staff see hours in `/bal`. Admins with Telegram linked are told about new requests and cancellations. [My Settings and Telegram]({{ site.baseurl }}/docs/app/my-settings/)
- **Wallchart:** staff now see their own leave under **My Leave**; before, it was always empty. Picking a month no longer jumps to the wrong month when the view starts on the 29th to 31st. [Wallchart]({{ site.baseurl }}/docs/app/wallchart/)

## 19 November 2026

- **Payroll:** the CSV now starts with Collsoft's own column names, **Works No.** and **Name**, and ends with one hours column for each leave type, the same every week. [Payroll]({{ site.baseurl }}/docs/app/payroll/)
- **Timetastic import:** a leave type made with **Create exact** is now unpaid until a person confirms it. Before, every new type was counted as paid. [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/)
- **Leave Types:** a type nobody has confirmed shows "Nobody has confirmed whether this leave is paid" with **Paid** and **Unpaid** buttons. [Leave Types]({{ site.baseurl }}/docs/app/leave-types/)

## 18 November 2026

- **Staff app:** shifts show on the right day. On a phone or computer set to a time zone behind UTC (for example North America), every shift showed one day early. [Staff App]({{ site.baseurl }}/docs/app/staff-app/)

## 17 November 2026

- **Timetastic import:** on a row blocked by an unanswered question, **Explain** is now greyed out, with a line saying why. The refusal code shows once, not twice. [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/)
- **Timetastic import:** a row that needs a day length now lists the bookings that need it and says when the opening balance was confirmed in hours. [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/)
- **Timetastic import:** a top-up that ticks only some people no longer blocks the people left unticked. They keep their figures. [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/)
- **Help, Timetastic import:** batch size is your choice. **Pick the next 5** is a shortcut, and you can tick any number of people or everyone not yet imported. We suggest 5 to 10. [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/)
- **My Schedule:** your shifts now show when you sign in. Before, every signed-in staff member saw "No shifts scheduled". [My Schedule]({{ site.baseurl }}/docs/app/my-schedule/)

## 16 November 2026

- **Timetastic import:** a half day that was not charged now says which booking date the Half day rule must cover, and to press **Run the leave import again** after setting it. [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/)
- **Timetastic import:** setting the Half day rule after an import, then running the leave import again, now charges the half days the earlier run left out. [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/)
- **Timetastic import:** answering the full-time day on the rules sheet no longer fails with "SETTING_NOT_AUTHORISED" when you admin more than one organisation. [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/)
- **Staff app:** cancelling a pending request now takes its hours off "awaiting approval" on your balance card straight away. [Staff App]({{ site.baseurl }}/docs/app/staff-app/)

## 15 November 2026

- **Staff app:** there is now a **?** button at the top that opens help for the page you are on. [Staff App]({{ site.baseurl }}/docs/app/staff-app/)
- **Help:** every main page's **?** now opens help for that page, including Leave Admin, Rule Book, My Settings (Telegram) and Time in Lieu. [Leave Admin]({{ site.baseurl }}/docs/app/leave-admin/)
- **Leave Admin:** shows one menu and one **?**, not two. [Leave Admin]({{ site.baseurl }}/docs/app/leave-admin/)
- **Leave Requests:** the page explains its filters and downloads, and a request with no figure reads "Days not calculated" with the reason. [Leave Requests]({{ site.baseurl }}/docs/app/leave-requests/)
- **Leave Requests:** the **Import Balances** button is gone. Load balances with the Timetastic import instead. [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/)
- **Time in Lieu:** changing **Date Earned** no longer stops Add TOIL or Bulk Add from saving. [Time in Lieu (TOIL)]({{ site.baseurl }}/docs/app/toil/)

## 14 November 2026

- **Roster:** dropping a person on a day now opens the shift card with their home room and suggested times to check, instead of saving a shift straight away. [Roster]({{ site.baseurl }}/docs/app/roster/)
- **Roster:** past days are locked, and leave days say why they can't be rostered when you hover. [Roster]({{ site.baseurl }}/docs/app/roster/)
- **Roster:** with no rooms set up, the roster says to add rooms first and links to them. [Roster]({{ site.baseurl }}/docs/app/roster/)
- **Roster:** confirmations and errors show as an on-screen message, and Help guides you through the week. [Roster]({{ site.baseurl }}/docs/app/roster/)
- **Timetastic import:** Help now walks you through the current import step, and the help link opens this site. [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/)
- **Timetastic import:** half days follow your half-day rule, and every rounded half day explains its extra minute. [Timetastic import]({{ site.baseurl }}/docs/app/timetastic-import/)
