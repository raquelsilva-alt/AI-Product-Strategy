# Golden Dataset & Reliability Contract

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

**Adversarial rows included:** __
**Coverage gaps identified by partner:**

## Confidence UX Design

**Approach:** show uncertainty / tiered confidence / human-in-loop trigger

**High confidence (>90%):**
**Medium confidence (70-90%):**
**Low confidence (<70%):**

**User control surface:**

## Reliability Contract

| Metric | Target | Measurement | Alert Threshold |
|--------|--------|-------------|-----------------|
| Accuracy | | | |
| Hallucination rate | | | |
| Latency (p95) | | | |
| Drift velocity | | | |

## HITL Architecture
<!-- When does a human step in? What's the escalation path? -->

## Red-Team Findings
*What failure mode did your partner find that you missed?*
