# Humanize Writing

A rewriting engine that turns AI-flavored text in **Bahasa Indonesia or English** into natural,
human-sounding prose. It preserves meaning and stays grounded in the available evidence: it never
invents statistics, quotations, names, or citations, and it flags suspicious claims instead of
silently carrying them forward.

> The working instructions are written in English so any Gen AI can use them. Both input languages
> are fully supported, and the output remains in the input language unless translation is requested.

## What it does

| Capability | What you get |
|------------|--------------|
| **Paraphrase** | Multi-level rewriting (lexical, syntactic, sentence, discourse) with a claim-by-claim meaning lock |
| **Humanize** | Removes 26 core AI-writing patterns plus language-specific tells — EN lexicon (delve, tapestry, "plays a crucial role") and ID lexicon ("Tak dapat dipungkiri", "Dalam era globalisasi...", English-syntax calques) |
| **Anti-Slop** | Removes formulaic structures, false symmetry, generic claims, and template openers/closers |
| **De-Hallucinate** | 1:1 claim mapping, V1–V5 verification classes, flagging protocol for suspicious source claims |
| **Grammar / EYD** | EYD 2022/PUEBI + KBBI for ID (incl. foreign terms preserved untranslated); US/UK register for EN + translationese detection |
| **Citation styles** | APA 7, MLA 9, Turabian, Vancouver, Harvard, Chicago, and IEEE; formatting only from supplied or verified sources |
| **Quality Evaluation** | Rubric-based scoring, claim-diff checks, pairwise comparison, and reusable regression cases |
| **Guardrails** | Explicit validators for claim preservation, modality, entities, quotations, formatting, and no-fabrication |
| **Full Rewrite** | All of the above as a 7-stage pipeline with mandatory guardrail and final-audit checks |

## Modes

Pick via triggers: paraphrase / parafrase · humanize / humanisasi / hilangkan jejak AI · AI slop · fact check / anti halusinasi / cek fakta · cek EYD / grammar check · citation formatting / APA / MLA / Turabian / Vancouver / Harvard / Chicago / IEEE · evaluate / score / uji kualitas · default = FULL.

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
│   ├── grammar-en.md            ← US/UK register, translationese (ID→EN)
│   └── citations.md             ← seven citation-style normalization workflow
├── references/
│   ├── ai-lexicon-en.md         ← EN AI word/structure lexicon + density scoring
│   ├── ai-lexicon-id.md         ← ID AI word/structure lexicon + density scoring
│   ├── style-presets.md         ← 9 register presets with examples & watchlists
│   ├── evaluation-rubric.md     ← quality dimensions, scoring anchors, and thresholds
│   └── citation-styles.md       ← seven citation-style reference
├── checklists/
│   └── final-audit.md           ← mandatory gates: meaning, AI patterns, grammar, flow, AI-risk, and guardrails
└── templates/
    └── report.md                ← deliverable + change-log format
```

## Non-negotiable constraints

1. **Meaning preservation** — the rewrite makes the same claims as the source, no more and no less.
2. **No fabrication** — do not invent statistics, names, quotations, dates, studies, or citations. Flag suspicious claims rather than silently "fixing" or propagating them.
3. **Register target** — keep the output in the input language and choose its style through a preset instead of defaulting to overly formal AI prose.

## Cross-platform installation and usage

This is a portable [Agent Skills](https://agentskills.io/) package. Keep the complete
`humanize-writing/` directory, including `SKILL.md`, `core/`, `protocols/`, `references/`,
`checklists/`, and `templates/`. Do not copy only `SKILL.md`: it references the supporting
documents.

### Compatibility and prerequisites

| Platform | Native skill support | Recommended location | Minimum prerequisite | Activation and verification |
|---|---|---|---|---|
| Claude Code | Yes, Agent Skills standard | `.claude/skills/` or `~/.claude/skills/` | A current Claude Code release with custom skills enabled | `/humanize-writing`; run `/doctor` if discovery fails |
| OpenCode | Yes, Agent Skills standard | `.opencode/skills/`, `.claude/skills/`, or `.agents/skills/` | OpenCode with the `skill` tool enabled and permission not set to `deny` | Ask for `humanize-writing`; confirm it appears in the available skills |
| Gemini CLI | Yes, Agent Skills standard | `.gemini/skills/`, `~/.gemini/skills/`, or `.agents/skills/` | Gemini CLI with Agent Skills support | `/skills`; start a new session after installation |
| GitHub Copilot CLI | Yes, Agent Skills standard | `.github/skills/`, `~/.copilot/skills/`, or `.agents/skills/` | A current Copilot CLI with skills support | `/skills reload`, then `/skills info humanize-writing` |
| Google Antigravity App/CLI/IDE | Yes, Agent Skills standard | `.agents/skills/` or `~/.gemini/config/skills/` | An Antigravity surface with Agent Skills enabled | Reload the workspace; use `/humanize-writing` or natural language |
| Gemini Apps (Web, Mac, Mobile) | Yes, Agent Skills upload | `gemini.google.com` → **Customize** → **Skills** → **Create** → **Upload** | Personal Google Account (18+), Keep Activity on | Upload folder or `.zip` with `SKILL.md` in root; invoke via `/` or `@` or automatic matching |
| ChatGPT | Conditional, product/workspace feature | Uploaded ZIP through Skills UI | Eligible Business, Enterprise, Healthcare, or Edu workspace with Skills and upload permissions | Upload, enable, then ask ChatGPT to use the skill |
| Codex CLI | Agent Skills support varies by release | `.agents/skills/` or documented path | A release with folder-based skill discovery | Reload skills and request `humanize-writing` |
| Cursor | Agent Skills support varies by release | `.cursor/skills/` or `.agents/skills/` | A release with custom skill/Markdown support | Reload the project and request `humanize-writing` |
| Windsurf | Agent Skills support varies by release | Documented workspace skill path or `.agents/skills/` | A release with custom workflow/skill support | Reload the workspace and request `humanize-writing` |
| Other compatible agents | Depends on implementation | `.agents/skills/` or documented platform path | Agent Skills discovery and Markdown resource access | Follow the host's reload/list command |

The skill has no runtime package, API key, database, or operating-system-specific dependency.
Rewriting, citation-style guidance, guardrails, and evaluation are instruction-driven. LanguageTool,
web access, and external evaluation frameworks are optional enhancements, not installation
requirements. Citation normalization requires supplied references or verifiable metadata; the skill
never invents missing bibliographic data.

**Compatibility boundary:** the host must be able to discover a folder-based `SKILL.md` and read
its referenced Markdown files. A model or chat surface that accepts only a single prompt cannot
install this package as a persistent skill; attach the complete directory or paste the required
files for that session instead.

### Common installation options

From a local checkout, copy the directory into the platform-specific location below. Replace
`/path/to/humanize-writing` with the directory that contains this README.

```sh
cp -R /path/to/humanize-writing <skills-directory>/humanize-writing
```

If the skill is published in a compatible skills registry, use the registry's installer instead,
then verify that the complete supporting directory was installed. Registry commands and package
names vary by platform.

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

Start OpenCode in the project and describe the task in natural language. If your installation
supports a skills manager, use its equivalent project or global installation; manual copying is
the fallback.

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

Use `/skills list`, or the equivalent skills command, to verify discovery. Then ask Gemini CLI to
use `humanize-writing`.

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

Copilot CLI discovers compatible `SKILL.md` files in supported project and user skill directories.
Start a new task and say, for example, `Use humanize-writing to rewrite this in natural Indonesian
while preserving every claim`. If available in your version, use `/skills list` to verify discovery.

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

Open or reload the workspace, then ask the Antigravity agent to use `humanize-writing`.
Antigravity supports both automatic invocation and explicit `/<skill-name>` invocation where available.

### Gemini Apps (Web, Mac, and Mobile) — Upload Method

Gemini Apps (`gemini.google.com`, the Gemini Mac app, and the mobile app) support installing custom skills by uploading a folder or `.zip` archive (requires an 18+ account with **Keep Activity** turned on).

Per Google's upload requirements ([Create & manage skills for Gemini Apps](https://support.google.com/gemini/answer/17094296)):
- `SKILL.md` must be located in the **root (main) folder** of the uploaded folder or `.zip` archive.
- The skill `name` inside `SKILL.md` must be lowercase with hyphens (`humanize-writing`).
- Only supported plain-text files (`.md`, `.txt`, etc.) are included; total size must not exceed 100 MB.
- Hidden binary/OS metadata files (such as `.DS_Store`, `.git/`, `.pyc`, or `__MACOSX`) must be excluded so the upload validation does not fail.

**Step 1: Prepare a clean `.zip` archive (with `SKILL.md` at the root)**

```sh
cd /path/to/humanize-writing
zip -r -X humanize-writing-gemini.zip \
  SKILL.md core protocols references checklists templates \
  -x "*.DS_Store" -x "__MACOSX/*" -x "*.git*" -x "*.pyc"
```

*(Alternatively, you can upload the `humanize-writing` folder directly from your computer as long as it contains no hidden `.DS_Store` or `.git` files.)*

**Step 2: Upload to Gemini Web (`gemini.google.com`)**

1. Go to [gemini.google.com](https://gemini.google.com) (or open the Gemini app on Mac).
2. On the left sidebar, click **Customize** (if you don't see it, first click **More**) → **Skills**.
3. At the top of the Skills page, click **Create** → **Upload**.
4. Select `humanize-writing-gemini.zip` (or the `humanize-writing/` folder) and click **Open**.
5. Review the imported skill details and click **Create** at the top.
6. **Usage**: In any chat or task thread, type `/` (or `@`) and select `humanize-writing`, or simply ask Gemini in natural language — Gemini automatically applies activated skills when relevant.

### ChatGPT — Upload Method

ChatGPT Skills can be installed by uploading a `.zip` package on accounts and workspaces with the Skills feature enabled (or attached directly in chat sessions if the Skills UI is unavailable).

**Step 1: Create a clean `.zip` package**

You can package either the root files (`humanize-writing-gemini.zip` above) or the complete `humanize-writing/` directory without hidden OS/Git files:

```sh
zip -r -X humanize-writing.zip humanize-writing \
  -x "*/.git/*" -x "*/.DS_Store" -x "__MACOSX/*"
```

**Step 2: Upload to ChatGPT**

1. In ChatGPT, open **Skills** from the sidebar or profile menu.
2. Click **Create** → **Upload from your computer**, and select `humanize-writing.zip`.
3. Enable the skill for your conversation or workspace.
4. **Usage**: Invoke the skill with `/` or natural-language prompts such as:

```text
Use the humanize-writing skill. Humanize the following Indonesian text in the Simple style.
Preserve every claim, number, name, quotation, and modality. Flag suspicious source claims.
```

If the Skills UI is not available on your plan, upload/attach the `.zip` archive (or the relevant Markdown files) directly in the chat message composer and instruct ChatGPT to read and follow `SKILL.md`.

> **Note:** ChatGPT may scan an uploaded skill and mark it as **Needs Review** or **Blocked**. This is a workspace/product safety check rather than an issue with the Agent Skills format; review workspace permissions before retrying.

### Codex CLI, Cursor, Windsurf, and other compatible tools

For tools that implement the open Agent Skills convention, install the complete directory at:

```text
<project>/.agents/skills/humanize-writing/SKILL.md
```

or, for a user-wide installation:

```text
~/.agents/skills/humanize-writing/SKILL.md
```

The exact discovery path, reload command, and slash-command behavior are tool-specific.
Natural-language activation remains the portable fallback.

When a tool documents a different project or global skill directory, use that directory while
preserving the same package structure. If it supports the shared `.agents/skills/` convention, the
generic installation above usually applies.

For Codex, Cursor, Windsurf, or another host with a dedicated skills directory, copy the complete
directory into that documented location, reload the host, and verify that `SKILL.md` and its
supporting Markdown files are readable. Use natural-language activation when slash commands are
not available.

## Usage

The skill routes requests to `PARA`, `HUM`, `SLOP`, `FACT`, `GRAM`, `EVAL`, or `FULL`. Request a
mode explicitly when precision matters:

```text
Use humanize-writing in HUM mode. Rewrite this English text so it sounds natural.
Match the supplied writing sample. Do not add or remove claims.
```

```text
Use humanize-writing in EVAL mode. Score the candidate against the source using
the evaluation rubric. Check guardrails before assigning quality scores.
```

```text
Use humanize-writing in CITE mode. Normalize the supplied references to APA 7.
Preserve every author, title, date, DOI, URL, quotation, and claim. Mark missing
metadata as UNVERIFIED instead of inventing it.
```

For the best results, provide the target audience, purpose, preferred style preset, and a short
writing sample. The output language follows the input language unless translation is requested.

## Platform notes

- Platform support is determined by the host application's current Agent Skills implementation, not by this skill alone.
- Manual installation is the most reliable and transparent option.
- Keep all supporting files together and reload/restart the host after installation if it does not discover the skill immediately.
- The skill does not treat AI-detector evasion as the objective; readability, fidelity, correctness,
  and audience fit take priority.

## License

This project is released under the **MIT License**. See [`LICENSE`](LICENSE).

## Attribution

This project adapts and expands on [blader/humanizer](https://github.com/blader/humanizer)
(26 AI-writing patterns, plus voice matching and audience-fit checks). It also incorporates
EYD 2022/PUEBI and KBBI for Bahasa Indonesia, along with seven citation and copy-editing styles:
APA 7, MLA 9, Turabian, Vancouver, Harvard, Chicago, and IEEE.

---

Language-specific examples remain in the Indonesian protocols and lexicon so the skill can process
Indonesian text correctly. The operational instructions and installation guidance are written in
English for cross-model compatibility.
