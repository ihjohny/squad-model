# squad-model
### *Enterprise Mobile Super-App Operating Model & Engineering Playbook*

A battle-tested, high-quality operating model for scaling engineering teams, agile delivery, architectural governance, and release management in tier-1 mobile super-applications.

👉 **[Launch Interactive Presentation (HTML Slides)](https://ihjohny.github.io/squad-model/presentation.html)**

---

## 📚 Core Documentation & Presentation

| Resource | Description | Format |
| :--- | :--- | :--- |
| 🖥️ **[Interactive Slide Deck](https://ihjohny.github.io/squad-model/presentation.html)** | 12-slide presentation deck with an interactive 5% bug buffer calculator, STRIDE matrix, release timeline, and toggleable **Key Takeaways / Presenter Notes** (<kbd>T</kbd>). | [Open Live Slides ↗](https://ihjohny.github.io/squad-model/presentation.html) |
| 📘 **[Master Engineering Playbook](ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md)** | The complete, all-in-one guide: 30-second quickstart, plain-English glossary, "Day in the Life" walkthrough, RACI matrix, 9-stage lifecycle, STRIDE threat modeling, 4-hour task rule, 5% bug buffer, release calendar, role cheatsheets, and operational checklists. | Markdown Document |
| 📝 **[Markdown Slide Deck](SLIDES.md)** | Plain-text presentation slides with presenter cues for Google Slides, Marp, Keynote, or Obsidian. | Markdown Deck |

---

## ⚡ The Five Golden Rules at a Glance

```
  1. Box Before Build       ── Define system boundaries & FE/BE effort ratios before squad intake.
  2. Lock at ARB            ── Cross-product architecture review locks dev hours, QA hours, and release dates.
  3. Chunk to ≤ 4 Hours     ── Granular tasks surface blockers within 24 hours at morning standups.
  4. Enforce 5% Bug Buffer  ── Mathematically cap QA bug-fixing time to maintain sprint commitments.
  5. BE Freeze First        ── All backend microservices deploy to production BEFORE mobile sanity starts.
```

---

## 🚀 The 9-Stage Super-App Pipeline

```
[1. PO Grooming & Box Solution] 
         │
         ▼
[2. Squad Intake & 4h Refinement] ── Confluence Solution Doc & STRIDE Threat Model
         │
         ▼
[3. ARB Architectural Gateway]   ── Cross-product review (POL/SOL) & Estimation Lock
         │
         ▼
[4. Sprint Execution & Code Review]── Dev Time vs. Refinement Time Tracking
         │
         ▼
[5. Squad QA & Defect Buffer]     ── Max 5% bug-fixing threshold on Dev Env (VPN)
         │
         ▼
[6. UAT & Staging Verification]   ── Zero defect leakage KPI & Live Issue Pool sorting
         │
         ▼
[7. TCAB & Backend Freeze]        ── Production deployment before sanity start date
         │
         ▼
[8. Branch Merge & Sanity Cycle]  ── Squad branch consolidation & dual-gate sanity
         │
         ▼
[9. Staged Store Rollout]         ── 5% -> 20% -> 50% -> 100% with Crashlytics watch (≥ 99.8%)
```
