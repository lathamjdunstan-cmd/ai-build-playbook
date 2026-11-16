# Adeline Estate: a website and CRM I shipped, and the AI team that runs on them

Adeline Estate is a wedding and accommodation venue I co-own in the Hunter Valley, NSW. I built its website and a custom CRM with AI tools. A team of AI agents on Grok Bot now works the pipeline, the inbox and the books under my direction.

[Back to the playbook](README.md)

---

## Evidence standard

- Checked 16 November 2026. Read-only. All times are Sydney time (AEDT).
- Sources are my CRM, the bookings inbox, my WIP Sheet and Command Centre (both Google Sheets) and the agents' own reports.
- Some records were written by the agents. Treat them as recorded operating results, not an independent audit.
- Schedules are as each agent reported its own routines. The routine settings themselves weren't readable.
- "Sent" means recorded as sent. It does not mean delivered.
- **UNSURE** marks anything the records don't support or that conflicts.

---

## 1. Shipped: [adelineestate.au](https://www.adelineestate.au)

**The website.** Built in Lovable, with Claude Design and ChatGPT.

**A custom CRM.** I built the back end and sales pipeline in Lovable with ChatGPT and Grok Bot agents. No off-the-shelf CRM. It captures venue guide requests and enquiries from the site into a leads table, with stages from new enquiry to booking won. The agents now read and update it as part of their routines.

**What it handles.** 64 wedding leads were logged from 13 September to 14 November 2026: 35 venue guide requests and 29 enquiries. (Lovable CRM, leads table, wedding only, test rows excluded. 62 distinct emails. 6 rows were hand-entered.)

**Known open issues:**
- Some redirects return HTTP 200 instead of 301. The records said the fix needed Cloudflare rules, but the domain is managed at GoDaddy, not Cloudflare. The redirect fix is still open.
- **Fixed 16 November 2026:** some replies bounced from Hotmail addresses because the domain had no DKIM or DMARC (diagnosed 10 November). I added both records. A test from the bookings inbox now passes SPF, DKIM and DMARC, and a test to a Hotmail address landed in the inbox.

---

## 2. The team

Seven role agents and one manager Bot, all on **Grok Bot** (SpaceXSI). Start dates are each agent's creation date.

| Agent | Role | Triggers | Connects to | Does on its own | Waits for me | Started |
|---|---|---|---|---|---|---|
| **Primary Bot** | Team manager | Daily 7:54am visit heads-up (only if a visit is today or tomorrow). Mon 8:41am waiting-on-me list. Tue 9:12am accountability check. | Other Bots, bookings Gmail and Calendar, WIP Sheet, Google Drive | Hands out tasks, chases owners, compiles lists and digests | Any supplier or client message | 2 Oct |
| **Ava** | Executive assistant | Weekday 8am brief. 8am and 4pm WIP checks. Fri 4:04pm numbers chase. Fri 4:47pm handoff. | WIP Sheet, bookings Gmail, Calendar, Drive, a shared context folder | Keeps the WIP tidy, chases owners, compiles weekly numbers, writes briefs | Anything sent outside the team. Some WIP writes needed Auto-review approval. | 13 Sep |
| **Alex** | Sales coordinator | Lead check three times an hour, 7am to midnight. Inbox watch every 30 min. Daily 9:43am follow-ups. Fri 2:20pm sales pack. Monday pipeline review (time **UNSURE**). | bookings Gmail, Calendar, Lovable CRM, WIP, Brevo (some sends), Command Centre (read-only) | First replies to clean wedding leads, nurture follow-ups, date replies after checking bookings, CRM and WIP updates | Anything unusual (saved as a draft), non-standard pricing, discounts, Airbnb messages, calendar RSVPs, bounced addresses, booking and deposit stages | 11 Sep |
| **Riley** | Operations coordinator | Airbnb alert check every 30 min, 7:27am to 9:57pm. Post-checkout checks. Fri 3:13pm ops numbers. | Outlook (Airbnb notifications), Airbnb host site in a shared browser, bookings Gmail, Calendar, WIP | Vets Airbnb enquiries using a guest-vetting skill. Watches stays, deliveries and changeovers. | Every Airbnb guest message (since 7 Oct). Booking cleaners. | 13 Sep |
| **Quinn** | Finance coordinator | Mon 8:13am cash and overdue summary. Friday finance pack by 4pm. | bookings Gmail, WIP, Xero (read-only; bank lines blocked by account role) | Logs invoices. Checks maths, duplicates and superseded versions. Writes packs. | All payments and quote acceptances | 13 Sep |
| **Maya** | Marketing coordinator | Fri 2:23pm enquiry summary (from 9 Oct) | bookings Gmail, WIP | Counts enquiries by source. Drafts listing work. | Publishing and spending | 13 Sep |
| **Morgan** | Strategy and performance | Mon 8:59am management pack. Friday Command Centre entry by 6pm. | Command Centre, WIP, report files | Analysis, weekly packs, Friday rows | All decisions | 13 Sep |
| **Eden** | Product and guest experience | Mon 9:13am, first Monday of the month only (first run 2 Nov) | bookings Gmail, WIP, Google Drive | Feedback review, checklists, venue guide fact-checks | Offer and policy changes | 13 Sep |

Out of scope here: a separate OpenAI assistant I also use (product name **UNSURE**), and my earlier n8n and Telegram agent, which is a different project.

---

## 3. How I stay in control

**Two kinds of control.** A few are platform settings: Grok Bot's Auto-review approval cards and saved Allow rules. Most are standing rules I gave in chat. Rules in chat can fail, and one did (see section 5).

**How I approve.** Plain words in the Grok Bot chat. Draft cards where I press Send. Drafts left in the bookings inbox. Auto-review approval cards.

**Standing rules, in order:**
- **7 Oct:** no automatic Airbnb guest messages. Every one needs my OK.
- **8 Oct:** a WIP update doesn't prove anyone saw it. It never authorises outreach.
- **11 Oct:** standing permission for lead replies and follow-ups. Airbnb, RSVPs and anything unusual still wait.
- **Lead guardrails:** real email, 120 guests or fewer, no clearly low budget, nothing odd. Otherwise draft only. Never promise availability. Maximum 5 sends per run.
- **28 Oct:** check Sent for that person before any send.
- **30 Oct:** "Reply STOP" only on nurture to non-responders.
- **5 Nov:** read the full Airbnb thread before any guest rundown or draft.
- Finance is read-only and draft-first.

**Fully automatic:** first replies to clean wedding leads, daily follow-ups, inbox watches, CRM and WIP updates, invoice logging and checks, briefs, WIP checks, weekly packs and Command Centre entries.

**Always waits for me:** payments and quotes, Airbnb guest messages, tour and visit confirmations, booking cleaners, one-off client and supplier replies, pricing exceptions.

**How I review:** a daily heads-up and 8am brief. Monday cash, waiting-on-me and strategy packs. A Tuesday accountability check. Friday packs feed the Command Centre by 6pm. A monthly guest feedback review. Decisions are logged on the WIP Sheet and in a decision log file.

---

## 4. Results

| Result | Period | Source |
|---|---|---|
| **Venue guide speed.** Before auto-replies, the median first response was 251 minutes (25 leads, agent-entered timestamps). After auto-replies began on 11 October, 15 of 20 measured guides went out within 20 minutes. Median 10.45 minutes. | 13 Sep to 11 Oct, then 14 Oct to 14 Nov | CRM submission times matched to sent guides in the bookings inbox |
| **Follow-ups.** At most 142 automated follow-ups. 191 in total, including a 7 October batch of 42 sent by a separate assistant and 7 approved one by one. | 12 Oct to 16 Nov | Alex's Friday packs and daily reports. Not recounted in Gmail (**UNSURE**). |
| **Invoices.** 31 invoices logged, worth A$20,756.40. Three superseded versions caught. One A$1 arithmetic error caught. One possible duplicate labour charge of A$210 flagged. | 13 Sep to 16 Nov | WIP FINANCE and COMPLETED tabs |
| **Scam caught.** A fake video-call invite linked to a remote-access installer. Moved to spam. Records say nobody clicked. | 4 to 5 Oct | WIP |
| **Reporting rhythm.** Monday management packs saved from 21 Sep. Friday numbers handoffs every week from 2 Oct to 13 Nov. 36 completed items on the WIP. | 21 Sep to 16 Nov | Saved packs, WIP |

**Invoice caveats.** The total uses the corrected figure on one invoice (A$20,755.40 as printed). Quotes and superseded versions are excluded. 19 of 31 come from one contractor. 6 are open. The rest are reported paid, but none are bank-verified, because Xero bank access is blocked. The possible A$210 duplicate was flagged on 28 to 31 October. Both bills were later reported paid on 5 November, and the duplicate is still unconfirmed. It was not caught before money went out.

---

## 5. What went wrong

| Date | What happened | How it was caught | What changed |
|---|---|---|---|
| 7 Oct | A duplicate Airbnb message went out after the send hung on "Sending..." | Recorded | Every Airbnb guest message now needs my OK |
| 19 Oct | A date reply auto-sent after a two-hour review window passed without my answer | Recorded | Whether that timeout still applies is **UNSURE** |
| From 20 Oct | Brevo email authentication was incomplete. Delivery and junk-folder risk. | Records | Brevo paused. Gmail used instead. Domain DKIM and DMARC fixed 16 Nov for Gmail sends. Brevo is not yet authenticated and stays paused. |
| 28 Oct | A scheduled lead check and a manual reply both sent a guide to the same lead, 37 seconds apart | The agent found it checking Sent. I asked why. | Hard rule for all agents: check Sent before any send. Built into the lead and follow-up routines. |
| 29 Oct | A follow-up run failed | Caught up at 1:44pm | Cause not logged |
| 30 Oct | A call confirmation to an engaged lead ended "Reply STOP to unsubscribe" | I caught it | STOP only on nurture to non-responders. Both routines updated, confirmed 3 Nov. |
| 5 Nov | Riley built a check-in rundown from the calendar without reading each guest's thread | I caught it | Always read the full thread first. An Auto-review rule was approved the same day (wording **UNSURE**). |
| 10 Nov | A held follow-up was sent | Recorded | **UNSURE** |
| 10 to 11 Nov | Routine wakes returned "Aborted" | Recorded | **UNSURE** |

---

## 6. Not claimed

These figures appeared in summaries but aren't backed yet: 59 guides sent, 528 emails sent, about 162 WIP tasks and 1 wedding won. All **UNSURE**.

## 7. What this deployment shows

- **The measurable win is speed.** Median venue guide response dropped from hours to about 10 minutes once sending was automated with guardrails.
- **The failures I logged were mostly coordination, not model ability.** Two senders, a missed check, a hung send. Each became a written rule.
- **Most blockers were access.** Xero bank lines, redirects and email authentication all stalled on permissions or setup. The email one took two DNS records to fix once I found where the domain was managed.
- **Rules in chat are not gates.** The 19 October and 10 November sends show the gap. Where a mistake is costly, the control has to live in the platform.
