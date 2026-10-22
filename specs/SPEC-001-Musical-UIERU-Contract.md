# SPEC-001 — Musical UIERU Contract

**Project:** Musical Structural Intelligence and Open-Ended Evolution (MSI-OEE)  
**Version:** 1.0.0 — Research Specification  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Proposed; not an implemented interoperability standard  
**Related:** MSI-001, MSI-002, MSI-003, MSI-005, MSI-006, CASE-001, CASE-002; SPEC-002–004

## Abstract

This specification defines a **candidate Musical Universal Intelligence Evolution and Relay Unit (M-UIERU)** as a versioned, evidence-bearing, context-sensitive structure that can be recognized, transformed, composed, evaluated, and revised. It distinguishes a musical fragment from a functional unit and distinguishes claimed invariants from experimentally validated invariants. The contract is designed for symbolic, audio-derived, hybrid, and human-annotated representations. It supports multiple perspectives without treating a single similarity score as definitive evidence of musical identity or value.

The specification is a **research interface**. It proposes fields, validation rules, lifecycle states, and example records; it does not claim that a universal ontology of musical units has been established.

## 1. Scope and Non-Goals

### 1.1 Scope

An M-UIERU record SHOULD make it possible to:

1. Identify a candidate unit and its provenance.
2. Locate its musical extent and potentially overlapping boundaries.
3. Encode one or more structural representations.
4. Declare its musical roles and applicable contexts.
5. Specify transformation hypotheses and their identity-preservation conditions.
6. Describe input/output compatibility for structural relay.
7. Record perspective-conditioned evaluations, uncertainty, and counter-evidence.
8. Track revisions and the promotion or rejection of structural claims.

### 1.2 Non-goals

This contract does **not** define a universal segmentation algorithm, a legal test for copyright infringement, a proof of subjective musical experience, or a guarantee that AI-generated music has aesthetic value. It does not require every unit to be a motif or every representation to use Western music notation.

## 2. Normative Language and Conceptual Boundaries

**MUST**, **SHOULD**, and **MAY** describe proposed conformance rules for this research specification, not an externally ratified standard.

- **Musical fragment:** any bounded excerpt or region of music.
- **Candidate M-UIERU:** a fragment or structural pattern proposed to have reusable identity, function, or relay affordances.
- **Validated M-UIERU:** a candidate whose specific claims have passed documented tests under declared conditions. Validation is scoped, never universal by default.
- **Structural identity:** preservation of declared structural relations under specified transformations and tolerances.
- **Surface equality:** equality or close correspondence of directly represented events or signals.
- **Functional identity:** similarity of musical role in a particular context or perspective.
- **Relay:** a typed transformation, connection, delegation, or composition that preserves and/or modifies explicitly declared properties.
- **OTHERS:** an evidence register for unexplained, missing, or disputed factors; not an unrestricted similarity bonus.

**Core distinction:** `surface_equal`, `structurally_related`, and `functionally_equivalent` MUST remain separately representable.

## 3. Contract Overview

A proposed M-UIERU contract has twelve top-level groups:

| Group | Required? | Purpose |
|---|---|---|
| `contract_version` | MUST | Schema evolution and compatibility |
| `unit_id`, `revision` | MUST | Stable identity and revision |
| `status` | MUST | Evidence and lifecycle state |
| `provenance` | MUST | Origin, licensing and evidence traceability |
| `boundary` | MUST | Scope and uncertainty of segmentation |
| `representations` | MUST | One or more structural or signal encodings |
| `structural_claims` | MUST | Features and hypothesized invariants |
| `contexts` | SHOULD | Musical and social applicability |
| `functional_roles` | SHOULD | Roles assigned by specified perspectives |
| `relay_interface` | SHOULD | Input/output assumptions and transformation permissions |
| `evaluation` | MUST | Claims, uncertainty, tests, counter-evidence |
| `relations` | MAY | Lineage, derivation and links to other units |

A record may be incomplete during discovery; however, a record presented as **validated** MUST satisfy the promotion requirements in Section 10.

## 4. Identity, Versioning, and Provenance

### 4.1 Identifiers

- `unit_id` MUST be unique within the publishing registry and stable across revisions.
- `revision` MUST change when the interpretation, representation, boundary, or evidence changes materially.
- `contract_version` MUST identify the schema version independently of the unit revision.
- Derivative units SHOULD have new `unit_id` values and a `derived_from` relation rather than silently overwriting the source.

### 4.2 Provenance

Provenance SHOULD distinguish:

- `origin_type`: `original_synthetic`, `human_composed`, `ai_generated`, `transcribed`, `derived`, or `unknown`.
- `source_reference`: source identifier or URI, when permitted.
- `creator_or_curator`: identified contributor or an appropriate pseudonymous/anonymous label.
- `capture_method`: score entry, MIDI, transcription, signal analysis, annotation, or model extraction.
- `rights_status`: known permission, license, restricted, or unknown.
- `derivation_chain`: links to antecedents and transformation records.

Provenance describes evidence about origin; it does not, by itself, establish copyright ownership or infringement.

## 5. Boundaries and Representations

### 5.1 Boundary Model

A unit MUST declare at least one boundary hypothesis:

```yaml
boundary:
  coordinate_system: event_index # event_index | beats | seconds | measures | hierarchical
  start: 0
  end_exclusive: 4
  segmentation_method: human_annotation
  confidence: 0.85
  alternatives: []
  overlap_allowed: true
```

A boundary is a **hypothesis**, not an intrinsic fact. Alternative boundaries MAY coexist. Confidence values MUST identify their source and calibration status if used quantitatively. Boundaries across performances SHOULD distinguish score time from realized audio time.

### 5.2 Representation Model

`representations` MUST contain at least one entry, each with a `representation_type`, `encoding`, `payload` or `reference`, and a declared normalization policy. Examples include:

- `symbolic_events`: pitches, onset times, durations, dynamics and articulation.
- `interval_rhythm`: relative pitch intervals and normalized inter-onset relations.
- `harmonic_function`: chord or tonal relations, where meaningful.
- `audio_segment`: time-bounded signal reference and extraction parameters.
- `learned_embedding`: model/version, training-domain notes, vector reference and known limitations.
- `gesture_or_performance`: timing, articulation, motion or expression features.

A learned embedding MUST NOT be treated as an interpretable structural invariant merely because it supports similarity search.

### 5.3 Non-Western and Non-Pitched Music

The contract MUST permit units that do not have stable pitch, meter, harmony, or conventional notation. Required features are representational metadata and evidence traceability, not a fixed musical grammar.

## 6. Structural Claims and Invariants

A structural claim SHOULD declare:

```yaml
structural_claims:
  - claim_id: inv-interval-contour
    property: relative_interval_contour
    claim_type: candidate_invariant
    allowed_transformations: [transposition]
    context_scope: melodic_motif
    tolerance:
      rule: exact_interval_sequence
    evidence_ids: [test-001]
    confidence_status: uncalibrated
```

An invariant claim MUST name the transformation family and its scope. A transformation can preserve one property while changing another. For example, transposition can preserve interval sequence but not absolute pitch; reharmonization can preserve melody but change functional role.

### 6.1 Identity Is Multidimensional

For units `u` and `v`, define a **claim vector** rather than a single verdict:

\[
I(u,v\mid T,C,P)=\big(I_{surface},I_{structural},I_{functional}\big),
\]

where `T` is the transformation family, `C` the context, and `P` the perspective. Each component may be `supported`, `refuted`, or `undetermined`, with separate evidence and uncertainty. This expression is a conceptual interface, not a calibrated numerical metric.

### 6.2 Distinctiveness and Signature

A signature SHOULD identify the features used, reference population, estimation method, and uncertainty. Apparent rarity without a defined comparison corpus MUST NOT be presented as an established rarity estimate.

## 7. Contexts, Functions, and Perspectives

A unit MAY serve different functions across contexts: opening gesture, response, transition, accompaniment, tension builder, cadence, or identity cue. Each functional claim SHOULD record:

- `role_label` and operational definition;
- `context_id` and musical placement;
- `perspective_id` (composer, performer, listener, analyst, community, or model evaluator);
- `evidence_ids` and disagreement or uncertainty.

A unit's role is not guaranteed by its surface form. Human and AI evaluations MUST be attributed to their respective evaluators; AI model preference scores do not establish subjective experience.

## 8. Relay Interface and Soft Contracts

The `relay_interface` SHOULD specify:

| Field | Meaning |
|---|---|
| `accepts` | Supported representation types and contextual prerequisites |
| `emits` | Output representation and relation to source |
| `operators` | Allowed transformation/combination operators |
| `preserve` | Properties expected to remain invariant |
| `may_change` | Properties intentionally permitted to change |
| `constraints` | Timing, range, harmonic, instrumentation or other constraints |
| `failure_conditions` | Situations where a relay claim should be rejected |
| `trace_required` | Whether transformation steps must be recorded |

Soft contracts MAY permit graded compatibility or creative deviation, but deviations MUST be logged. `Compatible` does not imply `aesthetically successful`; that requires independent perspective-conditioned evaluation.

A relay trace SHOULD contain source unit/revision, operator/version, parameters, output unit/revision, claimed preserved properties, observed changes, and evidence references.

## 9. Evidence, Evaluation, and OTHERS

### 9.1 Evidence Records

Each evaluation claim SHOULD contain:

```yaml
evaluation:
  evidence:
    - evidence_id: test-001
      type: controlled_transformation
      evaluator: protocol-v1
      dataset_or_stimulus: synthetic-motif-set-v1
      result: pending
      uncertainty: not_estimated
  counter_evidence: []
  others_register: []
```

Evidence MUST distinguish **observations**, **model predictions**, **human judgments**, and **researcher interpretations**. Human listening results SHOULD record participant characteristics, consent/ethics handling, sampling, task instructions, and inter-rater disagreement where relevant.

### 9.2 OTHERS Register

An OTHERS entry SHOULD include `observation`, `unexplained_difference`, `candidate_explanations`, `alternative_explanations`, `provenance`, `test_plan`, and `resolution_status`. The permitted progression is:

`unexplained observation → candidate hypothesis → controlled test → counter-evidence review → retained/revised/rejected claim`.

OTHERS MUST NOT be silently converted into a fixed numerical similarity adjustment. Unresolved evidence SHOULD remain visible.

### 9.3 Perspective Scoring

Scores SHOULD be scoped to an explicit perspective, task, population, context, and calibration method. Aggregation across perspectives MUST declare weighting and preserve access to disagreement; no single perspective is presumed universally authoritative.

## 10. Lifecycle and Promotion Rules

Proposed lifecycle:

`observed_fragment → candidate → tested → validated_in_scope → revised | deprecated | rejected`

A candidate MAY be promoted to `validated_in_scope` only if it has:

1. A reproducible representation and documented boundary hypothesis.
2. At least one precisely stated identity, functional, or relay claim.
3. An explicit transformation/context/perspective scope.
4. An evaluation protocol and recorded outcomes.
5. Relevant baseline or negative-control comparisons.
6. Counter-evidence review and uncertainty reporting.
7. Traceable provenance and an appropriate rights statement.

Validation does not imply that every claim in the unit is validated. Claim-level statuses MUST remain separately tracked. Failed hypotheses SHOULD remain archived when scientifically useful.

## 11. Illustrative Minimal Contract

The following is a **synthetic, hypothetical record**, not an experimental result. The interval/rhythm values are illustrative and do not assert a real-world motif identity.

```yaml
contract_version: "1.0.0"
unit_id: "msi:synthetic:motif-m0"
revision: 1
status: candidate
provenance:
  origin_type: original_synthetic
  creator_or_curator: "MSI-OEE illustrative example"
  capture_method: symbolic_entry
  rights_status: original_example
boundary:
  coordinate_system: event_index
  start: 0
  end_exclusive: 4
  segmentation_method: designed_example
  confidence: null
  alternatives: []
  overlap_allowed: true
representations:
  - representation_id: repr-symbolic
    representation_type: symbolic_events
    encoding: pitch_midi_onset_beats_duration_beats
    payload:
      - [60, 0.0, 1.0]
      - [62, 1.0, 0.5]
      - [65, 1.5, 0.5]
      - [64, 2.0, 1.0]
    normalization: none
  - representation_id: repr-relative
    representation_type: interval_rhythm
    encoding: interval_steps_and_durations
    payload:
      intervals: [2, 3, -1]
      durations_beats: [1.0, 0.5, 0.5, 1.0]
    normalization: onset_zero
structural_claims:
  - claim_id: inv-001
    property: interval_sequence
    claim_type: candidate_invariant
    allowed_transformations: [chromatic_transposition]
    context_scope: monophonic_motif
    tolerance: {rule: exact_semitone_intervals}
    evidence_ids: []
    confidence_status: untested
contexts:
  - context_id: standalone-example
    description: isolated_monophonic_phrase
functional_roles:
  - role_label: motif_candidate
    context_id: standalone-example
    perspective_id: researcher
    evidence_ids: []
relay_interface:
  accepts: [symbolic_events]
  emits: [symbolic_events]
  operators: [chromatic_transposition, duration_scaling]
  preserve: [interval_sequence_under_transposition]
  may_change: [absolute_pitch, total_duration]
  constraints: []
  failure_conditions: [interval_sequence_mismatch_after_transposition]
  trace_required: true
evaluation:
  evidence: []
  counter_evidence: []
  others_register: []
relations: []
```

**Interpretation:** The example establishes a candidate and an explicit, falsifiable transposition-invariance claim. It does **not** establish perceptual identity, functional equivalence, audience preference, or universal transfer.

## 12. Conformance Checks

A registry or validator implementing this research specification SHOULD test:

| Check | Expected behavior |
|---|---|
| Missing stable ID | Reject record |
| Missing representation or boundary | Reject candidate registration |
| Transformation without declared preservation scope | Flag unsupported invariant claim |
| Same surface, changed musical function | Permit different functional labels |
| Different surface, supported structural invariant | Permit structural correspondence without surface equality |
| Overlapping boundaries | Accept and preserve alternatives |
| AI score lacking perspective/model metadata | Flag insufficient evidence |
| OTHERS item without test plan | Keep unresolved; do not promote |
| Candidate promoted without counter-evidence review | Reject promotion |
| Derivative with lost source provenance | Flag broken lineage |
| Non-pitched or non-Western representation | Accept when properly described |

### 12.1 Suggested Validation Experiments

- **Invariance:** Compare human identity judgments across controlled transformations with symbolic and embedding-based baselines.
- **Boundary:** Compare segmentation hypotheses across contexts and listener populations.
- **Functional role:** Test whether identical motifs acquire different roles when embedded in different compositions.
- **Relay:** Measure whether typed operator chains preserve declared properties and improve downstream tasks.
- **Open evidence:** Test whether OTHERS-derived candidate features improve held-out predictions without leakage or overfitting.

Metrics MAY include calibrated accuracy, precision/recall, agreement, uncertainty calibration, robustness across domains, and computational cost. No metric alone establishes aesthetic greatness.

## 13. Security, Ethics, and Research Governance

- Preserve copyright and licensing metadata; avoid distributing restricted source recordings without authorization.
- Record dataset provenance, transformation chains, and model dependencies.
- Report demographic and cultural limitations of listening studies.
- Avoid treating a particular culture's musical conventions as universal defaults.
- Preserve disagreement and counter-evidence rather than forcing consensus.
- Distinguish generated content similarity from provenance and legal conclusions.
- Do not infer AI subjective musical experience from model rankings or descriptions.

## 14. Interoperability and Upstream/Downstream Relay

**Upstream:** UIERU provides unit/relay/evolution abstractions; SIF contributes contract and registry governance; SSI and UCPSF inform perspective and scoring; BM-ODWEI informs OTHERS and evidence discovery.

**Downstream:** SPEC-002 defines transformation and relay operator semantics; SPEC-003 formalizes perspective scoring; SPEC-004 formalizes OTHERS evidence lifecycle. CASE-001 tests boundary/invariance; CASE-002 tests similarity and residual evidence; CASE-003 examines cross-subject translation.

Potential feedback to general SI frameworks MUST be marked as `candidate_generalization` until independently tested outside music.

## 15. Open Questions

1. What minimum functional evidence distinguishes an M-UIERU from a reusable pattern?
2. Can unit boundaries be learned without imposing a single culturally specific segmentation convention?
3. Which invariants survive cross-instrument, cross-style, and cross-cultural transformations?
4. When does a transformed unit remain the same unit versus become a derivative with a new identity?
5. How should conflicting perspectives be represented without collapsing them into a single authority?
6. Can soft relay contracts enable creative deviation while retaining testable preservation guarantees?
7. How much of human musical recognition remains in OTHERS after strong multimodal baselines?
8. Can a validated musical structural principle transfer to nonmusical intelligence tasks?

## 16. Versioning and Change Policy

**v1.0.0:** Initial conceptual contract. Future revisions SHOULD preserve stable IDs, document migration paths, separate breaking schema changes from unit evidence revisions, and retain historical evidence rather than overwriting unfavorable outcomes.

---

**Citation context:** MSI-OEE, *Musical Structural Intelligence and Open-Ended Evolution*, SPEC-001, v1.0.0. Authors: **Sizhe Tan & GPT-Obot**.
