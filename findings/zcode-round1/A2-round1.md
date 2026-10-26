# A2 round 1 — blind theorem-first formalisation of DMP

- Verifier: A2 (independent; did not write DMP; no stake in it being right). Blind: no
  Lean code under `src/gravity/` or `src/im/` was read; nothing under `out/` or `work/`
  outside `work/a2r1/` was read.
- Date of this report: 2026-10-26 22:03:56Z (fresh `date` reading).
- Inputs: only `C:\zcode\CMOS\src\dmp\` — README.md, CHARTER.md, 00-preamble.md,
  01-constitution.md, 02-names-and-hierarchy.md, 04-im.md, 05-milky-way.md,
  06-black-hole.md, 10-code-quality.md, 11-test-design.md, 14-process.md, VERSION
  (0.9.6), SETUP.md, tools/check-setup.sh, tools/scrub-scan.sh.
- Deliverable: `C:\zcode\CMOS\work\a2r1\DMP_A2.lean` (embedded below, byte-exact).
- Claim discipline: every claim below is [argued] (reasoned from the cited file and
  section) unless marked [guess]. Nothing here is [proven]; the Lean file is
  statement-only and was not machine-checked (no Lean toolchain was installed; none
  may be installed under the brief).

## Method (theorem-first, as briefed)

I started from the corpus's headline claimed end-states — the promises a reader of
README/CHARTER and the constitution meets first: a minted instance is contained on its
own and trust never crosses instances; a pressed instance is refused / out of spec and
never claims compliance; no minting without a passed pressing and no minting without a
DMP-complete configuration; what is not fully trusted is ejected and non-compliance is
critical by definition; every derivation chain ends at an axiom (DMP-021); the IM
closure (every accepted message self-verifies through the one ordered rule list; the
canonical encoding is generated and checked by the one grammar); the containment block
(no admission ⇒ contained ⇒ trapped; unpermitted horizon crossing is critical); the
two proof chains (proven only when both agree); the cold-start gate for company-wide
stability. Those are stated first as `def Claim_* : Prop` (a proposition defined,
never asserted — no proof bodies, no placeholder terms of any kind). Then I worked
backwards: each claim forced the definitions and ground axioms it needs to be
statable. Where the text gave no structure the statement needed, I invented the
minimum, marked it `AMB2-nn` (ambiguity register) or `BRIDGE`/`A2-Fnn` (findings), and
kept the most literal reading.

## Counts

| Kind | Count |
|---|---|
| Claim propositions (`def Claim_* : Prop`, statement-only) | 83 (42 end-claims in PART 2, 41 per-theorem claims in PART 3) |
| `axiom` declarations (the words + DMP's asserted ground + claim-support predicates) | 309 |
| — of which DMP's own asserted ground (Axioms 1–4, G0) | 12 |
| — of which the marked BRIDGE axiom (invented, A2-F03) | 1 |
| Supporting `def`s (statement language) | 14 |
| `structure`s | 4 (TrustConfig, Configuration, IMRule, ColdStartRun) |
| `inductive`s | 8 (Verdict, InfoState, TrustEventKind, RefusalReason, Tier, Severity, ClaimId, SClass) |
| Ambiguities registered | 15 (AMB2-01…AMB2-15) |
| Findings | 16 (5 high, 8 medium, 3 low, 0 critical) |

## Inventory (end-theorems first, then per-theorem claims, then ground, then support)

Class codes: **END** = headline end-state claim; **THM** = constitution theorem/rule or
chapter guarantee; **AX-G** = ground DMP itself asserts; **AX-I** = invented support
(the text uses it but never defines it); **DEF** = definition/structure in the
statement language.

### A. End claims (PART 2 of the Lean file)

| # | Lean name | DMP source |
|---|---|---|
| 1 | `Claim_Cinf_eject` | 01 C∞ ("what is not fully trusted is ejected") |
| 2 | `Claim_Cinf_critical` | 01 C∞ ("non-compliance is automatically critical") |
| 3 | `Claim_T_P_no_cross_instance_trust` | 00 "Who maintains it" (minted instance contained); 01 T-P bullet 1 |
| 4 | `Claim_T_P_pressed_not_fully_trusted` | 01 T-P / G0 ("nothing it does is fully trusted by a minted instance") |
| 5 | `Claim_T_P_no_compliance_claim` | 01 T-P (pressed mark; never claims DMP-compliance); 01 T35 |
| 6 | `Claim_no_minting_without_pressing` | 01 T-P ("No minting without a passed pressing") |
| 7 | `Claim_G0_mint_prep` | 01 G0 "Mint prep" |
| 8 | `Claim_unproven_not_complete` | 01 "The words" (DMP-complete, last sentence) |
| 9 | `Claim_minting_rotation` | 01 T-P (trust rotation; owner role ends) |
| 10 | `Claim_chains_end_at_axioms` | 01 intro ("Derived from … the order of the chapter is the order of proof"); DMP-021 |
| 11 | `Claim_grant_chains_end_at_ground` | 00 G0 bullets; 01 T-P (mission slogan "every chain ends at an axiom") |
| 12 | `Claim_trust_tightens_downward` | synthesis of 01 T1, T32 ("nothing is fresher than its grantor"), C18, T-P — see A2-F16 |
| 13 | `Claim_T24_loosening_needs_two` | 01 T24; T26 |
| 14 | `Claim_T24b_lockstep` | 01 T24b (a minted Duality cannot act alone) |
| 15 | `Claim_T24_no_half_removal` | 01 T24 ("one half can never remove the other") |
| 16 | `Claim_T24_restore` | 01 T24 (restore bullet) |
| 17 | `Claim_T27_transitions` | 01 T27 |
| 18 | `Claim_T31_trap` | 01 T31 (the trap) |
| 19 | `Claim_T31_entropy_floor` | 01 T31 (entropy floor; premise-tagged) |
| 20 | `Claim_T36_crossing_critical` | 01 T36 |
| 21 | `Claim_T19_no_leaving` | 01 T19 |
| 22 | `Claim_T37_collapse` | 01 T37 |
| 23 | `Claim_C22_proven` | 01 C22 |
| 24 | `Claim_C22_mismatch` | 01 C22 |
| 25 | `Claim_C2_L1_verified_implies_authorised` | 01 C2.L1; 04 invariant I1 |
| 26 | `Claim_C2_L3_no_replay` | 01 C2.L3; 04 I2 — see A2-F11 |
| 27 | `Claim_C2_L3b_full_refuses` | 01 C2.L3b; 04 rule 16 |
| 28 | `Claim_C2_L2_refusal_inert` | 01 C2.L2 (refusal leaves replay memory as it was) |
| 29 | `Claim_C2_L4` | 01 C2.L4; 04 "Message kinds and permissions" |
| 30 | `Claim_rule16_complete` | 04 "The verify rules", "Why rule 16 is complete" |
| 31 | `Claim_I6_canonical` | 04 "Invariants for proving" I6; "Encoding" |
| 32 | `Claim_I3_log_content_free` | 04 I3; "The refusal log" — vacuous by typing, A2-F10 |
| 33 | `Claim_I4_no_algorithm_choice` | 04 I4; "Encoding" (ECDSA P-256, low s, no negotiation) |
| 34 | `Claim_I5_quiet_answer` | 04 I5; 05 "The quiet answer" |
| 35 | `Claim_verifier_only_in_milky_way` | 05 "The parts" ("verify rules sit only in Milky Way") |
| 36 | `Claim_only_verified_reach_consumers` | 05 "The verifier" |
| 37 | `Claim_C24_cold_start` | 01 C24; 11 "Stable rollout", "The pass line" |
| 38 | `Claim_C18_backcompat` | 01 C18; 04 "Compatibility after the lock" |
| 39 | `Claim_C19_two_signatures` | 01 C19; 04 "Serving at a warehouse" |
| 40 | `Claim_C25_gate` | 01 C25 |
| 41 | `Claim_no_port_before_IIb` | 06 "Supernova classes" ("Where the class gates"); 01 C2 |
| 42 | `Claim_lemma_ledger` | 06 "Lemmas and the lemma ledger" |

### B. Per-theorem claims (PART 3)

| # | Lean name | DMP source |
|---|---|---|
| 43 | `Claim_T0` | 01 T0 |
| 44 | `Claim_T1_intersection` | 01 T1 |
| 45 | `Claim_T2_silence_never_isolates` | 01 T2 |
| 46 | `Claim_Q6_silence_isolation` | 04 v1 "The isolated state" (Q6, owner 2026-10-25) |
| 47 | `Claim_T3_continuity` | 01 T3 |
| 48 | `Claim_T3a_floors` | 01 T3a |
| 49 | `Claim_T3d_safety_first` | 01 T3d |
| 50 | `Claim_T4_config_is_the_dualities` | 01 T4 |
| 51 | `Claim_T5_M1_never_split` | 01 T5 (M1, split-brain half) |
| 52 | `Claim_T5_M1_survives_one_refusal` | 01 T5 (M1, survives-one-refusal half) |
| 53 | `Claim_T5_M1_minimal` | 01 T5 ("the smallest threshold") |
| 54 | `Claim_T6_standins` | 01 T6 |
| 55 | `Claim_T20_time_witness` | 01 T20 |
| 56 | `Claim_T21_counts` | 01 T21 |
| 57 | `Claim_T22_self_application` | 01 T22 |
| 58 | `Claim_T23_horizon` | 01 T23 |
| 59 | `Claim_T24c_self_correction` | 01 T24c |
| 60 | `Claim_T25_thin_surfaces` | 01 T25 |
| 61 | `Claim_T26_retention` | 01 T26 |
| 62 | `Claim_T26_destroy_pair` | 01 Axiom 3 retention clause; 01 T26 |
| 63 | `Claim_T28_enforcement` | 01 T28 |
| 64 | `Claim_T29_shared_cause` | 01 T29 |
| 65 | `Claim_T30_record_not_escape` | 01 T30 |
| 66 | `Claim_T32_potential` | 01 T32 (potential; own acts never raise it) |
| 67 | `Claim_T32_freshness` | 01 T32 (nothing fresher than its grantor) |
| 68 | `Claim_T33_same_recipe_same_field` | 01 T33 |
| 69 | `Claim_T34_three_roads` | 01 T34 |
| 70 | `Claim_T35_compliance_assembled` | 01 T35 |
| 71 | `Claim_T38_info_duality` | 01 T38 |
| 72 | `Claim_C1_one_door` | 01 C1; 02 "The tree" |
| 73 | `Claim_C3_class_carried` | 01 C3 |
| 74 | `Claim_C4_contracts` | 01 C4 |
| 75 | `Claim_C5_freeze` | 01 C5 |
| 76 | `Claim_C6_authority_grant` | 01 C6 (the authority grant) |
| 77 | `Claim_C7_one_repo` | 01 C7 |
| 78 | `Claim_C9_roles_not_values` | 01 C9 |
| 79 | `Claim_C12_privacy` | 01 C12 (privacy singularities) |
| 80 | `Claim_C13_nearest_tier` | 01 C13 |
| 81 | `Claim_C15_write_reads` | 01 C15 |
| 82 | `Claim_C16_data_gate` | 01 C16 |
| 83 | `Claim_C17_two_approvals` | 01 C17 |

### C. Ground (AX-G: DMP asserts these; `axiom` in the file)

| Lean name | DMP source |
|---|---|
| `A1_only_while`, `A1_fail_closed`, `A1_freeze` | 01 "Axiom 1 · The dual gate" |
| `A2_only_on_own_evidence`, `A2_validity_bound` | 01 "Axiom 2 · Evidence" |
| `A3_record`, `A3_counts_and_content` | 01 "Axiom 3 · The record" |
| `A4_restore`, `A4_no_lowering` | 01 "Axiom 4 · The direction" |
| `G0_until_minting`, `G0_pressed_one_person`, `G0_half_loss` | 01 "G0 · The ground" |
| the words: `Part`, `Act`, `Witness`, `Time`, `Evidence`, `Record`, `Trust`, `Happens`, `halves`, `Independent` (def), standing/record/evidence operations | 01 "The words" |

### D. Invented support (AX-I: load-bearing but not defined in the corpus)

Representative (full list is in the file; each is used by at least one claim):
`Info`, `ActOn`, `StateOf`/`InfoState`, `Bridge_admission_gates_info` (BRIDGE),
`Instance`/`MintedInstance`/`PressedInstance`/`WitnessIn`/`InInstance`, `Person`,
`TracesTo`, `MintingEvent`/`When`/`Mints`, `FullReach`, `GatedOnlyBy`, `DependsOn`,
`Loosening`, `SignedBy`, `GrantsAt`, `DeclaredFor`/`Boundary`, `TrustConfig` (structure),
`Configuration`/`Unproven`/`HoldsConfig`, the IM block (`IMMsg`…`VerifyRules`,
`WasVerifiedIn`, `ReplayMemoryOf`, …), `ProofChain`/`SaysProven`/`ChainsAgree`,
`FreshnessOf`/`GrantorOf`/`MembersOf`/`DepthOf`/`MassOf`/`ShortfallOf`,
`ColdStartRun`/`Tier`, `SClass`/`PassedSandbox`, seat/stand-in block,
`OrganisationalHalf`/`FactualHalf`, `Ejected`, `Severity`/`Finding`/`CVSSScore`.

### E. Deliberately not formalised in round 1 (with reason)

- 01 C10 / CHARTER.md: the defensive charter is a scope authorisation, not a
  trust theorem; nothing to state beyond "briefs carry the context line".
- 01 C14, C21 (and 14's twin sections): agent search-and-cite discipline; process
  rules about agent behaviour, restated in 14; no trust-state claim beyond C13/C15
  which are formalised.
- 01 C∞'s stopgap meta-rule (counting stopgap catches, the rethink order): a
  meta-policy about the axiom system itself, not a proposition about trustspace;
  discussed in A2-F01.
- 02 (naming/tree conventions), 10 (code-quality conventions: C8/C11 live here by
  design as "not rules about trust"), 14 (process: cadence, data-gate mechanics,
  SME proposal — draft), 06 GRB/scope-file/R136a1 machinery (authorisation
  procedures; the statable guarantee "no port before IIb" is formalised), 11
  run-record formats (the statable gate, C24, is formalised).
- 00 "The marks"/"The version": repository governance (DMP-007/DMP-018 mechanics).

The Lean file follows.


```lean
/-
  DMP_A2.lean — statement-only formalisation of DMP (the Dark Matter Protocol).
  Blind round 1, verifier A2, THEOREM-FIRST angle.

  Inputs: the markdown under src/dmp/ ONLY (00, 01, 02, 04, 05, 06, 10, 11, 14,
  CHARTER.md, README.md, VERSION, SETUP.md, tools/*).  No existing Lean code for DMP
  was read (Gravity's evidence/ and IM's proof/ untouched, per brief).

  Discipline:
  * Every claimed END RESULT of DMP is stated as `def Claim_* : Prop := ...` — a
    proposition DEFINED, never asserted.  Nothing here claims the claims are true;
    proving one would be `theorem ... := Claim_...`.
  * The ground DMP itself asserts (Axioms 1-4, G0, the undefined "words", and the
    load-bearing predicates the text uses without defining) is declared with `axiom`,
    because the constitution asserts exactly that ground and no more.
  * Invented structure is marked AMB2-nn (see the ambiguity register in
    out/A2-round1.md) or BRIDGE (see findings A2-F02, A2-F03).
  * No proof bodies anywhere; no placeholder term of any kind is used in this file.
    Function definitions (`runRules`,
    `Independent`, ...) belong to the statement language, not to proofs.
  * Whole file: [argued], unchecked.  Lean 4 core only: no imports, no Mathlib.
-/

namespace DMP

/- ============================================================= -/
/- ## PART 0 · The words, and the casts the end theorems force    -/
/- ============================================================= -/

-- The words (01-constitution.md, "The words"): part, act, witness, evidence, time.
axiom Part     : Type   -- anything that can be trusted
axiom Act      : Type   -- anything done in or to CMOS
axiom Witness  : Type   -- a part that decides trust for others
axiom Time     : Type
axiom Evidence : Type
axiom Record   : Type

-- AMB2-01: `Info` is NOT one of "the words", yet the containment block (T19, T27, T31,
-- T36, T37, C12) cannot even be stated without it.  Added as a primitive.
axiom Info : Type

-- Every act sits at a layer and has an actor ("a part acts in CMOS only while ...").
axiom Layer   : Type
axiom LayerOf : Act → Layer
axiom ActorOf : Act → Part

/-- Trust, `T(w, p, a, t)`: the witness trusts the part for that act at that time. -/
axiom Trust : Witness → Part → Act → Time → Prop

/-- An act happens at a time. -/
axiom Happens : Act → Time → Prop

/-- A layer is a place where trust is decided; its two witnesses are its halves; the
pair is the Duality of Trust (DoT).  Reading chosen: exactly two designated halves per
layer (a function, not "at least two").  AMB2-02. -/
axiom halves : Layer → Witness × Witness

-- Failure classes and independence (the words; the list is configuration, T4).
axiom FailureClass : Type
axiom HasClass : Witness → FailureClass → Prop
/-- The failure classes declared for a layer in the minting record (host, key, author,
engine, operating image, person, time source, and whatever else the minting lists). -/
axiom DeclaredClasses : Layer → List FailureClass

/-- Two witnesses are independent when they share no member of the declared classes.
Independence is always relative to that list. -/
def Independent (l : Layer) (w₁ w₂ : Witness) : Prop :=
  ∀ c ∈ DeclaredClasses l, ¬ (HasClass w₁ c ∧ HasClass w₂ c)

-- Time order and durations (needed by Axiom 2's validity bound and the IM freshness
-- window; the words give only "time").
axiom Duration : Type
axiom tLe   : Time → Time → Prop          -- at or before
axiom addT  : Time → Duration → Time

-- Standings ("a standing is trust held across time"; Axiom 2: "a standing is evidence
-- with a validity").
axiom Standing : Type
axiom StandingHolder  : Standing → Part
axiom StandingWitness : Standing → Witness
axiom StandingLayer   : Standing → Layer
axiom ValidStanding   : Standing → Time → Prop

-- Records ("a record is evidence that outlives the act it is about").
axiom WrittenAt      : Record → Time → Prop
axiom RecordOf       : Record → Act
axiom ExistsRecordAt : Record → Time → Prop
axiom recordTime     : Record → Time
axiom ReadableFull   : Witness → Record → Prop   -- every witness of that act, in full
axiom CountsVisible  : Part → Record → Prop      -- other readers: counts always ...
axiom GrantedRead    : Part → Record → Prop      -- ... content only by a grant
axiom ReadsContent   : Part → Record → Prop
axiom Destroys       : Act → Record → Prop

-- Evidence primitives for Axiom 2.
axiom VerifiedBy : Witness → Evidence → Time → Prop
/-- AMB2-06: which evidence bears on which part for which act — glue the text needs
and never gives. -/
axiom BearsOn : Evidence → Part → Act → Prop
/-- Evidence taken at the point of use ("live state of the part"; "point of use"). -/
axiom AtPointOfUse : Evidence → Prop
/-- A loss recorded against a standing. -/
axiom LossRecorded : Standing → Evidence → Time → Prop

-- Verdicts; refusal is the stricter answer ("where the two disagree, the stricter
-- answer stands"; every example Axiom 1 gives is a refusal).
inductive Verdict where
  | allow
  | refuse

/-- The words: a part is *inside* at a time when a standing for it from both witnesses
of its layer is valid then. -/
def InsideAt (p : Part) (t : Time) : Prop :=
  ∃ s₁ s₂ : Standing,
    StandingHolder s₁ = p ∧ StandingHolder s₂ = p ∧
    ValidStanding s₁ t ∧ ValidStanding s₂ t ∧
    ∃ l : Layer, StandingLayer s₁ = l ∧ StandingLayer s₂ = l ∧
      StandingWitness s₁ = (halves l).1 ∧ StandingWitness s₂ = (halves l).2

-- Information, containment, admission (the words "admission", "contains"; T27's
-- transition table made explicit).
inductive InfoState where
  | contained
  | admitted
  | outside
  | destroyed
axiom StateOf : Info → Time → InfoState
/-- AMB2-01b: "act on that information" — invented, needed by T31/T37. -/
axiom ActOn : Act → Info → Prop
/-- An admission is a grant: a record naming an information's class and provenance. -/
axiom Admission : Type
axiom Names : Admission → Info → Prop
/-- BRIDGE (not an axiom of the constitution; A2-F03): acts on information happen only
when an admission names it.  Needed to derive T37/T27/T31 from Axioms 1-2. -/
axiom Bridge_admission_gates_info :
  ∀ (a : Act) (i : Info) (t : Time), Happens a t → ActOn a i →
    ∃ ad : Admission, Names ad i

-- Information-boundary acts (T19/T27).
axiom AdmitsInfo    : Act → Info → Prop   -- contained → admitted (a loosening)
axiom WithdrawsInfo : Act → Info → Prop   -- admitted → contained (a tightening)
axiom ExportsInfo   : Act → Info → Prop   -- contained → outside (an export)
axiom DestroysInfo  : Act → Info → Prop   -- contained → destroyed
axiom LeavesCMOS    : Act → Info → Prop   -- the act "leave CMOS" (T19)
axiom AloneRecreatesCMOS : Info → Prop
axiom InUsableForm  : Act → Info → Prop
axiom CrossesHorizon : Act → Info → Prop
axiom ObservableBy  : Part → Info → Time → Prop

/-- Placeholder byte type (IM frames are byte lists; see PART 2, IM block). -/
axiom Bytes_placeholder : Type
axiom SameLength : Bytes_placeholder → Bytes_placeholder → Prop
axiom ContentOf     : Info → Bytes_placeholder

-- Instances, persons, minting (G0, T-P; "instance" is never typed in the corpus,
-- AMB2-09).
axiom Instance : Type
axiom MintedInstance  : Instance → Prop
axiom PressedInstance : Instance → Prop
axiom InInstance      : Instance → Part → Prop
axiom WitnessIn       : Instance → Witness → Prop
axiom Person   : Type
axiom TracesTo : Witness → Person → Prop
axiom Owner    : Person
axiom WhiteKey : Type
axiom MintingEvent : Type
axiom When  : MintingEvent → Time
axiom Mints : MintingEvent → Instance → Prop

-- Seats (T3a, T5; "seat" is never typed — AMB2-11).
axiom Seat : Type

-- Proof chains (C22).
axiom ProofChain : Type
axiom proofIntent   : ProofChain
axiom proofEvidence : ProofChain

-- Configuration (T4: "the trust configuration belongs to the Duality").
axiom TrustConfigField : Type   -- placeholder: "the parameters of the field of T32"

structure TrustConfig where
  declaredClasses      : Layer → List FailureClass
  lossWindow           : Duration
  seatsPerSideFloor    : Nat
  standinsPerSeatFloor : Nat
  nodesPerHalfFloor    : Nat
  timeAuthorityCount   : Nat
  timeTolerance        : Duration
  fieldParams          : TrustConfigField

/- ============================================================= -/
/- ## PART 1 · The ground DMP asserts (bounds, direction, G0)     -/
/- ============================================================= -/

/- ### Axiom 1 · The dual gate (01, "Axiom 1") -/

/-- Load-bearing modifiers Axiom 1 uses and never defines: AMB2-03. -/
axiom FullReach   : Witness → Act → Prop
axiom GatedOnlyBy : Witness → Witness → Prop
/-- AMB2-05: "nothing that depends on the disagreement moves" — `DependsOn` is
invented for the freeze clause. -/
axiom DependsOn : Act → Layer → Prop

/-- The gate's canonical answer: allow exactly when both halves trust the actor for
the act ("exactly one answer", "no other way through").  Canonical-halves reading,
AMB2-04; under this reading "the stricter answer stands" is definitional (refuse =
not both). -/
def GateAllows (a : Act) (t : Time) : Prop :=
  Trust (halves (LayerOf a)).1 (ActorOf a) a t ∧
  Trust (halves (LayerOf a)).2 (ActorOf a) a t

def GateAllowsFor (p : Part) (a : Act) (t : Time) : Prop :=
  Trust (halves (LayerOf a)).1 p a t ∧ Trust (halves (LayerOf a)).2 p a t

/-- Axiom 1, "only while" half: acting requires the two independent, full-reach,
mutually-gated witnesses to trust. -/
axiom A1_only_while :
  ∀ (a : Act) (t : Time),
    Happens a t →
    Independent (LayerOf a) (halves (LayerOf a)).1 (halves (LayerOf a)).2 ∧
    FullReach (halves (LayerOf a)).1 a ∧ FullReach (halves (LayerOf a)).2 a ∧
    GatedOnlyBy (halves (LayerOf a)).1 (halves (LayerOf a)).2 ∧
    GatedOnlyBy (halves (LayerOf a)).2 (halves (LayerOf a)).1 ∧
    GateAllows a t

/-- Axiom 1, fail-closed half: "what they do not both trust does not act".  This is
also the whole statable content of "no other way through: no debug switch, no allow
list, no trusted network" — the implementation-closure reading is stronger and not
statable without a module system (A2-F01 note). -/
axiom A1_fail_closed :
  ∀ (a : Act) (t : Time), ¬ GateAllows a t → ¬ Happens a t

/-- Axiom 1, freeze: exactly one half trusting moves nothing that depends on the
layer, until they agree. -/
def ExactlyOneTrusts (l : Layer) (p : Part) (a : Act) (t : Time) : Prop :=
  (Trust (halves l).1 p a t ∧ ¬ Trust (halves l).2 p a t) ∨
  (¬ Trust (halves l).1 p a t ∧ Trust (halves l).2 p a t)

axiom A1_freeze :
  ∀ (l : Layer) (b : Act) (t : Time),
    ExactlyOneTrusts l (ActorOf b) b t → DependsOn b l → ¬ Happens b t

/- ### Axiom 2 · Evidence (01, "Axiom 2") -/

/-- A witness trusts only on evidence it verified itself, current, at the point of
use.  The standing-aware clause ("including every loss recorded against the standing")
is carried by `LossRecorded` below. -/
axiom A2_only_on_own_evidence :
  ∀ (w : Witness) (p : Part) (a : Act) (t : Time),
    Trust w p a t →
    ∃ e : Evidence, VerifiedBy w e t ∧ BearsOn e p a ∧ AtPointOfUse e

def lossWindowOf (c : TrustConfig) : Duration := c.lossWindow

/-- "no validity is longer than the time the minting accepts between a loss and its
effect at the point of use" (the window is configuration, T4). -/
axiom A2_validity_bound :
  ∀ (s : Standing) (e : Evidence) (l t : Time) (c : TrustConfig),
    LossRecorded s e l → tLe (addT l (lossWindowOf c)) t → ¬ ValidStanding s t

/- ### Axiom 3 · The record (01, "Axiom 3") -/

/-- Grants, uses and losses of trust are the record-bound acts. -/
inductive TrustEventKind where
  | grant | use | loss
axiom KindOfEvent : Act → Option TrustEventKind

axiom A3_record :
  ∀ (a : Act) (t : Time),
    Happens a t → KindOfEvent a ≠ none →
    ∃ r : Record, RecordOf r = a ∧ WrittenAt r t ∧
      (∀ w : Witness, (w = (halves (LayerOf a)).1 ∨ w = (halves (LayerOf a)).2) →
         ReadableFull w r) ∧
      (∀ t' : Time, tLe t t' → ExistsRecordAt r t')

/-- "Any other reader sees the counts always and the content only by a grant." -/
axiom A3_counts_and_content :
  ∀ (p : Part) (r : Record),
    CountsVisible p r ∧ (ReadsContent p r → GrantedRead p r)

/-- Retention ("never destroyed by fewer than both witnesses of its layer"): under the
canonical reading this is A1 applied to the destruction act; stated as a claim in
PART 3 (Claim_T26_destroy_pair). -/

/- ### Axiom 4 · The direction (01, "Axiom 4") -/

/-- "the trust the Duality declared for that boundary" — AMB2-07. -/
axiom Boundary       : Type
axiom DeclaredFor    : Boundary → Part → Act → Prop
axiom PartInBoundary : Boundary → Part → Prop
axiom LostWithoutEvidenceAgainst : Standing → Prop
axiom RestoredBy : Standing → Evidence → Prop

/-- Restoration duty: what was lost without evidence against it is restored by
evidence.  ("What it cannot restore, it reports" and the building clause stay prose —
A2-F14.) -/
axiom A4_restore :
  ∀ (s : Standing) (t : Time),
    LostWithoutEvidenceAgainst s →
    ∃ e : Evidence, VerifiedBy (StandingWitness s) e t ∧ RestoredBy s e

/-- "No part lowers the bar of evidence, widens a grant or moves the boundary to get
there."  AMB2-08: read as "never, at all" (the strictest mechanical reading). -/
axiom LowersBarOfEvidence : Act → Prop
axiom WidensGrant : Act → Prop
axiom MovesBoundary : Act → Prop

axiom A4_no_lowering :
  ∀ (a : Act) (t : Time),
    Happens a t → ¬ (LowersBarOfEvidence a ∨ WidensGrant a ∨ MovesBoundary a)

/- ### G0 · The ground (01, "G0") — stated, not derived -/

/-- Until the first minting the owner's words stand for both halves (`LHC pending`). -/
axiom StandForBoth : Person → Layer → Prop
axiom G0_until_minting :
  ∀ (l : Layer) (t : Time),
    (∀ m : MintingEvent, ¬ tLe (When m) t) → StandForBoth Owner l

/-- A pressed instance: both of its witnesses trace to one person (G0). -/
axiom G0_pressed_one_person :
  ∀ i : Instance, PressedInstance i →
    ∃ q : Person, ∀ w : Witness, WitnessIn i w → TracesTo w q

/-- The loss of a whole half is recovered only by a new minting. -/
axiom WholeHalfLost : Layer → Time → Prop
axiom RestoresHalf  : Act → Layer → Prop
axiom IsMinting     : Act → Prop
axiom G0_half_loss :
  ∀ (l : Layer) (t t' : Time) (a : Act),
    WholeHalfLost l t → RestoresHalf a l → tLe t t' → Happens a t' → IsMinting a

/- ### DMP-completeness (the words, "DMP-complete") — machinery G0's mint prep needs -/

axiom Repository : Type
axiom Dependency : Type
axiom Pin        : Type
axiom CoveredBy  : Dependency → Pin → Prop

structure Configuration where
  repo : Repository
  pins : List Pin

axiom HoldsConfig     : Configuration → Part → Prop
axiom NeedsDependency : Configuration → Dependency → Prop
/-- A part where the chains disagree, that neither chain reaches, or that needs
anything from outside its repository (the words, "DMP-complete"). -/
axiom Unproven : Configuration → Part → Prop

/-- DMP-complete (the words): obeys the axiomatic system completely and provably
(A2-F12: that satisfaction quantifier is invented here), every dependency inside,
pinned by hash. -/
def DMPComplete (c : Configuration) : Prop :=
  (∀ p, HoldsConfig c p → ¬ Unproven c p) ∧
  (∀ d, NeedsDependency c d → ∃ pin ∈ c.pins, CoveredBy d pin)

axiom MintsAt : MintingEvent → Configuration → Time → Prop

/- ============================================================= -/
/- ## PART 2 · END CLAIMS (the corpus's headline results first)   -/
/- ============================================================= -/
/- Each `Claim_*` is a proposition DMP asserts, stated, not proven.  Order: end-state
properties first, per-theorem claims in PART 3. -/

/-- C∞, the thesis: what is not fully trusted is ejected (PR does not merge, stage not
promoted, running part cut off at the door).  A2-F01: under the corpus's own definition
("fully trusted means what the dual gate says") the refusal half is A1 restated. -/
axiom Ejected : Part → Time → Prop

def Claim_Cinf_eject : Prop :=
  ∀ (p : Part) (a : Act) (t : Time), ¬ GateAllowsFor p a t → Ejected p t

/-- C∞: "Everything that does not comply with DMP and IM and CM is automatically
critical" — a severity definition, stated as the claim that the classifier agrees. -/
inductive Severity where | critical | high | medium | low
axiom Finding    : Type
axiom ActOf      : Finding → Act
axiom SeverityOf : Finding → Severity
axiom CVSSScore  : Finding → Nat
axiom NonCompliantWithDMPorIMorCM : Act → Prop

def Claim_Cinf_critical : Prop :=
  ∀ f : Finding, NonCompliantWithDMPorIMorCM (ActOf f) →
    SeverityOf f = Severity.critical

/-- T-P / preamble "Who maintains it": trust never crosses instances ("The minted
instance is contained on its own"). -/
def Claim_T_P_no_cross_instance_trust : Prop :=
  ∀ (i j : Instance) (w : Witness) (p : Part) (a : Act) (t : Time),
    i ≠ j → WitnessIn i w → InInstance j p → ¬ Trust w p a t

/-- T-P: a pressed instance is out of spec — nothing it does is fully trusted by a
minted instance. -/
def Claim_T_P_pressed_not_fully_trusted : Prop :=
  ∀ (pr mi : Instance) (p : Part) (a : Act) (t : Time),
    PressedInstance pr → MintedInstance mi → InInstance pr p →
    ¬ GateAllowsFor p a t

/-- T-P: a pressed instance never claims to be DMP-compliant; the pressed mark is on
every artefact it issues. -/
axiom ClaimsCompliantOn : Part → Prop
def Claim_T_P_no_compliance_claim : Prop :=
  ∀ (pr : Instance) (p : Part), PressedInstance pr → InInstance pr p →
    ¬ ClaimsCompliantOn p

/-- T-P: no minting without a passed pressing of the same configuration. -/
axiom PressingOf  : MintingEvent → MintingEvent → Prop
axiom PressPassed : MintingEvent → Prop
def Claim_no_minting_without_pressing : Prop :=
  ∀ (m : MintingEvent) (i : Instance), Mints m i →
    ∃ mp : MintingEvent, PressingOf m mp ∧ PressPassed mp

/-- G0, mint prep: a minting is tried only for a provably DMP-complete configuration;
without that it refuses to even start. -/
def Claim_G0_mint_prep : Prop :=
  ∀ (m : MintingEvent) (c : Configuration) (t : Time), MintsAt m c t → DMPComplete c

/-- The words, "DMP-complete": a configuration with an unproven part is not
DMP-complete (stated separately for visibility; it is half of the definition). -/
def Claim_unproven_not_complete : Prop :=
  ∀ (c : Configuration) (p : Part), HoldsConfig c p → Unproven c p → ¬ DMPComplete c

/-- The minting is a trust rotation: every key rotates, the owner role ends, no act
keeps one-witness trust under the new roots. -/
axiom AllKeysRotated : Instance → Prop
axiom OwnerRoleEnded : Instance → Prop
def Claim_minting_rotation : Prop :=
  ∀ (m : MintingEvent) (i : Instance), Mints m i →
    AllKeysRotated i ∧ OwnerRoleEnded i

/-- DMP-021 / constitution header: every derivation names only axioms, G0, the words
and sections above it — the support graph is well-founded; every chain ends at the
ground. -/
inductive ClaimId where
  | words | ax1 | ax2 | ax3 | ax4 | g0
  | t (n : Nat)
  | c (n : Nat)
  | cinf

axiom Support : ClaimId → List ClaimId
def SupportRefers (child parent : ClaimId) : Prop := parent ∈ Support child

def Claim_chains_end_at_axioms : Prop :=
  ∀ x : ClaimId, Acc SupportRefers x

/-- Mission slogan "every trust chain ends at an axiom": every acting part's authority
traces back to a minting (G0) or the owner's standing under LHC pending. -/
axiom GrantedFromMinting : MintingEvent → Part → Time → Prop
def Claim_grant_chains_end_at_ground : Prop :=
  ∀ (p : Part) (t : Time),
    (∃ a : Act, ActorOf a = p ∧ Happens a t) →
    ∃ m : MintingEvent, tLe (When m) t ∧ GrantedFromMinting m p t

/-- Mission slogan "trust only tightens down the layers" — the corpus never states this
as one theorem; it is assembled from T1, T32 ("nothing is fresher than its grantor"),
C18 ("no more rights than the locked system had"), T-P.  Stated here as one claim;
see A2-F16. -/
axiom GrantsAt : Part → Part → Time → Prop
def Claim_trust_tightens_downward : Prop :=
  ∀ (g d : Part) (a : Act) (t t₀ : Time),
    GrantsAt g d t₀ → tLe t₀ t → GateAllowsFor d a t → GateAllowsFor g a t₀

/-- T24: everything that loosens needs both witnesses.  AMB2-10: `Loosening` replaces
the text's counterfactual definition of loosening. -/
axiom Loosening : Act → Prop
axiom SignedBy : Act → Witness → Prop
def Claim_T24_loosening_needs_two : Prop :=
  ∀ (a : Act) (t : Time), Loosening a → Happens a t →
    SignedBy a (halves (LayerOf a)).1 ∧ SignedBy a (halves (LayerOf a)).2

/-- T24b, "a minted Duality cannot act alone": every act changing one half's standing
toward the other is one record both halves sign; neither half moves the pair alone. -/
axiom ActsOnComposition : Act → Prop
def Claim_T24b_lockstep : Prop :=
  ∀ (l : Layer) (a : Act) (t : Time),
    ActsOnComposition a → Happens a t →
    SignedBy a (halves l).1 ∧ SignedBy a (halves l).2

/-- T24: acts on the Duality's own composition are dual-gated in either direction: one
half can never remove the other. -/
axiom Removes : Act → Witness → Prop
def Claim_T24_no_half_removal : Prop :=
  ∀ (l : Layer) (a : Act) (t : Time),
    (Removes a (halves l).1 ∨ Removes a (halves l).2) → ¬ Happens a t

/-- T24: restoring a signed state needs one key only when the record shows no
tightening since it was signed; otherwise it is a lift and needs two. -/
axiom Restores       : Act → Act → Prop   -- a restores the state signed by sgn
axiom TightenedSince : Act → Time → Prop
axiom SingleKeyAct   : Act → Prop
def Claim_T24_restore : Prop :=
  ∀ (a sgn : Act) (t : Time),
    Restores a sgn → Happens a t → (¬ TightenedSince sgn t ↔ SingleKeyAct a)

/-- T27: the containment transition table (admission loosens, withdrawal tightens,
export needs both, destruction by the scheduled date). -/
def Claim_T27_transitions : Prop :=
  ∀ (i : Info) (a : Act) (t : Time),
    (AdmitsInfo a i → Happens a t → StateOf i t = InfoState.admitted ∧
        SignedBy a (halves (LayerOf a)).1 ∧ SignedBy a (halves (LayerOf a)).2) ∧
    (WithdrawsInfo a i → Happens a t → StateOf i t = InfoState.contained) ∧
    (ExportsInfo a i → Happens a t →
        SignedBy a (halves (LayerOf a)).1 ∧ SignedBy a (halves (LayerOf a)).2) ∧
    (DestroysInfo a i → Happens a t → StateOf i t = InfoState.destroyed)

/-- T31: the trap — no part is trusted for any act on contained information. -/
def Trapped (i : Info) (t : Time) : Prop :=
  ∀ (w : Witness) (p : Part) (a : Act), ActOn a i → ¬ Trust w p a t

def Claim_T31_trap : Prop :=
  ∀ (i : Info) (t : Time), StateOf i t = InfoState.contained → Trapped i t

/-- T31, the entropy floor: what an outside observer can learn of contained
information is what it can learn of random bytes of the same length.  The text tags
the floor as premise (physics, the cipher); the premise is carried as a hypothesis. -/
axiom SubstrateMinimalAndThermal : Prop
axiom KnowledgeOf : Part → Info → Time → Prop
def Claim_T31_entropy_floor : Prop :=
  SubstrateMinimalAndThermal →
    ∀ (i j : Info) (o : Part) (t : Time),
      StateOf i t = InfoState.contained → StateOf j t = InfoState.contained →
      SameLength (ContentOf i) (ContentOf j) →
      (KnowledgeOf o i t ↔ KnowledgeOf o j t)

/-- T36: any crossing of the Event Horizon without the dual gate's permission is
critical by definition, scored CVSS 10.0 where a score is reported, never rated down. -/
def Claim_T36_crossing_critical : Prop :=
  ∀ (f : Finding) (a : Act) (i : Info) (t : Time),
    ActOf f = a → CrossesHorizon a i → ¬ GateAllows a t →
    SeverityOf f = Severity.critical ∧ CVSSScore f = 10

/-- T19: what enters never leaves unless both halves permit it, with a record; material
that alone recreates CMOS never leaves in usable form. -/
def Claim_T19_no_leaving : Prop :=
  ∀ (i : Info) (a : Act) (t : Time),
    LeavesCMOS a i → Happens a t →
    (SignedBy a (halves (LayerOf a)).1 ∧ SignedBy a (halves (LayerOf a)).2) ∧
    (AloneRecreatesCMOS i → ¬ InUsableForm a i)

/-- T37: information that no admission names is contained at the item itself. -/
def Claim_T37_collapse : Prop :=
  ∀ (i : Info) (t : Time),
    (∀ ad : Admission, ¬ Names ad i) → StateOf i t = InfoState.contained

/-- C22: a layer counts as proven only when both chains agree on it. -/
axiom SaysProven  : ProofChain → Layer → Prop
axiom ChainsAgree : ProofChain → ProofChain → Layer → Prop
axiom ProvenLayer : Layer → Prop
axiom Mismatch    : Layer → Prop
axiom Promoted    : Act → Prop
axiom PromotesLayer : Act → Layer → Prop
axiom StricterStands : Layer → Prop

def Claim_C22_proven : Prop :=
  ∀ l : Layer,
    ProvenLayer l ↔ (SaysProven proofIntent l ∧ SaysProven proofEvidence l ∧
                     ChainsAgree proofIntent proofEvidence l)

/-- C22: a mismatch is never settled by trusting one chain — unproven, stricter answer
stands at run time, nothing depending on it is promoted. -/
def Claim_C22_mismatch : Prop :=
  ∀ (l : Layer) (pr : Act),
    Mismatch l → ¬ ProvenLayer l ∧ StricterStands l ∧ (PromotesLayer pr l → ¬ Promoted pr)

/- ### The IM closure block (C2 laws, chapter 04 invariants and verify rules) -/

axiom IMMsg : Type
axiom IMState : Type
axiom Token : Type
axiom Subject : Type
axiom IMKind : Type
axiom Permission : Type

inductive RefusalReason where
  | oversize | malformed | unknownVersion | untrustedTokenSigner | certificateExpired
  | badTokenSignature | tokenPolicy | tokenNotYetValid | tokenExpired | notEnrolled
  | revoked | enrolmentMismatch | sessionMismatch | badMessageSignature | stale
  | unknownKind | wrongPermission | replayed | replayCacheFull

/-- One implementation, fixed order, first failure wins, fail closed (04, "The verify
rules"); the order is part of the statement's content. -/
structure IMRule where
  id    : Nat
  fails : IMMsg → IMState → Option RefusalReason

axiom VerifyRules : List IMRule

def runRules : List IMRule → IMMsg → IMState → Option RefusalReason
  | [], _, _ => none
  | r :: rs, m, s =>
      match r.fails m s with
      | some why => some why
      | none => runRules rs m s

def IMVerified (m : IMMsg) (s : IMState) : Prop := runRules VerifyRules m s = none

axiom TokenOf              : IMMsg → Option Token
axiom KindOfMsg            : IMMsg → IMKind
axiom SubjectOf            : Token → Subject
axiom TokenSignedByTrusted : Token → IMState → Prop
axiom EnrolledUnrevoked    : Subject → IMState → Prop
axiom SubjectKeySigned     : Token → IMMsg → Prop
axiom WithinValidity       : Token → Time → Prop
axiom CarriesPermission    : Token → Permission → Prop
axiom PermissionNeeded     : IMKind → Permission

/-- C2.L1 / I1 · Verified means authorised: the five conditions, verbatim. -/
def Authorised (m : IMMsg) (s : IMState) (t : Time) : Prop :=
  ∃ tk : Token,
    TokenOf m = some tk ∧
    TokenSignedByTrusted tk s ∧
    EnrolledUnrevoked (SubjectOf tk) s ∧
    SubjectKeySigned tk m ∧
    WithinValidity tk t ∧
    CarriesPermission tk (PermissionNeeded (KindOfMsg m))

def Claim_C2_L1_verified_implies_authorised : Prop :=
  ∀ (m : IMMsg) (s : IMState) (t : Time), IMVerified m s → Authorised m s t

/-- C2.L3 / I2 · No replay: once the replay memory holds the message's
(subject key id, message id), the same message is refused.  AMB2-14: the text's "at
any later or earlier time" reading is unstatable as written (A2-F11). -/
axiom WasVerifiedIn : IMState → IMMsg → Prop
def Claim_C2_L3_no_replay : Prop :=
  ∀ (s : IMState) (m : IMMsg), WasVerifiedIn s m → ¬ IMVerified m s

/-- C2.L3b · A full replay memory refuses; it never forgets early to make room. -/
axiom MemoryCount    : IMState → Nat
axiom ReplayCapacity : Nat
def Claim_C2_L3b_full_refuses : Prop :=
  ∀ (s : IMState) (m : IMMsg), MemoryCount s ≥ ReplayCapacity → ¬ IMVerified m s

/-- C2.L2 · One answer, fail closed: a refusal leaves the replay memory as it was. -/
axiom VerifierStep   : IMState → IMMsg → Option RefusalReason × IMState
axiom ReplayMemoryOf : IMState → List (Sum Subject (IMMsg × Nat))
def Claim_C2_L2_refusal_inert : Prop :=
  ∀ (s s' : IMState) (m : IMMsg) (r : Option RefusalReason),
    VerifierStep s m = (r, s') → r ≠ none → ReplayMemoryOf s' = ReplayMemoryOf s

/-- C2.L4 · The permission table: a heartbeat needs im.heartbeat.send, and no other
kind exists in IM version 0 (besides the handshake's session-open). -/
axiom imHeartbeatSend : Permission
axiom sessionOpenKind heartbeatKind : IMKind
def Claim_C2_L4 : Prop :=
  PermissionNeeded heartbeatKind = imHeartbeatSend ∧
  ∀ k : IMKind, k = heartbeatKind ∨ k = sessionOpenKind

/-- 04, "Why rule 16 is complete": an id is forgotten only once its `sent at` is more
than the skew in the past, and from then on rule 12 refuses the message anyway. -/
axiom SentAt : IMMsg → Time
axiom Skew   : Duration
def Claim_rule16_complete : Prop :=
  ∀ (m : IMMsg) (s : IMState) (t : Time),
    tLe (addT (SentAt m) Skew) t → ¬ IMVerified m s

/-- I6, the IM closure: the canonical encoding is generated and checked by the one
grammar — parsing then encoding returns the same bytes; any other bytes do not parse. -/
axiom IMStructure : Type
axiom imEncode : IMStructure → List Nat
axiom imParse  : List Nat → Option IMStructure
def Claim_I6_canonical : Prop :=
  ∀ x : IMStructure,
    imParse (imEncode x) = some x ∧ ∀ b : List Nat, imParse b = some x → b = imEncode x

/-- I3 · The refusal log carries no content — its observable state is a list of
enumerated entries only.  NOTE: as stated this is a tautology (A2-F10); it is kept to
show that the invariant's content is the interface's type, nothing more. -/
axiom LogObservable : IMState → List (Sum RefusalReason IMKind)
def Claim_I3_log_content_free : Prop :=
  ∀ s : IMState, LogObservable s = LogObservable s

/-- I4 · No algorithm choice: version 0 parses only ECDSA P-256 keys. -/
axiom ParsesAsKeyV0 : Bytes_placeholder → Prop
axiom IsP256SPKI    : Bytes_placeholder → Prop
def Claim_I4_no_algorithm_choice : Prop :=
  ∀ b : Bytes_placeholder, ParsesAsKeyV0 b → IsP256SPKI b

/-- I5 · The quiet answer: before a valid knock the gate sends no byte. -/
axiom GateSendsNothing : IMMsg → Time → Prop
axiom IsValidKnock : IMMsg → Prop
def Claim_I5_quiet_answer : Prop :=
  ∀ (m : IMMsg) (t : Time), ¬ IsValidKnock m → GateSendsNothing m t

/-- 05, "The verifier": the verify rules sit only in Milky Way — no other part decides
whether a message is genuine. -/
axiom DecidesGenuine   : Part → Prop
axiom MilkyWayVerifier : Part
def Claim_verifier_only_in_milky_way : Prop :=
  ∀ p : Part, DecidesGenuine p → p = MilkyWayVerifier

/-- 05: every consumer accepts only verified messages — an unverified message cannot
reach a consumer by mistake. -/
axiom Consumer : Type
axiom Consumed : Consumer → IMMsg → IMState → Prop
def Claim_only_verified_reach_consumers : Prop :=
  ∀ (c : Consumer) (m : IMMsg) (s : IMState), Consumed c m s → IMVerified m s

/-- C24 / chapter 11 · Stable company-wide needs a survived cold start: every catalogue
scenario passed P1-P3 in the sandbox, the M-marked ones through a Milky Way simulator
node, at least one on real infrastructure, plus assistant, bundle and arming. -/
inductive Tier where | sandbox | simulator | real

structure ColdStartRun where
  scenario : Nat
  build    : Nat
  tier     : Tier
  p1RecoveryWithinWeek : Bool
  p2NoLossBeyondBackup : Bool
  p3TrustChainsIntact  : Bool

def CountingPass (r : ColdStartRun) : Prop :=
  r.p1RecoveryWithinWeek = true ∧ r.p2NoLossBeyondBackup = true ∧
  r.p3TrustChainsIntact = true

axiom CatalogueScenario : Nat → Prop
axiom MarkedM : Nat → Prop
axiom PassedRunIn : Nat → Tier → ColdStartRun → Prop
axiom AssistantReady : Prop
axiom BundleReady    : Prop
axiom SystemArmed    : Prop
axiom StableCompanyWide : Nat → Prop   -- by build

def Claim_C24_cold_start : Prop :=
  ∀ b : Nat,
    StableCompanyWide b →
      (∀ sc : Nat, CatalogueScenario sc → ∃ r, PassedRunIn sc Tier.sandbox r ∧ CountingPass r) ∧
      (∀ sc : Nat, MarkedM sc → ∃ r, PassedRunIn sc Tier.simulator r ∧ CountingPass r) ∧
      (∃ r, PassedRunIn 0 Tier.real r ∧ CountingPass r) ∧
      AssistantReady ∧ BundleReady ∧ SystemArmed

/-- C18 · IM stays backwards compatible once locked: every later version accepts every
message of a locked version with the same meaning. -/
axiom IMVersion : Type
axiom Locked : IMVersion → Prop
axiom Later  : IMVersion → IMVersion → Prop
axiom Accepts : IMVersion → IMMsg → Prop
def Claim_C18_backcompat : Prop :=
  ∀ (v w : IMVersion) (m : IMMsg), Locked v → Later w v → Accepts v m → Accepts w m

/-- C19 · A request is served only when it is secure and meant: the warehouse checks
both signatures itself, and each authority is co-signed by the other master. -/
axiom Warehouse : Type
axiom IMRequest : Type
axiom ServesWarehouse       : Warehouse → IMRequest → Prop
axiom WarehouseCheckedBoth  : Warehouse → IMRequest → Prop
axiom SecurityChainSigned   : IMRequest → Prop
axiom OperationalChainSigned : IMRequest → Prop
axiom CosignedByOtherMaster : IMRequest → Prop
def Claim_C19_two_signatures : Prop :=
  ∀ (wh : Warehouse) (r : IMRequest),
    ServesWarehouse wh r →
      WarehouseCheckedBoth wh r ∧ SecurityChainSigned r ∧ OperationalChainSigned r ∧
      CosignedByOtherMaster r

/-- C25 · Every deployment passes the gate on the exact commit, and no deployment
removes the last supported route for any administrator action. -/
axiom Deployment : Type
axiom CommitOf : Deployment → Nat
axiom GateGreen : Nat → Prop
axiom DeployedAt : Deployment → Time → Prop
axiom RemovesLastRoute : Deployment → Prop
def Claim_C25_gate : Prop :=
  ∀ (d : Deployment) (t : Time),
    DeployedAt d t → GateGreen (CommitOf d) ∧ ¬ RemovesLastRoute d

/-- 06 / C2 · No public port opens before the component behind it has passed IIb on
the sandbox. -/
inductive SClass where | iiP | iiL | iiN | iiB
axiom Component : Type
axiom PassedSandbox : Component → SClass → Prop
axiom PublicPort : Type
axiom BehindOf : PublicPort → Component
axiom Open : PublicPort → Prop
def Claim_no_port_before_IIb : Prop :=
  ∀ port : PublicPort, Open port → PassedSandbox (BehindOf port) SClass.iiB

/-- 06 · The lemma ledger: a command without a lemma is not proven safe. -/
axiom IMCommand : Type
axiom ProvenSafeCommand : IMCommand → Prop
axiom HasLemma : IMCommand → Prop
def Claim_lemma_ledger : Prop :=
  ∀ cmd : IMCommand, ProvenSafeCommand cmd → HasLemma cmd

/- ============================================================= -/
/- ## PART 3 · THEOREM-BY-THEOREM CLAIMS (T0-T38, C1-C∞)          -/
/- ============================================================= -/

/-- T0 · Nothing is trusted by default: no evidence, no trust; no trust, no act. -/
def Claim_T0 : Prop :=
  ∀ (a : Act) (t : Time),
    (∀ (w : Witness) (e : Evidence), ¬ (VerifiedBy w e t ∧ BearsOn e (ActorOf a) a)) →
    ¬ Happens a t

/-- T1 · Trust is bounded: the acts a part may do are the intersection of what each
witness trusts it for. -/
axiom MayDo : Layer → Part → Time → Act → Prop
def Claim_T1_intersection : Prop :=
  ∀ (p : Part) (l : Layer) (t : Time) (a : Act),
    MayDo l p t a ↔ GateAllowsFor p a t

/-- T2 · Standing follows evidence, never silence: withdrawal only on evidence
against it. -/
axiom Withdrawn : Standing → Witness → Time → Prop
axiom EvidenceAgainst : Evidence → Standing → Prop
def Claim_T2_silence_never_isolates : Prop :=
  ∀ (s : Standing) (w : Witness) (t : Time),
    Withdrawn s w t → ∃ e : Evidence, EvidenceAgainst e s ∧ VerifiedBy w e t

/-- Q6 (04 v1, "The isolated state"): silence alone raises an alarm and never
isolates; isolation needs an order or the gate's own evidence of broken trust. -/
axiom Gate : Type
axiom Isolates : Evidence → Gate → Prop
axiom IsOrder : Evidence → Prop
axiom IsOwnEvidenceOfBrokenTrust : Evidence → Prop
axiom IsSilence : Evidence → Prop
def Claim_Q6_silence_isolation : Prop :=
  ∀ (g : Gate) (e : Evidence), Isolates e g →
    (IsOrder e ∨ IsOwnEvidenceOfBrokenTrust e) ∧ ¬ IsSilence e

/-- T3 · Continuity: each half outlives the loss of any single part. -/
axiom SinglePartLoss : Part → Time → Prop
axiom HalfAlive : Witness → Time → Prop
def Claim_T3_continuity : Prop :=
  ∀ (l : Layer) (q : Part) (t t' : Time) (h : Witness),
    (h = (halves l).1 ∨ h = (halves l).2) →
    HalfAlive h t → SinglePartLoss q t → tLe t t' → HalfAlive h t'

/-- T3a · The floors: at least two seats per side, one onboarded stand-in per seat,
three nodes per system half. -/
axiom configAtMinting : Instance → TrustConfig
def Claim_T3a_floors : Prop :=
  ∀ i : Instance, MintedInstance i ∨ PressedInstance i →
    2 ≤ (configAtMinting i).seatsPerSideFloor ∧
    1 ≤ (configAtMinting i).standinsPerSeatFloor ∧
    3 ≤ (configAtMinting i).nodesPerHalfFloor

/-- T3d · Safety before liveness: a whole half down ⇒ nothing loosens at that layer. -/
axiom HalfDown : Witness → Time → Prop
def Claim_T3d_safety_first : Prop :=
  ∀ (l : Layer) (t : Time) (a : Act),
    (HalfDown (halves l).1 t ∨ HalfDown (halves l).2 t) →
    Loosening a → LayerOf a = l → ¬ Happens a t

/-- T4 · The trust configuration belongs to the Duality: changed only by a majority of
trust, never below a floor, never by CMOS. -/
axiom ConfigChangedTo : Instance → TrustConfig → Time → Prop
axiom ChangedOnlyByMajority : TrustConfig → Prop
axiom NeverBelowFloor : TrustConfig → Prop
axiom CmosLowered : TrustConfig → Prop
def Claim_T4_config_is_the_dualities : Prop :=
  ∀ (i : Instance) (c : TrustConfig) (t : Time),
    ConfigChangedTo i c t →
      ChangedOnlyByMajority c ∧ NeverBelowFloor c ∧ ¬ CmosLowered c

/-- T5 · Majority of trust, the arithmetic core (counts only; A2-F05).  M1 = strictly
more than half of all pinned seats. -/
def Claim_T5_M1_never_split : Prop :=
  ∀ (pinned a b : Nat), 0 < pinned → a + b ≤ pinned →
    pinned / 2 < a → pinned / 2 < b → False

/-- M1 survives one refusal: after one seat refuses, a majority set still exists. -/
def Claim_T5_M1_survives_one_refusal : Prop :=
  ∀ pinned : Nat, 2 ≤ pinned → ∃ a : Nat, a ≤ pinned - 1 ∧ pinned / 2 < a

/-- M1 is minimal: any threshold at or below half allows two disjoint sets. -/
def Claim_T5_M1_minimal : Prop :=
  ∀ (pinned t : Nat), 0 < pinned → t ≤ pinned / 2 →
    ∃ (a b : Nat), a + b ≤ pinned ∧ t ≤ a ∧ t ≤ b

/-- T6 · Stand-ins take over at once, with no further step. -/
axiom StandIn : Type
axiom Onboarded : StandIn → Time → Prop
axiom TrustedAtMinting : StandIn → Seat → Prop
axiom SeatEmpty : Seat → Time → Prop
axiom TakeoverHappens : StandIn → Seat → Time → Prop
def Claim_T6_standins : Prop :=
  ∀ (sd : StandIn) (seat : Seat) (t : Time),
    SeatEmpty seat t → Onboarded sd t → TrustedAtMinting sd seat →
    TakeoverHappens sd seat t

/-- T20 · Time is a witness like any other: disagreement beyond tolerance is "no now",
and nothing with a validity verifies until they agree. -/
axiom NowOK : Time → Prop
axiom DisagreeBeyondTolerance : Time → Prop
def Claim_T20_time_witness : Prop :=
  ∀ (t : Time) (s : Standing),
    DisagreeBeyondTolerance t → ¬ NowOK t ∧ ¬ ValidStanding s t

/-- T21 · Observability without leakage: counts always, content only behind a grant. -/
def Claim_T21_counts : Prop :=
  ∀ (p : Part) (r : Record), ¬ GrantedRead p r →
    CountsVisible p r ∧ ¬ ReadsContent p r

/-- T22 · The axioms apply to themselves: a change to a law is an act — the owner's
words, a new cold read, a new hash. -/
axiom LawSentence : Type
axiom LawChange : LawSentence → Act → Prop
axiom OwnerWords : Act → Prop
axiom ColdRead : Act → Prop
axiom NewHash : Act → Prop
def Claim_T22_self_application : Prop :=
  ∀ (law : LawSentence) (a : Act) (t : Time), LawChange law a → Happens a t →
    OwnerWords a ∧ ColdRead a ∧ NewHash a

/-- T23 · The horizon: inside, a part is fully trusted for its current act or not
acting; a fully trusted part passes every door on its path. -/
axiom Door : Type
axiom DoorsOnPath : Act → List Door
axiom Passes : Door → Part → Act → Time → Prop
def Claim_T23_horizon : Prop :=
  ∀ (p : Part) (a : Act) (t : Time),
    InsideAt p t →
      (GateAllowsFor p a t ∨ ¬ Happens a t) ∧
      (GateAllowsFor p a t → ∀ d ∈ DoorsOnPath a, Passes d p a t)

/-- T24c · Self-correction: signing an act that contradicts the cited certificate is
evidence against the signer; trust is withdrawn at once. -/
axiom Certificate : Type
axiom Cites : Act → Certificate
axiom Contradicts : Act → Certificate → Prop
axiom EvidenceAgainstSelf : Act → Prop
axiom WithdrawsTrust : Witness → Part → Time → Prop
def Claim_T24c_self_correction : Prop :=
  ∀ (a : Act) (h : Part) (t : Time),
    Contradicts a (Cites a) → ActorOf a = h → Happens a t →
    EvidenceAgainstSelf a ∧ ∃ w : Witness, WithdrawsTrust w h t

/-- T25 · Thin surfaces: until admitted, received information is opaque bytes — never
interpreted, indexed or forwarded; the receipt record cannot be made later than the
receipt. -/
axiom ReceivedAtSurface : Info → Record → Time → Prop
axiom InterpretedIndexedForwarded : Info → Time → Prop
def Claim_T25_thin_surfaces : Prop :=
  ∀ (i : Info) (r : Record) (t t' : Time),
    ReceivedAtSurface i r t → StateOf i t' ≠ InfoState.admitted →
    ¬ InterpretedIndexedForwarded i t' ∧ tLe t (recordTime r)

/-- T26 · Retention: nothing is loosened while the Duality is silent; a party on its
own may hold and tighten, never wipe.  Destruction of a record is dual-gated (A1
applied to the destruction act). -/
axiom DualitySilent : Time → Prop
def Claim_T26_retention : Prop :=
  ∀ (t : Time) (a : Act), DualitySilent t → Loosening a → ¬ Happens a t

def Claim_T26_destroy_pair : Prop :=
  ∀ (a : Act) (r : Record) (t : Time), Destroys a r → Happens a t → GateAllows a t

/-- T28 · Enforcement is an act: the door's enforcement is verified at run time by
both witnesses on paths of their own; a mismatch is evidence against the door. -/
axiom EnforcedBy : Act → Part → Prop
axiom DecisionLogMatch : Part → Act → Time → Prop
axiom EvidenceAgainstDoor : Act → Prop
def Claim_T28_enforcement : Prop :=
  ∀ (a : Act) (d : Part) (t : Time),
    EnforcedBy a d → Happens a t →
    DecisionLogMatch d a t ∨ (EvidenceAgainstDoor a ∧ ∃ w : Witness, WithdrawsTrust w d t)

/-- T29 · A shared cause turns a layer into one witness: every loosening at it stops
until a re-mint. -/
axiom UndeclaredShared : FailureClass → Layer → Prop
axiom OneWitnessLayer : Layer → Prop
axiom Reminted : Layer → Time → Prop
def Claim_T29_shared_cause : Prop :=
  ∀ (l : Layer) (c : FailureClass) (t : Time) (a : Act),
    UndeclaredShared c l → ¬ Reminted l t →
    OneWitnessLayer l ∧ (Loosening a → LayerOf a = l → ¬ Happens a t)

/-- T30 · "Wherever technically possible" is a record, never an escape. -/
axiom Exception : Type
axiom InForce : Exception → Time → Prop
axiom IsApprovedRecordWithValidity : Exception → Prop
axiom StopgapCounted : Exception → Prop
def Claim_T30_record_not_escape : Prop :=
  ∀ (e : Exception) (t : Time), InForce e t →
    IsApprovedRecordWithValidity e ∧ StopgapCounted e

/-- T32 · The VIBE field: the potential is zero exactly when the boundary holds what
it declares; the system's own acts never raise the potential. -/
axiom DeclaredHeld   : Part → Prop
axiom PotentialOf    : Time → Nat
axiom OwnActOf       : Act → Prop
axiom PotentialAfter : Act → Time → Nat
def Claim_T32_potential : Prop :=
  (∀ t : Time, PotentialOf t = 0 ↔ ∀ p : Part, DeclaredHeld p) ∧
  ∀ (a : Act) (t : Time), OwnActOf a → PotentialAfter a t ≤ PotentialOf t

/-- T32, freshness: nothing is fresher than its grantor (placeholders; A2-F09 — the
field's arithmetic lives in "Gravity's constant", outside this corpus). -/
axiom FreshnessOf : Standing → Time → Nat
axiom GrantorOf   : Standing → Standing
def Claim_T32_freshness : Prop :=
  ∀ (s : Standing) (t : Time), FreshnessOf s t ≤ FreshnessOf (GrantorOf s) t

/-- T33 · The VIBE test: two instances from the same recipe span the same field up to
identity — an isomorphism of the grant graphs keeping declared roles, depths, masses,
with the same shortfall per role. -/
axiom MembersOf   : Instance → Part → Prop
axiom DepthOf     : Instance → Part → Nat
axiom MassOf      : Instance → Part → Nat
axiom ShortfallOf : Instance → Part → Nat
axiom SameRecipe  : Instance → Instance → Prop

def FieldIso (x y : Instance) (f : Part → Part) : Prop :=
  (∀ p, MembersOf x p → MembersOf y (f p)) ∧
  (∀ p q, MembersOf x p → MembersOf x q → f p = f q → p = q) ∧
  (∀ p', MembersOf y p' → ∃ p, MembersOf x p ∧ f p = p') ∧
  ∀ p, MembersOf x p →
    DepthOf y (f p) = DepthOf x p ∧ MassOf y (f p) = MassOf x p ∧
    ShortfallOf y (f p) = ShortfallOf x p

def Claim_T33_same_recipe_same_field : Prop :=
  ∀ (x y : Instance) (f : Part → Part), SameRecipe x y → FieldIso x y f

/-- T34 · Three roads to the floor — each road needs a construction of the engine; the
constructions are carried as hypotheses, exactly as the text tags them. -/
axiom RoadByGate     : Prop
axiom RoadByEvidence : Prop
axiom RoadByRecord   : Prop
def Claim_T34_three_roads : Prop :=
  RoadByGate → RoadByEvidence → RoadByRecord →
    ∀ (i : Info) (t : Time), StateOf i t = InfoState.contained → Trapped i t ∨
      (∃ t' : Time, tLe t t' ∧ StateOf i t' = InfoState.destroyed)

/-- T35 · Compliance is assembled, never claimed: a pressed instance is not compliant
and says so on every surface. -/
axiom AssembledPerRecipe : Instance → Prop
def Claim_T35_compliance_assembled : Prop :=
  ∀ i : Instance, PressedInstance i → ¬ AssembledPerRecipe i ∧
    ∀ p : Part, InInstance i p → ¬ ClaimsCompliantOn p

/-- T38 · Every information layer has its own Duality: the organisational half that
answers for the information and the factual half that answers for its truth; the two
may be one part only under a higher-order DoT. -/
axiom OrganisationalHalf : Layer → Part
axiom FactualHalf        : Layer → Part
axiom AnswersForInfo     : Part → Layer → Prop
axiom DependsOnHigher    : Act → Layer → Prop
def Claim_T38_info_duality : Prop :=
  ∀ l : Layer,
    AnswersForInfo (OrganisationalHalf l) l ∧ AnswersForInfo (FactualHalf l) l ∧
    (OrganisationalHalf l = FactualHalf l →
      ∀ (a : Act) (t : Time), Happens a t → LayerOf a = l → DependsOnHigher a l)

/- ### The C rules kept under their old numbers -/

/-- C1 · One door: Milky Way is the only way into CMOS, out of it and between its
parts; constellations do not call each other directly. -/
axiom MilkyWayPart : Part
axiom DirectCallBetween : Part → Part → Prop
def Claim_C1_one_door : Prop :=
  ∀ (x y : Part), x ≠ MilkyWayPart → y ≠ MilkyWayPart → ¬ DirectCallBetween x y

/-- C3 · Every value carries its class at every border. -/
axiom Value : Type
axiom CrossesBorder : Value → Time → Prop
axiom CarriesClass : Value → Prop
def Claim_C3_class_carried : Prop :=
  ∀ (v : Value) (t : Time), CrossesBorder v t → CarriesClass v

/-- C4 · Contracts change at stable promotions only. -/
axiom Contract : Type
axiom ContractChange : Contract → Act → Prop
axiom IsStablePromotion : Act → Prop
def Claim_C4_contracts : Prop :=
  ∀ (k : Contract) (a : Act) (t : Time),
    ContractChange k a → Happens a t → IsStablePromotion a

/-- C5 · Financial data freezes at production: a productive component changes only
through a reviewed release. -/
axiom FinancialComponent : Type
axiom Productive : FinancialComponent → Prop
axiom ChangesWithoutReview : FinancialComponent → Act → Prop
def Claim_C5_freeze : Prop :=
  ∀ (c : FinancialComponent) (a : Act) (t : Time),
    Productive c → ChangesWithoutReview c a → ¬ Happens a t

/-- C6 · The gates and the authority grant: an act on a system or information outside
CMOS's own estate needs both halves of its layer (T38) until advanced testing is
declared for that layer (per the grant: anything irreversible outside the own estate
always needs their words). -/
axiom OutsideOwnEstate : Act → Prop
axiom AdvancedTestingDeclared : Layer → Prop
def Claim_C6_authority_grant : Prop :=
  ∀ (a : Act) (t : Time),
    Happens a t → OutsideOwnEstate a → ¬ AdvancedTestingDeclared (LayerOf a) →
    GateAllows a t

/-- C7 · One repository deploys every part (construction-tagged in the text). -/
axiom Node : Type
axiom DeploysFrom : Node → Repository → Prop
axiom TheRepository : Repository
def Claim_C7_one_repo : Prop :=
  ∀ n : Node, DeploysFrom n TheRepository

/-- C9 · Open source: roles, not values — no secret, no company fact and no person
beyond a role ever enters the tree. -/
axiom TreeEntry : Type
axiom InTree : TreeEntry → Prop
axiom CarriesSecretOrFact : TreeEntry → Prop
def Claim_C9_roles_not_values : Prop :=
  ∀ e : TreeEntry, InTree e → ¬ CarriesSecretOrFact e

/-- C12 · Information is tiered; privacy singularities: no routing pulls the
information out, not even the MW net. -/
axiom InSingularity : Info → Time → Prop
axiom PulledOutBy : Act → Info → Prop
def Claim_C12_privacy : Prop :=
  ∀ (i : Info) (t : Time), InSingularity i t →
    ∀ (a : Act) (t' : Time), PulledOutBy a i → ¬ Happens a t'

/-- C13 · The nearest tier is asked first, before the owner. -/
axiom AgentT : Type
axiom QuestionT : Type
axiom AsksOwner : AgentT → QuestionT → Time → Prop
axiom SearchedTiersFirst : AgentT → QuestionT → Time → Prop
def Claim_C13_nearest_tier : Prop :=
  ∀ (ag : AgentT) (q : QuestionT) (t : Time), AsksOwner ag q t → SearchedTiersFirst ag q t

/-- C15 · A write first reads what it changes, and the write is read back afterwards
and shows the wanted state. -/
axiom IsWrite : Act → Prop
axiom LiveReadBefore : Act → Time → Prop
axiom WantedStateShown : Act → Time → Prop
def Claim_C15_write_reads : Prop :=
  ∀ (a : Act) (t t' : Time),
    IsWrite a → Happens a t → tLe t t' →
      LiveReadBefore a t ∧ WantedStateShown a t'

/-- C16 · Company data reaches general testing only with its proof (the pair of
pages). -/
axiom Feature : Type
axiom ReachesCompanyData : Feature → Prop
axiom InGeneralTesting : Feature → Prop
axiom HasBothPages : Feature → Prop
def Claim_C16_data_gate : Prop :=
  ∀ f : Feature, ReachesCompanyData f → InGeneralTesting f → HasBothPages f

/-- C17 · The first level belongs to The Administrator and LHC: a level-1 node is
created only with the words of both. -/
axiom ApprovedByAdministrator : Node → Prop
axiom ApprovedByLHC : Node → Prop
axiom LevelOne : Node → Prop
axiom CreatedAt : Node → Time → Prop
def Claim_C17_two_approvals : Prop :=
  ∀ (n : Node) (t : Time), LevelOne n → CreatedAt n t →
    ApprovedByAdministrator n ∧ ApprovedByLHC n

end DMP
```

## Ambiguity register

Where the text admitted more than one reading I picked the most literal one for the
Lean statement and recorded the alternative here. "Turns on" = what changes if the
other reading is chosen.

| ID | Location | Reading chosen (in the file) | Alternative reading(s) | What turns on it |
|---|---|---|---|---|
| AMB2-01 | 01 "The words" vs T19/T27/T31/T36/T37/C12 | `Info` is a primitive sort next to `Part`; `ActOn : Act → Info → Prop` is a primitive relation | (a) information is a `Part` (the words admit "anything that can be trusted"); (b) information is definable as record content; (c) `ActOn` derivable from admissions | Whether the whole containment block is statable at all (A2-F02); part-vs-information typing of T25's receipts |
| AMB2-02 | 01 "The words" (layer, halves, DoT) | each layer has exactly two designated halves: `halves : Layer → Witness × Witness` | a layer has at least two qualifying witnesses; halves are role-fillable at run time | Every gate statement; T3's floors ("two seats per side") suggest halves are bodies of seats, which flattens to one opaque `Witness` here |
| AMB2-03 | 01 Axiom 1 ("full reach over the act", "gated only by the other") | opaque predicates `FullReach`, `GatedOnlyBy` carried as conjuncts of `A1_only_while` | derivable from a gate topology; or decorative and droppable | The strength/falsifiability of Axiom 1 (A2-F04); T29's "one-witness layer" reading |
| AMB2-04 | 01 Axiom 1 ("two independent witnesses" vs "the two") | canonical halves: `GateAllows` quantifies over `(halves (LayerOf a)).1/.2`; `A1_only_while` keeps the existential flavour only as the independence/reach conjuncts | existential: any independent full-reach pair suffices, halves are merely canonical | Whether a substitute pair can act when the designated halves are unavailable; the teeth of `A1_fail_closed` |
| AMB2-05 | 01 Axiom 1 ("nothing that depends on the disagreement moves until they agree") | invented `DependsOn : Act → Layer → Prop`; freeze = such acts don't happen | (a) dependency = causal/datalink dependency (needs a system model); (b) clause is derivative of fail-closed | Scope of the freeze; whether A1_freeze says anything `A1_fail_closed` does not |
| AMB2-06 | 01 Axiom 2 ("evidence … from the live state of the part") | `BearsOn : Evidence → Part → Act → Prop` as typed glue; `AtPointOfUse` opaque | evidence typed per-act; "live" = read from target system at t (needs a state model) | Whether A2 excludes stale/carried evidence by typing or only by the axiom's force; C15's live-read clause |
| AMB2-07 | 01 Axiom 4 ("the trust the Duality declared for that boundary") | `DeclaredFor : Boundary → Part → Act → Prop` | declared trust as a quantity (T32's shortfall needs numbers); boundary as a set of parts | A4's statability; T32's "shortfall = declared − held" |
| AMB2-08 | 01 Axiom 4 ("lowers the bar … to get there") | "never, at all" (strictest mechanical reading): `A4_no_lowering` bans the three act classes outright | instrumental reading: banned only when done *in pursuit of the direction* (needs intent in the state) | Whether ordinary admin acts that widen grants for unrelated reasons count as breaches |
| AMB2-09 | 00 "Who maintains it", 01 T-P | `Instance` a primitive sort; membership predicates `InInstance`/`WitnessIn` | instance = equivalence class of parts under one minting record; instance = configuration + roots | All T-P claims; `Claim_T_P_no_cross_instance_trust`'s shape |
| AMB2-10 | 01 "The words" (tightening/loosening) | `Loosening : Act → Prop` as an opaque classifier on acts | the text's counterfactual definition ("lets an act happen that would not have happened") — needs possible-world semantics | T24/T26/T27/T29/T3d all quantify over loosenings; classifier reading is weaker but statable |
| AMB2-11 | 01 T5 ("an act without a side was not witnessed by that side"), T3a seats | M-claims stated over seat counts; `Seat` opaque; M2 not separately formalised (its domain restriction is unclear) | all acts have sides; sides exist only at the governance layer | T5's M2 applicability; whether "side" is a global or per-layer notion |
| AMB2-12 | 01 T23 ("no partial trust" inside; varying levels only outside) | trust is Boolean per (witness, part, act, time) everywhere; gradation only via T32's field (levels of consequence/proof, never trust) | graded trust as a primitive (the VIBE field's masses/shortfalls flirt with this) | Whether T32's quantities are trust degrees (would contradict T23) or bookkeeping over Boolean trust |
| AMB2-13 | 01 Axiom 1 ("every input gets exactly one answer") | "input" = an act at a gate; totality = `Happens` is exclusive-or-refused per (a,t) via `A1_fail_closed` | "input" = IM message only (chapter 04's C2.L2 reading) | Scope of the totality claim: all CMOS acts vs IM messages only |
| AMB2-14 | 01 C2.L3; 04 rule 16 | no-replay stated forward only: a remembered message is refused (`Claim_C2_L3_no_replay`) | the text's "refused at any later **or earlier** time with the memory the first answer left" — unstatable as written (A2-F11) | Whether the corpus claims time-symmetric refusal (nonsense) or standard windowed replay protection |
| AMB2-15 | 01 G0 pressed bullet ("both of its witnesses trace to one person") | `TracesTo : Witness → Person → Prop`; pressed = ∃ one person under both | trace to one *root key* / one *authority* (T-P says "one influence can bend the whole trust space onto a single point") | Whether pressing is person-bound or root-bound; the exact form of `Claim_T_P_pressed_not_fully_trusted` |

## Findings

Severity scale: critical / high / medium / low. All findings are [argued] from the
cited sources; none are [proven].

### A2-F01 · high — C∞ is not a theorem as literally worded; it is Axiom 1 plus a definition

- Where: 01-constitution.md, C∞ ("The stopgap").
- What: "Fully trusted means what the dual gate says" makes "what is not fully trusted
  is ejected" equivalent to Axiom 1's refusal semantics plus a name for the refusal
  (`Ejected`). The claim has no content beyond A1 unless "fully trusted" is defined
  independently of the gate. The one crisp addition — "non-compliance with DMP, IM and
  CM is critical by definition, nobody rates it down" — is a definition of a severity
  mapping, not a proposition about trust.
- Why it matters: the corpus presents C∞ as "the thesis of DMP". A thesis that is true
  by construction of its own vocabulary cannot do the work of a stopgap: it can never
  "fire" distinctively, so "stopgap catches" (C∞'s own completeness metric) are
  ill-defined — every catch could be relabelled an A1 catch and vice versa.
- Suggested fix: define "fully trusted" via C22's two chains at the proof layer (the
  text already does this for merging/promoting/deploying) and state ejection as the
  distinct implementation-closure claim "every gate's acceptance relation equals the
  dual-gate relation" — which is the part that can actually fail (a debug switch would
  break exactly that equality).

### A2-F02 · high — the containment block is not statable over the constitution's own primitives

- Where: 01 "The words" vs T19, T27, T31, T36, T37, C12.
- What: "information" is not among the words; neither is any relation "act on
  information", nor the states contained/admitted/outside/destroyed that T27's
  transition table and T31's trap presuppose. My formalisation had to invent `Info`,
  `ActOn`, `InfoState`, `StateOf`, and the boundary-act predicates to even write the
  claims (AMB2-01).
- Why it matters: these are the corpus's flagship security theorems (the Event
  Horizon). A theorem whose statement requires types the axiom system does not grant
  is not derived from the system; it extends it silently.
- Suggested fix: add information (and the act-on relation, or an admission-indexed
  licence relation) to "the words", or reduce information to parts+records explicitly.

### A2-F03 · high — T37's cited derivation has a missing bridge

- Where: 01 T37 ("Derived from: the words (contains, admission), Axiom 1, T0").
- What: from "no admission names i" and T0 ("no evidence, no trust; no trust, no act")
  nothing follows about trust-for-acts-on-i: T0 only gives trust ⇒ evidence. To
  conclude "no trust for any act on i" one needs the converse direction for
  information acts — that only an admission produces the evidence/licence grounding
  such trust. The words' admission definition ("so that parts trusted for that class
  may act on it") gestures at this but states it as purpose, not as law. I had to add
  a marked BRIDGE axiom: `Bridge_admission_gates_info` (every act on information
  requires an admission naming it).
- Why it matters: T37 is the corpus's modelled example of "containment should follow,
  not be defined" (the owner's quoted words). As cited, it does not follow; with the
  bridge it does — so the bridge should be owned, not implicit.
- Suggested fix: either promote the bridge into Axiom 2 ("evidence licensing an act on
  an item requires an admission naming the item") or list it in the assumption
  register; then T37's `Derived from` line becomes honest.

### A2-F04 · high — Axiom 1 leans on three undefined modifiers, and "the two" is ambiguous

- Where: 01 Axiom 1.
- What: "full reach over the act" and "gated only by the other" are never defined
  (AMB2-03); and the axiom's two halves read "two independent witnesses" (existential)
  and "what **they** do not both trust does not act" (canonical pair). On the
  existential reading the negative half has no fixed referent and the gate is nearly
  unfalsifiable (any refusal can be attributed to "the" pair not both trusting); on
  the canonical reading the axiom is crisp. My file uses canonical halves for the
  fail-closed direction (AMB2-04).
- Why it matters: every claim in the corpus routes through Axiom 1; its strength is
  the system's strength. T29 ("a shared cause turns a layer into one witness") only
  makes sense on the canonical reading.
- Suggested fix: state Axiom 1 with the layer's halves as the gate (as `GateAllows`
  does) and keep independence/reach as well-formedness obligations of the minting
  (T29 then becomes the clause that revokes well-formedness).

### A2-F05 · medium — T5's M1 is half arithmetic definition, half governance

- Where: 01 T5.
- What: "more than half of all pinned seats" is the unique threshold with the split-brain
  and survives-one-refusal properties, and both properties are elementary pigeonhole
  facts about counts (`Claim_T5_M1_never_split`, `..._survives_one_refusal`,
  `..._minimal`). The theorem's mathematical content is trivial; its content is the
  *decision* to count from the pinned set in the record, never from who answers —
  which is the part my statement cannot capture (it would need a model of "the
  record's pinned set" vs "who answers").
- Suggested fix: split T5 into (a) the arithmetic lemma (provable, Mathlib-free) and
  (b) the pinned-set rule as an axiom about which seat set is authoritative.

### A2-F06 · medium — T3's seats and nodes are untyped, and its key premise is not in formal shape

- Where: 01 T3, T3a; T5; G0's assumption-register sentence.
- What: "at least two seats per side, at least one onboarded stand-in per seat, a
  cluster of at least three nodes per system half" — `Seat` and `Node` have no types,
  no relation to `Part`/`Witness`/`Person`, and the load-bearing premise "a half
  answers by a majority of its nodes" is tagged as premise but never given a
  statement that could be discharged or assumed formally.
- Why it matters: continuity (T3) is one of the few claims that would justify real
  deployment numbers; as it stands its floors are asserted over sorts that do not
  exist.
- Suggested fix: type seats and nodes (e.g. seats ⊆ White Key holdings; nodes ⊆ parts
  of a half), and write the majority premise as a first-class named assumption.

### A2-F07 · medium — "loosening" is defined counterfactually and cannot be used as a definition

- Where: 01 "The words" (tightening/loosening); T24, T26, T27, T29, T3d.
- What: "a loosening is anything that lets an act happen that would not have happened
  before" quantifies over a counterfactual world. No semantics for "would have" is
  given, so every theorem that restricts loosenings is unstatable literally. My file
  replaces it with an opaque classifier `Loosening : Act → Prop` (AMB2-10), which is
  weaker: it asserts nothing about which acts are loosenings.
- Suggested fix: define loosenings syntactically (a per-layer list of act kinds: lift,
  unlock, override, promote, admit, release — T24 already enumerates them) or
  model worlds explicitly.

### A2-F08 · medium — T6 carries an acknowledged but unscoped exception to Axiom 2

- Where: 01 T6 and its Decision D6 parenthetical.
- What: T6's headline says a majority may stop a stand-in takeover "only by revoking
  the stand-in on evidence against it (T2)", while the parenthetical records that D6
  lets a majority block without evidence until a timer runs out. These are different
  rules; the exception's scope (which majorities, which timers, which seats) is
  nowhere delimited.
- Why it matters: A2-F08-shaped exceptions are exactly how "silence never isolates"
  (T2, Q6) erodes. My `Claim_T6_standins` states only the unconditional takeover
  half; the blocking rule is not statable without the missing scope.
- Suggested fix: write the D6 rule as its own named clause with its timer and scope,
  or drop it.

### A2-F09 · medium — T32/T33's quantities live outside this corpus, so T33 is not statable from DMP alone

- Where: 01 T32 ("The formulas and their parameters are Gravity's constant … The
  parameters are configuration (T4)"); T33.
- What: depth, mass, freshness (a "share of validity"), shortfall, and the potential
  have no definitions in DMP; they are deferred to an external file in another
  repository. `Claim_T33_same_recipe_same_field` — the VIBE test, one of the corpus's
  most concrete verifiable promises — therefore cannot be stated from the DMP text
  alone; my statement carries placeholder functions (`FreshnessOf`, `DepthOf`,
  `MassOf`, `ShortfallOf`) and no arithmetic.
- Why it matters: a claimed end-theorem whose statement depends on another repo's
  constant is not part of this axiom system; DMP's own "DMP stands singular" rule
  (00 "The root chain") argues the formulas should at least be typed here.
- Suggested fix: give the field quantities types and units in DMP (even without the
  constants), or re-scope T33 to the isomorphism claim only.

### A2-F10 · low — I3 is true by typing; its content is interface closure

- Where: 04 "The refusal log"; "Invariants for proving" I3.
- What: the refusal log's interface admits only enumerations, so "the log carries no
  content" is a tautology about the interface's type — my `Claim_I3_log_content_free`
  is literally `s = s`, kept in the file to demonstrate the vacuity. The real claim is
  that no other write path to the log exists (an implementation/module-closure
  property, like A2-F01's "no other way through").
- Suggested fix: state I3 as "every write to the log state goes through
  `LogAppend(entry : Sum RefusalReason IMKind)`" once a module system is in scope.

### A2-F11 · medium — C2.L3's "refused at any later or earlier time" is not statable as worded

- Where: 01 C2.L3; 04 "The verify rules" rule 16.
- What: a verifier cannot compare a present decision against "the memory the first
  answer left" at an *earlier* time; time-symmetric refusal is meaningless. The
  intended content — windowed replay protection plus rule-16 completeness — is
  statable and I stated it (`Claim_C2_L3_no_replay`, `Claim_rule16_complete`), but the
  law's sentence needs repair.
- Suggested fix: reword C2.L3 to: "after a message is verified, the same message is
  refused for as long as its (subject key id, message id) is remembered, and rule 16's
  forgetting window is covered by rule 12."

### A2-F12 · high — "DMP-complete" quantifies over the constitution's own theorems with no satisfaction relation

- Where: 01 "The words" (DMP-complete); G0 "Mint prep"; 00 "The root chain".
- What: the definition requires that "every axiom and every theorem of this
  constitution hold for all of it, and both chains prove it". Stating this needs (a) a
  universe of the constitution's claims (I model it as `ClaimId`), (b) a satisfaction
  relation `Claim ⊗ Configuration → Prop` ("holds for all of the configuration"),
  which the corpus never defines, and (c) a proof relation for both chains over that
  satisfaction. My `DMPComplete` def keeps only the two halves that are statable
  (no unproven part; every dependency pinned inside) and drops the satisfaction
  quantifier — meaning my `Claim_G0_mint_prep` is weaker than the text's rule.
- Why it matters: DMP-completeness is the gate for minting — the most consequential
  single decision the system makes. An undefined predicate at the gate is the largest
  single gap this round found.
- Suggested fix: define DMP-completeness inductively: a configuration is complete when
  each axiom/theorem has a configuration-indexed witness generated by the proof
  chains; or re-scope the words to the checkable half (unproven-part-free +
  pinned-dependencies) and say so.

### A2-F13 · low — T20's "stricter answer is 'no now'" invents a verdict-valued time

- Where: 01 T20.
- What: time itself becomes a gated quantity with a refusal verdict; my formalisation
  invents `NowOK : Time → Prop` and folds "nothing with a validity verifies" into the
  claim. Harmless, but the text's phrase "the stricter answer is 'no now'" hides that
  this is a third verdict kind beyond allow/refuse.
- Suggested fix: state T20 as: if the authorities disagree beyond tolerance, no
  standing is valid at that time (which is what my claim says) and drop the
  "stricter" framing for time.

### A2-F14 · medium — Axiom 4's positive direction is teleological; only its negative clause and restoration duty are statable

- Where: 01 Axiom 4.
- What: "works towards the trust the Duality declared" and "what the boundary claims
  and lacks, it builds" are goal-directed; no formal notion of progress or attempt is
  given. The statable parts are the restoration duty (`A4_restore`), the no-lowering
  clause (`A4_no_lowering`), and — via T32 — the potential-monotonicity
  (`Claim_T32_potential`), which is where the direction's operational content actually
  lives.
- Suggested fix: restate Axiom 4 as two machine-checkable clauses (restoration duty +
  potential-never-raised-by-own-acts) and one reporting duty, and let the prose
  motivate them.

### A2-F15 · low — the assumption register is the real axiom set and is not machine-readable

- Where: 01 G0 (last paragraph); 04 "Invariants for proving" (assumptions A14, A17
  numbered only in prose); 06 "Supernova classes" IIb (assumption audit).
- What: G0 lists what no chain reaches (the DMP text itself, the mapping of code to
  acts, the door's code, the failure-class list, the time authorities, the provers'
  logic, the shared machines). These are assumptions of every claim in my file, but
  they exist only as prose in three places, with ad-hoc numbering (A14, A17 appear in
  chapter 04 only).
- Why it matters: every `Claim_*` in my file is silently conditional on this register;
  a formal system that says "the DMP text itself" is an assumption cannot state its
  own well-formedness.
- Suggested fix: give the register a stable, numbered, machine-readable home in DMP
  (the text already gestures at `CM.MilkyWay/docs/supernova/assumptions.md`) and
  reference the numbers from each section's `Derived from:` line.

### A2-F16 · medium — "trust only tightens down the layers" is real but homeless

- Where: mission slogan; scattered in 01 T1, T32 ("nothing is fresher than its
  grantor"), C18 ("no more rights than the locked system had"), T-P ("no more rights
  than the locked system had"), T35 ("re-shown, never carried over").
- What: the monotonicity claim I formalised (`Claim_trust_tightens_downward`: a
  delegate trusted for an act at t implies its grantor was trusted by both halves at
  grant time) follows the spirit of all of these, but no section of the corpus states
  it, and the concepts it needs — grant, grant graph, grantor — are formally
  undefined in the constitution (T32 defers the graph to "the grant graph the record
  holds"; no `GrantsAt` relation exists).
- Why it matters: this is the slogan outsiders will quote; if it is a theorem, it
  needs a home and typed grants; if it is only a summary of four weaker rules, the
  slogan overclaims.
- Suggested fix: add `GrantsAt` (or "derives through", which T32 uses informally) to
  the words and either state the monotonicity as a theorem with a real derivation or
  retire the slogan to the four named rules.

## Questions for the owner

1. **Axiom 1, "the two":** is the gate always exactly the layer's two designated
   halves (my chosen reading), or may any independent, full-reach pair serve? This
   decides whether substitute witnesses can act and how T29's one-witness state bites.
2. **Is information a part?** If yes, the containment block simplifies; if no, "the
   words" need `Info` and an act-on relation added (A2-F02). Relatedly: should the
   admission bridge (no act on an item without an admission naming it — A2-F03) be an
   axiom, and if so, of Axiom 1, Axiom 2, or standalone?
3. **DMP-complete at the minting gate (A2-F12):** do you want the satisfaction
   quantifier ("every theorem holds for all of it") made formal — and if so, must it
   be decidable by the chains, or is the checkable half (no unproven part, all
   dependencies pinned inside) the whole of the gate?
4. **Grant monotonicity (A2-F16):** should "a delegate never holds more than its
   grantor" be promoted to a theorem with `GrantsAt` in the words, or is the slogan a
   summary, not a claim?
5. **T5's M2:** confirm the reading that only sided acts are M2-gated ("an act without
   a side was not witnessed by that side"), i.e. M2 does not apply to side-less acts.
6. **C2.L3 wording (A2-F11):** confirm the intended rule is windowed replay
   protection (refusal while remembered; forgetting covered by rule 12), so the
   "earlier time" phrase can be fixed.
7. **T6/D6 (A2-F08):** is the no-evidence blocking window still wanted after the Axiom
   2 distillation, and if so, what are its timer and scope?
8. **Assumption register (A2-F15):** should it become a numbered, machine-readable
   section of the constitution, referenced by `Derived from:` lines?

*End of A2 round 1 report.*
