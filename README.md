<div align="center">

# squad-model

### *Enterprise Mobile Super-App Operating Model & Engineering Playbook*

How our mobile teams work: how squads are set up, how solutions get approved, and how a release ships on the same schedule every month.

[![Slides](https://img.shields.io/badge/Interactive_Slides-14_slides-4338ca)](https://ihjohny.github.io/squad-model/presentation.html)
[![Playbook](https://img.shields.io/badge/Master_Playbook-13_sections-0d9488)](./ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md)
[![Markdown Deck](https://img.shields.io/badge/SLIDES.md-Marp_ready-059669)](./SLIDES.md)

👉 **[Launch the Interactive Presentation](https://ihjohny.github.io/squad-model/presentation.html)**

**The short version:** an architect sketches the solution, the squad writes it up, the DAF reviews and approves it, and the SM sets the dates against a fixed monthly release calendar. While work flows to the monthly release, two limits do most of the work: tasks stay under 4 hours, and bug fixing stays under 10% of the dev estimate.

</div>

---

## 📚 What's in here

| Resource | What it is |
| :--- | :--- |
| 🖥️ **[Interactive Slide Deck](https://ihjohny.github.io/squad-model/presentation.html)** | 14 slides: the problem, the teams, the 9-stage pipeline, a worked DAF review, a live 10% buffer calculator, the release timeline, and the metrics. Presenter notes toggle with <kbd>T</kbd>; any slide links directly via `#N`. |
| 📘 **[Master Engineering Playbook](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md)** | Everything in detail: glossary, a squad engineer's day, the 7-SPOC ticket contract, the 9-stage lifecycle, the STRIDE security checklist, the release calendar, common failure modes, role cheatsheets, and handoff checklists. |
| 📝 **[Markdown Slide Deck](SLIDES.md)** | The same slides as plain markdown with presenter notes. Works in Google Slides, Keynote, Obsidian, and Marp (`marp SLIDES.md --pdf`). |

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

## 🚀 The pipeline at a glance

```
PLAN   1 · PO Grooming & Box Solution  →  2 · Squad Refinement (4h tasks)  →  3 · DAF Review ✅  →  SM locks the dates
BUILD  4 · Kanban Flow            →  5 · Squad QA (10% bug cap)       →  6 · UAT Sign-off 🎯
SHIP   7 · TCAB & Backend Freeze ❄️    →  8 · Dual-Gate Sanity             →  9 · Staged Rollout (5 → 100%)
```

The [full playbook](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#5-the-9-stage-super-app-delivery-lifecycle) walks through all nine stages with the detail and the flow diagram.

---

## 🧭 Using this repo

**Present it.** Open the [live deck](https://ihjohny.github.io/squad-model/presentation.html) or serve `presentation.html` locally. Arrow keys or <kbd>Space</kbd> to move, <kbd>T</kbd> toggles the presenter notes, <kbd>F</kbd> goes fullscreen, and `#4` at the end of the URL opens slide 4 directly.

**Read it, by role.**

| If you are… | Start here |
| :--- | :--- |
| New to the team | The [deck](https://ihjohny.github.io/squad-model/presentation.html), then the [glossary](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#2-plain-english-jargon-buster-the-super-app-glossary) and the [lifecycle](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#5-the-9-stage-super-app-delivery-lifecycle) |
| Running a release | The [release calendar](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#9-the-monthly-release-calendar) and [Checklist D](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#checklist-d-backend-tcab--release) |
| Reviewing a solution doc | The [STRIDE checklist](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#6-stride-threat-modeling-for-mobile-features) and the [DAF submission checklist](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#checklist-a-solution-document--daf-submission) |
| Checking team health | The [KPI table](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md#12-balanced-scorecard--engineering-kpi-framework) |

**Export it.** `SLIDES.md` renders in Marp (`marp SLIDES.md --pdf`) and Obsidian if you want to rebrand it or present offline.

**Adopt it.** One piece at a time; each step pays for itself before the next starts:

| Step | When | What to introduce |
| :--- | :--- | :--- |
| 1 | Weeks 1–2 | 4h subtasks, separate dev/refinement time logs, `[BLOCKER]` tag |
| 2 | Cycles 1–2 | The 10% bug buffer, sorting UAT bugs by type, the Live Issue Pool |
| 3 | The quarter | Box solutions, DAF reviews, the TCAB backend freeze, the release calendar |
