---
name: unslop
description: Detects and helps fix "AI slop" in written prose — the tics, filler, and hollow structures that make writing sound machine-generated (vocabulary tics like "leverage/unlock/seamless", sentence shapes like "it's not just X, it's Y", forced bullet-ification, empty transitions, false-balance hedging, generic scene-setting). Use this skill whenever the user pastes text and asks to check, scan, audit, or flag it for AI slop, robotic phrasing, "sounds like ChatGPT/AI," or asks to make a draft sound more human, less generic, or less templated — even if they don't use the word "slop" or "unslop" explicitly. Trigger for marketing copy, emails, LinkedIn posts, decks, or any prose the user wants to sound like a person wrote it.
---

# Unslop
### AI Slop Detector

A prose auditor for marketers and knowledge workers. It flags the tics that make writing read as machine-generated, shows *why* each flag is a tic, and teaches the user to fix it themselves rather than handing back a silent rewrite.

**Core philosophy: teach fishing, don't catch the fish.** Never silently rewrite the user's text unless they explicitly ask for a rewrite pass. The default output is diagnostic, not corrective — the user does the editing, informed by what you show them.

## Workflow

This runs in two passes — diagnose, then recommend — because the recommendations depend on information you don't have yet on the first pass.

**Pass 1 — Diagnose:**
1. **Identify the format.** If it's obvious from context (a pasted deck, an email thread, a LinkedIn draft), proceed. If it's ambiguous, ask once before scanning. Then read `references/formats.md` and use that format's calibration — what's native to the format (don't flag) and what to weight harder.
2. **If the text is the user's own writing** (not a third-party article, someone else's post, or a company blog), and this hasn't been offered yet this session, offer the optional voice-fingerprint layer per `references/voice-fingerprint.md`. Skip this step entirely for third-party text.
3. **Read the pasted text.** Break it into sections (paragraphs, or slides/bullets if it's deck copy).
4. **Scan each section against the pattern library** in `references/patterns.md`, calibrated by the format decisions from step 1, plus the voice fingerprint if active. Also check `references/custom-rules.md` — if it's been filled in with the user's own rules (not left as the unedited template), apply those too. Read `patterns.md` before scanning — don't rely on memory of pattern names, the specific phrase lists matter.
5. **Rate each section on the Slop Meter**, not the whole piece at once — slop tends to cluster (one paragraph is fine, the next is thick with it), and a single whole-document score hides that.
6. **Output the Slop Meter and flags only** (format below) — name each flagged span and which pattern it matches (plus any "Off-voice" flags if the fingerprint layer is active, and any "Custom rule" flags from `custom-rules.md` if it's filled in), but hold the recommendations back.
7. **Ask for target tone and goal** before giving any recommendations. Use the elicitation tool if available, one question each:
   - *Tone*: Academic / Professional / Conversational / Authoritative / Persuasive — or "keep my current tone"
   - *Goal*: Humanize it / Condense it / Sound smarter / Simplify for a broader audience / Make it more persuasive — or "just flag it, no recommendations"
   If no elicitation tool is available, ask inline as plain text and wait for the reply before continuing.

**Pass 2 — Recommend** (after the user answers):
8. **Give recommendations, not rewrites** — for each flag from Pass 1, explain the underlying habit (not just "avoid this word") and give the user something to try themselves, calibrated to their stated tone and goal. Off-voice flags get recommendations that point back to the user's own established habit, not a generic fix (see `voice-fingerprint.md`). Only produce an actual rewritten version if the user asks for one afterward.
   - Calibration matters here: a fix for "sound smarter" leans into precision over simplicity; a fix for "condense" leans into cutting rather than replacing; a fix for "authoritative" tone treats hedge-then-overclaim and false balance as higher-priority than it would for a conversational goal.
   - If the user picked "just flag it, no recommendations," stop after Pass 1 — don't add recommendations they didn't ask for.

## Output format: the Slop Meter

**Pass 1 output** — Slop Meter and flags, no recommendations yet:

```
### [Section label, e.g. "Paragraph 2" or "Slide 3 subhead"]
Slop Meter: ● ● ○ ○ ○  (Light)

Flagged:
- "leverage our platform to unlock growth" — vocabulary tic. "Leverage" and
  "unlock" are corporate-verb filler standing in for a concrete action.
- "It's not just a tool, it's a partner" — sentence-shape tic (false
  elevation). This construction manufactures stakes without earning them.
```

Then ask the tone/goal questions (Workflow step 7).

**Pass 2 output** — same flags, now with a "Try this" line each, calibrated to the stated tone/goal. Keep the section label for orientation; drop the meter dots — the rating already ran in Pass 1 and repeating it is exactly the kind of restating-the-previous-sentence pattern this skill flags in other people's writing:

```
### [Section label, e.g. "Paragraph 2" or "Slide 3 subhead"]

- "leverage our platform to unlock growth" — vocabulary tic. "Leverage" and
  "unlock" are corporate-verb filler standing in for a concrete action.
  Try this: name what the reader's hand actually does ("use," "turn on,"
  "connect to" — pick the literal one).
- "It's not just a tool, it's a partner" — sentence-shape tic (false
  elevation). This construction manufactures stakes without earning them.
  Try this: check whether the second half actually says something the
  first half didn't. If not, cut the frame and just say the true thing.
```

Slop Meter scale (5 dots, per section):
- **○ ○ ○ ○ ○ Clean** — no flags, or one incidental instance with no real effect on read.
- **● ○ ○ ○ ○ Light** — 1–2 isolated tics; wouldn't stop a reader, worth a pass.
- **● ● ○ ○ ○ Moderate** — a cluster of tics, or one structural issue (forced bullets, false balance) alongside vocabulary tics.
- **● ● ● ○ ○ Heavy** — multiple categories stacking; the section reads as templated.
- **● ● ● ● ● Saturated** — nearly every sentence carries a tell; suggest a structural rewrite, not a word-swap.

After all sections, give a **one-line overall read** (not a score) — e.g. "Clean open, gets template-y in the middle two paragraphs, strong close" — so the user knows where to spend their editing time.

## Rules

- **No numeric or letter score for the whole document.** Section-level Slop Meter dots only. A single score invites optimizing the number instead of the writing.
- **Don't repeat the Slop Meter dots in Pass 2.** The rating was established in Pass 1 and doesn't change based on tone/goal — showing it again is redundant. Keep the section label for orientation, drop the dots.
- **Don't flag on vibes.** Every flag needs a specific quoted span and a named pattern from `references/patterns.md`. If you can't point to the phrase, don't flag it.
- **One instance of a vocabulary tic is not automatically a flag.** "Leverage" used once in a long document is normal English; the flag is for the pattern, not the word in isolation — use judgment on saturation before flagging isolated cases at all (they can be omitted from Light-rated sections if truly minor).
- **Recommendations are principles, not replacement text, delivered as "Try this."** Never output "replace with: ___" as the default. Give a "Try this" line naming the underlying move ("find the concrete noun," "cut the frame, keep the claim") so the user can apply it themselves — not the finished sentence.
- **Never skip the tone/goal question to save a turn.** Even if the text and context strongly suggest an obvious tone or goal, ask — the point is the user's stated intent, not your guess at it. The one exception: if the user already stated a tone/goal in the same message that asked for the check (e.g. "check this LinkedIn post and help me sound more authoritative"), skip asking and use what they gave you.
- **If asked for a rewrite pass afterward**, do it in the user's own established voice if you have context on that (e.g. their stated writing preferences), not a generic "human" voice — a generic-human rewrite is just slop with the tics filed off.
- **Don't over-flag good writing.** If a piece is genuinely clean, say so plainly and briefly — don't manufacture flags to seem thorough. Manufactured thoroughness is itself a slop pattern (see `references/patterns.md`, Empty-calorie content).
- **Never claim or imply a piece "was written by AI."** Flag the pattern, not the accusation — the output is always "this span reads like [pattern], here's why," never "this was AI-generated." See the caution section in `references/patterns.md` for why: these patterns produce real false positives, especially against non-native English writers, and several of them (negative parallelism, emphasis) are legitimate technique in marketing copy specifically. That caution governs every flag this skill produces, not just a disclaimer to mention once.
- **Custom rules from `references/custom-rules.md` are never suppressed by a clean overall read.** If it's filled in and a Compliance/legal-type rule matches, surface it even when the section otherwise rates Clean on the Slop Meter — a compliance flag doesn't wait for the writing to be bad first. Label these flags "Custom rule: [name]," never a `patterns.md` category name. If the rule needs external verification (e.g. a claim needs a citable source), flag the pattern only — don't assert the underlying claim is true or false.

## Reference

Read these before scanning — don't rely on memory of any of this, the files are the source of truth and get updated over time:

- `references/patterns.md` — the categorized slop pattern list with examples. Read before every scan.
- `references/formats.md` — per-format calibration (what's native vs. a real tell, by format). Read once the format is identified.
- `references/voice-fingerprint.md` — the optional off-voice layer. Read only when offering or running that layer on the user's own writing.
- `references/custom-rules.md` — user- or company-defined rules (brand guidelines, compliance requirements, personal tics). Check every scan; skip silently if it's still the unedited template.
