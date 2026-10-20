# AI Lexicon & Tell-Signs — English

Detection aid, not a ban list. Context decides: a word is a finding only when it is (a) decorative/vague rather than precise, and (b) part of a pattern (≥2 per page or clustered). Never replace a precise term of art with a weaker word to satisfy this list.

---

## 1. High-signal vocabulary (AI-discriminative)

These words are heavily over-represented in LLM output. Each occurrence deserves scrutiny:

**Verbs**: delve, embark, unlock, leverage (verb), elevate, foster, underscore, navigate (figurative), harness, spearhead, revolutionize, streamline, curate (figurative), unpack, demystify, empower.

**Nouns**: tapestry, testament, realm, landscape (figurative), journey, synergy, paradigm, cornerstone, bedrock, treasure trove, game-changer, powerhouse, myriad, plethora.

**Adjectives**: crucial, vital, pivotal, robust, comprehensive, holistic, nuanced, multifaceted, intricate, vibrant, seamless, transformative, groundbreaking, cutting-edge, ever-evolving, dynamic, invaluable, remarkable, profound, comprehensive.

**Adverbs**: truly, genuinely, remarkably, profoundly, incredibly, seamlessly, deeply, vastly, notably, importantly (sentence-initial).

**Fixed phrases**: "plays a (crucial/vital/important) role in", "it's important to note that", "in today's (fast-paced/digital/ever-changing) world", "at the end of the day", "a testament to", "stands as a", "delve into", "in the realm of", "when it comes to", "the (key/tapestry/landscape) of", "not only... but also", "it's worth noting", "needless to say", "as an AI", "I hope this helps", "here's a (comprehensive/detailed) breakdown", "let's explore", " buckle up".

## 2. Structural tells (per paragraph)

- Sentence-initial: "Moreover", "Furthermore", "Additionally", "In conclusion", "Importantly", "Interestingly" — more than occasional use is a tell.
- "Not just X, but Y" / "It's not merely X — it's Y."
- Triads: three parallel adjectives/nouns/consequences with no content reason.
- Rhetorical question + immediate self-answer.
- "Whether you're a beginner or an expert...", "From X to Y" ranges ("From startups to enterprises").
- Every paragraph ends with a summarizing sentence.
- Uniform 18–24-word sentences; uniform paragraph length.
- Em dash as the default connector (2+ per paragraph).
- Colon-list scaffolding: "Three things matter: X, Y, and Z."

## 3. Formatting tells

- Bolded random phrases mid-paragraph; bold used for "emphasis".
- Emoji bullets or decorative section headers (in non-casual venues).
- Excessive H2/H3 nesting for a short text; every claim gets its own heading.
- Numbered lists where prose would do; lists of exactly 3 or 5 items repeatedly.

## 4. Chat residue (delete outright)

- "Certainly! / Sure thing! / Great question!"
- "Here is the rewritten version:"
- "As an AI language model, I..."
- "I cannot verify... but it is generally believed..."
- "Let me know if you'd like any changes!"
- Section written as "Revision 2", references to earlier drafts.

## 5. Density scoring (used by final audit)

Count per 1000 words:
- 0–2 lexicon hits, no structural clusters → low risk.
- 3–6 or one structural cluster → medium; humanize before delivery.
- 7+ or multiple families per paragraph → high; rewrite from ideas, not sentences.

**Caveat, always**: detectors are heuristics; a text can score clean and still read as AI (structural tells dominate), or score badly and read human. Optimize for the human reader first.
