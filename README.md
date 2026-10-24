# Humanize Writing

A rewriting engine that transforms AI-flavored text — **Bahasa Indonesia or English** — into natural, human-sounding prose. **Meaning-preserving** and **fact-grounding**: it never invents statistics, quotes, names, or citations, and it flags suspicious claims instead of silently propagating them.

> Working instructions are written in English so any Gen AI can use them; both input languages are fully supported, and output stays in the input language unless a translation is requested.

## What it does

| Capability | What you get |
|------------|--------------|
| **Paraphrase** | Multi-level rewriting (lexical, syntactic, sentence, discourse) with a claim-by-claim meaning lock |
| **Humanize** | Removes 26 core AI-writing patterns plus language-specific tells — EN lexicon (delve, tapestry, "plays a crucial role") and ID lexicon ("Tak dapat dipungkiri", "Dalam era globalisasi...", English-syntax calques) |
| **Anti-Slop** | Kills formulaic skeletons, false symmetry, generic claims, and template openers/closers |
| **De-Hallucinate** | 1:1 claim mapping, V1–V5 verification classes, flagging protocol for suspicious source claims |
| **Grammar / EYD** | EYD 2022/PUEBI + KBBI for ID (incl. foreign terms preserved untranslated); US/UK register for EN + translationese detection |
| **Quality Evaluation** | Rubric-based scoring, claim-diff checks, pairwise comparison, and reusable regression cases |
| **Guardrails** | Explicit validators for claim preservation, modality, entities, quotations, formatting, and no-fabrication |
| **Full Rewrite** | All of the above as a 7-stage pipeline with mandatory guardrail and final-audit checks |

## Modes

Pick via triggers: paraphrase / parafrase · humanize / humanisasi / hilangkan jejak AI · AI slop · fact check / anti halusinasi / cek fakta · cek EYD / grammar check · evaluate / score / uji kualitas · default = FULL.

## Style presets (FULL mode)

One register is locked before rewriting:

**Formal · Academic · Professional · Casual · Diplomatic · Educational · Simple · Confident · Marketing**

Presets shape *how* things are said — meaning lock and anti-hallucination still constrain *what* is said. Confident / Marketing never license invented claims or fake proof. Indonesian aliases remain accepted.

## Layout

```
humanize-writing/
├── SKILL.md                     ← router: language detection + mode selection + style presets
├── core/
│   ├── workflow.md              ← 7-stage pipeline (Meaning Lock → Diagnose → Content → Style → Grammar → Guardrails → Audit)
│   └── language-router.md       ← ID vs EN rules, calque detection
├── protocols/
│   ├── paraphrase.md            ← 4-level paraphrasing
│   ├── humanizer-en.md          ← 25+ AI patterns (blader/humanizer lineage), voice reconstruction
│   ├── humanizer-id.md          ← Indonesian AI tells: scaffolding, calques, basa-basi esai
│   ├── anti-slop.md             ← content-level slop removal
│   ├── anti-hallucination.md    ← claim inventory, verification classes, flagging
│   ├── guardrails.md            ← deterministic output validators and failure actions
│   ├── evaluation.md            ← rubric, pairwise evaluation, and regression protocol
│   ├── patterns.md              ← composable rewrite patterns inspired by Fabric
│   ├── grammar-id.md            ← EYD 2022/PUEBI + KBBI, §3.1 foreign terms stay untranslated
│   └── grammar-en.md            ← US/UK register, translationese (ID→EN)
├── references/
│   ├── ai-lexicon-en.md         ← EN AI word/structure lexicon + density scoring
│   ├── ai-lexicon-id.md         ← ID AI word/structure lexicon + density scoring
│   └── style-presets.md         ← 9 register presets with examples & watchlists
│   └── evaluation-rubric.md     ← quality dimensions, scoring anchors, and thresholds
├── checklists/
│   └── final-audit.md           ← mandatory gates: meaning, AI patterns, grammar, flow, AI-risk, and guardrails
└── templates/
    └── report.md                ← deliverable + change-log format
```

## Non-negotiable constraints

1. **Meaning preservation** — the rewrite asserts the same claims as the source, no more and no less.
2. **No fabrication** — no invented statistics, names, quotes, dates, studies, or citations. Suspicious claims are flagged, never silently "fixed" or propagated.
3. **Register target** — output stays in the input language; style is chosen per preset, not defaulted to over-formal AI prose.

## Cross-platform installation and usage

This is a portable [Agent Skills](https://agentskills.io/) package. Keep the complete `humanize-writing/` directory, including `SKILL.md`, `core/`, `protocols/`, `references/`, `checklists/`, and `templates/`. Do not copy only `SKILL.md`; the main file references the supporting documents.

### Compatibility and prerequisites

| Platform | Native skill support | Recommended location | Minimum prerequisite | Activation and verification |
|---|---|---|---|---|
| Claude Code | Yes, Agent Skills standard | `.claude/skills/` or `~/.claude/skills/` | A current Claude Code release with custom skills enabled | `/humanize-writing`; run `/doctor` if discovery fails |
| OpenCode | Yes, Agent Skills standard | `.opencode/skills/`, `.claude/skills/`, or `.agents/skills/` | OpenCode with the `skill` tool enabled and permission not set to `deny` | Ask for `humanize-writing`; confirm it appears in the available skills |
| Gemini CLI | Yes, Agent Skills standard | `.gemini/skills/`, `~/.gemini/skills/`, or `.agents/skills/` | Gemini CLI with Agent Skills support | `/skills`; start a new session after installation |
| GitHub Copilot CLI | Yes, Agent Skills standard | `.github/skills/`, `~/.copilot/skills/`, or `.agents/skills/` | A current Copilot CLI with skills support | `/skills reload`, then `/skills info humanize-writing` |
| Google Antigravity App/CLI/IDE | Yes, Agent Skills standard | `.agents/skills/` or `~/.gemini/config/skills/` | An Antigravity surface with Agent Skills enabled | Reload the workspace; use `/humanize-writing` or natural language |
| ChatGPT | Conditional, product/workspace feature | Uploaded ZIP through Skills UI | Eligible Business, Enterprise, Healthcare, or Edu workspace with Skills and upload permissions | Upload, enable, then ask ChatGPT to use the skill |
| Other compatible agents | Depends on implementation | `.agents/skills/` or documented platform path | Agent Skills discovery and Markdown resource access | Follow the host's reload/list command |

The skill itself has no runtime package, API key, database, or operating-system-specific dependency. All rewriting, guardrails, and evaluation procedures are instruction-driven. LanguageTool, web access, and external evaluation frameworks are optional enhancements, not installation requirements.

**Important compatibility boundary:** a host must be able to discover a folder-based `SKILL.md` and read its referenced Markdown files. A model or chat surface that accepts only a single prompt cannot install this package as a persistent skill; attach the complete directory or paste the required files for that session instead.

### Common installation options

From a local checkout, copy the directory into the platform-specific location below. Replace `/path/to/humanize-writing` with the directory containing this README.

```sh
cp -R /path/to/humanize-writing <skills-directory>/humanize-writing
```

If the skill is published in a compatible skills registry, use that registry's installer instead, then verify that the full supporting directory was installed. Registry commands and package names vary by platform.

### Claude Code

**Project scope**

```sh
mkdir -p .claude/skills
cp -R /path/to/humanize-writing .claude/skills/humanize-writing
```

**User scope**

```sh
mkdir -p ~/.claude/skills
cp -R /path/to/humanize-writing ~/.claude/skills/humanize-writing
```

Use it with `/humanize-writing` when slash invocation is enabled, or ask Claude Code to humanize, paraphrase, evaluate, or grammar-check text. Claude Code can also load it automatically when the task matches the description in `SKILL.md`.

### OpenCode

**Project scope**

```sh
mkdir -p .opencode/skills
cp -R /path/to/humanize-writing .opencode/skills/humanize-writing
```

**User scope**

```sh
mkdir -p ~/.config/opencode/skills
cp -R /path/to/humanize-writing ~/.config/opencode/skills/humanize-writing
```

Start OpenCode in the project and request the task in natural language. If your OpenCode installation supports a skills manager, the equivalent project/global installation can be used; manual copying is the fallback.

### Gemini CLI

**Project scope**

```sh
mkdir -p .gemini/skills
cp -R /path/to/humanize-writing .gemini/skills/humanize-writing
```

**User scope**

```sh
mkdir -p ~/.gemini/skills
cp -R /path/to/humanize-writing ~/.gemini/skills/humanize-writing
```

Some Gemini CLI versions also discover the cross-agent `.agents/skills/` directory:

```sh
mkdir -p .agents/skills
cp -R /path/to/humanize-writing .agents/skills/humanize-writing
```

Use `/skills list` or the equivalent skills command to verify discovery, then ask Gemini CLI to use `humanize-writing`.

### GitHub Copilot CLI

**Repository scope**

```sh
mkdir -p .github/skills
cp -R /path/to/humanize-writing .github/skills/humanize-writing
```

**User scope**

```sh
mkdir -p ~/.copilot/skills
cp -R /path/to/humanize-writing ~/.copilot/skills/humanize-writing
```

Copilot CLI discovers compatible `SKILL.md` files from supported project and user skill directories. Start a new task and say, for example, `Use humanize-writing to rewrite this in natural Indonesian while preserving every claim`. If available in your version, use `/skills list` to verify discovery.

If the skill was added during an active session, run:

```text
/skills reload
/skills info humanize-writing
```

### Google Antigravity

**Project scope**

```sh
mkdir -p .agents/skills
cp -R /path/to/humanize-writing .agents/skills/humanize-writing
```

**User scope (Antigravity App)**

The documented global Antigravity App location is:

```sh
mkdir -p ~/.gemini/config/skills
cp -R /path/to/humanize-writing ~/.gemini/config/skills/humanize-writing
```

The shared fallback for Antigravity CLI/IDE integrations is:

```sh
mkdir -p ~/.agents/skills
cp -R /path/to/humanize-writing ~/.agents/skills/humanize-writing
```

Open or reload the workspace, then ask the Antigravity agent to use `humanize-writing`. Antigravity exposes both automatic invocation and explicit `/<skill-name>` invocation when supported.

### ChatGPT

ChatGPT Skills are available only on accounts and workspaces that expose the Skills feature. Create a ZIP containing the complete `humanize-writing/` directory:

```sh
zip -r humanize-writing.zip humanize-writing
```

In ChatGPT, open **Skills**, choose **Create** or **Upload from your computer**, and upload the ZIP. Enable the skill for the conversation or workspace. Then use prompts such as:

```text
Use the humanize-writing skill. Humanize the following Indonesian text in the Simple style.
Preserve every claim, number, name, quotation, and modality. Flag suspicious source claims.
```

If the Skills UI is not available, attach the ZIP or the relevant Markdown files and explicitly instruct ChatGPT to follow `SKILL.md`.

ChatGPT may scan an uploaded skill and mark it as **Needs Review** or **Blocked**. This is a product safety decision, not a problem with the Agent Skills format. Review the package and workspace permissions before retrying.

### Codex CLI, Cursor, Windsurf, and other compatible tools

For tools that implement the open Agent Skills convention, install the complete directory as:

```text
<project>/.agents/skills/humanize-writing/SKILL.md
```

or, for a user-wide installation:

```text
~/.agents/skills/humanize-writing/SKILL.md
```

The exact discovery path, reload command, and slash-command behavior are tool-specific. Natural-language activation remains the portable fallback.

When a tool documents a different project or global skill directory, use that directory and preserve the same package structure. If it supports the shared `.agents/skills/` convention, the generic installation above usually applies.

## Usage

The skill auto-routes between `PARA`, `HUM`, `SLOP`, `FACT`, `GRAM`, `EVAL`, and `FULL`. Request a mode explicitly when precision matters:

```text
Use humanize-writing in HUM mode. Rewrite this English text so it sounds natural.
Match the supplied writing sample. Do not add or remove claims.
```

```text
Use humanize-writing in EVAL mode. Score the candidate against the source using
the evaluation rubric. Check guardrails before assigning quality scores.
```

For the strongest results, provide the target audience, purpose, desired style preset, and a short writing sample. The output language follows the input language unless translation is requested.

## Platform notes

- Platform support is determined by the host application's current Agent Skills implementation, not by this skill alone.
- Manual installation is the most reliable and transparent option.
- Keep all supporting files together and reload/restart the host after installation if it does not discover the skill immediately.
- The skill never treats AI-detector evasion as the objective; readability, fidelity, correctness, and audience fit take priority.

## Attribution

Adapts and expands on [blader/humanizer](https://github.com/blader/humanizer) (26 AI-writing patterns, plus voice matching and audience-fit checks), plus EYD 2022/PUEBI & KBBI for Bahasa Indonesia and standard copy-editing practice (Chicago/APA house style) for English.

---

Language-specific examples remain in the Indonesian protocols and lexicon so the skill can process Indonesian text correctly. The operational instructions and installation guidance in this package are written in English for cross-model compatibility.
