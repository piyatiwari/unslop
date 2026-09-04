# Format Calibration

The pattern library in `patterns.md` is format-agnostic, but the same feature reads differently depending on genre — bullets are a violation in a narrative doc and the native format on a slide. Use this file to decide what to skip and what to weight harder for the format at hand.

**If the format isn't obvious from context, ask once before scanning** ("Is this an email, a LinkedIn post, something else?") rather than guessing and miscalibrating the whole pass.

---

## Email

- **Native (skip):** greeting/sign-off conventions, moderate hedging on asks ("if you have a moment"), short paragraphs.
- **Still a tell:** vocabulary tics, forced bullet-ification of what could be a single-sentence ask.
- **Extra tell specific to this format:** the "I hope this email finds you well" family of openers — a generic-scene-setting tell unique to email, flag it even though it's not in the base pattern list by name.

## Slack / Teams (chat)

- **Native (skip):** sentence fragments, lowercase starts, minimal punctuation, no sign-off, brevity in general.
- **Still a tell:** vocabulary tics, filler transitions.
- **Extra tell — direction reverses here:** an unusually polished, multi-paragraph, header-and-bullet message in a chat thread is itself the tell. Over-formality is the AI signature in this format, the opposite of most others.

## LinkedIn / social post

- **Native (skip):** short punchy lines, one-line paragraphs, line breaks used for rhythm.
- **Weight harder here:** "It's not just X, it's Y" — this is the signature LinkedIn tic, treat it as a bigger deal than the default severity. Same for the "I used to think X. Then Y happened." hook-and-turn template when it feels templated rather than earned.

## Exec summary / one-pager

- **Native (skip):** front-loaded conclusion, dense bullets, minimal narrative scaffolding — bullets are correct here, don't flag them as genre mismatch.
- **Still a tell:** vocabulary tics, empty transitions, rule-of-three section headers imposed for symmetry rather than content.

## PRD / spec / PRFAQ (Amazon narrative style)

- **Native (skip):** continuous narrative prose, precise technical or business terms, first-person plural voice ("we believe").
- **Weight harder here:** forced bullet-ification is a bigger deal in this format — bullets are often a genre violation here, not just a stylistic tic, since the format's whole discipline is forcing complete argument through prose. Marketing vocabulary tics ("unlock," "seamless") read as more out of place here than in a blog post. Hedge-then-overclaim is worse here too — precision is the format's entire point, so an unresolved hedge undermines it more than elsewhere.

## Slide deck — on-slide bullets vs. speaker notes

Treat these as two different formats within one file, per section:

- **On-slide bullets, native (skip):** fragments, terse noun phrases, no requirement for full sentences, parallel structure across bullets.
- **On-slide bullets, still a tell:** vocabulary tics, vague aphoristic epigraph-style quotes (abstract metaphor with no concrete image — "clarity emerges from the shadows of..." is the shape to watch for), rule-of-three headers used purely for visual symmetry.
- **Speaker notes:** much closer to natural prose — score these against the base pattern library normally, without bullet-related exemptions.

## Blog / thought-leadership article

- **Native (skip):** longer narrative arcs, first-person voice, some scene-setting if it's specific to the actual argument.
- **Weight harder here:** generic (non-specific) scene-setting in the opening line — "In today's fast-paced digital landscape..." is a much bigger tell in a blog opener than buried mid-document. "In conclusion" wrap-ups and a header on every paragraph are also stronger tells here, since long-form is exactly where genuine structure (vs. templated structure) should show.

## Press release

- **Native (skip):** a quote-driven structure ("said [Name], [Title] at [Company]") is genre-correct even if the quote itself reads a little stock — don't flag the form. Standard closing "About [Company]" boilerplate is a real convention, not slop.
- **Still a tell:** vocabulary tics in the body copy, and unsupported validation claims ("customers love X") with no name, number, or quote behind them.

## Performance review / peer feedback

- **Weight harder here:** hedge-then-overclaim and empty-calorie filler are worse in this format than the default severity — "consistently exceeds expectations" or "continues to be a valuable team member" with zero concrete example attached is the single most common and most damaging tell in this genre, because the entire value of the document is the specific evidence, not the verdict.
- **Extra tell specific to this format:** praise or critique with no example attached at all — flag this even when no named pattern from `patterns.md` technically matches; the absence of specificity is itself the tell here.

## Proposal / RFP response

- **Native (skip):** formal register, structured sections, echoing the client's own stated language back to them (a legitimate technique, not a tell).
- **Still a tell:** vocabulary tics, "we are committed to excellence" boilerplate, and rule-of-three feature lists that are generic rather than tied to something the client specifically asked for.

## Meeting notes / recap

- **Native (skip):** fragments, terse action-item attribution ("Sam: follow up by Friday"), bullet format throughout.
- **Extra tell specific to this format, direction reverses:** an over-narrated recap that turns terse notes into flowing marketing-style prose is itself the tell — same over-formality mismatch as the Slack entry above.
