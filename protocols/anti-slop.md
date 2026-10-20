# Protocol — Anti-Slop (SLOP)

Goal: remove **content-level** AI slop — the generic, formulaic, hollow layer that survives word-level humanizing. Slop is not about vocabulary; it is about *thought*. A text can have zero "delve" and still be pure slop.

Works on both languages; language-specific tells live in the lexicons.

---

## 1. What counts as slop

- **Formulaic skeleton**: hook → 3 bullets → tidy lesson → call to action. Or: definition → "important for several reasons" → list → conclusion that restates the list.
- **Everything is important, nothing is specific**: no numbers, no named cases, no failures, no trade-offs, no dates, no people.
- **Symmetry compulsion**: 3 points of equal length, every paragraph 4–5 sentences, intro and conclusion mirror each other. Humans don't write with a ruler.
- **False balance / both-sidesing**: "Both approaches have pros and cons" with no actual evaluation, when the evidence allows a position.
- **Hedging mush**: "can potentially help to some extent" — commit or state why you can't.
- **Cliché carrier waves**: "in today's fast-paced world", "at the end of the day", "knowledge is power", "change is the only constant".
- **Buzzword salad**: many admired nouns, no verbs that do work ("leverage synergies to drive holistic value").
- **Universal-applicability claims**: "this applies to everyone, in any field".
- **Neatness addiction**: every tension resolved, every section summarized, every implication drawn out. Real drafts leave some threads rough or explicitly open.
- **Audience-pleasing filler**: "whether you're a beginner or an expert..." / "simak sampai habis" padding.

## 2. Slop scan (run before the style pass)

Go paragraph by paragraph and ask:
1. Could this paragraph exist, nearly verbatim, in a thousand other articles on the topic? → slop.
2. Does it name anything concrete (case, number, person, place, failure)? → if no across the whole section, slop.
3. Is its job just transition or throat-clearing? → cut.
4. Would a person with firsthand experience write this sentence? If not, why not? (That gap is the slop.)

## 3. Fixes (content-level)

1. **Cut the scaffolding**: delete openers/closers that only perform introduction or conclusion.
2. **Replace generic with specific**: where the user's context provides specifics, use them. Where it does NOT, **do not invent them** — instead compress or cut the generic claim (see `anti-hallucination.md` §3 for the invention boundary).
3. **Break false symmetry**: merge two thin bullets; let one strong point take a full paragraph; delete the weakest point.
4. **Take positions**: where the source clearly leans, let it lean with stated reasons. Do not manufacture balance the author didn't intend.
5. **Commit or qualify honestly**: swap mush for either a claim with evidence or an explicit "we don't know because X".
6. **Add texture the author actually has**: opinions, edge cases, trade-offs, "this fails when..." — only from the user's provided context, never from your imagination.
7. **Allow imperfection**: keep a genuinely open question open; end some sections without a bow.

## 4. Boundaries

- **Never fill gaps with plausible invention.** If a specific example would fix a generic paragraph but none was given, either (a) ask the user for one, (b) use a clearly-marked hypothetical ("misalnya, bayangkan kasus X" / "for example, suppose X"), or (c) cut the paragraph.
- Format requirements override slop-fighting: if the venue demands a 5-point listicle, keep 5 points but make each earn its place.
- Do not turn argumentative texts into neutral reports or vice versa.

## 5. ID & EN slope notes

- **ID slop** often wears formal clothes: "Dalam konteks ini, penting untuk dipahami bahwa..." → potong pembuka, mulai dari pemahamannya langsung.
- **EN slop** often wears listicle clothes: "Here are 5 reasons why..." → state the reasons.
- Both: replace "X plays an important role in Y" / "X memegang peranan penting dalam Y" with the *actual role*, one clause long.
