# Blog to Sanity: Publishing Skill

Invoke this skill when a blog post draft is content-complete and ready for the publishing checklist. The skill generates all missing publishing assets, runs quality scans, and appends a `## Marketing skill additions` section to the draft file for Jason's review.

## Trigger phrases

"run the publish skill on [post]", "prep [post] for Sanity", "publishing checklist on [post]", "blog to Sanity [post]"

## Inputs

- Path to the post draft markdown file in `PM/content/`

## What this skill does NOT do

- Does not auto-select titles, SEO meta, or any other option. Jason picks.
- Does not push to Sanity (that is a separate step after Jason's review and selection).
- Does not write or rewrite body copy, except for: adding contextual internal links, fixing confirmed AI tells, and cleaning up formatting issues.
- Does not set author (always Evan Marshall), date (publish date), or slug (derived from title Jason selects).

---

## Step-by-step workflow

Work through all steps in order. Do not skip any.

### Step 1: Read source files

Read all of these before generating any output:

1. The post draft markdown file provided as input
2. `PM/content/jason-voice-style-guide.md` (voice rules, AI tell checklist)
3. `.cursor/skills/writing-marketing-copy/SKILL.md` and `.cursor/skills/writing-marketing-copy/reference.md` (headline formulas, appeals, copy principles)
4. `PM/content/public-content-inventory.md` (existing content for internal link sweep)

---

### Step 2: Generate post title options

Produce 3-5 post title options. These are the display titles (shown on the blog index and post header), not the SEO meta title.

Rules:
- Write for engineers. Technical specificity beats vague excitement.
- No hype words: "amazing," "revolutionary," "game-changing," "shocking." Earned specificity beats adjectives.
- Self-interest and news angles outperform curiosity alone (per copywriting reference Section 2). If using curiosity, pair it with a clear implied benefit.
- Use at least one angle from each of the three headline classes: self-interest (what the reader gets), news (announcement, new capability), curiosity+benefit (a surprising fact that implies a payoff).
- Specific numbers beat round ones ("eight parallel agents" beats "multiple agents").
- No em dashes anywhere (hard rule from voice guide).
- No "it's not X, it's Y" constructions.
- Do not start any title with "AI."

Format:
```
### Post title options

1. **[Title]** - [one sentence on the angle: self-interest / news / curiosity+benefit]
2. ...
```

---

### Step 3: Generate SEO meta title options

Produce 3-5 SEO meta title options. These populate `seo.metaTitle` in Sanity.

Rules:
- 50-60 characters. Show the exact character count inline after each option as `(XX chars)`.
- Include the primary keyword naturally (do not stuff).
- Specific and benefit-forward. Avoid generic descriptors.
- These are search-snippet titles, not ad headlines. Tone should be informative and direct, not exclamatory.
- Write distinct angles, not minor variations of each other.

Format:
```
### SEO meta title options

1. [Title] (XX chars)
2. ...
```

---

### Step 4: Generate SEO meta description options

Produce 3-5 SEO meta description options. These populate `seo.metaDescription` in Sanity and also serve as the `description` field shown on the blog index.

Rules:
- 150-160 characters. Show the exact character count inline as `(XXX chars)`.
- The first sentence should answer the core question of the post in plain, specific language.
- Must create enough curiosity or stated value that an engineer scanning search results clicks through.
- No generic phrases: "In this post, we explore..." / "Learn how to..." / "Discover the power of..."
- No em dashes.
- Write distinct angles, not minor variations.

Format:
```
### SEO meta description options

1. [Description] (XXX chars)
2. ...
```

---

### Step 5: Write the 3-bullet summary

Write exactly 3 bullets that go at the top of the post as a preview summary. These get added to Sanity as a structured field (not in the body PortableText).

Rules:
- Each bullet is 1-2 sentences, in Jason's voice: direct, specific, no hedging.
- The three bullets together should make a reader who skims them want to read the full post.
- They should summarize the post's core argument and payoff, not just describe what the post covers.
- No em dashes. No generic openers ("This post covers...").

Format:
```
### 3-bullet summary

- [Bullet 1]
- [Bullet 2]
- [Bullet 3]
```

---

### Step 6: Table of Contents

Check if the post has 4 or more H2 sections OR is 1,200+ words.

If yes: generate a linked Table of Contents with anchor links matching the H2 headings.
If no: write `Table of Contents: not needed (fewer than 4 sections / under 1,200 words).`

Format:
```
### Table of Contents

- [Section title](#anchor)
- ...
```

---

### Step 7: Image alt text

Identify every image referenced or described in the draft (hero image, embedded diagrams, terminal recordings, screenshots). For each, suggest specific, descriptive alt text.

Rules:
- Alt text should describe what the image shows and why it matters to the post's argument, not just what is literally visible ("Before/after diagram comparing..." not "An image showing...").
- For terminal recordings or GIFs, describe the sequence of commands and what the output demonstrates.
- Keep each under 125 characters.

Format:
```
### Image alt text

- **Image 1 (hero):** [Suggested alt text]
- **Image 2 ([descriptor]):** [Suggested alt text]
```

If no images are referenced or described in the draft: flag this explicitly as a blocker. Every post needs at least one image.

---

### Step 8: AI tell scan

Read Section 6 of `PM/content/jason-voice-style-guide.md` and scan the entire post body for every AI tell listed there, plus these specific patterns:

**Hard rule violations (must fix):**
- Em dashes (U+2014 or double-hyphen used as a substitute)
- "It's not X, it's Y" constructions and all close variants

**Flag with proposed fix (Jason approves or ignores):**
- AI stock transitions: "Moreover," "In today's fast-paced world," "It's important to note that," "In conclusion," "Furthermore," "Additionally"
- Symmetrical triads everywhere (three-item parallel lists stacked throughout the post)
- Hedge language: "can help," "may improve," "might potentially," "could be argued"
- Uniform paragraph and sentence length (flag if three or more consecutive paragraphs are similar length with no short punchy one-liners between them)
- Generic, hypothetical examples ("imagine a company that...")
- Missing point of view (sections that summarize both sides without landing on an opinion)
- "And the most exciting part?" and variants (AI enthusiasm tell)
- "Believe it or not" (common AI opener)

For each hit: quote the offending line exactly and write a proposed fix. Jason can approve the fix or ignore the flag.

If no issues found: write `AI tell scan: clean.`

Format:
```
### AI tell scan

**Hard violations:**
- None / [quote] → proposed fix: [rewrite]

**Flags for review:**
1. Line: "[exact quote]"
   Flag: [which rule]
   Proposed fix: "[rewrite]"
```

---

### Step 9: Internal link sweep

Fetch `https://ito.ai/blog` to get the list of currently published posts. Read the titles and slugs.

Then read the post body and identify every place where a published Ito blog post could be linked contextually in the flow of the sentence. Add the links directly in the draft body (in-place edit).

Rules:
- 2-5 contextual links per 1,000 words.
- Links go in the sentence where the topic naturally comes up, not in a "further reading" block.
- Only link to published posts that are genuinely relevant (not just topically adjacent).
- Do not add a link if forcing it would feel awkward in the sentence.
- If no published posts are relevant enough to link, say so and do not add links.
- Add UTM parameters to every CTA and contextual link whose destination is an Ito-owned marketing, blog, product, or sign-up page (`ito.ai`, `www.ito.ai`, or `app.ito.ai`). Do not add UTMs to external sources or Ito run-artifact links used as evidence.
- Use this default tracking structure: `utm_source=blog`, `utm_medium=post+mention`, `utm_campaign=<short-post-identifier>`, and `utm_term=<short-placement-identifier>`.
- Keep `utm_campaign` short, lowercase, and hyphenated. It identifies the post or topic, for example `botw1-dolt-swap`. Reuse it for every tracked Ito link in that post.
- Keep `utm_term` short, lowercase, and hyphenated. It identifies where and how the reader encountered the link, for example `end-cta`, `mid-link`, or `inline-cta`.
- Add parameters with `&` when a destination already has a query string. Preserve any existing query parameters. Verify every tracked URL has all four parameters before pushing to Sanity.

After making in-place edits to the draft, log each addition in the inline edit changelog (Step 11).

---

### Step 10: AEO question sweep

AEO (Answer Engine Optimization) is about getting the post cited by Perplexity, ChatGPT, Google AI Overviews, and similar. The mechanism is a self-contained, specific answer to a question an engineer would actually type. Generic FAQ blocks ("What is X?") do not get cited and alienate engineers. Specific, technically credible answers to honest questions do both jobs.

**Part A: Find real questions engineers ask**

Run web searches to find what engineers actually ask about the post's topic:
- Search `"[topic]" site:reddit.com` and `"[topic]" site:news.ycombinator.com` to see what came up in real discussions
- Search the topic directly in a general web search and look at the "People also ask" / autocomplete results
- Look at what the post's closest competitors or reference docs already answer

Use these findings to generate questions. Do not generate questions from imagination alone.

**Part B: Write 3-5 FAQ questions and answers**

Apply this filter before including any question:

1. Would an engineer genuinely type this into ChatGPT or Perplexity in a moment of curiosity or frustration? If no, cut it.
2. Does the answer add information not already fully covered in the post body? If no, cut it.
3. Is the question specific enough that a generic "overview of this topic" post would NOT answer it? If no, it's too broad.
4. Is this an "honest skeptic" question (an objection, a comparison to an alternative, an edge case, a "why not just...")? If yes, prioritize it. These are the highest-value questions for both AEO and engineer credibility.

**Hard rules for the answers:**
- 50-150 words each. Self-contained enough that if Perplexity quoted only that answer, it would stand alone and be correct.
- Jason's voice: direct, specific, no hedging, no marketing language. State outcomes, not promises.
- Write with a point of view. Lead with the answer, then explain the mechanism or tradeoff in plain language. Use a concrete consequence from the post when available, rather than generic advice.
- Sound like a practitioner talking to one engineer: use "you" where natural, contractions, varied sentence length, and a short punchy sentence when it earns emphasis. Do not lapse into neutral documentation or abstract process language.
- Before presenting an FAQ, compare it against the voice guide's Section 6 checklist. Rewrite any answer that hedges, merely summarizes both sides, stacks symmetrical lists, or could apply unchanged to any company or topic.
- No em dashes. No "it's not X, it's Y" constructions. No adjective-only claims ("powerful," "seamless").
- Do not restate the post's body in question form. If the answer is already a clear paragraph in the body, skip this question.
- Honest answers to comparison questions ("Why not just use Docker Compose?") must be technically accurate and acknowledge what the alternative does well before explaining the gap.

**Part C: Placement recommendation**

For each FAQ, recommend one of two placements:
- **In-body:** the question can be answered naturally within an existing section (add it there as a subhead or rhetorical question, do not create a standalone FAQ block)
- **FAQ section at end:** the question does not fit in any existing section and warrants a dedicated block at the bottom of the post

If all questions fit in-body: do not create an FAQ section at the end. Only create an end-of-post FAQ block if at least 2 questions genuinely do not fit in the body.

Format:
```
### AEO question sweep

**Source questions found:**
- [List of real questions surfaced from Reddit/HN/search, with source]

**Proposed FAQs:**

**Q: [Question]**
A: [50-150 word answer in Jason's voice]
Placement: [In-body under "[Section name]" / FAQ section at end]

**Q: ...**
```

---

### Step 11: Technical reminders

Output a short checklist of human-verified steps that cannot be confirmed programmatically:

```
### Technical reminders

- [ ] Verify code blocks render correctly in Studio preview (not as plain text). If they render as plain text, file a ticket to add the `codeBlock` type to the `blogPost` body schema before publishing.
- [ ] Test all internal links added in Step 9 resolve to live pages after publish.
- [ ] Confirm all images are uploaded to the Sanity media library with alt text set before publishing.
- [ ] Studio preview: check the post renders correctly end-to-end before hitting Publish.
```

---

### Step 12: Inline edit changelog

After completing Steps 8, 9, and 10, compile a numbered log of every edit made directly to the post body (internal links added, AI tell rewrites applied, formatting fixes). Present this changelog in the agent chat response so Jason can review it side-by-side with the post draft.

Format (in the agent chat response, not in the draft file):
```
**Inline edits made to the post body:**

1. [Step 9] Added internal link to "[Post title]" on the phrase "[anchor text]" in paragraph starting "[first few words of paragraph]..."
2. [Step 8] Rewrote AI tell in paragraph starting "[quote]..." → "[new version]"
3. ...
```

If no inline edits were made: state that explicitly.

---

### Step 13: Append Marketing skill additions to the draft

Open the post draft file and append the following section at the end. Do not modify any content above this section except for the in-place inline edits from Steps 8 and 9.

```markdown
---

## Marketing skill additions

*Generated by the blog-to-sanity skill. Jason: review each section, pick your choices, then tell Cursor to push to Sanity.*

### Post title options
[output from Step 2]

### SEO meta title options
[output from Step 3]

### SEO meta description options
[output from Step 4]

### 3-bullet summary
[output from Step 5]

### Table of Contents
[output from Step 6]

### Image alt text
[output from Step 7]

### AI tell scan
[output from Step 8]

### AEO question sweep
[output from Step 10]

### Technical reminders
[output from Step 11]
```

---

## Phase 2: Pushing to Sanity (after Jason's review)

Once Jason has reviewed the `## Marketing skill additions` section and indicated his selections (title, SEO meta title, SEO meta description), run the following Sanity push sequence using the Sanity MCP:

1. Confirm the Sanity draft document ID from the post draft file header
2. Use `patch_documents` to set:
   - `title` = Jason's selected post title
   - `seo.metaTitle` = Jason's selected SEO meta title
   - `seo.metaDescription` = Jason's selected SEO meta description
   - `description` = Jason's selected SEO meta description (same value; this populates the blog index summary)
3. Push every end-of-post FAQ as a `faqBlock`, not as H2/H3 and paragraph Portable Text blocks. Set the section title and create one `faqItem` per question with the answer as Portable Text. This is the site’s collapsed accordion presentation and applies to every FAQ by default.
4. If a Table of Contents was generated and Jason approved it, add it as a note or structured field per Sanity schema (confirm field availability first with `get_schema`)
5. Convert the remaining post body to Portable Text and push it. For every image reference in the body, insert **two adjacent blocks** (not one):
   - Block 1: a normal-style block with the text `[image N]` (e.g. `[image 1]`), no italic marks
   - Block 2: a normal-style block immediately after with the text `[Alt text: <alt text from Step 7>]`

   This pair lets Jason click `[image N]` in Studio, replace it with the uploaded image from the media library, then copy the alt text from the line directly below.

   Never use verbose italic placeholder sentences for image slots. Always use this two-block `[image N]` / `[Alt text: ...]` format.
6. Confirm the patch succeeded by reading back the updated document
7. Report the Sanity Studio URL for Jason to do a final preview before publishing

Do not call `publish_documents`. Jason publishes manually after final review in Studio.

### UTM verification before handoff

Before reporting the Sanity draft link, confirm:

- Every Ito-owned CTA and contextual link has `utm_source=blog`, `utm_medium=post+mention`, the shared short campaign identifier, and a placement-specific term.
- The campaign identifier is short enough to remain recognizable in analytics exports.
- Evidence links to third parties and Ito run artifacts remain unmodified.
