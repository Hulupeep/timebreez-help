---
layout: default
title: Find Cover
parent: Page by page
nav_order: 31
permalink: /docs/app/find-cover/
---

# Find Cover Help

{: .note }
This page has not been checked against the current app yet. The pages listed under [Page by page]({{ site.baseurl }}/docs/app/) as checked are up to date.


{: .tip }
On the roster you can also ask for cover on Telegram when someone leaves early or doesn't turn up: the first yes gets the shift. See [Someone leaves early or doesn't turn up]({{ site.baseurl }}/docs/app/roster/#someone-leaves-early-or-doesnt-turn-up).

Requests go out only through the apps your organisation switched on in [Settings, Messaging]({{ site.baseurl }}/docs/app/settings/#messaging). A phone number is only needed when nothing else can reach the person. The button names the apps, for example **Send request via Telegram or Email (2)**.

## What It Does

When someone can't work their shift, quickly find an available replacement from your team.

## Why It Matters

Emergencies happen. Find Cover helps you fill gaps fast without endless phone calls or WhatsApp messages.

## How To Use It

1. From a shift, click **"Find Cover"**
2. See which **staff are available**
3. **Send a cover request** to one or more people
4. **Wait for responses**
5. **Confirm the replacement**

## Visual Diagram

```mermaid
flowchart TD
    A[Shift needs cover] --> B[Click Find Cover]
    B --> C[See available staff]
    C --> D[Send request to staff]
    D --> E{Someone accepts?}
    E -->|Yes| F[Shift reassigned]
    E -->|No one yet| G[Send WhatsApp reminder]
    G --> E
```

## Common Questions

### How do staff respond to cover requests?

They'll get a WhatsApp message or notification. They can accept or decline directly.

## Tips

- Send requests to multiple people for faster responses
- Check who's qualified for the room first
