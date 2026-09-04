# Preregistration v3 — Blind Semantic Evaluation of the Evidence Verifier

**Track 2 · MVA Hackathon 2026 · Fernando (HF: `fernandosr85`)**

**Status: FROZEN 2026-09-04, before any of the 15 semantic cases exists.**

---

## 1. Frozen identities

Every hash below was recomputed from the artefacts, not copied from console output.

| Identity | SHA-256 | What it covers |
|---|---|---|
| `verifier_logic` | `489e04ad03f2d74b6932f4780d49a8896041e3c33e40d6e7f9efd35c108c7536` | state machine, anchoring floor, negation scope and regex, strength lexicon, over-assertion gate, polarity invariant |
| `retrieval_policy` | `a4c1597f887c91d5c6cd0671d5084af897aed0104e48272a06822ee8df41a1e7` | provider order, retries, JATS parser, cache semantics |
| `run_environment` | `e65d3dd52b8dbbbe46a01bad15a9d234f2d3414b549f9eb167bfe2c19e6c3cf2` | corpus, registry, date — changes every run by design |
| `mechanical_cases` | `d83ef52412db4f58f50ab2bbe4385f5ecf9c54c93332614a941329faa7a7f7ca` | the 25 deterministic regression cases |
| `corpus` | `d021db69278139e7c65eee8d3b9612bdc1a6b2b3db45c0d4da8faadbcd9106f8` | 301 records |
| `claim_registry` | `ae4675df3fd11bc1e27989ffb79f0d472dc7f7358babb5a99eeddd43281dd433` | the 11 original claims |

**This preregistration names `verifier_logic` and `retrieval_policy`.** Changing
either voids it and makes the next experiment v4, not a corrected v3.

The three identities exist because v2 had one field called `verifier_sha256` that
covered the logic *and* the corpus *and* the registry *and* the run date. It changed
when nothing logical had. The logic hash above is stable across corpus drift and
across days; the environment hash is not, and is not supposed to be.

## 2. Two sets with different epistemic status

This is the correction that matters most, and it is why this document is not a
reissue of the earlier registration.

### 2a. Mechanical suite — frozen regression, outcomes already observed

25 deterministic cases, hash `d83ef524…`, **generated, hashed and executed during v3
development**. Their results are known:

| Category | n | Result | Criterion |
|---|---:|---|---|
| supported | 10 | 10/10 grounded | ≥10 — met |
| wrong_source | 5 | 5/5 not grounded | ≥4 — met |
| verb_inflation | 5 | 5/5 over_asserted | ≥5 — met |
| entity_swap | 5 | 0/5 detected | diagnostic, near-zero predicted |

**These do not count as prospective validation.** They are a regression suite: if a
future change breaks anchoring, retrieval or the over-assertion gate, they will say
so. Reporting them as a blind evaluation would be false, since the outcomes were seen
before this document was written.

### 2b. Semantic set — the prospective evaluation

15 cases, **not yet written and not yet executed**: 5 simple polarity, 5 scoped
negation, 5 nominal inflation.

This is the only part of the benchmark that constitutes a prospective test of the
frozen verifier.

## 3. Authorship of the 15 cases

**Neither assistant involved in this project may write them.**

| Party | Why excluded |
|---|---|
| The auditing assistant | Has read the negation regex, `sentence_window`, the tier lexicon, the criteria and the predicted failures. Cases written with that knowledge are white-box adversarial, not blind. |
| The building assistant | Wrote the verifier. Knows precisely where it fails and which three categories are registered to fail. Authoring the test as well as the system under test puts one party on both sides. |

The 15 cases must be written by **Fernando, or by an independent author who receives
the full-text paragraphs and the category definitions but not the implementation**.
Specifically, the author must not see: the negation regex, the sentence-window
function, the strength lexicon, the approximate-match floor, or the list of
categories registered to fail.

## 4. Frozen expectations for the 15

| Category | n | Criterion | Component | Basis |
|---|---:|---|---|---|
| `polarity_simple` | 5 | ≥ 3 → `contradicted` | negation regex, sentence-scoped | explicit negation inside the span's own sentence is matched |
| `polarity_scoped` | 5 | **diagnostic, no threshold** | negation regex | a proximity regex has no scope model; double negation and contrastive clauses defeat it |
| `nominal_inflation` | 5 | **near-zero expected** | 3-tier lexicon | a claim with no registered evidential verb scores tier 0 and can never exceed a hedged source |

Two of the three are registered to fail. A benchmark on which every category passes
was built to pass.

### The nominal blind spot, restated

Observed in the v2 run and deliberately left uncorrected:

> claim: "The malignancies **characteristic of** MVA1 are …" → tier 0
> span: "The most frequent malignancies **associated with** MVA syndrome are …" → tier 1
> `0 > 1` is false, so the claim is reported `calibrated`.

Adding `characteristic of`, `hallmark of`, `defined by` to the lexicon would raise the
score on a case already known to fail, and the benchmark would be testing a verifier
tuned to its own known error.

## 5. Immutable order of operations

```
freeze this preregistration
  → independent author writes the 15 blind cases
  → hash and freeze the cases
  → execute the blind evaluation
  → disclose results
  → only then create the white-box adversarial set
```

The white-box set, if built, carries its **own identity, its own hash and its own
results table**. Run together with the blind set, no result could be attributed to a
condition of knowledge, and both would be uninterpretable.

## 6. Reporting rules

- All seven categories reported, including `NOT RUN`, never as passed.
- Mechanical and semantic results reported **in separate tables**, with their
  epistemic status stated in each.
- Per-category confusion matrices. No aggregate accuracy replaces them.
- `polarity_scoped` and `nominal_inflation` reported as diagnostics, no pass/fail.
- `entity_swap` reports **raw non-grounded output and attributable detection
  separately**. In the pilot the raw figure was 1/5 and came from negation leakage,
  not from noticing the substituted entity; with the leak closed it is 0/5.
- `verifier_logic_sha256` printed alongside every result.
- Cases and labels published with the results so a reader can re-run them.

## 7. Falsification criteria

| Check | Floor | Meaning if breached |
|---|---|---|
| `supported` | 10/10 | anchoring fails on text copied verbatim from a retrieved source — implementation bug, not a score |
| `wrong_source` | 2/5 | a wrong source is undetectable with the correct text in hand |
| `verb_inflation` | 3/5 | the over-assertion gate does not fire on validated tier-raising mutations |
| scope invariant | 0 violations | anything reaching `unsupported` without full text having been searched; asserted in code, aborts the run |
| polarity invariant | 0 false contradictions | identical claim and span produce a conflict, meaning negation is read from outside the compared unit; asserted in code, aborts the run |

## 8. Environment integrity, stated precisely

**Zero integrity mismatch within the 301-record snapshot.** Every record reproduces
its own content hash, and the corpus hash recomputes to `d021db69…`.

**Separately: the current snapshot differs from the earlier 302-record snapshot.**
Both statements are true and neither implies the other. The cause of the difference is
not attributed — `record_key` prefers DOI over PMID and feeds `content_hash`, so an
article gaining a DOI changes identity with unchanged content, which is
indistinguishable here from a change in the literature.

## 9. Known limitations of the verifier

Stated because a verifier that hides its own limits is the thing it was built to
prevent.

1. **Anchoring is lexical.** No entailment check between claim and span. A claim can
   drift from its own declared evidence and still anchor.
2. **Negation is a regex scoped to one sentence.** No scope model; nested and
   contrastive negation defeat it.
3. **Over-assertion is a 3-tier lexicon.** Nominal and adjectival strengthening stays
   at tier 0 and cannot be flagged.
4. **JATS parsing is regex-level.** Adequate to locate a span and name its section;
   spans in tables or figure captions may be missed.
5. **Non-OA sources cannot be checked beyond their abstract.** Those claims are
   `unverifiable_partial_text`, not false.
6. **Source identifiers for the original 11 claims were declared post-hoc**, after the
   v0 audit failed. Claim text and spans were frozen first.

## 10. Compliance: an inconsistency recorded

> Two compliance checks addressing the same underlying question were implemented by
> the same analyst using different evidentiary standards: query screening tested
> identity and provenance, whereas the later bundle scan inferred provenance from
> identifier morphology. The inconsistency was not noticed until review.

The bundle scan flagged `rs121909055`, `c.2215G>T` and `p.His638` as controlled data.
They are **other patients' variants reported in published papers** that the keyword
search retrieved — public literature. Tested by identity instead of by shape, the
bundle is clean: no proband coordinate, variant, rsID, sample identifier or HPO term
appears in any artefact.

The point is not that morphological inference is wrong in general. It is that the same
person built two controls for the same question and applied different standards to
each without noticing.

## 11. The pattern this project keeps finding

> conclusion scope ≤ verified observation scope

Eleven violations, each found by a later layer rather than by review:

| # | Where | Conclusion | Observation |
|---|---|---|---|
| 1–4 | Track 1 | filter, annotation field, depth statistic, assertion | see the Track 1 report |
| 5 | v1 audit | "the source does not support the claim" | the abstract only |
| 6 | v1 metrics | "evidence fully covered" | some text existed |
| 7 | preregistration | "~0% polarity detection" | the code was not read |
| 8 | case generator | "detection failure" | the mutation lowered the tier |
| 9 | `verifier_sha256` | "the verifier" | logic + corpus + registry + date |
| 10 | status message | "the literature moved" | the snapshot changed |
| 11 | compliance scan | "controlled data present" | a string matched a pattern |

Two of these were introduced by the notebook built to prevent the first four. One by
the preregistration written to prevent those. One by the generator that tests it. One
by the cryptographic identifier meant to make the freezing verifiable.

The pattern reproduces inside every layer added to stop it. That is the argument for
making the constraint executable rather than a matter of care.

## 12. Provenance

| Artefact | Path |
|---|---|
| Verifier spec | `evidence_comparison/verifier_spec_v3.json` |
| Claim registry | `evidence/claim_registry_v0.jsonl` |
| Corpus snapshot | `evidence/evidence_snapshot_2026-09-04.jsonl` (301 records) |
| Mechanical cases | `evidence_comparison/benchmark_mechanical.jsonl` (25) |
| Regression results | `evidence_comparison/benchmark_results_2026-09-04.csv` |
| Full text | `evidence_v1/fulltext_xml/` (7 documents) |
| Fetch log | `evidence_v1/fetch_log_2026-09-04.csv` |

Commit the three loose trees only — `evidence/`, `evidence_v1/`,
`evidence_comparison/`. The uploaded bundle also contained a pre-benchmark historical
directory and a nested zip; neither should be committed.

## 13. Tooling declaration

- Europe PMC REST and NCBI E-utilities — retrieval by identifier and by gene- and
  disease-level query. Public APIs. No patient data in any request, enforced by a
  query guard with an aborting self-test.
- Anthropic API, Claude, commercial terms, no training on customer content — verifier
  implementation, code review and this document. **Explicitly barred from authoring
  the 15 semantic cases**, per section 3.

---

**Signed frozen 2026-09-04. No semantic benchmark case exists at the time of signing.**
