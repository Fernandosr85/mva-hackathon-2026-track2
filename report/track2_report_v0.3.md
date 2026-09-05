# The Proteasome Paradox in BUB1B-MVA
## A Genotype-Conditioned Repurposing Hypothesis

**Track 2 · Rare Disease, Real Kid: MVA Hackathon 2026**
**Fernando (HF: `fernandosr85`) · Independent Researcher, São Paulo, Brazil**
**Repository:** `https://github.com/Fernandosr85/mva-hackathon-2026-track2` — *private at the
time of submission. Access can be granted to the review panel on request.*

---

## Executive Summary

**We know the variant pair. We do not know what the second allele does — and that
distinction reverses the therapeutic logic.**

Track 1 identified `c.2210T>G` (`p.Leu737Ter`) with `c.3006T>G` (`p.Asn1002Lys`) in
*BUB1B*. The missense allele remains a variant of uncertain significance, and a missense
variant can break BubR1 two ways. It can produce a protein that does not work. Or it can
produce a protein that works but does not survive — degraded fast enough that the cell
never has enough of it.

Published work on MVA divides *BUB1B* missense variants into exactly these two classes,
and shows that for the low-abundance class, **scarcity rather than dysfunction is the
defect**: the protein works when its expression is equalised. Position does not predict
class, and `p.Asn1002Lys` has never been characterised.

If it is unstable-but-competent, blocking its degradation should raise residual BubR1 and
partially restore checkpoint function — and the source study showed a proteasome
inhibitor preventing exactly that clearance. But aneuploid cells also depend more heavily
on protein degradation, an effect documented from isogenic models through hundreds of
cancer lines to the response of myeloma patients to proteasome inhibitors.

**The same drug class therefore has two opposite predicted effects in this genotype:
rescue the mutant protein upstream, or kill the aneuploid cells downstream.** Viability
alone cannot distinguish them.

The same reasoning produces a second, sharper result. HSP90 inhibition is a validated
aneuploidy-selective vulnerability — but HSP90 is the chaperone that folds these unstable
BubR1 mutants and prevents their clearance. **A drug selected from the downstream
phenotype can worsen the upstream genetic lesion.** A phenotype-level screen returns that
compound as a hit with nothing to flag the conflict.

We propose a three-step ex vivo decision framework: classify the variant by abundance,
turnover, chaperone dependence and function at equalised expression; perturb the
proteasome measuring rescue and killing simultaneously; test selectivity against matched
controls. Four falsification criteria are fixed in advance, and one of them would
invalidate the proposal's own premise.

If the missense allele proves functionally competent but unstable, the result is both a
therapeutic hypothesis and a reusable functional axis for interpreting *BUB1B* variants
that computational prediction leaves unresolved.

This is not a recommendation to give a proteasome inhibitor to a child with MVA. It is a
genotype-conditioned repurposing hypothesis with competing mechanisms named, transfer
limits stated, and criteria that can end it.
---

## 1. Starting Point and Mechanism

Track 1 identified two *BUB1B* variants as the causal pair: `c.2210T>G`, `p.Leu737Ter`,
nonsense with NMD predicted from exon position; and `c.3006T>G`, `p.Asn1002Lys`, missense,
classified VUS. The pair matches the canonical MVA1 architecture, in which a truncating
allele accompanies a missense allele.

**Leaderboard confirmation establishes the pair, not the molecular behaviour of either
allele.** It does not prove phase, actual NMD, absence of truncated protein, or the
functional class of the missense variant. The proband presented with rhabdomyosarcoma,
one of the malignancies repeatedly reported in MVA1.

### BubR1 has two separable mitotic functions

BubR1 is not a generic dosage-sensitive checkpoint protein.

**Anaphase inhibition.** BubR1 is a component of the mitotic checkpoint complex with Mad2,
Cdc20 and Bub3, which inhibits APC/C–Cdc20 and delays anaphase until attachment
requirements are met.

**Attachment stabilisation.** BubR1 contributes to stable kinetochore–microtubule
attachment and checkpoint silencing through kinetochore co-recruitment of PP2A.

These are genetically separable: specific mutations impair one while leaving the other
substantially intact. A truncating allele and a missense allele therefore cannot be
modelled as two equivalent reductions in total dosage.

Patient-derived cells anchor this. Cell lines from MVA patients with biallelic *BUB1B*
mutations show impaired mitotic checkpoint, chromosome-alignment defects and low overall
BubR1 abundance; ectopic BubR1 restores checkpoint activity, establishing causation.

### Why the deficiency produces variegated aneuploidy

The spindle assembly checkpoint is a delay signal, not a permanent brake. Losing it does
not stall the cell — it removes the wait. Cells proceed into anaphase whether or not
chromatids are correctly attached, producing repeated missegregation rather than arrest.

Because these failures occur stochastically across divisions, different cells acquire
different chromosome complements. That is the *variegated* in mosaic variegated
aneuploidy: not one clonal aneuploidy but a distribution of them across tissues.

**No patient-specific PCS percentage or tissue-level aneuploidy burden is available in the
hackathon dataset.** This proposal assumes no numerical aneuploidy load for this
individual — a limitation that matters when a drug is designed to exploit aneuploidy.
## 2. The Pivotal Molecular Question

> **Is `p.Asn1002Lys` a low-abundance but function-competent BubR1 mutant?**

Suijkerbuijk et al. showed that MVA-associated substitutions divide into two categories:
those that reduce BubR1 protein abundance and those that do not. For the low-abundance
class, scarcity rather than dysfunction is the defect — the mutants "affected chromosome
segregation primarily by lowering BUBR1 protein abundance without affecting BUBR1
function." Their conclusion is explicit: chromosomal instability in these patients "is a
result of low BUBR1 protein abundance."

**Position does not predict class.** Kinase-domain substitutions showed a five- to
tenfold decrease in levels; Y155C and R550Q, away from that domain, did not affect levels
at all. But Q921H — in the kinase-domain region — was "indistinguishable from wild-type
LAP-BUBR1, both on protein level and functionality." Residues characterised: Y155C,
R550Q, R727C, R814H, L844F, I909T, Q921H, L1012P. **N1002K was not among them.**

Four outcomes, four different proposals:

| `p.Asn1002Lys` proves to be | Consequence |
|---|---|
| low abundance, function competent | rescue arm becomes the lead |
| low abundance, function also defective | stabilisation alone insufficient |
| stable, function defective | no rationale for stabilisation; vulnerability arm only |
| stable, near wild-type | the allele's causal contribution requires re-examination |

The fourth outcome would not redirect the proposal — it would challenge a premise
inherited from Track 1. **The experiment must be capable of invalidating its own starting
assumption**, and this one is.
---

## 3. The Proteasome Paradox

Two mechanisms act on the same target, in opposite therapeutic directions.

### Upstream: proteasomal clearance of an unstable mutant

In cells expressing unstable BubR1 missense mutants, HSP90 inhibition severely decreased
mutant levels while wild-type changed little, and **"inhibition of proteasomal degradation
with MG132 prevented the enhanced protein turnover caused by HSP90 inhibition."** The
authors conclude that "HSP90 activity is needed for folding of BUBR1 substitution mutants
and for preventing their clearance via proteasomal degradation."

**What this supports:** proteasomal degradation contributes to the loss of specific
unstable BubR1 missense proteins.

**What it does not support:** that `p.Asn1002Lys` behaves this way, or that an approved
proteasome inhibitor restores checkpoint activity. MG132 is a five-hour tool compound in
an overexpression system — a mechanistic probe, not evidence that an approved drug is a
rescue therapy.

### Downstream: proteasome dependency of the aneuploid state

Aneuploid cells "mitigate proteotoxic stress by reducing protein translation and
increasing protein degradation, rendering them more sensitive to proteasome inhibition,"
recapitulated "across hundreds of human cancer cell lines and primary tumors," with
aneuploidy levels "significantly associated with the response of patients with multiple
myeloma to proteasome inhibitors."

The chain runs from graded isogenic RPE1 clones through cancer lines and primary tumours
to **patient response** — the only axis evaluated here that reaches clinical data.

### The two directions

```
                    PROTEASOME INHIBITION
                             │
              ┌──────────────┴──────────────┐
        UPSTREAM RESCUE              DOWNSTREAM KILLING
              │                             │
   mutant BubR1 clearance ↓        proteostasis capacity ↓
              │                             │
      residual BubR1 ↑              proteotoxic stress ↑
              │                             │
        SAC function ↑ ?            aneuploid cell death ↑ ?
              │                             │
        missegregation ↓ ?          tumour clone cleared ?
```

### Why this is the design constraint, not a curiosity

**A viability assay cannot distinguish these.** Fewer viable cells could be
aneuploidy-selective killing or generic toxicity. Preserved viability could be checkpoint
rescue or no pharmacological activity at all. Either result, read alone, is
uninterpretable.

The experiment must therefore measure molecular rescue, chromosome behaviour, stress
response and cell fate **in the same cells**, which is what Section 5 specifies. A study
designed around a dose–response viability curve would produce a number and no mechanism.

**Probe and candidate stay separate.** MG132 is the mechanistic comparator, directly
matched to the prior BubR1 work. A clinically approved proteasome inhibitor is the
translational probe. They are not interchangeable, and treating them as one candidate
would read proof of mechanism as clinical attractiveness.
---

## 4. The HSP90 Veto: When Phenotype and Genotype Disagree

The proteasome paradox shows one target with two effects. HSP90 shows something sharper:
**a target the downstream phenotype recommends and the upstream lesion pushes in the
opposite direction.**

### The downstream case for HSP90 inhibition

Tang, Williams, Siegel and Amon identified AICAR, 17-AAG and chloroquine as selectively
antagonising proliferation in aneuploid cells, with aneuploid fibroblasts showing
increased sensitivity to the HSP90 inhibitor 17-AAG, and AICAR and 17-AAG effective
against aneuploid human cancer lines.

From the aneuploid phenotype alone, HSP90 inhibition is a well-supported candidate.

### The upstream case against it

HSP90 activity is required for the folding of BubR1 substitution mutants and for
preventing their proteasomal clearance. In a genotype whose defect is low abundance of an
unstable missense protein, inhibiting HSP90 attacks the downstream consequence while
**accelerating loss of the residual protein that constitutes the primary defect.**

If the truncating allele undergoes the predicted NMD and the two variants are in trans,
residual BubR1 would derive predominantly from the missense allele — the one HSP90 is
holding together.

> **A drug selected from the downstream phenotype can worsen the upstream genetic
> lesion.**

### What follows

HSP90 inhibition is **deprioritised pending direct classification of `p.Asn1002Lys`** —
not contraindicated. No clinical contraindication for this variant has been established,
and if the variant proves HSP90-independent the branch reopens. Step 1c of the experiment
tests the veto rather than assuming it.

The generalisable point is not about HSP90 or about this gene. **Any rare disease in which
an unstable mutant protein retains partial function creates the same trap:** the chaperone
preserving the residual protein may be the target the downstream phenotype recommends
inhibiting. Screening on the phenotype can select against the patient.

### Effect size runs the wrong way in the closest model

Among the Tang 2011 systems, MEFs "predisposed to chromosomal instability by dint of a
mutation in mitotic checkpoint genes" were growth-inhibited by AICAR and 17-AAG **"but to
a lesser effect than for purely aneuploid MEFs."**

MVA is a checkpoint-driven CIN state, not a defined constitutional trisomy. The model
mechanistically closest to the BUB1B lesion gave the weakest response. This is stated
rather than buried: it signals that transfer to MVA may be weaker than headline results
suggest.

A species caveat runs the same way. Mice homozygous for hypomorphic *BubR1* alleles,
expressing ~10% of normal BubR1, developed progeroid and age-related pathology "instead of
tumors," while human MVA1 gives cancer predisposition. These are not the same molecular
defect, but related severe BubR1 insufficiency produces markedly different organismal
phenotypes across species.
## 5. Decisive Experimental Plan

### Experiment 1 — Classify `p.Asn1002Lys`

This is not a new assay. It is the assay Suijkerbuijk describes, applied to a residue
they did not test.

| Step | Measurement | Reads out |
|---|---|---|
| 1a | BubR1 abundance, quantitative immunoblot, mutant vs wild-type | is the protein scarce? |
| 1b | Half-life under cycloheximide | is scarcity from turnover? |
| 1c | Level after HSP90 inhibition | does folding depend on HSP90? |
| 1d | Level after proteasome inhibition | is clearance proteasomal? |
| 1e | Function at **equalised expression** — SAC activity, chromosome alignment, cold-stable microtubules | defective, or merely scarce? |

**Step 1e is the one that separates the categories and the one most likely to be
skipped.** Without equalising expression, a functional deficit cannot be attributed to
the mutation rather than to its abundance.

Step 1c also converts the HSP90 veto from an assumption into a tested prediction.

### Gate A

```
        Experiment 1
             │
   ┌─────────┴─────────┐
low abundance      stable, or defective
+ competent        when equalised
   │                   │
   ▼                   ▼
Experiment 2       skip to Experiment 3
(rescue + kill)    (vulnerability only)
```

### Experiment 2 — Proteasome perturbation, both mechanisms measured at once

**Compounds.** MG132 as mechanistic probe — directly comparable to prior BubR1 work. A
clinically approved proteasome inhibitor as translational probe. **Not interchangeable.**

**Design.** Dose × time matrix — not because a rescue window is expected, but because
stabilisation and cytotoxicity may have separable kinetics. That separability is a
hypothesis the matrix tests.

**Readouts, all in the same cells:**

| Axis | Measurement | Reports |
|---|---|---|
| Protein | BubR1 abundance, turnover | rescue |
| Function | SAC activity, mitotic timing | rescue |
| Cytogenetic | missegregation, PCS rate, aneuploidy burden | rescue |
| Stress | proteotoxic-stress markers, ubiquitinated protein load | killing |
| Fate | viability, apoptosis | killing |

**Interpretation:**

| Pattern | Reading |
|---|---|
| BubR1 ↑, SAC ↑, missegregation ↓, viability preserved | rescue dominates |
| BubR1 ↑, SAC unchanged | abundance is not the limiting variable |
| Stress ↑, apoptosis ↑, no BubR1 change | killing only |
| Both, at different doses or times | mechanisms are separable |
| Neither | proteasome axis does not apply to this genotype |

### Experiment 3 — Selectivity

Comparators, in order of strength:

1. Patient MVA fibroblasts vs parental or unaffected-relative fibroblasts
2. Isogenic corrected vs uncorrected line, if editing is available
3. Unrelated euploid controls — weakest, background differs

**Endpoint.** A selectivity index: differential response between MVA context and matched
control at each axis from Experiment 2.

**What ends the proposal here.** No differential response. If MVA cells are no more
sensitive than matched controls, the aneuploidy-vulnerability transfer does not reach this
context, whatever cancer lines show.
## 6. Transferability and Safety

Upstream and downstream evidence occupy different evidentiary levels, and the report
should not blur them.

**Patient-derived MVA cells directly support the upstream BubR1 mechanism.**

**No cited therapeutic-vulnerability study tests BUB1B-MVA cells.** Downstream evidence
comes from:

| Model | What it is | Distance from this case |
|---|---|---|
| MVA patient fibroblasts | the condition itself, human | upstream mechanism only; never tested against these drugs |
| Trisomic MEFs | constitutional single-chromosome trisomy, mouse | not mosaic, not variegated, not human |
| CIN-prone MEFs | checkpoint mutation, mouse | mechanistically closest — weakest drug effect |
| RPE1 isogenic clones | engineered aneuploidy, human, immortalised | not constitutional, not mosaic |
| Cancer cell lines | somatic aneuploidy, transformed | transformation confounds |
| Myeloma patients | adults with malignancy | not constitutional, not paediatric |

**Selectivity cannot be assumed.** In MVA the aneuploid cells are the child's own tissues,
not only a tumour clone. A therapy that preferentially damages aneuploid cells may damage
constitutionally aneuploid normal tissue as well.

**This is the principal translational barrier of the proposal.**
## 7. Falsification Criteria

Fixed in advance, so negative results close branches rather than being explained away.

1. **`p.Asn1002Lys` is stable and functionally near wild-type.** Its causal contribution
   requires re-examination before the drug hypothesis stands. *This threatens the premise
   of the proposal itself.*
2. **The variant is unstable but proteasome inhibition does not raise its level.** The
   rescue mechanism lacks support.
3. **BubR1 abundance rises but checkpoint function does not.** Abundance is not the
   limiting variable for this residue, contrary to the Suijkerbuijk model.
4. **BUB1B-MVA cells show no greater susceptibility than matched controls.** The
   aneuploidy-vulnerability literature does not transfer to this context.
---

## 8. Supporting and Rejected Alternatives

Four further axes were evaluated. None displaces the proteasome as mechanistic lead, and
two are recorded as rejections — the analysis discards candidates rather than collecting
hits.

**GR agonists — translational challenger.** An integrative TCGA–PRISM study found "an
unexpectedly prominent number of glucocorticoid receptor agonists" among compounds
selectively reducing viability in aneuploid contexts. Dexamethasone and prednisolone are
approved, inexpensive, have decades of paediatric dosing experience, and are backbone
agents in ALL protocols — one of the three canonical MVA1 malignancies.

*Those are translational attractiveness, not mechanistic evidence.* The study is an
association, presented by its authors as a hypothesis: no isogenic system, no causal
perturbation, no patient-response analysis. No evidence demonstrates selective or
preventive activity in constitutional MVA. An earlier draft of this report ranked GR
agonists above the proteasome axis; that ranking confused ease of administration in a
child with strength of evidence and is withdrawn.

**AICAR — supporting.** Energy-stress induction showed activity in the same trisomic
models as 17-AAG, and carries the same transfer caveat.

**Chloroquine — rejected by the original study's own transfer test.** Selective in
trisomic MEFs; in human aneuploid cancer lines, "AICAR and 17-AAG, but not chloroquine,
showed significant anti-proliferative activity." The paper contains its own
transferability experiment and chloroquine failed it.

**Taxanes — pharmacology of the state, not a candidate.** *BUB1B* variants "lead to
decreased BubR1 expression and/or stability, which promotes increased premature chromatid
separation and, consequently, triggers CIN, driving resistance to Taxol-based therapies."
Taxanes rely on a functional checkpoint to hold cells in mitosis until they die; a crippled
checkpoint lets them slip through. The role here is conceptual — **the BUB1B lesion changes
pharmacological response, not only chromosome counts**, which is what makes repurposing a
coherent question for this genotype. It also carries a clinical note: BubR1 status may be
informative about what *not* to give.
## 9. Why This Is a Repositioning Proposal Rather Than a Drug Screen

A compound screen over MVA cells would rank hits by effect size. That cannot resolve the
central problem: a downstream phenotype can recommend a drug that worsens the upstream
lesion, as HSP90 inhibition illustrates. A phenotype-level screen would have returned
17-AAG as a hit with nothing to flag the conflict.

The proposed strategy begins with the genotype, classifies the unresolved missense allele,
and uses that to determine which pharmacological effects are interpretable. The goal is
not the largest viability effect. It is to determine whether an approved pathway can
either restore a limiting molecular function or exploit a downstream vulnerability —
**without mistaking one for the other**.

This makes mechanism characterisation part of drug selection rather than background
preceding it.
## 10. Potential Impact

The proposal is disciplined about what it does not establish. It should be equally
explicit about what would follow if it succeeded.

### For this child

Experiment 1 answers a question that currently has no answer: whether the missense allele
produces a scarce but working protein or a defective one. **That result is clinically
meaningful independently of any drug.**

Track 1 classified `p.Asn1002Lys` as a VUS with REVEL 0.472, which on the full Pejaver
calibration qualifies for no criterion at any evidence strength on either side —
computational prediction has nothing to say about it. A functional classification would
move the variant on evidence rather than prediction, and would be reportable to the
family's clinical team as functional evidence under ACMG/AMP criteria.

### For other MVA patients

Suijkerbuijk et al. found that MVA-associated substitutions divide into two classes, and
**position does not predict class**: Y155C and R550Q left levels intact, kinase-domain
substitutions were destabilised five- to tenfold, and Q921H in the same region was
indistinguishable from wild-type.

No clinical laboratory currently makes this distinction when reporting a *BUB1B* variant.
If the Experiment 1 assay discriminates classes reliably, it becomes a **reusable
functional axis for BUB1B variant interpretation**. Two missense variants with identical
REVEL scores and identical ACMG classifications may belong to different classes with
different therapeutic implications; nothing in the standard workflow distinguishes them.

For a disease with fewer than fifty reported cases worldwide, every variant moved from
uncertain to functionally classified is a substantial fraction of what is known.

### For rare-disease repurposing generally

The HSP90 case generalises beyond this gene. Any rare disease in which an unstable mutant
protein retains partial function creates the same trap: **the chaperone that preserves the
residual protein may be the target the downstream phenotype recommends inhibiting.**
Screening on the phenotype can select against the patient.

Making that conflict visible requires the mechanism to be characterised before the drug is
chosen.

### What would not follow

Success here would not establish that proteasome inhibition is safe or beneficial in a
child with constitutional mosaic aneuploidy. It would establish that the mechanism
operates in patient cells and which of two competing effects dominates. The distance from
there to a therapy is the largest gap in this document.
## 11. Scalability

Three components transfer, at different scopes.

**The functional classification assay — other *BUB1B* variants, immediately.** Abundance,
half-life, chaperone dependence, function at equalised expression. Gene-specific but
variant-agnostic; MVA1 has enough reported missense alleles to build a class map.

**The genotype–mechanism veto — any rare disease with an unstable mutant protein.**
Identify the downstream phenotype, list drugs exploiting it, check each against the
upstream lesion for conflict. Requires no new technology, only that mechanism
characterisation precede candidate selection. Nothing about it is particular to aneuploidy
or to mitosis.

**The evidence-verification layer — any evidence-grounded proposal.** Retrieval, coverage,
anchoring and support tracked on separate axes so that a claim's failure mode is
attributable: source not retrieved, text not accessible, span absent, or claim
unsupported. The verifier is frozen by hash and evaluated against a preregistered
adversarial benchmark with categories registered in advance to fail. This is the most
general component and the least field-specific.

**What does not scale.** The proband's genotype, and access to patient-derived cells. The
proposal is written so a laboratory holding MVA cells could execute it; it does not assume
this team could.
## 12. Evidence Verification and Auditability

The proposal was developed with a closed-world evidence-verification workflow. Claims
were separated into retrieval, text-coverage, anchoring, evidential-support and
assertion-calibration states, so that a claim's failure mode is attributable rather than
collapsed into "unsupported." Therapeutic sources retrieved after the verifier corpus was
frozen were kept in a separate evidence layer, so expanding the drug analysis did not
alter the preregistered verification environment.

**The process changed the proposal.** Five examples:

1. **GR agonists were demoted** from lead to challenger after separating mechanistic
   strength from translational attractiveness.
2. **HSP90 inhibition moved** from apparent aneuploidy-directed candidate to
   genotype-conditioned veto branch, once the upstream conflict was found.
3. **Chloroquine was deprioritised** after its selectivity failed to transfer from
   trisomic mouse fibroblasts to human aneuploid lines — in the original study's own data.
4. **The unfavourable Tang result was retained**: checkpoint-mutant fibroblasts, closest
   to the BUB1B lesion, responded less than purely aneuploid ones.
5. **MG132 and an approved proteasome inhibitor were separated** as probe and candidate,
   preventing proof of mechanism from being read as clinical attractiveness.

The governing rule: **conclusion scope must not exceed verified observation scope.** The
objective is not to eliminate uncertainty but to make it visible and experimentally
actionable.

**Frozen identities.** Three, because an earlier single field called `verifier_sha256`
covered the decision logic *and* the corpus *and* the registry *and* the run date, so it
changed when nothing logical had — the identifier asserted more than its name represented.

| Identity | SHA-256 |
|---|---|
| Verifier logic | `489e04ad03f2d74b6932f4780d49a8896041e3c33e40d6e7f9efd35c108c7536` |
| Retrieval policy | `a4c1597f887c91d5c6cd0671d5084af897aed0104e48272a06822ee8df41a1e7` |
| Preregistration | `f4ec3d6c4b0f82b0d8d163032e32a430e39bf2598b64a0e0f8f9f81a2da1d300` |

**Reproducibility, tested rather than argued.** The verifier is public and executable at
`kaggle.com/code/fernandosr85/track-2-evidence-verification`. Across three runs on three
consecutive days the discovery corpus drifted every time — 302, then 301, then 300 unique
records — while `verifier_logic_sha256`, `retrieval_policy_sha256` and the 25-case
`mechanical_cases_sha256` were byte-identical, and every benchmark figure and invariant
reproduced exactly. Under the earlier single-field design the identifier would have changed
on all three runs with no decision having changed. The case hash is stable because the
mechanical cases are drawn from the seven full-text documents, retrieved by identifier,
rather than from the drifting corpus.

The logic hash is stable across corpus drift and across days; the run environment hash is
not, by design. All artefacts and a verification command are in the repository.

**Status of the benchmark, stated plainly.** The preregistration was signed before any
test case existed. Twenty-five mechanical cases have been executed — supported 10/10,
wrong source 5/5, verb inflation 5/5, entity swap 0/5 as predicted — but their outcomes
were known before the preregistration was written, so they are a **regression suite, not
prospective validation**. The fifteen semantic cases that would constitute the blind test
**do not exist**. Neither the author nor the assistant that audited this work may write
them: both have read the verifier's implementation, and cases written with that knowledge
would be white-box adversarial rather than blind. Three categories therefore report
`NOT RUN` — never as passed.

## 13. Data Handling, Tooling and Declarations

### Data handling

**No data derived from the proband's genome was transmitted to any external service.**
Literature retrieval used gene- and disease-level queries only — `BUB1B`, `BubR1`, mosaic
variegated aneuploidy — enforced in code by a query guard with a self-test that aborts if
a controlled-data pattern passes or a gene-level query is blocked. Sources were resolved
by publication identifier.

The guard blocks the VCF sample identifier, HPO term identifiers, rsIDs, HGVS coding and
protein notation, and genomic coordinates. Blocking rsIDs is deliberately conservative: an
rsID is public, but querying literature by the proband's specific variant narrows toward
the individual, and the mechanism argument does not require it.

Variant identifiers in this report are those already published in the Track 1 submission,
released under CC BY 4.0.

All controlled data will be deleted within 30 days of the hackathon close, across every
environment under our control, with attestation to
`RarediseaserealkidMVAhackathon2026@synapse.org`.

### Tooling declaration

External services, assessed against the Processor / Recipient test set out by the Sage
Privacy Office — each returns a result, acquires no rights over the input, and cannot use
it for its own purposes:

| Service | Plan / terms | Data handling | Used for |
|---|---|---|---|
| Anthropic API, Claude | commercial terms | no training on customer content | analysis design, literature synthesis, code review, drafting |
| Europe PMC REST | public academic API | gene and disease terms, publication identifiers only | literature retrieval, full text |
| NCBI E-utilities / PMC | public API, identified caller | as above | literature retrieval, full-text fallback |

No external splice-prediction service was called. No LLM was given access to controlled
data at any point.

### A note on the Track 1 result

The Track 1 submission received a full match at rank 1 against the clinically confirmed
answer, which establishes the variant pair. It does not establish the molecular behaviour
of either allele, and the qualitative panel review of Track 1 methods has not yet taken
place. This proposal treats the genotype as its starting point and the functional class of
`p.Asn1002Lys` as open.

### Acknowledgement

> This work was made possible through the Hackathon, organized by Sage Bionetworks in
> partnership with the MVA Society, Hugging Face, and BEACON (The Benchmarking,
> Evaluation, and Assessment Consortium for Science), with prize sponsorship from AWS and
> Anthropic. We are deeply grateful to the child and their family who generously
> contributed their data and their story to advance research into this rare disease. We
> acknowledge their trust in making this Hackathon possible.

**Dataset citation.** Any publication arising from this work will cite the dataset using
the reference given on the hackathon's Synapse page as it stands at the time of
publication.

**Re-identification.** No public communication about this work includes information capable
of re-identifying the child or the family beyond what the family has already made public.

This report and its accompanying artefacts are released under CC BY 4.0. The executable
copy of the verifier hosted on Kaggle carries Apache 2.0, a code licence, which does not
conflict with the submission: the repository copy of the same notebook, and every artefact
it produces, remain under CC BY 4.0.
## Conclusion

Track 2 begins with a genetically defined BUB1B-MVA case but does not assume that genotype
alone specifies a therapy.

The unresolved molecular behaviour of `p.Asn1002Lys` is the decision point. Classifying it
can support a residual-protein rescue strategy, eliminate that strategy, redirect the work
toward downstream aneuploidy vulnerabilities, or challenge the causal premise inherited
from Track 1.

Among the axes examined, proteasome dependency has the strongest mechanistic support. Its
relevance is strengthened — and complicated — by evidence that proteasomal degradation
also regulates the abundance of selected unstable BubR1 mutants. That dual role creates a
falsifiable proteostasis-switch hypothesis, and the HSP90 case shows why the ordering
matters: a compound the downstream phenotype recommends may be the one the upstream lesion
rules out.

The intended output is not a recommendation to treat MVA with a proteasome inhibitor. It
is a decision framework capable of determining whether that idea deserves to survive the
first experiment.

**And it may not.** If `p.Asn1002Lys` proves stable and functionally near wild-type, it is
not the second hit, and this proposal loses the premise it was built on. That outcome is
registered in advance, in Section 7, alongside three others that each close a branch.

**The experiment can destroy the idea it was built to test. That is the point.**

## References

- Suijkerbuijk SJE, van Osch MHJ, Bos FL, Hanks S, Rahman N, Kops GJPL. Molecular causes
  for BUBR1 dysfunction in the human cancer predisposition syndrome mosaic variegated
  aneuploidy. *Cancer Res* 2010. PMC2887387.
- Ippolito MR, Zerbib J, Eliezer Y, et al. Increased RNA and protein degradation is
  required for counteracting transcriptional burden and proteotoxic stress in human
  aneuploid cells. *Cancer Discov* 2024;14(12):2532–2553. doi:10.1158/2159-8290.CD-23-0309
- Tang YC, Williams BR, Siegel JJ, Amon A. Identification of aneuploidy-selective
  antiproliferation compounds. *Cell* 2011;144(4):499–512. PMC3532042.
- Overlack K, Primorac I, Vleugel M, et al. A molecular basis for the differential roles of
  Bub1 and BubR1 in the spindle assembly checkpoint. *eLife* 2015. PMC4337726.
- Half the chromosome it used to be: identifying cancer treatments targeting aneuploid
  losses. *Genes* 2025;16(6):708. doi:10.3390/genes16060708
- BUB1B monoallelic germline variants contribute to prostate cancer predisposition by
  triggering chromosomal instability. *J Biomed Sci* 2024. doi:10.1186/s12929-024-01056-z
- Hanks S, Coleman K, Reid S, et al. Constitutional aneuploidy and cancer predisposition
  caused by biallelic mutations in BUB1B. *Nat Genet* 2004.
- Pejaver V, Byrne AB, Feng BJ, et al. Calibration of computational tools for missense
  variant pathogenicity classification. *Am J Hum Genet* 2022.
