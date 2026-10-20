# Protocol — De-Hallucinate / Fact-Grounding (FACT)

Goal: ensure the rewrite contains **no claims the source doesn't contain and no claims that aren't true**. Hallucination enters rewrites through two doors: *drift* (the rewrite says something the source didn't) and *fabrication* (the rewrite says something plausible but unverified).

This protocol is mandatory inside FULL mode, and is the whole job in FACT mode.

---

## 1. Claim extraction (the Stage 0 inventory, done rigorously)

Extract from the source, per sentence:
- **Atomic claims** — split compound sentences into individual assertions.
- **Type**: fact / number / attribution / quote / causal claim / prediction / opinion.
- **Modality & scope**: certain, likely, possible, alleged; universal ("always"), typical ("often"), rare ("sometimes").
- **Provenance**: is the claim attributed to a source in the text, or asserted by the author?

The rewrite must map 1:1 onto this set. Extra claim = hallucination. Missing claim = silent censorship (also a violation — report it instead of dropping it).

## 2. Verification pass (FACT mode; spot-check in FULL)

For each claim, classify:

| Class | Definition | Action |
|-------|-----------|--------|
| **V1 Verifiable & verified** | True to the best of available checkable knowledge (well-established facts, verifiable numbers/dates/names) | Keep |
| **V2 Verifiable & suspicious** | Conflicts with established knowledge, misattributed quote, improbable statistic, garbled name, wrong date | **Flag, do not silently fix or propagate** — see §5 |
| **V3 Unverifiable** | Plausible but checkable in principle (private claims, "a study shows", niche stats) | Preserve with attribution intact; note uncertainty if the text asserts it strongly without a source |
| **V4 Source-relative** | True only relative to the user's own material (their data, their experience, their draft's claims) | Preserve as the user's claim; never "correct" it from model knowledge |
| **V5 Opinion/prediction** | Not fact-apt | Preserve modality; never upgrade to fact |

Rules:
- Use **web search** when available and the claim is material (V2 candidates especially). When searching: prefer primary sources; treat search snippets as leads, not proof; require the claim to be *directly supported* by the source you read.
- Do not verify trivia the user clearly owns (their name, their project details) — V4.
- Never "verify" by pattern-matching your own memory for statistics; memory is the hallucination source. Established-general knowledge (capital cities, WWII dates, basic science) is fine from memory; specific numbers, quotes, study results, and recent events are not.

## 3. The invention boundary (what rewriters may NOT add)

Rewriting may reorganize, compress, clarify, and exemplify **only from given material**. Specifically forbidden:
- Inventing statistics, percentages, sample sizes, dates, URLs, DOIs.
- Inventing quotes or attributions ("as Einstein said" — if not in the source and not verifiably real).
- Inventing examples, anecdotes, case studies, user names, place names.
- Upgrading hedged claims while "clarifying" ("may contribute" → "contributes").
- Adding background "context facts" that sound helpful ("this is consistent with the UN SDGs") unless the user provided them.

Allowed additions that are **not** factual claims: transitions, definitions of established terms, restatements, clearly-marked hypotheticals ("misalnya, anggap saja...", "for instance, imagine..."), and meta-notes to the user.

## 4. Translation & paraphrase risk map

Highest hallucination risk moments (slow down here):
1. **Numbers and units** during any transformation — copy exactly, check once more at Stage 5.
2. **Names and titles** — never "normalize" a name into a more common spelling.
3. **Direction of causality** — "X causes Y" vs "Y is associated with X" must not flip.
4. **Comparatives and superlatives** — "one of the largest" ≠ "the largest".
5. **Negations** — the single most common silent drift; verify every negative sentence survived as negative.
6. **Dates and sequences** — "since 2015" vs "after 2015" vs "by 2015".
7. **Translation**: vague source → confident target. Keep vagueness ("beberapa" → "some", not "most").

## 5. Flagging protocol (when the source itself is wrong)

Do NOT silently propagate a suspicious claim, and do NOT silently "correct" it (you might be the one who's wrong). Instead:
1. Keep the rewrite faithful to the user's meaning.
2. Attach a numbered flag note under the output:
   > ⚠️ Flag 1 (paragraph X): "…" — this [misattributes X to Y / conflicts with (source) / states a number I could not verify]. Suggest: verify, soften, or remove.
3. Offer the softened wording as an option ("menurut sebagian peneliti" / "according to some researchers") — but let the user decide; do not apply silently.
4. Never add a fake citation to make a flagged claim look sourced.

## 6. Self-check before delivery (FACT gate)

- [ ] Every claim in the rewrite exists in the source or is verified.
- [ ] Every claim in the source survived (nothing silently dropped).
- [ ] Modality/scope/negation preserved 1:1.
- [ ] Numbers, names, dates copied exactly.
- [ ] All flags listed, none silently patched.
- [ ] No added "helpful context" that constitutes a new claim.
