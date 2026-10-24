# Quality Evaluation (EVAL)

Use this protocol when the user asks to score, compare, benchmark, or regression-test a rewrite. It adapts the useful parts of Ragas and DeepEval without requiring a Python package or an external evaluator.

## 1. Evaluation inputs

Prefer, in order:

1. source text + candidate rewrite;
2. source text + two or more candidate rewrites for pairwise comparison;
3. a small labeled regression set containing source, expected constraints, and candidate output.

Never score detector evasion as the objective. Human readability, fidelity, and usefulness take priority.

## 2. Dimensions and scoring

Score each dimension from 0 to 4 using `references/evaluation-rubric.md`:

- meaning preservation;
- factual grounding and no-fabrication;
- language correctness;
- naturalness and voice fit;
- AI-pattern reduction;
- audience and purpose fit;
- completeness and concision.

Calculate the simple mean only when all dimensions are scored. A missing or uncertain dimension must be marked `N/A`, not silently treated as zero.

## 3. Pairwise comparison

When comparing candidates, choose the better candidate per dimension and explain the decisive evidence in one sentence. A candidate that sounds more natural but drops a claim cannot win overall. Use this precedence:

1. guardrail pass;
2. meaning and factual grounding;
3. correctness;
4. audience fit and naturalness;
5. AI-pattern reduction;
6. concision.

## 4. Regression cases

Build cases around failure modes, not random examples:

- negation and modality (`may` vs `does`);
- numbers, dates, units, names, and quotes;
- causal direction versus association;
- suspicious source claims that must be flagged;
- technical terms and mixed ID/EN text;
- voice sample matching;
- decorative headings, triads, dashes, and chatbot residue;
- grammar corrections that could change meaning.

For each case, verify guardrails first, then score quality. A regression fails if a previously passing invariant breaks, even when the aggregate score rises.

## 5. Deliverable

For an evaluation report, provide per-dimension scores, decisive evidence, guardrail record, flags, and an overall status:

- **PASS**: no guardrail failures; all required dimensions ≥3.
- **PASS WITH FLAGS**: no guardrail failures; one or more source claims need user review.
- **FAIL**: any claim addition/drop, modality drift, literal mismatch, or required dimension <3.
