# Three Solutions Explored
*Generated from the Breakout Room <> Neighbourhood Labs session, 28 April 2026*

The breakout surfaced three distinct pains in the room. Below is one focused solution per pain — each small enough to test in a week, each playing to AI's real strength (admin and matching) without pretending it can replace the humans doing the actual work.

A shared design principle came out of the room: **don't build another app — surface through WhatsApp or whatever residents already use.**

---

## Solution 1 — "Pantry Relay"
### A WhatsApp-first surplus food matcher

**The pain.** Cook for Good and local pantries have surplus food appearing at unpredictable moments. The current workflow is a WhatsApp broadcast and hope someone with a car sees it in time. Logistics — not goodwill — is the bottleneck.

**What it does.** A pantry coordinator sends one WhatsApp message to a bot: *"40 hot meals, ready 6pm, need collected from Marchmont St, can split."* The AI parses it into structured fields (quantity, pickup window, location, divisible yes/no), then pushes a tailored alert to a pre-vetted list of drivers and receiving orgs whose stated availability matches. Drivers reply "yes" to claim a portion. The bot confirms back to the coordinator: *"Aisha taking 15 to Somers Town hub, 6:15pm."*

**Example output** — what the coordinator sees in WhatsApp:

> ✅ Logged: 40 meals, 6pm pickup, Marchmont St
> Alerted 7 drivers within 1km radius and free this evening
> 6:08pm — Aisha (car, Somers Town) claimed 15
> 6:11pm — Tom (bike, Bloomsbury) claimed 10
> 15 meals still unclaimed — broadening alert to 2km

**Reusable how.** Twilio + Claude API setup; any borough or food network with a WhatsApp group already in flight can swap in their own driver list and pickup locations. No new app for residents to learn.

---

## Solution 2 — "23 Languages"
### A multilingual form-and-letter helper

**The pain.** Elderly and non-English-speaking residents — the Afghan community was named specifically — are locked out of housing, benefits, and council services that have moved online. Staff collectively speak 23 languages but can't always cover demand. Letters arrive in English; forms are in English; the digital front door is a wall.

**What it does.** A community champion (or the resident themselves, on a shared device at a community centre) photographs an English letter or form. Claude translates it into the resident's language, *explains what it actually means in plain terms*, flags any deadlines, and drafts a reply or fills the form based on a short voice conversation in the resident's language. The champion reviews before anything is submitted. AI absorbs the translation and form-filling admin; the human stays in the loop on judgement and safeguarding.

**Example output** — a resident brings in a Universal Credit letter:

> **Original (English):** "You must verify your identity within 14 days or your claim will be suspended."
> **In Dari:** [translated text]
> **What this means:** The DWP needs to confirm who you are. If you don't reply by 12 May, your benefit payments stop.
> **What to do:** Bring your passport or biometric residence permit to your nearest Jobcentre, or upload a photo on the GOV.UK site. I can help you do this now if you'd like.
> **Drafted reply (if needed):** [pre-filled form fields shown for champion review]

**Reusable how.** Runs as a simple web tool any community organisation can load on a tablet. The "trusted human reviews before send" pattern is the safeguarding answer to the open-consumer-platform risk the room flagged.

---

## Solution 3 — "One Front Door"  ⭐ *Selected for development*
### A wellbeing signposter with a 30-second triage

**The pain.** Six-week wait for 1-to-1 mental health support. Multiple directories exist (Camden Council, Mind, GP referrals, peer groups, wellbeing cafés) but no single accessible multilingual entry point. Residents bounce between options and give up.

**What it does.** A resident sends a voice note or text — in any language — describing how they're feeling and what kind of help they want. The AI doesn't diagnose. It asks two or three clarifying questions ("Are you wanting to talk to someone this week, or is this more about feeling less isolated day-to-day?"), then signposts to the *closest match available now*: a peer support group meeting Thursday, a wellbeing café with a free slot Tuesday, a crisis line if the language flags risk. It books the slot if the org has shared its calendar; otherwise it gives the right phone number and what to ask for.

**Example output** — resident texts: *"I haven't really spoken to anyone in two weeks and I keep crying"*:

> That sounds really hard. Two quick questions so I point you to the right thing:
> 1. Would you rather talk one-to-one, or be around other people doing something together?
> 2. Are you free this week, or is next week better?
>
> *[resident replies: "around people, this week"]*
>
> Three options near you this week:
> • **Wellbeing Café, Camden Town** — Tues 2pm, free, drop-in, no booking needed
> • **Walk & Talk group, Regent's Park** — Wed 10am, 4 spaces left
> • **Cook for Good community lunch** — Fri 12pm, free
> If at any point you feel unsafe, Samaritans is 116 123, free, 24/7.

**Reusable how.** Same matching engine as the food relay, just pointed at wellbeing slots instead of meals. This is where the broader "Camden Task" idea from the room earns its keep — but scoped to one domain (wellbeing) so it's testable in a week, not a year.

---

## Why Solution 3 was chosen

The group picked this one because it had the broadest reach across the pains the room actually surfaced — language access, the six-week wait, and fragmented directories — while still being scopeable to a four-week pilot.

Solutions 1 and 2 remain valid candidates for follow-on builds. The matching engine underneath all three is structurally the same; building one well unlocks the others.
