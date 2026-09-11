# Changelog Update Template

Use this template when it's time to add new releases to the public changelog at `ito.ai/docs/changelog`.

The changelog lives in `heyito/devdocs` as `changelog.mdx`. Security-related changes are intentionally excluded from the public changelog per CSO guidance and are available to auditors upon request.

---

## Step 1: Pull the GitHub releases

Ask the agent:

> "Check the current changelog.mdx in heyito/devdocs, find the most recent release version listed, then pull all production releases from heyito/ito-web that came after it."

The agent will:
1. Read `changelog.mdx` from the `main` branch of `heyito/devdocs` to find the most recent version number (the `description` field of the first `<Update>` block at the top of the file)
2. Run `gh release list --repo heyito/ito-web --limit 20` and filter to only releases newer than that version

**Include only:** releases without `-staging` in the tag name (e.g. `v1.0.12`, `v1.0.13`).

**Skip:** any tag ending in `-staging` or marked as Pre-release.

---

## Step 2: Get the release notes for each production release

Ask the agent:

> "Fetch the release body for each of those production releases."

The agent will pull the raw GitHub release notes, which will include PR titles, ticket numbers, author names, and links. None of that goes into the public changelog.

**When a PR title is ambiguous**, fetch the PR body from the GitHub API before writing the entry. A title like "Pull Request Details page" or "Feature/1359" tells you nothing about whether something is new, an update, or internal. Use `gh pr view <number> --repo heyito/ito-web --json body,title` to read the PR description, which usually explains what changed and why. Use this context to write an accurate entry; do not guess from the title alone.

---

## Step 3: Scrub and translate to customer language

For each release, keep only what a customer or auditor would care about. Apply these rules:

**Include:**
- New user-facing features
- UI/UX improvements customers will notice
- Bug fixes that affected customer-visible behavior
- Performance improvements customers would feel

**Exclude:**
- Security fixes (per CSO guidance)
- Internal refactors, dead code removal, code organization
- Dependabot/dependency bumps
- Admin-only tooling and internal dashboards
- CI/CD, infrastructure, and deployment changes
- Staging/release merge PRs
- Anything with `[bot]` as the author

**Language rules:**
- No ticket numbers (e.g. `ITO-1234`)
- No GitHub PR links
- No engineer names or usernames
- No internal jargon (no "pipeline orchestration," "CDK," "SFN," "drizzle," etc.)
- Plain English only. If you wouldn't say it to a customer in a support email, rewrite it.

---

## Step 4: Group changes into categories

Each release entry uses up to three categories. Only include a category if there's something in it.

- **New**: net-new features or capabilities customers didn't have before
- **Improvements**: enhancements to existing features, performance gains, UX polish
- **Bug Fixes**: fixes to customer-visible problems

**Before labeling anything "New":** Read the full existing `changelog.mdx` from `main` and check whether the feature, page, or capability already appears in any prior entry. If it does, the change is an **Improvement**, not New, even if the PR title sounds like it's building something from scratch. Only use "New" if the product genuinely has never had this capability before.

---

## Step 5: Handle edge cases

**Two releases on the same date:**
Mintlify requires unique `label` values for anchors. When two releases share a date, use the version number as the `label` and the date as the `description`, like this:

```mdx
<Update label="v1.0.9" description="May 18, 2026" tags={["Bug Fixes"]}>
```

For releases with a unique date, use the date as the `label`:

```mdx
<Update label="May 22, 2026" description="v1.0.11" tags={["Features", "Bug Fixes"]}>
```

**Thin releases (only internal changes):**
If a release has nothing customer-visible after scrubbing, you have two options:
- Skip it entirely (acceptable if the gap is a day or two)
- Add a one-liner "General performance and stability improvements." under **Improvements** to keep the version history complete

---

## Step 6: MDX format for each entry

```mdx
<Update label="[Date or version, see Step 5]" description="[Version or date]" tags={["Tag1", "Tag2"]}>
## New

- **Feature name.** One to two sentences describing what it does and why it matters to the user.

## Improvements

- One improvement per bullet, written as a complete sentence.

## Bug Fixes

- Fixed [what was broken] on [where].
</Update>
```

All three sections use bullets, one entry per bullet. Available tags: `Features`, `Improvements`, `Bug Fixes`

---

## Step 7: Add to the PR branch

Ask the agent:

> "Update PR #[number] in heyito/devdocs to prepend these new entries to the top of changelog.mdx."

New entries always go at the **top** of the file (most recent first). Do not reorder or edit existing entries.

---

## Step 8: Review before merging

Check the Mintlify preview link from the PR before approving:

- [ ] Each new entry renders correctly in the Changelog tab
- [ ] Tag filters work as expected
- [ ] No security details, internal names, or ticket numbers visible
- [ ] Most recent release is at the top
- [ ] Merging will publish immediately: confirm content is ready
