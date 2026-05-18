# Three-Horizon Roadmap & Board Pitch

## Roadmap

### Horizon 1 — Now (0-3 months)
*Quick wins. Ship with existing capabilities.*

| Initiative | Metric | Confidence |
|-----------|--------|-----------|
| Client self-onboarding — reduce engineer involvement in onboarding new clients to the tool | Evaluation score improvement | H |
| Feedback loop + system integration — tighten accuracy rating loop and integrate with main systems | User-rated accuracy score | M |

### Horizon 2 — Next (3-9 months)
*Bets. Requires new capabilities or integrations.*

| Initiative | Metric | Confidence |
|-----------|--------|-----------|
| Cross-team knowledge access — build permissions layer so engineers can query across technical and contract RAGs in a single request | SR deflection rate improvement (+10 points) | M |
| Drift monitoring automation — automate knowledge base refresh trigger to stop silent accuracy degradation | Accuracy stability month-over-month (<5% drop) | L |

### Horizon 3 — Bet (9-18 months)
*Moonshots. High uncertainty, high potential.*

| Initiative | Metric | Confidence |
|-----------|--------|-----------|
| Full confidential data integration — break all knowledge silos with proper permissions, making the system the single source of truth for all support knowledge | SR deflection rate >80%, knowledge coverage completeness | M |
| 24/7 scale — handle full SR volume without engineer dependency outside business hours, 100 parallel requests | SRs resolved outside business hours without escalation | M |

---

## Board Pitch

**Thesis (1 sentence):**
We have a working system that resolves Cisco support requests at $1.61 per case versus $13 with human handling — this investment makes it reliable enough to scale and removes the ceiling on what it can save.

**The case:**

1. Why now: We are running 4,700 service requests per month through this system today — this is not a proposal, it is a production system with a measurable baseline. The timing window is the infrastructure ceiling: at 25 parallel requests we are processing a fraction of what the system could handle. Every month we delay costs us $38,851 in recoverable savings. The H1 initiatives — client self-onboarding and feedback loop integration — ship within 3 months with existing capabilities and will produce measurable deflection improvement before the next leadership review.

2. What's defensible: The moat is not the AI model — models are commodities. The moat is the proprietary knowledge base: Cisco firmware manuals, contracts, SLA terms, and field engineer resolution uploads that no external vendor can access or replicate. Every SR the system handles adds signal. Every resolution an engineer uploads deepens the advantage. The H2 bet — cross-team knowledge access — is the initiative that compounds this further: when engineers can query across technical and contract knowledge in a single request, the system becomes the single source of truth for support. That is not replicable in 6 months by anyone starting from outside.

3. The economics: AI COGS are $1.61 per SR against a $13 human baseline — an 88% cost reduction per deflected request. Monthly AI cost is $6,974 against a fully human cost of $61,100. Annual net benefit at current volume is $466,212. The cascading model strategy — routing 60% of queries to cheaper models and only 10% to the frontier model — means blended inference cost is $0.005 per SR. Even if inference costs triple, the margin holds. The pricing model is outcome-based: value is reported as SRs deflected, not seats. The number goes up as deflection improves.

**The risks:**

1. Trust / failure modes: The system is advisory only — it cannot take action on any connected system, cannot close tickets, and cannot modify anything. The failure mode we are managing is hallucination on contract and warranty queries, where we hold a 0% tolerance target. A tiered confidence UX ensures low-confidence answers surface a warning and route to a human rather than presenting a wrong answer as fact. The Wall Street Journal scenario — an engineer acts on incorrect advice that causes an outage — is caught by the HITL architecture: every SR still requires human sign-off on action. The H1 feedback loop initiative tightens accuracy measurement so we catch degradation in real time.

2. Scale / governance: Three things break at 10x volume — the 25 parallel request ceiling, the bi-weekly review cadence, and the drift monitoring loop (currently broken, remediation is manual). The $25K/quarter infrastructure ask addresses the first. The 3 engineer ask addresses th
