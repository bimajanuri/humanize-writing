# Language Router — Bahasa Indonesia vs English

Every file with a `<lang>` placeholder resolves to `id` or `en`. This file defines what changes per language and the rules for mixed input.

---

## 1. Detection

- Default: detect from the source text (function words are decisive: "yang, dan, di, ke, dari, untuk" → ID; "the, and, of, to, in" → EN).
- Mixed-language documents (common in Indonesian academic/corporate writing with English terms): process **segment-by-segment**, keep established English technical terms as-is inside ID prose (do not translate terms like "machine learning", "brand awareness", "supply chain" unless the user asks).
- If unsure → ask one question. Do not machine-guess a language-specific grammar pass.

## 2. What differs per language

| Aspect | `id` (Bahasa Indonesia) | `en` (English) |
|--------|-------------------------|----------------|
| AI-pattern lexicon | `references/ai-lexicon-id.md` | `references/ai-lexicon-en.md` |
| Humanizer protocol | `protocols/humanizer-id.md` | `protocols/humanizer-en.md` |
| Grammar authority | EYD 2022 / PUEBI + KBBI | House style (US default; UK opt-in) |
| Common AI tells | Formulaic essay scaffolds, "Tak dapat dipungkiri", inflated "sangat penting", stilted formalisms, English-syntax calques | "Delve", triads, "not just X but Y", em-dash overuse, empty openers |
| Register range | Formal (baku), semi-formal, casual/santai — must choose consciously; default semi-formal for general prose | Formal / neutral / conversational — default neutral |
| Mechanics | EYD 2022 rules (see `protocols/grammar-id.md`) | Spelling register (US/UK) consistency, serial comma policy |

> Register/style selection (the 9 FULL-mode presets: Formal, Academic, Professional, Casual, Diplomatic, Educational, Simple, Confident, Marketing) is defined in `references/style-presets.md`. Indonesian aliases are accepted. The preset decides register; this file decides language mechanics. Istilah asing/Inggris in ID text stay as-is — never translated (`protocols/grammar-id.md` §3.1).

## 3. Indonesian-specific rewrite rules

- **Do not "fix" meaning by translating to English patterns.** The most common cause of robotic Indonesian prose is syntactic calquing from English ("Hal ini memainkan peran penting dalam..." ← "plays a crucial role in"). Rewrite with natural Indonesian voice: "Ini penting karena...", "Peran X dalam Y terlihat dari...", etc.
- **Keep baku/non-baku intentional**: casual blog text may use "enggak, nggak, kayak" — a formal paper must not. Ask before downgrading formality of an academic text.
- **Avoid both extremes**: neither stiff bureaucratic Indonesian ("Berdasarkan hal tersebut di atas, penulis bermaksud untuk...") nor forced slang. Human writing in ID tends to be direct, uses concrete verbs, and mixes sentence lengths.
- **Loanwords**: keep standard adopted terms (aplikasi, data, riset) per KBBI/usage; do not invent "Indonesian-ized" versions of technical terms, and do not replace them with English either — keep what the author used.

## 4. English-specific rewrite rules

- Fix register consistency: do not mix US/UK spelling (`analyze` vs `analyse`) — default US.
- Avoid anglicism-free zones: if the user writes ID→EN translated prose, strip ID syntax (see `protocols/grammar-en.md` §6 translationese markers).
- Preserve the author's idiom level: American conversational, British formal, international academic — match what exists, do not homogenize to one "AI neutral".

## 5. Mixed-language and translation requests

- Translation + humanization = one pass, but the **meaning inventory (Stage 0) is built on the source language** and checked against the output.
- Never "improve" facts during translation (a classic hallucination vector: vague source → confident target).
- Keep proper nouns, citations, and defined terms identical across languages unless asked.
