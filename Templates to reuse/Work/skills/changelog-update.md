---
name: changelog-update
description: >-
  Pull production releases from heyito/ito-web since the last published entry
  on the Mintlify public changelog (heyito/devdocs, changelog.mdx), draft the
  scrubbed customer-facing update, get Jason's approval, then open a PR to
  heyito/devdocs. Use when the user asks to update the changelog, catch up the
  doc site changelog, or invokes /changelog.
disable-model-invocation: true
---

# Changelog Update

Bring the public changelog at `ito.ai/docs/changelog` up to date with recent `heyito/ito-web` releases, following the detailed rules in:

```
/Users/jason-ito/Ito AI Cursor/PM/templates/changelog-update-template.md
```

Read that file and follow it exactly for scrubbing, categorization, and MDX formatting. This skill sequences the run.

## Phase 1: Find the gap

1. Read `changelog.mdx` from the `main` branch of `heyito/devdocs` (GitHub MCP `get_file_contents`, not a stale local draft) to find the most recent published version, the `description` field of the first `<Update>` block.
2. Run `gh release list --repo heyito/ito-web --limit 30` and keep only production tags (no `-staging`, not marked Pre-release) newer than that version.
3. Check `PM/docs/` for an existing unpublished draft. If one exists but doesn't reach the latest production release, fold it in and extend it rather than starting over, note this in the new draft's review notes.

## Phase 2: Build the draft

Follow the template's Steps 2 through 6:
- Pull release bodies for each new production release.
- For any ambiguous PR title, fetch the PR body (and the linked issue, if the PR body is also thin) before writing the entry.
- Scrub to customer language; exclude security, internal, admin-only, and infra changes.
- Categorize into New, Improvements, Bug Fixes, each section as bullets.
- Handle same-date collisions and thin releases per Step 5.

Write the result to `PM/docs/changelog-draft-YYYY-MM-DD.md` (today's date), with a review-notes block at the top explaining what's included, what's excluded, and why, matching prior drafts in that folder.

## Phase 3: Show Jason the draft, then wait

Present the full draft in chat for review. Do not push anything yet. This is review-first: changelog content ships to every customer and needs a look before it goes out.

## Phase 4: Push once approved

Once Jason confirms the draft is good:

1. Create a new branch on `heyito/devdocs` off `main`, named `changelog-update-YYYY-MM-DD`.
2. Update `changelog.mdx` on that branch: prepend the new `<Update>` blocks to the top, above the existing entries. Do not reorder or edit existing entries.
3. Open a PR from that branch into `main` with a short body listing the versions covered.
4. Share the PR link back to Jason. Remind him the Mintlify preview should be checked before merging, and that merging publishes immediately.

## Notes

- `heyito/devdocs` is Jason's own product-docs surface, not `qaito` or `ito-web` engineering code, so opening this PR directly is expected and fine. It's still a content change to a live customer-facing page: always show the draft before pushing, and never merge the PR automatically.
- If the only releases since the last entry are thin (nothing customer-visible after scrubbing), say so and ask whether to skip them or add a one-line "general improvements" placeholder per the template's Step 5, don't decide silently.
