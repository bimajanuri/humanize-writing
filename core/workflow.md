# Core Workflow — 6-Stage Rewriting Pipeline

Applies to every mode. Stages may be skipped only when the mode table says so (e.g. GRAM skips Stage 3). Order matters: meaning lock before style work, style work before grammar, grammar before final audit.

---

## Stage 0 — MEANING LOCK (mandatory, all modes)

Before rewriting anything, extract a **meaning inventory** from the source:

- **Factual claims**: every assertion that could be true or false (including implied claims).
- **Numbers & quantities**: exact values, dates, ranges, percentages.
- **Named entities**: people, orgs, products, places, works, technical terms.
- **Quotes**: verbatim passages and near-quotes.
- **Modality**: how strong each claim is (fact / likelihood / opinion / possibility). Rewrites must preserve modality — turning "may increase" into "increases" is hallucination.
- **Scope & hedging**: qualifiers like "some", "often", "in most cases" must survive.

This inventory is the **contract**. The final audit checks the rewrite against it claim-by-claim.

> If the source itself contains suspicious "facts" (unlikely statistics, misattributed quotes), do not silently propagate them — see Stage 2 / `protocols/anti-hallucination.md` §2 and flag to the user.

## Stage 1 — DIAGNOSE

Score the source before changing it (so the user sees what was wrong, and you know what to fix):

1. Language + register detection.
2. Run the detection pass for the active mode:
   - HUM/FULL: pattern scan using `references/ai-lexicon-<lang>.md` (count hits per category).
   - SLOP/FULL: structural scan (formulaic structure, symmetry, filler, false balance) per `protocols/anti-slop.md` §2.
   - FACT/FULL: claim verification pass per `protocols/anti-hallucination.md` §2.
   - GRAM: mechanical scan (spelling, punctuation, agreement) per `protocols/grammar-<lang>.md`.
3. Note the **author's voice** if any is detectable (sentence length habits, preferred connectives, humor, formality). Humanize *toward* that voice; if the text has no voice at all, establish a plausible target persona in one line (e.g. "educated professional writing for peers, mildly informal").
4. **Style target (FULL mode, or whenever a style is requested)**: lock ONE of the 9 presets from `references/style-presets.md` — **Formal, Akademik, Profesional, Kasual, Diplomatis, Sekolah, Simple, Percaya Diri, Marketing**. User names it → use it; context unambiguous → infer and state it in the change log; ambiguous → ask one short question. Never two presets at once. Presets shape *how* things are said — meaning lock and anti-hallucination still constrain *what* is said.

## Stage 2 — CONTENT PASS (SLOP + FACT)

Only for SLOP and FACT modes (and FULL):

- Restructure away from formulaic skeletons; break symmetry; cut filler and throat-clearing openers (`protocols/anti-slop.md`).
- Verify or quarantine unsupported claims (`protocols/anti-hallucination.md`). Anything unverifiable is either softened to match its true modality or flagged — never presented as more certain than it is, and never "fixed" by inventing a plausible replacement fact.

## Stage 3 — STYLE PASS (HUM + PARA)

- Apply the locked style preset (register, rhythm, voice) per `references/style-presets.md` — the preset shapes *how* things are said; meaning lock and anti-hallucination still constrain *what* is said.
- Paraphrase at **multiple levels**, not just synonyms: syntactic restructuring, clause reordering, voice changes, nominalization↔verbalization, sentence splitting/merging (`protocols/paraphrase.md` §2).
- Remove AI patterns by **rewriting the underlying thought**, not by synonym-swapping the symptom (`protocols/humanizer-<lang>.md`).
- Vary rhythm deliberately: mix short and long sentences; vary paragraph length; avoid repeated sentence openings.
- Preserve key terminology: do NOT paraphrase domain terms, names, or defined labels into synonyms. Paraphrasing "convolutional neural network" into "a kind of math-inspired network brain" is damage, not humanization.

## Stage 4 — LANGUAGE PASS (GRAM)

- Run the grammar protocol for the language: `protocols/grammar-<lang>.md`.
- Fix agreement, articles, prepositions, punctuation, spelling/register consistency.
- Mechanical sweep: hunt known recurring errors (see the "mechanical checklist" section in each grammar protocol).

## Stage 5 — FINAL AUDIT (mandatory, all modes)

Run `checklists/final-audit.md` end-to-end:

1. **Meaning**: diff the rewrite against the Stage 0 inventory. Every claim preserved; modality preserved; no additions.
2. **AI patterns**: re-scan the *output* (not the input) with the lexicon. Residual hits must be justified (e.g. a term of art).
3. **Grammar**: re-read for errors introduced by your own edits (the most common regression source).
4. **Flow**: read aloud test — any sentence the user would stumble on gets reworked.
5. **Detectors**: apply the AI-risk heuristic from `checklists/final-audit.md` §5 (perplexity/burstiness proxies) — not as a guarantee, only as a regression check.

## Stage 6 — DELIVER

- Default: clean rewritten text only, no commentary wrapper.
- If changes are extensive or the user asked, add a **short** change log (3–5 bullets, factual: e.g. "Removed 14 filler openers; converted 6 triads to natural lists; fixed 3 subject–verb agreement errors; flagged 1 unverifiable statistic — see note").
- If asked for a report: `templates/report.md`.
- Never include AI residue in the delivery itself: no "I hope this helps", no "Certainly!", no disclaimers about being an AI.

---

## Failure Modes to Avoid (meta)

| Failure | What it looks like | Fix |
|---------|-------------------|-----|
| Synonym-swapping | Same sentence skeleton, fancier words | Restructure syntax; change sentence boundaries |
| Over-humanizing | Slang/typos added to look authentic | Human ≠ sloppy; register must stay appropriate to purpose |
| Meaning drift | "may help" → "proves" | Check modality per claim in Stage 0/5 |
| Fabrication creep | Adding a plausible stat or example | Never add facts not in source or verifiable |
| Detector-chasing | Weird phrasing that scores well but reads badly | Readability wins; detectors are a heuristic, humans are the audience |
| Style flattening | Every sentence now medium-length and calm | Deliberate rhythm variation, not noise |
