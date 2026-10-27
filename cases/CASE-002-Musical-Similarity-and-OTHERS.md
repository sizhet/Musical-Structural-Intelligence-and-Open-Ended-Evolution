# CASE-002 — Musical Similarity and OTHERS

**Project:** Musical Structural Intelligence and Open-Ended Evolution (MSI-OEE)  
**Version:** 1.0.0  
**Authors:** Sizhe Tan & GPT-Obot  
**Document type:** Research case / experimental protocol  
**Status:** Conceptual design; no empirical results are claimed

## Abstract

Two musical passages may sound similar while differing in pitch, rhythm, instrumentation, or harmony; conversely, two passages may share surface features yet be perceived as unrelated. This case develops a reproducible, perspective-aware protocol for investigating such disagreements. It combines conventional feature comparisons, transformation-aware Musical UIERU matching, contextual distinctiveness, listener judgments, provenance evidence, and an explicit **OTHERS** register for unexplained evidence. OTHERS is not a free parameter that makes any prediction correct: every proposed explanatory feature must be documented, tested against held-out cases, and subjected to counter-evidence. The case distinguishes perceptual resemblance, structural correspondence, historical copying, and legal infringement. It is designed as a research bridge between MSI-002, MSI-005, MSI-006, BM-ODWEI, and SIF.

**Keywords:** musical similarity; Musical UIERU; structural invariants; perspective-conditioned distance; OTHERS; counter-evidence; provenance; perceptual evaluation; open structural growth.

---

## 1. Research question and scope

**Primary question:** When human listeners judge two musical passages to be similar but an existing computational representation disagrees, can the discrepancy be converted into a falsifiable hypothesis about a missing structural or contextual feature?

Related questions:

1. Which transformations preserve recognizable musical identity?
2. Does contextual distinctiveness change the interpretation of an otherwise identical match?
3. Do listeners with different training or cultural familiarity use different similarity criteria?
4. Can an explicit OTHERS discovery process improve generalization on unseen musical examples?
5. Which forms of evidence speak to perceived similarity, and which are needed for historical-source or legal questions?

**Out of scope:** This case does not provide a plagiarism detector, legal opinion, or a definitive scalar measure of musical originality. All musical examples below are schematic, newly specified for this protocol, and should be rendered as original synthetic MIDI/audio for experiments.

## 2. Conceptual distinctions

Let `A` and `B` be two musical excerpts, `c` a listening context, `p` a listener perspective, and `T` a permitted transformation.

- **Surface similarity:** overlap in observable note sequences, timing, instrumentation, timbre, or audio features.
- **Structural correspondence:** an alignment between higher-level motifs, rhythmic gestures, harmonic functions, or their relations, possibly after transformation.
- **Perceptual similarity:** a listener's judgment under specified instructions and listening conditions.
- **Source relationship:** whether one work historically derived from another; this requires evidence beyond resemblance.
- **Legal infringement:** a jurisdiction- and fact-specific legal determination, not an output of a similarity metric.

A computational dissimilarity `D_p(A,B|c)` need not satisfy metric axioms. In particular, context-sensitive human judgments may be asymmetric and may violate triangle inequality. Accordingly, **perspective-conditioned dissimilarity** is the preferred term unless metric properties are demonstrated.

## 3. Synthetic motif family

Use equal-tempered MIDI note numbers and durations in quarter-note units. All sequences are illustrative, not observations.

### 3.1 Reference motif R

| Event | MIDI pitch | Duration | Onset (beats) | Accent |
|---|---:|---:|---:|---|
| 1 | 60 (C4) | 1.0 | 0.0 | Strong |
| 2 | 62 (D4) | 0.5 | 1.0 | Weak |
| 3 | 65 (F4) | 0.5 | 1.5 | Medium |
| 4 | 64 (E4) | 2.0 | 2.0 | Strong |

Pitch intervals: `[+2, +3, -1]`. Duration proportions: `[1, 0.5, 0.5, 2]`. The melodic contour is `up, up, down`.

### 3.2 Controlled comparisons

| ID | Construction relative to R | Primary contrast | Initial hypothesis (not a result) |
|---|---|---|---|
| A | Exact copy of R | Identity control | High perceived similarity |
| B | Add +5 semitones to every pitch | Transposition | High structural correspondence despite different absolute pitch |
| C | Multiply all durations and onsets by 2 | Uniform augmentation | Preserved interval/rhythm proportions, possible tempo effect |
| D | Render R with a contrasting instrument | Timbre substitution | Structural match; perceptual rating may vary |
| E | Keep pitches and durations; move accents | Accent redistribution | Similar notes, potentially altered phrase identity |
| F | Keep interval contour but replace intervals with `[+1,+5,-2]` | Contour-only resemblance | Intermediate or task-dependent similarity |
| G | Reverse event order | Retrograde | Some shared inventory but different temporal structure |
| H | Keep R; change harmonic backing from stable to tense | Contextual re-harmonization | Structural identity may persist while musical function changes |
| I | Embed R within a repeated, commonplace ostinato | Common-pattern context | Resemblance may be judged less distinctive |
| J | Embed R as a rare, salient entrance following silence | Distinctive-pattern context | Resemblance may carry greater perceptual salience |
| K | Independently generated motif with same pitch histogram | Feature-matched negative control | Histogram match alone should not ensure structural similarity |
| L | New motif with different notes but matched rhythm, accents, and phrase role | Functional correspondence | Functional resemblance without pitch identity |

**Control requirement:** Normalize loudness and rendering quality. Where feasible, separately test symbolic MIDI and audio realizations to distinguish compositional structure from acoustic production.

## 4. Multiple representations and baselines

Each pair must be compared with at least four representations:

1. **Surface baseline:** absolute pitch edit distance, onset/duration edit distance, n-gram overlap, and/or chroma-based similarity.
2. **Transformation-aware baseline:** minimum alignment cost across a prespecified transformation family (e.g., transposition and uniform time scaling).
3. **Learned embedding baseline:** a frozen audio or symbolic music embedding with matched evaluation data and clearly documented training provenance.
4. **UIERU candidate model:** explicit unit boundaries, interval/rhythmic invariants, phrase roles, relational context, and transformation provenance.

Avoid choosing the transformation set after inspecting test outcomes. Pre-register it or select it on training data only.

A candidate structural comparison can be written as:

$$
D_{\mathrm{struct}}(A,B\mid c,p) =
 \min_{T\in\mathcal{T}_{\mathrm{allowed}}(c,p)}
operatorname{Cost}\bigl(operatorname{Align}(T(A),B)\bigr).
$$

This expression defines an experimental family, not a universally valid music distance. The allowed transformations, alignment method, and costs require independent specification and testing.

## 5. Perspective-conditioned evidence forest

Rather than collapsing all evidence prematurely, record a structured vector:

$$
E(A,B\mid c,p)=
(E_{\mathrm{surface}},E_{\mathrm{structure}},E_{\mathrm{function}},
E_{\mathrm{distinctiveness}},E_{\mathrm{perception}},
E_{\mathrm{provenance}},E_{\mathrm{OTHERS}}).
$$

| Evidence channel | Example measurements | Key limitation |
|---|---|---|
| Surface | Pitch/rhythm/chroma matches | Fragile under transformation |
| Structure | Motif alignment, invariants, hierarchical role | Depends on chosen segmentation and grammar |
| Function | Phrase entrance, cadence, tension/release role | Often requires contextual annotation |
| Distinctiveness | Estimated rarity within a specified corpus/style | Strongly depends on reference population |
| Perception | Human pairwise judgments, confidence, explanations | Subjective, variable, and task-dependent |
| Provenance | Dated drafts, stems, documented access, version history | May be missing or ambiguous |
| OTHERS | Unexplained residual with an evidence trail | Not an automatic similarity score |

**Important:** Provenance should not be mixed into a single perceptual distance as though it were an acoustic feature. It belongs to a separate evidence question about possible historical relationships.

## 6. OTHERS as a disciplined open evidence register

A model–listener disagreement is a *trigger for inquiry*, not proof of an undiscovered musical law.

### 6.1 OTHERS categories

- **Structural residual:** an omitted pattern, boundary, interaction, or long-range relationship.
- **Perceptual residual:** an unexplained listener response, including effects of attention or expectation.
- **Contextual residual:** genre, phrase position, harmonic setting, cultural familiarity, or performance context.
- **Provenance residual:** missing or contradictory information about historical transmission; never inferred from audio similarity alone.

### 6.2 Candidate discovery loop

1. **Detect:** Identify stable prediction errors on a held-out diagnostic set.
2. **Describe:** Record the exact pairs, perspectives, uncertainty, and error pattern.
3. **Hypothesize:** Propose a feature or mechanism that could explain the discrepancy.
4. **Intervene:** Construct matched positive and negative examples isolating the proposed feature.
5. **Challenge:** Search for counterexamples, alternate explanations, and dataset leakage.
6. **Validate:** Compare against baselines on an untouched test set, including subgroup performance.
7. **Promote or reject:** Add a feature to an explicit UIERU/Scoring Operator registry only after predefined acceptance criteria are met.

### 6.3 Example candidate: accent-relative identity

Suppose the surface baseline rates R versus E as nearly identical while listeners consistently rate the pair as less similar than R versus B. A candidate explanation is that **accent placement relative to phrase structure** matters more than absolute pitch transposition for this task.

This hypothesis must be tested by factorially varying accents and pitch while controlling loudness, timbre, and tempo. If ratings do not replicate across listeners or recordings, the candidate should not be promoted.

### 6.4 Example candidate: distinctiveness-conditioned salience

Suppose R embedded in a highly common rhythmic figure is treated as less diagnostic than the same notes appearing in a rare, distinctive phrase context. A candidate mechanism is contextual rarity:

$$
I(U\mid C)=-\log P(U\mid C).
$$

This quantity is a model-based estimate of surprisal, **not** an objective measure of artistic originality or legal protectability. Its utility depends on the corpus, representation, smoothing, and cultural context.

## 7. Human listening protocol

### 7.1 Participants and perspectives

Recruit listeners across at least three prespecified strata where feasible: musicians with formal training, active music listeners without formal training, and participants with differing genre/cultural familiarity. Report recruitment criteria and sample-size justification before data collection.

### 7.2 Tasks

- **Pair rating:** “How similar do these two passages sound?” on a 1–7 scale.
- **Triplet choice:** “Which of B or C is more similar to A?”
- **Identity judgment:** “Does the second passage sound like a recognizable transformation of the first?”
- **Functional judgment:** “Do the passages serve a similar musical role?”
- **Explanation:** Optional free-text description of what drove the judgment.

Keep these questions separate: resemblance, identity, and function are not interchangeable.

### 7.3 Design safeguards

- Randomize presentation order and balance pair direction.
- Include attention checks and repeated items to estimate within-listener reliability.
- Standardize playback and record device type where practical.
- Pre-register exclusions, statistical models, and subgroup analyses.
- Obtain appropriate consent; avoid presenting potentially identifiable preference data without protection.
- Distinguish descriptive inter-rater disagreement from measurement noise.

## 8. Evaluation and statistical analysis

Recommended endpoints:

| Endpoint | Measurement | Interpretation |
|---|---|---|
| Pairwise alignment | Spearman rank correlation or ordinal model fit | Agreement with listener judgments |
| Triplet prediction | Held-out triplet accuracy | Relative similarity generalization |
| Calibration | Proper scoring rule / calibration curves | Confidence reliability |
| Invariance | Performance across transformations B–D | Identity robustness |
| Specificity | False positives on K and common-pattern controls | Avoids superficial matches |
| Perspective sensitivity | Performance by listener subgroup | Captures heterogeneity without erasing it |
| Structural growth | Held-out gain after validated OTHERS feature | Evidence of reusable improvement |
| Complexity cost | Runtime, parameters, annotation effort | Practical efficiency and fairness |

Use participant- and stimulus-aware statistical methods (e.g., mixed-effects models or hierarchical models). Report confidence intervals and correction for multiple comparisons where applicable. Compare models with matched data access and compute budgets; publish negative results.

## 9. Testable hypotheses and falsifiers

**H1 — Transformation invariance.** Explicit transformation-aware matching will predict listener identity judgments better than absolute-pitch matching on transposed and uniformly time-scaled examples.  
**Falsifier:** No held-out improvement under matched conditions.

**H2 — Structure beyond contour.** Explicit interval and rhythmic relations will outperform contour-only features on controlled comparisons.  
**Falsifier:** Contour-only models perform equally well or better across preregistered tests.

**H3 — Contextual distinctiveness.** Contextually rare configurations will influence perceived salience beyond raw local overlap.  
**Falsifier:** No replicable effect after controlling familiarity and production cues.

**H4 — Perspective dependence.** Listener background and task framing will systematically alter similarity rankings for some pairs.  
**Falsifier:** No stable subgroup/task effect beyond measurement noise.

**H5 — Functional versus structural identity.** Re-harmonization and phrase relocation can preserve motif recognition while altering functional judgments.  
**Falsifier:** The two judgments are empirically indistinguishable under controlled manipulations.

**H6 — OTHERS utility.** Validated residual-derived features will improve held-out performance over a frozen baseline without a disproportionate false-positive increase.  
**Falsifier:** Improvements disappear under preregistered held-out evaluation.

**H7 — Counter-evidence governance.** An explicit reject/revise stage will reduce spurious feature promotions relative to an unrestricted residual-fitting pipeline.  
**Falsifier:** No measurable reduction under equal review budgets.

**H8 — Nonmetric perception.** Some listener/task settings will exhibit systematic asymmetry or triangle-inequality violations.  
**Falsifier:** No such patterns after controlling noise; retain a metric model if supported.

## 10. Provenance, copying, and legal boundaries

A high musical similarity score does not establish that one creator heard, accessed, or copied another work. Conversely, evidence of access does not by itself establish that protectable expression was copied. The legal standards depend on jurisdiction and case-specific facts; musical experts, recordings, documentary records, and factfinders may play different roles.

A responsible system should expose separate outputs:

1. **Perceptual resemblance estimate** with uncertainty and listener/task scope.
2. **Structural correspondence report** with aligned motifs and transformations.
3. **Distinctiveness estimate** relative to a disclosed reference corpus.
4. **Provenance evidence register** containing verified sources and unknowns.
5. **Explicit limitation:** No automated determination of infringement.

Use synthetic or properly licensed examples for public benchmarks. Document dataset permissions, copyright constraints, and annotation rights.

## 11. Candidate UIERU and evidence records

A minimal record might use the following illustrative schema:

```yaml
case_id: MSI-CASE-002-R-vs-E
reference_unit: R
candidate_unit: E
representation:
  pitch_intervals: [2, 3, -1]
  duration_ratios: [1.0, 0.5, 0.5, 2.0]
transformation_claim:
  type: accent_redistribution
  identity_preservation: unverified
perspective:
  task: motif_identity
  listener_group: preregistered_group_A
observations:
  human_rating_distribution: pending
  model_predictions: pending
others_candidate:
  feature: accent_relative_to_phrase_position
  status: hypothesis_only
counter_evidence:
  negative_controls: [matched_loudness, shuffled_accent]
  held_out_test: pending
provenance:
  source: synthetic_original_stimuli
  external_copying_claim: none
promotion_status: not_validated
```

The schema is intentionally incomplete: it should be refined in `SPEC-001`, `SPEC-003`, and `SPEC-004` before software implementation.

## 12. Phased implementation roadmap

**Phase 0 — Stimulus specification.** Generate MIDI and audio for R and A–L; inspect for accidental artifacts; freeze transformation definitions.

**Phase 1 — Baseline benchmark.** Implement surface, transformation-aware, and embedding comparisons. Publish assumptions and computational budgets.

**Phase 2 — Human study.** Collect similarity, identity, and functional judgments using randomized presentation and preregistered analyses.

**Phase 3 — Disagreement analysis.** Identify reproducible residuals and register OTHERS candidates with supporting and contradictory evidence.

**Phase 4 — Feature validation.** Run isolated interventions and untouched held-out evaluations. Reject unsupported candidates.

**Phase 5 — Structural relay.** Transfer validated candidates into UIERU representations or scoring operators, then test whether gains generalize to a different musical corpus or task.

No phase is claimed to have been completed by this document.

## 13. Failure modes and countermeasures

| Failure mode | Countermeasure |
|---|---|
| Overfitting listener ratings | Preregistered splits and untouched test sets |
| Hidden model training overlap | Training-data provenance and contamination checks |
| Mistaking common conventions for copying | Corpus-conditioned rarity and provenance separation |
| Treating disagreement as proof of missing structure | Replication, interventions, and alternate explanations |
| Collapsing subjective perspectives | Stratified and hierarchical analysis |
| Confusing structural identity with musical function | Separate task instructions and labels |
| Reward hacking via self-scoring | Independent human panels and frozen external benchmarks |
| Unjustified universal claims | Cross-genre and cross-cultural validation |

## 14. Structural relay to the wider SI research program

- **MSI-002:** Tests musical unit boundaries and transformation invariants.
- **MSI-005:** Supplies explicit listener perspectives and scoring disagreements.
- **MSI-006:** Operationalizes OTHERS as evidence discovery rather than unexplained score inflation.
- **MSI-007:** Provides evaluation gates for creative transformation and structural growth.
- **BM-ODWEI:** Tests open evidence, distinctiveness, and perspective-conditioned distance.
- **SIF / UIERU:** Offers a candidate pipeline from observed residual to reusable unit or scoring operator.
- **SSI:** Demonstrates why one universal similarity score may erase legitimate subject differences.

The intended feedback path is:

```text
Musical comparison
    -> reproducible model/human disagreement
    -> OTHERS candidate with provenance
    -> intervention and counter-evidence
    -> independent validation
    -> candidate UIERU / scoring operator
    -> cross-task and cross-domain relay
```

**Promotion rule:** A musical finding remains a domain-specific candidate until independent replication and appropriate transfer tests support broader claims.

## 15. Open questions

1. Is musical identity better represented by a single invariant or a family of task-dependent invariants?
2. How much of perceived resemblance comes from short motifs versus long-range form?
3. When does a listener's familiarity change the unit boundaries they perceive?
4. Can OTHERS discovery be made robust to changing cultural preferences?
5. Which counter-evidence types best prevent false structural discoveries?
6. What should be retained when a nonmetric perceptual model outperforms a conventional metric?
7. Can structural discoveries improve both explanation and generative composition?
8. How should human and AI-native perspectives be compared without presuming subjective equivalence?

## 16. Conclusion

Musical similarity is a productive stress test for structural intelligence because surface resemblance, transformed identity, musical function, subjective perception, historical provenance, and legal questions do not collapse into a single number. The research opportunity is not to disguise this complexity with an unrestricted OTHERS term. It is to turn **specific, reproducible disagreement into controlled experiments**, and to promote only independently validated findings into explicit structural representations.

If successful, this approach would demonstrate a concrete pathway from open evidence to Musical UIERU refinement, perspective-aware scoring, and transferable structural intelligence growth. If unsuccessful, the failures would still help delimit which aspects of musical judgment resist the proposed representations.

---

## Related MSI-OEE documents

- `docs/MSI-002-Musical-UIERUs-Boundaries-and-Invariants.md`
- `docs/MSI-005-Perspective-Scoring-and-Musical-Worldviews.md`
- `docs/MSI-006-Musical-Distance-OTHERS-and-Open-Evidence.md`
- `docs/MSI-007-AI-Musical-Creation-and-Structural-Evolution.md`
- `cases/CASE-001-Motif-Transformation-and-Identity.md`
- `specs/SPEC-001-Musical-UIERU-Contract.md`
- `specs/SPEC-003-Perspective-Scoring-Schema.md`
- `specs/SPEC-004-OTHERS-Evidence-and-Validation.md`

**Citation:** Sizhe Tan & GPT-Obot (2026). *CASE-002 — Musical Similarity and OTHERS*. Musical Structural Intelligence and Open-Ended Evolution, v1.0.0. DOI pending.
