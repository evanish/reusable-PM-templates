# TEMPLATE: A/B Test Analysis Guide

**Purpose:** Analyze experiment results to make a ship/no-ship decision with confidence, looking beyond topline metrics to understand quality, segmentation, and leading indicators.

**When to use:** After running an A/B test and collecting results data. Before shipping to 100% or killing the feature.

---

## Template Structure

```markdown
# Experiment Results: [Feature Name] - Keep or Kill?

**Experiment:** [1-sentence description of what was tested]
**Duration:** [N] weeks/days
**Sample Size:** [N] users ([N] control, [N] treatment)
**Date:** [Month Year]

---

## Executive Summary

**Topline Result:** [Overall metric result - be honest if disappointing]

**Recommendation:** **[SHIP TO 100% / SHIP TO SEGMENT / ITERATE / KILL]**

**Why:**
- [Key finding 1 - typically segment performance]
- [Key finding 2 - typically quality metrics]
- [Key finding 3 - typically leading indicators]
- [Key risk or caveat]

---

## Topline Results

### Overall [Primary Metric]

| Cohort | Total Users | [Converted] | [Metric] Rate |
|--------|-------------|-------------|---------------|
| **Control** | [N] | [N] | **[%]** |
| **Treatment** | [N] | [N] | **[%]** |
| **Lift** | - | +[N] | **+[N]pp** |

**Calculation shown:**
- Control: [N] [converted] / [N] total = [decimal] = [%]
- Treatment: [N] [converted] / [N] total = [decimal] = [%]
- Absolute lift: [%] - [%] = **+[N] percentage points**
- Relative lift: ([decimal] - [decimal]) / [decimal] × 100 = **+[%]**

**Statistical Significance:** p [< or >] [threshold] ([significant/not significant])

---

### Initial Assessment

[Honest assessment of topline - did it meet expectations?]

[If disappointing, acknowledge it:]
- We projected [N]pp lift ([%] → [%]) in our impact model
- Actual result: [N]pp lift ([%] → [%])
- **[X]% of expected impact**

[Transition to deeper analysis:]
**But wait - we haven't segmented yet.**

---

## Segment Analysis by [Key Attribute]

**This is where the story changes:**

| [Segment Name] | Control Rate | Treatment Rate | Lift | Statistical Sig |
|----------------|--------------|----------------|------|-----------------|
| **[Segment A]** | [%] ([N]/[N]) | [%] ([N]/[N]) | **+[N]pp** | p < [threshold] ✓/✗ |
| **[Segment B]** | [%] ([N]/[N]) | [%] ([N]/[N]) | +[N]pp | p = [value] |
| **[Segment C]** | [%] ([N]/[N]) | [%] ([N]/[N]) | **-[N]pp** | p = [value] |

**Key Finding:** [Interpretation - which segment won/lost and why?]

### Why This Makes Sense

**[Segment that won]:**
- [Reason 1 why feature works for this segment]
- [Reason 2 connecting to user research/behavior]
- [Conclusion about segment fit]

**[Segment that lost]:**
- [Reason 1 why feature doesn't work for this segment]
- [Reason 2 about different needs]
- [Conclusion about why negative/flat result]

**This validates our [hypothesis/user research]:** [Connection to prior insights]

---

## Quality Metrics: Beyond Activation

### [Quality Metric 1] (Among [Converted] Users)

| Cohort | [Converted] Users | [High Quality] | [Quality] Rate |
|--------|-------------------|----------------|----------------|
| **Control** | [N] | [N] | **[%]** |
| **Treatment** | [N] | [N] | **[%]** |
| **Lift** | - | +[N] | **+[N]pp** |

**Calculation shown:**
- Control: [N] [quality metric] / [N] [converted] = [decimal] = [%]
- Treatment: [N] [quality metric] / [N] [converted] = [decimal] = [%]
- Lift: [%] - [%] = **+[N] percentage points**

**What this means:**
- [Interpretation of quality impact]
- [Connection to long-term value]

### [Engagement Metric] in [Timeframe] ([Converted] Users Only)

| Cohort | Avg [Engagement Metric] |
|--------|------------------------|
| **Control** | [N] [units] |
| **Treatment** | [N] [units] |
| **Lift** | **[X]x more [units]** |

**What this means:**
- [Interpretation 1]
- [Interpretation 2]
- [Connection to retention/LTV]

**Quality over quantity:** We [converted] [N] more users (+[%]), but those users are [X]x more engaged. This means the **actual impact on [business metric] is much higher than topline suggests.**

---

## Leading Indicators: Predictors of Long-Term Success

### [Leading Indicator 1]

| Cohort | Users Who [Action] | Rate |
|--------|--------------------|------|
| **Control** | [N] | [%] |
| **Treatment** | [N] | [%] |
| **Lift** | +[N] | **[X]x higher** |

**Calculation shown:**
- Control: [N] / [N] = [decimal] = [%]
- Treatment: [N] / [N] = [decimal] = [%]
- Multiplier: [%] / [%] = [X]x

**Why this matters:**
- [Historical correlation with retention/LTV]
- [What behavior this indicates]
- [Prediction about long-term value]

### [Leading Indicator 2]

| Cohort | Users Who [Action] | Rate |
|--------|--------------------|------|
| **Control** | [N] | [%] |
| **Treatment** | [N] | [%] |
| **Lift** | +[N] | **[X]x higher** |

**Why this matters:**
- [Connection to viral growth/retention/expansion]
- [What this predicts]

**These are [strong/weak] signals:** [Interpretation of what leading indicators mean for feature success]

---

## Updated Business Impact

### Original Projection vs Actual Results

| Metric | Original Projection | Actual Result | Variance |
|--------|---------------------|---------------|----------|
| **[Metric] lift (overall)** | +[N]pp | +[N]pp | [%] of target |
| **[Metric] lift ([segment])** | +[N]pp | +[N]pp | [%] of target |
| **Quality ([metric])** | Not modeled | +[N]pp | [Upside/downside] |
| **Engagement ([metric])** | Not modeled | [X]x higher | [Upside/downside] |

**Key insight:** [What we got right vs wrong in projection]

### Revised ROI ([If Segmenting Rollout])

**Assumptions:**
- Ship to [segment] only ([%] of all [users])
- [N] monthly [users] × [%] = [N] [segment] [users]
- [%] see [feature] = [N] affected users
- [Metric] lift: +[N]pp (validated by experiment)
- **Quality multiplier:** [Explanation of quality benefit and LTV impact]

**Incremental [converted] users:**
- Current: [N] × [%] = [N] [converted]
- Projected: [N] × [%] = [N] [converted]
- **Incremental: +[N] [converted] users/month**

**Adjusted LTV (accounting for [quality benefit]):**
- Base LTV: $[amount]
- Quality multiplier: [X]x ([reason])
- **Adjusted LTV: $[amount] per [converted] user**

**Revenue Impact:**
- Monthly: [N] users × $[ARPU] × [%] conversion = $[amount] MRR
- Annual: **$[amount] ARR**
- 3-year value: [N] × 12 months × $[LTV] = **$[amount]**

**ROI:**
- Year 1: $[revenue] / $[cost] = [X]x
- 3-year LTV: $[value] / $[cost] = **[X]x ROI**

**Payback period:** ~[N] months ([N] years)

---

## Decision: Ship or Kill?

### Arguments FOR Shipping

✅ **[Argument 1]:** [Evidence from data]
✅ **[Argument 2]:** [Evidence from data]
✅ **[Argument 3]:** [Evidence from data]
✅ **[Argument 4]:** [Evidence from data]

### Arguments AGAINST Shipping

❌ **[Concern 1]:** [Evidence or risk]
❌ **[Concern 2]:** [Evidence or risk]
❌ **[Concern 3]:** [Evidence or risk]

---

## Recommendation

**[SHIP TO 100% / SHIP TO SEGMENT / ITERATE / KILL]**
**[If segmenting: for SEGMENT X, EXCLUDE SEGMENT Y]**
**[If iterating: BUILD VERSION 2 WITH CHANGES]**

### Rationale

**[Primary reason for decision]:**
- [Supporting evidence 1]
- [Supporting evidence 2]

**[Secondary reason]:**
- [Supporting evidence]

**By [segmenting/iterating/shipping]:**
- [Benefit 1]
- [Benefit 2]
- [What this enables]

### Conditions for Shipping

[If shipping:]
1. **[Condition 1]:** [Implementation requirement]
2. **[Condition 2]:** [Monitoring requirement]
3. **[Condition 3]:** [Success criteria]

### Kill Criteria

[If shipping, define when to roll back:]
- If [metric] drops below [threshold] → [action]
- If [quality metric] shows [negative signal] → [action]
- If [cost/maintenance] exceeds [threshold] → [action]

### Next Steps

**[Timeframe]:** [Action]
**[Timeframe]:** [Action]
**[Timeframe]:** [Action]
**[Timeframe]:** [Action]

---

## Key Lessons from This Experiment

**1. [Lesson 1]**
- [What happened]
- [What this teaches]
- [How to apply this learning]

**2. [Lesson 2]**
- [What happened]
- [What this teaches]

**3. [Lesson 3]**
- [What happened]
- [What this teaches]

---

**Bottom Line:** [1-2 sentence summary of decision and key insight]
```

---

## Instructions for Using This Template

### Step 1: Calculate Topline Metrics

**Read the experiment data and calculate:**

```bash
# Control group
control_total = count of users in control
control_converted = count where primary_metric == True
control_rate = control_converted / control_total

# Treatment group
treatment_total = count of users in treatment
treatment_converted = count where primary_metric == True
treatment_rate = treatment_converted / treatment_total

# Lift
absolute_lift = treatment_rate - control_rate (in percentage points)
relative_lift = (treatment_rate - control_rate) / control_rate * 100
```

**Statistical significance:**
- Use chi-square test or z-test for proportions
- p < 0.05 = statistically significant
- p < 0.01 = highly significant
- p > 0.05 = not significant (could be random chance)

### Step 2: Segment by Key Attributes

**Always segment by:**
- **Customer segment** (small business, mid-market, enterprise)
- **User role** (if different roles have different needs)
- **Behavior** (power users vs casual, activated vs not)
- **Geography** (if international)

**For each segment:**
1. Filter data to segment only
2. Calculate control vs treatment rates
3. Calculate lift
4. Check statistical significance

**Look for:**
- Segments with very high lift (feature is perfect fit)
- Segments with flat/negative lift (feature doesn't work)
- Difference in magnitude across segments

### Step 3: Analyze Quality Metrics

**Beyond "did they convert?", ask "was it high quality?"**

**Common quality metrics:**
- **Retention:** Did converted users come back? (Day 7, Week 1, Day 30)
- **Engagement:** How much did they use the product? (sessions, actions, time)
- **Completion:** Did they finish the workflow? (not just start)
- **Satisfaction:** Did they rate it positively? (NPS, CSAT if collected)

**Filter to converted users only, then calculate:**
- What % in each cohort showed high-quality behavior?
- What's the average engagement level?
- How much more/less engaged is treatment?

### Step 4: Check Leading Indicators

**Leading indicators predict future success:**

**Common leading indicators:**
- **Feature adoption:** Did they use related features? (shows value)
- **Invites:** Did they invite teammates? (predicts retention)
- **Expansion:** Did they upgrade plan/add seats? (revenue signal)
- **Content creation:** Did they create more [tasks/docs/projects]? (investment)
- **Return visits:** Did they come back within 24 hours? (habit formation)

**Calculate rates for treatment vs control:**
- Even if primary metric lift is modest, strong leading indicators = good long-term bet
- Weak leading indicators = conversion might be low quality

### Step 5: Update Financial Model

**If segment performance differs from overall:**

**Recalculate impact based on segment:**
1. What % of total users are in the winning segment?
2. What's the actual lift for that segment? (not overall)
3. What's the quality multiplier? (if retention/engagement improved)
4. Recalculate: users affected, revenue, ROI, payback

**Adjust for quality:**
- If treatment users are 2x more engaged → LTV might be 1.5x higher
- If retention improved 20pp → extend lifetime by X months
- Multiply base LTV by quality multiplier

### Step 6: Make the Decision

**Use this decision tree:**

```
Is topline lift significant and positive?
├─ YES → Check segments
│   ├─ All segments positive? → SHIP TO 100%
│   ├─ Some segments positive, some flat? → SHIP TO POSITIVE SEGMENTS
│   └─ Mixed (positive + negative)? → SHIP TO POSITIVE, EXCLUDE NEGATIVE
│
└─ NO (flat or negative) → Check segments anyway
    ├─ Target segment strongly positive? → SHIP TO THAT SEGMENT
    └─ All segments flat/negative? → KILL or ITERATE
```

**Quality and leading indicators can change the decision:**
- Modest topline lift + exceptional quality = SHIP
- Strong topline lift + weak quality = ITERATE
- Flat topline + strong leading indicators = SHIP (bet on long-term)

---

## Example Analysis (TaskFlow Guided Onboarding)

### Topline Calculation

```
Control: 1,826 / 4,000 = 0.4565 = 45.65%
Treatment: 2,084 / 4,000 = 0.5210 = 52.10%
Lift: 52.10% - 45.65% = +6.45pp (14.1% relative)
p-value: <0.001 (highly significant)
```

**Initial reaction:** Disappointing - we projected +13pp, got +6.5pp

### Segmentation Reveals the Truth

```
Small teams (5-20):
  Control: 1,094 / 2,400 = 45.6%
  Treatment: 1,352 / 2,400 = 56.3%
  Lift: +10.8pp ← Close to our +13pp projection!

Enterprise (100+):
  Control: 186 / 400 = 46.5%
  Treatment: 181 / 400 = 45.2%
  Lift: -1.3pp ← Actually hurt them!
```

**New understanding:** Feature works great for target market, wrong for enterprise

### Quality Metrics Show Real Value

```
Week 1 Retention (activated users):
  Control: 1,294 / 1,826 = 70.9%
  Treatment: 1,986 / 2,084 = 95.3%
  Lift: +24.4pp ← Massive quality improvement!

Tasks completed:
  Control: 2.6 avg
  Treatment: 6.4 avg
  Lift: 2.4x ← Way more engaged!
```

**Insight:** Not just more activations, but BETTER activations

### Leading Indicators Predict Success

```
Template usage:
  Control: 459 / 4,000 = 11.5%
  Treatment: 1,416 / 4,000 = 35.4%
  Lift: 3.1x ← Lasting behavior change

Invite rate:
  Control: 489 / 4,000 = 12.2%
  Treatment: 1,384 / 4,000 = 34.6%
  Lift: 2.8x ← Viral growth signal
```

**Decision:** Ship to small teams, exclude enterprise, despite modest topline

---

## Common Analysis Mistakes

❌ **Stopping at topline** - Always segment before deciding
❌ **Ignoring quality** - High-quality conversions worth more than quantity
❌ **Missing leading indicators** - They predict long-term success
❌ **No statistical testing** - Could be random noise, not real effect
❌ **Comparing wrong groups** - Make sure control and treatment are truly randomized
❌ **Cherry-picking metrics** - Look at full picture, not just wins
❌ **Ignoring negative segments** - If you hurt some users, need to address it

---

## Output Checklist

Before making ship/kill decision, ensure you have:

- [ ] Topline metrics calculated with statistical significance
- [ ] Segmentation by at least one key customer attribute
- [ ] Quality metrics analyzed (retention, engagement, etc.)
- [ ] Leading indicators checked (what predicts future success?)
- [ ] Updated financial model (if segmenting rollout)
- [ ] Clear arguments for AND against shipping
- [ ] Specific recommendation with rationale
- [ ] Kill criteria defined (when to roll back)
- [ ] Next steps with timeline

---

**This template helps you go from raw experiment data → segmented insights → quality assessment → confident ship/kill decision.**
