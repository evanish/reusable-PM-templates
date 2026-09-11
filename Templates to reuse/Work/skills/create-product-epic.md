---
name: create-product-epic
description: Build a large product epic from scratch by auditing existing GitHub issues, researching Slack decisions and meeting notes, identifying gaps, and producing a structured local draft before publishing. Use when creating a master epic, organizing a major feature area into sub-issues, or when there's a mix of existing tickets and net-new work to define. Trigger terms: epic, master issue, onboarding, major feature, organize tickets, sub-issues, product spec.
---

# Creating a Product Epic

Use this skill when organizing a major feature area into a structured master epic with sub-issues, especially when some tickets already exist and new ones need to be identified.

**Golden rule: always build locally first. Never push to GitHub until the draft is reviewed and approved.**

---

## Phase 1 — Gather Context

Pull from every relevant source before writing anything.

### 1a. User-provided input
- Ask for (or read) any existing draft, brief, or notes the user has
- Ask for any flow diagrams or Figma links
- Confirm the GitHub org/repo (e.g. `heyito/ito-web`)

### 1b. Slack research
Search Slack for decisions made about this feature area. Cover:
- The product channel (e.g. `#product`) for specs and decisions
- DMs between the PM and relevant stakeholders (engineers, design)
- Any threads where decisions were debated and resolved

Key things to extract:
- Confirmed decisions (who said what, when)
- Open questions still unresolved
- Scope that was explicitly included or excluded
- Any corrections to existing ticket bodies

### 1c. Meeting notes (Granola)
Check meeting notes for product planning sessions covering this feature area. Extract:
- Decisions made
- Action items not yet tracked in GitHub
- Design and engineering concerns raised

### 1d. GitHub issues audit
Read every existing issue that might be related. For each:
- Current status (open, closed, in progress)
- Assignee
- Whether the body is still accurate (flag outdated specs)
- Whether it's a launch blocker
- Whether it should be closed and replaced by better tickets

---

## Phase 2 — Build the Draft (Local File)

Create a markdown file (e.g. `feature-master-epic-draft.md`) in the workspace. Structure it as follows:

### File structure

```markdown
# [Feature] Master Epic — Draft

> Status: DRAFT
> Repo: org/repo
> Labels to create (if any)

## Remaining To-Dos
[ ] Checklist of manual steps that still need to happen

## Intended Flow (Narrative Spec)
Step-by-step walkthrough with branching paths.
Call out related issues per step.
Flag what's WIP vs. complete.

## Edge Cases
Table: edge case | status | notes

## Design Coverage
Table: screen | path | status

## Sub-Issues to Link
Table: # | title | assignee | status | notes
Separate section for "Not linked to this epic"

## New Tickets to Create
Table: title | context | priority | dependency

## Decisions Logged
Table: question | decision

## GitHub Issue Format (for publishing)
Proposed title, labels, tasklist in native GitHub format
```

### Narrative spec guidelines
- Break the flow into numbered steps matching the user journey
- For each step: describe behavior, call out related issues, flag WIP/blocked/complete
- For branching flows (Path A / Path B / Path C), label and separate clearly
- Capture non-obvious rules (e.g., "automation applies to future PRs only, not retroactively")

### Ticket table conventions
| Column | What to include |
|---|---|
| Status | ✅ Done, 🔄 In progress, 🚫 Blocked, 📋 Open, ⚠️ Needs action |
| Notes | Outstanding actions, correction comments needed, design status |

---

## Phase 3 — Identify Gaps

After drafting, run a systematic gap check:

**Missing tickets** — for each piece of work not covered by an existing issue:
- Notification flows (user, admin, coworker)
- Edge cases (race conditions, multi-tenant, concurrent actions)
- Migration / rollout work (e.g., existing beta customers)
- Analytics/tracking updates
- Status banners, end-state UI states

**Outdated tickets** — for each existing issue with stale body content:
- Write a correction comment draft
- Flag the assignee to review before proceeding
- Note in the epic sub-issues table

**Tickets to close** — for issues that are now superseded:
- Draft a closing comment linking the replacement tickets
- Do not include these in the epic tasklist

**Design gaps** — list screens that need design work before engineering can proceed.

**Decisions still open** — list any questions where no decision has been made yet.

---

## Phase 4 — Clarify Before Publishing

Before publishing, surface the short list of things that are still unresolved. Be specific:
- "Does X screen have a design? If not, this is blocked."
- "Is Y ticket a launch blocker or can we ship without it?"
- "Who owns Z? It's unassigned and has no activity."

Don't ask about things that can be figured out during implementation.

---

## Phase 5 — Publish

Once the draft is approved:

1. **Create the GitHub issue** using native tasklist format:
   ```markdown
   - [ ] #NNN — ticket title
   ```
   GitHub auto-checks items when sub-issues close.

2. **Create any labels** needed (e.g., `onboarding`) and apply to all related issues.

3. **Post correction comments** on any tickets with outdated specs.

4. **Create new tickets** identified during the gap check and add their numbers to the epic tasklist.

5. **Close superseded tickets** with a comment linking their replacements.

6. **Update ticket titles** that have drifted from current spec.

---

## Output checklist

Before calling a draft complete, verify these sections exist:

- [ ] Remaining to-dos (manual steps + open questions)
- [ ] Narrative spec with branching paths
- [ ] Edge cases table
- [ ] Design coverage matrix (screen → path → status)
- [ ] Sub-issues table (existing tickets with status + notes)
- [ ] New tickets to create (with priority + dependencies)
- [ ] Decisions log (question → decision, with source)
- [ ] GitHub issue format (tasklist ready to copy-paste)

---

## Patterns from the Onboarding Epic

Reference the `onboarding-master-epic-draft.md` for a complete worked example. Key patterns used:

- **Flow diagram embedded as mermaid** — paste the diagram directly into the markdown so it renders in GitHub
- **3-path branching** — Path A (new org founder), Path B (no existing org), Path C (fast-track to existing org)
- **Decisions logged by source** — each decision traces to a Slack thread or meeting so there's no ambiguity
- **Tickets flagged for correction** — e.g., #314 body had outdated spec; a correction comment was drafted and the assignee was warned before proceeding
- **Superseded ticket closure** — #292 was identified as covered by three other tickets; a closing comment was drafted linking all replacements
- **Launch blocker called out explicitly** — pilot customer migration was flagged as a blocker for a specific dependent ticket
- **Shipped work given credit** — #423 was shipped; marked ✅ in the sub-issues table with credit to the engineer and ship date
