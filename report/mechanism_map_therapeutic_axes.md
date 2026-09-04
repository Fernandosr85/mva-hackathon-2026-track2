# Track 2 — Mechanism Map, Block 2: Therapeutic Axes

**MVA Hackathon 2026 · Fernando (HF: `fernandosr85`)**
**Status:** working document. Every claim carries its source and its verification state.

**Verification states used throughout**

| Tag | Meaning |
|---|---|
| `[FULL TEXT]` | verified against retrieved full text held in `evidence_v1/fulltext_xml/` |
| `[ABSTRACT]` | verified against an abstract in the frozen 301-record corpus |
| `[RETRIEVED]` | verified by targeted retrieval outside the frozen corpus |
| `[GAP]` | asserted somewhere but not verified here |

The frozen v3 corpus is **not modified** by this document. Therapeutic sources sit in a
separate layer so the benchmark's evidence base stays intact.

---

## 1. The pivotal question, and why it comes first

Everything below branches on one unanswered fact:

> **Is `p.Asn1002Lys` a low-abundance but function-competent BubR1 mutant?**

Suijkerbuijk et al. divide MVA-associated *BUB1B* mutations into two classes — those
that reduce BubR1 protein abundance and those that do not `[FULL TEXT]`:

> "The previous analyses showed that the MVA-associated substitution and truncation
> mutations in BUBR1 could be divided in two categories: those that affect its protein
> abundance, and those that don't."

And for the low-abundance class, scarcity rather than dysfunction is the defect
`[FULL TEXT]`:

> "the inability of the 'low abundance' mutants to restore BUBR1 functionality raised
> the possibility that these mutations affected chromosome segregation primarily by
> lowering BUBR1 protein abundance without affecting BUBR1 function"

Their causal model is explicit `[FULL TEXT]`:

> "we propose that chromosomal instability in MVA patients carrying BUB1B mutations is
> a result of low BUBR1 protein abundance."

**Position does not settle it.** Kinase-domain substitutions were destabilised 5–10 fold,
but Q921H — in the same region — was "indistinguishable from wild-type LAP-BUBR1, both
on protein level and functionality" `[FULL TEXT]`. Residues studied: Y155C, R550Q, R727C,
R814H, L844F, I909T, Q921H, L1012P. **N1002K was not among them.**

### Four outcomes, four different proposals

| N1002K proves to be | Consequence |
|---|---|
| low abundance, function competent | rescue arm becomes the lead |
| stable, function defective | stabilisation has no rationale; vulnerability arm only |
| stable, near wild-type | the allele's causal contribution needs re-examination before any drug argument |
| low abundance **and** function defective | raising abundance may not suffice; both arms weaken |

The fourth is not a formality. The two categories were defined across a mutation panel,
not proven mutually exclusive for an untested residue.

### Measurements that answer it

Protein abundance; turnover and half-life under cycloheximide; response to
geldanamycin and to a proteasome inhibitor; functional competence when expression is
equalised; SAC activity; chromosome alignment and missegregation rate.

This is the assay Suijkerbuijk already describes. It is not a new experimental design.

---

## 2. Rescue arm — proteasomal clearance of an unstable mutant

### What is verified

In U2OS cells expressing I909T or L1012P mutant BubR1 `[FULL TEXT]`:

- HSP90 inhibition (geldanamycin) severely decreased mutant levels; wild-type showed
  only minor change
- "inhibition of proteasomal degradation with MG132 prevented the enhanced protein
  turnover caused by HSP90 inhibition"
- "Thus, HSP90 activity is needed for folding of BUBR1 substitution mutants and for
  preventing their clearance via proteasomal degradation"

### What follows, and what does not

**Supported:** proteasomal degradation contributes to the loss of specific unstable
BubR1 missense proteins.

**Not supported:** that a proteasome inhibitor rescues BubR1 function in N1002K. Two
steps are missing and both must be shown:

```
proteasome inhibition
  → N1002K clearance ↓        [plausible if N1002K is unstable — UNTESTED]
  → residual BubR1 ↑          [UNTESTED]
  → SAC activity ↑            [UNTESTED]
  → missegregation ↓          [UNTESTED]
```

**Probe versus therapy.** MG132 is a 5-hour tool compound in an overexpression system.
Bortezomib is the approved drug acting on the same pathway. They are not
interchangeable, and the distinction must survive into the report.

---

## 3. Vulnerability arm — proteasome dependency is the mechanistic lead

### Strongest evidence in the set `[ABSTRACT]` + `[RETRIEVED]`

Ippolito, Zerbib, Eliezer et al., *Cancer Discovery* 2024
(`10.1158/2159-8290.CD-23-0309`), in the frozen corpus:

> "aneuploid cells mitigate proteotoxic stress by reducing protein translation and
> increasing protein degradation, rendering them more sensitive to proteasome
> inhibition. These findings were recapitulated across hundreds of human cancer cell
> lines and primary tumors, **and aneuploidy levels were significantly associated with
> the response of patients with multiple myeloma to proteasome inhibitors**."

The evidence chain: isogenic RPE1 clones at graded aneuploidy → hundreds of cancer cell
lines → primary tumours → **patient response**. No other axis here reaches clinical data.

`[GAP]` Whether bortezomib specifically was the compound used in their experiments was
not verified. The clinical anchor is the drug class in myeloma, where bortezomib is
standard.

### Supporting, same direction `[ABSTRACT]`

- UBE2H identified as "a top aneuploid-selective dependency" — paired CRISPR screens,
  2026, `10.64898/2026.04.26.720636`. Ubiquitin-conjugating, same pathway.
- PRMT5:MEP50 overexpression "renders cancer cells less sensitive to proteasome
  inhibitors and CIN" — 2025, `10.1101/2025.09.12.675799`. Modulates the same axis.
- Proteostasis failure with autophagy saturation and compromised mitophagy in
  aneuploidy-induced senescence — Dev Cell 2021, `10.1016/j.devcel.2021.06.009`.

---

## 4. The proteasome paradox — the most discriminating feature of this proposal

The same intervention has two predicted effects in this genotype, pointing in opposite
therapeutic directions:

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
        CIN ↓ ?                      tumour clone cleared ?
```

**Consequence for experimental design.** Viability alone cannot distinguish these. A
single readout showing "more cells" or "fewer cells" leaves the mechanism unidentified.
The experiment must measure, in the same cells:

BubR1 abundance · BubR1 turnover · SAC function · chromosome missegregation ·
aneuploidy burden · proteotoxic-stress markers · viability and apoptosis

A dose × time matrix is worth running, since stabilisation and cytotoxicity may have
separable kinetics — but that separability is a hypothesis, not an expectation.

---

## 5. HSP90 — a genotype-mechanism veto, verified on both sides

**Downstream, HSP90 inhibition looks attractive** `[RETRIEVED]`. Tang, Williams, Siegel
and Amon, *Cell* 2011 (PMC3532042) identified AICAR, 17-AAG and chloroquine as
selectively antagonising proliferation in aneuploid cells; aneuploid MEFs showed
"increased sensitivity to the Hsp90 chaperone inhibitor 17-AAG"; AICAR and 17-AAG were
effective against aneuploid human cancer lines, especially combined.

**Upstream, it may be self-defeating** `[FULL TEXT]`. HSP90 activity is required for the
folding of BubR1 substitution mutants and for preventing their proteasomal clearance.
In a genotype whose defect is low abundance of an unstable missense protein, inhibiting
HSP90 attacks the downstream consequence while deepening the primary cause.

> **17-AAG is a validated aneuploidy vulnerability that may be mechanistically
> self-defeating in an unstable-BubR1 genotype.**

The correct label is **deprioritised pending the N1002K classification**, not
contraindicated. No clinical contraindication for this variant has been established.

This is the clearest demonstration in the proposal of why phenotype-level drug
screening is insufficient: the downstream state and the upstream lesion recommend
opposite actions on the same target.

---

## 6. Effect size runs the wrong way in the closest model

`[RETRIEVED]` Tang 2011, verbatim from a summary of the paper:

> "cultures of MEFs that are euploid but predisposed to chromosomal instability by dint
> of a mutation in mitotic checkpoint genes are also growth inhibited by AICAR and
> 17-AAG, **but to a lesser effect than for purely aneuploid MEFs**"

MVA is a checkpoint-driven CIN state, not a defined constitutional trisomy. **Among the
Tang 2011 models, the one mechanistically closest to the BUB1B lesion showed the weakest
response.** Checkpoint-driven CIN resembles the BUB1B defect more than a fixed trisomy
does; this is not a claim about overall model fidelity. This must be stated, not buried: it is a
signal that the aneuploidy-vulnerability transfer to MVA may be weaker than the
headline results suggest.

`[RETRIEVED]` A species caveat in the same direction: mice homozygous for hypomorphic
*BubR1* alleles, expressing ~10% of normal BubR1, developed progeroid and age-related
pathology — "instead of tumors". Human MVA1 gives cancer predisposition. These are not
the same molecular defect — mouse hypomorphs and human biallelic variants differ — but
**related severe BubR1 insufficiency produces markedly different organismal phenotypes
across species**, which is reason for caution transferring in either direction.

---

## 7. GR agonists — translational challenger, weaker mechanism

`[ABSTRACT]` *Genes* 2025, `10.3390/genes16060708`:

> "Pathway-altering compounds that selectively reduce viability in cells with aneuploidy
> profiles were discovered, including an unexpectedly prominent number of glucocorticoid
> receptor agonists."

Dexamethasone and prednisolone are approved, cheap, have decades of paediatric dosing
experience, and are backbone agents in ALL protocols — one of the three canonical MVA1
malignancies.

**That is translational attractiveness, not mechanistic strength.** The study is a
TCGA + PRISM integration: an association between aneuploidy profiles and drug response,
presented by its authors as a hypothesis. It has no isogenic system, no causal
perturbation, no patient-response analysis.

An earlier draft of this map ranked GR agonists ahead of the proteasome axis. That
ranking confused ease of administration in a child with strength of evidence, and is
withdrawn.

`[GAP]` No evidence that GR agonists have preventive or selective activity in
constitutional MVA. The ALL connection is contextual relevance only.

---

## 8. Chloroquine — deprioritised by the original study's own transfer test

`[RETRIEVED]` Tang 2011 found chloroquine selective in trisomic MEFs. In human aneuploid
cancer lines, "AICAR and 17-AAG, but not chloroquine, showed significant
anti-proliferative activity."

The paper contains its own transferability experiment, and chloroquine failed it. Low
priority — and a useful demonstration that this analysis discards candidates rather
than collecting hits.

---

## 9. Taxanes — pharmacology of the state, not a candidate

`[ABSTRACT]` `10.1186/s12929-024-01056-z`, in the frozen corpus:

> "BUB1B variants lead to decreased BubR1 expression and/or stability, which promotes
> increased premature chromatid separation and, consequently, triggers CIN, driving
> resistance to Taxol-based therapies."

Taxanes engage the spindle assembly checkpoint and require a functional SAC to hold
cells in mitosis until death. A cell with a crippled checkpoint slips through.

Its role here is not as a candidate but as evidence that **the BUB1B lesion changes
pharmacological response, not only cytogenetics**. That is what makes repurposing a
coherent question for this genotype at all.

It also carries a clinical note worth stating plainly: BubR1 status may be informative
about what *not* to give.

---

## 10. Ranking

| # | Axis | Role | Strongest evidence |
|---|---|---|---|
| 1 | Proteasome | **mechanistic lead** | isogenic → cell lines → tumours → patient response |
| 2 | GR agonists | translational challenger | TCGA/PRISM association only |
| 3 | HSP90 / 17-AAG | conditional veto branch | vulnerability verified; upstream conflict verified |
| 4 | AICAR / energy stress | supporting | p53-mediated apoptosis in trisomic MEFs |
| 5 | Chloroquine | deprioritised | failed the original study's human-line transfer |
| — | Taxanes | state pharmacology | resistance evidence; not a proposal |

Within the proteasome axis: **MG132 = mechanistic probe. Bortezomib = approved
translational candidate.** Keeping these apart prevents proof of mechanism from being
read as clinical attractiveness.

---

## 11. Central thesis

> **BUB1B-MVA may create a genotype-dependent proteostasis switch.** If `p.Asn1002Lys`
> is a functionally competent but unstable BubR1 mutant, proteasome inhibition could
> reduce its clearance and partially restore checkpoint function. If it is not
> rescuable by stabilisation, the same downstream aneuploid state may instead create an
> enhanced proteasome dependency that proteasome inhibition exploits. **The pivotal
> experiment is not whether a proteasome inhibitor is active, but which of these
> competing mechanisms dominates in the N1002K context.**

This is not a proposal to give bortezomib to a child with MVA. It is a proposal for
**ex vivo mechanistic investigation of an approved drug class**, with an explicit
genetic condition, an explicit competing mechanism, and stated falsification criteria.

---

## 12. Transfer gaps, stated rather than implied

**None of the cited therapeutic-vulnerability studies tests BUB1B-MVA cells.**

An earlier draft of this document wrote "no model used in any cited work is MVA". That
was false: Suijkerbuijk et al. used cell lines derived from MVA patients, and those cells
carry the upstream mechanism this entire proposal rests on. The correction matters
because the two halves of the argument have different evidentiary footing.

**Patient-derived MVA cells support the upstream BubR1 mechanism. Transfer of the
downstream aneuploidy vulnerabilities to MVA is untested.**

| Model | What it is | Distance from this case |
|---|---|---|
| **MVA patient fibroblasts** | **the condition itself, human** | **used for the upstream mechanism; never tested against any drug here** |
| Trisomic MEFs | constitutional single-chromosome trisomy, mouse | not mosaic, not variegated, not human |
| CIN-prone MEFs | checkpoint mutation, mouse | closest available — and gave the weakest drug effect |
| RPE1 isogenic clones | engineered aneuploidy, human, immortalised | not constitutional, not mosaic |
| Cancer cell lines | somatic aneuploidy in transformed cells | transformation confounds |
| Myeloma patients | adults with malignancy | not constitutional aneuploidy, not paediatric |

**Selectivity cannot be assumed.** In MVA the aneuploid cells are the child's own
tissues, not only a tumour clone. Any drug that exploits aneuploidy may act on normal
aneuploid cells too. This is the principal translational barrier and belongs in the
proposal, not in a footnote.

---

## 13. What would falsify the proposal

- **N1002K proves stable and near wild-type** — the allele's causal contribution needs
  re-examination before any drug argument built on it stands.
- **N1002K is unstable but proteasome inhibition does not raise its level** — the
  rescue arm has no mechanism.
- **BubR1 level rises but SAC function does not** — abundance was not the limiting
  variable, contrary to the Suijkerbuijk model.
- **MVA cells are no more sensitive to proteasome inhibition than matched controls** —
  the aneuploidy-vulnerability transfer does not reach this context.

Any of the four removes a branch. The first removes the proposal.

---

## 14. Tooling declaration

- Europe PMC REST and NCBI E-utilities — retrieval by identifier and by gene- and
  disease-level query. Public APIs. No patient data in any request.
- Targeted web retrieval for three sources outside the frozen corpus (PMC3532042,
  PMC11611680, PMC12192454). Verified against retrieved text where quoted; marked
  `[GAP]` where not.
- Anthropic API, Claude, commercial terms, no training on customer content — literature
  synthesis and code review. Claims produced this way are inputs to verification, never
  its output.
