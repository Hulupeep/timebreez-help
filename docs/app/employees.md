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

### Works No.

The **Works No.** is the person's employee number in your payroll system, for example **EMPID0000028** in Collsoft. Enter it with **Edit** on the person's card, in the **Works No.** field (older screens called it **Payroll ID**).

**Why it matters:** Collsoft matches each line of the [payroll file]({{ site.baseurl }}/docs/app/payroll/) to a person by Works No. If it is blank, that person's hours are not imported. If two people have the same one, one person's hours land on the other.

- An active person without one shows an amber **No Works No.** badge on their card. The **No Works No. (5)** button above the list shows only them; the number is how many there are.
- Saving a Works No. that another active person already has is refused, naming them, for example "EMPID0000028 is already Mary Murphy's Works No.". Capitals and spaces do not make it different. A leaver's old number can be reused.
- Clearing the field leaves the person with no Works No.
- The [Payroll]({{ site.baseurl }}/docs/app/payroll/) page lists anyone missing one before you download the file.

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
| ... has not been confirmed yet | They press **Use a different account**, sign in with the emailed sign-in link, then open the invite again |
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

**History (n)** lists every pay record, newest first, with who recorded it, when and why. The one in force today is marked **In force today**. A record that has not started yet can be taken back with **Withdraw (not started yet)** and a reason, for example "entered with the wrong date". A withdrawn record is crossed out, never deleted, and payroll ignores it. A record that has already started cannot be withdrawn: record a new one from a date instead.

**Why pay is recorded from a date:** a past payroll must come out the same every time you look at it. A pay rise is a new record from the date it starts, never an edit of the old one, so October's figures still use October's rate after the rise. Your payroll system (for example Collsoft) stays the master for rates; this record is so Timebreez's file and its explanations agree with it.

**PPS number** (or **Tax number** outside Ireland) is optional: payroll matches people by Works No. Only admins can see it. It shows masked. To see the full number, write why you need it and press **Show full number**; every full view is logged. Press **Record** or **Change** to enter it, with a reason. Press **Remove** and give a reason, for example "entered on the wrong person", to clear it.

Under the number, a line says how often it was viewed in full, for example "Viewed in full once. Last: ...", with who and why. **Show log** lists every time it was recorded, viewed in full or removed, by whom and why.

**Why PPS is kept, and why it is optional:** it gives the payroll person one place to find it. The payroll file never needs it, because the Works No. does the matching. It is a sensitive personal number, so managers cannot see it, it is masked even for admins, and each full view is logged with who looked and why.

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
