# TEMPLATE: Survey Analysis Guide

**Purpose:** Analyze user survey data to understand WHY users are experiencing problems, validate hypotheses, and identify solutions.

**When to use:** After you've identified a quantitative problem (e.g., funnel drop-off, low feature adoption) and need qualitative depth.

---

## Template Structure

```markdown
# Survey Analysis: [Problem Name]

**Analysis Date:** [Date]
**Data Source:** [CSV file name or survey tool]
**Context:** [What quantitative problem led to this survey? Include metric]

---

## Executive Summary

**Finding:** [1-2 sentence summary of top insight]

**Target Segment:** [Which user segment experiences this problem most?]

**Solution Validation:** [Do users explicitly request a solution? What % want it?]

**Business Impact:** [How does this connect to retention/revenue/growth?]

---

## Thematic Breakdown ([N] responses)

### THEME 1: [Name] ([X]% - [N] users)

**Specific phrases indicating this theme:**
- "[Exact user quote 1]" ([N] users)
- "[Exact user quote 2]" ([N] users)
- "[Exact user quote 3]" ([N] users)

**Key insight:** [What this theme reveals about user behavior/needs]

---

### THEME 2: [Name] ([X]% - [N] users)

[Repeat structure]

---

### THEME 3: [Name] ([X]% - [N] users)

[Repeat structure]

---

## Segmentation by [Key Attribute]

| [Segment Name] | Total Responses | Theme 1 | Theme 2 | Theme 3 |
|----------------|-----------------|---------|---------|---------|
| [Segment A] | [N] ([%]) | [N] ([%]) | [N] ([%]) | [N] ([%]) |
| [Segment B] | [N] ([%]) | [N] ([%]) | [N] ([%]) | [N] ([%]) |
| [Segment C] | [N] ([%]) | [N] ([%]) | [N] ([%]) | [N] ([%]) |

**Key findings:**
- [Segment insight 1]
- [Segment insight 2]

**Strategic implication:** [Who needs this solution most?]

---

## Solution Validation: Cross-Tab Analysis

### [Confusion Theme] → [Feature Request]

| [Theme Name] | Top Feature Request | % Requesting |
|--------------|---------------------|--------------|
| [Theme 1] | "[Solution name]" | [%] |
| [Theme 2] | "[Solution name]" | [%] |
| [Theme 3] | "[Solution name]" | [%] |

**Insight:** [Do multiple themes point to same solution? What does this validate?]

---

## Business Impact: [Key Metric] by [Theme]

### [Metric Name] by Confusion Type

| [Theme Name] | [Metric: Good] | [Metric: Neutral] | [Metric: Bad] |
|--------------|----------------|-------------------|---------------|
| [Theme 1] | [%] | [%] | [%] |
| [Theme 2] | [%] | [%] | [%] |
| [Theme 3] | [%] | [%] | [%] |

**Insight:** [How does this problem correlate with business metrics like NPS, retention, conversion?]

---

## Qualitative Insights: User Pain in Their Words

**Most Common Phrases (Verbatim):**

1. **"[Exact quote]"** ([N] mentions)
2. **"[Exact quote]"** ([N] mentions)
3. **"[Exact quote]"** ([N] mentions)
4. **"[Exact quote]"** ([N] mentions)
5. **"[Exact quote]"** ([N] mentions)

**Pattern:** [What do these quotes reveal? What solution are users implicitly requesting?]

---

## Recommendations

**Primary Solution:** [Solution name based on data]
- [What it is]
- [Why it addresses the problem]

**Why This Works:**
- ✅ [Addresses Theme 1 (X%): explanation]
- ✅ [Addresses Theme 2 (X%): explanation]
- ✅ [Addresses Theme 3 (X%): explanation]
- ✅ [Total addressable: X% of confused users]

**Target Segment:**
- [Which segment to build for first and why]

**Expected Impact:**
- [Predicted improvement in key metric]
- [Secondary benefits]

---

## Next Steps

1. ✅ **Discovery Complete** - We've identified the problem with data
2. **Impact Estimation** - Build ROI model to justify investment
3. **Design & Build** - Create solution
4. **A/B Test** - Measure impact vs control group
5. **Iterate** - Refine based on results

---

**Bottom Line:** [1-2 sentence summary tying themes to solution and expected impact]
```

---

## Instructions for Using This Template

### Step 1: Read the Survey Data

```
Read the CSV file containing survey responses. Look for fields like:
- Open-ended text responses (biggest_confusion, feedback, pain_point)
- Categorical data (company_size, user_role, industry)
- Ratings or sentiment (satisfaction_score, would_recommend)
```

### Step 2: Identify Themes

**Use this process:**

1. **Read 50-100 responses** to get a sense of common patterns
2. **Group similar responses** into 3-5 major themes
3. **Count exact phrase frequency** (e.g., how many said "need examples"?)
4. **Calculate theme prevalence** (% of total responses)

**Common themes to look for:**
- Lack of understanding ("didn't know how", "unclear what to do")
- Missing features ("wish there was", "need a way to")
- Friction/complexity ("too many steps", "overwhelming")
- Performance/bugs ("slow", "crashes", "doesn't work")
- Comparison to competitors ("X has this feature", "like Y does it")

### Step 3: Segment the Data

**Key segments to analyze:**
- **Company size** (small vs enterprise have different needs)
- **User role** (PM vs Engineer vs Designer)
- **Tenure** (new users vs experienced)
- **Behavior** (activated vs churned, power users vs casual)

**For each segment, calculate:**
- Total responses from that segment
- % experiencing each theme
- Whether this segment over-indexes on specific themes

### Step 4: Cross-Reference with Feature Requests

**If your survey asks "What feature would help?":**
- Map confusion themes to requested solutions
- Calculate what % of each theme requests each solution
- Identify if multiple themes converge on same solution (strong validation)

### Step 5: Connect to Business Metrics

**If you have data like NPS, retention, conversion:**
- Segment by theme (users who mentioned Theme 1 vs Theme 2)
- Calculate business metric for each theme
- Show correlation (e.g., "users confused about X have 20% lower NPS")

### Step 6: Pull Representative Quotes

**Select quotes that:**
- Represent the most common themes
- Use specific, vivid language
- Show emotional impact ("frustrated", "confused", "love")
- Come from your target segment

**Quote format:**
- Use verbatim text (don't paraphrase)
- Include frequency count if many users said similar things
- Attribute to segment if relevant (e.g., "Small team founder")

---

## Example (Using TaskFlow Data)

### Theme Identification Example

**Raw responses mentioning "examples":**
- "Needed examples to get started" (58 users)
- "Would help to see what a good task looks like" (60 users)
- "Show me a sample project" (59 users)
- "Wish there were templates or samples" (43 users)
- "Examples would have been helpful" (62 users)

**Grouped into theme:**
- **THEME: Need Examples/Templates** (60.4% - 483 users)

### Segmentation Example

**Small teams (5-20 people):**
- Total responses: 512 (64% of survey)
- Need examples: 318 (62% of small team responses)
- **Insight:** Small teams over-index on this problem

**Enterprise (100+ people):**
- Total responses: 72 (9% of survey)
- Need examples: 42 (58% of enterprise responses)
- **Insight:** Enterprise has this problem slightly less

### Cross-Tab Example

**Users who said "Stared at empty project" (Theme: Blank Canvas):**
- 89% requested "Sample projects or templates"
- **Validation:** This theme and solution are tightly connected

---

## Common Pitfalls to Avoid

❌ **Cherry-picking quotes** - Don't only show quotes that support your hypothesis
❌ **Ignoring segments** - Small teams and enterprise often have different needs
❌ **Vague themes** - "Confused" is not a theme; "Don't know what tasks to create" is
❌ **No quantification** - Always count how many users mentioned each theme
❌ **Missing business tie-in** - Connect themes to retention, NPS, conversion, etc.

---

## Output Checklist

Before finalizing your survey analysis, ensure you have:

- [ ] Clear theme names with % and user counts
- [ ] Verbatim quotes showing frequency
- [ ] Segmentation by at least one key attribute (company size, role, etc.)
- [ ] Cross-tab showing theme → solution requests
- [ ] Business metric impact (NPS, retention, conversion by theme)
- [ ] Specific, actionable recommendation based on data
- [ ] Next steps clearly stated

---

**This template helps you go from raw survey data → validated problem → specific solution in a structured, data-backed way.**
