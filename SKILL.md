---
name: humanize-writing
description: Rewrites, paraphrases, and humanizes Bahasa Indonesia or English text while preserving meaning and avoiding fabricated facts. Use when rewriting AI-flavored prose to sound natural, paraphrasing without altering claims, removing formulaic AI slop, checking EYD 2022 or English grammar, verifying factual grounding, formatting citations (APA 7, MLA 9, Turabian, Vancouver, Harvard, Chicago, IEEE), evaluating rewrite quality, or applying style presets (Formal, Academic, Professional, Casual, Diplomatic, Educational, Simple, Confident, Marketing).
---

# Humanize Writing

A **rewriting engine** that transforms AI-flavored text (Bahasa Indonesia or English) into natural, human-sounding prose — **without changing the author's meaning** and **without inventing new facts**. Working instructions are in English (so any Gen AI can use them); both input languages are fully supported, and output stays in the input language unless the user asks for a translation.

## Attribution

This skill adapts and expands on:
- **blader/humanizer** — the 26 AI-writing patterns used as the detection baseline
- **EYD 2022 / PUEBI & KBBI** — Bahasa Indonesia orthography and dictionary standards
- Standard copy-editing practice and citation normalization (APA 7, MLA 9, Turabian, Vancouver, Harvard, Chicago, and IEEE for EN; registered style guides for ID)
- **Ragas / DeepEval** — rubric-based evaluation, test cases, and regression thinking
- **Guardrails** — explicit input/output validation and failure handling
- **LanguageTool** — mechanical grammar and spelling checks when an external checker is available
- **Fabric** — composable, reusable task patterns

> **Non-negotiable constraints** (apply to every mode):
> 1. **Meaning preservation** — the rewrite must assert the same claims as the source, no more and no less. If a rewrite would add, drop, or soften a factual claim, it is a bug.
> 2. **No fabrication** — never add statistics, names, quotes, dates, studies, or citations that are not in the source or verifiably true. When in doubt, *flag* (see `protocols/anti-hallucination.md`), never invent.
> 3. **Register target** — output register defaults to: neutral-natural for ID, natural-formal or casual per request for EN. Academic-formal is opt-in, not default (over-formality is itself an AI tell).

---

## ROUTER — Choose the Mode FIRST

Pick the mode from the user's request before touching the text. If the request is ambiguous or asks for "everything", use **FULL** (the default pipeline).

| Mode | User intent (sample triggers) | Protocol to load |
|------|-------------------------------|------------------|
| **PARA** Paraphrase | "paraphrase", "parafrase", "rephrase", "rewrite this but keep the meaning", plagiarism-avoidance rewrites | `protocols/paraphrase.md` |
| **HUM** Humanize | "humanize", "make it sound human/natural", "remove AI traces", "pass detectors" | `protocols/humanizer-<lang>.md` + `references/ai-lexicon-<lang>.md` |
| **SLOP** Anti-Slop | "remove AI slop", "too generic/listicle/AI-typical content", "make it less formulaic" | `protocols/anti-slop.md` |
| **FACT** De-Hallucinate | "fact-check", "remove hallucinations", "is this true?", "ground this text" | `protocols/anti-hallucination.md` |
| **GRAM** Grammar/EYD | "cek EYD", "check grammar", "periksa ejaan", "fix punctuation/spelling" | `protocols/grammar-id.md` or `protocols/grammar-en.md` |
| **EVAL** Quality Evaluation | "evaluate this rewrite", "score quality", "compare versions", "uji kualitas" | `protocols/evaluation.md` + `references/evaluation-rubric.md` |
| **CITE** Citation Style | "format citations", "use APA 7", "convert to IEEE", "normalize references" | `protocols/citations.md` + `references/citation-styles.md` |
| **FULL** Full Rewrite | default / "make this not look like AI at all" | All of the above, in pipeline order (see `core/workflow.md`) + one style preset from `references/style-presets.md` |

**Language routing**: auto-detect the input language (ID vs EN). Mixed-language inputs are handled per-segment. For every language-specific file use the matching variant: `<lang>` = `id` or `en`. If detection is uncertain, ask one short question rather than guessing.

---

## STYLE PRESETS (FULL mode)

FULL mode locks **one** style preset before rewriting. Definitions, per-style examples (ID & EN), and AI-tell watchlists live in `references/style-presets.md`:

**Formal · Academic · Professional · Casual · Diplomatic · Educational · Simple · Confident · Marketing**

- User names a style → use it. Context unambiguous (thesis → Academic; office email → Professional; landing page → Marketing) → infer and state it in the change log. Indonesian aliases are accepted. Otherwise ask ONE short question with 2–3 best-fit options.
- Never mix two presets at once; "formal tapi santai" maps to the nearest preset (Professional), noted as a blend.
- Presets shape *how* things are said — meaning lock, anti-hallucination, and grammar gates still constrain *what* is said. **Confident / Marketing never license invented claims or fake proof.**

---

## MANDATORY LOAD ORDER

1. `SKILL.md` (this file) — pick the mode.
2. `core/workflow.md` — the pipeline stages and quality gates.
3. `core/language-router.md` — ID vs EN handling rules.
4. The protocol(s) for your mode (table above).
5. `protocols/guardrails.md` — validate every output before delivery.
6. `checklists/final-audit.md` — run before delivering ANY rewrite.
7. `references/citation-styles.md` — style rules when citation or reference formatting is requested.
8. `templates/report.md` — format of the deliverable (when the user wants a report; otherwise deliver clean text only).

> **Do not skip the final audit.** The audit catches meaning drift, residual AI patterns, and grammar regressions — the three ways rewrites fail.

---

## QUICK START (what to actually do)

Copy this checklist and track progress internally before delivering:

- [ ] **Step 1 — Detect language & mode**: Set `<lang>` (`id` or `en`) and pick the mode from the router table (`core/language-router.md`).
- [ ] **Step 2 — Lock meaning inventory & style preset**: List every factual claim, number, name, quote, modality, and entity in the source (`core/workflow.md`, Stage 0). In FULL mode, also lock one style preset (`references/style-presets.md`).
- [ ] **Step 3 — Run mode protocol(s)**: Apply the matching protocol(s) from `protocols/` and reference tables from `references/`.
- [ ] **Step 4 — Validate output guardrails**: Run `protocols/guardrails.md` to ensure zero claim additions/drops, zero modality drift, and exact literal-data parity.
- [ ] **Step 5 — Run final audit**: Verify all 5 gates in `checklists/final-audit.md` (meaning preserved, AI patterns gone, grammar clean, read-aloud flow, quality thresholds met).
- [ ] **Step 6 — Deliver**: If the user asked for a report, use `templates/report.md`; otherwise output clean rewritten text plus at most 3–5 short notes about notable changes.

---

## HANDLING MISSING OR AMBIGUOUS INFORMATION

- **Ambiguous mode**: Default to **FULL** mode unless a narrow task (like grammar-only or citation-only) is clearly requested.
- **Ambiguous style preset (in FULL mode)**: Infer from context when unambiguous (e.g., thesis → Academic; work email → Professional; landing page → Marketing) and note the choice in the change log. If genuinely ambiguous, ask ONE short question offering 2–3 best-fit options before rewriting.
- **Uncertain input language**: Ask one short question rather than guessing.
- **Missing citation metadata (in CITE mode)**: Never invent missing authors, dates, pages, DOIs, or URLs. Mark missing fields as `UNVERIFIED — check manually` (`protocols/citations.md`).
- **Unverifiable or suspicious source claims**: Do not silently delete or "fix" them with invented facts. Preserve the user's claim and attach a numbered `⚠️ Flag` note (`protocols/anti-hallucination.md` §5).

---

## COMMON MISTAKES TO AVOID

- **Synonym-swapping on an AI skeleton**: Keeping the same robotic sentence structure while swapping words. Fix by restructuring syntax and changing sentence boundaries (`protocols/paraphrase.md`).
- **Adding "helpful" context or examples**: Inventing statistics, examples, attributions, or background facts not in the source. Fix by strictly honoring the Stage 0 meaning inventory.
- **Modality or negation drift**: Turning "may reduce" into "reduces", "some" into "most", or dropping a negation. Fix by checking every claim against `protocols/guardrails.md`.
- **Translating established English technical terms in Indonesian prose**: Turning terms like *machine learning*, *supply chain*, or *user interface* into awkward literal Indonesian. Keep established foreign terms untranslated per `protocols/grammar-id.md` §3.1.
- **Chatbot residue in delivery**: Adding conversational filler like "Certainly! Here is your humanized text:" or "I hope this helps!". Deliver the text and factual notes only.

---

## OUTPUT LANGUAGE RULES

- Input ID → output ID (unless user asks for EN).
- Input EN → output EN (preserve the user's regional register if stated; default US).
- ID↔EN translation requests: translate **and** humanize in one pass, but treat translation as high hallucination risk (`protocols/anti-hallucination.md` §4 — translate only what is asserted; do not "improve" facts).
