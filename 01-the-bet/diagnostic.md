# Three-Axis Vulnerability Diagnostic

## Product
**Product:** AI Support Assistant — document, video, and image summarization into chat for equipment and contract issue resolution
**Your Role:** Program Manager, IT Operations

---

## Scores

### Contextual Moat — 2/5
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*

**Score rationale:** The system is embedded in the support workflow but only as an advisory layer — engineers and clients still close tickets manually. There is no deep workflow lock-in yet. Cross-team RAG access is not built, so the system does not yet sit at the center of how support knowledge flows across the organization. A well-configured competitor with a clean interface could be trialed over a weekend. The moat is the data, not the workflow depth — and workflow depth is what drives switching cost. Score improves as cross-team integration and 24/7 scale are delivered in H2/H3.

**Named attacker:** Claude / other internal AI tool or new internal build

---

### Data Advantage — 4/5
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*

**Score rationale:** This is the strongest dimension. The knowledge base is built from Cisco-specific firmware manuals, contract terms, SLA data, and field engineer resolution uploads that no external vendor can access. Every SR handled adds signal. Every resolution an engineer uploads deepens the advantage. The compounding feedback loops (user ratings → retrieval improvement, engineer uploads → RAG expansion) are active. Score is 4 not 5 because the drift monitoring loop is broken, cross-team RAG silos limit knowledge depth, and static file uploads create staleness risk.

**Named attacker:** GitHub Copilot / Microsoft — already integrated into the engineering toolchain and has access to code repositories, which partially overlaps with technical troubleshooting use cases

---

### Platform Exposure — 3/5
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native — then what?*

**Score rationale:** The hero feature — document and video summarization into chat — is replicable by any major platform within 12 months. Microsoft Copilot already ships document summarization natively inside Teams and SharePoint, which is the same environment where much of the knowledge base lives. The defense is not the feature, it is the proprietary data and domain specificity. A generic Copilot summarizing a Cisco firmware manual gives a generic answer. This system gives a Cisco-specific, version-accurate, contract-aware answer. Platform exposure is real but manageable as long as data advantage compounds faster than platform feature parity.

**Named attacker:** Microsoft Copilot — SharePoint integration means it is already adjacent to the knowledge base and one configuration away from attempting the same use case

---

## Killer Memo

> You run AI at **Microsoft**. Your OKR: make this product irrelevant before it becomes a dependency.
>
> 1. **Attack:** Their system reduces hallucinations through domain-specific RAG and is tightly scoped to equipment and contract queries — but it is built on top of Azure OpenAI, which we own. We can ship native Copilot integration into SharePoint and Teams that does the same summarization with zero additional infrastructure cost to the customer.
>
> 2. **Wedge:** We already have the integrations — SharePoint, Teams, Azure, the entire M365 stack. Their system requires a separate chat interface and a separate knowledge base pipeline. We ship the same feature inside the tools engineers already use every day, with no migration required.
>
> 3. **Why users switch:** They switch because we remove friction. No new tool to onboard, no separate login, no parallel system to maintain. The only thing their system has that we don't is the proprietary historical resolution data — and we close that gap the moment they connect SharePoint to Copilot, which their own H1 initiative is designed to do for us.

---

## Top Vulnerability
The system's hero feature is fully replicable by Microsoft Copilot using infrastructure the customer already pays for — the only defensible asset is the proprietary knowledge base, and every integration that connects that knowledge base to Microsoft tooling accelerates the encroachment.

## Confidence Level
**M** — The bet is sound and the data advantage is real, but the low contextual moat score (2/5) means the product has not yet earned deep switching cost. Confidence upgrades to H when cross-team knowledge integration is live and engineers cannot do their jobs without it.
