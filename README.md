<div align="center">

# squad-model

### *Enterprise Mobile Super-App Operating Model & Engineering Playbook*

How our mobile teams work: how squads are set up, how solutions get approved, and how a release ships on the same schedule every month.

[![Slides](https://img.shields.io/badge/Interactive_Slides-14_slides-4338ca)](https://ihjohny.github.io/squad-model/presentation.html)
[![Playbook](https://img.shields.io/badge/Master_Playbook-13_sections-0d9488)](./ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md)
[![Markdown Deck](https://img.shields.io/badge/SLIDES.md-Marp_ready-059669)](./SLIDES.md)

👉 **[Launch the Interactive Presentation](https://ihjohny.github.io/squad-model/presentation.html)**

**The short version:** an architect sketches the solution, the squad writes it up, the DAF reviews and approves it, and the SM sets the dates against a fixed monthly release calendar. During the sprint, two limits do most of the work: tasks stay under 4 hours, and bug fixing stays under 10% of the dev estimate.

</div>

---

## 📚 What's in here

| Resource | What it is | Format |
| :--- | :--- | :--- |
| 🖥️ **[Interactive Slide Deck](https://ihjohny.github.io/squad-model/presentation.html)** | 14 slides: the problem, how teams are set up, the 9-stage pipeline, a worked example of a DAF review, a live 10% buffer calculator, the release timeline, and the metrics we hold ourselves to. Presenter notes toggle with <kbd>T</kbd>. Any slide can be linked directly with `#N` in the URL. | [Open the slides ↗](https://ihjohny.github.io/squad-model/presentation.html) |
| 📘 **[Master Engineering Playbook](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md)** | Everything in detail: the glossary, a squad engineer's day, the 7-SPOC ticket contract, the full 9-stage lifecycle, the STRIDE security checklist, the release calendar, common failure modes, role cheatsheets, and checklists for each handoff. | Markdown |
| 📝 **[Markdown Slide Deck](SLIDES.md)** | The same slides as plain markdown with presenter notes. Works in Google Slides, Keynote, Obsidian, and Marp (`marp SLIDES.md --pdf`). | Markdown |

---

## ⚡ The five golden rules

```
  1. Box Before Build       ── An architect sketches the system before the squad starts work.
  2. Approve at DAF         ── The Design Authority Forum approves the solution and verifies estimates. The SM sets the dates.
  3. Chunk to ≤ 4 Hours     ── If a task is bigger than four hours, split it until it isn't.
  4. Enforce 10% Bug Buffer ── Bug fixing gets at most 10% of the dev estimate.
  5. BE Freeze First        ── Backend deploys to production before mobile sanity testing starts.
```

---

## 🔢 The numbers behind the process

| Number | What it means | Who owns it |
| :--- | :--- | :--- |
| **≤ 4 h** | Biggest allowed size of a Jira subtask | Every engineer |
| **2** | Senior approvals needed per pull request | Developer |
| **10%** | Bug-fixing cap, as a share of the dev estimate | Developer & Squad QA |
| **< 2%** | Defects QA is allowed to leak to UAT | Squad QA |
| **≥ 80%** | Unit test coverage on new business logic | Developer |
| **≤ 20%** | Meeting/refinement share of squad time | Squad Lead & SM |
| **100%** | UAT handover and store submission on the committed dates | Squad & Release Team |
| **≥ 99.8%** | Crash-free sessions during rollout | Whole team |
| **5→20→50→100%** | Staged store rollout over four days | Release Lead |

---

## 🚀 The 9-stage pipeline

```
[Phase 1: Plan]
  [1. PO Grooming & Box Solution]
            │
            ▼
  [2. Squad Intake & 4h Refinement]  ── Solution doc, STRIDE security checklist
            │
            ▼
  [3. DAF Review]                   ── Solution approved, estimates verified
            │                                      ✅ Then the SM locks the dates
[Phase 2: Build]
  [4. SM Scheduling & Sprint]        ── Daily 4h subtasks, dev vs refinement time logs
            │
            ▼
  [5. Squad QA]                      ── Bug fixing capped at 10% of the estimate
            │                                      ⏱️ CHECKPOINT: 10% cap enforced
            ▼
  [6. UAT & Staging]                 ── New regressions fixed, old bugs to the Live Issue Pool
            │                                      🎯 CHECKPOINT: UAT sign-off
[Phase 3: Ship]
  [7. TCAB & Backend Freeze]         ── Backend in production before sanity starts
            │                                      ❄️ CHECKPOINT: BE frozen first
            ▼
  [8. Branch Merge & Sanity]        ── Squad branches merged, QA sanity then UAT sanity
            │
            ▼
  [9. Staged Store Rollout]          ── 5% -> 20% -> 50% -> 100%, Crashlytics watched (≥ 99.8%)
```

---

## 🗂️ Repository layout

```
squad-model/
├── README.md                                  ← This file
├── ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md     ← The full playbook
├── SLIDES.md                                  ← The deck as markdown (Marp-ready)
└── presentation.html                          ← The interactive deck (GitHub Pages)
```

---

## 🧭 Using it

**Present it.** Open the [live deck](https://ihjohny.github.io/squad-model/presentation.html) or serve `presentation.html` locally. Arrow keys or <kbd>Space</kbd> to move, <kbd>T</kbd> toggles the presenter notes, <kbd>F</kbd> goes fullscreen, and `#4` at the end of the URL opens slide 4 directly.

**Read it.** Start with the [glossary](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#2-plain-english-jargon-buster-the-super-app-glossary) and the [pipeline](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#5-the-9-stage-super-app-delivery-lifecycle), then follow the playbook's table of contents for your role.

**Export it.** `SLIDES.md` renders in Marp (`marp SLIDES.md --pdf`) and Obsidian if you want to rebrand it or present offline.

**Adopt it.** A sensible order, one piece at a time:

| Step | When | What to introduce |
| :--- | :--- | :--- |
| 1 | Weeks 1–2 | 4h subtasks, separate dev/refinement time logs, `[BLOCKER]` tag |
| 2 | Sprints 1–2 | The 10% bug buffer, sorting UAT bugs by type, the Live Issue Pool |
| 3 | The quarter | Box solutions, DAF reviews, the TCAB backend freeze, the release calendar |

---

## 📖 Pointers

- New engineer onboarding: watch the [deck](https://ihjohny.github.io/squad-model/presentation.html), then read the [lifecycle](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#5-the-9-stage-super-app-delivery-lifecycle).
- Running a release: the [release calendar](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#9-the-monthly-release-calendar) and [Checklist D](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#checklist-d-backend-tcab--release).
- Reviewing a solution doc: the [STRIDE checklist](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#6-stride-threat-modeling-for-mobile-features) and the [DAF submission checklist](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#checklist-a-solution-document--daf-submission).
- Team health: the [KPI table](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#12-balanced-scorecard--engineering-kpi-framework).
