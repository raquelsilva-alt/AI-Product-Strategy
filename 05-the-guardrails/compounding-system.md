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
