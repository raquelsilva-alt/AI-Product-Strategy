# AI Product Strategy

> Make proactivity the win Happy clients do not need to report anything and support is less than 2 min

---

## Strategy at a Glance

| Component | Module | Status | Key Artifact |
|-----------|--------|--------|-------------|
| **The Bet** | M1 | [x] | `01-the-bet/` |
| **The Moat** | M2 | [x] | `02-the-moat/` |
| **The Margin** | M3 | [x] | `03-the-margin/` |
| **The Contract** | M4 | [x] | `04-the-contract/` |
| **The Guardrails** | M5 | [x] | `05-the-guardrails/` |
| **The Pitch** | M6 | [x] | `06-the-pitch/` |

---

## The Bet (M1)

**What we're building, for whom, why now.**

- **Product:**
- **AI Value Archetype:** Claude
- **Vulnerability Scores:** _(add: Moat _/5 · Data _/5 · Platform _/5)_
- **Top Risk:** Keep the specific with priatary data and alutiantions under 1%
- **Confidence:** M
- **Prototype:** magic-assist-insight.lovable.app
- **Kill Criteria:** The identification fails 5% to solve. Predictability and number of Devices accurace below 98%

→ Details: [`01-the-bet/`](01-the-bet/)

---

## The Moat (M2)

**Why this won't get copied in 6 months.**

- **Data Flywheel Score:**
- **Weakest Loop:** **Fix for weakest loop:**
- **Top Encroachment Threat:**
- **Encroachment Defense:** __________________________________________________
- **Vendor Portability:** _(add: Ready / Partial / Locked)_

→ Details: [`02-the-moat/`](02-the-moat/)

---

## The Margin (M3)

**Will this make money or bleed it?**

- **Gross Margin (current):**
- **Gross Margin (AI-adjusted):** 60%
- **Pricing Model:** Outcome-based
- **Pricing Today → Tomorrow:** No chargeback model — IT Operations absorbs cost as a → Outcome-based internal value model
- **Total AI COGS / unit:** $1.61
- **Cascading Strategy:** Triage: GPT-3.5 Turbo — handles simple queries, clarification requests,; frontier: GPT-4 — handles complex multi-source synthesis, plain language; ratio | Tier | Model | % of Queries | Est. Cost/SR |
- **Net Margin Shift:** | Metric | Before | After | Delta |
- **Break-even at:**

→ Details: [`03-the-margin/`](03-the-margin/)

---

## The Contract (M4)

**Why users will trust a probabilistic system.**

- **Reliability Target:** 90%
- **Golden Dataset:** 5 rows, 3 adversarial
- **Confidence UX:** Tiered confidence — no mixed signals, clear routing per tier
- **HITL Architecture:**
- **Failure Mode Coverage:** _to be filled during red-team exercise_

→ Details: [`04-the-contract/`](04-the-contract/)

---

## The Guardrails (M5)

**What breaks when this scales — and what compounds.**

- **Compounding System:** | Loop | Input | Output | Compounds? | Status | |------|-------|--------|-----------|--------| | User feedback | Accuracy rating + feedback on answer | Flags low-rated answers for review, improves retrieval/prompting | Y…
- **Governance Posture:** **Autonomy boundaries:**
- **Autonomy Boundaries:** **Escalation triggers:**
- **Escalation Triggers:** **Audit cadence:**
- **Audit Cadence:** **Regulatory exposure (EU AI Act / other):**
- **Shadow AI Audit (user-side):** 4 workarounds found · All 4 retained with appropriate governance level — none killed build candidates · adjacent spend Unknown — to be assessed. No current visibility into
- **Agent Boundaries:** *Note: Full agent architecture is owned by engineering. The topology below is a recommended starting point for validation with the engineering team.*
- **Regulatory Exposure:**

→ Details: [`05-the-guardrails/`](05-the-guardrails/)

---

## The Pitch (M6)

**How you get this funded, shipped, and adopted.**

- **Horizon 1 (Now):**
- **Horizon 2 (Next):**
- **Horizon 3 (Bet):**
- **Board Narrative:** **The case:**
- **Ask:** ## M1 Baseline vs. Now
- **Key Strategic Change:**

→ Details: [`06-the-pitch/`](06-the-pitch/)



# AI Product Strategy — Product School Exercises
**Scenario:** Cisco IT Operations — AI-powered support assistant
**Author:** Raquel Silva
**Date:** May 2026

---

# Exercise 1: Golden Dataset & Reliability Contract

## Golden Dataset Spec

| # | Input | Expected Output | Edge Case? | Judge Type |
|---|-------|----------------|-----------|-----------|
| 1 | Engineer asks about device error after firmware update | Step-by-step resolution + source reference | N | LLM |
| 2 | Client asks about warranty/contract coverage for their issue | Contract terms summary + coverage status + applicable support | N | LLM |
| 3 | Engineer asks about issue spanning hardware manual + firmware note for specific model/version | Synthesized answer from both sources, attributed | Y | LLM |
| 4 | Engineer asks about non-existent or unsupported device model | System asks for clarification instead of answering | Y | Rule |
| 5 | Client describes problem in plain language with no technical terms | Semantic interpretation + mapped resolution + source | Y | LLM |

**Adversarial rows included:** 3 (rows 3, 4, 5)

**Coverage gaps identified by partner:** _to be filled during red-team exercise_

---

## Confidence UX Design

**Approach:** Tiered confidence — no mixed signals, clear routing per tier

**High confidence (>90%):** Answer returned directly with source reference, no friction

**Medium confidence (70-90%):** Answer returned with advisory — *"Please confirm this with your team or the relevant department before proceeding"*

**Low confidence (<70%):** Partial answer shown with warning — *"Here's what I found, but I'm not confident this is accurate for your specific situation — please verify with an engineer or the relevant department before acting on this"*

**User control surface:** Feedback button + accuracy rating on every response

---

## Reliability Contract

| Metric | Target | Measurement | Alert Threshold |
|--------|--------|-------------|-----------------|
| Accuracy | 90% | LLM judge eval on golden dataset | <85% |
| Hallucination rate | 0% contract/warranty — <2% technical | Automated source grounding check | Any hallucination on contract queries — >1% on technical |
| Latency (p95) | <3 seconds | Response time monitoring | >3s on 5% of queries |
| Drift velocity | Monitored monthly | Golden dataset re-evaluation | >5% accuracy drop month-over-month |

---

## HITL Architecture

AI is advisory only — no write access to any connected system. 40% of SRs touch a human:
- 30% AI-assisted (medium confidence — human confirms or adjusts)
- 10% fully escalated (low confidence — engineer or relevant department handles)

Bi-weekly feedback review as standard. Critical issues trigger immediate out-of-cadence review. Public-facing escalation handling is owned by the client — Cisco receives feedback from clients for improvement purposes only.

---

## Red-Team Findings

*To be completed during partner red-team exercise.*

---
---

# Exercise 2: Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| User feedback | Accuracy rating + feedback on answer | Flags low-rated answers for review, improves retrieval/prompting | Y | Active |
| Engineer uploads resolution | Engineer adds missed resolution doc to RAG | Knowledge base expanded, future similar queries answered correctly | Y | Active |
| Drift monitoring | Monthly golden dataset re-evaluation detects accuracy drop | Triggers knowledge base refresh or model/prompt update | Y | Broken |

**Broken loop identified by partner:** Drift monitoring exists but remediation is too slow and manual — improvements to the refresh process are missing

**Fix plan:** Define a clear owner for drift remediation, establish a maximum time-to-fix SLA after drift is detected, and automate the knowledge base refresh trigger where possible

---

## Context Connectivity

Knowledge flows into the system from multiple sources: engineering documentation,
contracts, vendor manuals, field engineer resolution uploads, and internally produced
documentation (new and existing).

**Where it flows well:**
- SharePoint-connected sources auto-scan and stay current
- Field engineers can upload new resolutions directly to the RAG, expanding coverage over time

**Where it silos:**
- Static file uploads (PDFs, docs uploaded directly instead of via URL) do not
auto-update when the source document changes — answers may be based on outdated
firmware or contract versions without the user knowing
- Cross-team RAG access is currently blocked — engineering, contracts, and field
teams cannot query each other's knowledge bases due to confidentiality concerns.
Boundaries and permission layers need to be built before cross-team connectivity
can be enabled safely

**Partial mitigation in development:**
- 2x weekly automated scan to detect differences between uploaded static docs and
their source — not yet live

**Key risk:** A user could receive a confident, well-sourced answer based on a
document that has since been updated, with no indication that the source may be stale

---

## Governance Policy

**Scope:** Technical support queries only — device troubleshooting, firmware guidance,
warranty and SLA reference. Not in scope: contract management, commercial decisions,
or customer service escalations (owned by the client's public-facing layer)

**Autonomy boundaries:** AI is advisory only — it provides information, it cannot
perform any system updates, close tickets, or take actions on any connected system.
Humans (engineers or clients) retain all decision-making authority

**Escalation triggers:** Low confidence responses (<70%) surface a warning and
recommend human verification. Critical system issues escalate outside standard cadence.
Public-facing escalation handling is owned by the client — Cisco receives feedback
from clients for improvement purposes only

**Audit cadence:** Bi-weekly feedback review as standard. Critical issues trigger
immediate out-of-cadence review

**Regulatory exposure:** Currently Americas-based — EU AI Act does not apply directly.
If client base expands to EU, system would likely classify as limited risk (transparency
obligations). Current exposure to assess: CCPA for California-based clients, and
contractual liability risk if incorrect technical advice contributes to an outage or
data loss. Regulatory exposure to be formally assessed as client base and regions grow

---

## Agent Topology

*Note: Full agent architecture is owned by engineering. The topology below is a
recommended starting point for validation with the engineering team.*

**Retrieval Agent**
- Can: Search the RAG across permitted knowledge bases, identify correct device
model/version, pull relevant documents, videos, and images
- Cannot: Access knowledge bases outside the user's permission scope, query
cross-team RAGs until boundaries are built
- Approves: Source selection for the query

**Summarization Agent**
- Can: Generate step-by-step resolutions, contract summaries, and multi-source
synthesized answers with source attribution
- Cannot: Perform any system actions, modify documents, or access external systems
- Approves: Format and content of the response

**Confidence & Routing Agent**
- Can: Evaluate output confidence, apply tiered UX logic (high/medium/low),
flag low-confidence responses, surface warnings, recommend escalation
- Cannot: Override a human decision, close tickets, or take autonomous action
- Approves: Whether the answer is shown directly, shown with a warning, or blocked
and escalated to a human

**Governance note:** No agent has write access to any connected system.
All agents are advisory only. Human approval required for any action taken
as a result of AI output.

---

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| ChatGPT | IT / Authorized | M | Govern — add usage monitoring |
| GitHub Copilot | Engineering / Authorized | L | Keep |
| Internal network AI tools | Cisco IT / Authorized | L | Keep |
| Unmonitored personal AI accounts | Unknown | H | Govern — build detection and enforce policy; employees risk termination for unauthorized use |

**Total tools found:** 4 (3 authorized + 1 shadow category identified)

**Tools after triage:** All 4 retained with appropriate governance level — none killed

**Estimated hidden spend:** Unknown — to be assessed. No current visibility into
personal account usage. Recommend adding to next governance audit cycle.

---
---

# Exercise 3: Cost Curve & Pricing Strategy

## Cost Model

| Cost Category | Per-SR | Monthly (4,700 SRs) | Notes |
|--------------|--------|---------------------|-------|
| Inference (primary model) | $0.02 | $94 | GPT-4, migrating to new model next month |
| Inference (cascading/triage) | TBD | TBD | To be defined post-migration |
| Infrastructure | $1.06 | $5,000 | Azure + Neo4j, $15K/quarter |
| Data/storage | Included | Included | Covered in infrastructure cost |
| Human-in-the-loop | $0.53 | $1,880 | 40% escalation rate × $13/SR engineer cost |
| **Total AI COGS** | **$1.61** | **$6,974** | |

**Baseline comparison:**
- Fully human-handled cost: $13/SR (based on $100K engineer salary, 15 min per SR)
- Current monthly cost fully human: $61,100/month
- AI-assisted monthly cost: $6,974/month
- **Monthly saving: ~$45,825**
- **Annual net benefit: ~$466,212**

**Deflection breakdown:**

| Tier | % of SRs | Monthly Volume | Saving vs Human |
|------|----------|----------------|-----------------|
| Fully deflected (AI handles) | 60% | 2,820 SRs | $36,660/month |
| AI-assisted (human confirms) | 30% | 1,410 SRs | $9,165/month |
| Fully escalated (human handles) | 10% | 470 SRs | $0 |

---

## Cascading Strategy

**Triage model:** GPT-3.5 Turbo — handles simple queries, clarification requests,
single-source lookups, and FAQ-style questions

**Frontier model:** GPT-4 — handles complex multi-source synthesis, plain language
interpretation, and low-confidence queries requiring maximum accuracy

**Mid-tier model:** GPT-4o mini — handles medium complexity queries, single-source
technical questions with known model/version

**Routing rule:** Combination of three signals:
- Query complexity detected at intake (classification)
- Number of sources required for the answer
- Confidence score from the triage model

| Condition | Model |
|-----------|-------|
| Simple + single source + known model/version | GPT-3.5 Turbo |
| Multiple sources needed OR medium confidence | GPT-4o mini |
| Complex + multi-source + plain language OR low confidence | GPT-4 |

**Expected cascade ratio:**

| Tier | Model | % of Queries | Est. Cost/SR |
|------|-------|-------------|--------------|
| Simple | GPT-3.5 Turbo | 60% | ~$0.002 |
| Medium | GPT-4o mini | 30% | ~$0.01 |
| Complex | GPT-4 | 10% | ~$0.02 |
| **Blended** | | **100%** | **~$0.005** |

**Note:** Cascading reduces blended inference cost from $0.02 to ~$0.005 per SR —
a 75% reduction in inference costs as volume scales

---

## Pricing Model

**Current pricing:** No chargeback model — IT Operations absorbs cost as a
shared internal service

**Proposed AI pricing:** Outcome-based internal value model

**Model:** Outcome-based

**Value metric:** Cost per SR deflected
- Baseline human cost: $13/SR (based on $100K engineer salary, 15 min per SR)
- AI cost: $1.61/SR (blended COGS at current volume)
- **Value delivered per deflected SR: $11.39**

**Monthly value report to leadership:**

| Metric | Current Month |
|--------|--------------|
| Total SRs | 4,700 |
| SRs fully deflected (60%) | 2,820 |
| SRs AI-assisted (30%) | 1,410 |
| SRs fully escalated (10%) | 470 |
| Monthly AI COGS | $6,974 |
| Monthly value delivered | ~$45,825 |
| **Net monthly benefit** | **~$38,851** |

**Note:** As deflection rate improves through better RAG coverage, cascading
optimization, and knowledge base expansion, the ROI compounds without
proportional cost increase. Deflection rate is the primary metric to track
and improve.

---

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | Low immediate impact — inference is only $94/month of $6,974 COGS, rises to ~$282/month. Manageable at current volume, material at scale | Evaluate competing model pricing first. If sustained, explore running a model in-house on existing infrastructure. Cascading ratio adjustment as lever |
| Heaviest segment doubles (engineering SRs 2,820 → 5,640/month) | Infrastructure scales from $5,000 to ~$8-10K/month but value delivered scales from $45,825 to ~$91,650/month — net benefit still grows significantly. Parallel request limit of 25 becomes a bottleneck | Scale infrastructure justified by ROI delivered. Currently in progress. Let deflection value fund the infrastructure investment |
| Model provider raises prices 50% | Blended inference rises from $0.005 to ~$0.0075/SR — ~$12/month extra at current volume. Low now, material at scale | Negotiate with provider using Cisco's volume as leverage. Cascading strategy provides credible threat to route more volume to cheaper models. Evaluate alternative providers if negotiation fails |

---

## Board One-Pager

**Before (traditional model):**
- Every SR handled manually by an engineer
- 4,700 SRs/month × $13/SR = $61,100/month in engineering time on support work
- Support coverage: 24/5 — no after-hours or weekend coverage
- Engineers tied up on repetitive troubleshooting, limited capacity for higher-value work
- Resolution speed dependent on engineer availability and queue depth
- Client experience inconsistent — dependent on which engineer picks up the ticket

**After (AI-enabled):**
- 60% of SRs fully deflected by AI — no engineer involvement needed
- 30% AI-assisted — engineer confirms or adjusts AI recommendation
- 10% fully escalated — complex or low-confidence queries handled by engineer
- Total AI COGS: $6,974/month
- Support coverage: moving toward 24/7 — AI available outside engineer hours
  without adding headcount
- Engineers freed for higher-value work — architecture, escalations, improvements
- Consistent, source-attributed answers with confidence tiering and feedback loop

**Net margin shift:**

| Metric | Before | After | Delta |
|--------|--------|-------|-------|
| Monthly support cost | $61,100 | $6,974 | -$54,126 |
| SR deflection rate | 0% | 60% | +60% |
| AI-assisted rate | 0% | 30% | +30% |
| Coverage hours | 24/5 | Toward 24/7 | +48hrs/week |
| Net monthly benefit | — | $38,851 | +$38,851 |
| **Annual net benefit** | — | **$466,212** | **+$466,212** |

**Strategic shift:** From reactive, human-dependent support to proactive,
AI-assisted resolution with human oversight — engineers elevated from
ticket handlers to knowledge curators and exception managers.

*Note: Figures based on hypothetical baseline of $13/SR engineer cost
($100K salary, 15 min per SR) and current volume of 4,700 SRs/month.
Deflection rates are early-stage estimates to be validated as system scales.*

---
---

# Strategy Evaluation — Board-Level Critique

## Strategy Inputs Summary

| Component | Summary |
|-----------|---------|
| The Bet | AI support assistant, 4,700 SRs/month, kill criteria at <40% deflection after 6 months |
| The Moat | Proprietary RAG on Cisco internal docs, 3 feedback loops (2 active, 1 broken) |
| The Margin | $1.61/SR AI vs $13/SR human, $466K annual net benefit, outcome-based value model |
| The Contract | 90% accuracy, tiered confidence UX, 5-row golden dataset, HITL advisory only |
| The Guardrails | 3-agent topology, shadow AI audited, Americas-based, bi-weekly review |

---

## Evaluation Results

### Bet validation — 3/5
**Strengths:** Grounded in real operational pain with measurable baseline. Kill criteria is specific and actionable.
**Gaps:** No user interview evidence. 60% deflection assumption is untested. Falsifiable hypothesis not explicitly stated.
**Recommendation:** Run a 2-week structured pilot with 10 engineers to measure actual deflection rate before scaling infrastructure.

### Capability assessment — 3/5
**Strengths:** 3-agent topology well-designed. RAG + Neo4j stack in place. Cascading strategy shows infrastructure maturity.
**Gaps:** Cross-team RAG permissions layer not built. Drift remediation loop broken. Model migration underway mid-deployment.
**Recommendation:** Prioritize cross-team permissions layer and broken drift loop as Q1 engineering commitments.

### Impact analysis — 4/5
**Strengths:** $466,212 annual net benefit clearly articulated. Compounding logic is sound. 24/7 coverage upgrade is a real qualitative win.
**Gaps:** No sensitivity model if deflection stalls below 60%. After-hours coverage gap not quantified.
**Recommendation:** Build a deflection sensitivity table at 40%, 50%, 60%, and 70% for leadership review.

### Defensibility check — 4/5
**Strengths:** Internal product — low platform encroachment risk. Proprietary knowledge base is not replicable. Engineer resolution uploads create genuine compounding defensibility.
**Gaps:** Data flywheel depends on engineer upload behavior that is not yet measured or incentivized. Cross-team silos limit moat depth.
**Recommendation:** Define and track a "knowledge base contribution rate" as a leading moat indicator.

### Pricing alignment — 4/5
**Strengths:** Outcome-based value model is correct for internal product. Cascading reduces blended inference 75%. Stress tests well-reasoned.
**Gaps:** 25 parallel request ceiling will break economics at scale. No 10x volume model exists.
**Recommendation:** Build a 12-month volume projection showing COGS and net benefit at 1x, 3x, and 10x current SR volume.

### Trust & reliability — 4/5
**Strengths:** Tiered confidence UX is thoughtful and user-appropriate. HITL correctly scoped. 0% hallucination target for contract queries shows appropriate risk calibration.
**Gaps:** Golden dataset has only 5 rows. Drift remediation loop is broken. No SLA for how quickly accuracy drops must be fixed.
**Recommendation:** Expand golden dataset to 25 rows and define a drift remediation SLA (e.g. >5% accuracy drop fixed within 5 business days).

### Governance & scale — 3/5
**Strengths:** Shadow AI audit more thorough than most enterprise teams attempt. Agent boundaries clearly defined. Bi-weekly review cadence pragmatic for early stage.
**Gaps:** Broken drift loop means silent accuracy degradation is possible. No detection mechanism for personal account shadow AI. No plan for governance upgrade at 10x volume.
**Recommendation:** Fix drift remediation loop before scaling — assign named owner, SLA, and automate refresh trigger.

### Gap identification — 3/5
**Strengths:** Team demonstrates genuine self-awareness about gaps — broken loop, unbuilt permissions, untested deflection rate all surfaced honestly.
**Gaps:** Weakest component is the Moat — flywheel depends on unmeasured engineer behavior. Biggest untested assumption is 60% deflection rate.
**Recommendation:** Replace the 60% deflection assumption with actual measured pilot data before next leadership review.

---

## Overall Assessment

**Overall strategy strength: 3.5/5**

**Biggest risk:** The 60% deflection rate assumption is untested — if actual deflection lands at 35-40%, the entire ROI story collapses and the infrastructure investment is hard to justify.

**Top 3 actions:**
1. Run a 2-week pilot with real engineers to measure actual deflection rate — replace the assumption with evidence before scaling or presenting to leadership
2. Fix the broken drift remediation loop — assign an owner, define a time-to-fix SLA, and automate the knowledge base refresh trigger
3. Build the cross-team RAG permissions layer — without it, the system cannot synthesize across engineering and contracts knowledge, which is its highest-value use case and primary moat driver
