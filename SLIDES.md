---
marp: true
theme: default
paginate: true
---

# Scaling Mobile Super-App Engineering Teams
## *How our mobile teams ship*

> The same slides as `presentation.html`, in plain markdown. The `> 💡` blocks are presenter notes.

---

## The problem

### Why normal agile breaks at this scale

- **30% of the month** goes to bug fixing, because edge cases never got reviewed.
- **20 hours** of meetings logged as coding, so the metrics stop meaning anything.
- **Tests run twice:** a backend deploys mid-run, the results are void, QA starts over.
- **Silent breakage:** Squad A changes a checkout payload. Squad B's subscription flow crashes in staging, two days before submission.

> 💡 **Note:** none of this is a talent problem. It's what happens when six teams can't see what the other five are doing.

---

## The big picture

### How it all fits together

Every feature goes through the same three steps:

- **The DAF approves** (before code): reviews the solution doc, checks the approach and the edge cases, confirms the dev and QA estimates hold up.
- **The SM schedules** (from the release plan): sets the dev completion date and the UAT handover date, fitted to the release version and month.
- **The rules protect** (while work flows): tasks stay under 4 hours, bug fixing stays under 10% of dev hours, the backend freezes before sanity testing.

> 💡 **Note:** approval and scheduling are deliberately separate. The people reviewing the solution are not the people committing to dates.

---

## Five rules

### The five golden rules

1. **Box Before Build** *(the SA draws it)* — no squad starts work without an architect's one-page sketch of the system.
2. **Approve at DAF** *(DAF decides)* — the forum signs off on the solution and the estimates before coding starts.
3. **Chunk to ≤ 4 Hours** *(engineers own it)* — if a task is bigger than four hours, split it until it isn't.
4. **Enforce 10% Buffer** *(dev + QA own it)* — bug fixing gets at most 10% of the dev estimate.
5. **BE Freeze First** *(release team owns it)* — backend goes to production before mobile sanity testing starts.

> 💡 **Note:** five lines any engineer can recite. That's the point. If a rule needs a paragraph to explain, it doesn't get followed.

---

## Teams

### How the teams are set up

- **Business & UAT** (what gets built): product owners write the PRDs. UAT accepts features on staging and gives the final go/no-go.
- **Tech leads & the DAF** (how it fits together): the solution architect sketches each feature. Squad main leads run delivery, one lead across one or more squads. The release lead owns store operations. The DAF is a joint forum of Core, Payments (POL), Subscriptions (SOL) and Platform architects.
- **The squads** (who builds it): each squad has Android, iOS, backend, QA, a dev lead and a scrum master. Engineers loan between squads when priorities spike.
- **7 owners on every ticket**: PO (the why), SA (the sketch), dev lead (code & doc), QA (test plan), SM (dates & blockers), UAT (acceptance), reviewers (architecture).
- All decisions go in ticket comments with @mentions. Nothing important lives in DMs.

> 💡 **Note:** you're never the only person on a feature. The ticket already says who reviews it, who tests it, and who signs it off.

---

## The pipeline

### Nine stages, three phases

**Phase 1 · Plan** — 01 PO Grooming (PRD in, one-page sketch out) → 02 Squad Refinement (solution doc, security checklist, 4h tasks) → **03 DAF Review ✅** (forum approves, estimates confirmed)

**Phase 2 · Build** — 04 Scheduling & Kanban Flow (dates set from the release plan, pull one 4h task at a time, honest time logs) → 05 Squad QA (testing on dev, bug fixing within 10%) → **06 UAT Staging 🎯** (regressions fixed, old bugs to the pool)

**Phase 3 · Ship** — **07 TCAB & Freeze ❄️** (backend in production before sanity starts) → 08 Dual-Gate Sanity (QA sanity, then UAT) → 09 Staged Rollout (5, 20, 50, then 100%, watching Crashlytics)

> 💡 **Note:** if a stage can't be finished, work stops there. That's much cheaper than finding out in production.

---

## The DAF

### What happens in a DAF review

- **Before, the write-up:** the squad shares the solution doc — sequence flows, failure handling, the security checklist, the 4h task list. At least a day before the slot.
- **In the room, the questions:** the panel asks about the cases nobody planned for. Gateway dies mid-payment? Partial refund on retry? Retry storm on a bad connection?
- **After, the sign-off:** approach approved, task list checked, dev and QA hours confirmed. If it needs work, it comes back with notes.
- **Who's in the room:** Core Product Leads, Main Product Leads, POL, SOL, Platform Architects.

The split that keeps it honest:

- **The DAF decides:** the approach, the task breakdown, whether the estimates hold up.
- **The SM locks:** dev completion date, UAT handover date, release version and month. From business needs and the release plan, not from the review.

> 💡 **Note:** once the DAF has approved and the SM has scheduled, the scope is fixed. New requests go through estimation again. They don't come in through the side door.

---

## Docs before code

### Two documents before any code

- **📐 The architect's Box Solution** (one page, at grooming):
  - Touched microservices: Payment (POL), Subscription (SOL), Core Profile
  - Rough effort split, e.g. 40% Frontend / 60% Backend
  - Downstream systems: external gateways, telco billing
- **📜 The squad's solution doc** (Confluence, for the DAF review):
  - Sequence diagrams for the happy path and the failure paths
  - What happens offline: flaky networks, timeouts, retry and caching rules
  - The STRIDE security checklist for anything touching money or identity
  - Blockers and the 4h task list

**No box, no build. No doc, no DAF.**

> 💡 **Note:** an hour on these documents routinely saves a week of debugging. "I assumed the API worked differently" is what this is designed to prevent.

---

## Daily work

### No task bigger than four hours

- A 16-hour feature splits into: DTO models and tests (4h), repository and cache fallback (3.5h), UI and state binding (4h), error dialogs and analytics (3h).
- A developer can be blocked for a few hours, but never for days. Standup catches it within 24.
- Honest time logs feed the dashboard: Dev Time (target: 90% of the estimate delivered) vs. Refinement Time (capped at 20% of squad time).

> 💡 **Note:** small PRs get reviewed in half an hour. Three-day PRs sit in the queue for days. That's most of the argument for the 4-hour rule right there.

---

## Quality

### The 10% bug buffer, in practice

```
Max bug-fixing time  ≤  10% × locked dev hours
```

- Example: a 40-hour estimate carries a 4.0-hour allowance. (Interactive calculator on this slide in `presentation.html`.)
- **Within the buffer:** typos, styling, missed null checks. Fixed quietly, and the team never feels it.
- **Buffer blown:** fixing stops. Dev and lead sit down — were the edge cases tested locally? Was the spec ambiguous? Is there design debt to file?
- A bug caught on the dev environment costs roughly a tenth of the same bug found after UAT.

> 💡 **Note:** if a fix takes ten hours, it was never a bug. The estimate or the design was wrong, and it's better to learn that in week one.

---

## When UAT finds a bug

### Two kinds of bugs

One question decides who fixes it and what it counts against: does it also happen on the live app?

- **No → a regression from the new work:** introduced by this squad's recent PR, fixed before UAT sign-off, counts against the QA leakage KPI (under 2%).
- **Yes → a pre-existing live bug:** the SA confirms it exists in production, it's detached from the feature and sent to the Live Issue Pool, and it's fixed through the squad's monthly quota.

The split keeps the release date safe from old debt, measures QA only on what it could have caught, and still gets the old bugs fixed on a schedule.

> 💡 **Note:** if it happens in production, it was never your regression. Hand it over and keep your date.

---

## Releases

### The backend freezes first

The same 28 days, every month:

- **Days 1–18** build flow and squad QA (90% of dev hours done)
- **Day 19** staging handover · **Day 20** fixes and UAT sign-off
- **Days 21–22** ❄️ TCAB, backend live in production, frozen
- **Days 23–27** dual-gate sanity (QA, then UAT) · **Day 28** rollout starts

Rollout: **5, 20, 50, then 100%** of users over four days, crash-free sessions held at 99.8% or better. Rollback plan stays armed: spike → hotfix → re-verify → re-upload.

> 💡 **Cardinal rule:** mobile sanity never runs against a changing backend. Backend deploys first, sanity runs second. And if a feature can't reach staging by day 19, it waits for next month — heroics are how three working features break at once.

---

## The numbers

### What we measure

| Target | Metric | Owner |
| :--- | :--- | :--- |
| 100% | UAT handover on the committed date | Squad |
| < 2% | bugs leaked from QA to UAT | Squad QA |
| ≥ 90% | of estimated dev hours delivered | Developers |
| ≤ 10% | bug-fix hours against dev estimate | Developers |
| ≤ 20% | of squad time spent in refinement | Lead & SM |
| 100% | of the monthly live-issue quota | Squad + SA |
| 100% | store submission on the planned date | Release team |
| ≥ 99.8% | crash-free sessions in rollout | Whole team |

> 💡 **Note:** each of these maps to a rule you've already seen. We don't measure anything the process doesn't actively protect.

---

## Getting started

### Rolling it out? Do it in three passes.

- **Pass 1 (weeks 1–2), time hygiene:** 4h tasks everywhere, dev and refinement hours logged separately, `[BLOCKER]` tag cleared within 4h.
- **Pass 2 (cycles 1–2), quality discipline:** the 10% buffer and its alarm, sorting UAT bugs by type, the Live Issue Pool with monthly quotas.
- **Pass 3 (the quarter), the full process:** box solutions and DAF reviews, the TCAB backend freeze, the 28-day release calendar.

Recap: **Box Before Build · Approve at DAF · Chunk to ≤ 4h · Enforce 10% Buffer · BE Freeze First.**

> 📘 **Full details:** the Master Engineering Playbook (`ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md`) has the complete lifecycle, the ticket template, the security checklist and the release checklists.

---

## Presenting this deck

- **Google Slides / Keynote:** paste each slide's bullets onto a matching slide; the `> 💡` blocks are presenter notes.
- **Marp:** render directly with `marp SLIDES.md --pdf` (the front matter sets pagination).
- **Obsidian:** the `---` separators split slides in most slide plugins; the 💡 blocks double as callouts.
- Suggested flow: the problem first, then the big picture, then the pipeline and the DAF in detail, and finish on the numbers and the rollout plan.
