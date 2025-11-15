# TEMPLATE: ROI & Impact Estimation Guide

**Purpose:** Estimate the business impact of a proposed feature to justify engineering investment and get leadership buy-in.

**When to use:** After you've identified a problem and proposed solution, before committing engineering resources.

---

## Template Structure

```markdown
# Impact Estimation: [Feature Name]

**Feature:** [1-sentence description of what you're building]
**Problem:** [What problem does this solve? Include metric]
**Solution:** [How does this feature solve the problem?]

---

## Current State (Baseline Metrics)

**From [data source] analysis:**

| Metric | Value | Source |
|--------|-------|--------|
| **[Metric 1]** | [Value] | [Where you got this number] |
| **[Metric 2]** | [Value] | [Where you got this number] |
| **Current [key rate]** | [%] | [Data source] |
| **[Time metric]** | [Duration] | [Data source] |

**Note:** [Any caveats about data quality or assumptions]

---

## Value Per [Action]

**Revenue Model:**
- **[Conversion metric]:** [%]
- **ARPU (average revenue per user):** $[amount]/month
- **Average customer lifetime:** [N] months
- **LTV per paying customer:** $[amount] × [N] months = $[total]

**Value per [action]:**
```
$[LTV] × [conversion %] = $[value] per [action]
```

---

## Projected Impact (Realistic Scenario)

### Users Affected

**Assumption:** [How will feature rollout work?]
- **Total monthly [user type]:** [N] users/month
- **Feature adoption rate:** [%] ([reason for this assumption])
- **Users affected:** [N] × [%] = **[N] users/month**

### Expected Lift

**Reasoning:**
- [Data point 1 supporting lift estimate]
- [Data point 2 supporting lift estimate]
- [Conservative adjustment and why]
- **Being extra conservative:** [final %]pp lift

**Lift calculation:**
- **Current [rate]:** [%]
- **Projected [rate]:** [%] + [N]pp = **[%]**

### Business Impact

**Current [converted users] (of those who see feature):**
- [N] users/month × [%] = [N] [converted]/month

**Projected [converted users] (with feature):**
- [N] users/month × [%] = [N] [converted]/month

**Incremental impact:**
- **+[N] [converted users]/month**

### Revenue Impact

**Monthly recurring revenue:**
- [N] users × $[ARPU] × [conversion %] = **$[amount] MRR**

**Annual recurring revenue:**
- $[MRR] × 12 months = **$[amount] ARR**

**3-year LTV value:**
- [N] users × 12 months × $[LTV] = **$[amount]**

---

## Investment Required

**Engineering estimate:** [N] engineers × [N] weeks/months
- [Task 1]
- [Task 2]
- [Task 3]
- [Task 4]

**Cost:** **$[amount]**

**Other costs:**
- Design: $[amount]
- QA: $[amount]
- Infrastructure: $[amount]/month ongoing
- **Total:** $[amount]

---

## ROI Analysis

### Year 1
- **Revenue:** $[ARR]
- **Cost:** $[total investment]
- **ROI:** [X]x ([interpretation: break even / profitable / loss])

### 3-Year LTV
- **Value:** $[LTV value]
- **Cost:** $[total investment]
- **ROI:** **[X]x**

### Payback Period
- Monthly incremental MRR: $[amount]
- Months to break even: $[cost] / $[MRR] = **~[N] months** ([N] years)

---

## Key Assumptions & Risks

### Assumptions
1. **[Assumption 1]** - [why you believe this]
   - Risk: [what if this is wrong?]
   - Mitigation: [how to reduce this risk]

2. **[Assumption 2]** - [why you believe this]
   - Risk: [what if this is wrong?]
   - Mitigation: [how to reduce this risk]

3. **[Assumption 3]** - [why you believe this]
   - Risk: [what if this is wrong?]
   - Mitigation: [how to reduce this risk]

### Risks

**Execution risks:**
- [Risk 1]
- [Risk 2]

**Market risks:**
- [Risk 1]
- [Risk 2]

**Data risks:**
- [Risk 1]
- [Risk 2]

---

## Strategic Value (Beyond ROI)

**[Strategic pillar 1]:**
- [How this unlocks growth/competitive positioning/etc.]

**[Strategic pillar 2]:**
- [How this creates compound value]

**[Strategic pillar 3]:**
- [What this enables for future roadmap]

---

## Three Scenarios Analysis

### Pessimistic Scenario (20th percentile)

**Assumptions:**
- Lower adoption: [%] instead of [%]
- Lower lift: [%] → [%] instead of [%] → [%]
- [Other conservative assumption]

**Impact:**
- Incremental users: +[N]/month
- ARR: $[amount]
- 3-year LTV: $[amount]
- ROI: [X]x over 3 years

### Realistic Scenario (50th percentile)

**Assumptions:**
- Expected adoption: [%]
- Conservative lift based on data: [%] → [%]
- [Your "most likely" case]

**Impact:**
- Incremental users: +[N]/month
- ARR: $[amount]
- 3-year LTV: $[amount]
- ROI: [X]x over 3 years

### Optimistic Scenario (80th percentile)

**Assumptions:**
- High adoption: [%]
- Strong lift plus secondary effects: [%] → [%] + [secondary benefit]
- [Best-case if everything works]

**Impact:**
- Incremental users: +[N]/month
- ARR: $[amount]
- 3-year LTV: $[amount]
- ROI: [X]x over 3 years

**Key insight:** Even in pessimistic case, ROI is [X]x. Realistic case is [X]x. [Interpretation]

---

## Recommendation

**[BUILD / DO NOT BUILD / BUILD WITH MODIFICATIONS]**

### Why This [Passes/Doesn't Pass]:

[If BUILD:]
✅ **[Reason 1]**
✅ **[Reason 2]**
✅ **[Reason 3]**

⚠️ **[Caveat 1]**
⚠️ **[Caveat 2]**

[If DO NOT BUILD:]
❌ **[Reason 1]**
❌ **[Reason 2]**
❌ **[Reason 3]**

### Alternative Approaches to Explore

[If not building at current scope:]

**Option A: [Lighter-weight version] ($[cost], [timeline])**
- [What it is]
- **Pros:** [benefits]
- **Cons:** [tradeoffs]

**Option B: [Different approach] ($[cost], [timeline])**
- [What it is]
- **Pros:** [benefits]
- **Cons:** [tradeoffs]

**Option C: [Validation approach] ($[cost], [timeline])**
- [What it is]
- **Pros:** [benefits]
- **Cons:** [tradeoffs]

---

## Recommended Next Steps

1. **[Timeframe]:** [Action]
2. **[Timeframe]:** [Action]
3. **[Timeframe]:** [Action]
4. **[Timeframe]:** [Action]
5. **[Timeframe]:** [Action]

**Bottom line:** [1-2 sentence summary of decision and rationale]
```

---

## The Impact Estimation Formula

```
Impact = Users Affected × Current Action Rate × Expected Lift × Value per Action
```

### Breaking Down Each Component:

**1. Users Affected**
- How many users will be exposed to this feature?
- Not always 100% - account for gradual rollout, specific segments, voluntary adoption
- Example: 5,000 signups/month × 70% see feature = 3,500 affected

**2. Current Action Rate**
- What % of users currently take the desired action?
- Find in analytics: activation rate, conversion rate, feature adoption, etc.
- Example: 45% of signups complete first task

**3. Expected Lift**
- How much will the feature improve the action rate?
- **This is the hardest part** - base it on:
  - Similar features you've shipped (historical data)
  - Competitor benchmarks (if public)
  - User research (e.g., "60% drop due to X, fixing X recovers 30% of drop-off")
  - Expert judgment from eng/design/PM
- Example: 45% → 58% = +13pp lift

**4. Value per Action**
- What is each incremental action worth to the business?
- Calculate: Action → Conversion → ARPU × Lifetime = LTV
- Example: Activation → 60% convert → $12/mo × 24 months = $172.80 LTV

---

## How to Estimate Lift (The Hard Part)

### Method 1: User Research-Based Estimation

**If you know the problem cause:**
1. Identify what % of users drop due to specific cause (from surveys)
2. Estimate what % of that drop-off you can recover
3. Be conservative (recover 30-50% of addressable drop-off)

**Example:**
- Current: 45% activation
- Problem: 60% drop-off between steps due to confusion
- Solution: If we eliminate confusion, recover 30% of that drop-off
- Math: 60% drop × 30% recovery = 18pp theoretical lift
- Conservative: 13pp actual estimate (accounting for execution risk)
- Projected: 45% + 13pp = 58%

### Method 2: Competitive Benchmark

**If competitors have similar feature:**
1. Find competitor's performance (if public)
2. Adjust for your product/market differences
3. Be conservative (aim for 70-80% of their performance)

**Example:**
- Competitor activation: 65%
- Your current activation: 45%
- Gap: 20pp
- Realistic target: Capture 60% of gap = +12pp lift
- Projected: 45% + 12pp = 57%

### Method 3: Historical Performance

**If you've shipped similar features:**
1. Look at past lift from analogous features
2. Adjust for scope/complexity differences
3. Average across multiple examples if available

**Example:**
- Last onboarding improvement: +8pp lift
- This feature is 1.5x scope
- Conservative estimate: 1.2x impact = +10pp
- Projected: 45% + 10pp = 55%

### Method 4: First Principles (When No Data Available)

**Break down the impact chain:**
1. What % of users will see the feature? (adoption)
2. Of those, what % will use it? (engagement)
3. Of those, what % will it help? (effectiveness)
4. Multiply these together

**Example:**
- 80% of users see feature
- 70% of those engage with it
- 40% of those successfully complete action
- Current baseline: 45%
- Incremental lift: 80% × 70% × 40% × (100% - 45%) = 15pp
- Conservative: 10pp (accounting for friction)
- Projected: 45% + 10pp = 55%

---

## Three Scenarios: How to Build Them

**Always create pessimistic/realistic/optimistic to show range:**

### Pessimistic (20th percentile)
- Lower adoption (30% vs 70%)
- Lower lift (+5pp vs +13pp)
- Account for execution issues
- No secondary benefits
- **Use case:** "What if things go wrong?"

### Realistic (50th percentile)
- Expected adoption (70%)
- Conservative lift estimate (+13pp)
- Your "most likely" case
- **Use case:** "What we actually expect"

### Optimistic (80th percentile)
- High adoption (90%)
- Strong lift (+18pp)
- Include secondary benefits (retention, viral growth)
- **Use case:** "What if things go really well?"

**Present all three** so leadership understands the range of outcomes.

---

## Decision Criteria: When to Build vs Not Build

### GREEN LIGHT (Build It):
- ✅ 3-year ROI > 3x
- ✅ Payback period < 18 months
- ✅ Year 1 ROI > 0.5x (at least half your money back)
- ✅ Even pessimistic scenario shows positive ROI
- ✅ Aligns with strategic priorities

### YELLOW LIGHT (Build with Modifications):
- ⚠️ 3-year ROI 2-3x (okay but not great)
- ⚠️ Payback 18-36 months (acceptable with strategic value)
- ⚠️ Year 1 ROI break-even or slightly negative
- ⚠️ Pessimistic scenario shows low/no ROI
- **Action:** Scope down, validate with prototype, or phase rollout

### RED LIGHT (Don't Build):
- ❌ 3-year ROI < 2x
- ❌ Payback > 36 months
- ❌ Year 1 ROI deeply negative (lose >50% of investment)
- ❌ Pessimistic scenario shows negative ROI
- ❌ High uncertainty in lift estimate
- **Action:** Find cheaper solution, validate hypothesis first, or kill

---

## Example Calculation (TaskFlow Guided Onboarding)

### Step 1: Users Affected
- Monthly signups: 5,000
- Feature adoption (gradual rollout): 70%
- **Users affected: 3,500/month**

### Step 2: Current Action Rate
- Current activation: 45%
- **Current activated: 2,025/month** (4,500 × 45%)

### Step 3: Expected Lift
- Problem: 60% drop due to confusion (survey data)
- Solution: Guided onboarding eliminates confusion
- Conservative recovery: 30% of 60% drop = 18pp theoretical
- Execution discount: Use 13pp actual
- **Projected activation: 58%** (45% + 13pp)

### Step 4: Value per Action
- Activation → 60% convert to paid
- ARPU: $12/month
- Lifetime: 24 months
- LTV: $12 × 24 = $288
- **Value per activation: $288 × 60% = $172.80**

### Step 5: Calculate Impact
- Current: 3,500 × 45% = 1,575 activated
- Projected: 3,500 × 58% = 2,030 activated
- **Incremental: +455 users/month**

### Step 6: Calculate Revenue
- MRR: 455 × $12 × 60% = $3,276
- **ARR: $39,312**
- **3-year LTV: 455 × 12 × $172.80 = $943,296**

### Step 7: ROI
- Investment: $100,000
- Year 1 ROI: $39k / $100k = 0.39x (lose $61k)
- **3-year ROI: $943k / $100k = 9.4x**
- **Payback: 30 months**

### Step 8: Decision
- 3-year ROI is strong (9.4x)
- BUT payback is long (2.5 years)
- AND Year 1 is deeply negative
- **Decision: Scope down or validate with cheaper approach first**

---

## Common Pitfalls to Avoid

❌ **Overly optimistic lift** - Don't assume you'll recover 100% of drop-off
❌ **Ignoring adoption** - Not all users will use your feature
❌ **Forgetting conversion** - Activated users don't all become paying customers
❌ **No scenarios** - Single-point estimates hide uncertainty
❌ **Missing costs** - Don't forget ongoing maintenance, infrastructure, support
❌ **Ignoring payback** - 10x ROI over 10 years isn't as good as 3x over 1 year
❌ **No strategic context** - Pure ROI doesn't capture competitive/platform value

---

## Output Checklist

Before presenting to leadership, ensure you have:

- [ ] Clear baseline metrics with sources
- [ ] Detailed calculation of users affected
- [ ] Well-reasoned lift estimate (not just a guess)
- [ ] Complete value-per-action calculation
- [ ] Three scenarios (pessimistic/realistic/optimistic)
- [ ] Year 1 and 3-year ROI
- [ ] Payback period calculated
- [ ] Key assumptions and risks stated
- [ ] Clear recommendation (build/don't build/modify)
- [ ] Alternative approaches if not building

---

**This template helps you go from feature idea → validated ROI model → confident decision with leadership buy-in.**
