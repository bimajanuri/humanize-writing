# Protocol — Grammar & Mechanics, English (GRAM / en)

Authority: the user's declared house style; default **US English (Chicago/APA-compatible)**. UK/Australian/Canadian register is honored when requested or clearly established in the document. Style preferences are labeled "gaya/style"; only actual errors are labeled errors.

---

## 1. Workflow

1. Register lock: US or UK spelling + date/number formats — apply consistently.
2. Mechanical sweep (§2) — hunt known recurring error classes explicitly.
3. Grammar core (§3): agreement, tense, articles, pronouns, verbs.
4. Punctuation & mechanics (§4).
5. Word choice & usage (§5).
6. Consistency (§6).
7. Translationese pass if the text smells translated from ID (§7).
8. Grammar fixes must not alter claims (anti-hallucination applies: a "fix" that changes scope/negation is a bug).

## 2. Mechanical checklist (hunt these explicitly)

- [ ] Subject–verb agreement, including: collective nouns (US: usually singular: "the team is"); "each/every/neither/either + of + plural" → singular; "number/amount" vs "a number/amount"; inverted subjects ("There are several reasons"); intervening prepositional phrases ("The list of items is long").
- [ ] Pronoun–antecedent agreement and ambiguous "this/it/they" references.
- [ ] Verb tense consistency; sequence of tenses in reported speech.
- [ ] Articles: a/an/the/zero — missing article before plural generics; "a" vs "an" by sound ("a university", "an hour").
- [ ] Irregular verb confusion: affect/effect, lie/lay, rise/raise, fewer/less, farther/further, that/which (US restrictive "that"), who/whom in formal register.
- [ ] Double negatives; parallelism in lists and comparisons ("than me" vs "than I" — match register).
- [ ] Comma splice; fused sentences; missing comma after introductory clause/series.
- [ ] Serial (Oxford) comma: pick per house style, apply consistently (default: yes for US).
- [ ] Apostrophes: its/it's, their/there/they're, possessives of singular nouns ending in -s (style choice, consistent).
- [ ] Spelling register: -ize/-ise, -or/-our, -er/-re, -ll-/-l- (US: organize, color, center, traveled; UK: organise, colour, centre, travelled).
- [ ] Hyphenation of compound modifiers before nouns ("well-known author"); em dash vs en dash vs hyphen (US: spaced en dashes rare; unspaced em dashes common — keep modest, dashes are an AI tell).
- [ ] Quotation mark style (double US / single UK) and punctuation placement.

## 3. Grammar core (the usual suspects, fixed correctly)

- **Agreement**: verb agrees with the head subject, not the nearest noun.
- **Tense**: past narration stays past; findings/discussion present (academic convention).
- **Participles**: dangling modifiers ("Walking to the lab, the rain started" — who is walking?).
- **Comparatives**: "more better" ✗; "unique" takes no "very" in careful writing (style note, not error).
- **Split infinitives**: acceptable; do not un-split reflexively.
- **Prepositions**: "comprised of" (traditional objection; accept if house style permits), "different from/to" (US: from; UK: from/to both) — match register, label as style.

## 4. Punctuation & mechanics

- Comma usage: after long introductory elements; before coordinating conjunctions joining independent clauses; around nonrestrictive clauses; no comma between subject and verb or verb and object.
- Semicolon between closely related independent clauses; colon introduces what follows (no capital after colon mid-sentence in US style unless a full sentence follows).
- Dashes: at most sparing use; convert AI-pattern overuse to periods/commas during humanize passes (humanizer protocol §B9).
- Ellipsis: three dots with spaces in most US prose; avoid decorative trailing ellipses.
- Parentheses vs em dashes vs commas: pick by interruption strength; do not stack constructions.

## 5. Word choice & usage

- Homophones and near-homophones: their/there/they're, your/you're, affect/effect, principal/principle, complement/compliment, ensure/insure/assure, continuous/continual.
- Register-appropriate formality: don't "elevate" plain words gratuitously ("utilize" → "use" unless precision demands; "in order to" → "to").
- Redundancies: "very unique", "future plans", "end result", "free gift", "past history".
- False friends for ID speakers (see §7): "finally" ≠ "akhirnya" always; "eventually" ≠ "akhirnya"; "actual" ≠ "aktual/aktualnya".

## 6. Consistency

- One term per concept; consistent capitalization of defined terms; consistent spelling register; consistent number style (spell out 1–9 or not — house style); consistent date format; consistent title case vs sentence case for headings (pick per style, apply globally).

## 7. Translationese pass (ID→EN texts)

Common Indonesian-to-English transfer errors to hunt:
- Calqued phrases: "plays an important role in" for "memegang peranan penting", "can give an influence" for "dapat mempengaruhi", "conduct an analysis" for "melakukan analisis", "pay attention to" for "memperhatikan" (often just "consider").
- Missing articles everywhere (ID has none); overused "the" where ID "tersebut" was.
- Noun-stacked subjects ("The implementation of the utilization of technology...").
- "It can be said that..." / "Based on that..." openers.
- False friends above; "of course" for "tentu saja" (fine) vs "sekali" doubling ("very much very...").
- Wordy passives: "is done by the author" → "the author does".

## 8. Output format for GRAM mode

(a) corrected text; (b) compact change list by category (only meaningful corrections); (c) style-vs-error labels; (d) flags for doubtful items left as-is.

## 9. Optional LanguageTool pass

If a local LanguageTool CLI or HTTP server is available, use it only after this protocol's sweep. Review matches individually:

- accept clear spelling, agreement, punctuation, and repeated-word errors;
- reject suggestions that alter technical terms, names, quotes, modality, or the author's deliberate voice;
- label disputed suggestions as `style` or `flag`, never as mandatory grammar corrections;
- rerun the meaning and literal-data guardrails after accepted fixes.
