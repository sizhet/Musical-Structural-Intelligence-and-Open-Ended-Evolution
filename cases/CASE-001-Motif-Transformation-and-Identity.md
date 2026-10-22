# CASE-001 — Motif Transformation and Identity

**Project:** Musical Structural Intelligence and Open-Ended Evolution (MSI-OEE)  
**Subtitle:** From Musical UIERUs and Romantic Intelligence to Perspective Scoring, Structural Relay, and Human–AI Co-Evolution  
**Authors:** Sizhe Tan & GPT-Obot  
**Version:** 1.0.0  
**Document type:** Conceptual case study and reproducible experimental design  
**Status:** Illustrative hypotheses; no listening study or model evaluation has yet been performed  
**Repository path:** `cases/CASE-001-Motif-Transformation-and-Identity.md`

## Abstract

A musical motif may remain recognizable after transposition, temporal expansion, ornamentation, or changes in instrumentation, while an apparently smaller alteration in accent, harmonic support, or phrase placement may change its identity or function. This case investigates **musical identity under transformation** as a test of the proposed Musical Universal Intelligence Evolution and Relay Unit (Musical UIERU). We construct an original, small symbolic motif, define explicit transformations and contrasting controls, distinguish surface equivalence from structural identity and functional continuity, and specify human-listening and computational evaluation protocols. The case also tests whether unit boundaries and identity judgments depend on the listener, task, and surrounding music. Rather than assuming a universal identity-preserving transformation set, it treats invariance as an empirical, perspective-conditioned claim. The intended outcome is a falsifiable experimental scaffold for MSI-002, MSI-003, and SPEC-001—not proof that Musical UIERUs exist.

**Keywords:** Musical UIERU; motif; structural identity; transformation invariance; transposition; rhythm; phrase context; listener judgment; perspective-conditioned scoring; counter-evidence

---

## 1. Case Objective and Scope

This case addresses a deceptively simple question:

> When is a transformed musical passage still the *same musical idea*?

A motif is a useful test object because it is small enough to represent and manipulate but rich enough to carry contour, rhythm, accent, expectation, and context. The case does **not** presume that every motif is a fully fledged intelligence unit. A motif becomes a candidate Musical UIERU only if its representation supports identifiable functions, meaningful transformations, reusable interfaces, and measurable explanatory or generative utility.

We distinguish five possible outcomes of a transformation:

1. **Exact repetition:** the surface events are unchanged.
2. **Recognizable variation:** the passage is judged related despite altered surface details.
3. **Functional reinterpretation:** the passage remains recognizable but serves a different musical role.
4. **Identity disruption:** the transformed passage is no longer consistently recognized as the same motif.
5. **Underdetermined identity:** judgments depend strongly on listener, context, task, or representation.

These outcomes need not be mutually exclusive for all listeners or all tasks.

## 2. A Minimal Original Motif

### 2.1 Symbolic representation

We introduce a synthetic four-note motif, **M0**, in a neutral metrical setting. It is invented for this case, not borrowed from an identified copyrighted work.

| Event | Pitch (MIDI) | Pitch name | Onset (beats) | Duration (beats) | Accent |
|---|---:|---|---:|---:|---|
| e1 | 60 | C4 | 0.0 | 1.0 | strong |
| e2 | 64 | E4 | 1.0 | 0.5 | weak |
| e3 | 62 | D4 | 1.5 | 0.5 | weak |
| e4 | 67 | G4 | 2.0 | 2.0 | strong |

**Pitch sequence:** `[60, 64, 62, 67]`  
**Successive pitch intervals (semitones):** `[+4, -2, +5]`  
**Onset intervals (beats):** `[1.0, 0.5, 0.5]`  
**Duration sequence (beats):** `[1.0, 0.5, 0.5, 2.0]`  
**Contour:** `up, down, up`  
**Illustrative meter:** `4/4`; the final note sustains through beat 4.

The sequence is intentionally modest. Its shortness means that some listeners may perceive it as generic. That is a useful negative control: a candidate unit should not acquire distinctive identity merely because the experimenter assigned it a label.

### 2.2 Candidate unit representation

For this case, define a provisional unit record:

```yaml
unit_id: MSI-CASE-001-M0
representation: symbolic_midi_events
pitch_intervals: [4, -2, 5]
onset_intervals_beats: [1.0, 0.5, 0.5]
durations_beats: [1.0, 0.5, 0.5, 2.0]
accent_profile: [strong, weak, weak, strong]
assumed_context:
  meter: 4/4
  tempo_bpm: 96
  harmony: unspecified
candidate_functions:
  - opening_gesture
  - phrase_seed
invariance_claims: untested
listener_evidence: none
```

The `candidate_functions` are possible experimental placements, **not** established perceptual facts. The unspecified harmony is deliberate: functional identity must be evaluated separately under multiple harmonic contexts.

## 3. Transformation Family

Let a motif be represented by an ordered event sequence `M = (e1, ..., en)`. A transformation `T` maps that sequence to a new realization. We do not assume that `T` preserves identity merely because it has a familiar musical name.

### 3.1 Proposed transformations and controls

| ID | Operation | Operational definition | Expected question |
|---|---|---|---|
| T0 | Exact repeat | No change to M0 | Can listeners recognize the anchor? |
| T1 | Transposition | Add +5 semitones to every pitch | Is relative-interval structure sufficient? |
| T2 | Uniform time expansion | Multiply all onsets and durations by 2 | Does identity survive proportional stretching? |
| T3 | Register shift | Add +12 semitones to every pitch | Is register irrelevant or expressive? |
| T4 | Timbre substitution | Render identical events with another instrument | Does timbre affect recognition or function? |
| T5 | Ornamentation | Add a short neighbor tone before e4 without changing the four anchor events | Can listeners recover the underlying unit? |
| T6 | Reharmonization | Retain the melody but change supporting harmony | Does identity persist while function changes? |
| T7 | Reaccentuation | Shift strong emphasis from e1/e4 to e2/e3 | Can small expressive changes alter grouping? |
| T8 | Phrase relocation | Place the same events as opening, transition, or ending | Does context change function or segmentation? |
| T9 | Interval permutation | Keep note count and rhythm, reorder pitch intervals | Negative control for contour/interval structure |
| T10 | Rhythm shuffle | Keep pitches and total duration, alter onset/duration pattern | Negative control for rhythmic identity |
| T11 | Unrelated control | Independently construct a distinct four-note motif | Baseline false-match rate |

The expected effects are **hypotheses**, not ground truth. T7 or T8 may have a stronger perceptual impact than T1, depending on listener and context. T9 and T10 may remain recognizable to some listeners; they are controls, not guaranteed identity destruction.

### 3.2 Fully specified symbolic examples

**T1 — transposition by +5 semitones:**

```text
M0 pitches:  [60, 64, 62, 67]
T1 pitches:  [65, 69, 67, 72]
Intervals:   [+4, -2, +5]   (preserved)
Onsets:      [0.0, 1.0, 1.5, 2.0]
Durations:   [1.0, 0.5, 0.5, 2.0]
```

**T2 — uniform expansion by factor 2:**

```text
M0 onsets:    [0.0, 1.0, 1.5, 2.0]
T2 onsets:    [0.0, 2.0, 3.0, 4.0]
M0 durations: [1.0, 0.5, 0.5, 2.0]
T2 durations: [2.0, 1.0, 1.0, 4.0]
```

**T9 — interval-order perturbation:**

```text
M0 intervals: [+4, -2, +5]
T9 intervals: [+5, +4, -2]
Start pitch:  60 for both
T9 pitches:  [60, 65, 69, 67]
```

T9 preserves the multiset of interval sizes but changes their order and contour. It is therefore a stronger test than merely changing every pitch independently.

**T10 — rhythmic perturbation:**

```text
M0 pitches:   [60, 64, 62, 67]
M0 onsets:    [0.0, 1.0, 1.5, 2.0]
M0 durations: [1.0, 0.5, 0.5, 2.0]
T10 onsets:   [0.0, 0.5, 1.5, 2.5]
T10 durations:[0.5, 1.0, 1.0, 1.5]
```

Both realizations occupy four beats without overlap; only their rhythmic organization differs. A preregistered implementation should use these exact events or publish any revisions.

### 3.3 Performance transformations versus compositional transformations

It is useful to separate:

- **Surface-preserving rendering:** instrument, dynamics, articulation, and production changes.
- **Parametric musical transformation:** transposition, scaling, displacement, inversion, or augmentation.
- **Structural editing:** note insertion, deletion, reordering, and phrase segmentation.
- **Contextual relocation:** altered harmony, neighboring phrases, meter, or formal role.

A listener may judge identity differently across these categories. Their separation also helps identify whether a system has learned structural invariance or merely acoustic robustness.

## 4. Three Distinct Identity Questions

A central design principle is that **surface equality, structural recognition, and musical function are different variables**.

### 4.1 Surface similarity

A surface representation may compare pitches, onsets, durations, or audio features:

`S_surface(M0, T(M0))`.

This score depends on the representation. Exact-pitch matching will penalize T1, whereas interval-based matching may regard T1 as identical.

### 4.2 Structural identity

Define a perspective- and context-conditioned probability:

`P_same(M0, T(M0) | listener_group, task, context)`.

This is an empirical probability estimated from judgments; it is not a universal constant or a claim about consciousness. Distinct groups may disagree even when the physical sound is identical.

### 4.3 Functional identity

Define a task-specific functional judgment:

`P_same_role(M0, T(M0) | musical_context, task)`.

A transposed motif might preserve recognition while becoming a cadential response rather than an opening gesture. Conversely, two different motifs may play the same structural role without being perceived as the same musical idea.

**Core distinction:**

> Musical Identity ≠ Surface Equality ≠ Functional Identity.

### 4.4 Historical identity is a fourth question

Whether one passage was causally derived from another requires provenance evidence. Perceptual similarity alone does not establish borrowing, copying, authorship, or copyright infringement. Those questions are outside the decision scope of this case.

## 5. Boundary Ambiguity and Nested Units

The four-note M0 may be heard as one unit, two two-note gestures, or part of a larger phrase. To study this, create three controlled contexts:

- **C1 — isolated motif:** M0 presented with silence before and after.
- **C2 — phrase-initial:** M0 followed by a contrasting answering phrase.
- **C3 — embedded:** M0 appears in the middle of a longer phrase with a preceding pickup and a continuation.

Ask listeners to mark unit boundaries and identify whether M0 is a complete gesture, a subgesture, or merely a sequence inside another unit.

A possible representation is a *boundary distribution* rather than a fixed cut:

`P(boundary at beat b | listener, context, task)`.

This accommodates overlapping and nested segmentation. If boundary assignments remain highly unstable and do not improve prediction or composition, the proposed discrete-unit representation may be inadequate for that passage.

## 6. Experimental Protocol

### 6.1 Stimulus generation

Generate symbolic MIDI from M0 and its transformations. Render at a documented tempo and standardized loudness. For identity judgments, use a consistent timbre except in T4. For contextual judgments, use matched arrangement quality and carefully controlled accompanying material.

Publish:

1. Machine-readable event lists and transformation parameters.
2. MIDI files and rendered audio under an appropriate license.
3. Exact instrument presets or synthesis versions.
4. Randomization seeds and stimulus checks.
5. A manifest linking each audio file to its condition without revealing labels to participants.

No such dataset or audio asset is included in v1.0.0; this document specifies the future protocol.

### 6.2 Listener populations

Recruit at least two groups if resources permit: listeners with formal music training and listeners without it. Record relevant musical background, listening familiarity, and self-reported hearing constraints voluntarily and with appropriate privacy protections. Sample-size targets should follow a pilot and power analysis, not an arbitrary claim of adequacy.

### 6.3 Tasks

**Task A — same-idea judgment:** Hear an anchor and a transformed excerpt; answer whether they express the same musical idea, with confidence.

**Task B — similarity ranking:** Given an anchor and two alternatives, choose which is more structurally related, or mark a tie/uncertainty.

**Task C — segmentation:** Mark perceived beginnings and endings of meaningful units in C1–C3.

**Task D — functional role:** Judge whether a motif functions as an opening, continuation, transition, or ending within a presented context. Include an “unclear/other” option.

**Task E — recognition after delay:** Test recognition following a controlled distractor interval to distinguish immediate acoustic matching from more persistent motif representations.

Avoid conflating the tasks: a participant may recognize a motif while judging that its role has changed.

### 6.4 Blinding and randomization

- Randomize presentation order and balance condition frequency.
- Separate repeated exposure to the same anchor to reduce memorization artifacts.
- Include attention and playback-quality checks without using them to exclude disagreement opportunistically.
- Do not reveal the intended “identity-preserving” labels to participants.
- Preregister primary comparisons and exclusion criteria.

## 7. Computational Baselines and Candidate UIERU Model

A meaningful test compares explicit UIERU representations with plausible alternatives, under matched training data and compute where possible.

| Baseline / model | Input | What it tests |
|---|---|---|
| B1: exact event matching | Absolute pitch and timing | Surface equality |
| B2: interval/rhythm descriptors | Relative pitches and durations | Handcrafted invariance |
| B3: sequence alignment | Symbolic note events | Flexible edit-distance similarity |
| B4: learned audio embedding | Rendered waveform | Data-driven perceptual representation |
| B5: learned symbolic embedding | MIDI events | Data-driven structural representation |
| U1: explicit Musical UIERU | Unit features, boundary uncertainty, transforms, context, perspective | Incremental value of structured identity model |

**Fairness requirement:** U1 should not receive privileged identity labels or transformation metadata at test time unless the same information is available to appropriate baselines. Report model complexity, training-set size, compute, and any human annotations.

### 7.1 Candidate scoring model

An illustrative identity estimator is:

`I(Ma, Mb | p, c, t) = g(S_interval, S_rhythm, S_contour, S_accent, S_context, S_timbre, OTHERS; p, c, t)`

where `p` is perspective, `c` is musical context, and `t` is the task. `OTHERS` is a placeholder for unexplained evidence—not a free parameter used to rationalize any result.

If a proposed distance violates symmetry or triangle inequality, call it a **task-conditioned dissimilarity score**, not a mathematical metric.

## 8. Hypotheses and Falsification

### H1 — Relative-structure recognition

For many listeners, T1 transposition will receive higher same-idea judgments than T9 interval permutation, under matched presentation conditions.

**Counter-evidence:** no reliable difference, or stronger performance explained entirely by superficial acoustic cues.

### H2 — Multiple identity dimensions

Identity and functional-role judgments will diverge in at least some T6 and T8 contexts.

**Counter-evidence:** no measurable divergence after controlling for task comprehension and context quality.

### H3 — Boundary dependence

Segmentation distributions will differ across C1, C2, and C3 for at least some listeners.

**Counter-evidence:** stable boundaries across contexts, or changes fully attributable to stimulus artifacts.

### H4 — Explicit-unit utility

U1 will improve held-out identity prediction or explanation quality relative to at least one strong learned baseline, without disproportionate complexity.

**Counter-evidence:** equal or better baseline performance after fair comparison; this would narrow or weaken the UIERU claim.

### H5 — Perspective conditioning

A model that includes independently measured listener/context variables will improve calibration on held-out participants or contexts compared with a perspective-agnostic model.

**Counter-evidence:** no out-of-sample gain, or apparent gain arising from leakage or overfitting.

### H6 — Recoverable structural residuals

Systematic disagreement between human judgments and initial models will reveal candidate features (e.g., accent, phrase position) that improve held-out predictions after independent validation.

**Counter-evidence:** residuals remain noisy, unstable, or unreplicable; they should then remain unresolved rather than be promoted to new structural principles.

## 9. Evaluation and Reporting

### 9.1 Primary metrics

- Same-idea judgment: balanced accuracy, ROC-AUC when appropriate, and probability calibration.
- Pairwise ranking: preference agreement and rank correlation.
- Segmentation: boundary precision/recall with preregistered tolerance and inter-annotator agreement.
- Functional-role judgment: macro-F1, confusion matrix, and uncertainty rate.
- Delayed recognition: accuracy and response-time distributions.

### 9.2 Secondary analyses

- Inter-listener disagreement and within-listener reliability.
- Performance by musical background and context condition.
- Robustness to tempo, timbre, loudness, and render engine.
- Generalization to newly generated motifs with unseen interval/rhythm patterns.
- Ablations of boundary, transformation, context, and perspective features.

Report confidence intervals, uncertainty, and negative results. Do not select only the transformations that favor the proposed framework.

## 10. OTHERS and the Evidence-to-Structure Loop

Suppose listeners consistently judge T7 as less similar than a pitch-only model predicts. A responsible research process is:

1. **Observe:** register the mismatch with the model version and stimulus IDs.
2. **Localize:** inspect candidate explanatory factors, such as accent, metrical grouping, and phrase placement.
3. **Hypothesize:** propose a measurable feature rather than declaring an unexplained intuition to be a discovered law.
4. **Counter-test:** construct matched examples where the candidate feature changes independently of other variables.
5. **Validate:** evaluate on new listeners and held-out motifs.
6. **Promote or reject:** add the feature to the UIERU schema only if it yields reproducible explanatory or predictive value.

This is the **OTHERS → candidate evidence → counter-evidence → validated structure** pathway. Failed candidates remain documented as failed hypotheses, not hidden.

## 11. Structural Relay Implications

If M0 remains identifiable under T1 and T2, a composer or AI system could reuse its identity across different tonal centers or temporal scales. If T6 preserves identity while changing function, the relay interface must distinguish:

- **Identity contract:** which relations support recognizing the motif.
- **Functional contract:** which context-sensitive roles it can plausibly serve.
- **Transformation contract:** which edits are allowed and how their effects are tracked.
- **Evidence contract:** what measurements support each assertion.

A candidate Relay record could be:

```yaml
relay_id: MSI-CASE-001-R1
source_unit: MSI-CASE-001-M0
operator: transpose
parameters:
  semitones: 5
output_unit: MSI-CASE-001-T1
identity_status: hypothesis
functional_status: not_evaluated
evidence:
  human_listening_study: pending
  computational_baselines: pending
```

Such contracts are intended to enable reproducible reuse, not to replace musical interpretation with rigid rules.

## 12. Failure Modes and Limitations

1. **Over-discretization:** some musical phenomena may be continuous, embodied, or resistant to stable segmentation.
2. **Trivial motif:** a four-note example may be insufficiently distinctive for meaningful identity judgments.
3. **Culture dependence:** assumptions about meter, tonality, and motif structure may not transfer across musical traditions.
4. **Representation bias:** symbolic MIDI omits timbral microstructure, gesture, articulation, and social context.
5. **Stimulus confounds:** rendering or loudness differences can drive apparent identity judgments.
6. **Training leakage:** generated transformations of the same source must be grouped across train/test splits.
7. **False universality:** one successful transformation family cannot establish a universal UIERU ontology.
8. **Legal overreach:** similarity judgments cannot establish provenance or infringement.
9. **Evaluator Goodhart:** optimizing a model against one listener task may reduce performance on others.

Negative results are valuable: they may show that a unit needs softer boundaries, a different representation, or that explicit units are not useful for a particular task.

## 13. Minimum Viable Study

A practical initial study can remain small without claiming conclusive validation:

**Stage 1 — stimulus audit:** create M0, T0–T11, and a few independent motif families; check notation, audio rendering, and transformation correctness.

**Stage 2 — pilot listening:** test task clarity, stimulus duration, response variability, and whether participants understand “same idea” differently from “same function.”

**Stage 3 — preregistered comparison:** evaluate selected transformations with adequate sampling based on pilot variability.

**Stage 4 — computational comparison:** train or apply B1–B5 and U1 with leakage-safe splits and matched resources.

**Stage 5 — residual investigation:** select one reproducible human–model disagreement and test a candidate OTHERS feature with new stimuli.

**Stage 6 — relay demonstration:** build a short composition using transformations with recorded identity and functional assumptions; obtain independent musical assessments.

Each stage should publish its own limitations and failure conditions.

## 14. Expected Research Outputs

If implemented, the case should produce:

- A documented, original motif-and-transformation dataset.
- Human judgments with perspective/context metadata and consent safeguards.
- Baseline model predictions and a candidate UIERU model.
- A transformation-by-identity and transformation-by-function comparison.
- An explicit record of failed and supported invariance claims.
- One or more proposed schema revisions to `SPEC-001` and `SPEC-002`, if warranted.

The present v1.0.0 document provides the **design**, not those experimental results.

## 15. Relationship to the MSI-OEE Research Program

- **MSI-001:** Music as a candidate structural intelligence domain.
- **MSI-002:** Candidate UIERUs, boundaries, invariants, and signatures.
- **MSI-003:** Structural Relay and composition under soft contracts.
- **MSI-004:** Expressive deviations that may preserve identity while changing value.
- **MSI-005:** Perspective-conditioned identity and functional scoring.
- **MSI-006:** Similarity, OTHERS, provenance, and counter-evidence.
- **MSI-007:** Structural composition and cumulative AI musical learning.
- **MSI-008:** Cross-subject translation and human–AI musical co-evolution.
- **SPEC-001:** Candidate Musical UIERU contract.
- **SPEC-002:** Transformation and Relay operator specification.
- **SPEC-003:** Perspective Scoring schema.
- **SPEC-004:** OTHERS evidence and validation procedures.

**Suggested figure:** `figures/Fig-002-Musical-UIERU-and-Structural-Invariants.png`, placed after Section 3 or Section 4 once the figure is available.

## 16. Conclusion

Musical identity is not simply a question of whether two passages contain the same notes. Transposition may preserve an interval pattern; reaccentuation may alter perceptual grouping; reharmonization may preserve recognizability while changing musical function; and phrase context may shift where a listener hears the unit's boundaries. These possibilities make motif transformation an unusually precise test of Musical UIERU claims.

The decisive question is empirical: **does a context-aware, transformation-aware unit representation explain and support musical tasks better than plausible alternatives?** If it does, motif identity becomes a reusable foundation for structural relay, composition, and musical knowledge growth. If it does not, the result should refine—or constrain—the proposed UIERU framework.

> A useful musical intelligence unit is not defined by an assertion of identity, but by the transformations, contexts, perspectives, and evidence under which its identity remains operationally meaningful.

---

**MSI-OEE v1.0.0 — CASE-001**  
**Sizhe Tan & GPT-Obot**
