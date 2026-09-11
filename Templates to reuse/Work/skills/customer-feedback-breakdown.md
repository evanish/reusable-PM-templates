---
name: customer-feedback-breakdown
description: Pulls #customer-feedback Slack channel history for the latest period, categorizes bug response findings into 6 buckets, and appends a new period column to the breakdown markdown file. Use when asked to update the customer feedback breakdown, run the weekly feedback analysis, or calculate false positive rate from customer feedback.
---

# Customer Feedback Breakdown

Reads #customer-feedback (Slack channel C0ANANF48D7), categorizes each customer bug response into one of 6 buckets, deduplicates, and appends a new period to the report.

**Output file:** `/Users/jason-ito/Ito AI Cursor/PM/data/customer-feedback-breakdown-all-periods.md`

## Step 1: Determine the date range

Read the output file to find the end date of the most recent period (the latest P-column header). The new period starts from that cutoff and ends at today.

Convert both dates to Unix timestamps (CDT = UTC-5).

## Step 2: Pull Slack history

Use `plugin-slack-slack` > `slack_read_channel` with:
- `channel_id`: `C0ANANF48D7`
- `oldest`: Unix timestamp of period start
- `latest`: Unix timestamp of now
- `limit`: 100
- `response_format`: `detailed`

Paginate with `cursor` until `pagination_info` says no more messages.

## Step 3: Filter to bot messages only

Exclude:
- Youform onboarding survey submissions (":tada: You received a new submission")
- Youform GitLab interest form submissions
- Reaction-only events (inline comment reactions with no comment text)
- Pure @itoqa rerun requests that contain no feedback on the finding

Keep: all "New customer PR comment feedback" and "New customer PR thread interaction" messages from bot B0BAWHR4B8F, plus @itoqa master comments that include substantive feedback.

## Step 4: Deduplicate

A comment + resolve on the same PR by the same person within ~5 seconds = one finding (count as the comment's category, not the bare resolve).

Multiple bare resolves by the same person on the same PR within ~2 seconds = one finding.

Bare resolves separated by more than 5 seconds on the same PR = separate findings.

## Step 5: Categorize each finding

Apply exactly one category:

| Category | Signals |
|---|---|
| **Fixed (Confirmed + Resolved)** | "Fixed in [commit]", "Good catch", "Addressed in [commit]", "this was a real bug" |
| **Won't Fix / Intentional** | "intentional", "by design", "won't fix", "working as designed", dismissals with no technical refutation |
| **False Positive** | "not a bug", "never shipped", "not reachable", "this can't trigger", "ran on wrong commit/code", "edge case that can't occur", "Ito reset its narrative" |
| **Resolved, Unclear Why** | Bare resolve with no comment, or "can't repro anymore" without a stated fix |
| **Took Seriously / Investigating** | "fair callout", "good catch" without a committed fix, "might want a fix", consulting another tool |
| **Filed Ticket** | Explicit mention of filing a Jira/Linear/GitHub issue |

**Tie-break rule:** "False Positive" beats "Won't Fix" when the customer provides a technical reason the finding is factually wrong (the code path is unreachable, the value never existed, the behavior is correct). "Won't Fix" applies when the issue is real but the customer declines to address it.

## Step 6: Count and calculate

Tally counts per category. Compute:
- Total findings
- Days in period (from cutoff to today)
- Findings/day
- Each category as % of total

## Step 7: Update the output file

Append a new column (P4, P5, etc.) to each table in the output file:
- Raw Counts table
- Percentage by Period table
- Period-over-Period Change table (delta vs. prior period in pp)
- Volume Trend table

Update the Key Observations section to reflect the new period's notable shifts.

Do not rewrite prior period data. Only add the new column.

## Key context

- The Slack bot (B0BAWHR4B8F) posts one message per customer action. A "comment" and "resolve" for the same finding on the same PR at the same timestamp = one action, not two findings.
- Truemedicine, DoltHub, and trymedallion are the highest-volume customers. DoltHub often batch-resolves many findings in rapid succession.
- "False Positive" rate is the most strategically important metric for Barron and the eng team. Highlight it prominently.
- Prior period cutoffs: P1 ended Jul 1 ~12:00 PM CDT, P2 ended Jul 7 ~12:45 PM CDT, P3 ended Jul 15 ~3:30 PM CDT.
