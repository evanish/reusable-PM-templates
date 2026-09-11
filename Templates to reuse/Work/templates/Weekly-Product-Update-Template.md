# Slack Weekly Product Update — Template & Instructions

This template documents exactly how to produce the weekly customer-facing Slack update, from scanning GitHub to final formatting. Follow these steps in order.

## How to kick this off

Paste this into Cursor at the start of each Friday session:

> "Run the weekly product update workflow per `templates/slack-weekly-product-update.md`. The date range is [MONDAY DATE] through [FRIDAY DATE]. Pull closed issues and merged PRs from both `demox-labs/qaito` and `heyito/ito-web`, apply the classification and exclusion rules in the template, draft the Slack message, and send it to my DM for approval before doing anything else."

---

## Step 1: Pull what shipped this week from GitHub

Ask Cursor to scan both repos for the week's date range:

> "Pull all closed issues and merged PRs from `demox-labs/qaito` and `heyito/ito-web` closed between [START DATE] and [END DATE]. Give me a full list organized by theme."

GitHub queries Cursor runs under the hood:

```
repo:demox-labs/qaito is:issue is:closed closed:YYYY-MM-DD..YYYY-MM-DD
repo:heyito/ito-web is:issue is:closed closed:YYYY-MM-DD..YYYY-MM-DD
repo:demox-labs/qaito is:pull-request is:merged merged:YYYY-MM-DD..YYYY-MM-DD
repo:heyito/ito-web is:pull-request is:merged merged:YYYY-MM-DD..YYYY-MM-DD
```

Note: QA Ito (`demox-labs/qaito`) and Ito Web (`heyito/ito-web`) are separate repos with separate issue boards. Always pull from both.

---

## Step 2: Classify — customer-visible vs. internal

**Count as customer-visible if it involves:**

- Any change to what customers see, read, or interact with (UI, test output, PR comments, dashboard, onboarding, billing)
- Speed or reliability improvements that affect run time or login stability
- Bug fixes that were blocking or degrading the customer experience
- New capabilities customers can actually use

**Treat as internal (exclude) if it involves:**

- PostHog event tracking, analytics, logging, observability
- Cost alarms, infra scaling, CI/CD pipeline changes
- Admin-only tooling not visible to end users
- Security fixes unless they affected customer access (e.g., login broken = include; log sanitization = exclude)
- Staging environment setup, devcontainer changes, developer tooling

---

## Step 3: Apply these additional exclusion filters

Beyond customer-visible vs. internal, apply these judgment calls before finalizing the list:

**Exclude if it was tabled or debated and not shipped**

- Example: "Ito comments when it starts/skips a run" — debated, ultimately tabled. Don't include things that were discussed but not shipped.

**Exclude if it shipped earlier in the week, not in this deploy**

- Verify close dates. If something closed several days earlier and isn't part of the current deploy, note the date discrepancy.
- Exception: if there's nothing else to highlight, recent-enough is fine. Use judgment.

**Exclude if a bigger change is coming soon that makes it redundant**

- Example: dashboard filter controls were shipped but excluded because a full dashboard metrics redesign was coming. Don't hype something you're about to replace.

**Exclude if it's a UI grouping/organizational change that customers won't notice**

- Example: automations page now groups runs by PR instead of listing them flat. Technically shipped, but customers may not perceive it as a meaningful improvement. When in doubt, verify in the live interface before including.

**Exclude if it's purely an internal admin feature**

- Example: "admin can now cancel stuck pipeline runs" — useful for the team, not a customer win.

**Exclude transactional email launches unless the emails themselves are notable**

- Customers don't generally care that you wired up Brevo. They'd care what the email says or that it arrives reliably.

---

## Step 4: Draft the bullets

**Rules:**

- Maximum 4–5 bullets. If you have more, cut. Keep only the things customers will actually notice or care about.
- Each bullet = one short sentence for the bold label + one or two sentences of plain-English description. No more.
- No jargon. Write as if explaining to a non-technical early adopter.
- Don't lead with how it works internally. Lead with what the customer experiences.

**Format per bullet:**

```
[emoji] **Bold label** — One or two sentences. Keep it tight.
```

**Emoji guide:**  
Choose emojis that relate to the topic and description. For example:

- Speed / performance → ⚡
- Video / recordings / visual evidence → 🔍 or 📺
- Billing / free trial / no credit card → 🚫
- Login / auth / sessions → 🔐
- Dashboard / controls / filters → 🎛️ or 📊
- Bug fix → 🐛
- New feature → ✨
- If unsure, suggest two options and let the PM choose

**Colon, not em dash:** use colon (:) (not a hyphen nor em dash) between the label and the description.

---

## Step 5: Write the message wrapper

**Intro line** (before the list):

```
Wanted to share new features and improvements we launched this week:
```

- Casual, direct, no fluff. Ends with a colon, not a period.
- You can vary this slightly week to week, but keep it short — one sentence.

**Closing line** (after the list, in italics):

```
_Let us know what you think with an emoji, or please reply with any questions._
```

- Always italicize the closing line in Slack.
- Keep it an invitation, not a demand. Emoji reaction first, then reply for questions.

---

## Step 6: Slack formatting rules

These are the quirks you'll hit when posting via the Slack MCP:


| What you want               | What to type                                                                                                           |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Bold text**               | `**text`** (double asterisks — the MCP renders single `*text*` as italic)                                              |
| *Italic text*               | `_text_`                                                                                                               |
| Blank line between sections | Put a zero-width space (`​`) on its own line between the intro and the list, and between the list and the closing line |
| Numbered list               | Just type `1.`, `2.`, etc. — Slack renders them as a plain list                                                        |


**Full message structure (copy this skeleton):**

```
[Intro sentence]:
​
1. [emoji] **Label** — Description.

2. [emoji] **Label** — Description.

3. [emoji] **Label** — Description.

4. [emoji] **Label** — Description.
​
_Let us know what you think with an emoji, or please reply with any questions._
```

---

## Step 7: Send draft for approval — do not post to customers yet

Post the message to your own Slack DM first (user ID: `U0AHBD1N58D`) so the PM can review it. Then explicitly ask:

> "Does this look good to send to customer channels? Reply with approval and I'll post it."

**Do not post to customer channels until you receive explicit approval.** Wait for a clear "yes, send it" before proceeding to Step 8.

When reviewing the draft, check:
- [ ] Bold labels are actually bold (not italic)
- [ ] Spacing between intro, list, and closing looks right
- [ ] Emojis render correctly
- [ ] Nothing feels too long or jargon-y
- [ ] Any tabled or not-yet-shipped items have been removed

---

## Step 8: Post to customer channels (only after approval)

For the current list of customer channels and their Slack channel IDs, always refer to:

**`slack/customer-channels.md`**

This is the source of truth — new customers are added there as they onboard, so always pull from it rather than using a hardcoded list here.

> **Note:** These are Slack Connect (externally shared) channels. The Slack MCP cannot post to them directly — it requires a workspace admin to enable "Allow apps to post in Slack Connect channels" under **Slack Admin > Settings > Slack Connect**. Until that permission is granted, copy-paste the final message manually into each channel.

