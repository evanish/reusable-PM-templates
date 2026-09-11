# GitHub Issue Template, August 2026

This is the canonical template for Ito Web and QA Ito issues. Earlier versions are retained in `archive/` for reference only.

## How we shape tickets together

- **Project**: If not specified, ask: "Is this for Ito Web or QA Ito?"
- **Missing fields**: If a required section is not mentioned, ask a brief question or insert a `[TODO]` note in the final ticket.
- **Placeholders**: `[TODO]` bullets are acceptable for designs, links, metrics, and unresolved product decisions.
- **Formatting**: Use bold labels, bullets, and checkboxes exactly as below so issues paste cleanly into GitHub.
- **Avoid redundancy**: Do not restate the same fact across Summary, Context, Out of scope, and Acceptance criteria. Say it once in the section where it fits best.
- **No local-file-only links**: Do not cite a local workspace file as a source. Search Notion for an equivalent page first. If none exists, ask Jason where he would like a Notion file created, then link to that notion file in the ticket. Put a placeholder in your draft so you don't forget, then replace the placeholder with the notion link.
- **Approved content**: Once Jason says a draft is ready to create, copy its saved title and body verbatim to GitHub. Do not make editorial or formatting changes during creation.

### Technical and analytics rigor

- **Verify before suggesting**: For GitHub permissions, external integrations, or current product behavior, check official documentation and relevant Ito code before drafting. State the verified constraint and the decision the engineer must make.
- **Separate acquisition from product behavior**: State whether requested behavior applies to every eligible user or only a defined segment. Do not treat an acquisition source as a separate product flow without evidence.
- **Make open decisions concrete**: Under `To Discuss with Humans` or the equivalent, name the decision, constraints, and customer-impacting edge case. Avoid generic directions such as "research permissions."
- **Analytics starts with existing taxonomy**: Inspect the active PostHog event schema and relevant capture code first. Reuse an existing event when it represents the action or outcome.
- **Create an event only for a genuinely new outcome**: When needed, specify the exact event name, client or server origin, trigger point, `distinct_id`, company-group association, properties, and idempotency behavior.
- **Make tracking acceptance criteria testable**: State which exact existing events and properties must emit, or which new event must emit and when.
- **Epic structure**: When a parent issue has child issues, create the parent first, then create children from approved drafts and link them as GitHub sub-issues.

### When the user gives an idea or bug in plain language

- Decide whether it is a **bug** or **feature / improvement**.
- Ask only for missing critical pieces: project, severity, customers, context, acceptance criteria, and measuring success.
- **Reach discussion for proactive customer communication**: When a change would make Ito proactively post, comment, notify, email, or react in a customer-facing surface, ask before drafting:
  1. Who should receive it?
  2. Who should not receive it? What existing filters (like silent mode, read-only, etc) should apply here?
  3. How often should a person, organization, PR, or other unit see it?
  Do not infer the answers. If Jason does not yet have an answer, add them under `To Discuss with Humans` and ask Jason in the agent chat window.


- **Check for duplicates** before drafting.
- Draft the ticket using the appropriate template.
- Show the full markdown and create the GitHub issue only after Jason confirms it is ready.
- After creation, return the issue URL and log the ticket in the daily file below.

### Duplicate check

Before drafting, search open and closed issues using two or three distinct keyword phrases.

```bash
gh issue list --search "<keywords>" --state open --limit 10
gh issue list --search "<keywords>" --state closed --limit 5
```

If a likely duplicate is found:

1. Read it: `gh issue view <number>`.
2. Ask Jason whether to add new information to it, create a different issue, or skip creating an issue.
3. If adding a comment, draft only the new information and post it only after Jason confirms.

### Daily bugs-and-issues log

- For each day issues are created, maintain `bugs-issues-MM-DD-YYYY.md`.
- Append each shaped ticket.
- Use `Status: Draft` while shaping it.
- After GitHub creation, use:

  ```text
  Status: Issue successfully created
  URL: https://github.com/<owner>/<repo>/issues/<number>
  ```

## Bug template

**Title**  
Short, specific, action-oriented. Keep under 72 characters.

**Type**: bug  
**Severity**: critical | high | medium | minor

**Customers affected**

- List specific customers or organizations if known, or "unknown / broad".

**Summary**  
One or two sentences on what is broken and why it matters.

**Steps to reproduce**

1. Step one, including environment, URL, repository, or branch when relevant.
2. Step two.
3. Step three.
4. Observed result.

**Attachments / references**

- [Link to logs]
- [Link to screenshot / recording]
- [Link to Slack thread or related issues / PRs]

## Feature / improvement template

**Title**  
Short, specific outcome. Keep under 72 characters.

**Type**: feature | experiment | iteration

**Summary**  
One to three sentences on what changes and why it matters.

**Context**

*For humans*:

- The concise "why this, why now" when it is not obvious from the summary.
- The bare-minimum facts a reviewer needs to build the right thing.
- For proactive customer communication, record:
  - Who receives it.
  - Who must not receive it.
  - How often it appears.

*To Discuss with Humans*:

- The concrete product decisions a human must make before implementation. State the decision, constraints, and customer-impacting edge case.
- Technical tradeoffs or functionality questions to discuss with the engineer working on the ticket

- Use `[TODO: discuss]` for unresolved decisions. Do not infer them.

*For AI*:

- Prior attempts, related or duplicate tickets, and links to issues, PRs, Slack threads, designs, and customer evidence.
- Non-obvious reasoning behind scope calls, including why something is in or explicitly out.
- If a dependency may exist, scan active GitHub issues and suggest the three most likely dependencies for Jason to confirm. Include issue titles and links.

**Out of scope**

Guardrails only: adjacent or tempting work we are deliberately not doing. Do not restate in-scope work here.

- [Feature or behavior we will not build, as a short bullet.]

**Acceptance criteria**

- [ ] When X, Y happens.
- [ ] Edge case A behaves as expected.
- [ ] UX, API, or data behavior matches the design, if applicable.
- [ ] Tracking behavior is explicit and testable, if applicable.

**Measuring success**

- How we will know this worked, such as a metric, behavior change, support-ticket reduction, or qualitative feedback.
- Be honest about what is realistically measurable.

**Attachments / references**

- [Link to design / Figma]
- [Link to customer feedback thread]
- [Link to related issues / PRs]

## Lessons learned

- **Context split (2026-07-09)**: Keep `For humans` concise for a briefed reviewer. Put deeper background, prior attempts, evidence, and scope reasoning in `For AI`.
- **`To Discuss with Humans` placement (2026-08-14)**: Put unresolved product decisions directly after `For humans` and before `For AI`, so they are visible in review.
- **Reach discussion before proactive communication (2026-08-14)**: Do not infer audience or cadence. Discuss who receives a proactive message, who must not, and how often it appears.
- **No `In scope` section (2026-07-09)**: Acceptance criteria defines in-scope behavior. Keep only `Out of scope` for deliberate exclusions.
- **Redundancy check (2026-07-09)**: Before showing a draft, remove repeated facts from Summary, Context, and Out of scope.
- **No local-file-only source links (2026-07-09)**: GitHub readers cannot open Jason's local workspace files. Link a Notion equivalent or use a TODO.
- **Bullet-list Summary for multi-part work (2026-07-17)**: When a ticket does multiple things, open with one sentence and use bullets for distinct actions.
- **Inline markdown links (2026-07-17)**: Format every URL in the ticket as an inline Markdown link.
- **Sub-bullets for qualifying notes (2026-07-17)**: Put meaningful caveats under the relevant main bullet.
- **Simplified API guidance (2026-07-17)**: Do not dictate exact API paths or parameter formats in `For AI`. Link the documentation and direct engineering to confirm current details.
- **Cross-ticket references use real issue numbers (2026-07-17)**: When companion tickets are filed, replace placeholders with real GitHub issue numbers and links.
