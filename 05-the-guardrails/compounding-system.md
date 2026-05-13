# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| User feedback | Accuracy rating + feedback on answer | Flags low-rated answers for review, improves retrieval/prompting | Y | Active |
| Engineer uploads resolution | Engineer adds missed resolution doc to RAG | Knowledge base expanded, future similar queries answered correctly | Y | Active |
| Drift monitoring | Monthly golden dataset re-evaluation detects accuracy drop | Triggers knowledge base refresh or model/prompt update | Y | Broken |

**Broken loop identified by partner:** Drift monitoring exists but remediation is too slow and manual — improvements to the refresh process are missing

**Fix plan:** Define a clear owner for drift remediation, establish a maximum time-to-fix SLA after drift is detected, and automate the knowledge base refresh trigger where possible
Ready for Context Connectivity when you are!

## Context Connectivity
<!-- How does knowledge flow across teams and domains? Where does it silo? -->

## Governance Policy

**Scope:**
**Autonomy boundaries:**
**Escalation triggers:**
**Audit cadence:**
**Regulatory exposure (EU AI Act / other):**

## Agent Topology
<!-- If using agents: what can each agent do? What can't it do? Who approves what? -->

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |

**Total tools found:**
**Tools after triage:**
**Estimated hidden spend:**
