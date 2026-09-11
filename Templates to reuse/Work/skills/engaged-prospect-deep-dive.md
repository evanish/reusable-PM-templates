---
name: engaged-prospect-deep-dive
description: Produces a structured intelligence brief on a prospect who is interested in Ito but has not yet become a paying customer — specifically focused on understanding why they are still engaged despite struggling with setup or onboarding. Use when Jason asks to "do a deep dive on [company]", "come up to speed on [prospect]", "understand why [company] is still with us", or invokes the engaged-prospect-deep-dive skill by name.
---

# Engaged Prospect Deep Dive

Produces a structured brief on a specific prospect: why they're interested, what's blocking them, who's championing it, and why they're still engaged despite struggles.

## Step 1 — Find all call files for the prospect

The call notes live in:
```
/Users/jason-ito/Ito AI Cursor/customer-calls/granola_notes/Barron Caster calls/
/Users/jason-ito/Ito AI Cursor/customer-calls/granola_notes/Grayson Cooper calls/
/Users/jason-ito/Ito AI Cursor/customer-calls/granola_notes/Jason Evanish calls/
```

Files are named `YYYY-MM-DD_<Company>_<Person>.md`. Search all three folders for files where the company name in the filename matches the prospect. Read every matching file in full — both the `## Summary` and `## Transcript` sections.

## Step 2 — Pull quotes (transcript-first)

**Always read `## Transcript` first.** Extract verbatim quotes from there.

- Best quotes come directly from customer contacts (not Ito team).
- Internal Ito team members — **not** customer voices: Evan Marshall, Grayson Cooper, Barron Caster, Jason Evanish.
- Exception: if a customer wholeheartedly endorses something an Ito team member said (e.g. "Yeah, exactly" / "That's right" / strong affirmation), quote the full exchange.
- Only fall back to the `## Summary` section if the transcript has no usable quote for a point. If you do, mark it `[summary — not verbatim]`.
- If no quote exists for a section, say so explicitly. Do not paraphrase as if it's a quote.

## Step 3 — Write the brief

Use this structure. Weave quotes directly into each section as the primary evidence — not as a separate "quotes" section at the end.

```
# Engaged Prospect Deep Dive: [Company Name]

**Calls reviewed:** N total
- YYYY-MM-DD — [whose folder] — [short title]
- ...

---

### 1. Initial interest — what resonated and what didn't
What first got them on a call? What hooked them? What left them skeptical or cold?
[Analysis + verbatim quotes]

### 2. Biggest questions and objections
What did they push back on, ask repeatedly, or need convincing about?
[Analysis + verbatim quotes]

### 3. Champion(s) — who and why they're most excited
Who inside their company is driving this? What specifically motivates them?
[Analysis + verbatim quotes]

### 4. Biggest obstacles — what's blocking us
Technical, org, trust, product gaps — what has actually prevented them from going live?
[Analysis + verbatim quotes]

### 5. Setup cooperation — open vs resistant
What have they been willing to do to help with setup (secrets, repo access, env config, etc.)?
What have they pushed back on or dragged their feet on?
[Analysis + verbatim quotes]

### 6. What's kept them engaged despite struggles
Why haven't they walked away? What keeps them coming back to the calls?
[Analysis + verbatim quotes]

### 7. Deal status and path forward
Where does the deal stand as of the most recent call?
What has to happen to get them to paying customer?
If a trial period is needed, how many weeks?
[Analysis + verbatim quotes]
```
