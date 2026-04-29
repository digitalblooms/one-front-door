# Claude design prompt — WhatsApp mockup
*The prompt used to generate the One Front Door mobile mockup.*

This is the prompt as pasted into Claude. It produced `04_WhatsApp_mockup.html` on the first attempt. Reusable for any other WhatsApp-based service mockup — swap the conversation script.

---

Create an interactive HTML mockup of a WhatsApp conversation, styled to look exactly like the real WhatsApp mobile interface (iOS or Android — pick one and stay consistent). The mockup demonstrates an AI-powered wellbeing signposting service called **"One Front Door"** that residents in a London neighbourhood interact with directly inside WhatsApp.

## Visual requirements

- Render inside a phone frame (roughly 390 × 844px, iPhone proportions) so it reads as a real mobile screen, not a desktop chat.
- WhatsApp's actual visual language: the green header bar (`#075E54` / `#128C7E`), the cream/beige chat background with the subtle pattern, message bubbles with the correct colours (incoming = white, outgoing = light green `#DCF8C6` with the little tail), timestamps, double blue ticks for read receipts, and the input bar at the bottom with the paperclip, camera, and microphone icons.
- At the top of the chat, show the contact as **"One Front Door"** with a small avatar (use a simple icon — an open door, a heart, or similar), a "last seen" or "online" status, and a small **"Service account"** or **"Verified"** badge so it's clear this is a service, not a person.

## The conversation to render

Show it as if mid-scroll, with these messages in order:

1. *Resident, in English:* "I haven't really spoken to anyone in two weeks and I keep crying"
2. *One Front Door, reply:* "That sounds really hard. Two quick questions so I point you to the right thing — what language would you prefer to chat in?" with three quick-reply buttons underneath: **English**, **العربية**, **دری**
3. *Resident taps:* "English"
4. *One Front Door:* "Would you rather talk one-to-one with someone, or be around other people doing something together?" with two quick-reply buttons: **One-to-one**, **Around people**
5. *Resident taps:* "Around people"
6. *One Front Door:* "And are you free this week, or is next week better?" with quick replies: **This week**, **Next week**
7. *Resident taps:* "This week"
8. *One Front Door:* sends a "typing…" indicator briefly, then a single rich message with three options laid out as a clean card list inside the bubble:
   - **Wellbeing Café, Camden Town** — Tuesday 2pm · free · drop in, no booking needed
   - **Walk & Talk group, Regent's Park** — Wednesday 10am · 4 spaces left
   - **Cook for Good community lunch** — Friday 12pm · free

   Below the list, a softer line: *"If at any point you feel unsafe, Samaritans is 116 123, free, 24/7."*

   And three action buttons: **Book Tuesday**, **Book Wednesday**, **Book Friday**
9. *Resident taps:* "Book Tuesday"
10. *One Front Door:* "Done. I've let the Wellbeing Café know to expect you. Aisha, one of the volunteers there, speaks Dari and Arabic too. Want me to send a reminder Tuesday morning?" with quick replies: **Yes, send reminder**, **No thanks**

## Design details that matter

- Use real WhatsApp typography (system font stack — SF Pro on iOS, Roboto on Android).
- Quick-reply buttons should match WhatsApp Business API button styling (rounded, light background, sit just below the message bubble, separated by thin dividers).
- The card-style listing in message 8 should look like a WhatsApp interactive list message — bordered, slightly inset, with each option clearly tappable.
- Show realistic timestamps (a couple of minutes apart) and read receipts.
- Include the WhatsApp "end-to-end encrypted" notice at the very top of the chat.
- Keep the whole thing scrollable so the full conversation is reachable.

## What I do *not* want

- No fake desktop browser frame — this is a phone.
- No marketing copy, no logos other than WhatsApp's, no "demo" watermarks.
- No invented features that weren't in the conversation above.
- The AI should never claim to diagnose or counsel — it signposts only.

## Output

A single self-contained HTML file using inline CSS (no external dependencies). Make it pixel-careful — it should be screenshottable for a slide deck and pass for a real WhatsApp screen at first glance.
