# Final Audit — mandatory before delivering any rewrite

Run all five gates on the OUTPUT (not the input). A failed gate → fix and re-run the gate you failed. Deliver nothing until every gate passes or a justified exception is documented in the report.

---

## Gate 1 — Meaning preservation

Diff the rewrite against the Stage 0 meaning inventory, claim by claim:

- [ ] Every factual claim in the source appears in the rewrite (nothing silently dropped).
- [ ] No claim in the rewrite is absent from the source or unverified (nothing added).
- [ ] Modality preserved: may/might/is likely → same strength; "proves" did not sneak in.
- [ ] Scope preserved: some/most/all; one of/the; often/always.
- [ ] **Negations**: every negative sentence in the source is still negative (highest-frequency drift).
- [ ] Numbers, dates, units, names, titles copied exactly.
- [ ] Causality direction unchanged; correlations not upgraded to causes.
- [ ] Quotes still verbatim (or explicitly marked as paraphrase per user instruction).

## Gate 2 — AI patterns removed

Rescan the rewritten OUTPUT with the matching lexicon (`references/ai-lexicon-<lang>.md`):

- [ ] Lexicon density ≤ 2 hits/1000 words; every remaining hit justified (term of art / quote / best available word).
- [ ] No structural clusters: no repeated sentence openings, no triad compulsion, no uniform rhythm, no phantom-argument scaffolding.
- [ ] No chat residue, no meta-writing, no knowledge-limit disclaimers.
- [ ] Formatting: no decorative bold/emoji; dash usage modest; headings proportional to text length.
- [ ] Openers/closers: no template openers ("Dalam era..."/"In today's world..."), no meringkas-only closers.

## Gate 3 — Grammar clean (incl. regressions you introduced)

- [ ] Run the mechanical checklist of `protocols/grammar-<lang>.md` on the OUTPUT.
- [ ] Specifically re-check sentences you rewrote — edits introduce new errors more often than old ones.
- [ ] Register/spelling consistent throughout (US/UK; baku/non-baku ID).
- [ ] Punctuation style applied consistently (serial comma, quotes, dashes).

## Gate 4 — Read-aloud flow

- [ ] Read the whole text aloud (or simulate carefully): any stumble = rework that sentence.
- [ ] Rhythm variance present: some short sentences, some long; varied paragraph lengths; varied openings.
- [ ] Transitions are earned, not performative ("Moreover"-chains cut to what's needed).
- [ ] The text sounds like ONE consistent human with a point of view, not a texture mix.

## Gate 5 — AI-risk heuristic (regression check, not a guarantee)

Score proxies on the output (see lexicon §5 for thresholds):

- [ ] Lexicon density: low (0–2/1000w) or justified.
- [ ] Sentence-length variance: noticeably non-uniform (compute mentally or spot-check: are there both <8-word and >30-word sentences?).
- [ ] Perplexity proxy: enough rare/specific words, concrete nouns, and asymmetric constructions that a human reader would not call it "generic".
- [ ] Burstiness proxy: paragraph openings vary; no metronomic paragraph sizes.

> If Gate 5 flags risk but Gates 1–4 pass, prefer readability: a text optimized for detectors but awkward for humans is a failure. Note the tension in the report; do not degrade the text further.

---

## Sign-off

- Gates passed: 1 ☐ 2 ☐ 3 ☐ 4 ☐ 5 ☐
- Documented exceptions (with reason): ______
- Flags to user (hallucination suspects etc.): ______
