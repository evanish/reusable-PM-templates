# TEMPLATE: Survey Design

**Purpose:** Design short, high-completion surveys that yield actionable signal without burning through respondent goodwill.

**When to use:** Before sending any customer or user survey. Covers everything from product-market fit measurement to feature feedback to ROI benchmarking. Use this template to design the survey, then use `TEMPLATE-survey-analysis.md` to analyze the results.

**Framework sources:** ProfitWell analysis of 5M+ SaaS customer surveys (Patrick Campbell) and Sean Ellis's product-market fit methodology.

---

## Template Structure

```markdown
# Survey: [Topic or Goal]

**Goal:** [One sentence: what decision or insight does this survey generate?]
**Audience:** [Who is receiving this, and roughly how many?]
**Delivery:** [Email / in-app / link - and who sends it?]
**Target completion time:** Under 60 seconds

---

## Invite Copy

**Subject:** [Product or Company] - [X seconds]
Example: "Help shape [Product] - 60 seconds"

**Body:**
[2-3 sentences max. State the exact time it takes. Frame it as a two-way
conversation, not data collection. "Help us" not "tell us about your experience."]

Example:
"We are building [product] for teams like yours and want to make sure we're
solving the right problems. Three quick questions - takes about 60 seconds.
No login required."

---

## Questions

**Q1: [Primary signal question]**
Type: Multiple choice (forced - no N/A)
> [Question text]
> - [Option A]
> - [Option B]
> - [Option C]

**Q2: [Follow-up "why" - only include if Q1 uses the "choice + why" pattern]**
Type: Open-ended (short - one sentence prompt)
> "What is the main reason you chose that answer?"

**Q3: [Secondary signal question]**
Type: Multiple choice (forced)
> [Question text]
> - [Option A]
> - [Option B]
> - [Option C]
> - [Option D]

**Q4: [Optional tertiary question]**
Type: Multiple choice (forced)
> [Question text]
> - [Option A]
> - [Option B]
> - [Option C]

---

## What You Will Do With the Results

- Q1: [Signal or metric you will pull from this question]
- Q2: [How this open-ended data will be used]
- Q3: [Signal or metric you will pull from this question]
- Q4: [Signal or metric you will pull from this question]
- [Decision this data will inform]
```

---

## Core Rules (ProfitWell / Patrick Campbell)

Derived from analysis of 5M+ SaaS customer development surveys. Apply all of these before finalizing any survey.

### 1. Under 1 minute

Completion rate drops sharply past 4 minutes. Surveys under a minute can also be sent much more frequently. Design for 60 seconds or less.

### 2. Max 4-5 questions

Every question you add reduces the quality of all other responses. Stop at 4. Do not add a question because a stakeholder requested it unless you can prove the data cannot be found in your own systems.

### 3. No lazy questions

Never ask for information you already have: email address, plan type, usage frequency, company size, role. Only ask what you cannot pull from your own database.

### 4. Singular focused goal

Pick one thing the survey is designed to learn. Avoid survey creep (adding questions from other teams or other goals). Treat every additional question as a tax on the quality of every other answer.

### 5. Force decisions, not ratings

Avoid 1-10 scales. They produce data where everything clusters in the middle and you cannot distinguish strong signal from weak. Use multiple choice with clear, distinct options. Force respondents to pick.

### 6. Set expectations in the invite

Include the exact time commitment in the subject line. This is one of the highest-leverage changes you can make. Example: "Help shape [Company] - 60 seconds"

### 7. Frame it as a two-way conversation

The best response rates come from users who feel like they are shaping something real, not just feeding a data machine. Use "help us" framing, not "give us your feedback" framing.

---

## The Sean Ellis PMF Survey

Use this when you need to measure product-market fit or benchmark how essential a product is. It is the most reliable short-form PMF signal available.

### The two questions

**Q1 (forced choice - always first):**
> "How would you feel if you could no longer use [product]?"
> - Very disappointed
> - Somewhat disappointed
> - Not disappointed

Do not add a fourth "N/A" option when surveying active users. Force the decision.

**Q2 (open-ended, immediately after Q1):**
> "What is the main reason you chose that answer?"

Position this directly after Q1. It works for every response type:

| Response | What the open-ended reveals |
|---|---|
| Very disappointed | Exactly what value the product delivers. These are your best quotes and your core value proposition. |
| Somewhat disappointed | What is missing or not landing. Product roadmap signal. |
| Not disappointed | Where the product has not clicked. Onboarding or ICP fit signal. |

### Interpreting PMF results

- **40%+ "very disappointed"**: Strong PMF. Superhuman used this threshold publicly as their benchmark.
- **25-40%**: Directionally positive. Worth investing to improve.
- **Under 25%**: PMF not established. The qualitative answers from the lower-disappointment groups are your most important data.

**Always segment the "very disappointed" group separately.** Their open-ended answers define your best-fit customer and contain the language to use in positioning and marketing.

### Full PMF survey example

```
Subject: "Help shape [Product] - 60 seconds"

Body: "Quick question about your experience with [Product]. Takes under a minute.
Your answers will directly shape what we build next."

Q1: How would you feel if you could no longer use [product]?
- Very disappointed
- Somewhat disappointed
- Not disappointed

Q2: What is the main reason you chose that answer?
[Open text]

Q3: [Optional - one additional multiple choice question for your specific goal]
```

---

## Pre-Send Checklist

- [ ] Can this be completed in under 60 seconds?
- [ ] Are there 4 or fewer questions?
- [ ] Does every question ask something that cannot be answered from existing data?
- [ ] Are rating scales replaced with forced-choice options?
- [ ] Is there at most one open-ended (or one "choice + why" pair)?
- [ ] Does the invite subject line state the exact time commitment?
- [ ] Is the framing "help us shape this" rather than "give us your feedback"?
- [ ] Is there a plan for what each question's data will be used for before the survey goes out?

---

**Bottom Line:** A survey under a minute with 3-4 precisely chosen questions will outperform a 15-question survey on both completion rate and quality of signal. Every time.
