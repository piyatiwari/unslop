# Voice Fingerprint (optional layer)

An opt-in second layer on top of the core pattern-library check. Where `patterns.md` catches generic AI tells, this catches "doesn't sound like *this specific person*" — which is a different, narrower, and more useful signal when the text is the user's own draft.

## When to offer it

Offer once per session, and only when both are true:
- The text being checked is the user's own writing (a draft, an email they're sending, their own post) — **not** a third-party article, someone else's post, or a company blog they're just curious about.
- It hasn't already been offered and answered this session.

Ask plainly: something like "Want me to also flag anything that doesn't sound like *you* specifically, on top of the generic slop check? I can build a quick fingerprint from a writing sample, or from what I've already seen you write in this conversation."

**Never offer it on third-party text.** A voice fingerprint compares against the user's voice — there's nothing to compare when the text isn't theirs. If the user declines or the text isn't theirs, proceed with the pattern-library check alone and don't ask again this session.

## Building the fingerprint

Build it only from what's actually observable — either a sample the user pastes for this purpose, or writing they've produced earlier in the same conversation. Never invent traits or infer psychological characteristics from them. Note concrete, describable habits only:

- Typical sentence length and rhythm (short and declarative vs. long and compound)
- Hedge usage (do they hedge honestly, or avoid hedging entirely?)
- Contraction use
- Humor, asides, or self-deprecation
- Paragraph length and structure
- Vocabulary register (plain vs. elevated; technical vs. general)
- Punctuation habits (em-dashes, semicolons, sentence fragments used deliberately)

If the user already has stated writing preferences on file (e.g. a general preference for short declarative sentences, honest hedges, no corporate padding), those can seed the fingerprint directly without needing a fresh sample — but confirm with the user that this is still their current voice before relying on it, since preferences can shift.

## Using it

During Pass 1, add a second, visually distinct flag category alongside the pattern-library flags:

```
Off-voice:
- [span] — doesn't match your established pattern of [specific trait, e.g.
  "short declarative sentences"]. This section runs long and compound where
  your other writing stays clipped.
```

Label these **"Off-voice"**, never a pattern name from `patterns.md` — they're personal deviations, not universal AI tells, and conflating the two would misrepresent a stylistic drift as a generic slop pattern.

## Rules

- Off-voice flags are always secondary. Never let them crowd out, replace, or outnumber the core pattern-library flags in the output.
- Never fabricate or assume a fingerprint. If there's no real sample and no prior writing in the conversation to draw from, say so and skip the layer rather than guessing.
- If the fingerprint and the pattern library disagree on a span (pattern library reads it as clean, but it's off-voice, or vice versa), report both — they're answering different questions and neither overrides the other.
- The Pass 2 "Try this" recommendations for an off-voice flag point back toward the user's own established habit, not toward a generic fix — e.g. "your own pattern here is X; this section drifted toward Y" rather than a universal principle.
