# humanize-writing

A rewriting engine that transforms AI-flavored text — **Bahasa Indonesia or English** — into natural, human-sounding prose. **Meaning-preserving** and **fact-grounding**: it never invents statistics, quotes, names, or citations, and it flags suspicious claims instead of silently propagating them.

> Working instructions are written in English so any Gen AI can use them; both input languages are fully supported, and output stays in the input language unless a translation is requested.

## What it does

| Capability | What you get |
|------------|--------------|
| **Paraphrase** | Multi-level rewriting (lexical, syntactic, sentence, discourse) with a claim-by-claim meaning lock |
| **Humanize** | Removes 25+ AI-writing patterns — EN lexicon (delve, tapestry, "plays a crucial role") and ID lexicon ("Tak dapat dipungkiri", "Dalam era globalisasi...", English-syntax calques) |
| **Anti-Slop** | Kills formulaic skeletons, false symmetry, generic claims, and template openers/closers |
| **De-Hallucinate** | 1:1 claim mapping, V1–V5 verification classes, flagging protocol for suspicious source claims |
| **Grammar / EYD** | EYD 2022/PUEBI + KBBI for ID (incl. foreign terms preserved untranslated); US/UK register for EN + translationese detection |
| **Full Rewrite** | All of the above as a 6-stage pipeline with a mandatory 5-gate final audit |

## Modes

Pick via triggers: paraphrase / parafrase · humanize / humanisasi / hilangkan jejak AI · AI slop · fact check / anti halusinasi / cek fakta · cek EYD / grammar check · default = FULL.

## Style presets (FULL mode)

One register is locked before rewriting:

**Formal · Akademik · Profesional · Kasual · Diplomatis · Sekolah · Simple · Percaya Diri · Marketing**

Presets shape *how* things are said — meaning lock and anti-hallucination still constrain *what* is said. Percaya Diri / Marketing never license invented claims or fake proof.

## Layout

```
humanize-writing/
├── SKILL.md                     ← router: language detection + mode selection + style presets
├── core/
│   ├── workflow.md              ← 6-stage pipeline (Meaning Lock → Diagnose → Content → Style → Grammar → Audit)
│   └── language-router.md       ← ID vs EN rules, calque detection
├── protocols/
│   ├── paraphrase.md            ← 4-level paraphrasing
│   ├── humanizer-en.md          ← 25+ AI patterns (blader/humanizer lineage), voice reconstruction
│   ├── humanizer-id.md          ← Indonesian AI tells: scaffolding, calques, basa-basi esai
│   ├── anti-slop.md             ← content-level slop removal
│   ├── anti-hallucination.md    ← claim inventory, verification classes, flagging
│   ├── grammar-id.md            ← EYD 2022/PUEBI + KBBI, §3.1 foreign terms stay untranslated
│   └── grammar-en.md            ← US/UK register, translationese (ID→EN)
├── references/
│   ├── ai-lexicon-en.md         ← EN AI word/structure lexicon + density scoring
│   ├── ai-lexicon-id.md         ← ID AI word/structure lexicon + density scoring
│   └── style-presets.md         ← 9 register presets with examples & watchlists
├── checklists/
│   └── final-audit.md           ← 5 mandatory gates: meaning, AI patterns, grammar, flow, AI-risk
└── templates/
    └── report.md                ← deliverable + change-log format
```

## Non-negotiable constraints

1. **Meaning preservation** — the rewrite asserts the same claims as the source, no more and no less.
2. **No fabrication** — no invented statistics, names, quotes, dates, studies, or citations. Suspicious claims are flagged, never silently "fixed" or propagated.
3. **Register target** — output stays in the input language; style is chosen per preset, not defaulted to over-formal AI prose.

## Install

Copy (or clone) this folder into your agent's skills directory — for Claude: `~/.claude/skills/humanize-writing/`.

## Attribution

Adapts and expands on [blader/humanizer](https://github.com/blader/humanizer) (25 AI-writing patterns), plus EYD 2022/PUEBI & KBBI for Bahasa Indonesia and standard copy-editing practice (Chicago/APA house style) for English.

---

*Instruksi dalam Bahasa Indonesia tersedia di dalam file tiap protokol (mis. `protocols/grammar-id.md` §3.1 untuk aturan istilah asing, dan `references/style-presets.md` untuk 9 gaya penulisan FULL mode).*
