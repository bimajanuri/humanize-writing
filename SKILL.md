---
name: humanize-writing
description: |
  Rewrites, paraphrases, and humanizes Bahasa Indonesia or English text while preserving meaning and avoiding fabricated facts. Supports paraphrase, humanize, anti-slop, de-hallucination/fact-grounding, grammar/EYD, citation-style normalization, evaluation, and full rewrite workflows. Use for natural rewrites, AI-pattern reduction, grammar checks, factual grounding, quality evaluation, shortening, tone/register changes, or named styles including Formal, Academic, Professional, Casual, Diplomatic, Educational, Simple, Confident, and Marketing. Includes language routing, claim guardrails, modular rewrite patterns, optional LanguageTool integration guidance, seven citation styles, evaluation rubrics, AI-pattern lexicons, and final audit gates.
compatibility: Agent Skills-compatible AI coding assistants and chat agents
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

1. Detect language → set `<lang>`.
2. Lock the **meaning inventory**: list every factual claim, number, name, and entity in the source. This is the contract the rewrite must honor (`core/workflow.md`, Stage 0). In FULL mode also lock the **style preset** — Formal, Academic, Professional, Casual, Diplomatic, Educational, Simple, Confident, Marketing (`references/style-presets.md`).
3. Run the mode protocol(s).
4. Apply the output guardrails in `protocols/guardrails.md`.
5. Self-audit with `checklists/final-audit.md`: (a) meaning preserved? (b) AI patterns gone? (c) grammar clean? (d) register right? (e) quality thresholds met?
6. Deliver. If the user asked for a report, use `templates/report.md`; otherwise output the rewritten text plus at most 3–5 short notes about notable changes (never chatbot-residue phrasing like "Here's your rewritten text!").

---

## OUTPUT LANGUAGE RULES

- Input ID → output ID (unless user asks for EN).
- Input EN → output EN (preserve the user's regional register if stated; default US).
- ID↔EN translation requests: translate **and** humanize in one pass, but treat translation as high hallucination risk (`protocols/anti-hallucination.md` §4 — translate only what is asserted; do not "improve" facts).
