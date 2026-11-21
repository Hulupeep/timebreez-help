---
layout: default
title: Employees
parent: Page by page
nav_order: 4
permalink: /docs/app/employees/
---

# Employees

**Who uses it:** admins and managers. In the menu: **Employees**.

## The list

Filter by **Active**, **Inactive**, **Historical imports** or **All**. Historical imports are people brought across from Timetastic who have already left: they are kept so past leave adds up, and they never get a login. Use **Invite Employee** or **+ Add Employee** to add someone.

Open a person's card to see their **Employment Terms**: status, hours per week, and their working pattern. Choose the **Allowance unit** (days, hours or minutes), enter the scheduled minutes for each weekday, and press **Confirm working pattern**. Leave costs are worked out from this pattern, so confirm it before approving their leave.

The card's balance says which leave year it is for, for example "in 2026". Once next leave year is open, a second line shows it on its own, for example "Annual Leave 2027: 20 days left". Leave booked in next year comes off next year's allowance, never this year's. Carry-over is added at year end.

## Inviting someone

Timebreez does not email invites yet. You send the link yourself.

1. Press **Invite Employee**, enter their email address and role, and create the invite.
2. A link appears with **Copy link**. Copy it and send it to them, for example by text or WhatsApp.
3. You can copy the link again later from **Pending Invitations**, next to their invite.

If the email already has a pending invite, you are told to copy its link from Pending Invitations instead.

### What the person sees

The link opens **Join your team on Timebreez**.

- They enter the email address you invited and press **Send me a sign-in link**. They open that email and it brings them back to finish joining.
- If the email does not arrive, they can press **Send the link again** (only the newest email works), **Use a different email**, or **Continue with Google** if that address is a Google account.
- The page says who the invite is for, for example "This invite is for Mary Murphy", with the email partly hidden.
- If they are already signed in with the invited email, it asks "Join with this account?" with **Join** or **Use a different account**.
- If they are signed in with a different account, there is no **Join**. The page says the invite is for someone else and to press **Use a different account** and sign in with the email the invite was sent to.
- If the invite has expired, been used or been revoked, the page says so straight away.

| Message they may see | What to do |
|---|---|
| This invite link does not work any more | It expired, was used or was revoked. Send a new invite |
| That is not the email address this invite was sent to | They enter the address you invited, or you send a new invite |
| ... is already a member of this organisation | They are signed in with an account that is already in. **Open your dashboard**, or **Use a different account** and sign in with the invited email |
| ... is already joined to this organisation as Mary Murphy, not as the person this invite is for | That login is on another person's staff record. The invite stays pending until the invited person joins with their own account. **Join** is hidden, because it would fail the same way |
| This invite was sent to ..., but that login is already attached to ...'s staff record | One login can only be on one staff record, so a new invite gives the same message. An admin disconnects the login from the wrong record (see [The login on a record](#the-login-on-a-record)), then the person opens the link again |
| The person this invite is for has already joined Timebreez with a different account | They sign in with that account, or you check the staff list |

## A person's page

Click a name to open their page. Tabs: **Schedule**, **Leave**, **Compliance**, and for admins and managers **Payroll** and **History**.

### The login on a record

Admins see a **Login** box on each person's page:

- "Signed in as ..." names the login that opens this record.
- "No login is connected" means nobody has joined as this person yet. Send an invite.

If the wrong account joined as this person, press **Disconnect account**, add a reason if you like (it is kept in the audit trail), and confirm. The person's record, leave and history stay. That login no longer opens the record. Send the person a new invite to connect the right account. You cannot disconnect your own login.

### Payroll tab

**How they are paid** shows the pay in force today: **Hourly** or **Salaried**, the hourly rate, and how often they are paid (weekly, fortnightly, every four weeks or monthly), with the date it applies from, who recorded it and why.

To change it, an admin presses **Change from a date** (or **Record pay** if there is none), fills in the type, rate, how often, **Applies from** and **Why**, and saves. An hourly person needs a rate; for a salaried person it is optional. The earlier record is kept. The payroll file uses whichever record applies on the last day of the pay period. A change with a future date shows underneath as "From ...".

With no pay record yet, the payroll file uses the older rate on the staff profile, if there is one.

**PPS number** (or **Tax number** outside Ireland) is optional: payroll matches people by Works No. Only admins can see it. It shows masked. To see the full number, write why you need it and press **Show full number**; every full view is logged. Press **Record** or **Change** to enter it, with a reason.

**Example.** Mary Murphy moves from €14.00 to €14.80 an hour from 1 January. You press **Change from a date**, enter 14.80, applies from 1 January, why "new rate per the payroll register". Her December payroll still uses €14.00; January's uses €14.80.

### Leave tab

Shows their Annual Leave and Sick Leave balances, their requests (pending ones are marked "Pending approval"), and **Balance history & adjustments**: every change to the balance, with the reason.

### Correcting a balance

1. In **Balance history & adjustments**, press **Adjust** next to the balance.
2. Enter the amount in **Days** or **Hours**. Days are only offered when the person has a confirmed day length; otherwise you see "This person has no confirmed day length, so enter the adjustment in hours".
3. Write the **Reason (required)** and the **Effective date**.
4. Press **Post adjustment**.

An adjustment can take a balance below zero. You are warned first. Nothing is overwritten: the adjustment is added to the history with your reason.

**Example.** Mary Murphy was owed one day from last year that Timetastic did not carry over. Her day is 495 minutes. You adjust +1 day, reason "carry-over agreed for 2025", effective 1 January. Her history shows +495 minutes with that reason.

Managers, HR and admins can adjust. Staff cannot.
