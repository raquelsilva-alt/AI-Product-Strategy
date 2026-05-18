# Cost Curve & Pricing Strategy

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

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | Low immediate impact — inference is only $94/month of $6,974 COGS, rises to ~$282/month. Manageable at current volume, material at scale | Evaluate competing model pricing first. If sustained, explore running a model in-house on existing infrastructure. Cascading ratio adjustment as lever |
| Heaviest segment doubles (engineering SRs 2,820 → 5,640/month) | Infrastructure scales from $5,000 to ~$8-10K/month but value delivered scales from $45,825 to ~$91,650/month — net benefit still grows significantly. Parallel request limit of 25 becomes a bottleneck | Scale infrastructure justified by ROI delivered. Currently in progress. Let deflection value fund the infrastructure investment |
| Model provider raises prices 50% | Blended inference rises from $0.005 to ~$0.0075/SR — ~$12/month extra at current volume. Low now, material at scale | Negotiate with provider using Cisco's volume as leverage. Cascading strategy provides credible threat to route more volume to cheaper models. Evaluate alternative providers if negotiation fails |

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

Keep in Mind
80% of requests can usually run on a cheaper model. Adjust the cascading ratio in your cost curve — the savings compound fast. Start with your highest-volume feature.
