# A1-round1 — blind formalisation of DMP 0.9.6 (axiom-first, round 1)

Verifier: A1 (independent, blind — did not write DMP, no stake in it being right).
Date of reading: 2026-10-26 (fresh clock reading taken 2026-10-26 21:24:17Z before this
report was assembled; corpus state read in the same session).

## Method and claim discipline

- Sources: only the files under `src/dmp/` (00, 01, 02, 04, 05, 06, 10, 11, 14, CHARTER,
  README, SETUP, VERSION, tools/check-setup.sh, tools/scrub-scan.sh). **Not read**, per the
  blind protocol: anything under `src/gravity/`, `src/im/`, or other verifiers' work in
  `out/` and `work/`. No Lean toolchain was installed (walls forbid installs), so the Lean
  file was **not machine-checked**; it is statement-only by design.
- Claim tags: every substantive claim below is **[argued]** (reasoned from the cited
  file + section) unless marked **[guess]**. Nothing here is **[proven]**: a statement-only
  file proves nothing by construction. The one positive *check* reported (F-checks below)
  is a text inspection, tagged [argued].
- Method (axiom-first): first the corpus's own foundational layer — "the words",
  Axioms 1–4, G0, C∞'s meta-rule — formalised as `axiom`/`def`/`inductive` declarations;
  then, working forward, every theorem TYPE the text claims follows, as `def … : Prop`
  with no proof body. No `sorry` and no proof placeholder anywhere: the file stands alone
  and claims nothing proven.
- Where the text admits several readings, the most literal one was formalised and the
  choice recorded in the ambiguity register (AMB1-01…16).

## Corpus identity [argued]

DMP 0.9.6 (`VERSION`). Chapter table per README.md. The constitution's own account of its
structure [01, "How this chapter is built"]: "the words", then **three bounds** (Axiom 1
dual gate, Axiom 2 evidence, Axiom 3 record) and **one direction** (Axiom 4 restoration),
then **the ground G0** (the minting, "stated, not derived"); everything after that claimed
as theorem (T-sections) or kept rule (C-sections); C∞ stands last as the meta-rule
("Counts": 3 bounds, 1 direction, 1 ground, 1 meta-rule). Retired/absent numbers per the
text: C8, C11 (moved to chapters 10/14), C20, C26 (never stable), C23 = C∞; T7–T18 absent
without explanation (finding A1-F12).

## Inventory table

Lean names resolve in namespace `DMP` of `DMP_A1.lean`. "Words/scaffold" rows are
declarations of vocabulary (types and relations), which carry no assertive content.

| Corpus item | Lean declaration(s) | Source location |
|---|---|---|
| The words (undefined vocabulary + defined words) | §W: `Part`, `Act`, `Time`, `Evidence`, `IsWitness`, `T`, `ActsIn`, `Halves`, `DoT`, `Independent`, `Standing`, `Contains`, `InsideP`, `IsDoor`, `IsSurface`, `Tightening`, `Loosening`, et al. | 01, "The words" |
| Load-bearing but undeclared primitives (finding A1-F08) | §W: `Information`, `Layer`, `Record`, `Value`, `Boundary`, `Configuration`, `InfoClass`, `FailureClass`, `Grant`, `Key` | 01 passim |
| DMP-complete (word) | `DmpComplete` (def) over `AxiomsHoldIn`, `BothChainsProve`, `DepsPinnedInside`, `SelfHealing` | 01, "The words" (DMP-complete) |
| Axiom 1 · The dual gate | `AX1_only_while_both_trust`, `AX1_one_answer`, `AX1_stricter_stands`, `AX1_disagreement_holds_dependents`, `AX1_no_side_doors` | 01, "Axiom 1 · The dual gate" |
| Axiom 2 · Evidence | `AX2_self_verified_evidence`, `AX2_grounding_shape`, `AX2_withdrawal_on_evidence`, `AX2_validity_bound` | 01, "Axiom 2 · Evidence" |
| Axiom 3 · The record | `AX3_record_exists`, `AX3_readers`, `AX3_retention_two_witnesses` | 01, "Axiom 3 · The record" |
| Axiom 4 · The direction | `AX4_direction` | 01, "Axiom 4 · The direction" |
| G0 · The ground | `G0_owner_stands_for_both`, `G0_standin_semantics`, `G0_ratification`, `G0_pressed`, `G0_half_loss`, `G0_minting_only_complete`, `G0_roots_never_minted` | 01, "G0 · The ground" |
| T0 · Nothing is trusted by default | `THM_T0` | 01, "T0" |
| T37 · Collapse | `THM_T37_collapse` | 01, "T37" |
| T38 · Every information layer has its own Duality | `THM_T38_info_layer_dot` | 01, "T38" |
| T1 · Trust is bounded | `THM_T1_bounded` | 01, "T1" |
| T2 · Standing follows evidence, never silence | `THM_T2_standing_follows_evidence` | 01, "T2" |
| T3 · Continuity | `THM_T3_continuity` | 01, "T3" |
| T3a · The floors | `THM_T3a_floors` | 01, "T3a" |
| T3b · No lockout | `THM_T3b_no_lockout` | 01, "T3b" |
| T3c · Nothing gates contacting the Duality | `THM_T3c_contact` | 01, "T3c" |
| T3d · Safety before liveness | `THM_T3d_safety_before_liveness` | 01, "T3d" |
| T4 · Trust configuration belongs to the Duality | `THM_T4_config_owned_by_duality` | 01, "T4" |
| T5 · Majority of trust (M1, M2) | `THM_T5_majority`, `M1`, `M2` (defs) | 01, "T5" |
| T6 · Stand-ins take over | `THM_T6_standins` | 01, "T6" |
| T19 · The data boundary | `THM_T19_data_boundary` | 01, "T19" |
| T20 · Time is a witness like any other | `THM_T20_time_witness` | 01, "T20" |
| T21 · Observability without leakage | `THM_T21_observability` | 01, "T21" |
| T22 · The axioms apply to themselves | `THM_T22_axioms_self_apply` | 01, "T22" |
| T24 · Tighten down on one witness, loosen with two | `THM_T24_tighten_loosen` | 01, "T24" |
| T24b · Lockstep | `THM_T24b_lockstep` | 01, "T24b" |
| T24c · Self-correction | `THM_T24c_self_correction` | 01, "T24c" |
| T28 · Enforcement is an act | `THM_T28_enforcement_act` | 01, "T28" |
| T29 · A shared cause turns a layer into one witness | `THM_T29_shared_cause` | 01, "T29" |
| T30 · "Wherever technically possible" is a record | `THM_T30_exceptions` | 01, "T30" |
| T23 · The horizon | `THM_T23_horizon` | 01, "T23" |
| T25 · Thin surfaces | `THM_T25_thin_surfaces` | 01, "T25" |
| T26 · Retention | `THM_T26_retention` | 01, "T26" |
| T27 · Containment | `THM_T27_containment` | 01, "T27" |
| T31 · The trap, and the floor | `THM_T31_trap_floor` | 01, "T31" |
| T34 · Three roads to the floor | `THM_T34_three_roads` | 01, "T34" |
| T32 · The trust field (VIBE) | `THM_T32_vibe`, `Vibe`, `Potential`, `Shortfall`, `HasDepth` (defs) | 01, "T32" |
| T33 · The VIBE test | `THM_T33_vibe_test` | 01, "T33" |
| T-P · The pressing | `THM_TP_pressing` | 01, "T-P" |
| T35 · Compliance is assembled, never claimed | `THM_T35_compliance_assembled` | 01, "T35" |
| T36 · The horizon is the one boundary | `THM_T36_horizon_boundary` | 01, "T36" |
| C1 · One door | `THM_C1_one_door` | 01, "C1" |
| C2 · Every message verifies itself (Laws L1–L4b) | `THM_C2_L1_verified_authorised`, `THM_C2_L2_one_answer`, `THM_C2_L3_no_replay`, `THM_C2_L3b_full_memory`, `THM_C2_L4_permission_table` | 01, "C2" (Law block) |
| C3 · Every value carries its class | `THM_C3_values_carry_class` | 01, "C3" |
| C4 · Contracts change at stable promotions only | `THM_C4_contracts` | 01, "C4" |
| C5 · Financial data freezes at production | `THM_C5_financial_freeze` | 01, "C5" |
| C6 · The gates and the authority grant | `THM_C6_authority_grant` | 01, "C6" (grant block) |
| C7 · One repository deploys every part | `THM_C7_one_repository` | 01, "C7" |
| C9 · Open source: roles, not values | `THM_C9_roles_not_values` | 01, "C9" |
| C10 · The defensive charter | `THM_C10_charter` | 01, "C10"; CHARTER.md |
| C12 · Information is tiered | `THM_C12_tiers` | 01, "C12" |
| C13 · The nearest tier is asked first | `THM_C13_nearest_tier` | 01, "C13" |
| C14 · Every path is combined | `THM_C14_combine_paths` | 01, "C14" |
| C15 · A write first reads what it changes | `THM_C15_write_reads_first` | 01, "C15" |
| C16 · Company data reaches general testing only with its proof | `THM_C16_data_gate` | 01, "C16" |
| C17 · The first level belongs to The Administrator and LHC | `THM_C17_admin_lhc` | 01, "C17" |
| C18 · IM stays backwards compatible once locked | `THM_C18_im_backcompat` | 01, "C18" |
| C19 · A request is served only when it is secure and meant | `THM_C19_two_signatures` | 01, "C19" |
| C21 · Look it up, don't guess | `THM_C21_look_up` | 01, "C21" |
| C22 · Prove forward and back: two chains | `THM_C22_two_chains` | 01, "C22" |
| C24 · Stable company-wide needs a survived cold start | `THM_C24_cold_start` | 01, "C24"; 11, "Stable rollout" |
| C25 · Every deployment obeys DMP | `THM_C25_deployments` | 01, "C25" |
| C∞ · The stopgap (ejection clause; meta-rule → report) | `THM_Cinf_ejection` | 01, "C∞" |
| IM verify rules 1–16, order, fail closed | `IM_verified_iff_no_rule_fails`, `IM_first_failure_reason`, `IM_no_other_accept`, `InRuleRange`, `RuleFails`, `ReasonOf`, `Reason` (28 constructors) | 04, "The verify rules" |
| IM refusal log: counts, never content | `THM_IM_refusal_log_no_content` | 04, "The refusal log" |
| IM invariants I1–I6 | I1 = `THM_C2_L1…`; `THM_IM_I2`, `THM_IM_I4`, `THM_IM_I5_quiet`, `THM_IM_I6_canonical` | 04, "Invariants for proving" |
| IM: a version is IM only with its proof; one version, no negotiation | `THM_IM_version_discipline` | 04, "What IM is (the axiomatic chain)" (draft) |
| IM v1: depth bounded on the wire | `THM_IM_depth_bounded` | 04, bullet 4 (draft) |
| IM v1: two chains, intersection of permissions, DualTrust | `THM_IM_v1_dual_trust` | 04, "IM version 1" (proposal) |
| IM v1: orders — isolate 1 sig, lift/override 2, silence never isolates, no timeout | `THM_IM_v1_orders` | 04, "Orders and the White Key" |
| MW: only verified messages reach consumers | `THM_MW_verified_only` | 05, "The verifier" |
| MW: verify rules sit only in Milky Way | `THM_MW_only_verifier` | 05, "The parts and where they live" |
| MW: TLS and IM identities are one | `THM_MW_identity_binding` | 05, "Transport encryption" |
| BH: no public port before IIb passed | `THM_BH_port_IIb` | 06, "Where the class gates"; 01 C2 |
| BH: no lemma, not proven safe | `THM_BH_lemma_ledger` | 06, "Lemmas and the lemma ledger" |
| BH: class raised never lowered, strictest wins | `THM_BH_class_monotone` | 06, "Supernova classes" |
| BH: GRB scope file, flag secrecy, escape ring, reached flag blocks | `THM_BH_grb` | 06, "GRB runs and the scope file" |
| CS: run counts only on unchanged surface; pass line P1∧P2∧P3 | `THM_CS_pass_line` | 11, "The cold-start surface…", "The pass line" |
| PROC: no tacit approval (from Axiom 2; draft) | `THM_PROC_no_tacit_approval` | 14, "Rules need the expert" |
| Root chain: one direction, nothing points back up | `THM_ROOT_chain` | 00, "The root chain" |
| Pin mismatch refused by the gate | `THM_ROOT_pin` | 00, "The root chain" |
| Version rule; laws file changes only with its section | `THM_ROOT_version` | 00, "The version"; 00, "The marks" |
| `none yet` printed by the runner on every run | `THM_MARKS_print_unenforced` | 00, "The marks" |
| Dwarf galaxies | `THM_DWARF` | 00, "Who maintains it" |
| Tree discipline (namespace = folder; unlisted refused) | `THM_TREE_discipline` | 02, "The tree" |
| SETUP check fails exactly on the five listed conditions | `THM_SETUP_check` | SETUP.md "The check"; tools/check-setup.sh |
| Scrub scan fails exactly on pattern hits outside the allow list | `THM_SETUP_scrub` | tools/scrub-scan.sh |

Counts: **21 asserted axiom declarations** (1 structural + 13 Axiom-clauses + 7 G0),
**86 theorem statements** (`def THM_* : Prop`), 21 helper definitions, 8 inductives,
≈530 vocabulary declarations total (scaffold types/relations; several names per line).
C∞'s meta-rule (stopgap catches toward zero, axioms toward fewer, preference order
theorem-merge-new-axiom) is a rule about the corpus, not a proposition about CMOS; it is
recorded here, not in the Lean file.

## Checks run against the text [argued]

- Version rule: "A section cannot be stable since a version newer than VERSION" — the
  maximum `stable since` in the corpus is 0.9.6 and VERSION is 0.9.6: **holds**, no
  violation found (01 passim; VERSION).
- No `sorry`, no proof body, no `theorem` declaration in the Lean file (grep-verified);
  all 86 theorem statements are `def … : Prop`.

---

# Embedded Lean file: `work/a1r1/DMP_A1.lean`

(Embedding is byte-identical to the delivered file; it was **not** machine-checked — no
Lean toolchain was installed, per the walls. The file is statement-only: axioms as
`axiom`, theorem claims as `def … : Prop`.)

```lean
/-!
# DMP_A1.lean — blind axiom-first formalisation of DMP 0.9.6 (verifier A1, round 1)

Statement-only Lean 4. Sources: the DMP text alone (`src/dmp/`: 00-preamble.md,
01-constitution.md, 02-names-and-hierarchy.md, 04-im.md, 05-milky-way.md,
06-black-hole.md, 10-code-quality.md, 11-test-design.md, 14-process.md, CHARTER.md,
README.md, SETUP.md, VERSION, tools/*). Gravity's and IM's Lean trees were NOT
read (blind formalisation).

Conventions
* The corpus's undefined vocabulary ("the words") and every relation the text
  uses without defining are declared as `axiom` constants, tagged `-- W` or
  `-- scaffold`. Scaffolding is vocabulary the formaliser added so the text
  becomes sayable; it carries no assertive content of its own.
* The corpus's foundational assertions (Axioms 1-4, G0, plus the two
  structural axioms `T_first_is_witness` and `AX1`'s clauses) are `axiom`
  propositions.
* Everything the corpus claims *follows* (the T- and C-sections, the chapter
  04/05/06 rules, the preamble rules) is stated as `def Name : Prop := ...` —
  a theorem TYPE, no proof body. The file contains no proof of anything and
  needs none: it stands alone. No proof placeholder of any kind is used.
* Every declaration carries a source tag [file, section] in its docstring.
-/

namespace DMP

/- ================================================================
   §W · The words  [01-constitution.md, "The words"]
   "Undefined, like point and line." Declared, not defined.
   "a definition forbids nothing" — definitions only name.
   ================================================================ -/

-- W1-W4: words the text declares undefined.
axiom Part     : Type   -- W1 person, body, agent, system, node, key, chain, rule, deployment
axiom Act      : Type   -- W2 message, read, write, grant, merge, promotion, deployment, decision, answer, seat taken
axiom Time     : Type   -- W3 "time"
axiom Evidence : Type   -- W4 what a witness verifies
axiom IsWitness : Part → Prop   -- "a witness is a part that decides trust for others"

-- Load-bearing words the text uses but does NOT declare (finding A1-F08):
axiom Information   : Type  -- used from T37 on ("piece of information")
axiom Layer         : Type  -- "a place where trust is decided"
axiom Record        : Type  -- "evidence that outlives the act it is about"
axiom Value         : Type  -- T1 "a value a part is not trusted for"; C3
axiom Boundary      : Type  -- Axiom 4 "the declared boundary"; the words "contains"
axiom Configuration : Type  -- "a configuration of CM, interconnected through IM"
axiom InfoClass     : Type  -- C3 class / identification axis of a value
axiom FailureClass  : Type  -- the words "independent": host, key, author, engine, image, person, time source, ...
axiom Grant         : Type  -- "Admission is a grant: a record ..."
axiom Standing      : Type  -- "trust held across time"
axiom Key           : Type  -- keys, roots, White Keys (T19, T27, 04, 11)
axiom MsgIdOf       : Type  -- message ids (04 replay rule)            -- scaffold
axiom LogEntry      : Type  -- refusal-log entries (04)                -- scaffold
axiom RootRepo      : Type  -- DMP, Gravity, IM, CM (00 "The root chain")
axiom Component     : Type  -- a component under a Supernova class (06)-- scaffold
axiom Scenario      : Type  -- a cold-start scenario (11)               -- scaffold
axiom Finding       : Type  -- a security finding (C∞, T36)             -- scaffold

-- Core trust relation: T w p a t — witness w trusts part p for act a at time t. [the words]
axiom T : Part → Part → Act → Time → Prop
axiom T_first_is_witness : ∀ w p a t, T w p a t → IsWitness w

-- Acts, layers, actors. [the words; Axiom 1 "This holds at every layer"] (scaffold for the maps)
axiom ActsIn   : Act → Time → Prop     -- the act happens (is done/answered) in CMOS
axiom ActorOf  : Act → Part            -- the part that does the act
axiom LayerOf  : Act → Layer           -- the layer where the act's trust is decided
axiom LayerOfP : Part → Layer          -- the layer a part sits at
axiom ActOn    : Act → Information → Prop   -- the act is an act on that information [T37, T31]

-- Evidence verified by the witness itself at the point of use. [Axiom 2]
axiom VerifiedBy : Part → Evidence → Time → Prop          -- w verified e itself, live, at use
axiom Grounds    : Evidence → Part → Act → Time → Prop    -- e is what grounds trust for that act
axiom DependsOnPart : Act → Part → Prop                   -- "wherever the act's trust depends on the part"
axiom IsLiveState    : Evidence → Part → Prop             -- from the live state of the part
axiom NotCarrierCheck : Evidence → Prop   -- only a carrier's check / earlier read / claim / memory / position

-- Layers and the Duality of Trust. [the words]
axiom Halves : Layer → Part × Part        -- the two witnesses of the layer
def Half1 (l : Layer) : Part := (Halves l).1
def Half2 (l : Layer) : Part := (Halves l).2
def DoT (l : Layer) : Prop := IsWitness (Half1 l) ∧ IsWitness (Half2 l)

-- Independence relative to the minting record's declared failure-class list. [the words]
axiom SharesFailureClass : Part → Part → FailureClass → Prop
axiom DeclaredClasses : Layer → List FailureClass          -- part of the minting record (T4)
def Independent (l : Layer) : Prop :=
  ∀ c ∈ DeclaredClasses l, ¬ SharesFailureClass (Half1 l) (Half2 l) c

-- Standings: trust held across time; "a standing is evidence with a validity". [the words, Axiom 2]
axiom stAbout    : Standing → Part      -- whose standing
axiom stFrom     : Standing → Part      -- the witness holding it
axiom stValid    : Standing → Time → Prop
axiom stValidity : Standing → Nat       -- scaffold: length of the validity
axiom Withdrawn  : Standing → Prop      -- an act against the standing
axiom Lapse      : Standing → Prop      -- validity ran out: a lapse, not an act
axiom EvidenceAgainstSt : Evidence → Standing → Prop
axiom SilenceWitness : Part → Time → Prop          -- a witness is silent
axiom Alarms         : Part → Standing → Time → Prop
axiom IsolationOf    : Part → Standing → Time → Prop   -- isolating on silence

-- Inside / doors / surfaces. [the words]
axiom InsideP   : Part → Time → Prop   -- inside: a standing for it from both witnesses is valid then
axiom IsDoor    : Part → Prop          -- a door is any point of use
axiom IsSurface : Part → Prop          -- receives from parts that hold none
axiom MeetsDoor : Part → Part → Prop   -- actor reaches door              -- scaffold
axiom RefusedAt : Part → Part → Act → Time → Prop  -- door refuses actor for act  -- scaffold
axiom Alive     : Part → Time → Prop   -- part has not been lost          -- scaffold

-- Records. [Axiom 3]
axiom Leaves      : Act → Record → Prop
axiom WrittenAtAct : Record → Act → Prop
axiom ActOf       : Record → Act
axiom Outlives    : Record → Act → Prop
axiom Reads       : Part → Record → Time → Prop
axiom SeesCounts  : Part → Record → Time → Prop
axiom SeesContent : Part → Record → Time → Prop
axiom ContentGrant : Part → Record → Prop
axiom WitnessOf   : Part → Act → Prop     -- a witness of that act
axiom DestroyedBy : Record → List Part → Prop
axiom RetentionLaw : Record → Prop        -- premise: external law (finding A1-F09)

-- Grants. [the words "Admission is a grant"; Axiom 3]
axiom GrantOf     : Grant → Record
axiom HasGrant    : Part → Grant → Time → Prop
axiom GrantScope  : Grant → InfoClass      -- the class the grant names
axiom GrantCovers : Grant → Information → Prop   -- scaffold

-- Admission, containment, information states. [the words; T27; T37]
axiom Admission : Type
axiom adInfo    : Admission → Information
axiom adClass   : Admission → InfoClass
axiom AdmissionValid : Admission → Time → Prop
axiom AdmittedAt     : Information → Time → Prop   -- information is inside while its admission is valid
axiom Contained      : Information → Prop          -- collapsed on the item (T37) / withdrawn (T27)
axiom PersonalData   : Information → Prop
axiom NonCMOS        : Information → Prop

-- "contains", the words' own definition, in the literal trust reading (AMB1-05).
axiom Beyond : Boundary → Part → Prop
def Contains (b : Boundary) (i : Information) : Prop :=
  ∀ (w p : Part) (a : Act) (t : Time), Beyond b p → ActOn a i → ¬ T w p a t

-- Tightening / loosening. [the words]
axiom Tightening : Act → Prop
axiom Loosening  : Act → Prop
axiom GatesOn    : Part → Part → Prop        -- witness gates part
axiom SignedByW  : Part → Act → Prop         -- the witness's signature is on the act's record
axiom LiftCondition   : Act → Information → Prop      -- what would lift a tightening (T24)
axiom IndependentOfLift : Information → Act → Prop    -- lift condition independent of the isolated thing

-- Values, classes, reach. [T1, C3]
axiom ClassOf : Value → InfoClass
axiom Reaches : Value → Part → Prop
axiom TrustedForClass : Part → InfoClass → Time → Prop   -- scaffold: admission + dual gate

-- Time, clocks. [T20]  -- scaffold
axiom timeLE : Time → Time → Prop
axiom after  : Time → Time
axiom TimeZero : Time
axiom TimeAuthority : Type
axiom ServersOf  : TimeAuthority → List Part
axiom ClockRead  : TimeAuthority → Time → Time
axiom DivergeBeyondTolerance : Time → Prop
axiom NoNow  : Time → Prop
axiom AuthorityIndependent : TimeAuthority → TimeAuthority → Prop

-- Inputs and answers of a gate. [Axiom 1]  -- scaffold
axiom Input : Type
axiom InputAct : Input → Act
inductive Answer | permit | refuse          -- binary; see AMB1-02
axiom HalfAnswer1 : Input → Answer
axiom HalfAnswer2 : Input → Answer
axiom AnswerTo    : Input → Answer → Prop
axiom DependsOn : Act → Act → Prop          -- "nothing that depends on the disagreement moves"

-- Shared vocabulary used by several sections (scaffold). [00, 01, 06, 14]
axiom tToAct : Time → Act            -- scaffold: a representative act of a time
axiom HolderOf : Information → Part  -- scaffold: the part answering for the information
axiom dmpRepo gravityRepo imRepo cmRepo : RootRepo
axiom configOfRepo : RootRepo → Configuration
axiom proofLayerOf : Configuration → Layer   -- the layer where an instance's DoT sits
axiom Crosses : Act → Boundary → Prop        -- T36 crossing of the horizon
axiom WithPermission : Act → Prop

/- ================================================================
   §G0v · G0 vocabulary (scaffold)  [01 "G0 · The ground"; 00 "Who maintains it"]
   -/

axiom MintingEvent : Type                     -- the ceremony that forms LHC and makes the White Keys
axiom LHCMinted   : Time → Prop               -- a first LHC exists
axiom OwnerWordsStandForBoth : Time → Prop    -- the un-minted regime
axiom OwnerTrusts : Part → Act → Time → Prop  -- the owner's own trust
axiom Ratified : MintingEvent → Act → Prop
axiom Revoked  : MintingEvent → Act → Prop
axiom IsPressed : Configuration → Prop
axiom IsMinted  : Configuration → Prop
axiom TracesTo  : Part → Part → Prop          -- witness traces to a person
axiom MarkedPressed : Configuration → Prop
axiom ActsOf        : Configuration → Act → Prop
axiom TrustedIn     : Configuration → Act → Time → Prop
axiom HalfLost   : Layer → Time → Prop
axiom RecoversBy : Layer → Act → Prop
axiom IsMintingAct : Act → Prop
axiom StartsMinting : Configuration → Prop
axiom PendingAct : Act → Prop                 -- act taken under `LHC pending`
axiom RootRepoNeverMintedFlag : RootRepo → Prop

/- ================================================================
   §D · DMP-complete  [01 "The words", "DMP-complete"]
   -/

/-- scaffold: "the axioms and theorems hold for all of the configuration".
    Conjoining every AX_/THM_ below here would make the definition
    self-referential inside the very file that states them; the corpus itself
    defers the checking to "both chains prove it" (C22). -/
axiom AxiomsHoldIn    : Configuration → Prop
axiom BothChainsProve : Configuration → Prop
axiom DepsPinnedInside : Configuration → Prop   -- every dependency inside the repository, pinned by hash
axiom SelfHealing      : Configuration → Prop   -- heals itself with no connection across its Event Horizon
axiom UnprovenPart     : Configuration → Part → Prop
def DmpComplete (c : Configuration) : Prop :=
  AxiomsHoldIn c ∧ BothChainsProve c ∧ DepsPinnedInside c ∧ SelfHealing c

/- ================================================================
   §A · The three bounds and one direction  [01-constitution.md]
   Asserted, not derived. G0 below is "stated, not derived".
   ================================================================ -/

/-- A1 · The dual gate (necessity clause): a part acts only while two independent
    witnesses, each with full reach over the act and gated only by the other,
    trust it for that act. "Full reach" and "gated only by the other" are folded
    into the two-halves hypothesis (AMB1-01). [01 "Axiom 1 · The dual gate"] -/
axiom AX1_only_while_both_trust :
  ∀ (a : Act) (t : Time),
    DoT (LayerOf a) → Independent (LayerOf a) → ActsIn a t →
      T (Half1 (LayerOf a)) (ActorOf a) a t ∧
      T (Half2 (LayerOf a)) (ActorOf a) a t

/-- A1 · "Every input gets exactly one answer." -/
axiom AX1_one_answer : ∀ i : Input, ∃! ans : Answer, AnswerTo i ans

/-- A1 · "Where the two disagree, the stricter answer stands."
    With the binary answer space of AMB1-02 the stricter answer is `refuse`. -/
axiom AX1_stricter_stands :
  ∀ i : Input, HalfAnswer1 i ≠ HalfAnswer2 i → AnswerTo i Answer.refuse

/-- A1 · "…and nothing that depends on the disagreement moves until they agree." -/
axiom AX1_disagreement_holds_dependents :
  ∀ (i : Input) (b : Act) (t : Time),
    HalfAnswer1 i ≠ HalfAnswer2 i → DependsOn b (InputAct i) → ¬ ActsIn b t

/-- A1 · "the gate has no other way through: no debug switch, no allow list, no
    trusted network" — outside the G0 stand-in regime, acting implies the joint
    trust of the two halves, whatever path the act took. -/
axiom AX1_no_side_doors :
  ∀ (a : Act) (t : Time),
    ¬ OwnerWordsStandForBoth t →
    DoT (LayerOf a) → Independent (LayerOf a) →
    ActsIn a t → BothTrust (LayerOf a) (ActorOf a) a t

/-- A2 · Evidence: a witness trusts only on evidence it verified itself at the
    point of use — from the live state of the part wherever the act's trust
    depends on the part, and from the current state of the record. [01 "Axiom 2"] -/
axiom AX2_self_verified_evidence :
  ∀ (w p : Part) (a : Act) (t : Time), T w p a t →
    ∃ e : Evidence, VerifiedBy w e t ∧ Grounds e w p a t

/-- A2 · the grounding evidence is live where the act depends on the part, and
    never a carrier's check, an earlier read, a claim, a memory or a position. -/
axiom AX2_grounding_shape :
  ∀ (w p : Part) (a : Act) (t : Time) (e : Evidence),
    Grounds e w p a t →
      (DependsOnPart a p → IsLiveState e p) ∧ ¬ NotCarrierCheck e

/-- A2 · "without evidence against a standing, the standing does not change."
    (The act clause — "without evidence for an act, the act does not happen" — is
    the contrapositive of AX2_self_verified_evidence read with AX1, i.e. T0.) -/
axiom AX2_withdrawal_on_evidence :
  ∀ s : Standing, Withdrawn s → ∃ e : Evidence, EvidenceAgainstSt e s

/-- A2 · "A standing is evidence with a validity, and no validity is longer than
    the time the minting accepts between a loss and its effect at the point of use." -/
axiom AcceptedLossLatency : Nat   -- configuration (T4)
axiom AX2_validity_bound : ∀ s : Standing, stValidity s ≤ AcceptedLossLatency

/-- A3 · The record: every grant, every use and every loss of trust leaves a
    record, written at the act, that outlives the act. [01 "Axiom 3"] -/
axiom TrustGrantAct : Act → Prop   -- scaffold: a is a grant of trust
axiom TrustUseAct   : Act → Prop   -- scaffold: a is a use of trust
axiom TrustLossAct  : Act → Prop   -- scaffold: a is a loss of trust
axiom AX3_record_exists :
  ∀ a : Act, TrustGrantAct a ∨ TrustUseAct a ∨ TrustLossAct a →
    ∃ r : Record, Leaves a r ∧ WrittenAtAct r a ∧ Outlives r a

/-- A3 · every witness of the act can read its record in full; any other reader
    sees the counts always and the content only by a grant. -/
axiom AX3_readers :
  ∀ (w : Part) (r : Record) (t : Time), Reads w r t →
    SeesCounts w r t ∧
    (WitnessOf w (ActOf r) → SeesContent w r t) ∧
    (¬ WitnessOf w (ActOf r) → (SeesContent w r t → ∃ g : Grant, ContentGrant w r))

/-- A3 · retention: kept as long as the law requires and no longer than it allows
    (the law is external — finding A1-F09); never destroyed by fewer than both
    witnesses of its layer. -/
axiom AX3_retention_two_witnesses :
  ∀ (r : Record) (ps : List Part), DestroyedBy r ps →
    Half1 (LayerOf (ActOf r)) ∈ ps ∧ Half2 (LayerOf (ActOf r)) ∈ ps

/-- A4 · The direction: every part inside the declared boundary works towards the
    trust the Duality declared for that boundary; restores what was lost without
    evidence against it, builds what the boundary claims and lacks, reports what
    it cannot restore; never lowers the bar of evidence, widens a grant or moves
    the boundary; the three bounds govern every step. [01 "Axiom 4 · The direction"] -/
axiom DeclaredBoundary : Boundary
axiom InsideB          : Boundary → Part → Time → Prop
axiom LostWithoutEvidenceAgainst : Part → Act → Time → Prop
axiom Restores : Part → Act → Time → Prop
axiom Builds   : Part → Act → Time → Prop
axiom Reports  : Part → Act → Time → Prop
axiom Restorable : Part → Act → Time → Prop
axiom ClaimsAndLacks : Boundary → Act → Time → Prop
axiom LowersEvidenceBar : Part → Time → Prop
axiom WidensGrant       : Part → Time → Prop
axiom MovesBoundary     : Part → Time → Prop
axiom BoundsForbid      : Act → Time → Prop
axiom AX4_direction :
  ∀ (p : Part) (t : Time), InsideB DeclaredBoundary p t →
    (∀ a, LostWithoutEvidenceAgainst p a t →
            (Restorable p a t → Restores p a t) ∧ (¬ Restorable p a t → Reports p a t)) ∧
    (∀ a, ClaimsAndLacks DeclaredBoundary a t → Builds p a t) ∧
    ¬ (LowersEvidenceBar p t ∨ WidensGrant p t ∨ MovesBoundary p t) ∧
    (∀ a, BoundsForbid a t → ¬ ActsIn a t)

/- ================================================================
   §G0 · The ground  [01-constitution.md, "G0 · The ground"]
   "It is stated, not derived."
   -/

/-- G0 · until the first LHC is minted the owner's words stand for both halves
    and the record says `LHC pending`; every gate that asks for the owner's words
    is G0, not a theorem. The biconditional reading is AMB1-03. -/
axiom G0_owner_stands_for_both :
  ∀ t : Time, ¬ LHCMinted t → OwnerWordsStandForBoth t

axiom G0_standin_semantics :
  ∀ (l : Layer) (p : Part) (a : Act) (t : Time), OwnerWordsStandForBoth t →
    (T (Half1 l) p a t ↔ OwnerTrusts p a t) ∧ (T (Half2 l) p a t ↔ OwnerTrusts p a t)

/-- G0 · the minting ratifies or revokes every act taken under `LHC pending`, by
    record class and hash range, never one by one. -/
axiom G0_ratification :
  ∀ (a : Act), PendingAct a → ∃ m : MintingEvent, Ratified m a ∨ Revoked m a

/-- G0 · a pressed instance: both of its witnesses trace to one person; it is
    marked pressed in every artefact it issues, and nothing it does is fully
    trusted by a minted instance. -/
axiom G0_pressed :
  ∀ c : Configuration, IsPressed c →
    (∃ person : Part, TracesTo (Half1 (proofLayerOf c)) person ∧
                      TracesTo (Half2 (proofLayerOf c)) person) ∧
    MarkedPressed c ∧
    ∀ (m : Configuration) (a : Act) (t : Time),
      IsMinted m → ActsOf c a → ¬ TrustedIn m a t

/-- G0 · the loss of a whole half is recovered only by a new minting. -/
axiom G0_half_loss :
  ∀ (l : Layer) (a : Act) (t : Time), HalfLost l t → RecoversBy l a → IsMintingAct a

/-- G0 · mint prep: a minting is tried only for a configuration that is provably
    DMP-complete; the root repositories are never minted. -/
axiom G0_minting_only_complete : ∀ c : Configuration, StartsMinting c → DmpComplete c
axiom G0_roots_never_minted : ∀ r : RootRepo, RootRepoNeverMintedFlag r

/- ================================================================
   §T · The theorems of the constitution, in the chapter's own order
   (the "order of proof", rule DMP-021). Types only — nothing here is proven.
   ================================================================ -/

def BothTrust (l : Layer) (p : Part) (a : Act) (t : Time) : Prop :=
  T (Half1 l) p a t ∧ T (Half2 l) p a t

/-- Fully trusted: what the dual gate says (C∞). At a layer whose halves are not
    independent, nothing is fully trusted. -/
def FullyTrusted (p : Part) (a : Act) (t : Time) : Prop :=
  DoT (LayerOf a) ∧ Independent (LayerOf a) ∧
  T (Half1 (LayerOf a)) p a t ∧ T (Half2 (LayerOf a)) p a t

/-- T0 · Nothing is trusted by default: no evidence, no trust; no trust, no act.
    [01 "T0"; Derived from: Axiom 2, Axiom 1] -/
def THM_T0 : Prop :=
  ∀ (p : Part) (a : Act) (t : Time),
    (¬ ∃ (w : Part) (e : Evidence), T w p a t ∧ VerifiedBy w e t ∧ Grounds e w p a t) →
      (¬ T (Half1 (LayerOf a)) p a t) ∧ (¬ ActsIn a t)

/-- T37 · Collapse: information that no admission names is contained at the item
    itself; admission is the only act that lifts the collapse.
    [01 "T37"; Derived from: the words, Axiom 1, T0] -/
def THM_T37_collapse : Prop :=
  (∀ i : Information, (¬ ∃ ad : Admission, adInfo ad = i) → Contained i) ∧
  (∀ (i : Information) (w p : Part) (a : Act) (t : Time),
      ActOn a i → T w p a t → ∃ ad : Admission, adInfo ad = i ∧ AdmissionValid ad t)

/-- T38 · Every information layer has its own Duality: organisational and factual
    halves; neither half alone admits, changes or releases; the two halves may be
    one part only under a higher-order DoT; at the top, the owner under G0.
    [01 "T38"; Derived from: the words, Axiom 1, G0] -/
axiom InfoLayer    : Information → Layer → Prop   -- l is the information layer of i's kind
axiom AdmissionAct : Act → Admission → Prop
axiom HigherLayer  : Layer → Layer → Prop
def THM_T38_info_layer_dot : Prop :=
  (∀ (i : Information) (l : Layer), InfoLayer i l → DoT l) ∧
  (∀ (l : Layer) (ad : Admission) (a : Act) (t : Time),
      InfoLayer (adInfo ad) l → AdmissionAct a ad → ActsIn a t →
        SignedByW (Half1 l) a ∧ SignedByW (Half2 l) a) ∧
  (∀ l : Layer, Half1 l = Half2 l → ∃ l' : Layer, HigherLayer l l' ∧ DoT l') ∧
  (∀ l : Layer, Half1 l = Half2 l → (∀ l' : Layer, ¬ HigherLayer l l') →
      OwnerWordsStandForBoth TimeZero)

/-- T1 · Trust is bounded: the acts a part may do are the intersection of what
    each witness trusts it for; a value a part is not trusted for never reaches it.
    [01 "T1"] -/
def THM_T1_bounded : Prop :=
  (∀ (p : Part) (a : Act) (t : Time),
      ActorOf a = p → ActsIn a t → BothTrust (LayerOf a) p a t) ∧
  (∀ (v : Value) (p : Part) (t : Time),
      ¬ TrustedForClass p (ClassOf v) t → ¬ Reaches v p)

/-- T2 · Standing follows evidence, never silence: withdrawn only on evidence
    against it; a lapse is not an act against it; silence alarms, never isolates.
    [01 "T2"; Derived from: Axiom 2] -/
def THM_T2_standing_follows_evidence : Prop :=
  (∀ s : Standing, Withdrawn s → ∃ e : Evidence, EvidenceAgainstSt e s) ∧
  (∀ s : Standing, Lapse s → ¬ Withdrawn s) ∧
  (∀ (w : Part) (s : Standing) (t : Time),
      SilenceWitness w t → Alarms w s t ∧ ¬ IsolationOf w s t)

/-- T3 · Continuity: each half of every pair outlives the loss of any single part
    (the half as an institution — seats and stand-ins — even when the lost person
    is of that half), and neither half can be cut off from its layer.
    [01 "T3"; Derived from: Axioms 1-4; premise: a half answers by majority] -/
axiom SingleLoss : Part → Time → Prop
def THM_T3_continuity : Prop :=
  ∀ (l : Layer) (p : Part) (t t' : Time),
    DoT l → SingleLoss p t → timeLE t t' →
      Alive (Half1 l) t' ∧ Alive (Half2 l) t'

/-- T3a · The floors: at least two seats per side, at least one onboarded stand-in
    per seat, a cluster of at least three nodes per system half (a half answers by
    a majority of its nodes). Numbers above a floor are configuration. [01 "T3a"] -/
axiom SeatsPerSide : Part → Time → Nat          -- scaffold: seats of that side (the argument is a half)
axiom OnboardedStandInFor : Part → Part → Prop  -- stand-in for a seat-holder
axiom NodesOf : Part → List Part
def THM_T3a_floors : Prop :=
  ∀ (l : Layer) (t : Time),
    SeatsPerSide (Half1 l) t ≥ 2 ∧ SeatsPerSide (Half2 l) t ≥ 2 ∧
    (∀ h : Part, h = Half1 l ∨ h = Half2 l → ∃ si : Part, OnboardedStandInFor si h) ∧
    (NodesOf (Half1 l)).length ≥ 3 ∧ (NodesOf (Half2 l)).length ≥ 3

/-- T3b · No lockout: a route by which The Administrator reaches a channel is part
    of that half's reach; removing the last route for an action cuts a half off.
    [01 "T3b"] -/
axiom Route   : Part → Part → Part → Prop   -- scaffold: who can reach the channel for the action
axiom HalfReach : Part → Part → Part → Part → Prop
def THM_T3b_no_lockout : Prop :=
  ∀ (h admin channel action : Part),
    HalfReach h admin channel action → ∃ r : Part, Route r channel action

/-- T3c · Nothing gates contacting the Duality: at the minting every part receives
    the standing to address a record to both witnesses; a contact carries no
    authority; an isolated part keeps it. [01 "T3c"] -/
axiom ContactAct : Act → Prop
axiom Addresses  : Act → Part → Prop
axiom AuthorityCarrying : Act → Prop
axiom IsolatedPart : Part → Time → Prop
def THM_T3c_contact : Prop :=
  (∀ (p : Part) (a : Act) (t : Time), ContactAct a → ActorOf a = p →
      Addresses a (Half1 (LayerOfP p)) ∧ Addresses a (Half2 (LayerOfP p))) ∧
  (∀ a : Act, ContactAct a → ¬ AuthorityCarrying a) ∧
  (∀ (p : Part) (a : Act) (t : Time), IsolatedPart p t → ContactAct a → ActorOf a = p →
      Addresses a (Half1 (LayerOfP p)))

/-- T3d · Safety before liveness: if a whole half refuses or falls silent, nothing
    loosens; nothing is promoted; the direction waits. [01 "T3d"] -/
axiom HalfSilent  : Layer → Time → Prop
axiom HalfRefuses : Layer → Time → Prop
axiom Promotion   : Act → Prop
def THM_T3d_safety_before_liveness : Prop :=
  ∀ (l : Layer) (a : Act) (t : Time),
    (HalfSilent l t ∨ HalfRefuses l t) →
      (Loosening a → ¬ ActsIn a t) ∧ (Promotion a → ¬ ActsIn a t)

/-- T4 · The trust configuration belongs to the Duality, never to CMOS: fixed by
    both halves at the minting, changed only by a majority of trust, never below a
    floor; CMOS verifies, works towards it, reports, and never lowers it.
    [01 "T4"] -/
axiom ConfigParameter : Type
axiom ConfigurationParameter : Configuration → ConfigParameter → Prop
axiom SetByBothHalves : ConfigParameter → Prop
axiom ChangedBy       : ConfigParameter → Act → Prop
axiom MajorityOfTrust : Act → Prop
axiom CMOSLowers      : Configuration → ConfigParameter → Prop
def THM_T4_config_owned_by_duality : Prop :=
  ∀ (c : Configuration) (k : ConfigParameter),
    ConfigurationParameter c k →
      SetByBothHalves k ∧
      (∀ a : Act, ChangedBy k a → MajorityOfTrust a) ∧
      ¬ CMOSLowers c k

/-- T5 · Majority of trust: M2 — at least half of each side's seats, rounded up
    (an act without a side was not witnessed by that side, AMB1-08); M1 — more
    than half of all pinned seats; the smallest threshold that never lets two
    disjoint sets carry contradicting acts and survives one refusal. Seats are
    counted from the pinned set in the record. [01 "T5"] -/
inductive Side | A | B
axiom Seat        : Type
axiom SideOf      : Seat → Side
axiom Pinned      : Time → List Seat
axiom SideCount   : Side → Act → Time → Nat   -- scaffold: that side's pinned seats that signed the act
axiom PinnedCount : Side → Time → Nat
def M2 (a : Act) (t : Time) : Prop :=
  ∀ s : Side, SideCount s a t * 2 ≥ PinnedCount s t
def M1 (a : Act) (t : Time) : Prop :=
  SideCount Side.A a t + SideCount Side.B a t > PinnedCount Side.A t + PinnedCount Side.B t
axiom Contradicts : Act → Act → Prop
axiom CarriedBy   : Act → List Seat → Prop
axiom OneRefused  : Act → Time → Prop
def DisjointSeats (s1 s2 : List Seat) : Prop := ∀ x : Seat, x ∈ s1 → x ∈ s2 → False
def THM_T5_majority : Prop :=
  (∀ (s1 s2 : List Seat) (a1 a2 : Act) (t : Time),
      DisjointSeats s1 s2 → CarriedBy a1 s1 → CarriedBy a2 s2 →
        M1 a1 t → M1 a2 t → ¬ Contradicts a1 a2) ∧
  (∀ (a : Act) (t : Time), OneRefused a t → M1 a t)

/-- T6 · Stand-ins take over at once; a majority may stop it only by revoking the
    stand-in on evidence against it. [01 "T6"] -/
axiom SeatEmpty        : Part → Time → Prop
axiom TookOverAtOnce   : Part → Part → Time → Prop
axiom StopsTakeover    : Act → Part → Prop
axiom EvidenceRevoke   : Part → Act → Prop
axiom ActTime          : Act → Time
def THM_T6_standins : Prop :=
  ∀ (h si : Part) (t : Time),
    OnboardedStandInFor si h → SeatEmpty h t →
      TookOverAtOnce si h t ∧
      (∀ (m : Act), StopsTakeover m si → ActsIn m (ActTime m) → EvidenceRevoke si m)

/-- T19 · The data boundary: what enters never leaves unless both halves permit it,
    with a record; material that alone recreates CMOS never leaves in usable form.
    [01 "T19"] -/
axiom Entered  : Value → Time → Prop
axiom LeavesAt : Value → Time → Prop
axiom ExportRecord : Record → Prop
axiom RecreatesCMOS : Value → Prop
axiom UsableForm : Value → Part → Prop
def THM_T19_data_boundary : Prop :=
  (∀ (v : Value) (t : Time), Entered v t → LeavesAt v t →
      ∃ r : Record, ExportRecord r ∧
        SignedByW (Half1 (LayerOf (tToAct t))) r ∧
        SignedByW (Half2 (LayerOf (tToAct t))) r) ∧
  (∀ (v : Value) (t : Time), RecreatesCMOS v → LeavesAt v t →
      ∀ p : Part, ¬ UsableForm v p)

/-- T20 · Time is a witness like any other: two independent time authorities, each
    with two servers the witness checks itself; the clock never moves backwards;
    disagreement beyond tolerance is "no now" and nothing with a validity verifies
    until they agree. [01 "T20"] -/
def THM_T20_time_witness : Prop :=
  (∃ a1 a2 : TimeAuthority, a1 ≠ a2 ∧ AuthorityIndependent a1 a2 ∧
      (ServersOf a1).length ≥ 2 ∧ (ServersOf a2).length ≥ 2) ∧
  (∀ (a : TimeAuthority) (t t' : Time), timeLE t t' → timeLE (ClockRead a t) (ClockRead a t')) ∧
  (∀ t : Time, DivergeBeyondTolerance t → NoNow t) ∧
  (∀ (s : Standing) (t : Time), NoNow t → ¬ stValid s (after t))

/-- T21 · Observability without leakage: records carry counts always and content
    only behind a grant. [01 "T21"; Derived from: Axiom 3, T1] -/
def THM_T21_observability : Prop :=
  ∀ (w : Part) (r : Record) (t : Time), Reads w r t →
    SeesCounts w r t ∧ (SeesContent w r t → ∃ g : Grant, ContentGrant w r)

/-- T22 · The axioms apply to themselves: a change to a law is an act — the
    owner's words, a new cold read, a new hash; verified at every run by both
    proof chains. [01 "T22"] -/
axiom LawChange   : Act → Prop
axiom OwnerWorded : Act → Prop
axiom ColdRead    : Act → Prop
axiom NewHash     : Act → Prop
def THM_T22_axioms_self_apply : Prop :=
  ∀ (a : Act) (t : Time), LawChange a → ActsIn a t →
    OwnerWorded a ∧ ColdRead a ∧ NewHash a ∧ BothChainsProve (configOfRepo dmpRepo)

/-- T24 · Tighten down on one witness, loosen with two; acts on another part's
    standing and on the Duality's own composition are dual-gated in either
    direction; every tightening names its lift condition, independent of the
    isolated thing; a stolen-key isolation lifts on nothing that key signs.
    [01 "T24"] -/
axiom TighteningBy      : Part → Act → Prop
axiom ActsOnStanding    : Act → Part → Prop
axiom ActsOnComposition : Act → Prop
axiom StolenKeyIsolation : Act → Prop
def THM_T24_tighten_loosen : Prop :=
  (∀ (a : Act) (t : Time), Tightening a → ActsIn a t →
      ∃ w : Part, IsWitness w ∧ SignedByW w a ∧ TighteningBy w a) ∧
  (∀ (a : Act) (t : Time), Loosening a → ActsIn a t →
      ∃ w1 w2 : Part, IsWitness w1 ∧ IsWitness w2 ∧ w1 ≠ w2 ∧
        SignedByW w1 a ∧ SignedByW w2 a) ∧
  (∀ (a : Act) (p : Part), ActsOnStanding a p ∨ ActsOnComposition a →
      Loosening a → SignedByW (Half1 (LayerOf a)) a ∧ SignedByW (Half2 (LayerOf a)) a) ∧
  (∀ tg : Act, Tightening tg → ∃ lc : Information, LiftCondition tg lc ∧ IndependentOfLift lc tg) ∧
  (∀ tg : Act, StolenKeyIsolation tg → Tightening tg)

/-- T24b · Lockstep: acts changing one half's standing toward the other are one
    record both halves sign, changing both sides alike; a loss is not an act; a
    half that cannot move in lockstep is not removed from inside — the pair is
    re-minted. [01 "T24b"] -/
axiom ChangesHalfStanding : Act → Prop
axiom TrustMovedAlike : Layer → Act → Prop
axiom CannotLockstep  : Layer → Prop
def THM_T24b_lockstep : Prop :=
  (∀ (a : Act) (t : Time), ChangesHalfStanding a → ActsIn a t →
      SignedByW (Half1 (LayerOf a)) a ∧ SignedByW (Half2 (LayerOf a)) a ∧
      TrustMovedAlike (LayerOf a) a) ∧
  (∀ l : Layer, CannotLockstep l → ∃ m : Act, IsMintingAct m ∧ RecoversBy l m)

/-- T24c · Self-correction: signing an act that contradicts the certificate the
    act cites is evidence against oneself; the peer half withdraws trust at once;
    the layer above restores from the certified state with new witnesses; after a
    configured number of restorations in a window the layer stops and escalates.
    [01 "T24c"] -/
axiom SignsAgainstDirective  : Part → Prop
axiom IsPeer                 : Part → Part → Prop
axiom EvidenceAgainstOneself : Part → Prop
axiom WithdrawsTrustAtOnce   : Part → Part → Prop
axiom RestoresFromCertified  : Part → Part → Prop
axiom RestorationsInWindow   : Part → Nat
axiom ConfiguredLimit        : Nat
axiom EscalatesStop          : Layer → Prop
def THM_T24c_self_correction : Prop :=
  ∀ (p q : Part),
    SignsAgainstDirective p → IsPeer q p →
      EvidenceAgainstOneself p ∧ WithdrawsTrustAtOnce q p ∧
      (∃ w1 w2 : Part, IsWitness w1 ∧ IsWitness w2 ∧
        RestoresFromCertified w1 p ∧ RestoresFromCertified w2 p) ∧
      (RestorationsInWindow p ≥ ConfiguredLimit → EscalatesStop (LayerOfP p))

/-- T28 · Enforcement is an act: the door's enforcement is itself an act both
    witnesses verify at run time, each on a path of its own; a mismatch is
    evidence against the door; every door obeys the cluster floor (three nodes).
    [01 "T28"] -/
axiom DoorDecisionLog    : Part → Record
axiom WitnessDecisionLog : Part → Record
axiom Mismatch : Record → Record → Prop
axiom VerifiesAtRuntime : Part → Record → Record → Time → Prop
axiom EvidenceAgainstDoor : Part → Time → Prop
def THM_T28_enforcement_act : Prop :=
  ∀ (d : Part) (t : Time), IsDoor d →
    (∀ w : Part, w = Half1 (LayerOfP d) ∨ w = Half2 (LayerOfP d) →
        VerifiesAtRuntime w (DoorDecisionLog d) (WitnessDecisionLog w) t) ∧
    (∀ t' : Time, Mismatch (DoorDecisionLog d) (WitnessDecisionLog (Half1 (LayerOfP d))) →
        EvidenceAgainstDoor d t') ∧
    (NodesOf d).length ≥ 3

/-- T29 · A shared cause the minting record does not declare turns the layer into
    a one-witness layer: every loosening at it stops. [01 "T29"] -/
axiom UndeclaredSharedCause : Layer → Prop
axiom OneWitnessLayer : Layer → Prop
def THM_T29_shared_cause : Prop :=
  ∀ l : Layer, UndeclaredSharedCause l →
    OneWitnessLayer l ∧
    ∀ (a : Act) (t : Time), Loosening a → LayerOf a = l → ¬ ActsIn a t

/-- T30 · "Wherever technically possible" is a record, never an escape: an
    exception only as a record both witnesses approved, with a validity, counted
    as a stopgap catch; an exception that is not such a record is a breach.
    [01 "T30"] -/
axiom ExceptionClaim : Act → Prop
axiom ApprovedRecord : Record → Act → Prop
axiom HasValidity    : Record → Prop
axiom StopgapCatch   : Act → Prop
axiom Breach         : Act → Prop
def THM_T30_exceptions : Prop :=
  ∀ e : Act, ExceptionClaim e →
    (∃ r : Record, ApprovedRecord r e ∧ SignedByW (Half1 (LayerOf e)) r ∧
                   SignedByW (Half2 (LayerOf e)) r ∧ HasValidity r ∧ StopgapCatch e) ∨
    Breach e

/-- T23 · The horizon: inside, for the act now, fully trusted or not acting; a
    fully trusted part passes every door and never meets a refusal for what it is
    trusted for; any other part is refused at the first door it reaches; a value
    moves to any part trusted for its class. [01 "T23"] -/
def THM_T23_horizon : Prop :=
  (∀ (p : Part) (a : Act) (t : Time), InsideP p t → ActorOf a = p → ActsIn a t →
      FullyTrusted p a t) ∧
  (∀ (p : Part) (a : Act) (t : Time), InsideP p t → ActorOf a = p →
      ¬ FullyTrusted p a t → ¬ ActsIn a t) ∧
  (∀ (p d : Part) (a : Act) (t : Time), IsDoor d → MeetsDoor p d → ActorOf a = p →
      FullyTrusted p a t → ¬ RefusedAt d p a t) ∧
  (∀ (v : Value) (p : Part) (t : Time), TrustedForClass p (ClassOf v) t → Reaches v p)

/-- T25 · Thin surfaces: receipt into quarantine and its record are a dual-gated
    act of the surface; admission is a separate, later dual-gated act; until
    admitted the information is opaque bytes; the receipt record cannot be made
    later than the receipt. [01 "T25"] -/
axiom AtSurface : Part → Information → Time → Prop
axiom Opaque      : Information → Prop
axiom Interpreted : Information → Prop
axiom Indexed     : Information → Prop
axiom Forwarded   : Information → Prop
axiom ReceiptRecord : Part → Information → Record → Prop
axiom RecActTime : Record → Time
def THM_T25_thin_surfaces : Prop :=
  ∀ (s : Part) (i : Information) (t : Time), IsSurface s → AtSurface s i t → ¬ AdmittedAt i t →
    (Opaque i ∧ ¬ Interpreted i ∧ ¬ Indexed i ∧ ¬ Forwarded i) ∧
    (∀ r : Record, ReceiptRecord s i r → timeLE (RecActTime r) t)

/-- T26 · Retention: with the Duality silent nothing is admitted and nothing sealed
    changes; a party on its own may hold and tighten, never admit, grant or
    promote; it may go dark, never wipe. [01 "T26"] -/
axiom DualitySilent : Layer → Time → Prop
axiom NewlyAdmitted : Information → Time → Prop
axiom Sealed        : Information → Prop
axiom Unchanged     : Information → Time → Prop
axiom SingleParty   : Part → Prop
axiom MayHold       : Part → Information → Prop
axiom MayWipe       : Part → Information → Prop
def THM_T26_retention : Prop :=
  (∀ (l : Layer) (i : Information) (t : Time), DualitySilent l t →
      ¬ NewlyAdmitted i t ∧ (Sealed i → Unchanged i t)) ∧
  (∀ (p : Part) (i : Information) (t : Time), SingleParty p →
      MayHold p i ∧ ¬ MayWipe p i) ∧
  (∀ (p : Part) (a : Act) (t : Time), SingleParty p → ActorOf a = p → Loosening a →
      ¬ ActsIn a t)

/-- T27 · Containment: non-CMOS information never interacts directly with CMOS
    information; admission is a loosening (both witnesses, while a grant holds);
    withdrawal is a tightening and needs one witness; a lapse ends admission by
    itself; contained-to-outside is an export (both halves); contained-to-destroyed
    runs on the date scheduled at containment; personal data only on a grant.
    [01 "T27"] -/
axiom DirectInteract : Information → Information → Prop
axiom CMOSInfo   : Information → Prop
axiom Withdrawal : Act → Information → Prop
axiom GrantExpired : Grant → Time → Prop
axiom ExportAct  : Act → Information → Prop
axiom OwnKeyOf   : Information → Key → Prop
axiom ScheduledAt : Key → Time → Prop
axiom KeyDestroyed : Key → Prop
axiom DestroyedItem : Information → Prop
axiom LegalDate   : Information → Time
axiom HeldByCMOS  : Information → Time → Prop
def THM_T27_containment : Prop :=
  (∀ i j : Information, NonCMOS i → CMOSInfo j → ¬ DirectInteract i j) ∧
  (∀ (i : Information) (a : Act) (t : Time), NewlyAdmitted i t → ActsIn a t →
      Loosening a ∧ SignedByW (Half1 (LayerOf a)) a ∧ SignedByW (Half2 (LayerOf a)) a) ∧
  (∀ (i : Information) (a : Act) (t : Time), Withdrawal a i → ActsIn a t →
      Tightening a ∧ ∃ w : Part, SignedByW w a) ∧
  (∀ (i : Information) (g : Grant) (t : Time), GrantExpired g t → ¬ AdmittedAt i (after t)) ∧
  (∀ (i : Information) (a : Act) (t : Time), ExportAct a i → ActsIn a t →
      SignedByW (Half1 (LayerOf a)) a ∧ SignedByW (Half2 (LayerOf a)) a) ∧
  (∀ i : Information, Contained i →
      ∃ k : Key, OwnKeyOf i k ∧ ScheduledAt k (LegalDate i) ∧
        (KeyDestroyed k → DestroyedItem i)) ∧
  (∀ (i : Information) (t : Time), PersonalData i → HeldByCMOS i t →
      ∃ g : Grant, HasGrant (HolderOf i) g t ∧ GrantCovers g i)

/-- T31 · The trap, and the floor: contained information reaches no part at all —
    not read, interpreted, forwarded or exported; its only transitions are
    re-admission and destruction; the design makes emission minimal and thermal —
    the entropy floor. [01 "T31"; the floor is premise] -/
axiom ReadA        : Act → Prop
axiom InterpretA   : Act → Prop
axiom ForwardA     : Act → Prop
axiom ReAdmission  : Act → Information → Prop
axiom DestructionOf : Act → Information → Prop
axiom TransitionBy : Act → Information → Prop
axiom AtEntropyFloor : Information → Prop
def THM_T31_trap_floor : Prop :=
  ∀ i : Information, Contained i →
    (∀ (p : Part) (a : Act) (t : Time), ActOn a i →
        ¬ (ReadA a ∨ InterpretA a ∨ ForwardA a)) ∧
    (∀ a : Act, TransitionBy a i → ReAdmission a i ∨ DestructionOf a i) ∧
    AtEntropyFloor i

/-- T34 · Three roads to the floor: each of the three bounds alone brings
    contained information to the entropy floor. [01 "T34"; each road is
    construction] -/
axiom EvidenceDecay : Information → Prop
axiom ScheduledDestruction : Information → Prop
axiom DestroyedByDate : Information → Prop
def THM_T34_three_roads : Prop :=
  ∀ i : Information, Contained i →
    ((∀ (w p : Part) (a : Act) (t : Time), ActOn a i → ¬ T w p a t) → AtEntropyFloor i) ∧
    (EvidenceDecay i → AtEntropyFloor i) ∧
    (ScheduledDestruction i → DestroyedByDate i)

/- §T32 · The trust field (the VIBE field). [01 "T32"]
   The arithmetic sort `Quantity` and the exact weighting are abstract: the corpus
   delegates the formulas to "Gravity's constant" outside DMP (AMB1-09, A1-F07). -/

axiom Quantity : Type
axiom qadd qmul qsub : Quantity → Quantity → Quantity
axiom qzero qone : Quantity
axiom qle : Quantity → Quantity → Prop
axiom IsZero  : Quantity → Prop
axiom NonNegQ : Quantity → Prop
axiom Member      : Part → Prop                    -- standing includes contributing to Milky Way
axiom MembersList : Time → List Part               -- scaffold: the members at a time
axiom GrantGraph  : Part → Part → Prop             -- edge: child derives through grantor
axiom Mass        : Part → Quantity
axiom derivedCountQ : Part → Quantity             -- scaffold: members deriving through p
axiom mass_def : ∀ p : Part, Mass p = qadd qone (derivedCountQ p)
inductive GrantChain : Part → Nat → Prop where
  | top  (l : Layer) : GrantChain (Half1 l) 0
  | top2 (l : Layer) : GrantChain (Half2 l) 0
  | step (c g : Part) (n : Nat) : GrantGraph c g → GrantChain g n → GrantChain c (n + 1)
def HasDepth (p : Part) (n : Nat) : Prop :=
  GrantChain p n ∧ ∀ m : Nat, m < n → ¬ GrantChain p m
axiom Freshness : Part → Time → Quantity   -- share of validity left since the last live verification
axiom Declared  : Boundary → Part → Quantity
axiom Held      : Part → Quantity
def Shortfall (p : Part) : Quantity := qsub (Declared DeclaredBoundary p) (Held p)
axiom WeightByFreshness : Quantity → Quantity → Quantity   -- scaffold: "weighted by freshness" (AMB1-09)
def Vibe (p : Part) (t : Time) : Quantity :=
  qmul (Mass p) (WeightByFreshness (Shortfall p) (Freshness p t))
def sumList : List Quantity → Quantity
  | [] => qzero
  | x :: xs => qadd x (sumList xs)
def Potential (t : Time) : Quantity := sumList ((MembersList t).map (fun p => Vibe p t))
def BoundaryHoldsDecls (t : Time) : Prop := ∀ p ∈ MembersList t, IsZero (Shortfall p)
axiom SystemAct       : Act → Prop
axiom DecidedByWeight : Act → Prop
axiom IndependentShares : Part → Part → Prop

/-- T32 · the field: the potential is zero exactly when the boundary holds what it
    declares; the system's own acts never raise the potential; the weight never
    votes (no level of trust); member isolation. The three arithmetic premises are
    stated inside the theorem because the corpus leaves them to Gravity's
    constant. -/
def THM_T32_vibe : Prop :=
  (∀ x y : Quantity, NonNegQ x → NonNegQ y → (IsZero (qmul x y) ↔ (IsZero x ∨ IsZero y))) →
  (∀ x y : Quantity, NonNegQ x → NonNegQ y → NonNegQ (qadd x y)) →
  (∀ (p : Part) (t : Time), p ∈ MembersList t → NonNegQ (Vibe p t)) →
    ((∀ t : Time, IsZero (Potential t) ↔ BoundaryHoldsDecls t) ∧
     (∀ (a : Act) (t : Time), SystemAct a → ActsIn a t →
        qle (Potential (after t)) (Potential t)) ∧
     (∀ (a : Act) (t : Time), DecidedByWeight a → ¬ ActsIn a t) ∧
     (∀ (m1 m2 : Part) (t : Time), Member m1 → Member m2 → m1 ≠ m2 →
        IndependentShares m1 m2))

/-- T33 · The VIBE test: two instances deployed from the same recipe span the same
    field, up to identity; the forward chain's expected field and the reverse
    chain's measured field agree layer by layer; a pull request moves the field
    only where its declaration moved. [01 "T33"; the digest is construction] -/
axiom SameRecipe : Configuration → Configuration → Prop
axiom FieldIso   : Configuration → Configuration → Prop
axiom ForwardExpected : Configuration → Layer → Quantity
axiom ReverseMeasured : Configuration → Layer → Quantity
axiom MovedOnlyWhereDeclared : Configuration → Configuration → Prop
def THM_T33_vibe_test : Prop :=
  ∀ c1 c2 : Configuration, SameRecipe c1 c2 →
    FieldIso c1 c2 ∧
    (∀ l : Layer, ForwardExpected c1 l = ReverseMeasured c2 l) ∧
    MovedOnlyWhereDeclared c1 c2

/-- T-P · The pressing: trust never crosses instances; information crosses only
    through an entry path both witnesses opened; loosening inside a pressed
    instance needs a fresh owner-signed challenge; no minting without a passed
    pressing of the same configuration; a pressed instance is never axiomatically
    sound ("Gravity abhors it"). [01 "T-P"] -/
axiom EvidenceValidIn : Evidence → Configuration → Prop
axiom OpenedByBoth    : Configuration → Information → Prop
axiom HoldsInfo       : Configuration → Information → Prop
axiom NativeTo        : Configuration → Information → Prop
axiom FreshOwnerChallenge : Act → Time → Prop
axiom PassedPressing    : Configuration → Prop
axiom SameConfiguration : Configuration → Configuration → Prop
def THM_TP_pressing : Prop :=
  (∀ (c1 c2 : Configuration) (e : Evidence), c1 ≠ c2 → EvidenceValidIn e c1 →
      ¬ EvidenceValidIn e c2) ∧
  (∀ (c : Configuration) (i : Information), (IsMinted c ∨ IsPressed c) → HoldsInfo c i →
      NativeTo c i ∨ OpenedByBoth c i) ∧
  (∀ (c : Configuration) (a : Act) (t : Time), IsPressed c → Loosening a → ActsIn a t →
      FreshOwnerChallenge a t) ∧
  (∀ c : Configuration, StartsMinting c →
      ∃ p : Configuration, PassedPressing p ∧ SameConfiguration p c) ∧
  (∀ c : Configuration, IsPressed c → ¬ DmpComplete c)

/-- T35 · Compliance is assembled, never claimed: a component proves what it does
    and claims nothing more; compliance belongs to an assembly; a standalone
    appliance, an off-recipe assembly and a pressed instance are not compliant and
    say so on every surface. [01 "T35"] -/
axiom ClaimsCompliance : Configuration → Information → Prop
axiom ShownInConfiguration : Configuration → Configuration → Prop
axiom AssembledByRecipe : Configuration → Prop
axiom DeclaresNotCompliant : Configuration → Prop
def THM_T35_compliance_assembled : Prop :=
  ∀ c : Configuration,
    (∀ (i : Information), ClaimsCompliance c i → DmpComplete c) ∧
    (¬ AssembledByRecipe c ∨ IsPressed c → (¬ DmpComplete c ∧ DeclaresNotCompliant c))

/-- T36 · The horizon is the one boundary between information and data: a crossing
    without the dual gate's permission is critical by definition, scored CVSS 10.0
    where a score is reported, and no class, scope, mitigation or exposure estimate
    rates it down. [01 "T36"] -/
inductive SeveritySort | critical | high | medium | low | info
axiom RatedSeverity : Finding → SeveritySort
axiom RatesDown : Finding → SeveritySort → Prop
axiom FindingOf' : Act → Finding → Prop
def THM_T36_horizon_boundary : Prop :=
  ∀ (a : Act) (b : Boundary), Crosses a b → ¬ WithPermission a →
    ∃ f : Finding, FindingOf' a f ∧ RatedSeverity f = SeveritySort.critical ∧
      ∀ s : SeveritySort, ¬ RatesDown f s

/- ================================================================
   §C · The C-rules of the constitution ("the rules this constitution always
   had, kept under their old numbers"). Types only.
   ================================================================ -/

/-- C1 · One door: Milky Way is the only way into CMOS, out of it and between its
    parts; constellations do not call each other directly. [01 "C1"] -/
axiom MilkyWay : Part
axiom ViaMilkyWay : Act → Prop
axiom References    : Part → Part → Prop
axiom Constellation : Part → Prop
def THM_C1_one_door : Prop :=
  (∀ (a : Act) (t : Time), Crosses a DeclaredBoundary → ActsIn a t → ViaMilkyWay a) ∧
  (∀ x y : Part, Constellation x → Constellation y → References x y → x = y)

/-- C2 and its Law block C2.L1-L4b: every message verifies itself. [01 "C2"] -/
axiom Msg : Type
axiom Token : Type
axiom Subject : Type
axiom Kind : Type
axiom Permission : Type
axiom TokenSigner : Part → Prop
axiom SignedToken : Token → Part → Prop        -- signed by that signer
axiom Names : Token → Subject → Prop
axiom EnrolledUnrevoked : Subject → Time → Prop
axiom SubjectKey : Token → Key
axiom KeySigned : Key → Msg → Prop
axiom InWindow : Token → Time → Prop
axiom Carries : Token → Permission → Prop
axiom NeededPermission : Kind → Permission
axiom KindOf : Msg → Kind
axiom TokenOf : Msg → Token
axiom VerifiedMsg : Type
axiom VerifiedOf : VerifiedMsg → Msg
inductive Reason | oversize | malformed | unknownVersion | untrustedTokenSigner
  | certificateExpired | badTokenSignature | tokenPolicy | tokenNotYetValid
  | tokenExpired | notEnrolled | revoked | enrolmentMismatch | sessionMismatch
  | badMessageSignature | stale | unknownKind | wrongPermission | replayed
  | replayCacheFull | doorClosed | doorRefused | doorLimit | transportRefused
  | untrustedDevice | transportCertificateExpired | transportMismatch
  | transportNoCertificate | connectionLimit
inductive Verdict | verified (v : VerifiedMsg) | refused (r : Reason)
axiom Verify : Msg → Time → Verdict
def IsVerified (m : Msg) (t : Time) : Prop := ∃ v : VerifiedMsg, Verify m t = Verdict.verified v
def RefusalOf (m : Msg) (t : Time) (r : Reason) : Prop := Verify m t = Verdict.refused r
axiom MemAt : MsgIdOf → Time → Prop

/-- C2.L1 · Verified means authorised. -/
def THM_C2_L1_verified_authorised : Prop :=
  ∀ (m : Msg) (t : Time), IsVerified m t →
    ∃ (sg : Part) (tk : Token) (s : Subject),
      TokenSigner sg ∧ SignedToken tk sg ∧ Names tk s ∧ EnrolledUnrevoked s t ∧
      KeySigned (SubjectKey tk) m ∧ InWindow tk t ∧
      Carries tk (NeededPermission (KindOf m))

/-- C2.L2 · One answer, fail closed: exactly one answer; the first failing rule's
    row, in the table's order, with that row's reason; a refusal leaves the replay
    memory as it was. (The 16 rules and their order are §IM below.) -/
def InRuleRange (i : Nat) : Prop := 1 ≤ i ∧ i ≤ 16
axiom RuleFails : Nat → Msg → Time → Prop
axiom ReasonOf : Nat → Reason
def THM_C2_L2_one_answer : Prop :=
  (∀ (m : Msg) (t : Time), IsVerified m t ∨ ∃ r : Reason, RefusalOf m t r) ∧
  (∀ (m : Msg) (t : Time) (r : Reason), RefusalOf m t r →
      ∃ i : Nat, InRuleRange i ∧ RuleFails i m t ∧
        (∀ j : Nat, InRuleRange j → j < i → ¬ RuleFails j m t) ∧ ReasonOf i = r) ∧
  (∀ (m : Msg) (t : Time) (r : Reason) (id : MsgIdOf), RefusalOf m t r →
      MemAt id (after t) → MemAt id t)

/-- C2.L3 · No replay: through one verifier, the same signed message is verified at
    most once — "at any later or earlier time" read as global uniqueness
    (AMB1-10). -/
def THM_C2_L3_no_replay : Prop :=
  ∀ (m : Msg) (t1 t2 : Time), IsVerified m t1 → IsVerified m t2 → t1 = t2

/-- C2.L3b · A full replay memory refuses; it never forgets early to make room. -/
axiom MemoryFull : Time → Prop
def THM_C2_L3b_full_memory : Prop :=
  ∀ (t : Time) (m : Msg), MemoryFull t → ¬ IsVerified m t

/-- C2.L4 · The permission table: a heartbeat needs im.heartbeat.send, and no other
    kind exists in IM version 0. -/
axiom Heartbeat : Kind
axiom heartbeatSend : Permission
axiom KnownKind : Kind → Prop
axiom Version0Kind : Kind → Prop
def THM_C2_L4_permission_table : Prop :=
  (NeededPermission Heartbeat = heartbeatSend) ∧
  (∀ k : Kind, Version0Kind k → k = Heartbeat) ∧
  (∀ (m : Msg) (t : Time), IsVerified m t → KnownKind (KindOf m))

/-- C3 · Every value carries its class, its identification axis, and a token at
    every border that is not an administrator; reveal is a grant. [01 "C3"] -/
axiom HasTokenAt : Value → Part → Prop
axiom IsAdministrator : Part → Prop
axiom Revealed : Value → Time → Prop
def THM_C3_values_carry_class : Prop :=
  (∀ (v : Value) (p : Part) (t : Time), Reaches v p → ¬ IsAdministrator p → HasTokenAt v p) ∧
  (∀ (v : Value) (t : Time), Revealed v t → ∃ g : Grant, GrantScope g = ClassOf v)

/-- C4 · Contracts change at stable promotions only. [01 "C4"] -/
axiom Contract : Type
axiom ContractChangedAt : Contract → Act → Prop
axiom StablePromotion : Act → Prop
def THM_C4_contracts : Prop :=
  ∀ (k : Contract) (a : Act), ContractChangedAt k a → StablePromotion a

/-- C5 · Financial data freezes at production. [01 "C5"] -/
axiom FinancialData : Value → Prop
axiom Productive : Part → Time → Prop
axiom Auditable : Value → Time → Prop
axiom ChangesValue : Act → Value → Prop
axiom ChangedByReviewedRelease : Value → Act → Prop
def THM_C5_financial_freeze : Prop :=
  ∀ (v : Value) (t : Time), FinancialData v → Productive (HolderOf v) t →
    Auditable v t ∧ ∀ a : Act, ChangesValue a v → ChangedByReviewedRelease v a

/-- C6 · The gates and the authority grant: the recorded grant wording is
    protected (rule DMP-009); an act on a system or on information outside CMOS's
    own estate needs both halves of the layer it belongs to (T38); until both have
    declared advanced testing, every act there needs their words per act, and
    anything irreversible outside the estate always does. [01 "C6"] -/
axiom OwnEstateAct : Act → Prop
axiom Irreversible : Act → Prop
axiom AdvancedTestingDeclaredHalf : Part → Act → Time → Prop
axiom PerActWords : Act → Prop
def THM_C6_authority_grant : Prop :=
  ∀ (a : Act) (t : Time), ActsIn a t → ¬ OwnEstateAct a →
    SignedByW (Half1 (LayerOf a)) a ∧ SignedByW (Half2 (LayerOf a)) a ∧
    ((Irreversible a ∨
      ¬ AdvancedTestingDeclaredHalf (Half1 (LayerOf a)) a t ∨
      ¬ AdvancedTestingDeclaredHalf (Half2 (LayerOf a)) a t) → PerActWords a)

/-- C7 · One repository deploys every part. [01 "C7"] -/
axiom DeploysFrom : Part → RootRepo → Prop
axiom DeployedPart : Part → Prop
def THM_C7_one_repository : Prop :=
  ∀ (p : Part) (r1 r2 : RootRepo), DeployedPart p → DeploysFrom p r1 → DeploysFrom p r2 → r1 = r2

/-- C9 · Open source: roles, not values — no secret, no company fact and no person
    beyond a role ever enters the tree. [01 "C9"] -/
axiom InTree : Information → Prop
axiom Secret : Information → Prop
axiom CompanyFact : Information → Prop
axiom PersonBeyondRole : Information → Prop
def THM_C9_roles_not_values : Prop :=
  ∀ i : Information, InTree i → ¬ (Secret i ∨ CompanyFact i ∨ PersonBeyondRole i)

/-- C10 · The defensive charter: every security-shaped act serves defensive
    security and privacy engineering of the organisation's own systems.
    [01 "C10"; CHARTER.md] -/
axiom SecurityShaped : Act → Prop
axiom DefensiveOwnEstate : Act → Prop
axiom TargetsThirdParties : Act → Prop
axiom DevelopsExploitsOrMalware : Act → Prop
axiom HarvestsCredentials : Act → Prop
axiom RunsOutOfScope : Act → Prop
def THM_C10_charter : Prop :=
  ∀ (a : Act) (t : Time), SecurityShaped a → ActsIn a t →
    DefensiveOwnEstate a ∧
    ¬ (TargetsThirdParties a ∨ DevelopsExploitsOrMalware a ∨
       HarvestsCredentials a ∨ RunsOutOfScope a)

/-- C12 · Information is tiered (MW net first, then routed outward, Tier 3 only
    through an exit node); a layer places information, never grants trust; privacy
    is a singularity no routing pulls out; credentials are singularities of their
    kind; every singularity is a cluster of at least three nodes; what an agent
    learns goes back into Tier 1. [01 "C12"] -/
axiom Tier : Type
axiom tier1 tier2 tier3 : Tier
axiom TierOf : Information → Tier
axiom Places : Layer → Information → Prop
axiom GrantsTrust : Layer → Information → Prop
axiom SingularityOf : Information → Prop
axiom RoutePullsOut : Layer → Information → Prop
axiom RoutedAsIfEmpty : Information → Prop
axiom CountsOnlyRecord : Information → Prop
axiom LearnedByAgent : Information → Prop
axiom IntoTier1 : Information → Prop
def THM_C12_tiers : Prop :=
  (∀ i : Information, TierOf i = tier1 ∨ TierOf i = tier2 ∨ TierOf i = tier3) ∧
  (∀ (l : Layer) (i : Information), Places l i → ¬ GrantsTrust l i) ∧
  (∀ i : Information, SingularityOf i →
      (∀ l : Layer, ¬ RoutePullsOut l i) ∧ RoutedAsIfEmpty i ∧ CountsOnlyRecord i) ∧
  (∀ i : Information, SingularityOf i → (NodesOf (HolderOf i)).length ≥ 3) ∧
  (∀ i : Information, LearnedByAgent i → IntoTier1 i)

/-- C13 · The nearest tier is asked first; the agent cites the record it used or
    records the empty search, and only then asks the owner. [01 "C13"] -/
axiom AsksOwner : Act → Prop
axiom Cites : Act → Record → Prop
axiom RecordedEmptySearch : Act → Prop
def THM_C13_nearest_tier : Prop :=
  ∀ (a : Act) (t : Time), AsksOwner a → ActsIn a t →
    (∃ r : Record, Cites a r) ∨ RecordedEmptySearch a

/-- C14 · Every path is combined: read paths and write trails before the owner;
    a write path is read through its trail or dry run, never by writing to find
    something out. [01 "C14"] -/
axiom NamesPaths : Act → Prop
axiom NamesUnknown : Act → Prop
axiom ReadsByWriting : Act → Prop
def THM_C14_combine_paths : Prop :=
  ∀ (a : Act) (t : Time), AsksOwner a → ActsIn a t →
    NamesPaths a ∧ NamesUnknown a ∧ ¬ ReadsByWriting a

/-- C15 · A write first reads the live state it will change and asserts what it
    expects; every write is read back afterwards and shows the wanted state; when
    the expected state is not found, nothing is written. [01 "C15"] -/
axiom WriteAct : Act → Prop
axiom LiveRead : Act → Act → Prop
axiom HappensBefore : Act → Act → Prop
axiom AssertsExpected : Act → Prop
axiom ReadBack : Act → Act → Prop
axiom ShowsWanted : Act → Prop
axiom ExpectedFound : Act → Prop
def THM_C15_write_reads_first : Prop :=
  (∀ (a : Act) (t : Time), WriteAct a → ActsIn a t →
      ∃ r b : Act, LiveRead a r ∧ HappensBefore r a ∧ AssertsExpected r ∧
                   ReadBack a b ∧ ShowsWanted b) ∧
  (∀ (a : Act) (t : Time), WriteAct a → ¬ ExpectedFound a → ¬ ActsIn a t)

/-- C16 · Company data reaches general testing only with its proof: the pair of
    pages (handling explanation, GRB report) exists, built from the current
    artifact template. [01 "C16"] -/
axiom GeneralTesting : Act → Prop
axiom Touches : Act → Information → Prop
axiom HandlingPage : Information → Prop
axiom GrbReport : Information → Prop
axiom FromCurrentTemplate : Information → Prop
def THM_C16_data_gate : Prop :=
  ∀ (a : Act) (i : Information) (t : Time), GeneralTesting a → ActsIn a t → Touches a i →
    HandlingPage i ∧ GrbReport i ∧ FromCurrentTemplate i

/-- C17 · The first level belongs to The Administrator and LHC: a new node at
    level 1 is created only with the words of both; until the first LHC is minted,
    The Administrator's words are recorded alone with `LHC pending`. [01 "C17"] -/
axiom LevelOneNode : Part → Prop
axiom CreatedBy : Act → Part → Prop
axiom WordsOfAdmin : Act → Prop
axiom WordsOfLHC : Act → Prop
axiom PendingRecord : Act → Prop
def THM_C17_admin_lhc : Prop :=
  ∀ (n : Part) (a : Act) (t : Time), LevelOneNode n → CreatedBy a n → ActsIn a t →
    WordsOfAdmin a ∧ (WordsOfLHC a ∨ (¬ LHCMinted t ∧ PendingRecord a))

/-- C18 · IM stays backwards compatible once locked: every later version accepts
    every message of a locked version with the same meaning; a locked version is
    never broken — a broken algorithm is contained, not retired. [01 "C18"] -/
axiom ImVersion : Type
axiom Locked : ImVersion → Time → Prop
axiom Accepts : ImVersion → Msg → Prop
axiom MeaningOf : Msg → ImVersion → Information   -- scaffold: what the message means under a version
axiom Speaks : Part → ImVersion → Prop
def THM_C18_im_backcompat : Prop :=
  ∀ (v v' : ImVersion) (m : Msg) (t t' : Time),
    Locked v t → timeLE t t' → Accepts v m →
      Accepts v' m ∧ MeaningOf m v' = MeaningOf m v

/-- C19 · A request is served only when it is secure and meant: two signatures
    (Doppler's security chain, the operations master's operational chain), the
    warehouse checks both itself, and each signing authority is co-signed by the
    other master. [01 "C19"] -/
axiom Warehouse : Part → Prop
axiom Serves : Act → Prop
axiom UnderSecurityChain : Act → Prop
axiom UnderOperationalChain : Act → Prop
axiom CoSigned : Act → Prop
axiom ChecksItself : Part → Act → Prop
def THM_C19_two_signatures : Prop :=
  ∀ (a : Act) (w : Part) (t : Time), Serves a → Warehouse w → ActsIn a t →
    UnderSecurityChain a ∧ UnderOperationalChain a ∧ CoSigned a ∧ ChecksItself w a

/-- C21 · Look it up, don't guess: the source of truth itself, before acting or
    asking; when more than one record fits, name every one and ask; never silently
    pick one. [01 "C21"] -/
axiom ReadSource : Act → Prop
axiom QuotesMatch : Act → Prop
axiom NamesAllCandidates : Act → Prop
axiom SilentlyPicks : Act → Prop
axiom AmbiguousFor : Act → Prop
def THM_C21_look_up : Prop :=
  ∀ (a : Act) (t : Time), ActsIn a t → AmbiguousFor a →
    (∃ r : Act, ReadSource r ∧ HappensBefore r a ∧ (QuotesMatch a ∨ NamesAllCandidates a)) ∧
    ¬ SilentlyPicks a

/-- C22 · Prove forward and back: two totally independent end-to-end chains; a
    layer counts as proven only when both chains agree on it; a mismatch is never
    settled by trusting one chain. [01 "C22"] -/
axiom ProofChain : Type
axiom intentChain evidenceChain : ProofChain
axiom Proves : ProofChain → Layer → Prop
axiom ProvenAt : Layer → Prop
def THM_C22_two_chains : Prop :=
  (∀ l : Layer, ProvenAt l ↔ (Proves intentChain l ∧ Proves evidenceChain l)) ∧
  (∀ l : Layer,
      ((Proves intentChain l ∧ ¬ Proves evidenceChain l) ∨
       (¬ Proves intentChain l ∧ Proves evidenceChain l)) →
        ¬ ProvenAt l ∧
        (∀ (a : Act) (t : Time), LayerOf a = l → Loosening a → ¬ ActsIn a t))

/-- C24 · Stable company-wide needs a survived cold start: a signed catalogue with
    full coverage, every scenario passed in the sandbox, the critical ones through
    a Milky Way simulator node, at least one on real infrastructure — each on the
    pass line P1 ∧ P2 ∧ P3. [01 "C24"; 11-test-design.md] -/
axiom Catalogue : Prop
axiom Passed : Scenario → Prop
axiom SimPassed : Scenario → Prop
axiom RealPassed : Scenario → Prop
axiom MarkedM : Scenario → Prop
axiom P1 P2 P3 : Scenario → Prop
def THM_C24_cold_start : Prop :=
  Catalogue ∧
  (∀ s : Scenario, Passed s → P1 s ∧ P2 s ∧ P3 s) ∧
  (∀ s : Scenario, MarkedM s → SimPassed s) ∧
  (∃ s : Scenario, RealPassed s)

/-- C25 · Every deployment obeys DMP: the gate runs on the exact commit and the
    deployment does not run on red; no deployment removes the last supported route
    for an administrator action; the list of known gaps only shrinks. [01 "C25"] -/
axiom Deployment : Act → Prop
axiom GateGreenOn : Act → Part → Prop
axiom RemovesRoute : Act → Part → Prop
axiom LastRoute : Part → Part → Prop
axiom KnownGapCount : Part → Time → Nat
def THM_C25_deployments : Prop :=
  (∀ (d : Act) (c : Part) (t : Time), Deployment d → ActsIn d t → GateGreenOn d c) ∧
  (∀ (d : Act) (c act : Part) (t : Time), Deployment d → ActsIn d t →
      RemovesRoute d act → LastRoute c act → False) ∧
  (∀ (g : Part) (t t' : Time), timeLE t t' → KnownGapCount g t' ≤ KnownGapCount g t)

/-- C∞ · The stopgap: what is not fully trusted is ejected — the pull request does
    not merge, the stage is not promoted, the running part is cut off at the door;
    everything that does not comply with DMP and IM and CM is automatically
    critical and nobody rates it down. (The meta-rule — stopgap catches counted
    toward zero, axioms toward fewer — governs this corpus itself, not CMOS, and
    lives in the report, not here.) [01 "C∞"] -/
axiom Ejected : Part → Time → Prop
axiom BreaksDmpImCm : Act → Prop
axiom FindingOfAct : Act → Finding
def THM_Cinf_ejection : Prop :=
  (∀ (p : Part) (a : Act) (t : Time), ¬ FullyTrusted p a t → ActsIn a t →
      Ejected p t) ∧
  (∀ a : Act, BreaksDmpImCm a →
      RatedSeverity (FindingOfAct a) = SeveritySort.critical ∧
      ∀ s : SeveritySort, ¬ RatesDown (FindingOfAct a) s)

/- ================================================================
   §IM · IM, the Interstellar Medium, version 0 (and the v1 proposal)
   [04-im.md]. Draft in the corpus; the verify rules and invariants are the part
   the corpus marks as machine-checkable.
   ================================================================ -/

/-- The verify rules: a message is verified iff no rule 1-16 fails; the refusal is
    the first failing rule's row reason; the verifier has no other way to accept.
    [04 "The verify rules"] -/
axiom IM_verified_iff_no_rule_fails :
  ∀ (m : Msg) (t : Time), IsVerified m t ↔ ∀ i : Nat, InRuleRange i → ¬ RuleFails i m t

axiom IM_first_failure_reason :
  ∀ (m : Msg) (t : Time) (r : Reason), RefusalOf m t r →
    ∃ i : Nat, InRuleRange i ∧ RuleFails i m t ∧
      (∀ j : Nat, InRuleRange j → j < i → ¬ RuleFails j m t) ∧ ReasonOf i = r

axiom IM_no_other_accept :
  ∀ (m : Msg) (t : Time), IsVerified m t → ∀ i : Nat, InRuleRange i → ¬ RuleFails i m t

/-- The refusal log carries counts by reason and kind, never content: no subject,
    no token, no payload, no address, no secret can reach it. [04 "The refusal log"] -/
axiom Mentions : LogEntry → Information → Prop
axiom LoggedEntry : LogEntry → Prop
def THM_IM_refusal_log_no_content : Prop :=
  ∀ e : LogEntry, LoggedEntry e → ¬ ∃ i : Information, Mentions e i

/-- I2 · no replay inside the window (the same claim as C2.L3). [04 "Invariants"] -/
def THM_IM_I2 : Prop := THM_C2_L3_no_replay

/-- I4 · no algorithm choice: version 0 parses only ECDSA P-256 keys and 64-byte
    signatures; anything else is malformed. [04 "Invariants"] -/
axiom P256Form : Msg → Prop
def THM_IM_I4 : Prop :=
  ∀ (m : Msg) (t : Time), IsVerified m t → P256Form m

/-- I5 · the quiet answer: before a valid knock the gate sends no byte.
    [04 "Invariants"; 05 "The quiet answer"] -/
axiom ValidKnock : Input → Time → Prop
axiom SendsNothing : Input → Time → Prop
def THM_IM_I5_quiet : Prop :=
  ∀ (k : Input) (t : Time), ¬ ValidKnock k t → SendsNothing k t

/-- I6 · canonical form: parsing then encoding returns the same bytes; any other
    bytes do not parse. [04 "Invariants"] -/
axiom Bytes : Type
axiom ParsesFrom : Bytes → Msg → Prop
axiom Encodes : Msg → Bytes
def UniqueParse (b : Bytes) (m : Msg) : Prop := ∀ m' : Msg, ParsesFrom b m' → m' = m
def THM_IM_I6_canonical : Prop :=
  ∀ (m : Msg) (b : Bytes), ParsesFrom b m → ParsesFrom (Encodes m) m ∧ UniqueParse (Encodes m) m

/-- Verification is remembered; a refused message never uses up an id. -/
axiom IdOf : Msg → MsgIdOf
axiom IM_remember_on_verify : ∀ (m : Msg) (t : Time), IsVerified m t → MemAt (IdOf m) (after t)

/-- A version of IM is accepted at a door only when it carries the composition
    proof for itself; a gate runs exactly one version, no negotiation. [04 "What
    IM is (the axiomatic chain)", draft] -/
axiom ImVersionOf : Msg → ImVersion
axiom HasCompositionProof : ImVersion → Prop
axiom RunsVersion : Part → ImVersion → Prop
def THM_IM_version_discipline : Prop :=
  (∀ (m : Msg) (t : Time), IsVerified m t → HasCompositionProof (ImVersionOf m)) ∧
  (∀ (g : Part) (v1 v2 : ImVersion), RunsVersion g v1 → RunsVersion g v2 → v1 = v2)

/-- Depth is bounded on the wire (from version 1): a door refuses a message above
    the maximum depth. [04 "What IM is", bullet 4] -/
axiom EnvelopeDepth : Msg → Nat
axiom HasDepthField : Msg → Prop
axiom MaxDepth : Nat
def THM_IM_depth_bounded : Prop :=
  ∀ (m : Msg) (t : Time), IsVerified m t → HasDepthField m → EnvelopeDepth m ≤ MaxDepth

/-- IM v1 · two chains of trust: a component may send a kind only when BOTH tokens
    carry the permission (the intersection); both tokens name the same subject and
    subject key; a root configured for both chains is refused. [04 "IM version 1";
    proposal] -/
axiom SecurityToken OpToken : Type
axiom SecTokenOf : Msg → SecurityToken
axiom OpTokenOf  : Msg → OpToken
axiom CarriesP  : SecurityToken → Permission → Prop
axiom CarriesP2 : OpToken → Permission → Prop
axiom SameSubjectKey : SecurityToken → OpToken → Prop
axiom HasOpToken : Msg → Prop
axiom RootForBothChains : Key → Prop
axiom IsTrustedRoot : Key → Prop
def THM_IM_v1_dual_trust : Prop :=
  (∀ (m : Msg) (t : Time), IsVerified m t → HasOpToken m →
      CarriesP (SecTokenOf m) (NeededPermission (KindOf m)) ∧
      CarriesP2 (OpTokenOf m) (NeededPermission (KindOf m))) ∧
  (∀ m : Msg, HasOpToken m → SameSubjectKey (SecTokenOf m) (OpTokenOf m)) ∧
  (∀ k : Key, RootForBothChains k → ¬ IsTrustedRoot k)

/-- IM v1 · isolation orders: isolate is a tightening (one signature: Doppler's
    security leaf or a White Key); lift and override are loosenings and need two
    signatures from two different keys; silence alone never isolates; nothing but
    an order ends an isolation — no timeout, no automatic recovery.
    [04 "IM version 1", "Orders and the White Key"] -/
axiom IsolationOrder : Act → Prop
axiom LiftOrder : Act → Prop
axiom OverrideOrder : Act → Prop
axiom WhiteKeySigned : Part → Act → Prop
axiom StaleHealthReport : Time → Prop
axiom IsolatedGate : Part → Time → Prop
def THM_IM_v1_orders : Prop :=
  (∀ (a : Act) (t : Time), IsolationOrder a → ActsIn a t →
      ∃ w : Part, WhiteKeySigned w a) ∧
  (∀ (a : Act) (t : Time), (LiftOrder a ∨ OverrideOrder a) → ActsIn a t →
      ∃ w1 w2 : Part, WhiteKeySigned w1 a ∧ WhiteKeySigned w2 a ∧ w1 ≠ w2) ∧
  (∀ (g : Part) (t : Time), StaleHealthReport t → ¬ IsolatedGate g (after t)) ∧
  (∀ (g : Part) (t t' : Time), IsolatedGate g t → timeLE t t' →
      ¬ (∃ a : Act, LiftOrder a ∨ OverrideOrder a) → IsolatedGate g t')

/- ================================================================
   §MW · Milky Way  [05-milky-way.md]
   -/

/-- Verified is a type only the verifier can create; every consumer accepts only
    verified messages, so an unverified message cannot reach a consumer by
    mistake. [05 "The verifier"] -/
axiom Consumed : VerifiedMsg → Time → Prop
def THM_MW_verified_only : Prop :=
  ∀ (v : VerifiedMsg) (t : Time), Consumed v t → IsVerified (VerifiedOf v) t

/-- The verify rules sit only in Milky Way: no other part decides whether a
    message is genuine. [05 "The parts and where they live"] -/
axiom DecidesGenuine : Part → Prop
def THM_MW_only_verifier : Prop :=
  ∀ d : Part, DecidesGenuine d → d = MilkyWay

/-- The two identities are one: the certificate TLS showed is the certificate IM
    proves, both directions. [05 "Transport encryption"] -/
axiom Session : Type
axiom TlsCertOf : Session → Key
axiom ImCertOf  : Session → Key
def THM_MW_identity_binding : Prop :=
  ∀ s : Session, TlsCertOf s = ImCertOf s

/- ================================================================
   §BH · Black Hole  [06-black-hole.md]
   -/

inductive SnClass | IIb | IIn | IIL | IIP
axiom PassedClass : Component → SnClass → Prop
axiom PublicPort : Component → Prop

/-- No public port opens before the component behind it has passed IIb on the
    sandbox. [06 "Where the class gates"; 01 C2] -/
def THM_BH_port_IIb : Prop :=
  ∀ c : Component, PublicPort c → PassedClass c SnClass.IIb

/-- A command without a lemma is not proven safe, whatever passed around it.
    [06 "Lemmas and the lemma ledger"] -/
axiom ImCommand : Type
axiom HasLemma : ImCommand → Prop
axiom ProvenSafe : ImCommand → Prop
def THM_BH_lemma_ledger : Prop :=
  ∀ c : ImCommand, ¬ HasLemma c → ¬ ProvenSafe c

/-- Two lines (what it does, where it is used) can raise a class, never lower it,
    and the strictest wins. [06 "Supernova classes"] -/
axiom EffectiveClass : Component → SnClass
axiom DistanceClass  : Component → SnClass
axiom LineRaised     : Component → SnClass
axiom atLeast : SnClass → SnClass → Prop
def THM_BH_class_monotone : Prop :=
  ∀ c : Component,
    atLeast (EffectiveClass c) (DistanceClass c) ∧ atLeast (EffectiveClass c) (LineRaised c)

/-- GRB runs: a run without a scope file does not happen; the flag value is fresh,
    planted only in the sandbox, never written into the repository, a document or
    a log; the escape ring's isolation is checked before the run; a reached flag
    blocks the class until fixed and re-run. [06 "GRB runs and the scope file"] -/
axiom GrbRun : Type
axiom HasScopeFile : GrbRun → Prop
axiom FlagValue : GrbRun → Information
axiom FreshRandom : Information → Prop
axiom PublishedAnywhere : Information → Prop
axiom RingChecked : GrbRun → Prop
axiom ReachedFlag : GrbRun → Prop
axiom ClaimsClass : GrbRun → Component → SnClass → Prop
def THM_BH_grb : Prop :=
  (∀ r : GrbRun, HasScopeFile r) ∧
  (∀ r : GrbRun, FreshRandom (FlagValue r) ∧ ¬ PublishedAnywhere (FlagValue r)) ∧
  (∀ r : GrbRun, RingChecked r) ∧
  (∀ (r : GrbRun) (c : Component) (k : SnClass), ReachedFlag r → ClaimsClass r c k →
      ¬ PassedClass c k)

/- ================================================================
   §CS · Cold start  [11-test-design.md]
   -/

/-- A run counts for a promotion only if the cold-start surface has not changed
    since; the pass line is P1 and P2 and P3 — a scenario that fails P3 has
    failed. -/
axiom RunCountsFor : Scenario → Prop
axiom SurfaceUnchanged : Scenario → Prop
def THM_CS_pass_line : Prop :=
  (∀ s : Scenario, RunCountsFor s → SurfaceUnchanged s) ∧
  (∀ s : Scenario, (P1 s ∧ P2 s ∧ ¬ P3 s) → ¬ Passed s)

/- ================================================================
   §PROC · Process  [14-process.md; the axiom-derived part]
   -/

/-- Rules need the expert (draft): tacit approval is gone — the absence of
    evidence moves nothing (Axiom 2); silence leaves the rule a proposal. -/
axiom ProposedRule : Information → Prop
axiom WeighedIn : Information → Time → Prop
axiom InForce : Information → Time → Prop
def THM_PROC_no_tacit_approval : Prop :=
  ∀ (r : Information) (t : Time), ProposedRule r → ¬ WeighedIn r t → ¬ InForce r t

/- ================================================================
   §ROOT · The root chain, marks, versions, tree, dwarf galaxies, setup
   [00-preamble.md; 02-names-and-hierarchy.md; SETUP.md; tools/*]
   -/

axiom HoldsVendored : RootRepo → RootRepo → Prop
/-- Each root repository depends only on the ones before it, in one direction;
    nothing ever points back up the chain. [00 "The root chain"] -/
def THM_ROOT_chain : Prop :=
  HoldsVendored gravityRepo dmpRepo ∧ HoldsVendored imRepo dmpRepo ∧
  HoldsVendored imRepo gravityRepo ∧ HoldsVendored cmRepo dmpRepo ∧
  HoldsVendored cmRepo gravityRepo ∧ HoldsVendored cmRepo imRepo ∧
  ∀ a b : RootRepo, HoldsVendored a b → ¬ HoldsVendored b a

/-- A copy that no longer matches its pin is refused by the gate.
    [00 "The root chain"] -/
axiom Pin : Type
axiom MatchesPin : RootRepo → Pin → Prop
axiom GateAccepts : RootRepo → Pin → Prop
def THM_ROOT_pin : Prop :=
  ∀ (r : RootRepo) (p : Pin), ¬ MatchesPin r p → ¬ GateAccepts r p

/-- The version: a section cannot be stable since a version newer than VERSION;
    the laws file changes only together with its section.
    [00 "The version"; 00 "The marks"] -/
axiom Ver : Type
axiom verLE : Ver → Ver → Prop
axiom CurrentVersion : Ver
axiom StableSince : Information → Ver
axiom SectionStable : Information → Prop
axiom LawsFileChanged : Information → Prop
axiom SectionChanged : Information → Prop
def THM_ROOT_version : Prop :=
  (∀ (s : Information) (v : Ver), SectionStable s → StableSince s = v →
      verLE v CurrentVersion) ∧
  (∀ s : Information, LawsFileChanged s → SectionChanged s)

/-- A stable section that says `none yet` is printed by the `dmp` runner on every
    run, so nobody mistakes prose for a gate. [00 "The marks"] -/
axiom PrintedByRunner : Information → Prop
axiom EnforcedByNone : Information → Prop
def THM_MARKS_print_unenforced : Prop :=
  ∀ s : Information, SectionStable s → EnforcedByNone s → PrintedByRunner s

/-- Dwarf galaxies: everything in a dwarf galaxy trusts the main galaxy and
    nothing else; it holds no roots of its own; and it contains its own
    information from every other dwarf galaxy of the same main galaxy
    [00 "Who maintains it"]. -/
axiom DwarfOf : Configuration → Configuration → Prop
axiom TrustsOnly : Configuration → Configuration → Prop
axiom InfoFrom : Configuration → Information → Prop
def THM_DWARF : Prop :=
  ∀ (d m : Configuration), DwarfOf d m →
    TrustsOnly d m ∧
    ∀ (d' : Configuration) (i : Information), DwarfOf d' m → d ≠ d' →
      InfoFrom d' i → HoldsInfo d i

/-- Tree discipline: the namespace of every file is the folder name or starts
    with it followed by a dot; a node-shaped folder the tree does not list is
    refused. [02 "The tree"] -/
axiom NamespaceOf : Part → Information
axiom FolderNameOf : Part → Information
axiom NamespaceMatchesFolder : Part → Prop
axiom Listed : Part → Prop
axiom NodeShaped : Part → Prop
axiom RefusedByGate : Part → Prop
def THM_TREE_discipline : Prop :=
  (∀ x : Part, Listed x → NamespaceMatchesFolder x) ∧
  (∀ x : Part, NodeShaped x → ¬ Listed x → RefusedByGate x)

/-- SETUP: a repository needs nothing SETUP.md does not list — the check fails
    exactly on the five listed conditions. [SETUP.md "The check";
    tools/check-setup.sh] -/
inductive Outcome | ok | fail
axiom RunCheckSetup : RootRepo → Outcome
axiom LeanPinMismatch : RootRepo → Prop
axiom DotnetMismatch : RootRepo → Prop
axiom UnlistedHostReached : RootRepo → Prop
axiom PinHostUnlisted : RootRepo → Prop
axiom UnlistedToolchain : RootRepo → Prop
def THM_SETUP_check : Prop :=
  ∀ r : RootRepo, RunCheckSetup r = Outcome.fail ↔
    (LeanPinMismatch r ∨ DotnetMismatch r ∨ UnlistedHostReached r ∨
     PinHostUnlisted r ∨ UnlistedToolchain r)

/-- The scrub scan fails exactly when a tracked file matches a pattern outside the
    allow list. [tools/scrub-scan.sh] -/
axiom RunScrubScan : RootRepo → Outcome
axiom Tracked : RootRepo → Information → Prop
axiom MatchesPattern : Information → Information → Prop
axiom AllowListed : Information → Prop
def THM_SETUP_scrub : Prop :=
  ∀ (r : RootRepo) (i : Information), Tracked r i →
    (RunScrubScan r = Outcome.fail ↔ ∃ p : Information, MatchesPattern i p ∧ ¬ AllowListed i)

end DMP
```

---

## Ambiguity register

Each entry: location; reading chosen for the Lean statement; alternative reading(s);
what turns on the choice.

- **AMB1-01** — 01 "Axiom 1": "each with full reach over the act and gated only by the
  other". Chosen: folded into the two-halves hypothesis — the pair's joint trust is the
  necessary condition of acting. Alternative: "reach" is a technical-channel notion (cf.
  T3b routes) and the clause additionally forbids third gates and constrains channel
  administration. Turns on: whether Axiom 1 says anything about who may configure routes
  and channels.
- **AMB1-02** — 01 Axiom 1: the gate's answers. Chosen: binary `permit`/`refuse`
  (`inductive Answer`). Alternative: graded answers (T3d "hold", T24 "the stricter answer
  stands" suggest an ordered answer space). Turns on: `AX1_stricter_stands` is only
  literally "stricter" in a lattice; binary collapses it to "disagreement → refuse".
- **AMB1-03** — 01 G0: "the owner's words stand for both halves". Chosen:
  biconditional substitution (`G0_standin_semantics`: each half's trust equals the
  owner's). Alternative: the owner's words merely licence individual gates without any
  trust relation (the text says gates "ask for the owner's words"). Turns on: whether
  pre-minting acts satisfy Axiom 1's letter or are axiom-free exceptions.
- **AMB1-04** — 01 "The words": "independent". Chosen: relative to the layer's declared
  failure-class list (the literal definition). Alternative: absolute independence of the
  two witnesses. Turns on: T29 only demotes layers for *undeclared* shared causes, so the
  list's composition decides independence (see A1-F04).
- **AMB1-05** — 01 "The words": "contains". Chosen: trust reading — no witness beyond the
  boundary is trusted for any act on the information (`Contains`). Alternative: modal
  reading — no act *can* carry the information across (impossibility, not mere absence of
  trust). Turns on: whether containment is derivable from T0+Axiom 1 (as T37 claims) or an
  additional primitive force.
- **AMB1-06** — 01 "The words": "inside". Chosen: two predicates — `InsideP` (parts, via
  standings from both witnesses) and `AdmittedAt` (information, via admission). The word
  list uses "inside" for both. Alternative: one unified notion. Turns on: which "inside"
  T23 (horizon), T31 (trap) and T36 quantify over.
- **AMB1-07** — 01 "The words": "time" is a declared undefined word, but T20 derives
  "now" from two time authorities. Chosen: one primitive sort with an abstract order;
  T20 as a constraint on witnesses of time. Alternative: time *is* the authorities'
  readings. Turns on: whether T20 is a construction of the word or a rule about it.
- **AMB1-08** — 01 T5: "(an act without a side was not witnessed by that side)".
  Chosen: acts carry a side attribution; a side-less act counts as unwitnessed by both
  sides. Alternative: side-less acts cannot occur. Turns on: quorum arithmetic for
  governance acts that have no side.
- **AMB1-09** — 01 T32: "shortfall … weighted by freshness"; "mass times shortfall".
  Chosen: abstract `WeightByFreshness` and a `Quantity` sort, with the zero-characterisation
  stated under explicit arithmetic premises inside `THM_T32_vibe`. Alternative: the exact
  formulas of "Gravity's constant" (outside this corpus). Turns on: whether T32 is
  formalisable from DMP alone at all (A1-F07).
- **AMB1-10** — 01 C2.L3: "refused at any later **or earlier** time". Chosen: global
  uniqueness of verification across all times (`THM_C2_L3_no_replay`: t1 = t2).
  Alternative: only later times; "earlier" is rhetorical. Turns on: the strength of I2 and
  the claimed completeness of rule 16 (04, "Why rule 16 is complete").
- **AMB1-11** — 01 Axiom 1: "This holds at every layer". Chosen: `LayerOf` total — one
  deciding layer per act. Alternative: acts spanning several layers need the dual gate at
  each. Turns on: the composition claim of 04 ("a network of nodes that meet DMP is itself
  a node that meets DMP").
- **AMB1-12** — 01 "The words": a witness may be "a proof chain, a body of people".
  Chosen: `IsWitness : Part → Prop` (witnesses are parts). Alternative: separate sorts for
  natural persons and institutions, bridged by `TracesTo`. Turns on: how T-P's "both
  witnesses trace to one person" is typed.
- **AMB1-13** — 01 "The words": DMP-complete requires "both chains prove it". Chosen:
  abstract primitive `BothChainsProve`. Alternative: unfold to C22's two-chain
  definitions. Turns on: circularity — completeness defined via proofs built from the same
  axioms (the corpus accepts this self-reference in T22; noted, not resolved).
- **AMB1-14** — 01 Axiom 3: "leaves a record". Chosen: at least one record per qualifying
  act (∃ in `AX3_record_exists`). Alternative: exactly one canonical record per act.
  Turns on: the destruction rule (which record's layer's witnesses must both sign).
- **AMB1-15** — 01 C∞: "Where gates disagree, the stricter answer stands" (review gate,
  verify, proof chains). Chosen: formalised only within one layer's two halves
  (`AX1_stricter_stands`); cross-gate strictness left unstated. Alternative: a global
  strictest-of-all-gates rule. Turns on: how review-gate verdicts trade off against
  proof-chain verdicts.
- **AMB1-16** — 01 T38: "higher-order DoT" and "at the top … the owner stands for both
  halves only under G0". Chosen: `HigherLayer` relation without well-foundedness; the top
  resolved by `G0_owner_stands_for_both`. Alternative: the regress must be finite (then
  finiteness itself needs an axiom or T32's depth notion must be total). Turns on: whether
  every layer's Duality grounds out at the minting.

## Findings

Severity scale: critical / high / medium / low. All findings are [argued] from the cited
locations.

- **A1-F01 · high — "Theorem" label overclaims, by the chapter's own semantics.**
  Where: 01 "How this chapter is built" + "What a derivation is here" vs the T/C sections.
  What is wrong: the chapter asserts "Everything after that is a **theorem**", while its
  own derivation semantics says a `Derived from:` line naming a *construction*,
  *configuration* or *premise* "does not mean the theorem follows from what it names".
  T3 (premise: majority-of-nodes), T24c/T32/T33/T34 (construction), C1 (one door is
  construction), C4/C5 (construction) are therefore design choices constrained by the
  axioms, not consequences of them — contradictory with the "theorem" classification
  (circular classification, not circular logic). Why it matters: Gravity's proof obligation
  and the system's claimed coverage are inflated; a formaliser must either weaken these to
  implications over configurations or reclassify them. Fix: split the chapter's own three
  categories (theorem / parameterised construction / premise-bounded rule) in each
  section's status line.
- **A1-F02 · high — Stable sections with "Enforced by: none yet" contradict the marks
  rule.** Where: 00 "The marks" ("A stable section without a check is a defect in DMP,
  not a rule; the fix is a check, or the mark goes back to draft") vs the stable sections
  carrying `none yet`: 01 Axiom 4, C3, C4, C5, C24; 00 "The root chain", "How DMP
  hardens"; 02 "The three levels", "Names in use", "Sealed candidates"; 10 "Settings are
  exposed", "Documentation moves with code", "Every change is a pull request"; 14 "Roles",
  "Every pull request goes through CM", "Custom scripts become issues", "The cadence",
  "Completion goals", "Advanced testing", "What the owner does by hand". What is wrong:
  contradictory — 01's header says every section is stable and a PR breaking one is
  refused, while 00 downgrades exactly those sections to "a defect, not a rule".
  Why it matters: a gate cannot both refuse on them and treat them as non-rules; the
  corpus violates its own status discipline in ~18 stable sections. Fix: add checks, move
  the marks to draft, or scope 00's defect rule to exclude the constitution.
- **A1-F03 · high — A stable hash-locked law depends on a draft table.** Where: 01 "C2"
  (stable since DMP 0.1.0, laws file locked by sha256) vs 04 "The verify rules" (draft).
  What is wrong: C2.L2 fixes the verify semantics by reference to "the first row of
  chapter 04's table whose test fails, in the table's order", and C2.L4 names the version-0
  permission table — but chapter 04 is draft and can be reordered or changed without
  changing C2's laws-file hash. A stable law's meaning depends on draft content.
  Why it matters: the one place where DMP claims machine-checked laws (C2) is not
  self-contained; the hash lock does not lock what the law means. Fix: freeze the rule
  order and table inside the law text, or mark C2 draft until 04 is stable.
- **A1-F04 · medium — Independence is gerrymanderable, and the proof layer's shared root
  sits on the boundary of the definition.** Where: 01 "The words" (independent), "C22"
  ("both end at the DMP text on purpose"), G0 (assumption register), T29. What is wrong:
  independence = sharing no member of the *declared* class list; the two proof chains
  deliberately share the DMP text and (per G0) the prover-logic premise; whether that
  shared dependency breaks the proof layer's DoT depends entirely on whether the minting's
  class list includes it — and T29 only demotes layers for *undeclared* causes. Why it
  matters: the "two independent witnesses" at the proof layer — the load-bearing instance
  of Axiom 1 — can be constituted true by list choice. Fix: state that declared shared
  roots are recorded as accepted shared members and excluded from the test, or add the
  DMP-text class and accept the consequence.
- **A1-F05 · medium — Axiom 1 is unsatisfiable in the ground state the corpus licenses.**
  Where: 01 "Axiom 1" + "G0" ("LHC pending"; owner's words for both halves) + "T-P" (both
  trace to one ⇒ out of spec). What is wrong: until the minting, the two halves trace to
  one person, so under the words' independence definition Axiom 1's hypothesis fails for
  every layer; the system's base state violates its own first axiom, patched by calling
  pre-minting gates "G0, not a theorem" — a scoping the axiom itself does not carry.
  Why it matters: whether the T-theorems hold pre-minting is undefined; a formaliser must
  parameterise (done here: AX1 carries the DoT/Independent hypotheses). Fix: scope Axiom 1
  ("once minted") and state the pre-minting regime as part of G0.
- **A1-F06 · medium — T24 vs T27: one-witness withdrawal of a Duality grant has no
  precedence rule.** Where: 01 "T24" ("An act on another part's standing … is an act under
  the dual gate and T5 in either direction") vs "T27" ("Withdrawal … is a tightening and
  needs one witness"). What is wrong: an admission is a grant (a record the Duality made),
  so T27's one-witness withdrawal is arguably an act on a standing in T24's sense; both
  are stated as flat rules with no conflict clause. Why it matters: two literal readings
  give different gate behaviour for the same act; the stricter-answer rule does not apply
  (this is rules-disagreeing, not witnesses). Fix: "notwithstanding T24" in T27, or fold
  admissions into T24's lockstep set.
- **A1-F07 · medium — T32's formulas are not in the corpus it claims them in.** Where:
  01 "T32" ("The formulas and their parameters are Gravity's constant" — a file outside
  DMP). What is wrong: the VIBE definitions (weighting of shortfall by freshness, mass's
  counting, the arithmetic sort) are delegated outside DMP, yet T32 asserts the
  potential-zero characterisation that depends on them — unformalizable from DMP alone
  (formalised here with explicit arithmetic premises inside the theorem). Why it matters:
  T33's VIBE test and the "stable publishes a VIBE digest" pipeline inherit the gap.
  Fix: inline the formulas into T32, or state T32's claims as conditional on Gravity's
  constant.
- **A1-F08 · medium — The declared word list omits load-bearing primitives.** Where:
  01 "The words" vs Axiom 4 (boundary), T37/C12 (information), T1/C3 (value), Axiom 3
  (counts), the words themselves (grant, validity), 04 (message, key). What is wrong: the
  corpus's foundational vocabulary list is incomplete; several terms used in axioms and
  theorems are neither declared undefined nor defined. Why it matters: an axiom system
  that prides itself on naming its primitives ("undefined, like point and line") silently
  relies on at least six more. Fix: extend "the words" (costless, since declared undefined).
- **A1-F09 · low — "The law" is an external authority absent from the assumption
  register.** Where: 01 Axiom 3 ("kept as long as the law requires and no longer than it
  allows"), T27 ("the date the law sets"), T31 ("the longest legal retention"). What is
  wrong: retention obligations are delegated to an undefined "law"; G0's list of what no
  chain reaches does not include it. Fix: add the law to the assumption register or as
  minting configuration.
- **A1-F10 · low — The DMP-0xx enforcement rules are dangling references.** Where:
  `Enforced by:` lines throughout 00/01/02/10/14 (DMP-001…DMP-021, ~40 references). What
  is wrong: the rule bodies live in CM's `tools/dmp` and are not in this corpus, so the
  enforcement layer of DMP is ungrounded within DMP. Why it matters: the claim "DMP names
  the rules that check it" (00 "The root chain") cannot be verified from DMP alone.
  Fix: vendor the rule list, or mark the pointers as external references to CM.
- **A1-F11 · low — Two different standards of "twice".** Where: 06 "Supernova classes"
  (II-P: "two pieces of evidence that cannot fail the same way", e.g. tests + "a review by
  a session that did not build it") vs 01 "C22" (chains "share nothing they could fail
  together beyond the roots they declare"). What is wrong: a II-P evidence pair sharing an
  author or engine satisfies II-P but not C22's standard; "cannot fail the same way" is
  never tied to the declared-failure-class definition. Fix: align II-P with the words'
  independence definition.
- **A1-F12 · low — Unexplained numbering gap T7–T18.** Where: 01 (section order T0, T37,
  T38, T1…T6, T19…) and "Counts" (which explains retired C numbers only). What is wrong:
  either theorems were merged during distillation (then the parsimony count should say
  so) or the numbers were never assigned (then say that). Fix: one sentence in "Counts".
- **A1-F13 · medium — DMP's own proof standard lives in sections that do not exist.**
  Where: 01 "What a derivation is here" ("An argument becomes a proof when both proof
  chains of chapter 06 carry it: Gravity down from these sentences, Lean up from the code
  (the gravitational wave test)") and G0/T34/C2/04 (references to "the assumption register
  (chapter 06)", "the lemma ledger (chapter 06)") vs 06-black-hole.md (holds only parts,
  Supernova classes, GRB scope files — all draft). What is wrong: the condition that turns
  DMP's "argued" theorems into "proven" ones is specified in absent text. The corpus
  concedes "until then a theorem is argued, not proven", which keeps it honest, but it
  means that by DMP's own standard nothing in DMP is currently proven. Why it matters:
  verifiers cannot check the promotion criterion; the gap is load-bearing for every
  "Enforced by: DMP-021" derivation. Fix: write the two chapter 06 sections, or restate
  the standard inline in 01.

## Questions for the owner

1. (A1-F02) Which is authoritative when they conflict: the stable mark with
   "Enforced by: none yet", or 00's "a defect in DMP, not a rule"?
2. (A1-F03) Is chapter 04's verify table intended to be frozen by C2's laws-file hash
   (then the table must move into the law), or may the draft chapter move independently?
3. (A1-F04) Do the two proof chains' shared root — the DMP text itself — belong to a
   declared failure class of the proof layer, and if so how does that layer keep two
   independent witnesses under the words' definition?
4. (A1-F05) Pre-minting: is the owner-stand-in an instance of the dual gate (then AX1
   holds with the owner as both halves) or a licensed exception outside the axioms?
5. (A1-F06) T27 lets one witness withdraw an admission; T24 dual-gates acts on standings
   "in either direction". Which prevails for admission withdrawal?
6. (A1-F07) Should the VIBE formulas move into DMP (making T32 self-contained), or stay
   Gravity's constant (then T32's zero-characterisation should be stated as conditional)?
7. (A1-F12) Were T7–T18 merged during the 0.9.0 distillation, or never assigned?

## Walls

Work confined to `work/a1r1/` (this report's fragments and `DMP_A1.lean`) and
`out/A1-round1.md`. `src/dmp` read-only; `src/gravity`, `src/im`, other `out/`/`work/`
entries never opened; no installs, no network writes, no git commands in the clones.
