# Composable Rewrite Patterns

Use these as small, named operations rather than one undifferentiated rewrite prompt. Select only the patterns required by the diagnosis. This is the Fabric-inspired part of the skill: patterns are reusable, composable, and independently auditable.

## Pattern catalog

| Pattern | Use when | Operation | Guardrail |
|---|---|---|---|
| `meaning-lock` | every mode | extract atomic claims, literals, entities, modality, and scope | 1:1 claim map |
| `voice-match` | a sample or clear author voice exists | match rhythm, openings, word choice, punctuation, and deliberate quirks | do not copy claims from the sample |
| `state-directly` | staging, fake contrast, rhetorical run-up | state the supported point without the theatrical setup | retain real contrasts |
| `deinflate` | inflated significance or sales language | keep the concrete fact and remove unsupported importance | do not weaken a real quantified claim |
| `de-slop` | filler, symmetry, template structure | cut redundancy and rebuild from the paragraph's main point | no claim drops |
| `vary-rhythm` | repeated openings or uniform sentences | change sentence boundaries and paragraph rhythm | preserve voice sample preferences |
| `grammar-mechanical` | grammar or EYD mode | run language checklist, then optional LanguageTool | style suggestions are not errors |
| `claim-diff` | every rewrite | compare source and output claim by claim | fail on additions/drops |
| `flag-source-risk` | suspicious or unverifiable source claim | preserve source-relative wording and add a flag | never invent a correction |
| `audience-fit` | wrong-reader or over-explained text | lead with the reader's decision, subject, or consequence | retain context that changes interpretation |

## Composition

Default FULL composition:

```text
meaning-lock
→ audience-fit
→ diagnose
→ flag-source-risk
→ de-slop
→ state-directly
→ deinflate
→ voice-match
→ vary-rhythm
→ grammar-mechanical
→ claim-diff
→ final-audit
```

Skip a pattern when its trigger is absent. Never apply `deinflate`, `de-slop`, or `state-directly` by blind word replacement; rewrite the underlying idea.
