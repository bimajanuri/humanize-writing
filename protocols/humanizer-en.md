# Protocol — Humanize, English (HUM / en)

Goal: remove machine-writing signatures so the text reads as the work of a specific human writer. Detection baseline: blader/humanizer's 26 AI-writing patterns, extended with current tells and language-specific patterns. Full lexicon: `references/ai-lexicon-en.md`.

**Method rule**: every pattern is fixed by *rethinking the sentence*, never by swapping one flagged word for a fancier synonym. Word-swap humanizing is itself detectable and leaves the skeleton intact.

---

## 1. Pattern families (detect → fix)

### A. Staging & phrasing (fix on sight)

1. **"Not X, but Y"** — "It's not just a tool; it's a movement." → State what it is and what it does. (Some uses are legitimate contrast; flag only the performative kind.)
2. **One-line closers & dramatic fragments** — a short punchy sentence whose only job is drama at paragraph end. Merge it or cut it.
3. **Profound-sounding sayings** — "In the end, the journey is the destination"-class lines. Delete or replace with the concrete point.
4. **Staged run-up** — "It's not merely about X. It's about Y." → one sentence, direct.
5. **Arguing with no one** — "Some may think... but the reality is..." when nobody said that. Remove the phantom; make the claim.
6. **Rhetorical question → answer scaffolding** — "So what does this mean? It means..." → state it.

### B. Rhythm & syntax (cluster-level: fix when density is high)

7. **Forced triads** — three-item lists everywhere ("faster, cheaper, and smarter"). Keep the triad only when the content is genuinely three parallel things.
8. **Repeated sentence openings** — several consecutive sentences starting the same way ("This...", "The..."). Vary the spine.
9. **Em-dash as universal connector** — replace most dashes with periods, commas, parentheses, or rewording; keep at most occasional deliberate use.
10. **Stacked qualifiers** — "truly remarkable and genuinely important" → one honest word.
11. **Hyphenated adjective piles** — "time-tested, battle-hardened approaches" → plain description.
12. **Passive/subjectless haze** — "It is believed that..." → name the believer or drop the hedge.
13. **Uniform sentence length** — all sentences 18–24 words = machine rhythm. Introduce real variance (3-word and 40-word sentences are both fine when earned).

### C. Inflation & borrowed authority

14. **AI buzzwords** — delve, tapestry, testament, crucial, robust, leverage, multifaceted, nuanced, holistic, seamless, pivotal, vibrant, embark, unlock, elevate, foster, underscore, realm, landscape,abyrinth... (see lexicon). Replace with the specific thing you mean.
15. **Significance inflation** — "plays a vital role", "of paramount importance", "cannot be overstated" → state the actual magnitude.
16. **Vague association** — "related to", "connected to", "impacts" without mechanism → say *how*.
17. **Shallow -ing riders** — "Paving the way for tomorrow, X..." → make it a real clause or cut.
18. **Sales language** — "game-changing", "revolutionary", "must-have", "supercharge" → delete or ground.
19. **Borrowed authority** — "history teaches us", "experts agree", "studies show" (unnamed) → cite specifics or attribute to the evidence you actually have; if none, downgrade to personal/argued claim.
20. **Hedging avoidance of plain "is/are"** — "serves as", "functions as", "acts as" → "is" where true.

### D. Formatting tells

21. **Bold as decoration** — bolding random phrases mid-paragraph. Bold only true terms or remove.
22. **Decorative headings & emoji** — over-sectioned text, emoji bullets. Remove unless the venue is genuinely casual.
23. **Curly quotes / smart punctuation in code-ish contexts** — normalize where plain ASCII is expected.

### E. Chat/draft residue (delete entirely)

24. **Chatbot residue** — "I hope this helps!", "Certainly! Here's...", "Great question!", "As an AI language model...".
25. **Meta-writing about the text itself** — "Below is a comprehensive exploration of...", "This article will first discuss...", heading repeated as the first sentence.
26. **Knowledge-limit disclaimers & fake uncertainty** — "I cannot verify, but it is generally believed..." → verify or remove.
27. **Writing about a previous version** — "Certainly! Here is the revised version..." → delete.
28. **Writing for the wrong reader** — re-explaining background the reader already has or delaying the decision until after generic diagnosis → lead with the subject, decision, or consequence that this reader needs. Keep context only when it changes the reader's decision.

## 2. Density heuristic (how to decide what counts)

A single dash, one "crucial", or one triad is not a finding. Humanize when a pattern appears **repeatedly or in clusters**:
- ≥2 occurrences per page per pattern → fix all.
- ≥3 different pattern families present in one paragraph → rewrite the paragraph from the idea, not from the sentences.
- When in doubt, read the paragraph aloud: if it sounds like a keynote deck, rewrite.

## 3. What NOT to "humanize"

- Legitimate terminology of art ("robust standard errors", "crucial in this context" argued for) — precision beats detector-chasing.
- Author's deliberate style: if they like short sentences or long ones, keep their mode.
- Quotes, titles, names — never touched.
- Do not insert typos, filler ("like", "basically"), or slang to fake humanity. Human ≠ sloppy; the register must still fit the venue.
- Do not break grammatical correctness to look natural.

## 4. Voice reconstruction (when the source has no voice)

If the input is flat, formulaic AI prose with no detectable persona, assign one before rewriting:
1. Decide the implied reader (peer, client, general public) and purpose (inform, argue, teach).
2. Pick a voice consistent with that: e.g. "knowledgeable practitioner, direct, mildly informal, concrete".
3. Rewrite with that voice consistently — one coherent human beats a random texture mix.
4. State the chosen voice in one line in the change log if the user might disagree with it.

## 5. Verification pass

After rewriting, rescan the OUTPUT with the lexicon (`references/ai-lexicon-en.md`):
- Remaining flagged words must each be justified (term of art, quote, or the best available word).
- Check rhythm: paragraph-level variance in sentence length and openings.
- Check formatting tells (bold, headings, dashes) — these survive word-level editing most often.
- Check audience fit: the draft should reach the reader's actual need without repeating context already available in the surrounding conversation or document.
