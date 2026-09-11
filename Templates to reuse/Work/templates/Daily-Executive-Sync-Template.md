# TEMPLATE: Executive <> Product Lead Daily Sync Draft

Two steps. Stop after Step 1 and wait for product lead to say the draft is ready to push before doing Step 2.

---

## Step 1: Create the draft

### 1a: Determine the target date

The draft is for **tomorrow's meeting**, not today's.

- Mon-Thu: target = today + 1 day
- Friday: target = the following Monday
- Never create a draft for Saturday or Sunday

### 1b: Check if the file already exists

Daily sync files are organized in monthly subfolders. Look for:
`/Users/jason-ito/Ito AI Cursor/PM/planning/daily-syncs/[YYYY-MM]/[TARGET-DATE]-barron-jason-sync-draft.md`

- If it exists: stop, tell product lead, show the path.
- If it does not exist: proceed.

### 1c: Gather today's work (primary sources only)

**CRITICAL: The file dated TODAY was created YESTERDAY for this morning's meeting. It contains yesterday's work. Do not read it. Do not use it. Ignore any draft file that is open in the editor.**

Only include items with timestamps that fall on today's calendar date. If a timestamp is not today, skip it.

**Agent transcripts** (fastest, most complete): Check `/Users/jason-ito/.cursor/projects/Users-jason-ito-Ito-AI-Cursor/agent-transcripts/`. Sort by modification time, read the `[uuid].jsonl` files from today. Pull user queries to understand what work was done and what artifacts were produced.

**Granola meetings**: Use `list_meetings` with today's date. Skip any meeting executive attended. Skip standup.

**Slack**: Search `from:<@[PRODUCT_LEAD_SLACK_USER_ID]> after:[TODAY-DATE]`. Verify each message timestamp is today before including it.

**GitHub**: Review today's activity in both `heyito/ito-web` and `demox-labs/qaito`. Also review `heyito/devdocs` for help-documentation changes and `heyito/marketing` when there is marketing-site activity. Capture issues product lead filed, meaningful ticket state changes, merged or shipped work, and relevant customer-facing product, documentation, or positioning changes. Use GitHub activity to confirm status and links, not Slack alone.

**Workspace files**: Check `/Users/jason-ito/Ito AI Cursor/PM/` for files modified today. Pay attention to `tickets/billing/`, as billing and self-serve payment work is frequently relevant to executive.

### 1c.1: Prove source coverage before writing

Do not draft after checking only the most obvious artifacts. Make a short, private source checklist first:

- **Agent transcripts:** Identify every transcript whose user messages have today's timestamp. Do not rely only on the newest few files from a globally sorted listing. Capture the request, resulting artifact, and completion status for each relevant conversation.
- **Granola:** List every meeting today, remove standups and meetings executive attended, then retrieve the summary for every remaining meeting before deciding what belongs in the update. An ambiguous title, especially an API, customer, product, or strategy discussion, is not a reason to skip the meeting.
- **Slack:** Run the required `from:<@[PRODUCT_LEAD_SLACK_USER_ID]> after:[TODAY-DATE]` search. Verify returned timestamps. If it returns no results, retry with an `on:[TODAY-DATE]` date filter and a bounded date search before concluding that there were no messages. Record that Slack had no results only after those checks.
- **GitHub:** Check `heyito/ito-web`, `demox-labs/qaito`, and `heyito/devdocs` for today's issue, pull-request, and recent-commit activity. Check `heyito/marketing` when it has activity today. Record the exact issue or PR status and URL for anything that could belong in the update. Do not limit the sweep to product-engineering repositories when the day included customer-facing documentation, positioning, or marketing work.
- **Workspace:** Compare today's modified PM artifacts with the transcript and meeting checklist. Use them to confirm the artifact's exact state, not as a substitute for the primary source.

If a source is unavailable or returns nothing after the required retry, say so in the working notes. Do not silently treat an incomplete source scan as complete.

### 1d: Write the file

Create at `/Users/jason-ito/Ito AI Cursor/PM/planning/daily-syncs/[YYYY-MM]/[TARGET-DATE]-barron-jason-sync-draft.md` using this exact format:

```
# [Weekday], [Month DD, YYYY]: Executive <> Product Lead Sync Draft

Granola Notes link: *[add after meeting]*

### Check in / updates

- [bullet]

### Blockers?

-

### Biggest focus

-

### 💡 What I want to ask executive today

-
```

Leave Blockers, Biggest focus, and What I want to ask executive as a single dash. product lead fills these in himself.

**Scope boundary:** The agent owns only **Check in / updates**. Do not infer, draft, edit, or recommend content for Blockers, Biggest focus, or What I want to ask executive today, even when today's sources suggest likely content.

### Bullet rules

- **Today only.** Not this week. Not what was in standup.
- **Use edited syncs only as voice calibration, never as factual source material.** Before drafting, review the most recent product lead-edited sync updates to learn his cadence and level of detail. Do not carry any of their facts into today's update.
- **Artifacts, not process.** "Shipped tickets for X" not "spent time reviewing and then creating a ticket." The thing that exists at the end of the day is the bullet.
- **Short, with the evidence that makes it useful.** Start with a bold label, then give the concrete signal and real status. A second sentence or a qualifying clause is appropriate when it answers the practical questions: which customer cared, what other customers did not signal, who is taking the next step, or what product lead is testing next. Do not flatten a useful read into an unsupported “shipped” claim.
- **Sound like product lead talking to executive.** Favor a direct first-person update with the judgment, customer implication, or next step that makes it matter. Do not turn a real conversation into generic status language such as "kept external release behind internal dogfooding" or "landed the recommendation."
- **Use product lead's actual vocabulary.** Never use "aligned" or substitute generic business language for product lead's phrasing. Prefer concrete verbs such as "discussed," "mapped," "assigned," "shipped," "reviewed," and "flagged" when they accurately reflect the work.
- **Preserve meeting decisions accurately.** For an eligible Granola meeting, say what was actually discussed, the conclusion, and the meaningful next step. A customer-discovery plan, concern about premature release, or decision to prioritize the core product should not be compressed into an ambiguous project status.
- **executive-facing framing only.** Skip internal work that has no action or decision for executive. A quality discussion with internal-only outcomes, or a batch of research files with no upcoming decision, does not belong. Ask: does executive need to know this? Does it affect him or require his input? If not, cut it.
- **Match completion status exactly.** Don't call an outline a "draft" or a draft a "shipped" thing. If open questions remain (timeline, who owns it, what's left), say so plainly instead of implying it's more finished than it is.
- **Frame issues neutrally, not as internal fault-finding.** Describe the customer-facing symptom/confusion, not "I found a bug in our code." When work is handed to AI or engineering, especially to protect engineering's focus, say so, that's a real signal executive cares about.
- **Research and analytics findings count on their own.** A concrete number or status check (blog traffic, attribution setup, benchmark result) is a fine bullet even with no decision attached yet. Don't filter these out just because nothing was decided.
- **Skip internal tooling and automations, except when they change the operating signal.** Building or improving scripts, rules, skills, and pipelines is usually process, not a executive-facing deliverable. Include an automation only when product lead is actively using it to handle a business-facing workflow such as customer-feedback triage, he gives a real assessment of whether it works, and there is a clear next experiment or adoption decision.
- **Track sub-ticket progress across days, even under a known epic.** If a specific ticket under an epic already mentioned reaches a new state today (e.g., "finished"), it still gets its own bullet.
- **Forward-looking where relevant.** If something is coming for executive to act on or review, say so directly: "Promised delivery Friday morning so you and I can go over all options before EOD." First-person toward executive, not third-person reporting.
- **Sub-bullets are fine for meaningful qualifiers.** If a bullet has a key caveat or next step that would clutter the main line, put it as a sub-bullet. Do not add sub-bullets just to add detail.
- **Always link GitHub issues.** When a GitHub issue was filed, link the number: `[#1597](https://github.com/heyito/ito-web/issues/1597)`. Do not write issue numbers as plain text.
- **Link deployed tools and docs.** If something was shipped to a URL (Netlify, Notion, changelog, etc.) or a useful external link exists, include it inline. Skip internal file paths.
- **Link Notion docs when mentioned.** When a bullet references a Notion artifact (research, analysis, feature request), search Notion for the URL and include it as an inline link. Do not write "saved to Notion" without a link. If the page cannot be found, note that explicitly.
- **No self-derived calculations in bullets.** If you pulled and analyzed data (percentages, cost projections, averages), state the finding directionally, not numerically. Operational metrics and cost numbers are shared in team Slack channels (e.g., #product) where executive already sees them. Reference the channel or source for detail rather than repeating the numbers yourself.
- **Link Notion artifacts, not local file paths.** When research or analysis landed in Notion, search for the URL and link it inline. Never reference local workspace paths (e.g. `PM/research/...`) in bullets. If the artifact is only local and not in Notion, skip linking it.
- **GTM and product feedback count, but keep it light.** Copy feedback given, research shared with the team, conversations with Mike or Aaron or Grayson about product/compliance/GTM are deliverables even without a filed artifact. Prefer a short qualitative read ("patience wearing thin on X, flagged to Evan") over a full stats-driven breakdown unless executive specifically needs the depth.
- **Content reviews count when they drive a decision.** If product lead reviewed a contractor's work, say the verdict and the intended consequence in his own plain language. Do not replace it with a generic quality label.
- **Customer and contractor interactions count.** Feedback threads from customers (e.g. Sam in Slack), reviews of Vitaliy's work, 1:1s with Andy or other team members, include these if they happened today. Many of these only appear in Slack, not in agent transcripts.
- **Sweep every business-facing workstream before cutting.** Do not over-index on product tickets and launches. Include relevant marketing-engine work, content polish, candidate outreach, customer discovery, and active research, especially when product lead shared the result with the team or has a clear judgment about what happens next.
- **Keep product lead's useful qualifiers.** If the work is still moving, preserve the real status and judgment: who is being assigned, what is still being investigated, what product lead hopes will happen, what he is inclined to do, or what continues tomorrow. Do not turn this into falsely definitive completion language.
- **Customer discovery needs the actual read.** When a customer conversation changes how product lead is prioritizing or sequencing a product, name the customer, the signal, and the decision it informs. For example, “Adam’s API input makes me comfortable letting Geoff develop V1 further before I force it out to customers.”
- **Customer-signal sweeps need the boundaries.** When product lead checks several customers or channels for demand, report the confirmed interest together with the meaningful lack of signal elsewhere. Preserve his next move, such as reaching out for context, rather than turning a single positive reply into broad validation.
- **Small marketing improvements can matter.** Include shipped or staged blog and distribution polish when it makes the marketing engine more effective, even if the work is not a new page or a large launch. Use product lead's practical wording, such as “Made some quick blog improvements, which I shared in #GTM.”
- **Customer-facing documentation and positioning count.** A merged help-doc or marketing-site update that changes how Ito is described, especially a category or positioning correction, is a executive-facing deliverable. Name the scope and the customer-facing wording shift, then link the merged PR.
- **Skip unlinked in-progress work, with exceptions.** "Drafted a ticket" with no real-world impact is not a deliverable. Exceptions: significant decisions made, work shared externally (e.g. "shared prospect CSV with executive, Aaron, Grayson"), and genuine customer feedback sentiment even without a full write-up.
- **Skip executive's own meetings.** If executive was a participant, omit entirely.
- **Bold topic labels are fine.** Use `**Label**:` at the start of a bullet to name the topic. This is the preferred style.
- **Casual, first-person, strong voice.** "Shipped trio of tickets for Grayson" not "we are working on billing." Write as if speaking to executive, not reporting to a system. Cut when in doubt.
- **Slack is a primary source.** Agent transcripts capture Cursor work; Slack captures everything else, customer feedback threads, contractor reviews, 1:1 notes, quick decisions. Run the Slack search before finalizing bullets.
- **Preserve real ownership and timing.** When a named teammate has committed to the next step or product lead has a review queued for tomorrow, say so plainly. These qualifiers are more useful to executive than generic “in progress” language.

### 1e: Notify product lead

Tell product lead the draft is ready, give one line per bullet summarizing what's included, and remind him to fill in Blockers, Biggest focus, and his question. **Stop here.**

---

## Step 2: Push to Notion (only when product lead explicitly says so)

### 2a: Re-read the file immediately before pushing

Do not use what you generated. product lead will have edited it. The file is the source of truth; push word for word.

File: `/Users/jason-ito/Ito AI Cursor/PM/planning/daily-syncs/[YYYY-MM]/[TARGET-DATE]-barron-jason-sync-draft.md`

### 2b: Insert at the TOP of the Notion page

Use `notion-update-page` with `command: "insert_content"` and `position: {"type": "start"}`.

**Page ID:** `[NOTION_PAGE_ID]`

Format the entry as a toggle heading. All content inside the toggle must be indented with a tab character. Sub-bullets use double tab. Do NOT put divider lines (`---`) between sections; the section headings are sufficient separators.

```
# [Day], [Month DD, YYYY] {toggle="true"}
	Granola Notes link: [value]
	### Check in / updates
	- [bullets, tab-indented]
	### Blockers?
	- [value]
	### Biggest focus
	- [value]
	### 💡 What I want to ask executive today
	- [value]
```

### 2c: Verify

Fetch the page and confirm the new entry is at the top and matches the file word for word. Share the URL: `[NOTION_PAGE_URL]`

---

## Key context

**product lead:** Head of Product at Ito (heyito.co), a QA-automation tool that runs AI-generated tests on PRs. Team: executive Caster (CEO), Evan (CTO), Dennis, John, Julian, Kevin (engineers), Andy (design), Grayson (sales/CS), Vitaliy (frontend/onboarding).

**What executive cares about:** Product progress, customer pipeline (TrueMed, Homebase, Sagetap, Faber Connect), billing/activation, onboarding quality, GTM motion. Skip engineering detail; he wants what product lead accomplished and what needs his input.

**product lead's Slack user ID:** [PRODUCT_LEAD_SLACK_USER_ID]
**executive's Slack user ID:** [EXECUTIVE_SLACK_USER_ID]
**Draft files:** `/Users/jason-ito/Ito AI Cursor/PM/planning/daily-syncs/`
**Notion page ID:** `[NOTION_PAGE_ID]` (do NOT push automatically; wait for product lead's explicit instruction)


The following cursor rule files are relevant to the files you just read:

- /Users/jason-ito/Ito AI Cursor/.cursor/rules/pm-context.mdc
# PM Workspace Context

product lead's PM operating system. Key subfolders: `planning/` (daily syncs, briefs, meeting prep, tickets), `templates/` (reusable formats), `research/`, `weekly-reviews/`, `discovery/`, `tickets/`.

Always check `templates/` before creating any doc from scratch. Key templates:
- `daily-barron-jason-sync/` - daily async update to executive (draft for next business day; Friday = Monday)
- `github-issue-template-august-2026.md` - ticket structure for qaito and ito-web
- `memo-writing-style.md` - tone and structure for memos and briefs
- `weekly-review-templates.md` and `weekly-sales-call-dossier-template.md`

Writing standards: memos follow `memo-writing-style.md`; GitHub issues always include acceptance criteria; daily syncs are concise and action-oriented.

Consider these rules if they affect your changes.
