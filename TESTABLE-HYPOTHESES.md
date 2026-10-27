# TESTABLE HYPOTHESES

## Musical Structural Intelligence and Open-Ended Evolution (MSI-OEE)

**Version:** 1.0.0  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Proposed, not empirically validated  
**Scope:** Falsifiable research hypotheses, controls, metrics, and evidence governance

> **Research principle:** A structural explanation earns its place by outperforming credible alternatives under declared conditions—not by redescribing a successful example after the fact.

## 1. Purpose and interpretation

This document translates MSI-OEE's conceptual claims into empirical propositions. A **Musical UIERU** is treated as a *candidate operational construct*, not an established natural kind. **Romantic Intelligence**, **OTHERS**, and **AI-native preference** are likewise proposed constructs requiring measurement and validation.

Each hypothesis specifies an independent variable or intervention, an observable outcome, an appropriate baseline, and a disconfirming result. Thresholds, sample sizes, exclusion rules, and statistical tests must be registered **before** examining held-out results. The example success criteria below are design targets, not reported findings.

**Evidence labels:** `HYPOTHESIS` (untested), `PILOT` (exploratory), `PRE-REGISTERED` (protocol frozen), `REPLICATED` (independent confirmation), `CONTESTED` (material counter-evidence), `NOT SUPPORTED` (prespecified test failed). Avoid using “validated” without naming the population, task, and conditions.

## 2. Experimental foundations

### 2.1 Shared data design

Use legally usable, documented musical material: controlled synthetic motifs; permissioned or appropriately licensed recordings/MIDI; and independently sourced, stylistically diverse material. Partition at the **composer, work, motif-family, and source-recording** levels where relevant to prevent near-duplicate leakage. Hold out entire styles, transformations, performers, or listener populations for transfer tests.

### 2.2 Baseline families

- **B0 — Surface:** pitch/rhythm n-grams, edit distance, chroma, onset and tempo features.
- **B1 — Conventional structural:** interval contours, motif discovery, alignment and graph-based music representations.
- **B2 — Learned:** pretrained audio/symbolic embeddings and sequence/generative models.
- **B3 — Matched-compute ablation:** same model capacity, training data, retrieval budget, and evaluation time without explicit UIERU/Relay/OTHERS components.
- **B4 — Human:** blinded listeners and qualified musicians, with disagreement reported rather than erased.

A favorable result against B0 alone is insufficient to establish a new structural mechanism. Whenever possible, compare against B1–B3 and report compute, model size, annotation cost, and human effort.

### 2.3 Evaluation and uncertainty

Report effect sizes and uncertainty intervals; use group-aware bootstrap or hierarchical models for repeated judgments; correct for multiple testing where appropriate. Measure reliability among raters and within raters over time. Preserve individual and group-level results instead of replacing divergent perspectives with a single universal score. Record negative results, failed transformations, and counterexamples.

## 3. Hypothesis register

### H01 — Musical unit identity survives declared transformations

**Claim.** An explicit candidate Musical UIERU representation predicts human-rated motif identity under a *prespecified* set of identity-preserving transformations better than surface representations.

**Intervention.** Apply controlled transposition, tempo scaling, instrumentation change, ornamentation, and rhythmic displacement to a held-out motif set; include identity-breaking perturbations.

**Measures.** Pairwise identity judgments, triplet ranking accuracy, calibration, and out-of-family transfer.

**Baselines.** B0, B1, B2, B3.

**Disconfirmation.** No reproducible advantage over strong baselines, or identity predictions collapse on unseen transformations. Identity may be perspective-specific rather than universal.

**Links.** [MSI-002](docs/MSI-002-Musical-UIERUs-Boundaries-and-Invariants.md), [CASE-001](cases/CASE-001-Motif-Transformation-and-Identity.md), [SPEC-001](specs/SPEC-001-Musical-UIERU-Contract.md).

### H02 — Unit boundaries depend on musical context

**Claim.** Context-conditioned segmentation better predicts perceived motif or phrase boundaries than fixed-window or context-free segmentation.

**Intervention.** Embed identical note sequences in different harmonic, metric, and phrase contexts; counterbalance presentation order.

**Measures.** Boundary F1 or tolerance-aware agreement, rater uncertainty, cross-context prediction.

**Baselines.** Fixed windows, conventional segmentation, context-free learned embeddings.

**Disconfirmation.** Context adds no out-of-sample explanatory power or improvements result solely from added parameters.

**Links.** MSI-002, CASE-001, SPEC-001.

### H03 — Structural and functional identities are separable

**Claim.** Listeners can judge a motif as structurally related across contexts while assigning it a different musical function.

**Intervention.** Recontextualize the same motif as opening, transition, accompaniment, or cadence-like material.

**Measures.** Separate structural-identity and functional-role ratings; within-participant dissociation.

**Baselines.** One-dimensional similarity scores and context-free classifiers.

**Disconfirmation.** Ratings do not dissociate reliably, or functional labels cannot be independently operationalized.

**Links.** MSI-002, MSI-003, CASE-001.

### H04 — Explicit Relay improves long-range musical organization

**Claim.** Under matched resources, a Relay-graph composer produces stronger long-range thematic development and structural coherence than a generation-only baseline.

**Intervention.** Generate pieces from identical prompts or seed motifs with and without explicit sequential, hierarchical, and transformative Relay planning.

**Measures.** Blind expert ratings, motif return/development tracking, section-level consistency, diversity, listening preference.

**Baselines.** B2 and B3; include an ordinary hierarchical composition planner.

**Disconfirmation.** No gain under blind evaluation, or apparent coherence comes at a large cost to musical interest/diversity.

**Links.** [MSI-003](docs/MSI-003-Structural-Relay-and-Musical-Composition.md), [SPEC-002](specs/SPEC-002-Transformation-and-Relay-Operators.md).

### H05 — Soft contracts can preserve identity while enabling expressive change

**Claim.** A declared set of soft constraints permits more expressive variants at a comparable structural-identity retention rate than either rigid constraints or unconstrained generation.

**Intervention.** Compare rigid, soft, and unconstrained transformation policies on the same motifs.

**Measures.** Identity retention, perceived expressiveness, novelty, violation severity, and failure rates.

**Disconfirmation.** Soft contracts yield no Pareto improvement, or violations cannot be characterized consistently.

**Links.** MSI-003, MSI-004, SPEC-002.

### H06 — Controlled deviation can improve expressive value

**Claim.** For some musical contexts and listeners, bounded timing, dynamics, articulation, or harmonic deviations increase perceived expressiveness relative to mechanically exact realizations.

**Intervention.** Apply parameterized deviations with matched loudness, quality, and performance conditions; include random-deviation controls.

**Measures.** Expressiveness, preference, perceived intentionality, and musical appropriateness.

**Baselines.** Quantized performance, human performance, random perturbation.

**Disconfirmation.** Deviations are no better than random noise or any benefit disappears under blinded replication.

**Interpretation.** A positive result supports *context-dependent expressive deviation*, not subjective experience or a universal theory of Romantic Intelligence.

**Links.** [MSI-004](docs/MSI-004-Romantic-Intelligence-and-Creative-Deviation.md).

### H07 — Aesthetic evaluation is perspective-conditioned

**Claim.** Subject- and context-aware scoring models predict held-out listener judgments better than a single global preference score, especially across heterogeneous listener groups.

**Intervention.** Compare global and perspective-conditioned models using consented listener history, cultural context, expertise, and task-specific judgments.

**Measures.** Calibration, predictive log loss, rank agreement, subgroup performance, and fairness/error disparity.

**Baselines.** Population-average and group-agnostic personalized models.

**Disconfirmation.** Perspective conditioning adds no generalizable value or merely memorizes participant identity.

**Links.** [MSI-005](docs/MSI-005-Perspective-Scoring-and-Musical-Worldviews.md), [SPEC-003](specs/SPEC-003-Perspective-Scoring-Schema.md).

### H08 — Disagreement carries discoverable information

**Claim.** Persistent human–model or cross-listener disagreement can help identify reproducible, previously omitted musical predictors.

**Intervention.** Compare candidate-feature discovery from a preregistered disagreement sample against random and uncertainty-matched samples.

**Measures.** Independent replication rate, incremental predictive validity, feature interpretability, and false-discovery rate.

**Baselines.** Random sampling, active learning by uncertainty, conventional error analysis.

**Disconfirmation.** Disagreement-guided discovery offers no higher validated yield or primarily captures noise and demographic confounds.

**Links.** MSI-005, [MSI-006](docs/MSI-006-Musical-Distance-OTHERS-and-Open-Evidence.md), [SPEC-004](specs/SPEC-004-OTHERS-Evidence-and-Validation.md).

### H09 — Transformation-aware similarity reduces misleading comparisons

**Claim.** Transformation-aware structural comparison improves recognition of related motifs while avoiding excessive false positives on common musical conventions.

**Intervention.** Evaluate transformed positives, common-pattern negatives, and rare-pattern hard negatives with source-family isolation.

**Measures.** Precision–recall, false-positive rate at fixed recall, calibration, and rarity-stratified performance.

**Baselines.** Surface distances, learned embeddings, conventional motif alignment.

**Disconfirmation.** Performance degrades on common-pattern controls, or advantages vanish under held-out families.

**Caution.** This is a similarity study, **not** a legal plagiarism or infringement adjudicator.

**Links.** MSI-006, [CASE-002](cases/CASE-002-Musical-Similarity-and-OTHERS.md).

### H10 — OTHERS can be converted into reusable evidence-backed features

**Claim.** A governed OTHERS pipeline produces more independently useful new structural features than ad hoc residual labeling.

**Intervention.** Compare preregistered residual → hypothesis → counter-evidence → held-out validation → promotion workflow with ungoverned feature addition.

**Measures.** Replicated feature yield, cross-task reuse, false promotion rate, provenance completeness, and maintenance cost.

**Baselines.** Standard feature engineering, residual clustering, unguided model expansion.

**Disconfirmation.** No advantage after accounting for annotation and computation costs, or promoted features fail replication.

**Links.** MSI-006, SPEC-004.

### H11 — Explicit structural memory supports transferable creative growth

**Claim.** A composer that retains validated new UIERUs and Relay operators improves on unseen composition tasks more reliably than a system that only accumulates outputs or examples.

**Intervention.** Run repeated composition/evaluation cycles with structural-memory, example-memory, and no-memory conditions under matched budgets.

**Measures.** Transfer performance, novelty without memorization, retention, compute efficiency, and failure recovery.

**Baselines.** Retrieval-augmented generation and finetuning with matched resources.

**Disconfirmation.** Structural memory yields no independent transfer gain or merely replays stored examples.

**Links.** [MSI-007](docs/MSI-007-AI-Musical-Creation-and-Structural-Evolution.md), SPEC-001, SPEC-002.

### H12 — Independent evaluators mitigate self-scoring drift

**Claim.** Separating candidate generation from independent, periodically refreshed evaluation reduces reward hacking and preserves external musical quality over iterative optimization.

**Intervention.** Compare self-scoring-only evolution with blind human panels, frozen external evaluators, adversarial tests, and evaluator rotation.

**Measures.** External quality trends, novelty, evaluator disagreement, overfitting gap, and exploit frequency.

**Disconfirmation.** Independent governance does not improve externally measured quality or blocks useful innovation disproportionately.

**Links.** MSI-007, SPEC-003, SPEC-004.

### H13 — Intermediate UIERUs can improve access to unfamiliar music

**Claim.** A sequence of structurally faithful intermediate arrangements improves listeners' comprehension of an unfamiliar musical pattern more than direct exposure alone.

**Intervention.** Randomize participants to staged translation, repeated exposure, explanatory text, and unrelated intermediate examples; use the AX-1-style controlled structure in CASE-003.

**Measures.** Recognition of hidden relationships, transfer to new variants, retention after delay, and preference as a **separate** outcome.

**Baselines.** Mere exposure, instruction-only, and unconstrained simplification.

**Disconfirmation.** No advantage beyond exposure, or apparent comprehension requires losing the target's declared invariants.

**Links.** [MSI-008](docs/MSI-008-Human-AI-Musical-Co-Evolution.md), [CASE-003](cases/CASE-003-Human-AI-Musical-Translation.md).

### H14 — Bidirectional Relay can outperform one-way alignment

**Claim.** A human–AI co-composition process that updates both structural proposals and human-facing explanations yields greater mutual task success than AI-only adaptation to static preference labels.

**Intervention.** Compare one-way preference optimization, human-only iterative editing, and bidirectional structural Relay with transparent revision histories.

**Measures.** Blind musical-quality ratings, structural novelty, user agency, task completion, retention, and explanation fidelity.

**Disconfirmation.** No improvement under equal interaction budgets, or the process reduces user control or diversity.

**Links.** MSI-008, CASE-003, SPEC-003.

### H15 — Musical discoveries can transfer back to general SI mechanisms

**Claim.** At least some mechanisms discovered in musical boundary inference, soft-contract Relay, or perspective-conditioned scoring improve a *nonmusical* structural task when transferred with minimal domain-specific changes.

**Intervention.** Freeze the musical mechanism, then evaluate it on independent symbolic-sequence, interaction, or structured-creative tasks against domain-specific baselines.

**Measures.** Transfer gain, adaptation cost, failure cases, and generality limits.

**Disconfirmation.** Gains require extensive task-specific redesign or disappear outside music.

**Links.** [MSI-001](docs/MSI-001-From-Music-to-Musical-Structural-Intelligence.md), [FUTURE-DIRECTIONS](FUTURE-DIRECTIONS.md).

## 4. Dependency map and suggested priority

| Stage | Hypotheses | Why first? |
|---|---|---|
| A — Representation | H01–H03 | Determine whether the proposed unit and identity distinctions are measurable. |
| B — Relay and expression | H04–H06 | Test compositional utility and meaningful deviation. |
| C — Evaluation and evidence | H07–H10 | Establish perspective and OTHERS governance before recursive growth. |
| D — Structural evolution | H11–H12 | Test accumulation and protect against self-scoring drift. |
| E — Human–AI translation | H13–H14 | Evaluate cross-subject learning and collaboration. |
| F — Generalization | H15 | Test whether music findings genuinely Relay into broader SI. |

Prioritize **H01, H02, H07, H09, and H13** as early pilots: they have comparatively clear manipulations, outcomes, and baseline families. Do not interpret exploratory pilot effects as confirmatory evidence.

## 5. Minimum preregistration template

For each study, record:

1. **Hypothesis ID and version**; responsible investigators and study date.
2. **Population and sampling:** inclusion criteria, musical training, listening equipment, consent and privacy plan.
3. **Materials:** source, rights, generation method, partition keys, and exclusion rules.
4. **Manipulation and controls:** randomization, blinding, and confound checks.
5. **Primary and secondary outcomes:** operational definitions and measurement reliability.
6. **Baselines and ablations:** compute, data, parameters, and human effort.
7. **Sample-size rationale:** power analysis or justified precision target; no invented universal sample size.
8. **Statistical plan:** effect size, interval, multiplicity, subgroup and missing-data handling.
9. **Failure conditions:** prespecified falsifiers and competing explanations.
10. **Release policy:** reproducibility artifacts, anonymization, counter-evidence and limitations.

## 6. Evidence record schema (illustrative YAML)

```yaml
hypothesis_id: H01
study_id: MSI-OEE-H01-PILOT-001
status: HYPOTHESIS
version: 1.0.0
construct: transformation_conditioned_motif_identity
population: pending_preregistration
materials:
  provenance: pending
  rights_review: pending
  train_test_separation: composer_and_motif_family
conditions:
  - candidate_musical_uieru
  - conventional_structural_baseline
  - learned_embedding_baseline
primary_outcome: held_out_human_identity_prediction
statistical_plan: pending_preregistration
counter_evidence_registry: []
results: null
claim_scope: none_until_evaluated
```

The schema is an example, not a claim that the study has been run. In a future implementation, records should link to [SPEC-001](specs/SPEC-001-Musical-UIERU-Contract.md), [SPEC-003](specs/SPEC-003-Perspective-Scoring-Schema.md), and [SPEC-004](specs/SPEC-004-OTHERS-Evidence-and-Validation.md).

## 7. Nonclaims and guardrails

- **No experimental results are asserted in this document.**
- A positive identity or similarity score does not establish a universal Musical UIERU ontology.
- Musical similarity is distinct from copying history and legal infringement.
- Functional AI preferences do not establish subjective pleasure, consciousness, or human-like emotion.
- Human listening judgments are valuable evidence but are not a single objective aesthetic ground truth.
- Producing more music is not equivalent to validated structural growth.
- “Open-ended” requires longitudinal evidence of genuinely new, transferable capabilities, not a finite novelty demonstration.
- A music-domain effect does not automatically validate a general SI theory.

## 8. Navigation

**Core theory:** [MSI-001](docs/MSI-001-From-Music-to-Musical-Structural-Intelligence.md) · [MSI-002](docs/MSI-002-Musical-UIERUs-Boundaries-and-Invariants.md) · [MSI-003](docs/MSI-003-Structural-Relay-and-Musical-Composition.md) · [MSI-004](docs/MSI-004-Romantic-Intelligence-and-Creative-Deviation.md) · [MSI-005](docs/MSI-005-Perspective-Scoring-and-Musical-Worldviews.md) · [MSI-006](docs/MSI-006-Musical-Distance-OTHERS-and-Open-Evidence.md) · [MSI-007](docs/MSI-007-AI-Musical-Creation-and-Structural-Evolution.md) · [MSI-008](docs/MSI-008-Human-AI-Musical-Co-Evolution.md).

**Research cases:** [CASE-001](cases/CASE-001-Motif-Transformation-and-Identity.md) · [CASE-002](cases/CASE-002-Musical-Similarity-and-OTHERS.md) · [CASE-003](cases/CASE-003-Human-AI-Musical-Translation.md).

**Specifications:** [SPEC-001](specs/SPEC-001-Musical-UIERU-Contract.md) · [SPEC-002](specs/SPEC-002-Transformation-and-Relay-Operators.md) · [SPEC-003](specs/SPEC-003-Perspective-Scoring-Schema.md) · [SPEC-004](specs/SPEC-004-OTHERS-Evidence-and-Validation.md).

**Research governance:** [OPEN-QUESTIONS](OPEN-QUESTIONS.md) · [VALIDATION-ROADMAP](VALIDATION-ROADMAP.md) · [FUTURE-DIRECTIONS](FUTURE-DIRECTIONS.md).

---

**MSI-OEE v1.0.0 — Sizhe Tan & GPT-Obot**  
*From musical structure to testable intelligence claims, with counter-evidence preserved.*
