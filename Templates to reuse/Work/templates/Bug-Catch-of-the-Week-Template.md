# Bug Catch of the Week: Weekly Post Template

Use this template to draft each new **Bug Catch of the Week** post. It reflects the first DoltLite post's final structure and editorial choices. Run `/blog-to-sanity` only after this draft is content-complete.

## Before drafting

- Choose a verified high- or critical-severity runtime finding. A lower-severity finding is acceptable only when its runtime lesson is unusually clear.
- Confirm the finding was acknowledged, reproduced, fixed, or otherwise independently validated.
- Identify the primary search question, the affected runtime condition, the bounded consequence, the root cause, and the fix.
- Determine whether the source is open source, private, permissioned, or Ito internal. Do not identify a customer without approval.
- Gather source links: repository, pull request or issue, fix commit, and Ito run evidence when public and appropriate.
- Choose a short UTM campaign identifier for all Ito marketing, blog, sign-up, and product links in this post. Example: `botw2-auth-scope`.

## Draft metadata

```markdown
# Bug Catch of the Week: [Specific failure mode and realistic consequence]

**Series:** Bug Catch of the Week
**Byline:** Evan Marshall
**Primary search question:** [A real question an engineer might search]
**Proposed slug:** `/blog/[search-first-slug]`
**Meta description:** [Temporary working description. `/blog-to-sanity` supplies final options.]
**Source classification:** [Open source / Private anonymized / Permissioned / Ito internal]
**UTM campaign:** `[short-post-identifier]`
```

## Body template

### 1. Open with the failure

Start with the surprising result in two to four short lines. Do not start with background, a definition, or "when a system...".

```markdown
**[The affected operation] failed. The Good:** [The error or safeguard that appeared to work.] **The Bad:** [The concrete state that made the failure dangerous.]

[One short reaction, if it earns its place.]

That was the failure Ito caught in [product or truthful anonymous descriptor] *before* merge. [One or two sentences on the affected operation, bounded potential consequence, confirmation, and fix.]

This is **Bug Catch of the Week**, a semi-regular series about verified, critical and high severity bugs caught in the wild *before* they merge. Each entry follows a real **runtime analysis** finding: Ito runs the code on a pull request, exercises the affected path, and shows what static **analysis alone** could not verify.
```

The opening must answer the search question without becoming a summary of the entire article. Keep the claim precise: distinguish a potential consequence from a confirmed production incident.

### 2. Add "The bug catch at a glance"

Keep this to five factual bullets. It gives skimmers the claim, stakes, and evidence before the narrative starts.

```markdown
## The bug catch at a glance

- **Product:** [Repository link and a plain description, or an anonymized descriptor.]
- **Severity:** [High or critical.] [Affected user flow, system, or operation.]
- **The catch:** [Observed failure under a specific runtime condition.]
- **Potential production consequence:** [Bounded real-world consequence.]
- **Evidence:** [Pull request], [Ito test result], and [fix commit].
```

Follow it with the first visual.

```markdown
[Image 1: Screenshot of Ito's finding on the [product] pull request]

[Alt text: Ito AI code review finding on a [product] pull request showing [specific runtime failure and consequence].]
```

### 3. Tell the story in this order

Use these H2s unless a finding truly requires a different order. This sequence made the first post easy to follow: reveal the surprising state, explain the missing assumption, show the test, then explain the mechanism and fix.

```markdown
## The impossible-looking symptom

[One paragraph on the change and why the happy path looked safe.]

[One short sentence introducing the forced runtime condition.]

[Describe what the operation reported, then what was actually left behind.]

[Explain why that state makes retry or recovery unsafe.]

## What the first explanation missed

[Describe what a careful code reviewer could reasonably establish from the diff.]

[Name the untested runtime condition and why code reading alone cannot establish the required state.]

[Explain the unsafe operation order in plain language.]

[Image 2: Before-and-after diagram of the [operation] failure path]

[Alt text: Before-and-after [operation] diagram showing the unsafe [old behavior] and the recovery-safe [fixed behavior].]

## The investigation

[One sentence on the runtime test.]

1. [Expected post-failure state.]
2. [Observed state after the injected or reproduced failure.]
3. [How the implementation explains that result.]
4. [How the maintainer confirmed and resolved it.]

## The mechanism and consequence

[Write the exact causal chain in chronological order. Name each state-changing operation that matters.]

[A short contrast sentence: the returned error may be correct while the resulting state is unsafe.]

[Explain what the fix changes, including the recovery state it preserves.]

[State whether production impact was reported. Do not imply an incident without evidence.]

[Restate the consequence precisely: what data, permission, workflow, or customer outcome could be lost, exposed, or corrupted.]

## Why reading the code was not enough

[What static review could establish.]

[What it could not prove under this runtime condition.]

[A contextual Ito blog link with UTMs, if one is genuinely relevant.]

[The direct runtime test that proved the failure before production, and the resulting fix or coverage.]
```

### 4. Close with the lesson, evidence, then CTA

Do not lead with a product pitch. Land the engineering lesson, show the evidence, then offer Ito as the quiet next step.

```markdown
The Key Lesson: [One sentence connecting the failure path to the engineering practice readers should adopt.]

**Want a closer look at the evidence?** See it all below.

- [Product pull request #[number]]([URL])
- [Fix commit]([URL]) `[short SHA]`
- [Ito test result for the pull request]([Ito artifact URL])

*Want Ito to run your code before your next merge? Sign up to [run Ito on your PRs.]([signup URL with UTMs])*
```

Do not attach UTMs to external source links or Ito run-artifact evidence links. Add them to every CTA and contextual link to `ito.ai`, `www.ito.ai`, or `app.ito.ai` that is intended to drive readers onward.

```text
utm_source=blog
utm_medium=post+mention
utm_campaign=[short-post-identifier]
utm_term=[short-placement-identifier]
```

Use one short campaign identifier throughout the post. Use a short term that says where or how the link appeared, such as `mid-link`, `inline-cta`, or `end-cta`. Preserve existing query parameters and join new ones with `&`.

## Editorial guidance from the first post

- Lead with the adverse state, not a technical definition. The Good and The Bad format gave the failure immediate stakes without hype.
- Use the runtime test as evidence, not as a slogan. Name what failed, what the system returned, and what persisted afterward.
- Explain the root cause as a timeline. Readers should be able to picture the old state, each risky step, the failure point, and the state left behind.
- Give a junior engineer enough context to understand why the error return was insufficient. Do not assume they already know the storage, auth, concurrency, or lifecycle edge case.
- Keep Ito in the background. The product's role belongs in the observed test, the evidence link, one relevant contextual link, and the final low-pressure CTA.
- Prefer "static review could establish X, but could not prove Y" over claims about whether other tools did or did not catch the bug.
- Use the two-image minimum when it adds clarity: an evidence screenshot after the facts, then a before-and-after state diagram beside the mechanism.
- Do not add a Runtime Rule callout by default. The first final post was clearer without it. Bring it back only when the rule makes the mechanism easier to remember, not as series decoration.
- Do not add an FAQ merely for AEO. The direct opening answer and self-contained sections should carry the post. Run the separate `/blog-to-sanity` skill for its SEO, AEO, internal-link, quality, and Sanity preparation steps.

## Pre-publish check

- [ ] The title names a concrete failure and consequence.
- [ ] The opening, at-a-glance bullets, and body make the same bounded claim.
- [ ] The body explains the runtime condition, observed failure, mechanism, fix, and validation.
- [ ] Every production-impact statement is evidence-backed and distinct from a potential consequence.
- [ ] Public source links work. Private-source details cannot identify the customer.
- [ ] Each image has `[Image N: ...]` and an under-125-character `[Alt text: ...]` line.
- [ ] Every Ito marketing, blog, product, or sign-up link has the four UTM fields. Evidence links are left clean.
- [ ] The CTA comes after the engineering lesson and source evidence.
- [ ] The draft is ready for `/blog-to-sanity`.
