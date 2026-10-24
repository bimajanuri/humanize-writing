# Citation Style Normalization (CITE)

Use this protocol only when the user requests citation or reference formatting. Citation style
normalization changes presentation, not the author's claims or the source record.

## Supported styles

- **APA 7**
- **MLA 9**
- **Turabian**
- **Vancouver**
- **Harvard**
- **Chicago**
- **IEEE**

Load `references/citation-styles.md` for style-specific rules and select exactly one style before
editing. If the user does not specify a style, ask one concise question rather than guessing.

## Integrity rules

1. Preserve authors, titles, dates, journals, publishers, volume/issue, pages, DOI, URL, and access
   dates exactly when supplied.
2. Never invent missing authors, dates, page numbers, DOI values, URLs, or publication details.
3. Mark missing or conflicting metadata `UNVERIFIED — check manually`.
4. Keep quotations, page references, claim modality, and citation-to-claim relationships unchanged.
5. Ensure every in-text citation maps to a reference entry and flag uncited or unused entries.
6. Do not silently convert citation style when the user requests only humanization or grammar.
7. Run `protocols/guardrails.md` and `checklists/final-audit.md` after normalization.

## Output

```text
citation_style: APA 7 | MLA 9 | Turabian | Vancouver | Harvard | Chicago | IEEE
references_checked: N
metadata_flags: N
mapping_flags: N
status: PASS | PASS_WITH_FLAGS | FAIL
```
