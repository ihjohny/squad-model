# squad-model
### *Enterprise Mobile Super-App Operating Model & Engineering Playbook*

A practical, high-quality operating model for scaling mobile engineering teams, cross-product governance, and monthly releases in enterprise super-apps.

👉 **[Launch Interactive Presentation (HTML Slides)](https://ihjohny.github.io/squad-model/presentation.html)**

---

## 📚 Core Documentation & Presentation

| Resource | Description | Format |
| :--- | :--- | :--- |
| 🖥️ **[Interactive Slide Deck](https://ihjohny.github.io/squad-model/presentation.html)** | 12-slide presentation with an interactive 10% bug buffer calculator, 3-phase delivery flow, STRIDE security matrix, and presenter notes (<kbd>T</kbd>). | [Open Live Slides ↗](https://ihjohny.github.io/squad-model/presentation.html) |
| 📘 **[Master Engineering Playbook](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md)** | The complete guide: 30-second quickstart, plain-English glossary, daily engineer routine, RACI matrix, 9-stage lifecycle, STRIDE threat model, 4-hour task rule, 10% bug buffer, release calendar, role cheatsheets, and operational checklists. | Markdown Document |
| 📝 **[Markdown Slide Deck](SLIDES.md)** | Clean slide text with presenter cues for Google Slides, Keynote, Marp, or Obsidian. | Markdown Deck |

---

## ⚡ The Five Golden Rules at a Glance

```
  1. Box Before Build       ── Define system boundaries & FE/BE effort ratios before squad intake.
  2. Lock at ARB            ── Cross-product architecture review (Core Products, Main Leads, POL/SOL) locks dev hours, QA hours, and release dates.
  3. Chunk to ≤ 4 Hours     ── Granular tasks surface blockers within 24 hours at morning standups.
  4. Enforce 10% Bug Buffer ── Mathematically cap QA bug-fixing time to maintain sprint commitments.
  5. BE Freeze First        ── All backend microservices deploy to production BEFORE mobile sanity starts.
```

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
  [3. ARB Architectural Gateway]    ── Core Products, Main Leads, POL/SOL & Estimation Lock

[Phase 2: Sprint Execution & Quality]
  [4. Sprint Execution & Code Review]── Daily 4h Subtasks, Dev vs. Refinement Time Tracking
            │
            ▼
  [5. Squad QA & Defect Buffer]      ── Max 10% bug-fixing threshold on Dev Env (VPN)
            │
            ▼
  [6. UAT & Staging Verification]    ── Zero defect leakage KPI & Live Issue Pool triage

[Phase 3: Production & Rollout]
  [7. TCAB & Backend Freeze]         ── Production deployment before sanity start date
            │
            ▼
  [8. Branch Merge & Sanity Cycle]   ── Squad branch consolidation & dual-gate sanity (QA + UAT)
            │
            ▼
  [9. Staged Store Rollout]          ── 5% -> 20% -> 50% -> 100% with Crashlytics watch (≥ 99.8%)
```

