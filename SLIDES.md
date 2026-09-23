---
marp: true
theme: default
paginate: true
---

# Scaling Mobile Super-App Engineering Teams
## *A Battle-Tested Operating Model for High-Velocity Mobile Organizations*

> This markdown deck mirrors `presentation.html` slide for slide — the `> 💡` blocks are presenter notes.

---

## Act 1 · The Problem

### Standard Agile Breaks at Super-App Scale

- **30% of the sprint** eaten by bug spills, because edge cases were never reviewed upfront.
- **20 hours** logged as "coding" but spent in clarification meetings — sprint metrics lie.
- **Phantom bugs** from moving targets: backend deploys land while mobile QA is mid-test.
- **Silent cross-product breakage:** Squad A changes a checkout payload; Squad B's subscription purchase crashes.

> 💡 **The point:** none of these are talent problems — they are *coordination* problems. Coordination is exactly what the model automates.

---

## Act 2 · The Model at a Glance

### Approved. Scheduled. Protected.

How every feature travels from idea to store — three verbs, three owners:

- **✅ Approved — by the DAF:** the solution doc is reviewed by the cross-product forum, the task solution & approach are approved before coding, and dev & QA estimates are verified against the task breakdown.
- **📅 Scheduled — by the SM:** dev-completion and UAT dates are locked by the SM — not by the DAF — anchored to business needs and the planned release version/month, on one fixed 28-day release rhythm.
- **🛡️ Protected — by guardrails:** tasks chunked to ≤ 4 hours, bug fixing capped at 10% of dev hours, and the backend frozen before sanity starts.

> 💡 **Say this:** "Three verbs run this model — the DAF approves it, the SM schedules it, the guardrails protect it."

---

## Act 2 · Five Non-Negotiables

### The Five Golden Rules

1. **Box Before Build** *(SA draws it)* — never refine a ticket without an architect's one-page Box Solution.
2. **Approve at DAF** *(DAF decides)* — the forum approves the task solution and verifies dev & QA estimates.
3. **Chunk to ≤ 4 Hours** *(engineers own it)* — small, verifiable subtasks surface blockers within 24 hours.
4. **Enforce 10% Buffer** *(dev + QA own it)* — cap bug-fixing time to expose design debt early.
5. **BE Freeze First** *(release team owns it)* — backend deploys to production before mobile sanity ever starts.

*Approval ≠ scheduling: the DAF verifies the plan; the SM commits the dates from business needs and the planned release version/month.*

> 💡 **Why it works:** five memorable rules beat fifty policies. Every engineer knows exactly what the organization will and won't tolerate.

---

## Act 2 · Who Runs This

### Autonomous Squads, Matrix Governance

- **Layer 1 — Business & UAT** *(the "why")*: Product Owners own vision & PRDs; UAT owns business acceptance and Go/No-Go.
- **Layer 2 — Leadership & the DAF** *(the "what fits")*: Solution Architect draws Box Solutions; Squad Main Leads (1 lead, 1+ squads); Release Lead owns store operations; the **DAF** is the joint forum of Core, Payments (POL), Subscriptions (SOL) & Platform architects.
- **Layer 3 — The Squad Pool** *(the "how")*: each squad = Android, iOS, Backend, QA, SM, Dev Lead. Fluid staffing: inter-squad loans, revamp taskforces, Growth squads keep shipping.
- **7 owners on every ticket**: PO → intent · SA → blueprint · Dev Lead → code & doc · QA → test plan · SM → dates & blockers · UAT → acceptance · Reviewers → architecture.
- **Communication rule:** all decisions via `@mentions` in the ticket — never in private chats.

> 💡 **The point:** you are never alone on a feature. Before coding starts, the ticket already names the architect, the QA, and the UAT tester who are on the hook with you.

---

## Act 2 · The Workflow

### From PRD to 100% Rollout in 9 Stages

**Phase 1 · Architect** — 01 PO Grooming (PRD in, Box Solution out) → 02 Squad Refinement (Solution Doc + STRIDE + ≤ 4h tasks) → **03 DAF Review ✅** (forum approves the approach & verifies estimates)

**Phase 2 · Build** — 04 SM Scheduling & Sprint (SM locks dates from the release plan; daily 4h subtasks, honest logging, 2 approvals) → 05 Squad QA (bug fixing held inside the 10% buffer) → **06 UAT Staging 🎯** (regressions fixed, legacy bugs routed to the pool)

**Phase 3 · Ship** — **07 TCAB & Freeze ❄️** (backend live before sanity starts) → 08 Dual-Gate Sanity (QA pool, then UAT pool Go) → 09 Staged Rollout (5 → 20 → 50 → 100%, watched on Crashlytics)

> 💡 **Say this:** walk the three columns left to right. Each ends with a hard stop: *solution approved → dates committed → backend frozen*. Nothing advances until the previous phase is sealed.

---

## Act 3 · Inside the Process

### The DAF: Where Solutions Get Approved

- **Step 1 — Submit:** Solution Doc with sequence flows, failure fallbacks, STRIDE analysis, and the ≤ 4h task list — circulated ≥ 24 h ahead.
- **Step 2 — Defend:** the forum hunts corner cases: *gateway dies mid-payment? partial refund on retry? retry storm on 2G?*
- **Step 3 — Approve ✓:** the forum signs off — solution approach approved, task breakdown validated, dev & QA hours verified realistic.
- **Who's in the room:** Core Product Leads · Main Product Leads · POL (Payments) · SOL (Subscriptions) · Platform Architects.

**The split that keeps it honest:**

- **The DAF decides 🧠** — solution approach · task breakdown · estimate validity (dev & QA hours).
- **The SM locks 📅** — dev-completion date · UAT handover date · release version/month — from business needs & the planned release.

> 💡 **Say this:** "DAF approval is your shield." Once the solution is approved and the SM has scheduled the sprint, product cannot quietly add scope — any change means re-estimation and re-approval.

---

## Act 3 · Design Before Code

### One Blueprint & One Contract per Feature

- **📐 The Architect's Box Solution** (1 page, drawn at grooming):
  - Touched microservices: Payment (POL) · Subscription (SOL) · Core Profile
  - Baseline effort split, e.g. 40% Frontend / 60% Backend
  - Downstream systems: external gateways & telco billing
- **📜 The Squad's Solution Doc** (Confluence, the DAF exhibit):
  - Sequence diagrams for happy paths *and* timeout/retry failures
  - Network failure matrix: offline cache, flaky 3G, backoff with jitter
  - STRIDE threat model · blockers + ≤ 4h task list

**No Box → No Sprint. No Doc → No DAF.**

> 💡 **Engineering principle:** an hour of diagramming is worth a week of debugging. The blueprint kills architecture drift; the contract kills "I assumed the API worked differently".

---

## Act 3 · Execution Rhythm

### No Task Bigger Than 4 Hours

- A 16-hour feature decomposes into: *DTO & serialization tests [4h] · repository & cache fallback [3.5h] · UI + state binding [4h] · error dialogs & analytics [3h]*.
- **Smoke-detector effect:** a developer can be stuck for hours, never for days — blockers surface within 24 h at standup.
- **Honest hours fuel the dashboard:** Dev Time (target ≥ 90% of locked hours delivered) vs. Refinement Time (≤ 20% overhead), rolled up per engineer and per squad.

> 💡 **Say this:** "4-hour tasks protect *you*. Small PRs get reviewed in 30 minutes instead of rotting in a queue for days — and nobody discovers at sprint end that you were blocked since Tuesday."

---

## Act 3 · Quality Discipline

### Squad QA & the 10% Bug Buffer Rule

```
Max Allowed Bug-Fix Time  ≤  10% × Locked Dev Hours
```

- Example: a 40-hour locked ticket carries a **4.0-hour** allowance. (Interactive calculator lives on this slide in `presentation.html`.)
- **Green path (within the buffer):** typos, styling, edge-case null checks — fixed quietly, the sprint never feels it.
- **Quality alarm (buffer breached):** fixing stops; retro with the Squad Lead — were edge cases tested locally? was the API spec ambiguous? is there design debt to raise?
- Shift-left economics: a defect caught on the Dev env costs **10× less** than in UAT or production.

> 💡 **Say this:** "If it takes 10 hours to debug, it wasn't a bug — it was an unfinished feature. The 10% alarm makes sure architects own that early, not the developer alone at 2 AM."

---

## Act 3 · Fair Triage

### Every UAT Bug Gets a Verdict

One question decides who owns the fix: **does it reproduce on live production?**

- **NO → Type A · Story Regression:** introduced by this squad's recent PR; fixed before UAT sign-off; counts against the QA KPI (leakage < 2%).
- **YES → Type B · Pre-Existing Live Defect:** SA validates → detached from the feature → Live Issue Pool → fixed via the squad's monthly quota.

Why the split matters: delivery dates are protected from legacy debt, the QA KPI only measures what QA could have caught, and old potholes still get fixed — on quota.

> 💡 **Engineering principle:** never fear UAT finding an old bug. If it reproduces on production, it was never your sprint's regression — it goes to the pool and your feature still ships on time.

---

## Act 3 · Ship It

### The Backend Freezes First

The 28-day calendar, same every month:

- **Days 1–18** sprint execution + squad QA (≥ 90% dev hours)
- **Day 19** staging handover · **Day 20** UAT fixes & sign-off
- **Days 21–22** ❄️ TCAB → backend live in production → **frozen**
- **Days 23–27** dual-gate sanity (QA pool, then UAT Go) · **Day 28** staged rollout

Staged rollout, watched live: **5% → 20% → 50% → 100%** over four days, guard ≥ 99.8% crash-free sessions; spike → hotfix → re-verify → re-upload.

> 💡 **Cardinal rule:** mobile sanity *never* runs against a changing backend. BE deploys to production first; mobile sanity runs second. Backward-plan from Day 19 — if a feature can't make staging by then, it belongs in next month's release.

---

## Act 4 · What Good Looks Like

### The Scoreboard

| Target | Metric | Owner |
| :--- | :--- | :--- |
| 100% | On-time UAT handover | Squad |
| < 2% | UAT bug leakage | Squad QA |
| ≥ 90% | Locked dev hours delivered | Developers |
| ≤ 10% | Bug-fix vs dev-time ratio | Developers |
| ≤ 20% | Refinement overhead | Lead & SM |
| 100% | Live-issue quota fulfilled | Squad + SA |
| 100% | Store submission on calendar date | Release team |
| ≥ 99.8% | Crash-free sessions | Whole team |

> 💡 **Say this:** every KPI maps to a mechanism you've already seen. Nothing is measured that the model doesn't actively protect.

---

## Act 4 · Make It Yours

### Adopt It in Three Waves

- **Wave 1 (Weeks 1–2) — Time Hygiene:** ≤ 4h subtasks, Dev vs. Refinement logging, `[BLOCKER]` tag with a 4h SLA.
- **Wave 2 (Sprints 1–2) — Quality Discipline:** 10% bug buffer + alarm, defect bifurcation, Live Issue Pool quotas.
- **Wave 3 (The Quarter) — Full Governance:** Box Solutions + DAF review, TCAB backend freeze, the 28-day calendar.

Recap: **Box Before Build · Approve at DAF · Chunk to ≤ 4h · Enforce 10% Buffer · BE Freeze First.**

> 📘 **Go deeper:** the Master Engineering Playbook (`ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md`) has the full lifecycle, the 7-SPOC RACI contract, STRIDE matrix, and operational checklists — everything to run this starting Monday.

---

## Presenting This Deck

- **Google Slides / Keynote:** paste each slide's bullet block onto a matching slide; the `> 💡` blocks are presenter notes.
- **Marp:** render directly — `marp SLIDES.md --pdf` (front matter configures pagination).
- **Obsidian:** the `---` separators split slides in most slide plugins; the 💡 blocks double as callouts.
- The acts are the story: **Act 1** why the model exists → **Act 2** the model at a glance → **Act 3** the process up close → **Act 4** the payoff and adoption.
