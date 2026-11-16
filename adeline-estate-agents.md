# Adeline Estate: seven business agents on Grok Bot

Adeline Estate is a wedding and accommodation venue I co-own in the Hunter Valley, NSW. Seven AI agents on Grok Bot run parts of the business under my direction. This page documents the system and what the records show it did.

[Back to the playbook](README.md)

---

## Evidence standard

- These facts come from my operating WIP, Command Centre and emails. I checked them through 16 November 2026.
- Some entries were written by the agents themselves. Treat them as recorded operating results. They are not an independent audit of the runtime.
- "Sent" means recorded as sent. It does not mean delivered.
- **UNSURE** marks anything the records don't support or that conflicts.
- The operating records cover September to November 2026. The exact go-live date of each agent is **UNSURE**.

## System boundaries

- **Grok Bot** runs the seven agents. **Routines** are its recurring or event-triggered workflows.
- A record showing an agent used Gmail or another system doesn't prove the exact plugin, API, browser connection or permission scope. Current connector configuration is **UNSURE** unless stated.
- My ChatGPT assistant is a **dot**. It is separate from the seven agents.
- My earlier n8n, Railway, Telegram and Claude API build is a separate project. It is not the runtime for these agents.
- Automatic sync between Grok Bot and my dot is **UNSURE**. There is no evidence of a shared database or a specific integration architecture.
- All seven agents maintain WIP records and produce or update working files.

## The agents

| Agent and role | Recorded triggers | Systems used in the records |
|---|---|---|
| **Ava**, executive assistant | Morning and afternoon WIP checks. Friday reporting chase and handoff. Logged runs fall around 8 am and 4 pm. The exact configured schedule is **UNSURE**. | Gmail, master WIP (Google Sheets), Command Centre checks, departmental reporting files. |
| **Alex**, sales coordinator | Hourly first-reply routine. Daily 9:43 am follow-up routine. Friday 2:20 pm sales-pack routine. Website forms and email supply inputs. A direct form-submission webhook is **UNSURE**. | Gmail, Google Calendar, Lovable CRM and lead records, WIP, read-only Command Centre checks. Brevo sends recorded from 15 October, later paused. |
| **Maya**, marketing coordinator | Friday 2:23 pm enquiry-count routine. Friday website and listing checks around 2:30 pm. Other triggers **UNSURE**. | Gmail form notifications, WIP, marketing files, the public website, a Lovable project. Direct database access **UNSURE**. Some directory changes blocked by missing access. |
| **Riley**, operations coordinator | 8 am day-before cleaner routine. 12:07 pm check-in routine. Post-checkout checks. Current replacement-cleaner automation **UNSURE**. | Gmail, Google Calendar, Airbnb host interface, Airbnb notifications via Hotmail, WIP, operations files. Airbnb API integration **UNSURE**. |
| **Quinn**, finance coordinator | Invoice emails and team handoffs. Friday finance pack due by 4 pm. Exact polling or event-trigger setup **UNSURE**. | Gmail, invoice attachments, WIP, finance files. Xero read access from 15 October. Bank statement lines blocked by account permissions. |
| **Eden**, product and guest experience | Monthly feedback review on the first Monday. Configured 7 October. First recorded review 2 November. Weekday WIP checks. | Gmail, Google Drive, WIP, product documents, an improvement register. Direct Airbnb review integration **UNSURE**. |
| **Morgan**, strategy and performance adviser | Monday management reviews. Friday Command Centre update due by 6 pm, after Ava's handoff. Exact automation schedule **UNSURE**. | WIP, Command Centre, departmental reports, management-review documents. Direct access to every underlying system **UNSURE**. |

## What they do and what comes to me

These are recorded operating rules. They are written instructions, not technically enforced approval gates. I have no configuration or code evidence of enforcement.

| Agent | Works on its own under standing instructions | Comes to me for a decision |
|---|---|---|
| **Ava** | Updates WIP status. Checks commitments. Chases missing reports. Prepares briefs and handoffs. | Business decisions and unresolved commitments. The full current approval policy is **UNSURE**. |
| **Alex** | Sends standard first replies and follow-ups. Checks for replies and earlier sends. Updates CRM and WIP. Stops follow-up when a lead replies, books or asks to stop. | Specific availability replies and resends. See the 19 October incident below. |
| **Maya** | Counts and deduplicates form submissions. Researches listings. Audits pages. Drafts changes. | Website publishing and directory changes. Approval doesn't mean access was available or the change succeeded. |
| **Riley** | Monitors bookings. Prepares operational updates. Sends notices within authorised routines. | Cleaner bookings, supplier commitments and site-visit confirmations. |
| **Quinn** | Logs invoices. Checks arithmetic. Flags possible duplicates. Separates quotes from bills. Prepares pay-or-hold information. | All payments and financial commitments. There is no evidence Quinn executes payments. |
| **Eden** | Reviews guest correspondence. Maintains product documents. Records unknown facts. Drafts improvements. | Guest-facing checklists, bond rules and readiness standards. |
| **Morgan** | Consolidates departmental reports. Separates reported from verified figures. Enters weekly snapshots. Prepares recommendations. | Changes to targets, strategy and the operating arrangement. |

## Recorded results

Small, dated and sourced. Sources refer to rows in my private WIP and Command Centre.

| Agent | Result | Date | Source |
|---|---|---|---|
| **Ava** | 4 of 4 departmental packs included in the weekly handoff, recorded around 4:55 pm. | 6 Nov 2026 | WIP, PEOPLE row 3 |
| **Alex** | 27 follow-up nudges recorded as sent in one weekly pack, 14 of them through Brevo. | 16 to 23 Oct 2026 | WIP, SALES row 3 |
| **Alex** | 2 of 2 new-lead first replies within 20 minutes in one reporting period. Other periods include a 22-minute reply and a 2-hour-37-minute reply. | Pack of 23 Oct 2026 | WIP, SALES |
| **Maya** | Audited 13 of 13 journal posts for page links and enquiry calls to action. | 23 Sep 2026 | WIP, COMPLETED row 5 |
| **Riley** | 2 of 2 day-before cleaner notices recorded as sent on time with correct times. | 28 and 30 Oct 2026 | WIP, OPERATIONS row 2 |
| **Quinn** | Found an A$1 arithmetic error. The invoice stated A$2,353.35. The correct total was A$2,354.35. | 20 Oct 2026 | WIP, FINANCE row 13 |
| **Eden** | Logged three proposed improvements from October guest correspondence. These are recommendations awaiting decisions, not implemented changes. | 2 Nov 2026 | WIP, PRODUCT & PRODUCT DELIVERY row 9 |
| **Morgan** | Six dated weekly snapshots in the Command Centre. | 9 Oct to 13 Nov 2026 | Command Centre, Weekly rows 8 to 13 |

### Invoice logging

- Quinn's log holds **31 invoice or receipt entries**: 29 in FINANCE and 2 in COMPLETED.
- Their stated face values total **A$20,755.40**. With Quinn's A$1 correction, the total is **A$20,756.40**.
- Quotes and identified superseded versions are excluded. A subscription receipt is included.
- Two entries may overlap on a A$210 labour charge. That is unresolved.
- This is logged bill value. It is not bank-verified spending or money saved.
- Whether every entry was first received between 13 September and 16 November is **UNSURE**.

## What went wrong

| Agent | Problem | Response | Status |
|---|---|---|---|
| **Alex** | A reply about dates auto-sent on 19 October after a two-hour review window passed without my answer. | Recorded in the sales records. | Whether that timeout rule is still active is **UNSURE**. |
| **Alex** | Brevo email authentication was incomplete. That raised delivery and junk-folder concerns. | Brevo sends paused by 20 October. Gmail used instead. | Authentication still unresolved in later records. (SALES rows 37, 40) |
| **Ava** | Targets I had already approved were still listed as awaiting a decision. | Status corrected 18 September. Ava assigned to link dependent work. | Completion of every dependent link **UNSURE**. (COMPLETED row 9) |
| **Maya** | Redirects meant to return HTTP 301 still returned HTTP 200. | The approved 13 October Lovable work fixed journal metadata. The redirects need Cloudflare rules. | Still unresolved on 13 November. (MARKETING row 5) |
| **Riley** | Cleaner notices asked for photos and a "done" reply. | I removed those requirements on 6 October. Notices inspected from 7, 21 and 30 October omit it. | Fixed. The cleaner's notices were later cancelled after 5 November. |
| **Quinn** | Revised invoice versions risked being counted twice. | Older versions of two invoices marked superseded, current versions kept (13 to 16 November). | Not all duplicate-payment risk is resolved. A possible A$210 double charge was flagged after I'd recorded the bills as paid. Payment reconciliation is unresolved. (FINANCE rows 34 to 36) |
| **Eden** | An "updated" venue-guide link still served the old June PDF. | Caught in a 13 September fact-check. A new v4 link was verified and set for future sends. | Fixed. (COMPLETED rows 15, 17) |
| **Morgan** | Command Centre write access was blocked in September. | A Mac-export workaround was kept from 25 September. Later weekly entries are present. | How and when direct access was restored is **UNSURE**. (COMPLETED row 28) |

## Numbers I'm not claiming yet

These figures appeared in earlier summaries. The records don't yet support them.

- **64 wedding enquiries, 13 September to 16 November 2026: UNSURE.** Maya's form counts and Alex's lead counts use different definitions and cutoffs. No deduplicated lead export has reconciled them.
- **Venue guides sent within 2 to 20 minutes: UNSURE.** One period supports it. Others include slower replies, an unverified reply and delivery failures.
- **191 automatic follow-ups, 6 October to 16 November 2026: UNSURE.** A large 7 October batch is attributed to my ChatGPT dot, not Grok Bot. A send-level reconciliation is still needed.

## What this deployment shows

- **Most blockers were access, not model ability.** Xero bank lines, Command Centre writes, Cloudflare redirects, directory listings and email authentication all stalled on permissions or setup.
- **A written approval rule is not an approval gate.** The 19 October auto-send followed a two-hour timeout rule. Where a mistake would be costly, approval needs to be enforced by the system.
- **Agents report on themselves.** Several records were written by the agents. Morgan's job includes separating reported figures from verified ones. This page applies the same test.
