# Output Guardrails

Guardrails are pass/fail checks applied after every rewrite and before delivery. They are inspired by validator pipelines: validate the source contract, validate the transformed text, then choose an explicit failure action. A failed guardrail is never hidden by a polished rewrite.

## 1. Meaning and claim validators

Compare the output against the Stage 0 meaning inventory:

- **Claim parity**: every source claim has one output counterpart; every output claim has a source counterpart.
- **Modality parity**: preserve fact, opinion, possibility, prediction, attribution, and uncertainty strength.
- **Scope parity**: preserve quantifiers, exclusions, negations, comparisons, and causal direction.
- **Entity parity**: names, organizations, products, places, technical terms, titles, and defined labels are copied or deliberately preserved.
- **Literal-data parity**: numbers, dates, units, percentages, URLs, citations, and quotes match exactly unless the user explicitly requested conversion.
- **No helpful additions**: no new examples, context facts, sources, explanations presented as facts, or implied promises.

## 2. Style and structure validators

- Output language matches the input language unless translation was requested.
- The selected style preset and implied audience are consistent throughout.
- Code, frontmatter, inline code, paths, URLs, and data are unchanged in file mode.
- Quotes and named entities are untouched.
- AI-pattern findings are removed or justified; a vocabulary hit alone is not an automatic failure.
- Grammar and punctuation pass the language protocol. If an external LanguageTool server is available, run it as a second mechanical check; do not treat every suggestion as mandatory.

## 3. Failure actions

Use the least destructive action that makes the issue explicit:

| Failure | Action |
|---|---|
| Claim added or dropped | Stop delivery, restore the claim mapping, and re-audit. |
| Modality, scope, negation, or causality changed | Revert that sentence and rewrite more conservatively. |
| Number, name, quote, URL, or citation changed | Copy from the source exactly; flag if the source itself is suspicious. |
| Grammar checker disagreement | Prefer the declared house style, domain terminology, and user voice; report a doubtful suggestion. |
| Unsupported source claim | Preserve it as a source-relative claim and add a numbered flag; never silently correct it. |
| Style or AI-pattern regression | Rework the paragraph from its main idea, not by synonym swapping. |

## 4. Structured guardrail record

For reports or evaluation runs, record:

```text
claims_source: N
claims_output: N
claim_additions: N
claim_drops: N
modality_drifts: N
entity_or_literal_mismatches: N
flags: N
grammar_uncertainties: N
status: PASS | PASS_WITH_FLAGS | FAIL
```

`PASS_WITH_FLAGS` is valid only when the flags concern suspicious claims already present in the source and the rewrite itself passes parity checks.
