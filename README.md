# AI Build Playbook

How I direct an AI coding agent to build and ship production software.

I'm an operator, not a career software engineer. I scope the work, write the rules the agent follows, review what it produces and decide what ships. The agent writes most of the code. This page shows how that works on a real build, with the numbers taken from the git history.

Running agents in a live business is documented separately: [Adeline Estate, seven agents on Grok Bot](adeline-estate-agents.md).

The app's repo is private because it holds client data. Everything below was checked against its full history, and I'm happy to walk through the repo live in an interview.

---

## 1. The build

A founder-diagnosis web app. A service-business founder answers short diagnostic reads across six areas of the business. The app names the one constraint holding the business back, explains it in plain language using the founder's own business profile, and turns it into a dated first move and a 90-day sprint. Progress is measured by how much less the business depends on the founder.

| | |
|---|---|
| Stack | Next.js 14, React 18, TypeScript, Supabase (Postgres, auth, 23 migrations), Vercel, Anthropic API (server-side) |
| First commit | 2 June 2026 |
| First live deploy | The next day (auto-deploy to Vercel on push to `main`) |
| Full app in production | 27 June 2026, 25 days after the first commit |
| Commits on `main` | 154 |
| Co-authored with Claude Code | 152 of 154 (the other two are merges) |
| Human author on every commit | Me |

## 2. How I run the agent

**Plan before code.** The rule in the instruction file reads: *"Plan before you code. Validate before you deploy. Show each step running."*

**Branches by feature.** Features are built on `feature/*` branches, merged into an integration branch, then into `main`. Merging to `main` deploys to production.

**Adversarial review before merge.** For larger changes the work goes through an adversarial review pass, and the confirmed findings are fixed before it ships. Four of those rounds are recorded in the commit history, with 17, 17, 20 and 8 confirmed findings fixed.

**Human red lines.** Where the agent's founder-facing wording is wrong for the audience, I correct it, and those corrections are committed as their own changes.

**Eyes on the screen.** Passing checks aren't enough. The rule: *"Eyes on the screen, not just green checks. A typecheck and a route probe both pass on a buried or incoherent feature… Eyeball before every push."*

## 3. The rules I gave the agent

The instruction file (`CLAUDE.md`) grew to over 800 lines across the build. Most of it is session handover notes. The core is a short block of non-negotiable rules. Some of them, quoted directly:

| Rule | Why it's there |
|---|---|
| "Connect, do not rebuild." | Agents default to rewriting. Most of the time the right move is wiring up what already exists. |
| "All AI runs server-side. The Anthropic key stays on the server, model as an env var." | Keeps keys out of the browser, and lets me change models without a code change. |
| "No engine ships founder-facing on an AI-drafted constraint menu. The diagnostic questions and constraint logic for each engine are Latham's IP. Do not invent them. Ask." | Added the day an AI-drafted question set reached the product. See failure 1 below. |
| "ONE VERDICT … two computations silently disagreeing about the one thing the product exists to name can never happen." | The product exists to give one answer. Two code paths giving different answers would make it worthless. |
| "Plan before you code. Validate before you deploy. Show each step running." | Stops the agent from charging ahead on a wrong assumption. |

Several of these rules were added straight after something went wrong. That's the pattern I'd teach any team: the instruction file is where each failure gets fixed for good.

## 4. What went wrong

Four real failures from the build, and what changed because of each one.

| Date | What happened | How it was fixed | What changed for good |
|---|---|---|---|
| 3 Jun | One diagnostic engine shipped on a question set the AI had drafted, not my tested coaching method. | Pulled from the founder-facing path the same day. | New rule: no AI-drafted diagnostic reaches founders. The agent asks instead of inventing. |
| 10 Jun | Every new founder was told the same constraint. Empty seed data was being counted as a real signal. | Areas with no real data were excluded from the verdict. | New rule: unmeasured areas never enter the constraint pool. |
| 13 Jun | A CSS reset wiped the home page spacing, but only in production. Local dev loaded styles in a different order and hid it. | Fixed the CSS. | New rule: verify production CSS by computed style in the live page, never by reading the source diff. |
| 26–27 Jun | The AI read returned 502 errors in production. The pinned Claude model had been retired and the error was being swallowed. | Switched to a current model and logged the real error. | Retired model IDs are now blocked, and AI errors are logged rather than hidden. |

## 5. What I'd do differently

Honest gaps in this build:

- **No CI.** Nothing runs automatically on each push. On a team I'd put typecheck, build and tests in CI from day one.
- **One test file.** The core sprint engine has tests. Most of the app doesn't. The adversarial reviews caught real issues, but they don't replace automated tests that run on every change.
- **No pull requests.** Merges were done locally. Working solo that was fine. With a team, every change goes through a PR so a human sees it before it merges.

These are the same guardrails I'd set up first when rolling AI coding tools out to a team. The agent can move fast because the checks around it are slow and boring.

---

Latham Dunstan, Sydney · [GitHub profile](https://github.com/lathamjdunstan-cmd) · [LinkedIn](https://www.linkedin.com/in/latham-dunstan-bb5a2a23)
