# Custom Rules (optional, user-defined)

This file starts empty on purpose — it's a template. Fill it in with your own personal tics or your company's brand/compliance guidelines, and the skill will check text against these too, alongside the built-in pattern library.

**Why this is a separate file from `patterns.md`:** those are universal AI tells anyone would recognize. What you add here is specific to you or your org — often a compliance rule, not a style preference — so it needs its own space, its own severity handling, and it should never get silently merged into or overwritten by updates to the core pattern library.

## Format

Copy this block for each rule you add:

```
### [Rule name]
**Type:** [Style preference | Brand guideline | Compliance/legal]
**Rule:** [What's not allowed or what's required, stated plainly]
**Why:** [The reason — helps whoever reads the flag understand it's not arbitrary]
**Detection:** [What to look for — specific words, phrasing patterns, or structures]
```

## Example (delete or replace this once you've added your own)

```
### No unverified superlatives
**Type:** Compliance/legal
**Rule:** Words like "best," "fastest," "most," "#1," "leading," or "only" can't
be used unless the claim is backed by a citable source (a study, a benchmark,
an audited stat). If no source is attached in the draft or mentioned by the
user, flag it.
**Why:** Unverified superlative claims create legal/regulatory exposure —
this isn't a style call, it's a review requirement.
**Detection:** Scan for superlative and absolute-ranking language. If flagged,
don't assume the claim is false — flag it as "needs a source attached," not
"this is wrong."
```

## How the skill uses this file

- Read this file during Pass 1, alongside `patterns.md` and the format calibration from `formats.md` — same pass, not a separate check.
- Label flags from this file distinctly: **"Custom rule: [rule name]"** — never merge them into a `patterns.md` category name, since they're not universal tells and a reader needs to know a flag here reflects a rule they (or their org) defined, not a general AI-writing tell.
- **Compliance/legal-type rules get surfaced even at Light overall density.** A single unverified superlative matters regardless of how clean the rest of the section reads — don't let a good Slop Meter rating bury a compliance flag.
- For a rule that requires external verification (like the superlative example) the skill can only flag the *pattern* — it can't verify the underlying claim. Say so plainly in the flag rather than asserting the claim is true or false.
- If this file is still just the template (unedited), skip it silently — don't flag the example content as if it were the user's real rule, and don't mention the file at all in output.
- Multiple rules of different types can coexist in one file — no need for separate files per rule.
