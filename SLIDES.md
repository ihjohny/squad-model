---
marp: true
theme: default
paginate: true
---

# Scaling Mobile Super-App Engineering Teams
## *A Battle-Tested Operating Model for High-Velocity Mobile Organizations*

---

## Slide 1: Title & Overview
### Scaling Mobile Super-App Engineering Teams
- **Core Focus**: Deliver fast with autonomous squads while keeping multi-system architecture stable, secure, and predictable.
- **Audience**: Engineering Leads, Mobile Developers, QA Engineers, Solution Architects, and Product Owners.
- **Key Tenets**: ARB Architecture Gate, 4-Hour Task Chunking, 10% Bug Buffer, and Pre-Sanity Backend Freeze.

> 💡 **Engineering Principle:** These are not bureaucratic hurdles. They are practical *guardrails* that protect sprint commitments, prevent scope creep, and stop weekend emergency fixes.

---

## Slide 2: The Core Problem
### Why Standard Agile Fails at Super-App Scale
- **Cross-Product Breakages**: Squad A changes a checkout payload; Squad B's subscription purchase crashes in staging.
- **Moving Target QA**: Microservices deploy while mobile QA is testing, producing phantom bugs and wasting QA cycles.
- **Invisible Work**: Developers spend 20 hours in clarification meetings and log it as "coding time", misleading sprint metrics.
- **Endless Bug Spills**: Minor defects eat 30% of sprint capacity because edge cases were never reviewed upfront.

> 💡 **Presenter Cue:** Highlight that governance protects developers: it stops other squads from breaking your feature right before release.

---

## Slide 3: Team Topology & the RACI Model
### Autonomous Squads with Matrix Governance
- **Lead Team**: Solution Architect (Box Solutions), Squad Main Lead (guiding 1+ squads), and Release Lead.
- **ARB Forum**: Cross-product council of Leads & Architects from Core Products, Main Product Leads, POL (Payments), and SOL (Subscriptions).
- **Dev Squad Pool**:
  - Each squad has Android, iOS, Backend, Squad QA, Internal Dev Lead, and Squad Main Lead.
  - **Single Feature Ownership**: Each senior engineer takes personal ownership of one primary feature.
  - **Fluid Staffing**: Squads temporarily loan engineers to each other for urgent priorities.
  - **Revamp Taskforces vs. Growth Squads**: Combined specialist squads tackle major app redesigns; Growth squads ship daily business features.
- **Dual Scrum Masters**: Squad SM (daily standups, 4h task hygiene, time logs) + Release SM (monthly release scope & pipeline readiness).
- **The 7 Ticket SPOCs**: PO, Integration SPOC (SA), Assignee (Dev Lead), Squad QA SPOC, SM, UAT SPOC, Code Reviewers (FE, BE).
- **Communication Rule**: Keep all discussions and decisions in Jira comments using `@mentions`.

> 💡 **Engineering Principle:** You are never left alone on a feature. Every ticket clearly lists the Solution Architect, Squad QA, and UAT Tester responsible with you.

---

## Slide 4: The 9-Stage Super-App Delivery Pipeline
### From PRD Inception to Production Store Rollout

```
[Phase 1: Architecture & Planning] ──► [Phase 2: Execution & Quality] ──► [Phase 3: Production & Rollout]
Steps 01 → 02 → 03 (ARB Lock)          Steps 04 → 05 → 06 (10% Cap)         Steps 07 → 08 → 09 (Freeze & Stores)
```

#### Phase 1: Architecture & Scoping
1. **PO Grooming**: Standard PRD + Solution Architect "Box Solution" with FE/BE effort split.
2. **Squad Refinement**: Confluence Solution Doc, STRIDE threat model, and tasks sized ≤ 4 hours.
3. **ARB Gateway**: Review with cross-product leads (Core Products, Main Leads, POL/SOL); permanently lock Dev/QA hours and target release month.

#### Phase 2: Execution & Quality
4. **Sprint Execution**: Daily 4-hour subtasks, daily time logs, peer code review (minimum 2 senior approvals).
5. **Squad QA**: Test on Dev environment (VPN); bug fixing time mathematically capped at **10% of locked dev estimate**.
6. **UAT Staging**: Deploy to staging before UAT deadline; fix feature regressions and route legacy bugs to Live Issue Pool.

#### Phase 3: Production & Release
7. **TCAB & BE Freeze**: All microservices deploy to production under TCAB *before* mobile sanity testing starts.
8. **Sanity Candidate**: Rotating Release Team merges squad branches; run dual-gate sanity (Squad QA then UAT).
9. **Staged Rollout**: Gradual store release (5% → 20% → 50% → 100%) with Crashlytics monitoring (≥ 99.8% crash-free).

> 💡 **Presenter Cue:** Walk through the 3 phases sequentially. Emphasize that each phase ends with an explicit gate: Scope Lock, Quality Cap, and Backend Freeze.

---

## Slide 5: The "Box Solution" & Confluence Standards
### Architecting Before Coding
- **Part 1: The Architect's Box Solution**:
  - High-level system diagram attached to the Jira ticket during PO grooming.
  - Lists all touched microservices (Core Telco, POL, SOL, Billing).
  - Sets the baseline effort split (for example, 40% Frontend / 60% Backend).
- **Part 2: The Squad's Confluence Solution Document**:
  - Clear sequence diagrams for success and failure paths.
  - Network failure matrix (offline cache, flaky connections, retry backoff).
  - STRIDE security threat analysis.
  - Subtask breakdown with every task ≤ 4 hours.

> 💡 **Engineering Principle:** You never start coding from an ambiguous 2-line ticket. You always have a Box Solution blueprint and a clear solution document first.

---

## Slide 6: STRIDE Threat Modeling for Mobile Features
### Practical Security for Telecom & Financial Journeys
- **Spoofing**: Fake headers or phone numbers → Signed mTLS tokens and SIM-binding validation.
- **Tampering**: Altering local cached balances on rooted devices → Trust only the server-side balance ledger.
- **Repudiation**: Disputing duplicate bundle purchases → Pass unique client idempotency keys to Payment Layer (POL).
- **Information Disclosure**: Leaking tokens into system logs → Obfuscate code with R8 and store secrets in Keystore / Keychain.
- **Denial of Service**: Retrying network calls on slow connections → Use exponential backoff, random jitter, and circuit breakers.
- **Elevation of Privilege**: Bypassing UI checks to call internal APIs → Enforce scoped OAuth2 permissions at the BFF gateway.

> 💡 **Presenter Cue:** STRIDE is practical edge-case planning, not dry theory. It asks simple questions: "What happens if the user taps twice?" or "What if the network drops mid-payment?"

---

## Slide 7: The ARB Gate: Locking Scope & Estimations
### Where Cross-Product Leaders Eliminate Surprises Upfront
- **The Council**: Solution Architects, Team Leads, Core Product Leads, and Main Product Leads from Core Telecom, Payments (POL), Subscriptions (SOL), and Platform Services.
- **The Defense**: Squad developer presents sequence flows, edge cases, error fallbacks, and security controls. The panel checks corner cases.
- **The Permanent Lock**: Once ARB approves, 4 commitments cannot change:
  - Dev Hours Locked
  - QA Hours Locked
  - UAT Delivery Date Locked
  - Target Release Month Tagged

> 💡 **Engineering Principle:** ARB approval is your shield. Once your hours and dates are locked, Product cannot secretly add features into your active sprint. Scope is protected.

---

## Slide 8: Time Engineering & the Central Jira Dashboard
### Eliminating Invisible Work, the 4-Hour Rule & Progress Visibility
- **The 4-Hour Rule & Subtask Hygiene**:
  - No Jira subtask may exceed 4 hours. Use standard subtask templates.
  - No multi-day black boxes. Blockers surface within 24 hours at morning standup.
- **Time Classification**:
  - **Refinement Time**: Meetings, documentation, discovery, KT, and PO clarifications.
  - **Dev Time**: Active coding, unit tests, and code review fixes. This drives velocity metrics.
- **The Central Jira Dashboard**:
  - Tracks weekly Dev Completion, UAT Delivery Alignment, and quarterly Production Delivery.
  - Monitors the 10% bug buffer, UAT bug leakage rate, and monthly Live Issue Quota completion.

> 💡 **Presenter Cue:** 4-hour tasks protect developers. Smaller pull requests get reviewed in 30 minutes instead of sitting idle for days.

---

## Slide 9: Squad QA & the 10% Defect Buffer Rule
### Mathematical Safeguards for Sprint Stability

```
Max Allowed Bug-Fix Time  ≤  10% × Locked Dev Estimate
```

- **Concrete Example**: A 40-hour locked dev ticket allows a maximum of **4.0 hours** for bug fixing.
- **Shift-Left**: Catching defects on the Dev environment costs 10x less time than discovering them in UAT or production.
- **Alarm Protocol**: If bug fixing exceeds the 10% buffer, the Squad Lead and Developer hold a short review to check code quality, API specifications, or local testing gaps.

> 💡 **Engineering Principle:** If a task takes 10 hours to debug, it was not a simple bug—it was an incomplete feature. The 10% rule ensures architects and leads address fundamental flaws early.

---

## Slide 10: UAT Staging & Defect Bifurcation
### Protecting Squad Metrics and Isolating Legacy Debt
- **Defect Type A: Story Bug / Regression**:
  - Caused by new changes in the current PR.
  - Must be fixed immediately before UAT sign-off.
  - Counts toward the **Squad QA KPI (UAT Bug Leakage Rate)**.
- **Defect Type B: Pre-Existing Live Defect**:
  - Found during UAT, but also happens on the current production app.
  - Detached from the feature ticket and moved to the **Live Issue Pool**.
  - Squads fix these through a dedicated **Monthly Live Issue Quota**.

> 💡 **Engineering Principle:** Never fear legacy bugs during UAT. Old issues go to the Live Issue Pool so your current sprint feature releases on time.

---

## Slide 11: Release Operations & the Backend Freeze
### Decoupling Microservices from Store Review Timelines
- **Days 01 – 18**: Sprint development, code reviews, and Dev environment QA testing.
- **Day 19**: UAT Staging handover over secure VPN.
- **Days 21 – 22**: **TCAB & Backend Freeze** — all backend microservices deploy to production *before* mobile sanity testing starts.
- **Days 23 – 28**: Rotating Release Team creates the release candidate branch, runs QA sanity, and completes business UAT.

> 💡 **Cardinal Rule:** Mobile sanity testing NEVER runs against changing backend code. Backend microservices freeze and deploy to production first; mobile sanity runs second.

---

## Slide 12: Five Golden Rules for High-Scale Teams
1. **Box Before Build**: Never refine a ticket without an architect's Box Solution blueprint.
2. **Lock at ARB**: Cross-product review (Core Products, Main Leads, POL/SOL) permanently locks dev hours and release dates.
3. **Chunk to ≤ 4 Hours**: Small, verifiable subtasks surface blockers within 24 hours at daily standups.
4. **Enforce 10% Buffer**: Mathematically cap bug-fixing time to diagnose code quality issues early.
5. **BE Freeze First**: Always deploy backend services to production before mobile sanity testing starts.

> 📘 **Operational Reference:** See the **Master Engineering Playbook** (`ENTERPRISE_MOBILE_SUPERAPP_WORKFLOW.md`) for complete role guides, RACI contracts, release calendar, and operational checklists.

---

## Presenting This Deck

- **Google Slides / Keynote**: Paste each slide's bullet block onto a matching slide; the `> 💡` blocks are presenter notes.
- **Marp**: Render directly — `marp SLIDES.md --pdf` (front matter at the top configures pagination).
- **Obsidian**: The `---` separators split slides in most slide plugins; the 💡 blocks double as callouts.
