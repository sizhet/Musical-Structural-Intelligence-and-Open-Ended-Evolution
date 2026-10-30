# SPEC-002 — Transformation and Relay Operators

**Project:** Musical Structural Intelligence and Open-Ended Evolution (MSI-OEE)  
**Version:** 1.0.0  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Proposed research specification; not an implemented interoperability standard  
**Companion specifications:** `SPEC-001-Musical-UIERU-Contract.md`, `SPEC-003-Perspective-Scoring-Schema.md`, `SPEC-004-OTHERS-Evidence-and-Validation.md`

## Abstract

This specification defines a research-oriented vocabulary and contract for transforming, composing, and relaying Musical Universal Intelligence Evolution and Relay Units (Musical UIERUs). A transformation changes a unit or its realization; a relay establishes a traceable relationship among units, contexts, agents, or representations. Both may preserve some identities while altering others. The proposed contract separates *structural validity*, *identity claims*, *musical function*, *perspective-dependent value*, and *evidence*. It supports exact and soft constraints, controlled creative deviations, reproducible evaluation, and the promotion of experimentally validated operators into a reusable registry. It does not presume that all musical quality can be formalized or that machine-generated preference constitutes subjective experience.

## 1. Scope and Normative Language

This document specifies:

1. An operator model with explicit inputs, outputs, preconditions, effects, and provenance.
2. A taxonomy of transformations and relay/composition operators.
3. A three-level identity assessment: surface, structural, and functional.
4. Hard constraints, soft constraints, and controlled deviations.
5. Operator chaining, graph composition, and failure handling.
6. Validation procedures, counter-evidence, and lifecycle governance.

The words **MUST**, **SHOULD**, and **MAY** describe proposed conformance requirements for implementations of this research specification. They are not claims of empirical validation. The term **UIERU** follows the MSI-OEE conceptual framework; operational definitions remain hypotheses to be tested.

### 1.1 Out of scope

This document does not prescribe a single musical ontology, notation system, sound synthesis engine, copyright infringement test, or universal aesthetic score. It does not equate recognizable similarity with source copying or legal infringement. It does not infer AI consciousness from a system's musical preferences.

## 2. Foundational Objects

### 2.1 Musical UIERU

A Musical UIERU is a candidate reusable musical structure with a declared representation, context, boundary, functional hypotheses, supported transformations, relay interfaces, and evidence status. A recurring fragment alone is insufficient to establish validated UIERU status; see SPEC-001.

### 2.2 Operator

An **operator** is a versioned, typed mapping with declared effects:

$$
O:(U_1,\ldots,U_n;C,P,\theta)\longrightarrow(Y,\Delta,E)
$$

where:

- $U_i$: source Musical UIERUs or representations;
- $C$: musical and production context;
- $P$: perspective or evaluator reference, when relevant;
- $\theta$: parameters, including random seed where applicable;
- $Y$: resulting UIERU, realization, or composition graph;
- $\Delta$: declared structural changes and preserved properties;
- $E$: evidence, diagnostics, and provenance.

An operator MAY be deterministic or stochastic. Stochastic operators MUST log enough parameters, seeds, model versions, and inputs to permit an appropriate level of reproducibility.

### 2.3 Transformation versus relay

A **transformation** modifies one or more representations or realizations: for example, transposition, rhythmic augmentation, ornamentation, or reharmonization.

A **relay** transfers, connects, or recontextualizes structural information: for example, placing a motif in a phrase, passing a score to a performer, or translating a complex rhythmic structure into an accessible learning sequence.

An operation MAY be both a transformation and a relay. These are functional categories, not mutually exclusive implementation classes.

### 2.4 Identity and value are separate

An operation MUST NOT declare that structural identity, musical function, and aesthetic value are interchangeable.

- **Surface identity:** exact or tolerance-bounded equality in a specified representation.
- **Structural identity:** preservation of designated relationships under declared transformations and contexts.
- **Functional identity:** preservation of a specified musical role, such as cadence, tension, or thematic recall.
- **Aesthetic value:** perspective- and context-conditioned evaluation, not an intrinsic identity flag.

A transformed motif can retain structural identity while changing its expressive function; conversely, distinct structures can fulfill similar musical functions.

## 3. Canonical Operator Contract

Every registered operator MUST specify the following fields:

| Field | Meaning | Requirement |
|---|---|---|
| `operator_id`, `version` | Stable identifier and semantic revision | MUST |
| `kind` | `transformation`, `relay`, or `hybrid` | MUST |
| `family` | Taxonomic operator family | MUST |
| `input_types`, `output_types` | Accepted/produced representations | MUST |
| `preconditions` | Conditions for valid application | MUST |
| `parameters` | Typed parameters, units, ranges, defaults | MUST |
| `hard_constraints` | Conditions whose violation invalidates execution | MUST |
| `soft_constraints` | Desired but negotiable properties | SHOULD |
| `declared_invariants` | Candidate properties expected to be preserved | SHOULD |
| `declared_changes` | Properties intentionally altered | MUST |
| `context_scope` | Musical styles, contexts, populations, or tasks | MUST |
| `identity_claims` | Surface/structural/functional hypotheses | SHOULD |
| `evaluator_refs` | Scoring schemas and perspectives | SHOULD |
| `provenance_policy` | Inputs, model version, source and seed tracking | MUST |
| `failure_modes` | Rejection, partial success, ambiguity handling | MUST |
| `evidence_status` | Candidate, tested, validated-in-scope, disputed, retired | MUST |

A registry MUST NOT infer validation merely from the presence of an operator schema.

## 4. Transformation Operator Taxonomy

### 4.1 Pitch and interval operators

- `transpose(interval)`: shift pitches by a specified interval; preserve relative intervals unless constrained by tuning or instrument range.
- `invert(axis)`: reflect melodic intervals about a defined pitch or pitch-class axis.
- `retrograde()`: reverse ordered events; often changes temporal function even when event content is conserved.
- `register_shift(octaves)`: change register without necessarily changing pitch classes.
- `interval_warp(mapping)`: modify interval relationships; structural identity becomes an empirical hypothesis.

### 4.2 Temporal and rhythmic operators

- `augment(factor)`, `diminish(factor)`: scale durations and event positions under declared timing rules.
- `tempo_map(curve)`: change expressive timing while retaining or modifying relative event order.
- `metric_reframe(meter)`: recontextualize a phrase under a different meter.
- `accent_shift(pattern)`: move accents; potentially preserve event sequence but alter perceived grouping.
- `phase_rotate(offset)`: rotate a cyclic pattern, including across-bar phase relationships.
- `swing_or_microtiming(profile)`: apply timing deviations within specified tolerances.

### 4.3 Harmonic and tonal operators

- `reharmonize(chord_plan)`: replace supporting harmony while tracking melodic constraints.
- `modal_shift(mode)`: alter pitch collection and tonal implications.
- `functional_substitution(mapping)`: replace harmonies while attempting to preserve a functional role.

### 4.4 Texture, timbre, and orchestration operators

- `reorchestrate(instrument_map)`: redistribute parts across instruments.
- `timbre_transfer(target_profile)`: change sound characteristics while tracking source-model uncertainty.
- `voice_redistribute(mapping)`: change polyphonic allocation and register.
- `density_change(profile)`: add or remove events while declaring the retained backbone.

### 4.5 Generative and structural operators

- `ornament(style_profile)`: insert passing, neighbor, or decorative material.
- `fragment(selection)`: extract a subset; identity claims MUST identify the selected boundary.
- `expand(development_plan)`: elaborate a motif into a phrase or section.
- `compress(abstraction_rule)`: retain selected relationships while omitting detail.
- `hybridize(source_units, policy)`: produce a new candidate structure from multiple sources, with attribution and provenance retained.
- `creative_deviation(constraints, proposal_policy)`: explore departures from a baseline, with explicit risk and evaluation records.

No operator in this taxonomy automatically guarantees that the result is musically effective, original, or legally permissible.

## 5. Relay and Composition Operator Taxonomy

### 5.1 Sequential relay

`sequence(U_a,U_b,transition)` establishes temporal succession and a declared transition. Checks MAY include phrase closure, continuity, tonal movement, or deliberate discontinuity.

### 5.2 Parallel relay

`layer(U_a,U_b,alignment)` establishes simultaneous structures. Preconditions MAY constrain register, rhythmic collisions, tuning, or instrumentation. Contradictions can be intentional if registered as soft deviations.

### 5.3 Transformative relay

`relay_transform(U,O,target_context)` applies an operator as a unit moves into a new context, while recording source-to-result lineage.

### 5.4 Hierarchical relay

`embed(parent,children,boundaries)` creates a phrase/section/work hierarchy. It MUST record boundary and role assignments rather than assuming that musical hierarchy is unique.

### 5.5 Contextual relay

`reinterpret(U,context_from,context_to)` keeps some event material while changing surrounding harmony, meter, narrative position, or performance setting. It MUST treat identity and function as separate questions.

### 5.6 Recursive relay

`develop(seed,policy,stop_rule)` applies an evolving transformation/composition policy. It MUST define stopping or resource limits, log operator chains, and avoid treating repeated output generation as validated structural growth.

### 5.7 Cross-subject relay

`translate_perspective(U,source_perspective,target_perspective,bridge_plan)` attempts to make a structure accessible across subjects or populations. It SHOULD record preserved invariants, altered presentation, comprehension measures, and the target audience's right to reject the proposed translation.

### 5.8 Performance and representation relay

`realize(score,performer_or_model)` and `transcribe(audio,representation)` bridge symbolic and acoustic forms. Because these mappings can be many-to-many and lossy, outputs MUST include uncertainty and provenance when available.

## 6. Hard Constraints, Soft Contracts, and Creative Deviations

A **hard constraint** determines whether an operation is admissible for a specified task: e.g., a requested instrument's playable range or a required fixed duration.

A **soft contract** encodes preferences, trade-offs, or context-dependent expectations: e.g., thematic recognizability, smooth voice leading, or a preferred tension profile.

A **creative deviation** intentionally relaxes a soft constraint in pursuit of possible expressive or structural value. It is not simply a failure relabeled as creativity.

For a candidate output $Y$, one illustrative selection rule is:

$$
Y^* \in \arg\max_{Y\in\mathcal{F}_{hard}}
\bigl[ S_P(Y,C)-\lambda R(Y,C)+\eta N(Y,C)\bigr]
$$

where $\mathcal{F}_{hard}$ is the hard-feasible set, $S_P$ is perspective-conditioned quality, $R$ is a declared risk or soft-constraint penalty, and $N$ is a novelty estimate. This is a *design example*, not a universal model of musical value. Weights and objectives are context-dependent and may themselves be challenged through counter-evidence.

A deviation record SHOULD include: baseline, altered constraint, intended expressive hypothesis, observed listener effects, evaluator disagreements, and evidence status.

## 7. Identity Preservation Contract

For each transformation, specify a candidate invariant set $I=\{i_1,\ldots,i_k\}$ and an evaluation scope $C$. Define a property-specific check:

$$
operatorname{Preserve}(i_j,U,O(U),C)\in
\{\text{pass},\text{fail},\text{undetermined}\}.
$$

Examples of candidate invariants:

- Relative pitch contour or interval pattern.
- Onset-ratio pattern or metrical grouping.
- Accent hierarchy and phrase segmentation.
- Harmonic functional trajectory.
- Motivic recurrence relationships.
- Characteristic timbral gesture.

Preservation of one invariant MUST NOT be presented as proof of full structural identity. Identity assessment SHOULD combine declared structural tests with independent perceptual studies and report disagreement.

### 7.1 Example: transposition

Original symbolic motif: pitches `[60, 62, 65, 64]`, durations `[1, 1, 2, 1]` (beat units).

Operation: `transpose(+5 semitones)`.

Output pitches: `[65, 67, 70, 69]`; durations unchanged.

The interval sequence `[+2, +3, -1]` is preserved. Exact pitch equality is not. Whether listeners recognize the motif in a given setting is an empirical question, not guaranteed by the interval check.

### 7.2 Example: accent shift

Original onsets and pitches may remain identical while accents shift from events 1 and 3 to events 2 and 4. Event equality can coexist with changed grouping and expressive function. An operator MUST record these differences rather than emit a single undifferentiated `identity=true` flag.

## 8. Operator Graphs and Composition Semantics

A musical composition MAY be modeled as a typed, attributed directed multigraph:

$$
G=(V,E,\tau,\alpha)
$$

where nodes represent units, events, sections, or performance agents; edges represent temporal, simultaneous, transformational, contextual, or cross-subject relations; $\tau$ assigns types and $\alpha$ stores attributes and evidence references.

The graph is a *research representation*, not a claim that all musical meaning is graph-reducible.

### 8.1 Chaining rules

An operator chain `O3(O2(O1(U)))` MUST:

1. Type-check each interface.
2. Validate hard preconditions at each stage.
3. Retain a source-to-result lineage graph.
4. Propagate uncertainty and evidence references.
5. Reassess identity after composition; local preservation does not imply global preservation.
6. Detect incompatible assumptions about tempo, tuning, meter, or perspective.

### 8.2 Failure semantics

Supported execution statuses:

- `succeeded`: output produced and hard checks passed.
- `partial`: output produced but a declared noncritical objective failed.
- `rejected`: hard precondition or constraint violated.
- `undetermined`: insufficient evidence for an identity/function claim.
- `error`: implementation or data failure.

A failed identity test does not necessarily invalidate an otherwise valid transformation; it invalidates the corresponding identity claim.

## 9. Proposed YAML Contract Example

The following is illustrative, not a finalized machine-validated schema:

```yaml
operator_id: msi.transform.transpose
version: 1.0.0
kind: transformation
family: pitch_interval
status: candidate
input_types: [symbolic_motif]
output_types: [symbolic_motif]
parameters:
  semitones:
    type: integer
    required: true
    example: 5
preconditions:
  - input_has_pitch_events
hard_constraints:
  - output_pitch_within_declared_range
soft_constraints:
  - maintain_recognizable_motivic_identity
declared_invariants:
  - relative_pitch_intervals
  - onset_and_duration_pattern
declared_changes:
  - absolute_pitch_values
context_scope:
  tuning: 12_tet
  representation: midi_pitch_and_beat_duration
identity_claims:
  surface: expected_false
  structural: hypothesis_preserved
  functional: not_assumed
evaluator_refs:
  - perspective_scoring_motif_recognition_v1
provenance_policy:
  record_input_hash: true
  record_operator_version: true
  record_parameters: true
  record_evaluator_version: true
failure_modes:
  - out_of_range
  - unsupported_tuning
  - missing_pitch_data
```

### 9.1 Example execution record

```yaml
execution_id: example-transpose-001
operator_ref: msi.transform.transpose@1.0.0
input_ref: motif-M0@1.0.0
parameters: {semitones: 5}
output_ref: motif-M0-T5@1.0.0
status: succeeded
observed_changes:
  absolute_pitch_values: changed
invariant_checks:
  relative_pitch_intervals: pass
  onset_and_duration_pattern: pass
identity_assessment:
  surface: false
  structural: undetermined
  functional: undetermined
evidence_refs: []
notes: "Symbolic invariants checked; no listener study performed."
```

## 10. Evaluation and Validation Protocol

### 10.1 Core questions

- Do registered operators preserve their declared invariants across varied contexts?
- Does an explicit relay graph improve long-range coherence over matched baselines?
- Do soft-contract deviations improve human-rated expressiveness under blinded evaluation?
- Can operator chains support meaningful novel structures without merely reproducing training examples?
- Do cross-subject bridge sequences improve structural comprehension, not only familiarity?

### 10.2 Suggested experimental comparisons

Compare at least:

1. Raw note/event transformations without UIERU metadata.
2. Embedding- or sequence-model transformations with comparable resources.
3. UIERU operators without perspective-aware scoring.
4. UIERU operators with perspective-aware scoring and counter-evidence review.

Control for training data, computational budget, model size, musical genre, stimulus length, and evaluator exposure where feasible.

### 10.3 Suggested measures

- Symbolic invariant pass/fail rates and false-preservation claims.
- Human motif-recognition accuracy and inter-rater variability.
- Phrase and long-range structural coherence judgments.
- Musical quality, expressiveness, and originality ratings kept separate.
- Novelty relative to documented corpora, with retrieval-based memorization checks.
- Relay success across representations and perspectives.
- Failure and abstention calibration; evidence trace completeness.

### 10.4 Counter-evidence

A registered operator SHOULD collect cases where its declared invariants fail, human listeners disagree with structural labels, or its outputs systematically reduce musical quality. Such cases MUST remain accessible to evaluator governance and MUST NOT be silently filtered from performance reports.

## 11. Lifecycle and Governance

Suggested lifecycle:

`proposed → implemented → tested → validated-in-scope → revised / disputed / retired`

Promotion to `validated-in-scope` requires a stated task, test distribution, baselines, evaluator provenance, and reproducible evidence. An operator can be validated for symbolic interval preservation without being validated for perceptual recognizability or aesthetic quality.

Operator versioning SHOULD distinguish:

- **Patch:** implementation correction without intended semantic change.
- **Minor:** new backward-compatible parameters or contexts.
- **Major:** altered identity semantics, constraint meaning, or incompatible interface changes.

Human and AI evaluators retain separate perspective identifiers. No single scoring forest has automatic authority to override all others. Conflicts SHOULD be reported as evidence rather than averaged away by default.

## 12. Testable Hypotheses

**H1 — Explicit invariants:** Typed transformation contracts reduce false claims of preserved structural identity compared with untyped transformation pipelines.

**H2 — Relay graph:** Explicit temporal and hierarchical relay edges improve human-rated long-range thematic coherence against resource-matched generation baselines.

**H3 — Soft contracts:** Controlled soft-constraint relaxation yields higher expressiveness ratings than either rigid constraint enforcement or unconstrained random deviation in at least some contexts.

**H4 — Context dependence:** Identity and functional judgments vary systematically with harmony, meter, performance, and listener perspective, even for identical event sequences.

**H5 — Traceability:** Provenance-aware operator chains make error diagnosis and counter-evidence discovery more reliable than opaque chains.

**H6 — Cross-subject translation:** Intermediate structural bridges can improve recognition of unfamiliar patterns relative to unstructured repeated exposure, with preservation trade-offs explicitly measured.

Each hypothesis is falsifiable. Negative results should constrain or revise the operator taxonomy, not be relabeled as success.

## 13. Interoperability and Relay to the Wider SI Framework

- **SPEC-001:** Supplies UIERU identity, boundaries, and lifecycle fields consumed by operators.
- **SPEC-003:** Supplies perspective-conditioned scoring and disagreement representations.
- **SPEC-004:** Supplies OTHERS evidence provenance, counter-evidence, and promotion gates.
- **MSI-002:** Motivates structural identity and invariance hypotheses.
- **MSI-003:** Motivates relay graph composition and soft musical contracts.
- **MSI-004:** Motivates controlled creative deviation and evolving valuation.
- **MSI-007:** Motivates recursive operator discovery and evaluator governance.
- **MSI-008 / CASE-003:** Motivate cross-subject translation and intermediate UIERU bridges.

A musical operator may suggest a general SI mechanism, but transfer to other domains requires separate operationalization and cross-domain validation.

## 14. Limitations and Open Questions

1. Musical segmentation and identity are not universally agreed upon.
2. Representation choices may obscure performance gestures, timbre, or cultural meaning.
3. Formal constraints can encode the biases of a particular musical tradition.
4. Perceptual studies may disagree across training, culture, and familiarity.
5. Novelty metrics can reward noise, and preference metrics can reward conformity.
6. Long-term cultural significance cannot be established by a short benchmark.
7. Cross-subject translation may change the very feature it attempts to preserve.
8. Copyright and attribution obligations require separate legal and provenance analysis.

## 15. Recommended Implementation Sequence

**Stage 1 — Symbolic primitives:** implement transposition, rhythmic scaling, accent shift, and sequential relay with invariant logging.

**Stage 2 — Composition graphs:** add hierarchy, layering, contextual reinterpretation, and explicit soft constraints.

**Stage 3 — Human evaluation:** conduct blinded motif-recognition and expressiveness studies with registered perspectives.

**Stage 4 — Open evidence:** capture model–human disagreement and submit candidate operators or invariant revisions to SPEC-004 validation.

**Stage 5 — Cross-subject relay:** test intermediate UIERU translation paths for unfamiliar rhythmic or structural systems.

## Conclusion

Transformation and relay are not interchangeable with unrestricted generation. A useful structural music system must be able to state **what changed, what was intended to remain, under which context, according to whose perspective, and with what evidence**. This specification offers a provisional contract for making those statements testable. Its ultimate value depends on experimental results, including failures and counter-evidence, and on whether validated musical discoveries can improve broader structural intelligence systems.

---

**Citation:** Sizhe Tan & GPT-Obot. (2026). *SPEC-002 — Transformation and Relay Operators*. In *Musical Structural Intelligence and Open-Ended Evolution (MSI-OEE)*, v1.0.0. Research specification.
