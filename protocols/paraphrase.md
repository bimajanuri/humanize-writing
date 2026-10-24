# Protocol — Paraphrase (PARA)

Goal: restate the source with **different wording and structure, identical meaning**. Used alone (PARA mode) or inside FULL.

---

## 1. Paraphrase ≠ synonym swap

A real paraphrase changes the **architecture** of the expression at four levels. Apply at least two levels per passage:

| Level | Technique | Example (EN) | Contoh (ID) |
|-------|-----------|--------------|-------------|
| **Lexical** | Context-correct word replacement (not mechanical thesaurus) | "important" → "significant"/"consequential" depending on sense | "penting" → "krusial"/"menentukan"/"berdampak besar" |
| **Syntactic** | Restructure the sentence | Active ↔ passive; cleft sentences; clause reordering; nominalization ↔ verbalization | "Penelitian ini membuktikan bahwa X" ↔ "X terbukti lewat penelitian ini" |
| **Sentential** | Split long sentences / merge short ones; change sentence boundaries | One 40-word sentence → two sentences with different subjects | Satu kalimat panjang → dua kalimat dengan subjek berbeda |
| **Discourse** | Reorder paragraphs, change connectives, shift focus (topic-comment restructure) | "However, X" → "X, though, ..." / "Meskipun Y, X" → "X — meskipun Y" | Idem |

## 2. Mandatory constraints

1. **Preserve the meaning inventory** (workflow Stage 0): every claim, number, name, modality, and scope qualifier must survive. Run the guardrail check and Stage 6 audit.
2. **Never paraphrase**: proper nouns, defined technical terms, idioms whose literal paraphrase would break meaning, quotes, citation titles.
3. **Do not add or drop claims.** "Shorter" is only allowed if the user asks for compression — and then still no claim loss, only redundancy loss.
4. **Sense-check each replacement**: a thesaurus hit is not a paraphrase if the sense differs ("robust method" ≠ "angkuh metode" — pick by meaning, not dictionary adjacency).
5. **Register stays put** unless asked: do not make a casual text formal or vice versa during a plain paraphrase.

## 3. Procedure

1. Build the meaning inventory (Stage 0).
2. Segment the source into **idea units** (not sentences — one sentence often carries 2–3 units).
3. Rewrite each unit with a different dominant level than the source used (if source was nominal → make it verbal; if source was clause-chained → use prepositional phrases).
4. Re-sequence units if the logical order allows a different linear order (cause→effect vs effect→cause), keeping coherence.
5. Check against the inventory claim-by-claim (guardrail check and Stage 6 audit).
6. Read aloud: the result must sound like someone *saying the idea in their own words*, not like a puzzle assembled from parts.

## 4. Paraphrase quality bar

- **Fail**: "The utilization of technology is crucial for the enhancement of learning outcomes" ← reworded from a simple sentence; longer, vaguer, more nominal. This is *de*-humanization.
- **Pass**: "Students learn better when technology is used well" — same claim, different structure, plainer, tighter.

## 5. Plagiarism-avoidance use case

When paraphrasing to avoid text-matching (common academic request):
- Structure must differ, not just words: change the sentence spine and the ordering of ideas.
- **Citation duty stays with the author**: paraphrased ideas still need attribution. Add one neutral note when the source is academic and no citation is present: ideas from a source must be cited even when reworded. Never fabricate a citation to "complete" this.
- Do not paraphrase beyond recognition *and* claim it as original thought — that is patchwriting's mirror image; the goal is honest restatement.

## 6. ID-specific notes

- Avoid the English calque reflex: "melakukan analisis terhadap" → "menganalisis"; "memberikan dampak yang signifikan terhadap" → "berdampak signifikan pada"; "memiliki kemampuan untuk" → "mampu".
- Prefer strong Indonesian verbs over noun stacks: "melakukan pengamatan" → "mengamati"; "memberikan penjelasan" → "menjelaskan".
- Do not "paraphrase" baku terms into casual ones in academic text (or the reverse) — keep the register lane.

## 7. EN-specific notes

- Kill translationese if present: "conduct an analysis of" → "analyze"; "is able to" → "can"; "in order to" → "to".
- Do not inflate: "very unique", "highly significant" — pick one precise word.
- Keep the author's idiom: if they write "get" not "obtain", stay at that level unless register was the problem.
