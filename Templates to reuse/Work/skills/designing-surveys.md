---
name: designing-surveys
description: Design short, high-completion customer and user surveys following ProfitWell best practices and the Sean Ellis PMF framework. Use when asked to create a survey, draft survey questions, evaluate survey quality, or measure product-market fit.
disable-model-invocation: true
---

# Designing Surveys

Based on ProfitWell's analysis of 5M+ SaaS customer development surveys (Patrick Campbell) and Sean Ellis's product-market fit survey methodology.

## Core Rules

1. **Keep it under 1 minute.** Completion rate drops sharply after 4 minutes. Under-a-minute surveys can also be sent far more frequently.
2. **Max 4-5 questions.** Every question you add reduces quality of all other answers.
3. **No lazy questions.** Never ask for information you already have (email, plan type, usage frequency, company size). Only ask what you cannot get from your own data.
4. **Singular focused goal.** Pick one thing the survey is for. Survey creep kills signal.
5. **Force decisions, not ratings.** Avoid 1-10 scales. They produce data where everything clusters in the middle and you learn nothing. Use multiple choice with clear, distinct options instead.
6. **Set expectations in the invite.** State the exact time required in the subject line. Example: "Help shape [Company] - 60 seconds". Respondents who know it is short are more likely to start and finish.
7. **Evoke community.** Frame the survey as a two-way conversation, not data extraction. Respondents who feel like they are shaping something real respond at higher rates.

## Question Design

### Prefer forced-choice over open-ended

Multiple choice is faster to answer and easier to aggregate. Reserve open-ended for one targeted follow-up per survey, at most.

### The "choice plus why" pattern

One multiple-choice question followed immediately by "What is the main reason you chose that?" is an acceptable open-ended. It works because the respondent already knows their answer and just has to explain it. Do not use this pattern more than once in a single survey.

### Avoid these framings

- Questions that imply the product is not working ("What would make this essential?" implies it is not essential)
- Negative anchors early in the survey ("What is the worst...")
- Anything that could embarrass or frustrate a satisfied user

## The Sean Ellis PMF Survey

The canonical product-market fit measurement tool. Use when you need to benchmark how indispensable a product is.

### The two questions

**Q1 (forced choice):**
> "How would you feel if you could no longer use [product]?"
> - Very disappointed
> - Somewhat disappointed
> - Not disappointed

Do not add a fourth "N/A" option if you are surveying active users. Force the decision.

**Q2 (open-ended, immediately after Q1):**
> "What is the main reason you chose that answer?"

This is the signal-rich follow-up. It works for every response type:
- "Very disappointed" respondents articulate exactly what value they get. These are your best quotes and your core value proposition.
- "Somewhat disappointed" respondents identify what is missing or not landing.
- "Not disappointed" respondents reveal where the product has not clicked, which is an adoption or onboarding signal.

### Interpreting results

- **40%+ "very disappointed"**: Strong PMF signal. Superhuman used this threshold publicly as their benchmark.
- **25-40%**: Directionally positive. Worth investing to push higher.
- **Under 25%**: PMF is not established. Qualitative answers from the "somewhat" and "not disappointed" groups are your most important data.

Segment the "very disappointed" responses separately. They define your best-fit customer and contain the language to use in positioning and marketing.

## Survey Structure Template

```
Invite copy: State who you are, and the ask. Emphasize how short and fast the sruvey is like "Three quick questions. Takes about 60 seconds. No login required."

## Checklist Before Sending

- [ ] Can this be completed in under 60 seconds?
- [ ] Are there 4 or fewer questions?
- [ ] Does every question ask something you cannot already know from your own data?
- [ ] Are rating scales replaced with forced-choice options?
- [ ] Is there at most one open-ended (or one choice+why pair)?
- [ ] Does the invite copy state the exact time commitment?
- [ ] Is the framing "help us shape this" rather than "give us feedback"?
