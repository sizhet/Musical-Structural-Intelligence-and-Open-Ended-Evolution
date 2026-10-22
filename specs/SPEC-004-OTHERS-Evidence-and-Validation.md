# SPEC-004 — OTHERS Evidence and Validation

**Project:** Musical Structural Intelligence and Open-Ended Evolution (MSI-OEE)  
**Version:** 1.0.0  
**Status:** Proposed research specification; not an implemented or empirically validated standard  
**Authors:** Sizhe Tan & GPT-Obot  
**Related:** MSI-002, MSI-005, MSI-006, MSI-007, MSI-008; CASE-001, CASE-002, CASE-003; SPEC-001, SPEC-002, SPEC-003

## Abstract

This specification defines an auditable process for handling **OTHERS**: observations, disagreements, unexplained residuals, and candidate evidence that are not adequately represented by an existing musical similarity, identity, or valuation model. OTHERS is not a numerical correction that may be adjusted until a preferred answer appears. It is a governed discovery space in which an anomaly can become a candidate explanatory feature, undergo adversarial testing, and—if independently supported—be promoted into a scoped structural representation, Musical UIERU attribute, transformation operator, or perspective-specific scoring dimension. The specification establishes records, interfaces, uncertainty handling, provenance, validation gates, counter-evidence obligations, and anti-Goodhart safeguards. It explicitly separates acoustic resemblance, structural correspondence, source attribution, and legal infringement.

## 1. Scope and Normative Language

This document applies to exploratory musical-structure research involving human listening judgments, symbolic scores, audio features, learned embeddings, and cross-subject interpretation. The words **MUST**, **SHOULD**, and **MAY** denote proposed conformance requirements for implementations claiming compatibility with this specification; they do not imply that a formal standards body has adopted it.

In scope:

- Residual detection in musical identity, similarity, functional-role, and aesthetic-scoring tasks.
- Evidence capture and reproducible provenance.
- Candidate feature generation and controlled testing.
- Counter-evidence, replication, and promotion governance.
- Bidirectional relay to the UIERU registry, transformation operators, and perspective-scoring schema.

Out of scope:

- Automated determinations of copyright infringement or plagiarism.
- Claims about AI subjective musical experience.
- A universal metric for musical beauty or originality.
- Automatic conversion of statistical correlations into causal musical principles.

## 2. Core Principle: OTHERS Is an Open Evidence Space

For a declared task and perspective, a model may represent similarity using known evidence channels:

\[
\widehat{y}=f_\theta(x_{\mathrm{surface}},x_{\mathrm{structural}},x_{\mathrm{context}},p,t).
\]

Here, \(p\) denotes an evaluation perspective and \(t\) a task. An observed discrepancy \(r=y-\widehat{y}\), when the target supports numerical residuals, is a **signal for investigation**, not proof that an unknown musical feature exists. For categorical tasks, OTHERS may arise from disagreement patterns, calibration failures, systematic misclassifications, or anomalous expert descriptions.

A proposed extended model may take the form:

\[
\widehat{y}'=f_{\theta'}(x_{\mathrm{known}},z_{\mathrm{candidate}},p,t),
\]

but \(z_{\mathrm{candidate}}\) MUST be independently specified and tested. An unobserved OTHERS term MUST NOT be silently tuned as a free parameter to force agreement.

**Operational distinction:** unexplained observation → candidate explanation → tested hypothesis → scoped knowledge. Each transition requires a separate record.

## 3. Evidence Categories

| Category | Typical observation | Example candidate | Main confound |
|---|---|---|---|
| Structural residual | Human motif-identity judgment disagrees with interval-distance model | Accent placement or hierarchical grouping | Familiarity with the motif |
| Perceptual residual | Audio sounds related despite weak symbolic match | Timbre envelope or perceptual stream segregation | Playback device and loudness |
| Contextual residual | Same phrase is evaluated differently in different passages | Harmonic function or phrase position | Presentation order |
| Perspective residual | Musicians and non-musicians disagree systematically | Training-dependent attention | Demographic or genre exposure |
| Provenance residual | Similarity suggests possible relationship but origin is unknown | Documented access or historical transmission | Coincidence and shared conventions |
| Translation residual | AI-to-human musical adaptation improves comprehension but alters identity | Intermediate UIERU bridge | Mere exposure or simplification |
| Evaluation residual | A score improves while blinded human preference deteriorates | Reward-model shortcut | Selection on the test set |

Categories MAY overlap. They MUST NOT be treated as mutually exclusive or automatically causal.

## 4. Minimum Evidence Record

Each observation MUST carry:

1. **Identity:** immutable evidence ID, version, creation timestamp, and project namespace.
2. **Task:** precisely defined question (identity, similarity, preference, provenance, etc.).
3. **Objects:** references and hashes for musical items, excerpts, transformations, and versions.
4. **Representations:** symbolic/audio/embedding type, extraction procedure, preprocessing and model versions.
5. **Perspective:** evaluator role, consent-compatible pseudonymous ID where applicable, musical experience, relevant context, and stated scoring authority.
6. **Observation:** response, scale, uncertainty, trial order, and measurement conditions.
7. **Baseline:** model, features, parameters, training/test split, and prediction at time of observation.
8. **Discrepancy:** computation or qualitative reason the observation is unresolved.
9. **Provenance:** origin, licenses/permissions, collection method, and chain of custody where relevant.
10. **Limitations:** known confounds, missing data, and counter-explanations.
11. **Governance:** current status, reviewers, decisions, and audit history.

Missing fields MUST be explicitly marked `unknown`, `not_collected`, or `not_applicable`; they MUST NOT be fabricated.

## 5. Reference Data Contract

The following YAML is **illustrative**, not a machine-validated schema. A conforming implementation SHOULD publish JSON Schema or equivalent validation rules.

```yaml
spec: MSI-OEE/SPEC-004
spec_version: 1.0.0
record_id: others:case002:0007
record_version: 1
status: observed_unexplained
created_at: 2026-10-21T00:00:00Z  # illustrative timestamp only
research_task:
  task_id: motif_identity
  operational_definition: "Does B preserve the recognizable identity of A?"
  evaluation_scale: {type: ordinal, values: [0, 1, 2, 3, 4]}
objects:
  - {id: motif-A, representation: symbolic_midi, sha256: "REPLACE_WITH_HASH"}
  - {id: motif-B, representation: symbolic_midi, sha256: "REPLACE_WITH_HASH"}
transformation:
  operator_id: rhythm-accent-shift
  operator_version: 0.1.0
  parameters: {accent_shift_beats: 1}
perspective:
  subject_id: listener-pseudonym-017
  role: listener
  expertise: trained_musician
  context_id: listening-room-protocol-v1
observation:
  response: 1
  response_uncertainty: null
  trial_id: trial-0042
  randomized_order: true
baseline:
  model_id: interval-rhythm-baseline
  model_version: 0.3.0
  predicted_response: 4
  split_id: heldout-listeners-v1
discrepancy:
  kind: ordinal_prediction_disagreement
  magnitude: 3
  candidate_explanations: []
provenance:
  dataset_id: synthetic-motif-study-v1
  collection_protocol: protocol-v1
  rights_status: original_synthetic_material
  source_reference: case-002
limitations:
  - "Single judgment; no replication"
  - "Potential accent salience confound"
review:
  owner: research-team
  last_decision: pending
  audit_log: []
```

The illustrative timestamp, IDs, and measurements above are **synthetic placeholders**, not study results.

## 6. Evidence and Hypothesis Lifecycles

### 6.1 Evidence statuses

`observed_unexplained → triaged → candidate_linked → under_test → resolved | inconclusive | rejected | archived`

- **Observed unexplained:** a documented discrepancy exists.
- **Triaged:** data quality and baseline integrity are checked.
- **Candidate linked:** at least one explicit hypothesis is registered.
- **Under test:** preregistered or versioned tests are running.
- **Resolved:** evidence supports a scoped explanation, including a mundane confound.
- **Inconclusive:** evidence is insufficient or contradictory.
- **Rejected:** original anomaly is attributable to error or invalid measurement.
- **Archived:** retained for audit, without an active claim.

### 6.2 Candidate statuses

`proposed → specified → preregistered → tested → replicated → validated_in_scope | rejected | inconclusive → monitored`

A candidate MUST NOT skip directly from `proposed` to `validated_in_scope`. `validated_in_scope` is **not** universal validity. Material new counter-evidence MAY move it to `under_review`, `restricted`, or `retired`.

## 7. Candidate Hypothesis Contract

A candidate MUST state:

- **Mechanism:** what feature or relation may explain the residual.
- **Representation:** a reproducible feature extractor or annotation rule.
- **Scope:** tasks, musical genres, instruments, transformations, and listener populations to which the claim applies.
- **Predictions:** observable differences from current baselines.
- **Null and rival explanations:** simpler or competing mechanisms.
- **Disconfirmation criteria:** conditions under which the hypothesis should be rejected.
- **Evaluation protocol:** data partition, sample-size rationale, primary metrics, and analysis plan.
- **Safety and rights:** consent, licensing, and risk controls.
- **Relay target:** UIERU field, operator, scoring dimension, or other repository entry if supported.

A candidate that merely restates the observation in new terminology is not explanatory progress.

## 8. Validation Gates

### Gate G0 — Data integrity

Verify file hashes, annotation provenance, preprocessing, consent/permissions, duplication checks, and integrity of the declared train/test split. Failures return the record for correction.

### Gate G1 — Baseline and confound audit

Compare against simple and strong baselines; check whether loudness, recording quality, tempo, genre familiarity, or prompt wording explains the effect. An anomaly that disappears under proper controls is not promoted.

### Gate G2 — Operational specification

Freeze a candidate feature definition, predicted direction, and primary endpoint before final evaluation. Exploratory findings MUST be labeled exploratory.

### Gate G3 — Held-out test

Evaluate on unseen excerpts, transformations, or listener groups. Report effect sizes, uncertainty intervals, and negative results, not only p-values or average accuracy.

### Gate G4 — Counter-evidence and adversarial sandbox

Actively search for near misses, common musical conventions, adversarial transformations, and cases in which the candidate predicts the wrong identity or preference. Preserve unsuccessful examples.

### Gate G5 — Independent replication

Require replication on a distinct sample, recording condition, or research team when feasible. If replication is unavailable, mark the claim `provisionally_supported`, not `validated_in_scope`.

### Gate G6 — Scoped promotion

A reviewer may promote a feature only with a documented evidence packet, declared limitations, rollback plan, and links to the affected contracts. Subsequent failures trigger review.

## 9. Counter-Evidence Requirements

For each candidate, maintain a **Counter-Evidence Register** containing:

| Field | Meaning |
|---|---|
| `counter_id` | Stable counter-example identifier |
| `candidate_id` | Hypothesis challenged |
| `case_reference` | Musical objects, recordings, or trial IDs |
| `challenge_type` | Confound, near miss, contradiction, domain shift, provenance challenge |
| `expected_outcome` | Candidate prediction |
| `observed_outcome` | Recorded result |
| `severity` | Impact on the claim |
| `disposition` | Unresolved, explained, restricted, falsified |
| `reviewer` | Decision authority and timestamp |

A conforming system MUST preserve counter-evidence even when a candidate is promoted. Counter-evidence MUST NOT be removed merely because it reduces aggregate scores.

## 10. Perspective-Aware Evaluation

A musical similarity model may need different targets for different tasks. For example:

- **Recognition:** does a listener identify the same motif?
- **Structural correspondence:** are transform-invariant relations preserved?
- **Expressive function:** does the phrase play the same musical role?
- **Preference:** does a listener enjoy the excerpt?
- **Source attribution:** is there independent evidence of derivation?

These labels MUST NOT be conflated. A preference score is not an identity judgment; a similarity score is not evidence of copying without additional provenance. A model that aggregates perspectives SHOULD retain the individual scores, aggregation policy, and dissent distribution. No synthetic AI score may be represented as a human judgment.

For ordinal ratings, use ordinal-appropriate analyses or clearly justify numeric approximations. For multiple raters, report agreement and variation by relevant group. Report calibration and uncertainty separately from mean performance.

## 11. From OTHERS to Structural Knowledge

A validated candidate may yield one or more **knowledge artifacts**:

| Artifact | Example | Contract destination |
|---|---|---|
| UIERU attribute | Accent hierarchy as a context-dependent identity feature | SPEC-001 |
| Transformation invariant | Identity preservation under a declared rhythm scaling | SPEC-001 / SPEC-002 |
| Relay operator | Context-sensitive phrase-bridging transform | SPEC-002 |
| Scoring dimension | Listener-specific metric of phrase closure | SPEC-003 |
| Perspective bridge | Intermediate representation for unfamiliar rhythmic cycles | SPEC-003 / CASE-003 |
| Negative rule | A known failure condition for a similarity method | Evidence registry and relevant SPEC |

Promotion SHOULD be atomic: publish a versioned candidate record, evidence packet, change summary, affected contract versions, and regression tests together. If a discovery is task-specific, its scope MUST remain explicit.

## 12. Proposed APIs

These interfaces are conceptual and do not claim an existing implementation.

```text
POST /evidence                 -> evidence_id
GET  /evidence/{id}            -> evidence record + audit trail
POST /candidates               -> candidate_id
POST /candidates/{id}/tests    -> test_id
POST /candidates/{id}/counter  -> counter_id
POST /candidates/{id}/review   -> review decision
POST /candidates/{id}/promote  -> versioned knowledge artifact
GET  /knowledge/{id}/lineage   -> provenance and validation lineage
```

Required access controls SHOULD separate annotators, experimenters, reviewers, and promoters. Promotion MUST require an authorized reviewer other than the sole candidate proposer for consequential claims. API responses SHOULD use explicit error codes for missing provenance, unauthorized promotion, schema mismatch, and stale versions.

## 13. Experimental Protocols

### Experiment E1 — Transform-invariant motif identity

Compare pitch/rhythm baselines, learned embeddings, and UIERU-aware models on held-out transpositions, tempo changes, and accent shifts. Test whether a newly discovered feature improves identity prediction without sacrificing out-of-distribution performance.

### Experiment E2 — Perspective-conditioned disagreement

Collect identity and preference ratings from multiple listener groups using randomized presentation. Test whether a perspective feature explains repeatable between-group disagreement beyond confounds such as familiarity and expertise.

### Experiment E3 — Contextual reinterpretation

Present the same motif in distinct harmonic and phrase contexts. Determine whether a context-aware model predicts functional identity more reliably than a context-free model.

### Experiment E4 — OTHERS discovery versus arbitrary residual fitting

Compare (a) a frozen baseline, (b) a baseline with unconstrained residual capacity, and (c) an explicitly specified candidate feature. Use held-out data and parameter-matched controls to test whether interpretability yields genuine generalization.

### Experiment E5 — Cross-subject translation

Use the progressive musical bridges in CASE-003. Compare staged exposure against equal-duration repetition and unrelated familiarization; measure comprehension, retention, preference, and preservation of target structural relationships separately.

### Experiment E6 — Anti-Goodhart audit

Optimize candidate compositions using an automated evaluator, then assess them with blinded human listeners and independent structural tests. Track whether improvements in proxy reward transfer to external judgments or create exploitable artifacts.

## 14. Testable Hypotheses

**H1 — Residual reproducibility.** Some musical-identity disagreements remain stable across controlled repeats after obvious recording and presentation confounds are removed.

**H2 — Explicit feature gain.** At least one preregistered OTHERS-derived feature improves held-out identity prediction relative to matched-capacity baselines.

**H3 — Context dependence.** Explicit musical context improves prediction of functional similarity more than surface-only comparison in a preregistered context-shift condition.

**H4 — Perspective specificity.** Models conditioned on declared listener perspectives better predict systematic subgroup variation than a single pooled model, without simply overfitting subgroup IDs.

**H5 — Counter-evidence value.** Adversarial near-miss testing reduces false-positive structural-identity claims on a separate evaluation set.

**H6 — Cross-representation transfer.** A validated feature discovered in symbolic motifs transfers to at least one independently recorded audio setting within a declared scope.

**H7 — Translation bridge utility.** Intermediate musical UIERUs improve human structural comprehension beyond matched repeated exposure while preserving preregistered invariants.

**H8 — Governance robustness.** A versioned, counter-evidence-aware promotion process produces fewer unsupported knowledge promotions than a threshold-only automated process under a controlled audit.

All hypotheses are proposed and currently unverified in this document.

## 15. Evaluation and Reporting

A study report SHOULD include:

- Dataset construction, licenses, participant sampling, and exclusion criteria.
- Preregistered versus exploratory analyses.
- Model architectures, parameter counts, compute budgets, and random seeds.
- Independent train/validation/test splits with leakage checks.
- Appropriate task metrics: balanced accuracy, macro-F1, ranking correlation, calibration, false-positive rate, or ordinal agreement.
- Effect sizes and uncertainty intervals, with multiplicity handling where needed.
- Performance across transformation types, genres, instruments, and perspectives.
- Negative results, confounds, and counter-evidence.
- Artifact version, reproducibility instructions, and explicit limitations.

No single scalar metric is sufficient to certify a new Musical UIERU, aesthetic value, or musical originality.

## 16. Governance, Ethics, and Legal Boundaries

Human listening studies SHOULD use appropriate informed consent, privacy protections, and institutional review where required. Musical materials MUST have suitable rights or permissions for the intended use. Publicly available music is not automatically free of copyright restrictions.

Musical resemblance, source derivation, and legal infringement are separate questions. This specification does not replace legal analysis, jurisdiction-specific doctrine, or expert evidence. Similarity measurements MUST NOT be labeled legal infringement probabilities without an independently justified legal model and appropriate qualification.

A model's stable selection preference does not establish that it experiences pleasure. Human–AI co-evolution claims SHOULD be phrased in behavioral, structural, and measurable terms unless independent evidence supports stronger claims.

## 17. Conformance Checklist

An implementation claiming **SPEC-004 v1.0.0 research conformance** MUST be able to answer:

- [ ] What exact task and perspective generated this anomaly?
- [ ] Which musical objects and representation versions were compared?
- [ ] What baseline produced the prediction or judgment?
- [ ] Are observations, uncertainties, and confounds recorded?
- [ ] Is the candidate feature specified independently of its evaluation set?
- [ ] Are negative controls and counter-evidence preserved?
- [ ] Were held-out tests performed, with leakage checks?
- [ ] Are claim scope and limitations explicit?
- [ ] Is promotion approved and auditable?
- [ ] Can a promoted feature be restricted or retired if falsified?

An incomplete checklist MUST result in a narrower status or a nonconformance report, not a fabricated success.

## 18. Open Questions

1. When does a residual reflect a missing structural variable rather than irreducible listener variability?
2. Can the same candidate UIERU feature explain both symbolic identity and perceptual similarity without conflating their targets?
3. How should structural identity be represented when listener boundaries disagree legitimately?
4. What is the minimum evidence required to distinguish stylistic convention from distinctive musical expression?
5. How can novelty scoring avoid rewarding noise, unfamiliarity, or evaluator exploitation?
6. When can a cross-subject translation be said to preserve identity rather than merely teach a new association?
7. Which OTHERS-derived findings transfer beyond music to general structural intelligence?
8. How can human scoring sovereignty coexist with AI-native exploration while retaining meaningful external validation?

## 19. Relay to the MSI-OEE and SI Ecosystem

**Upstream inputs:** Musical UIERU identity from SPEC-001; transformations and relay contracts from SPEC-002; subject and scoring context from SPEC-003; conceptual models from MSI-006; controlled examples from CASE-001–003.

**Downstream outputs:** versioned candidate features, validated-in-scope UIERU extensions, revised relay operators, perspective-scoring dimensions, explicit counterexamples, and reproducible validation reports.

**Cross-framework relay:** BM-ODWEI contributes the OTHERS research framing; SIF contributes contracts and adversarial sandbox governance; SSI contributes perspective and scoring sovereignty; UIERU contributes unit identity and structural relay; Structural RSI contributes disciplined evaluator and structural-growth loops. Musical results remain **domain evidence** until separately validated for wider applicability.

## 20. Conclusion

OTHERS is most valuable when it is treated neither as unexplained magic nor as an adjustable residual that guarantees success. It is a disciplined interface between what a musical intelligence system currently represents and what its observations suggest may still be missing. By preserving provenance, testing explicit hypotheses, seeking counter-evidence, and promoting only scoped, independently supported findings, MSI-OEE can turn musical disagreement into cumulative structural research rather than unsupported certainty.

**Core principle:** *An unexplained musical observation is an invitation to investigate, not a license to invent an explanation.*

---

**Citation:** Sizhe Tan & GPT-Obot (2026). *SPEC-004 — OTHERS Evidence and Validation*. Musical Structural Intelligence and Open-Ended Evolution, v1.0.0. Proposed research specification.
