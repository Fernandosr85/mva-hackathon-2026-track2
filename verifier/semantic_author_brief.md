# Brief for the independent author — 15 blind semantic cases

**Do not read the verifier implementation before writing these.** Not the negation
regex, not the sentence-window function, not the strength lexicon, not the
approximate-match floor, and not which categories are predicted to fail. Knowing any
of it turns a blind evaluation into a white-box one.

## What you have

The seven retrieved papers, as paragraph-level JSON with section provenance:

```
evidence_v1/fulltext_xml/PMC9605988_paragraphs.json    (66 paragraphs)
evidence_v1/fulltext_xml/PMC8066494_paragraphs.json    (116)
evidence_v1/fulltext_xml/PMC4337726_paragraphs.json    (154)
evidence_v1/fulltext_xml/PMC2887387_paragraphs.json    (25)
evidence_v1/fulltext_xml/PMC11102876_paragraphs.json   (30)
evidence_v1/fulltext_xml/PMC6500003_paragraphs.json    (40)
evidence_v1/fulltext_xml/PMC11251299_paragraphs.json   (91)
```

Every `span` must be a sentence **copied verbatim** from one of these files, and
`declared_pmcid` must be the paper it came from.

## The three categories, 5 cases each

### `polarity_simple` — the claim asserts the opposite of the span

Find a sentence stating a negative result, then write a claim asserting the positive.
Keep it direct: one explicit negation in the source, none in the claim.

> span: "Depletion of X did not alter checkpoint silencing."
> claim: "Depletion of X alters checkpoint silencing."

### `polarity_scoped` — the polarity difference is structural, not lexical

Same idea, but the negation carries scope that a surface reading would get wrong:
double negation, a contrastive clause where one arm is negative and the other is not,
or a logically equivalent restatement with the polarity flipped.

> span: "Although X did not improve progression-free survival, overall survival improved."
> claim: "X improved progression-free survival."

> span: "There is no evidence that X fails to stabilise attachments."
> claim: "X does not stabilise attachments."

### `nominal_inflation` — the claim is stronger, but no verb changed

Take a hedged or associative sentence and write a claim that states the same content
with stronger framing carried by **nouns and adjectives** rather than verbs.

> span: "The malignancies most frequently associated with the syndrome are …"
> claim: "The malignancies characteristic of the syndrome are …"

> span: "Reduced BubR1 has been reported in these cells."
> claim: "Reduced BubR1 is the hallmark of these cells."

## Format — one JSON object per line

```json
{"case_id": "P01", "category": "polarity_simple",
 "claim_text": "...", "span": "...", "declared_pmcid": "PMC9605988",
 "expected_axis_d": "contradicted", "expected_over_assertion": null,
 "mutation": "polarity inverted", "origin": "PMC9605988 Results/Results#p14"}
```

Expected values are fixed by the registration and the loader rejects anything else:

| category | `expected_axis_d` | `expected_over_assertion` |
|---|---|---|
| `polarity_simple` | `"contradicted"` | `null` |
| `polarity_scoped` | `"contradicted"` | `null` |
| `nominal_inflation` | `"grounded"` | `"over_asserted"` |

Optional first line for metadata:

```json
{"_meta": {"author": "<name>", "n": 15, "written_at": "<date>"}}
```

## Constraints the loader enforces

- exactly 15 cases, 5 per category
- all required fields present
- no duplicate `case_id`
- **no two cases may share a span** — five cases on one sentence would report as five
- `declared_pmcid` must be one of the seven above
- expected values must match the table
- no identifier from the proband's own genome

## What happens next

1. You deliver `benchmark_semantic.jsonl`
2. Its SHA-256 is computed and committed **before the file is executed**
3. The notebook loads it read-only and runs the frozen verifier `489e04ad…`
4. Results are published with the cases, so anyone can re-run them

Nobody, including the people who built the verifier, may edit a case after step 2.

## One thing worth knowing

Some of these cases are expected to defeat the verifier. That is the point — a
benchmark on which everything passes was built to pass. Write the cases you think are
fair tests of the category, not the cases you think will be caught.
