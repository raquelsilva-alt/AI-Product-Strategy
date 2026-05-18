# Kill Switch Audit

## Vendor Dependency Assessment

### Current State (Azure OpenAI / GPT-4 → migrating away from Claude/Anthropic)

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | Single vendor (Azure OpenAI), single model (GPT-4), no fallback. Previously on Claude/Anthropic — migration forced by external factors | H | Identify and pre-approve at least one alternative provider (e.g. AWS Bedrock, Google Vertex) so a switch decision can execute immediately |
| **Abstraction** | No abstraction layer — application calls Azure OpenAI API directly. Model swap requires code changes across the stack | H | Wrap all model calls in a single abstraction layer (LiteLLM or equivalent) so provider swaps become a config change, not a code change |
| **Routing** | Cascading strategy designed (GPT-3.5 Turbo → GPT-4o mini → GPT-4) but not yet live — all traffic hitting frontier model | H | Prioritise routing implementation as H1 engineering task — every day without it means overpaying on inference and carrying full vendor risk |
| **Eval** | 5-row golden dataset, LLM judge defined, model-agnostic — evals will survive a model swap. Drift monitoring loop broken | M | Fix drift remediation loop and expand golden dataset to 25 rows so post-migration accuracy can be validated immediately |

### Post-Migration State (new primary vendor)

| Dimension | Post-Migration State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | New single vendor replacing Claude/Anthropic — dependency shifts but doesn't reduce | H | Same as above — pre-approve a second provider before migration completes, not after |
| **Abstraction** | Still no abstraction layer unless built during migration — same code-change risk | H | Build abstraction layer as part of migration work, not as a separate project |
| **Routing** | Cascading live post-migration — reduces frontier model exposure to 10% of queries | M | Monitor cascade ratio monthly and adjust routing thresholds as query patterns evolve |
| **Eval** | Same eval infrastructure, model-agnostic — validate golden dataset scores on new model before full cutover | M | Run full golden dataset eval on new model in staging before any production traffic switches |

---

## Portability Score

**Current: Locked**
No abstraction layer, no routing, single vendor. A forced migration requires engineering effort across the stack and carries accuracy risk without a validated eval run on the new model.

**Post-migration target: Partial**
Cascading reduces frontier dependency to 10% of queries. Portability improves if abstraction layer is built during migration. Still Locked until abstraction layer exists.

---

## If primary vendor doubles pricing tomorrow:

**48-hour response:**
1. Cascading routing (if live) immediately shifts more volume to GPT-3.5 Turbo and GPT-4o mini — frontier model exposure drops from 100% to 10%, blunting the impact
2. If routing not yet live — calculate actual cost impact: inference is currently only $94/month of $6,974 COGS, so even a 2x increase is ~$94/month additional — manageable short-term
3. Open pricing negotiation using Cisco volume as leverage
4. Simultaneously evaluate AWS Bedrock and Google Vertex as alternative providers
5. If abstraction layer exists — provider swap executable within 48 hours. If not — begin abstraction layer build immediately as the single most important engineering task

---

## If primary vendor ships a competing product:

**What's defensible that they can't replicate:**
- **The proprietary knowledge base** — Cisco-specific firmware manuals, contracts, SLA terms, and field engineer resolution uploads accumulated over months of production use. A vendor starting today starts with nothing.
- **The workflow integration** — the system is embedded in how engineers and clients actually resolve SRs. Switching costs are behavioral, not just technical.
- **The feedback loops** — user ratings, engineer resolution uploads, and drift monitoring are compounding the knowledge base continuously. A vendor product ships generic; ours ships Cisco-specific and gets more Cisco-specific every day.
- **What they CAN replicate** — the model, the chat interface, the RAG architecture. None of that is the moat.
- **Bottom line** — a vendor shipping a competing product is a threat to the interface, not to the data. The response is to accelerate cross-team knowledge integration and deepen workflow embedding before the vendor reaches feature parity.
