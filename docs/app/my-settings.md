---
layout: default
title: My Settings and Telegram
parent: Page by page
nav_order: 9
permalink: /docs/app/my-settings/
---

# My Settings and Telegram

**Who uses it:** everyone. In the menu: **My Settings**.

My Settings has three tabs: **Notifications**, **Calendar** and **WhatsApp**. WhatsApp is not available yet.

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
| `/bal` | Your balances, in days and minutes |
| `/status` | Your requests and whether they are pending, approved or denied |
| `/whosout` | Managers only: who is off |
| `/stop` | Unlinks Telegram |

If the bot says "Link your Telegram first", do the steps above again.

## Calendar

The **Calendar** tab gives you a feed address. Add it to Google Calendar, Outlook or Apple Calendar and your shifts and approved leave appear there automatically.
