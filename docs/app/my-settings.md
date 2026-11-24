---
layout: default
title: My Settings and Telegram
parent: Page by page
nav_order: 9
permalink: /docs/app/my-settings/
---

# My Settings and Telegram

**Who uses it:** everyone. In the menu: **My Settings**.

My Settings has three tabs: **Notifications**, **Calendar** and **WhatsApp**. WhatsApp is not available yet. On **Notifications**, the column for Telegram is called **Messaging app**.

## Link Telegram

Once Telegram is linked you get leave approvals and updates there, and you can request time off without opening Timebreez.

1. Open **My Settings**, tab **Notifications**, and press **Connect Telegram**.
2. Your personal link is ready. Press **Open Telegram**. If your browser asks to open the Telegram app, say yes.
3. Press the **Start** button at the bottom of the chat. On the Telegram web page it says **Start Bot**. Pressing Start sends your personal code, so the bot knows it is you. Typing the word "start" does not work.
4. The bot replies **"You're linked"**. You can close the page. The card now shows **Connected**.

**No Start button, or Telegram didn't open?** Press **Open straight in the Telegram app**, or press **Copy** and send the copied message to the bot. It does the same as pressing Start. If the link has expired, press **Get a new link** and start again.

To unlink, press **Disconnect**, or send `/stop` to the bot.

## What you can send the bot

Message the bot directly, not in a group.

| Send | What happens |
|---|---|
| `/off 2026-12-01` | Requests one day off. The bot asks which leave type, then asks you to confirm |
| `/off 2026-12-01 2026-12-03` | Requests a range. Day/month/year works too: `/off 1/12/2026` |
| `/bal` | Your balances. Shown in hours if your allowance is in hours, otherwise in days |
| `/status` | Your requests and whether they are waiting for a decision, approved, declined or cancelled. A declined request shows the reason |
| `/cancel` | Lists leave you can cancel. Pick one, then **Yes, cancel it** or **Keep it**. The bot says how much went back and what you now have left |
| `/carry` | Your unused days, the carry-over limit and any request. `/carry 2` asks to carry 2, `/carry withdraw` takes back a waiting request. [Carry-over]({{ site.baseurl }}/docs/app/carry-over/) |
| `/whosout` | Managers only: who is off today. `/whosout week` shows the next 7 days |
| `/help` | Lists what you can send |
| `/stop` | Unlinks Telegram |

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
