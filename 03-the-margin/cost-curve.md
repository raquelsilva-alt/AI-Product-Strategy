# Cost Curve & Pricing Strategy

## Cost Model

| Cost Category | Per-User/Month | Notes |
|--------------|----------------|-------|
| Inference (primary model) | | |
| Inference (cascading/triage) | | |
| Infrastructure | | |
| Data/storage | | |
| Human-in-the-loop | | |
| **Total AI COGS** | | |

## Cascading Strategy
<!-- Cheap model → frontier model routing logic -->

**Triage model:**
**Frontier model:**
**Routing rule:**
**Expected cascade ratio:**

## Pricing Model

**Current pricing:**
**Proposed AI pricing:**
**Model:** seat-based / usage-based / outcome-based / hybrid

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | | |
| Heaviest segment doubles | | |
| Model provider raises prices 50% | | |

## Board One-Pager
<!-- Before/After: Old SaaS revenue vs. AI usage revenue for your product -->

**Before (traditional SaaS):**
**After (AI-enabled):**
**Net margin shift:**

Model shown in the slidedeck 
Features → tiers → blended COGS
Feature	Complexity	Model Tier	Cost/Req	Volume %	Weighted
_____	Simple	Small	$_____	___%	$_____
_____	Medium	Mid	$_____	___%	$_____
_____	Complex	Frontier	$_____	___%	$_____
Blended				100%	$_____
Estimate OK — structure beats false precision

Keep in Mind
80% of requests can usually run on a cheaper model. Adjust the cascading ratio in your cost curve — the savings compound fast. Start with your highest-volume feature.
