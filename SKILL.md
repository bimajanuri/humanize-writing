---
name: humanize-writing
description: |
  Rewrites, paraphrases, and "humanizes" text so it no longer reads as AI-generated output. Works on both **Bahasa Indonesia** and **English** input (auto-detected, or user-specified). Use this skill when the user asks to: paraphrase a text, rewrite/rephrase an essay or article, humanize AI-generated writing, remove AI traces / AI patterns, make text sound natural or written by a real person, pass AI detectors, remove "AI slop", check or fix EYD/PUEBI (Bahasa Indonesia) or English grammar, fact-check or de-hallucinate a draft, reduce buzzwords and clichés, adjust register/tone, or shorten/bloat-fix text, or apply a named writing style in FULL mode (Formal, Akademik, Profesional, Kasual, Diplomatis, Sekolah, Simple, Percaya Diri, Marketing). Trigger phrases: "paraphrase", "parafrase", "rephrase", "rewrite", "humanize", "humaniser", "buat manusiawi", "hilangkan jejak AI", "agar tidak terdeteksi AI", "anti AI", "detektor AI", "AI slop", "hapus slop", "tulis ulang", "natural-kan", "cek EYD", "cek tata bahasa", "grammar check", "periksa ejaan", "PUEBI", "KBBI", "anti halusinasi", "cek fakta", "fact check", "hapus halusinasi", "buzzword", " cliché", "tone", "register", "singkat lebih pendek", "buat lebih ringkas", "gaya penulisan", "gaya formal", "gaya kasual", "tulis dengan gaya", "percaya diri", "persuasif". Capabilities: 6-mode router (Paraphrase / Humanize / Anti-Slop / De-Hallucinate / Grammar-EYD / Full Rewrite), 25+ AI-pattern detection (EN & ID lexicons), meaning-preservation gate, fact-grounding protocol, language-specific grammar engines (EYD 2022/PUEBI + KBBI for ID; US/UK register for EN; foreign/English terms preserved untranslated in ID text), 9 FULL-mode style presets (Formal, Akademik, Profesional, Kasual, Diplomatis, Sekolah, Simple, Percaya Diri, Marketing), and a scored before/after audit report.
---

# Humanize Writing

A **rewriting engine** that transforms AI-flavored text (Bahasa Indonesia or English) into natural, human-sounding prose — **without changing the author's meaning** and **without inventing new facts**. Working instructions are in English (so any Gen AI can use them); both input languages are fully supported, and output stays in the input language unless the user asks for a translation.

## Attribution

This skill adapts and expands on:
- **blader/humanizer** — the 25 AI-writing patterns (EN) used as the detection baseline
- **EYD 2022 / PUEBI & KBBI** — Bahasa Indonesia orthography and dictionary standards
- Standard copy-editing practice (Chicago / APA house style for EN; registered style guides for ID)

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
| **FULL** Full Rewrite | default / "make this not look like AI at all" | All of the above, in pipeline order (see `core/workflow.md`) + one style preset from `references/style-presets.md` |

**Language routing**: auto-detect the input language (ID vs EN). Mixed-language inputs are handled per-segment. For every language-specific file use the matching variant: `<lang>` = `id` or `en`. If detection is uncertain, ask one short question rather than guessing.

---

## STYLE PRESETS (FULL mode)

FULL mode locks **one** style preset before rewriting. Definitions, per-style examples (ID & EN), and AI-tell watchlists live in `references/style-presets.md`:

**Formal · Akademik · Profesional · Kasual · Diplomatis · Sekolah · Simple · Percaya Diri · Marketing**

- User names a style → use it. Context unambiguous (thesis → Akademik; office email → Profesional; landing page → Marketing) → infer and state it in the change log. Otherwise ask ONE short question with 2–3 best-fit options.
- Never mix two presets in one text; "formal tapi santai" maps to the nearest preset (Profesional), noted as a blend.
- Presets shape *how* things are said — meaning lock, anti-hallucination, and grammar gates still constrain *what* is said. **Percaya Diri / Marketing never license invented claims or fake proof.**

---

## MANDATORY LOAD ORDER

1. `SKILL.md` (this file) — pick the mode.
2. `core/workflow.md` — the pipeline stages and quality gates.
3. `core/language-router.md` — ID vs EN handling rules.
4. The protocol(s) for your mode (table above).
5. `checklists/final-audit.md` — run before delivering ANY rewrite.
6. `templates/report.md` — format of the deliverable (when the user wants a report; otherwise deliver clean text only).

> **Do not skip the final audit.** The audit catches meaning drift, residual AI patterns, and grammar regressions — the three ways rewrites fail.

---

## QUICK START (what to actually do)

1. Detect language → set `<lang>`.
2. Lock the **meaning inventory**: list every factual claim, number, name, and entity in the source. This is the contract the rewrite must honor (`core/workflow.md`, Stage 0). In FULL mode also lock the **style preset** — Formal, Akademik, Profesional, Kasual, Diplomatis, Sekolah, Simple, Percaya Diri, Marketing (`references/style-presets.md`).
3. Run the mode protocol(s).
4. Self-audit with `checklists/final-audit.md`: (a) meaning preserved? (b) AI patterns gone? (c) grammar clean? (d) register right?
5. Deliver. If the user asked for a report, use `templates/report.md`; otherwise output the rewritten text plus at most 3–5 short notes about notable changes (never chatbot-residue phrasing like "Here's your rewritten text!").

---

## OUTPUT LANGUAGE RULES

- Input ID → output ID (unless user asks for EN).
- Input EN → output EN (preserve the user's regional register if stated; default US).
- ID↔EN translation requests: translate **and** humanize in one pass, but treat translation as high hallucination risk (`protocols/anti-hallucination.md` §4 — translate only what is asserted; do not "improve" facts).
