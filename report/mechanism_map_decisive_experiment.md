# Track 2 — Block 3: The Decisive Experiment

**MVA Hackathon 2026 · Fernando (HF: `fernandosr85`)**

Block 2 ends with a question the literature cannot answer: **is `p.Asn1002Lys` a
low-abundance but function-competent BubR1 mutant?** Block 3 is the sequence that
answers it and, at each gate, decides which half of the proposal survives.

The design principle throughout: **no readout that cannot distinguish between the
competing mechanisms.** Viability alone would tell us the drug did something and
nothing about which mechanism produced it.

---

## Experiment 1 — Classify N1002K

**Question.** Which of the two Suijkerbuijk categories does the proband's missense
allele belong to?

This is not a new assay. It is the assay that paper already describes, applied to a
residue it did not test.

| Step | Measurement | Reads out |
|---|---|---|
| 1a | BubR1 abundance by quantitative immunoblot, N1002K vs wild-type | is the protein scarce? |
| 1b | Half-life under cycloheximide | is scarcity due to turnover? |
| 1c | Level after geldanamycin (HSP90 inhibition) | does folding depend on HSP90? |
| 1d | Level after proteasome inhibition | is clearance proteasomal? |
| 1e | Function at **equalised** expression — SAC activity, chromosome alignment, cold-stable microtubules | is the protein defective, or merely scarce? |

Step 1e is the one that separates the categories, and it is the step most likely to be
skipped. Without equalising expression, a functional deficit cannot be attributed to
the mutation rather than to its abundance.

### What each result means

| Outcome | Class | Consequence |
|---|---|---|
| Low abundance, short half-life, function normal when equalised | low-abundance, competent | **rescue arm proceeds** |
| Low abundance, function still impaired when equalised | both defects | stabilisation alone insufficient; rescue arm weakens severely |
| Normal abundance, function impaired | stable, defective | rescue arm has no rationale; vulnerability arm only |
| Normal abundance, function near wild-type | neither | **the allele's causal contribution requires re-examination before any drug argument built on it stands** |

The fourth outcome would not merely redirect the proposal. It would call into question
whether N1002K is the second pathogenic allele at all — and Track 1 already reported
that allele as a VUS with REVEL in the indeterminate band and phase undemonstrated.
The experiment is capable of undermining its own premise.

---

## Gate A

```
        Experiment 1
             │
   ┌─────────┴─────────┐
   │                   │
low abundance      stable, or
+ competent        defective when equalised
   │                   │
   ▼                   ▼
Experiment 2       skip to Experiment 3
(rescue + kill)    (vulnerability only)
```

---

## Experiment 2 — Proteasome perturbation, both mechanisms measured at once

**Question.** In N1002K cells, does proteasome inhibition stabilise residual BubR1 and
restore checkpoint function, kill the cells through proteotoxic stress, or both?

**Compounds.** MG132 as mechanistic probe — the compound Suijkerbuijk used, so the
result is directly comparable. A clinically approved proteasome inhibitor as
translational probe. **These are not interchangeable and the report must not treat them
as one candidate.**

**Design.** Dose × time matrix. Not because a "rescue window" is expected, but because
stabilisation and cytotoxicity may have separable kinetics — a hypothesis the matrix
tests rather than assumes.

### Readouts, all in the same cells

| Axis | Measurement | Which mechanism it reports |
|---|---|---|
| Protein | BubR1 abundance, turnover | rescue |
| Function | SAC activity, mitotic timing | rescue |
| Cytogenetic | chromosome missegregation, PCS rate, aneuploidy burden | rescue |
| Stress | proteotoxic-stress markers, ubiquitinated protein load | killing |
| Fate | viability, apoptosis | killing |

**The reason for measuring all five.** Block 2 shows the same intervention has opposite
predicted effects here. A viability curve alone cannot say which won. "Fewer cells"
could be aneuploidy-selective killing or generic toxicity; "more cells" could be
checkpoint rescue or nothing at all.

### Interpretation

| Pattern | Reading |
|---|---|
| BubR1 ↑, SAC ↑, missegregation ↓, viability preserved | rescue dominates — the strongest possible result |
| BubR1 ↑ but SAC unchanged | abundance was not the limiting variable; the Suijkerbuijk model does not extend to this residue |
| Stress ↑, apoptosis ↑, no BubR1 change | killing dominates; the rescue arm is dead here |
| Both, at different doses or times | the two mechanisms are separable — informative and unusual |
| Neither | proteasome axis does not apply to this genotype |

---

## Experiment 3 — Selectivity, the hardest question

**Question.** Is any observed effect selective for the BUB1B-deficient aneuploid state,
or does it act on matched cells too?

This tests the principal translational barrier in Block 2. In MVA the aneuploid cells
are the child's own tissues, not only a tumour clone. A drug that exploits aneuploidy
may act on constitutionally aneuploid normal tissue.

**Comparators, in order of strength**

1. Patient MVA fibroblasts vs parental or unaffected-relative fibroblasts — the closest
   available, and the comparison Suijkerbuijk used
2. Isogenic corrected line vs uncorrected, if gene editing is available
3. Euploid control lines — weakest, since background differs

**Endpoint.** A selectivity index: differential response between the MVA context and
matched control, at each measurement axis from Experiment 2.

**What would end the proposal here.** No differential response. If MVA cells are no more
sensitive than matched controls, the aneuploidy-vulnerability transfer does not reach
this context, and the killing arm has no basis in MVA regardless of what cancer cell
lines show.

---

## What is deliberately not proposed

**No dosing in a patient.** Nothing here is a treatment recommendation. The Official
Rules describe Track 2 submissions as hypotheses for follow-up, not evidence that a
medicine works, and this proposal stays inside that.

**No claim that bortezomib treats MVA.** The proposal is that an approved drug class
merits genotype-conditioned ex vivo investigation, with a competing mechanism named and
falsification criteria stated in advance.

**No HSP90 inhibitor arm.** Block 2 established the conditional veto: 17-AAG is a
validated aneuploidy vulnerability that may deepen the primary lesion in an
unstable-BubR1 genotype. If Experiment 1 shows N1002K is HSP90-dependent (step 1c), that
branch stays closed. If it shows the opposite, the branch reopens — and the veto itself
becomes a testable prediction rather than an assumption.

---

## Why this design, and not a screen

A compound screen over MVA cells would produce hits ranked by effect size. This sequence
produces a **decision**, and each gate can close a branch.

The HSP90 case is the argument in miniature. The downstream phenotype says HSP90
inhibition should help. The upstream genotype says it may remove the little functional
BubR1 that remains. A phenotype-level screen would have returned 17-AAG as a hit and
given no reason to doubt it.

> **A phenotype-level hit can point in the wrong therapeutic direction once the causal
> genotype is considered.**

That is why mechanism characterisation is not preamble to the drug proposal. It is the
thing that decides which drugs are candidates at all.

---

## Resources and honest limits

**What this requires.** Patient-derived MVA fibroblasts or an equivalent BUB1B model;
matched controls; standard immunoblotting, live imaging and cytogenetics; approved
compounds. No novel reagent, no new assay development.

**What is outside this proposal.** Access to the proband's cells, which the hackathon
dataset does not include. The experiment is specified so that a laboratory holding such
cells — or the MVA Society's research network — could run it, not so that it could be
run here.

**What none of this establishes even if every result is favourable.** That proteasome
inhibition is safe or beneficial in a child with constitutional mosaic aneuploidy. That
is a separate question requiring in vivo work, and the gap between "the mechanism
operates in patient cells" and "the drug helps the patient" is the largest one in this
document.
