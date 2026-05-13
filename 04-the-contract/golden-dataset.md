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

**Approach:** Tiered confidence — no mixed signals, clear routing per tier

**High confidence (>90%):** Answer returned directly with source reference, no friction

**Medium confidence (70-90%):** Answer returned with advisory — *"Please confirm this with your team or the relevant department before proceeding"*

**Low confidence (<70%):** Partial answer shown with warning — *"Here's what I found, but I'm not confident this is accurate for your specific situation — please verify with an engineer or the relevant department before acting on this"*

**User control surface:** Feedback button + accuracy rating on every response
**User control surface:**

## Reliability Contract

| Metric | Target | Measurement | Alert Threshold |
|--------|--------|-------------|-----------------|
| Accuracy | 90% | LLM judge eval on golden dataset | <85% |
| Hallucination rate | 0% contract/warranty — <2% technical | Automated source grounding check | Any hallucination on contract queries — >1% on technical |
| Latency (p95) | <3 seconds | Response time monitoring | >3s on 5% of queries |
| Drift velocity | Monitored monthly | Golden dataset re-evaluation | >5% accuracy drop month-over-month |
