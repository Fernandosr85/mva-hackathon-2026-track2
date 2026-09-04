# The Proteasome Paradox in BUB1B-MVA

**Track 2 · Rare Disease, Real Kid: MVA Hackathon 2026**
**Fernando (HF: `fernandosr85`) · Independent Researcher, São Paulo, Brazil**
**Licence: CC BY 4.0**

A genotype-conditioned drug-repositioning hypothesis, plus the evidence-verification
layer used to build it.

---

## Read this first: four states, kept apart

The report calls the verification layer a scalable component. This repository exists so
that claim can be checked — and so that nothing here is mistaken for more than it is.

| # | Artefact | State | Where |
|---|---|---|---|
| 1 | **Verifier logic** | **FROZEN** · `489e04ad03f2d74b6932f4780d49a8896041e3c33e40d6e7f9efd35c108c7536` | `verifier/track2_evidence_verifier_v3.ipynb` |
| 2 | **Preregistration** | **FROZEN** · `f4ec3d6c4b0f82b0d8d163032e32a430e39bf2598b64a0e0f8f9f81a2da1d300` | `verifier/PREREGISTRATION_v3_FROZEN.md` |
| 3 | **25 mechanical cases** | **REGRESSION SUITE — outcomes already observed** | `evidence/frozen_v3/benchmark_mechanical.jsonl` |
| 4 | **15 semantic cases** | **DOES NOT EXIST** — awaiting an independent author | — |

### What states 3 and 4 mean

**The 25 mechanical cases are not prospective validation.** They were generated, hashed
and executed during v3 development, and their results were known before the
preregistration was written. Reporting them as a blind evaluation would be false. They
serve as a regression suite: if a future change breaks anchoring, retrieval or the
over-assertion gate, they will say so.

Results, for the record: supported 10/10 grounded; wrong source 5/5 detected; verb
inflation 5/5 flagged; entity swap 0/5, which was registered in advance as a predicted
failure.

**The 15 semantic cases do not exist.** They are the only prospective test of the frozen
verifier, and they have not been written. `verifier/semantic_author_brief.md` specifies
them.

Neither assistant involved in this project may write them. One read the negation regex,
the sentence-window function and the criteria; the other wrote the verifier and knows
precisely where it fails. Cases authored with that knowledge would be white-box
adversarial, not blind. The brief states what the author must not see.

Until they are written and executed, **three categories report `NOT RUN` — never as
passed.** The notebook enforces this: with no semantic file present it runs the
regression suite only, prints `REGRESSION ONLY`, and refuses to treat the run as a
registered benchmark.

---

## Layout

```
report/
  track2_report_v0.3.md                    the proposal
  three_minute_pitch.md                    pitch script, timed
  mechanism_map_therapeutic_axes.md        therapeutic axes, per-claim verification states
  mechanism_map_decisive_experiment.md     the experiment as a decision sequence

verifier/
  track2_evidence_verifier_v3.ipynb        runs top to bottom in a fresh session
  PREREGISTRATION_v3_FROZEN.md             signed before any semantic case existed
  semantic_author_brief.md                 for the independent author

evidence/
  frozen_v3/                               the corpus, registry, full text, results
  therapeutic_expansion/                   sources retrieved after the corpus was frozen

methods/
  METHODS_DESCRIPTION_track2.xlsx          the organisers' methods template, filled

manifests/
  SHA256SUMS.txt                           every file in this repository
```

---

## The proposal in one paragraph

Track 1 established a biallelic *BUB1B* genotype. The missense allele `p.Asn1002Lys` is
still a VUS, and a missense variant can break BubR1 two ways: a protein that does not
work, or a protein that works but is degraded too fast to be present in useful amounts.
Published work divides MVA-associated *BUB1B* missense variants into exactly these
classes and shows that for the low-abundance class, scarcity rather than dysfunction is
the defect. Position does not predict class, and this residue has never been
characterised.

If it is unstable-but-competent, blocking degradation should raise residual BubR1 — the
source study showed a proteasome inhibitor preventing exactly that clearance. But
aneuploid cells also depend more heavily on protein degradation, documented from
isogenic models through cancer lines to myeloma patient response. **The same drug class
therefore has two opposite predicted effects in this genotype.**

The same reasoning produces a sharper result. HSP90 inhibition is a validated
aneuploidy-selective vulnerability, but HSP90 is the chaperone that folds these unstable
BubR1 mutants. **A drug selected from the downstream phenotype can worsen the upstream
genetic lesion.**

---

## Verifying this repository

```bash
sha256sum -c manifests/SHA256SUMS.txt
```

Two hashes are named in the preregistration and must match:

```bash
python3 -c "
import json,hashlib
s=json.load(open('evidence/frozen_v3/verifier_spec_v3.json'))
h=hashlib.sha256(json.dumps(s['verifier_logic'],sort_keys=True).encode()).hexdigest()
print(h)
print('MATCH' if h=='489e04ad03f2d74b6932f4780d49a8896041e3c33e40d6e7f9efd35c108c7536' else 'MISMATCH')"
```

The logic hash is stable across corpus drift and across days. An earlier version bundled
the corpus hash, the registry hash and the run date into a single field called
`verifier_sha256`, so it changed when nothing logical had. That field asserted more than
its name represented, which is the failure this whole project is about.

`.gitattributes` marks frozen artefacts `-text` so `core.autocrlf` cannot rewrite line
endings on checkout. Without it these digests fail on any Windows clone.

---

## Data handling

**No data derived from the proband's genome was transmitted to any external service.**
Literature queries are gene- and disease-level only, enforced by a guard with a
self-test that aborts if a controlled-data pattern passes or a gene-level query is
blocked.

The guard's self-test uses **synthetic** identifiers — `WGS_EX0000000`, `HP:0000000`,
`rs999999999`. They exercise every pattern exactly as real ones would. An earlier draft
used the proband's actual identifiers as test fixtures, which would have published, in a
public repository, precisely the values the guard exists to keep out of a query. The
same leak by another route.

For the same reason the leak-detection list in the semantic loader omits the internal
sample identifier and reads it from `PROBAND_TOKENS_LOCAL`, which is gitignored. The
variant identifiers it does list were published under CC BY 4.0 in this team's Track 1
submission.

No controlled data appears in this repository. Controlled data will be deleted within 30
days of the hackathon close, with attestation to the organisers.

---

## Tooling

| Service | Terms | Data handling | Used for |
|---|---|---|---|
| Anthropic API, Claude | commercial | no training on customer content | analysis design, literature synthesis, code review, drafting |
| Europe PMC REST | public academic API | gene and disease terms, publication identifiers only | literature retrieval, full text |
| NCBI E-utilities / PMC | public API, identified caller | as above | retrieval, full-text fallback |

No LLM was given access to controlled data at any point.

---

## Acknowledgement

> This work was made possible through the Hackathon, organized by Sage Bionetworks in
> partnership with the MVA Society, Hugging Face, and BEACON (The Benchmarking,
> Evaluation, and Assessment Consortium for Science), with prize sponsorship from AWS
> and Anthropic. We are deeply grateful to the child and their family who generously
> contributed their data and their story to advance research into this rare disease. We
> acknowledge their trust in making this Hackathon possible.
