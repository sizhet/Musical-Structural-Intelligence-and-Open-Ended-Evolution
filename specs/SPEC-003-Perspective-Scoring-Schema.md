# SPEC-003 — Perspective Scoring Schema

**Project:** Musical Structural Intelligence and Open-Ended Evolution (MSI-OEE)  
**Version:** 1.0.0 — Research specification  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Proposed, implementation-oriented; not an empirical standard  
**Companion documents:** MSI-004, MSI-005, MSI-006, MSI-007, MSI-008; CASE-002, CASE-003; SPEC-001, SPEC-002, SPEC-004

## Abstract

Musical valuation is not a single objective score. A composition, motif, performance, or transformation may be assessed differently by a composer, performer, listener, cultural community, or AI evaluator, and the same evaluator may change judgments with context, experience, and time. This specification defines a **Perspective Scoring Schema (PSS)** for recording those judgments without erasing their subject boundaries. It separates observed ratings from inferred preferences, scoring models from their owners, confidence from consensus, and musical similarity from artistic merit. It also specifies evidence provenance, disagreement handling, missing dimensions (OTHERS), evaluation governance, and bidirectional human–AI relay. The schema is a proposal for falsifiable research, not a claim that aesthetic value can be completely formalized.

## 1. Purpose and scope

The PSS supports five operations:

1. **Represent** a subject's declared or operational scoring perspective.
2. **Evaluate** a defined musical target under an explicit context and task.
3. **Compare** judgments while retaining differences in scales and meanings.
4. **Relay** explanations and candidate musical structures between perspectives without silently replacing one perspective with another.
5. **Evolve** a scoring model under evidence, versioning, and counter-evidence review.

The PSS does **not** establish whether an AI has subjective experience; equate preference prediction with enjoyment; infer plagiarism from similarity alone; or establish universal rankings of musical greatness.

### 1.1 Normative vocabulary

**MUST**, **SHOULD**, and **MAY** indicate proposed conformance levels for implementations of this research specification. They do not imply an adopted industry standard.

### 1.2 Design principles

- **Subject-boundary first:** scoring ownership and perspective identity remain explicit.
- **Context-conditioned:** no score is meaningful without target, task, and context.
- **Multi-dimensional:** evaluation dimensions need not collapse into one scalar.
- **Provenance-aware:** distinguish human report, measured behavior, model prediction, and researcher inference.
- **Uncertainty-preserving:** represent missingness, variance, disagreement, and calibration separately.
- **Anti-Goodhart:** optimize neither a single proxy nor an evaluator that judges only its own outputs.
- **Open-ended:** preserve unexplained residuals as evidence candidates, not automatic discoveries.
- **Revision-capable:** scoring dimensions, weights, and models can evolve without rewriting history.

## 2. Conceptual model

Let a scoring event be

$$
E = (S, X, C, T, F, O, U, P, V),
$$

where:

- $S$: subject or evaluator identity and authority;
- $X$: musical target, including representation and version;
- $C$: listening, performance, cultural, and experimental context;
- $T$: evaluation task and question;
- $F$: scoring forest, with dimensions and aggregation policy;
- $O$: observations and outputs;
- $U$: uncertainty and disagreement information;
- $P$: provenance and evidence references;
- $V$: schema, model, and rubric versions.

A contextual score can be written:

$$
\mathbf{s}_{S,C,T}(X) = (s_1,\ldots,s_k),
$$

with a **partial** aggregation function, if authorized:

$$
A_{S,C,T}(\mathbf{s}) \rightarrow q.
$$

The scalar $q$ is optional. No global aggregation is assumed. Different subjects may use non-comparable dimensions, or decline aggregation entirely.

A **Scoring Forest** is a collection of potentially interacting scoring trees or operators, not necessarily a fixed weighted sum. Its components can include learned models, explicit rules, human judgments, comparative tests, and evidence filters. Some operators may be non-linear, context-dependent, or non-metric.

## 3. Entities and identifiers

### 3.1 Subject

A `subject` identifies whose perspective is represented. It MUST declare `subject_kind` from `human_individual`, `human_group`, `ai_system`, `hybrid_team`, or `institutional_protocol`. It MUST include `subject_id`, `authority_scope`, and `consent_or_authorization_basis` where relevant. A `human_group` is an aggregation cohort, **not** a unified conscious subject. An `ai_system` subject indicates operational evaluator ownership, **not** subjective consciousness.

### 3.2 Musical target

A `target` MUST have `target_id`, `target_kind` (motif, passage, composition, performance, audio_rendering, transformation, or set), `representation_refs`, and `version_or_hash`. It SHOULD reference Musical UIERU IDs and Relay Graph IDs from SPEC-001/002 when applicable. A comparison MUST state whether targets are the same composition, different performances, or independent works.

### 3.3 Context

A `context` SHOULD record listening device and environment where relevant, exposure count, playback order, cultural or genre framing, task instructions, participant expertise when voluntarily supplied, and presentation constraints. Personal data MUST be minimized. Contextual metadata should not be interpreted as a causal explanation without testing.

### 3.4 Evaluation task

Examples: perceived similarity, motif identity, structural coherence, emotional response, novelty, enjoyment, performance expressivity, accessibility, or source-attribution hypothesis. The task MUST specify its question, response mode, and interpretation boundaries. **Legal infringement is not a permissible direct output of a musical similarity score.**

## 4. Scoring dimensions

A `dimension` MUST specify:

| Field | Requirement | Meaning |
|---|---|---|
| `dimension_id` | MUST | Stable identifier |
| `label` | MUST | Human-readable name |
| `construct_definition` | MUST | What is actually being assessed |
| `measurement_mode` | MUST | Human report, behavior, expert annotation, algorithmic estimate, etc. |
| `scale` | MUST | Range, anchors, direction, missing-value rules |
| `scope` | MUST | Context and population in which claims apply |
| `evidence_refs` | SHOULD | Basis for this dimension |
| `calibration_ref` | SHOULD | Evidence of consistency or calibration |
| `weight_policy` | MAY | Context-specific weighting, if aggregation is allowed |

Illustrative dimensions (not a mandatory universal set):

- **Structural:** motif recognition, coherence, thematic development, transformation consistency.
- **Perceptual:** audibility of relationships, timbral distinction, rhythmic clarity.
- **Expressive:** perceived tension, release, emotional salience, performative nuance.
- **Aesthetic:** enjoyment, perceived beauty, originality, memorability.
- **Social/cultural:** stylistic fit, cultural resonance, collective participation.
- **Epistemic:** uncertainty, confidence in identification, explanation adequacy.
- **Creative growth:** transferability of a novel UIERU, reusability of a Relay operator, independent adoption.

A dimension labeled `emotion` MUST clarify whether it refers to **reported emotion**, **perceived emotion in music**, **physiological correlate**, or **model-predicted label**. These are not interchangeable.

## 5. Forest structure and aggregation

A `scoring_forest` MUST have a stable ID, version, owner/authority, dimension references, operator nodes, and declared aggregation policy. Operator nodes MAY be:

- `feature_estimator`: derives an observation from a musical representation;
- `human_response`: records a rating, ranking, comparison, or description;
- `context_gate`: activates or conditions another operator;
- `comparison_operator`: produces pairwise or triplet judgments;
- `uncertainty_estimator`: models predictive or measurement uncertainty;
- `counter_evidence_gate`: records conflicts, exclusions, or abstention;
- `aggregator`: combines compatible outputs with an explicit policy.

A forest MUST NOT silently merge incompatible scales. When scalar aggregation is requested, the implementation MUST record the transformation, normalization, weighting, missing-value handling, and authorization. Pareto sets or unaggregated score vectors SHOULD be supported as alternatives.

### 5.1 Why a distance may not be a metric

Human judgments of musical similarity can be asymmetric, context-sensitive, and sensitive to ordering. Thus a `dissimilarity_score` MUST NOT be advertised as a mathematical metric unless non-negativity, identity of indiscernibles, symmetry, and triangle inequality are shown for the defined domain. The preferred general term is **perspective-conditioned structural dissimilarity**.

## 6. Observation and uncertainty record

Each `observation` MUST distinguish `observed_value` from `model_estimate`. Required fields include `observation_id`, `dimension_id`, `target_id`, `source_type`, `value_or_response`, `scale_ref`, `timestamp_or_session`, and `provenance_ref`. Unknown values SHOULD be represented as `null` with a `missing_reason`, not as zero.

Uncertainty SHOULD distinguish:

1. **Measurement uncertainty:** noisy or inconsistent measurement.
2. **Model uncertainty:** prediction uncertainty under the stated model.
3. **Perspective heterogeneity:** real variation across subjects.
4. **Construct uncertainty:** ambiguity about what the rubric measures.
5. **Out-of-distribution uncertainty:** insufficient evidence for a new style, context, or population.

Confidence is not consensus. High model confidence cannot substitute for agreement with human participants, and human consensus cannot establish universal value.

## 7. Perspective sovereignty and permissions

Each forest MUST declare `owner_subject_id`, `editable_by`, `aggregatable_with`, and `relay_permissions`. A relay MAY suggest updates, but MUST NOT overwrite the source perspective or rewrite historical judgments. A human participant's rating MUST remain attributable to that participant or an appropriately anonymized record, not relabeled as an AI preference. An AI-predicted preference MUST remain explicitly a prediction.

For cross-subject scoring, use distinct records:

$$
F_H(X\mid C_H), \quad F_A(X\mid C_A), \quad F_{H\leftrightarrow A}(X\mid C_R).
$$

The hybrid forest is a **new negotiated evaluation process**, not proof that the original human and AI perspectives have become identical.

## 8. Disagreement and OTHERS

A `disagreement_record` MUST identify the compared observations, their tasks and scales, the observed discrepancy, and whether comparisons are valid. Differences due solely to incompatible questions or scales are **not** evidence of missing musical structure.

An `OTHERS_candidate` SHOULD include:

- `candidate_id` and `source_disagreement_ids`;
- `unexplained_observation` and alternative explanations;
- `hypothesized_feature` or `unknown`;
- `candidate_class`: structural, perceptual, contextual, provenance, or unclassified;
- `proposed_measurement`, `negative_controls`, and `counter_evidence_refs`;
- `validation_status`: proposed, under_test, supported_in_scope, rejected, or inconclusive;
- `promotion_target`: dimension, UIERU, Relay operator, or none.

**Promotion rule:** An OTHERS candidate MUST NOT become a validated scoring dimension or UIERU solely because it improves in-sample agreement. It requires independent evidence, documented failure conditions, and out-of-sample testing. A failed candidate remains useful counter-evidence.

## 9. Machine-readable example (illustrative YAML)

The following record is a **schema illustration**, not measured study data. All numerical ratings are hypothetical.

```yaml
schema: msi-oee/perspective-scoring/v1.0.0
record_id: pss-example-001
record_status: illustrative_only
subject:
  subject_id: listener-cohort-A
  subject_kind: human_group
  authority_scope: aggregated_study_responses
  consent_or_authorization_basis: hypothetical_example
  owner_note: "Cohort does not imply a unified subjective experience"
target:
  target_id: case-003-ax1-stage-3
  target_kind: audio_rendering
  representation_refs:
    - cases/CASE-003-Human-AI-Musical-Translation.md
  version_or_hash: illustrative-v1
context:
  context_id: listening-protocol-A
  exposure_count: 3
  presentation: randomized_blind
  genre_frame: unspecified
  population_scope: illustrative_only
task:
  task_id: accessibility-after-relay
  question: "How easy is it to follow the recurring rhythmic structure?"
  response_mode: ordinal_rating
scoring_forest:
  forest_id: human-accessibility-forest
  version: 1.0.0
  owner_subject_id: listener-cohort-A
  editable_by: [study_protocol_owner]
  aggregatable_with: []
  relay_permissions: [read_anonymized_aggregate]
  dimensions:
    - dimension_id: rhythmic-accessibility
      label: Rhythmic accessibility
      construct_definition: "Self-reported ease of tracking recurrence"
      measurement_mode: human_report
      scale: {min: 1, max: 7, direction: higher_is_more_accessible}
      scope: illustrative_listening_protocol
      calibration_ref: null
  operator_nodes:
    - {operator_id: response-collector, type: human_response}
  aggregation_policy: report_distribution_only
observations:
  - observation_id: example-response-summary
    dimension_id: rhythmic-accessibility
    target_id: case-003-ax1-stage-3
    source_type: hypothetical_aggregate
    value_or_response: {illustrative_median: 5, sample_size: null}
    scale_ref: rhythmic-accessibility
    timestamp_or_session: illustrative
    provenance_ref: hypothetical-no-participants
uncertainty:
  measurement_uncertainty: not_estimated
  model_uncertainty: not_applicable
  perspective_heterogeneity: not_measured
  construct_uncertainty: requires_pilot_validation
  out_of_distribution_uncertainty: unknown
provenance:
  provenance_id: hypothetical-no-participants
  evidence_type: specification_example
  empirical_claim: false
  source_refs: []
others_candidates: []
versioning:
  schema_version: 1.0.0
  rubric_version: 1.0.0
  model_version: null
```

## 10. Cross-subject musical relay protocol

A translation or co-evolution study SHOULD implement the following sequence:

1. **Register separate perspectives.** Create human and AI scoring records without conflation.
2. **Select a target.** Identify a musical UIERU or composition and its transformation history.
3. **Measure baseline.** Collect independent responses before explanation or adaptation.
4. **Propose a relay.** Create intermediate UIERUs or performances; record preservation contracts from SPEC-002.
5. **Evaluate independently.** Human judgments and AI evaluations are recorded with separate owners and tasks.
6. **Inspect disagreement.** Identify whether differences arise from scale, context, representation, or unknown factors.
7. **Run controls.** Compare with random exposure, simple repetition, and structure-destroying transformations.
8. **Revise cautiously.** Update only the authorized scoring models; preserve historical records.
9. **Retest.** Use held-out music, new listeners, and longitudinal follow-up where feasible.

A successful relay need not maximize immediate liking. It may increase structural recognition or understanding while preserving disagreement in aesthetic preference.

## 11. APIs and validation checks

A minimal implementation MAY expose:

```text
register_subject(subject_record) -> subject_id
register_forest(forest_record) -> forest_id
register_target(target_record) -> target_id
score(target_id, forest_id, context_id, task_id) -> evaluation_record
compare(evaluation_ids, comparison_policy) -> comparison_record
propose_others(disagreement_id, hypothesis) -> candidate_id
validate_candidate(candidate_id, protocol_id, evidence_refs) -> review_record
relay(source_perspective_id, target_perspective_id, transform_graph_id) -> relay_record
```

Implementations MUST reject or flag:

- Scores with missing target, task, perspective, or scale.
- Aggregation of incompatible constructs without an explicit mapping.
- Model predictions mislabeled as human reports.
- Missing evidence provenance or fabricated participant data.
- Unsupported claims that an AI has subjective experience.
- Unauthorized edits to another perspective's forest.
- OTHERS promotions without independent validation.
- Legal conclusions inferred solely from similarity scores.

## 12. Evaluation and falsification program

### 12.1 Experimental studies

**Study A — Perspective separation:** Ask composers, performers, trained listeners, and general listeners to assess the same controlled stimuli. Test whether perspective-conditioned models predict held-out responses better than a pooled model, controlling for sample size and complexity.

**Study B — Context dependence:** Randomize context framing and presentation order. Test whether differences are reproducible rather than noise or demand effects.

**Study C — Calibration:** Compare model confidence with observed accuracy and disagreement. Report reliability diagrams, proper scoring rules when probabilistic, and coverage of abstentions.

**Study D — Anti-Goodhart:** Optimize candidate compositions against one forest; then evaluate using blinded, independent judges and held-out rubrics. Record divergence between proxy improvements and external outcomes.

**Study E — OTHERS growth:** Investigate systematic residuals, preregister candidate features, and test whether they improve out-of-sample explanatory and predictive performance beyond matched-capacity baselines.

**Study F — Human–AI relay:** Test whether intermediate UIERUs improve comprehension of unfamiliar structures compared with exposure-only and simplified-but-structure-destroying controls.

### 12.2 Testable hypotheses

| ID | Hypothesis | Disconfirming evidence |
|---|---|---|
| PSS-H1 | Perspective-conditioned models improve held-out prediction of human judgments | No robust gain over matched pooled baselines |
| PSS-H2 | Context fields explain reproducible variation in evaluation | Effects vanish under randomization or replication |
| PSS-H3 | Preserving distinct scoring dimensions improves interpretability | No measurable benefit against a single-score baseline |
| PSS-H4 | Explicit uncertainty and abstention improve calibration | No calibration gain or worse decision quality |
| PSS-H5 | OTHERS governance yields transferable new features | Improvements disappear on independent test sets |
| PSS-H6 | Bidirectional relay improves structural understanding without requiring preference convergence | No improvement beyond exposure or repetition controls |
| PSS-H7 | Independent scoring limits proxy overoptimization | No reduction in proxy–external evaluation divergence |

### 12.3 Metrics

Use task-appropriate metrics rather than a universal score: rank correlation for preferences, agreement statistics for categorical judgments, calibration error for probabilistic estimates, effect sizes and confidence intervals for interventions, held-out predictive performance, and failure-rate analyses by context. For human studies, preregister primary endpoints where possible and report participant heterogeneity rather than only averages.

## 13. Privacy, ethics, and governance

Music responses may reveal personal or cultural associations. Collect only necessary participant data; document consent, retention, access, and withdrawal procedures. Avoid presenting a narrow cohort as representative of humanity. For culturally situated music, involve relevant communities and acknowledge uncertainty about interpretation. For AI systems, document model provenance, training-data limitations when known, and evaluation feedback loops. Scoring sovereignty is an architectural and governance commitment, not an assertion that all evaluators have equivalent moral or experiential status.

## 14. Compatibility and versioning

- **SPEC-001:** scoring records MAY reference UIERU IDs, identities, boundaries, and invariant claims.
- **SPEC-002:** relay records SHOULD reference transformation operators and preserved/changed properties.
- **SPEC-004:** OTHERS candidates MUST use the evidence and validation lifecycle specified there when available.
- **MSI-005:** provides the conceptual account of musical worldviews and subject-relative valuation.
- **CASE-002:** exercises musical similarity and residual disagreement.
- **CASE-003:** exercises cross-subject translation and learning.

Schema versions follow `MAJOR.MINOR.PATCH`. A change in the meaning of a construct or scale requires a new rubric version even if field names are unchanged. Historical evaluation records remain immutable; corrections should be append-only and traceable.

## 15. Open questions

1. When are perspective differences stable enough to justify separate scoring forests?
2. How can scoring dimensions be compared without erasing their contextual meanings?
3. What constitutes a valid new aesthetic dimension rather than a renamed proxy?
4. How can longitudinal changes in musical preference be separated from experimental habituation?
5. Which aspects of human embodiment can be operationally modeled, and which remain inaccessible?
6. How can a shared human–AI musical space emerge while preserving independent evaluation authority?
7. How should AI-native scoring structures be assessed when their outputs are not directly human-audible?
8. Under what evidence can a musical discovery be relayed back as a general SI principle?

## 16. Conclusion

Perspective Scoring is not a mechanism for declaring one final answer to what music is worth. It is an interface for **recording who evaluates what, in which context, by which construct, with what uncertainty, and under whose authority**. Its research value depends on whether those distinctions improve prediction, explanation, responsible creative search, and cross-subject learning. The schema supports open-ended structural growth while refusing to confuse model preference, human experience, consensus, and validated discovery.

---

**Citation:** Sizhe Tan & GPT-Obot (2026). *SPEC-003 — Perspective Scoring Schema*. Musical Structural Intelligence and Open-Ended Evolution, v1.0.0. DOI to be assigned upon release.
