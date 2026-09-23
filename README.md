<div align="center">

# squad-model

### *Enterprise Mobile Super-App Operating Model & Engineering Playbook*

A practical, battle-tested operating model for scaling mobile engineering teams, cross-product architecture governance, and predictable monthly releases in enterprise super-apps (telecom, fintech, payments).

[![Slides](https://img.shields.io/badge/Interactive_Slides-14_deck_·_4_acts-4338ca)](https://ihjohny.github.io/squad-model/presentation.html)
[![Playbook](https://img.shields.io/badge/Master_Playbook-13_sections-0d9488)](./ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md)
[![Markdown Deck](https://img.shields.io/badge/SLIDES.md-Marp_ready-059669)](./SLIDES.md)

👉 **[Launch the Interactive Presentation](https://ihjohny.github.io/squad-model/presentation.html)**

> **How work flows:** the architect boxes it → the squad refines it → the **DAF** approves it → the **SM** schedules it → the calendar ships it. Guardrails (≤ 4 h tasks, the 10% bug buffer, the pre-sanity backend freeze) protect the sprint in between.

</div>

---

## 📚 Core Documentation & Presentation

| Resource | Description | Format |
| :--- | :--- | :--- |
| 🖥️ **[Interactive Slide Deck](https://ihjohny.github.io/squad-model/presentation.html)** | 14 slides told in four acts — *Why → The Model → How It Runs → Payoff* — with a live 10% bug-budget calculator, a 9-stage workflow map, a 28-day release timeline, a UAT triage decision tree, and presenter takeaways (press <kbd>T</kbd>). Deep-link any slide with `#N`. | [Open Live Slides ↗](https://ihjohny.github.io/squad-model/presentation.html) |
| 📘 **[Master Engineering Playbook](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md)** | The complete guide: 30-second quickstart, plain-English glossary, daily engineer routine, 7-SPOC RACI model, 9-stage lifecycle, STRIDE threat model, 4-hour task rule, 10% bug buffer, monthly release calendar, anti-pattern guardrails, role cheatsheets, KPI scorecard, and operational checklists. | Markdown Document |
| 📝 **[Markdown Slide Deck](SLIDES.md)** | Clean slide text with presenter cues for Google Slides, Keynote, Marp, or Obsidian. Ships Marp-ready front matter: run `marp SLIDES.md --pdf` to export. | Markdown Deck |

---

## ⚡ The Five Golden Rules at a Glance

```
  1. Box Before Build       ── Define system boundaries & FE/BE effort ratios before squad intake.
  2. Approve at DAF         ── The Design Authority Forum approves the task solution & verifies estimates; the SM locks dates from business needs.
  3. Chunk to ≤ 4 Hours     ── Granular tasks surface blockers within 24 hours at morning standups.
  4. Enforce 10% Bug Buffer ── Mathematically cap QA bug-fixing time to maintain sprint commitments.
  5. BE Freeze First        ── All backend microservices deploy to production BEFORE mobile sanity starts.
```

---

## 🔢 The Numbers That Run the Model

Memorize these nine numbers — they encode the entire operating model:

| Number | Meaning | Owner |
| :--- | :--- | :--- |
| **≤ 4 h** | Maximum size of any Jira subtask (blockers surface within 24 h) | Every Engineer |
| **2** | Minimum senior approvals per pull request (Senior FE + Senior BE) | Developer |
| **10%** | Bug-fixing time cap, relative to locked dev hours | Developer & Squad QA |
| **< 2%** | UAT bug-leakage rate target (defects missed by Squad QA) | Squad QA |
| **≥ 80%** | Unit-test coverage on new business logic before QA handoff | Developer |
| **≤ 20%** | Refinement-time overhead as a share of total squad effort | Squad Lead & SM |
| **100%** | On-time UAT handover and on-time store submission | Squad & Release Team |
| **≥ 99.8%** | Crash-free user sessions during staged rollout | Entire Mobile Team |
| **5→20→50→100%** | Staged store rollout gates (Day 1 → Day 4) | Release Lead |

---

## 🚀 The 9-Stage Super-App Pipeline

```
[Phase 1: Architecture & Planning]
  [1. PO Grooming & Box Solution]
            │
            ▼
  [2. Squad Intake & 4h Refinement]  ── Confluence Solution Doc & STRIDE Threat Model
            │
            ▼
  [3. DAF Review & Approval]        ── Solution approved, estimates verified; SM locks dates
            │                                      ✅ DAF approved · SM-locked schedule
[Phase 2: Sprint Execution & Quality]
  [4. Sprint Execution & Code Review]── Daily 4h Subtasks, Dev vs. Refinement Time Tracking
            │
            ▼
  [5. Squad QA & Defect Buffer]      ── Max 10% bug-fixing threshold on Dev Env (VPN)
            │                                      ⏱️ CHECKPOINT: 10% cap enforced
            ▼
  [6. UAT & Staging Verification]    ── Zero defect leakage KPI & Live Issue Pool triage
            │                                      🎯 CHECKPOINT: UAT sign-off
[Phase 3: Production & Rollout]
  [7. TCAB & Backend Freeze]         ── Production deployment before sanity start date
            │                                      ❄️ CHECKPOINT: BE frozen first
            ▼
  [8. Branch Merge & Sanity Cycle]   ── Squad branch consolidation & dual-gate sanity (QA + UAT)
            │
            ▼
  [9. Staged Store Rollout]          ── 5% -> 20% -> 50% -> 100% with Crashlytics watch (≥ 99.8%)
```

---

## 🗂️ Repository Structure

```
squad-model/
├── README.md                                  ← You are here: overview & quick reference
├── ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md     ← Master playbook: the complete deep dive
├── SLIDES.md                                  ← Marp-ready markdown deck with presenter cues
└── presentation.html                          ← Interactive HTML deck (served via GitHub Pages)
```

---

## 🧭 How to Use This Repo

**Present it.** Open the [live slide deck](https://ihjohny.github.io/squad-model/presentation.html) (or serve `presentation.html` locally). Navigate with <kbd>←</kbd> <kbd>→</kbd> or <kbd>Space</kbd>, toggle presenter takeaways with <kbd>T</kbd>, go fullscreen with <kbd>F</kbd>, and share a specific slide by appending `#4` to the URL.

**Read it.** Start with the [30-second quickstart](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#1-executive-summary--the-30-second-quickstart) and [glossary](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#2-plain-english-jargon-buster-the-super-app-glossary) in the playbook, then follow its table of contents role by role.

**Export it.** `SLIDES.md` renders directly in Marp (`marp SLIDES.md --pdf`) and Obsidian, so you can rebrand and present offline.

**Adopt it.** Don't boil the ocean — roll the model out in three waves:

| Wave | Timeframe | What to Introduce |
| :--- | :--- | :--- |
| 1 — Time Hygiene | Weeks 1–2 | ≤ 4 h subtasks, Dev vs. Refinement time logging, `[BLOCKER]` escalation tag |
| 2 — Quality Gates | Sprints 1–2 | 10% bug buffer, UAT leakage KPI, defect bifurcation & Live Issue Pool |
| 3 — Governance | Quarter | Box Solutions, the DAF review, TCAB backend freeze & the monthly release calendar |

---

## 📖 Where to Go Next

- New engineer onboarding → play the [deck](https://ihjohny.github.io/squad-model/presentation.html) first, then the [playbook lifecycle](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#5-the-9-stage-super-app-delivery-lifecycle).
- Leading a release → the [release calendar](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#9-the-monthly-release-calendar) and [Checklist D](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#checklist-d-backend-tcab--release).
- Reviewing a solution doc → the [STRIDE matrix](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#6-stride-threat-modeling-for-mobile-features) and [DAF submission checklist](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#checklist-a-solution-document--daf-submission).
- Tracking team health → the [KPI scorecard](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#12-balanced-scorecard--engineering-kpi-framework).
