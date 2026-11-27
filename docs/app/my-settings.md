---
layout: default
title: My Settings and Telegram
parent: Page by page
nav_order: 9
permalink: /docs/app/my-settings/
---

# My Settings and Telegram

**Who uses it:** everyone. In the menu: **My Settings**.

My Settings has three tabs: **Notifications**, **Calendar** and **Messaging**. **Messaging** lists the messaging apps your organisation uses (an admin chooses them in [Settings, Messaging]({{ site.baseurl }}/docs/app/settings/#messaging)). On **Notifications**, the column for Telegram is called **Messaging app**.

## Link Telegram

Once Telegram is linked you get leave approvals and updates there, and you can request time off without opening Timebreez.

1. Open **My Settings**, tab **Notifications**, and press **Connect Telegram**. In the [staff app]({{ site.baseurl }}/docs/app/staff-app/#settings), it is first on the **Settings** tab.
2. Your personal link is ready. Press **Open Telegram**. If your browser asks to open the Telegram app, say yes.
3. Press the **Start** button at the bottom of the chat. On the Telegram web page it says **Start Bot**. Pressing Start sends your personal code, so the bot knows it is you. Typing the word "start" does not work.
4. The bot replies **"You're linked"**. You can close the page. The card now shows **Connected**.

**Browser says "invalid response" or "not secure"?** Your network is blocking the Telegram web link. Nothing is wrong with your link: use one of the two ways below.

**No Start button, or Telegram didn't open?** Press **Open straight in the Telegram app**, or press **Copy** and send the copied message to the bot. It does the same as pressing Start. If the link has expired, press **Get a new link** and start again.

To unlink, press **Disconnect**, or send `/stop` to the bot.

## What you can send the bot

Message the bot directly, not in a group. Type **/** in the chat to see the list of commands, so you don't have to remember them.

| Send | What happens |
|---|---|
| `/shifts` | Your shifts and leave for the next 7 days, one line a day, with the room. `/shifts next week`, `/shifts fri` or `/shifts 1-5 dec` work too. **Earlier** and **Next 7 days** move along a week |
| `/off` | Asks which day, with **Today**, **Tomorrow** and **Another day…** buttons, then which leave type |
| `/off today sick`, `/off fri am`, `/off 1-3 dec annual` | Type the day in plain words, and the leave type if you like. `am` or `pm` asks for a morning or afternoon. Dates like `2026-12-01` or `1/12/2026` work too |
| `/sick` | Off sick today, one tap to confirm. `/sick tomorrow` or `/sick am` work too |
| `/bal` | Your balances. Shown in hours if your allowance is in hours, otherwise in days |
| `/status` | Your requests and whether they are waiting for a decision, approved, declined or cancelled. A declined request shows the reason |
| `/cancel` | Lists leave you can cancel. Pick one, then **Yes, cancel it** or **Keep it**. The bot says how much went back and what you now have left |
| `/carry` | Your unused days, the carry-over limit and any request. `/carry 2` asks to carry 2, `/carry withdraw` takes back a waiting request. [Carry-over]({{ site.baseurl }}/docs/app/carry-over/) |
| `/whosout` | Managers only: who is off today. `/whosout week` shows the next 7 days |
| `/demo` | A practice run before you use the bot for real, with **My shifts**, **Time off**, **Off sick** and **My balance** buttons. Every screen is the real one, but nothing reaches your manager, the rota or payroll. Each reply starts with "DEMO, nothing is booked." After a practice booking, **Skip ahead: your manager approves** shows the approval message. Works before you link Telegram (with made-up data). To type in the demo, put `/demo` first, for example `/demo off fri`. `/practice` and `/tour` do the same |
| `/help` | Lists what you can send |
| `/stop` | Unlinks Telegram |

Before anything is booked, the bot shows a card: the leave type and day, what it uses (for example "Uses: 1 day"), and your balance now and after. Both balance figures come from Timebreez itself, the same as the app. If the request would take more than you have, or the leave year isn't open yet, the card says so with a ⚠️ line and what to do. Press **Confirm** to send it to your manager. For a single day you can switch between **Full day**, **Morning only** and **Afternoon only**. **Different type** and **Cancel** are there too. If the dates are locked for that leave type, the card says so and has no Confirm.

You can also just write, for example "sick today", "off tomorrow", "how many days have I got" or "am I working fri", and the bot treats it like the command.

If the bot says "Link your Telegram first", do the steps above again.

## Alerts for admins

If you are an admin with Telegram linked, the bot tells you when:

- someone asks for leave: who, which type, the dates, what it costs, and their balance now and after. If it is more than they have left, it says it needs your decision. **Review requests** opens Leave Requests;
- someone withdraws a request or cancels approved leave: how much went back to them. For approved leave it also says any shifts cancelled for it are back on the roster.

The new-request alert also says, for each day the person is rostered, how their room is left: for example "Mon 7 Dec, Toddlers: 2 left, 3 needed (15 children enrolled, 1:5). Short 1. Free floater: Mary Murphy." If a room has no child numbers or ratio set, it says it can't check. If the person isn't rostered on those dates, it says no room is affected.

### Approve or decline in Telegram

Admins and managers get **Approve** and **Decline** buttons on the new-request alert.

- **Approve** shows what will come off the balance, for example "Comes off: 2 days". Press **Yes, approve** to confirm you've checked that figure. If the figure changed since the alert, the bot shows the new one and asks again. If it can't work out the figure yet, it asks you to decide in Timebreez.
- **Decline** asks "Decline ...?". Press **Yes, decline**.
- **Back** changes nothing.

The same rules apply as in the app: you can't decide your own request, and only a request still waiting can be decided. When it's done the bot says "Approved" or "Declined" and the person is told.

### Morning message: who's off today

Each morning every admin and manager gets one message by email, and on Telegram if linked: who is off today, each room's adults against its ratio, who could cover (floaters first, then a room with an adult to spare), and the requests waiting, with Approve and Decline buttons on Telegram. An admin sets the time, the time zone, **Weekdays only**, and whether to send it at all, on the **Leave check** page.

Admins and managers also get an email for each new request, unless they switched that email off. Bookings brought in by the Timetastic import do not send alerts.

## Calendar

The **Calendar** tab gives you a feed address. Add it to Google Calendar, Outlook or Apple Calendar and your shifts and approved leave appear there automatically.
