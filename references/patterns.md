# AI Slop Pattern Library

Categorized tells for prose that reads as machine-generated. Each entry: the pattern, why it reads as slop, and an example. Use these to flag specific spans in `SKILL.md`'s workflow — don't flag on vibes, flag on a named pattern below.

Several patterns here (negative parallelism, em-dash overuse, actor-less constructions) draw on and use the terminology from Wikipedia's community-maintained essay [Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) — worth a read for anyone who wants the exhaustive version. See the caution at the end of this file before applying any of this mechanically, though; that essay is explicit that none of these patterns, alone or combined, proves a piece of text was AI-written.

---

## 1. Vocabulary tics

Words that function as filler verbs/adjectives — technically correct, but standing in for a concrete action or detail the writer didn't commit to.

**Words on the watch list:** leverage, unlock, elevate, seamless, robust, delve, foster, navigate (the landscape/complexity), streamline, empower, game-changer, cutting-edge, best-in-class, holistic, synergy, tapestry, landscape/ecosystem (as metaphor), transformative, journey (as metaphor for a process), utilize (instead of "use"), facilitate.

**This is a watch-list, not a ban-list.** These are also just the standard working vocabulary of B2B and enterprise tech — genuinely, correctly, used every day by huge numbers of people worldwide, including a large share of the global tech and GCC workforce for whom this is the register they learned English business writing in. Using "leverage" or "seamless" is not itself a sign of anything. The tell was never the word — it's the word *doing the job a concrete detail should be doing*. "We leverage our platform" said by someone who then names exactly what the platform does is not a flag. "We leverage our platform to unlock growth" with nothing underneath it is, because the words are covering for the absence of a real claim, not expressing a real one. Judge every instance against that test before flagging it, not against list membership alone.

**Why it's slop, when it is:** these words describe the *category* of benefit without specifying the *actual* benefit. "Leverage the platform to unlock growth" tells you nothing about what happens when someone clicks a button — the diagnosis is the missing specific, not the vocabulary choice.

**Flag threshold:** one instance in a long piece is normal English, not a flag, regardless of the writer's background. Flag when 2+ appear in close proximity *and* neither is doing real work (i.e., a concrete detail could replace it without changing the sentence's job), or when a sentence's only verb is one of these with nothing concrete elsewhere in it.

**Teaching question:** "Is there a concrete detail right here that this word is standing in for, or is the detail actually present and this word is just describing it accurately?" — only flag the former.

---

## 2. Sentence-shape tics

Structural templates that create false weight or false symmetry.

- **Negative parallelism (antithesis)** — "It's not just X, it's Y." Manufactures elevation without earning it. Flag whenever Y doesn't actually add new information over X. This is the most recognizable AI sentence-shape tic and has its own name in rhetoric (antithesis) — Wikipedia's AI-writing essay calls the "not only... but" / "not just... it's" family out specifically as one of the most common tells across AI-generated text.
- **Rule-of-three-itis** — always exactly three examples, three adjectives, three clauses, regardless of whether three is the right number. ("Fast, flexible, and future-proof.") Flag when the third item feels padded to complete the set.
- **Hedge-then-overclaim** — "While X is complex and nuanced, it's clear that Y" — the hedge does no real epistemic work, it's just throat-clearing before an assertion that isn't actually more clear for having been hedged first.
- **False balance** — "On one hand... on the other hand..." where both hands are actually the same hand, or the second isn't a real counterweight. Flag when the "tension" resolves to nothing.
- **Rhetorical question stacking** — "But what does this mean for you? And why does it matter now?" used as a transition instead of an actual transition.
- **Em-dash overuse** — reaching for an em dash where a comma or period would do, especially for punchy emphasis at the end of a sentence. One or two per long piece is a normal writer's habit; a dash in nearly every paragraph, especially stacked with other tics, is a tell. Note the em dash alone is weak evidence on its own — it's a stylistic habit some human writers genuinely have — so weight it only in combination with other flags in the same section, never as a standalone flag.
- **Actor-less constructions** — sentences where the object gets promoted to subject and nothing actually does anything: "the decision was made," "the shift is being felt across the industry," "growth is being driven by..." Different from ordinary passive voice (which at least implies an actor — "the lanes were closed" still has someone who closed them); this pattern removes the actor entirely. The cumulative effect is prose where things happen but nobody does them.

**Teaching question:** "Does the second half of this sentence say something the first half didn't?" / "If I cut the setup, does the claim still stand?" / "Who's the actual actor in this sentence — can I name them?"

---

## 3. Structural tics

Formatting and organizational patterns applied by default rather than because the content calls for them.

- **Forced bullet-ification** — turning a sentence that should just be a sentence into 3 bullets because bullets *look* organized. Flag when the bullets don't have parallel logical weight or could be one clause.
- **Unnecessary listing, more broadly** — beyond forcing things into exactly three (see rule-of-three-itis above), this is the wider tendency to listify content that was never a list — turning what should be a flowing paragraph into a bulleted enumeration just because a list scans as "organized" or "thorough." Flag when the list items don't have a genuine parallel relationship to each other, or when reading them as one sentence loses nothing.
- **Formatting overkill** — bolding so many terms that the page starts to look like a textbook glossary rather than prose someone wrote. If nearly every sentence has at least one bolded phrase, none of them are actually doing the job of emphasis anymore.
- **Header on every paragraph** — subheads used as scaffolding rather than navigation; if a reader wouldn't skip to that header, it's decoration.
- **"In conclusion" / "In summary" wrap-ups** — restating what a short piece just said, for a reader who just read it and doesn't need the recap.
- **Uniform section length** — every section is exactly 3 paragraphs / 5 bullets regardless of how much there actually was to say about that topic — a tell of generation-by-template rather than writing driven by the material.

**Teaching question:** "Would a reader actually skip to this header?" / "Do these bullets have the same logical weight, or did I just chop a sentence into pieces?"

---

## 4. Empty-calorie content

Passages that are grammatically fine and semantically thin — present tense, sound confident, add nothing.

- **Restating the previous sentence** — a second sentence that rephrases the first without adding new information, disguised as elaboration.
- **Filler transitions doing no logical work** — "Moreover," "Furthermore," "Additionally" used as connective tissue between two sentences that aren't actually building on each other.
- **Generic scene-setting** — "In today's fast-paced digital landscape, businesses are constantly seeking ways to..." — throat-clearing that could preface literally any topic, meaning it says nothing about this one.
- **Manufactured thoroughness** — padding a genuinely clean or simple piece with extra flags, caveats, or sections to *seem* rigorous. (Note: this is also a trap for the detector itself — see the rule in SKILL.md against over-flagging.)
- **Fake specificity** — invented statistics or suspiciously round confidence numbers ("73% of marketers agree...") with no source, used to simulate rigor.
- **Unearned significance tacking** — a plain factual statement gets an analytical phrase bolted onto the end to make it sound more important than it is: "...highlighting the platform's growing influence," "...underscoring a broader industry shift." The phrase adds no new information — it just tells the reader how to feel about the fact instead of trusting them to draw the conclusion themselves. Flag when the tacked-on phrase could be deleted without losing anything factual.

**Teaching question:** "If I deleted this sentence, would the reader lose information, or just words?"

---

## Caution: these patterns are not proof

Worth internalizing before applying any of this mechanically — this is Wikipedia's own stated position on its AI-writing essay, not just a house rule here: no single pattern, or even a combination of them, proves a piece of text was AI-written. A few concrete reasons to stay humble about this:

- **False positives concentrate on non-native English writers, and on standard professional register.** A Stanford study found AI-detection tools falsely flagged non-native English writers at a 61% rate. That risk shows up directly in this file's vocabulary list: words like "leverage," "unlock," and "seamless" are the ordinary working vocabulary of B2B and enterprise tech, used correctly and fluently by a huge global workforce — including much of the non-native-English tech and GCC workforce that learned business English through exactly this register. None of that is a tell on its own. See the vocabulary-tics section above for the actual test (is a concrete detail missing, or just described accurately) before flagging any instance.
- **These patterns can be legitimate technique, especially in marketing.** Wikipedia flags negative parallelism and "editorializing" partly because Wikipedia specifically requires neutral point of view. Marketing copy is supposed to have a point of view — mechanically stripping every instance of contrast or emphasis can gut the one sentence where the writer actually said something. Always weigh a flag against the format (`formats.md`) and the user's stated goal, not just the pattern match.
- **Detector accuracy collapses on lightly-edited text.** Independent research found automated AI detectors drop to roughly 26% accuracy on AI text that's been lightly paraphrased — meaning a human who edited an AI draft, or an AI-assisted human writer, can produce text these patterns under- or over-flag either direction.

Practically, this means: flag the pattern, not the accusation. The output of this skill is never "this was written by AI" — it's "this specific span reads like [pattern], here's why, here's what to try." That framing holds regardless of how the text was actually produced, which is the only claim this skill is actually in a position to make.

---

## Notes for future additions

This file is meant to grow. When a new tic gets flagged repeatedly by users and isn't captured by a category above, add it here with the same format: pattern → why it's slop → teaching question. Keep examples short and real-sounding rather than abstract.
