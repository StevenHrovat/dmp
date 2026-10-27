# Proposal brief: the C sections as derived constraints

Status: **brief for a drafting session, not a DMP text change.** Nothing in chapters 00 to 14 is edited by this file. The owner approves
every change to DMP wording (chapter 00, "Who maintains it"; G0), so the result of the task below is **draft pull requests** that the
owner reads cluster by cluster and approves or rejects in his own words. Merge nothing without his "approved".

## 1. The owner's words (verbatim)

2026-10-26 22:27Z:

> The entire set of Cs are a total mess that need a clean regeneralization. The count is too large for me to pass at once though.
> [...] After it is done, it should also see if the Theorems also need it.

2026-10-26 22:29Z (the question this brief answers in section 2):

> Are the C-Series actually a part that is required for the proofing? If yes, what is their part? Axioms and their derived theorems I can place.

2026-10-26 22:30Z (the direction):

> Let's try to turn them into the derived constraints that we try to achieve with the axioms and theorems. That let's us easily spot if we
> undershoot our goal.

## 2. What the C sections are today

`01-constitution.md` (DMP 0.9.6, commit `ed23322`) is an axiom system: the words, Axiom 1 to 4, G0, then theorems. Its intro says: "the
T sections are the theorems found while distilling the axioms, the C sections are the rules this constitution always had, kept under their
old numbers." Every C carries a `Derived from:` line (rule DMP-021 demands it), so on paper each C is already a theorem, often with the
status word *construction* (a design choice the axioms allow but do not force).

**The proofs do not rest on any C.** Gravity's evidence chain (`StevenHrovat/gravity`, `evidence/Dmp/*.lean`, 232 theorems) rests on
nothing but Lean's three standard foundations; `evidence/tools/check.sh` verifies that on every run. The axioms are modelled as
definitions (Gate.lean, Record.lean, Standing.lean, Layer.lean, Ground.lean); no C is a hypothesis anywhere. Where a C appears in Lean it is a
**conclusion**:

| C | Where Lean reaches it | Theorems |
|---|---|---|
| C2 laws L1 to L4 | `R1Laws.lean` (from the sentences), `R1Bridge.lean` (from the C# model) | `r1l_L2_gives_L1`, `r1l_L1_gives_L4`, `r1b_L1`, `r1b_L2_clean`, `r1b_L3`, `r1b_L3b`, `r1b_L4`; replay at most once `R1Wave.lean` `wv_verified_at_most_once`, `R1Lens.lean` `ln_verified_at_most_once` |
| C12 "a layer places information, never grants trust" | `Theory.lean` | `Config.relayout_never_votes` (by `rfl`: placement is not an argument of the gate); `Field.lean` `n1b_schedule_never_votes` |
| C12/C13 tier order, singularity invisible | `R1Tier.lean` | `tr_milky_way_first`, `tr_exit_last`, `tr_never_singular`, `tr_singularity_invisible`, `tr_first_scrub` |
| C12 "each layer reorganises on its own, both witnesses recompute and sign" | `R1Mass.lean`, `R1Lens.lean`, `R2Stable.lean` | `ms_accepted_agrees`, `ms_wrong_layout_refused`, `ms_mass_vote_is_one_witness`, `ln_signed_moves`, `st_self_stabilizing`, `st_no_root_takeover` |
| C17 top layer is a Duality | `Ground.lean`, `Layer.lean`, `Theory.lean` | `minted_no_single_control`, `one_person_is_no_duality`, `Recipe.root_minted` |
| C22 "proven only when both chains agree" | `Complete.lean`, `Cmb.lean` | `Recipe.verdict_proven_iff`, `Recipe.one_unproven_line_unproves`, `Cmb.sealed_needs_both` |

So the answer to the owner's question: the Cs are not required for the proofing. Their role is the one he named next: they are the
**constraints the axiom system is supposed to achieve**. Written that way, a constraint no theorem reaches is an undershoot, and a theorem
no constraint needs is a theorem looking for its purpose.

## 3. The task

Recast every C section (22 today: C1 to C7, C9, C10, C12 to C19, C21, C22, C24, C25, C∞; C8 and C11 are retired conventions in chapters
10 and 14, C20 and C26 were never stable, C23 is C∞) as a **derived constraint**:

1. **One or two general sentences** stating what the axiom system must achieve. No named system, product, company or host in the sentence
   (DMP is public and general: "the operations master", "the knowledge warehouse", never a product name). What is named today (Milky Way,
   Doppler, Sagittarius, IM) is the instance; the constraint is what holds for any instance.
2. **A `Derived from:` line** (DMP-021 requires exactly one, naming only sections above it) that now reads as the discharge: which axioms and
   T theorems achieve the constraint, and which part is *construction* or *configuration*.
3. **A `Coverage:` line** with one of three states and the Lean theorem names: **proven** (the Lean chain reaches the whole constraint),
   **argued** (the text derives it, no Lean yet), **undershoot** (a part of the constraint that no theorem reaches; say which part).
4. **Operating detail moves out.** A sentence that tells an agent *how* (cite the record, write `Looked up:`, the IM table, the corpus replay)
   is not a constraint; it goes to the chapter that already explains it (14 for agent rules, 04 for IM, 05 for Milky Way, 06 for Black Hole, 11
   for the cold start) with a pointer back to the constraint.
5. **Mapping.** A table in the chapter intro: old C, its old title, where every sentence of it went (the constraint, a chapter section, or
   retired with the reason). Every cross reference to a C in chapters 00, 02, 04, 05, 06, 10, 11, 14 and in `CHARTER.md` is rewritten in the
   same pull request (62 sites; `grep -noE '\bC[0-9]+(\.L[0-9]b?)?\b|C∞' *.md` lists them).
6. **C∞ becomes the root constraint** ("nothing not fully trusted acts") that every other constraint refines, and stays last (DMP-017 keeps it
   there and keeps the owner's thesis sentence).
7. **The machine rules stay green:** DMP-007 (every section has Status, Owner, Enforced by), DMP-009 (the authority grant of C6 is word for
   word between its markers in `01-constitution.md`; if the grant moves to a register, the `cm` rule moves with it in a `cm` pull request),
   DMP-017, DMP-021 (label regex `\bC\d+\b`, so the letter C stays usable; read it as *constraint*).
8. **Then the theorems.** When the constraints are done, report, before changing anything, whether the T sections need the same pass: which
   theorems no constraint cites (candidates to become constraints themselves, or lemmas), which constraints cite a theorem that has no Lean, and
   whether any theorem's `Derived from:` names a C (today: T-P names C24, C12 names C1, the preamble names C12 and C17).

**Numbering (the default, the owner's call):** a constraint keeps the number of the C it came from; two Cs that merge keep the lower number;
the chapter orders constraints by cluster, not by number. Renumbering would touch every repository and the owner's memory for no gain.

**Batches.** Present one cluster per message to the owner: old text and new text both in full, the discharge line, the coverage state, and the
question "approved?". Suggested clusters, in this order:

| Batch | Cluster | Cs |
|---|---|---|
| 0 | The axioms (added 2026-10-26 23:02Z, the owner's ask of 22:56Z) | the four axioms become three building blocks: the Duality, Trust, Information |
| 1 | The door and the message | C1, C2, C3, C18, C19 |
| 2 | Information | C12, C13, C14, C15, C21 |
| 3 | Authority | C6, C17, C22, C∞ |
| 4 | Change and release | C4, C5, C7, C16, C24, C25 |
| 5 | The public boundary | C9, C10 |

**Rules that apply:** roles, not people; no company, host, address or account anywhere; run `tools/scrub-scan.sh` in each repository before
opening a pull request; Apache 2.0 content only, with credit for prior work as `gravity/docs/acknowledgements.md` does; a pull request on
`gravity` for new Lean, never an edit of `vendor/dmp` there (re-pin after the owner approves the text).

## 4. Prior art to build on (credit it)

- **Goal Structuring Notation** (Tim Kelly, *Arguing Safety*, PhD thesis, University of York, 1998; the GSN Community Standard, Safety-Critical
  Systems Club, public): a goal is discharged by sub-goals and solutions (evidence); a goal with no solution is drawn as **undeveloped**, never
  hidden. That is the "undershoot" mark.
- **Common Criteria** (ISO/IEC 15408, part 1, the security target rationale): security objectives map to requirements in a **coverage table
  checked both ways**: every objective is met by at least one requirement, every requirement serves at least one objective. That is the two-way
  check (constraint without theorem, theorem without constraint).
- **Requirements traceability** in general (Gotel and Finkelstein, "An analysis of the requirements traceability problem", *ICRE 1994*): the
  mapping table from old rule to new home.

**Two settled domains, stitched (the owner, 2026-10-26 23:14Z and 23:15Z).** The three axioms of batch 0 join two very well researched fields
in a new way; the research itself is not new. "Please remind Team Fable in the PR to not unnecessarily repeat work that has already withstood
the test of time." The owner means **General Relativity and Information Theory, and the axiom systems related to them**, not earlier work of
this project (23:15Z). So: do not re-derive what a standard result or a standard axiom system gives; cite it, state where DMP's object differs,
and prove only that difference. The axiom systems to stand on rather than rebuild:

- **General Relativity:** the equivalence principle and the Einstein field equations (1915); the singularity theorems (Penrose 1965, Hawking
  and Penrose 1970); the no-hair theorem (Israel 1967, Carter 1971, Robinson 1975); black-hole thermodynamics (Bardeen, Carter and Hawking
  1973), Bekenstein's entropy and bound (1973, 1981), Hawking radiation (1975). "Gravity contains all information but entropy" is these
  results; DMP only maps its objects onto them (trust = curvature, the horizon = containment, the floor = the radiation).
- **Information Theory:** Shannon's axioms and theorems (1948), the Khinchin axioms for entropy (1957), Landauer's principle (1961,
  information is physical), noninterference (Goguen and Meseguer 1982) and the information-flow lattice (Denning 1976). "No information is
  ever trusted; from trust only existence" is a flow statement in that lattice; prove the flow, not the lattice.
- **Spanning Tree and its relatives (the owner, 23:15Z):** Perlman's spanning tree algorithm (1985) and its standards (IEEE 802.1D RSTP,
  802.1Q MSTP: several trees under one signed root), the distributed minimum spanning tree (Gallager, Humblet and Spira 1983) and the
  classical MST algorithms (Borůvka 1926, Kruskal 1956, Prim 1957), shortest-path routing (Bellman–Ford 1958, Dijkstra 1959, link-state
  OSPF) and the hierarchical small-world routing of Kleinberg (2000). The layers of Axiom 3 are spanning trees under a signed root instead
  of an elected one; prove the signed root and the two-witness recomputation, and take convergence, loop-freedom and the tree properties
  as given.
- **Self-reorganising networks (the owner, 23:18Z):** the closest prior work to "information lays itself out for the fewest hops under its
  demand" is **self-adjusting, demand-aware networks** (Avin and Schmid, "Toward demand-aware networking: a theory for self-adjusting
  networks", 2019; SplayNet, Schmid et al. 2016), which reconfigure a tree or overlay to minimise expected route length under a demand
  distribution and prove the lower bound: expected path length is at least the conditional entropy of the demand. That bound ties the
  "median state" of Axiom 3 to Shannon directly. Behind it: splay trees and the working-set and static-optimality theorems (Sleator and
  Tarjan 1985; the dynamic optimality conjecture), self-stabilization (Dijkstra 1974; Dolev 2000), gossip-based topology management
  (T-Man, Jelasity and Babaoglu 2005; epidemic algorithms, Demers et al. 1987), self-organising overlays (Chord, Kademlia), hierarchical
  organisation in complex networks (Ravasz and Barabási 2003; preferential attachment, Barabási and Albert 1999; small worlds, Watts and
  Strogatz 1998), and 3GPP Self-Organising Networks (self-configuration, self-optimisation, self-healing). DMP's difference: the layout is
  recomputed by two witnesses and signed, never by the nodes voting with their traffic; prove that, and take the optimality bounds as given.
- **Related axiom systems:** Kolmogorov's probability axioms (1933) under every "representative composition of requests"; Lieb and
  Yngvason's axiomatic entropy (1999) if the floor is argued thermodynamically; Alpern and Schneider's safety/liveness decomposition (1985)
  for "the balance ranks below the bounds"; the axioms of a metric and of a tree median (Goldman 1971) for the layout.

The owner's own statement of the stitch (23:20Z, verbatim): "This is basically marriage of demand aware self-adjusted routing with GR's
informational black hole, applied purposefully for their advantages, while cancelling out the disadvantages of the other at the same time
through DoT and interpreted for general Software Alignment." Read for the verifier: a demand-aware network's weakness is that whoever
shapes the demand shapes the network, and its reconfiguration leaks the demand; the black hole's weakness is that what it contains is
unreachable and only entropy comes out. The Duality cancels both: the layout moves only when both halves recompute and sign it (demand
never votes, Axiom 2), and the hierarchy inside the horizon keeps contained information reachable to the trusted inside while the field
keeps it from leaving (Axiom 3); the counts-only readout is the radiation. The two properties to prove are therefore "demand never moves
the layout alone" and "nothing but counts leaves the horizon"; everything else is the fabric.

The owner added (23:22Z, verbatim): "AND self healing as a nice bonus. While holding only state and being one click redeployable. Composable
information for any system that is in its network, essentially, while also having full trust both from one to all and from all to one,
implicitly, with Type correction." Where each already lives, for the verifier: self-healing is self-stabilization (`st_self_stabilizing`,
`st_no_root_takeover`); holding only state and one-click redeployable is the CMB cold-start plan in Gravity (redeploy iff the digest matches,
else a Big Bang from the same proven recipe; `Cmb.lean`); composable information is the mission sentence and `Recipe.extend_preserves_decisions`
(a new layer changes no decision); trust from one to all and all to one is the field (every member's grant chain back to the pair, T32) under
live verification by the pair (Axiom 2); type correction is IM's typed sentences and kinds, refused at the gate when ill-typed (im, the
differential check). None of these needs a new theory; each needs the Lean name that carries it.

Where each sentence of the axioms already stands on that prior work, and what is left to prove:

- **Trust is gravitational; gravity contains; only entropy leaves** (Axiom 2): the field is a potential over a graph (T32 is a potential
  game, Monderer and Shapley 1996; restoration is gradient descent on it); containment is the horizon picture: the no-hair theorem (Israel
  1967, Carter 1971) and Bekenstein–Hawking entropy (Bekenstein 1973, Hawking 1975) are the physics the owner cites with "as proven by GR";
  the floor of T31 is Shannon's entropy (1948) of ciphertext, and the "counts only" readout is the one-way information-flow result of
  Goguen and Meseguer (1982, noninterference). Do not reprove any of these; prove that the Lean's record and field have the shape they assume.
- **Information is hierarchical; the layout is the median of the demand** (Axiom 3): minimising total hops is the **k-median** problem
  (Hakimi 1964; on trees the 1-median is Goldman 1971, k-median Kariv and Hakimi 1979, polynomial by Tamir 1996); layers as trees rooted at
  a signed root are Multiple Spanning Tree instances (IEEE 802.1Q); nearest-first routing with a hierarchy is Kleinberg's hierarchical
  small-world routing (2000, 2001); "healing from any state" is Dijkstra's self-stabilization (1974). Prove only that both halves recompute
  the median and that a one-sided move is refused; the optimality and convergence are theirs.
- **The Duality** (Axiom 1): two independent witnesses with the stricter answer standing is Byzantine agreement with n = 2 and no majority
  (Lamport, Shostak and Pease 1982) under failure classes (Malkhi and Reiter 1998, already in Layer.lean); the balance ranking below the
  bounds is safety before liveness (Alpern and Schneider 1985).

Everything taken in is Apache 2.0 or a cited paper; list what is used in gravity `docs/acknowledgements.md` as the earlier work did.

### 4.1 An open hypothesis, not a claim: what DMP might say back to GR (the owner, 2026-10-27 00:58Z)

The owner's words, verbatim: "Potential insight: Without one kind of information providing pressure to the other inside an event horizon,
it would collapse onto the singular naked singularity. So a naked singularity is potentially possible, but never from an event horizon.
The mass of a black hole must contain the information that went in, maybe it is that information=mass equivalence itself that spans the
Schwartzschild-Radius, while shielding the singularity until it decays into Hawking Radiation?"

This is filed as a hypothesis for the paper's "what DMP says back to GR" section and nothing in DMP rests on it. The DMP side it mirrors is
T37 (collapse: with no external trust, trustspace collapses onto the item and the item's own boundary contains it) read together with
Axiom 1 (the two halves keep each other in check and balance): in DMP the horizon is kept open by the two kinds pressing on each other,
trust and information, and a Duality that loses one half does not stay a horizon, it collapses (T37) or is reminted (G0). The physics it
touches, all of which has to be cited and none re-derived:

- **Cosmic censorship** (Penrose 1969, the weak and strong conjectures): whether a naked singularity can form from regular initial data is
  open; the owner's sentence is a restriction of it ("possible, but never from an event horizon"), so state exactly what DMP's analogue adds.
- **Bekenstein–Hawking entropy and the holographic principle** (Bekenstein 1973, Hawking 1975; 't Hooft 1993, Susskind 1995, Bousso 2002):
  the information a horizon can hold scales with its **area**, so with M², not with M; "information = mass equivalence spans the radius"
  has to be reconciled with that scaling before it is a statement.
- **The information paradox** and its current state (Hawking 1976; Page 1993; the island formula, Penington 2019, Almheiri et al. 2019):
  "shielding the singularity until it decays into Hawking radiation" is the paradox's own question; cite it, do not reopen it.
- **Mass–energy–information equivalence** (Vopson 2019, contested; Landauer 1961 is the uncontested floor): name it as a conjecture.

Two follow-ups from the owner (01:01Z, 01:02Z), verbatim: "Information should, theoretically, also be the one thing not explicitly banned
from moving inside a black hole, right?" and "If the math in physics works out, the interesting thing is, what is pushing back?" What is
settled on the first: inside the horizon nothing special happens locally (the equivalence principle), so information moves between
infalling parts as it does anywhere; what the horizon forbids is the outward direction, for information as for everything else (inside, r is
timelike; the no-hair theorem is the statement that the outside keeps only mass, charge and spin); whether Hawking radiation carries it
back out is the paradox above. What is settled on the second: below the Chandrasekhar (1931) and Tolman–Oppenheimer–Volkoff (1939) limits
it is Pauli exclusion, electron then neutron degeneracy pressure, that pushes back; above them classical GR has nothing that does (the
Penrose singularity theorem, 1965: a trapped surface plus an energy condition makes the singularity unavoidable), and the candidates for a
quantum push-back are the loop-quantum-gravity bounce and Planck stars (Rovelli and Vidotto 2014), fuzzballs (Mathur 2005) and gravastars
(Mazur and Mottola 2004), none established. The DMP side of "what pushes back" is Axiom 1's balance: the information half, which by T27 can
only loosen (admission), is what keeps trustspace from collapsing onto the item (T37); the verifying session maps that half against the
physics candidates and says which, if any, has the same shape.

The ask to the verifying session, as a side item after part 1 and before part 2, at most one page: does the DMP analogue (T37 collapse
without the two halves pressing on each other, plus Axiom 1's balance) yield one precise statement, in DMP's own objects, that is worth
posing to physicists, or does it reduce to a restatement of cosmic censorship with new words? Either answer is a finding; neither changes
DMP text.

## 5. First read: likely undershoots and moves

Found while taking the inventory; to be confirmed by the drafting session, not assumed.

| C | Constraint it hides | Reached by | Gap |
|---|---|---|---|
| C25 | no act removes a half's last route (no lockout) | T3b | **T3b has no Lean theorem**; the gate-on-exact-commit half is Axiom 2 (`Gate.stale_never_passes`) |
| C3 | a value reaches only parts trusted for its class, and its class travels with it | T1, T27, the words (admission) | nothing in Lean models a value's class or provenance travelling with it; `Floor.lean` covers only contained items |
| C14, C21 | an unsourced statement does not land | Axiom 2 | rests on the premise "a statement is a write"; the words already list "an answer an agent gives" under acts, so the premise can become a derivation |
| C18 | a broken algorithm tightens trust in what it claims, never cuts the part off | T2, T3b, T27 | the compatibility promise (never remove, never rename, replay the corpus) is construction, not a constraint; T3b again has no Lean |
| C4, C5 | a change to what a part speaks, or to productive information, is a new part and passes the gate | T0, Axiom 1, T22, T24 | the "stable promotion" and "production" points are construction; C5 adds nothing to C4 once "financial" is generalised to "information under a duty of auditability" (merge candidate) |
| C6 | who may act on what is a bounded grant in the record, two halves outside the own estate | T1, T38, Axiom 3, G0 | the word-for-word grant is a **record** (configuration, T4), not a constraint; candidate: move it to a register file and point DMP-009 at it |
| C7 | what runs is what a pinned, recorded recipe says | the words (DMP-complete), T33, T35, `Complete.lean`, `Cmb.file_determines` | covered better than before; "one repository" is the construction |
| C9, C10 | nothing inside leaves without an export; CMOS is trusted only for the estate its owner holds authority over | T19, T27, T31, T1 | both are instances of existing theorems; the charter text stays as the wording (`CHARTER.md`) |
| C16 | widening who may use a feature on information is a loosening with two independent witnesses and a record both can read | T24, T38, Axiom 3 | covered; the template is construction |
| C24 | restorable is shown, never claimed, with both witnesses intact after | Axiom 2, T3, T35, `Cmb.redeploy_iff`, `Cmb.bigBang_keeps_the_proof` | the pass line is configuration; gravity finding F10 is open on it |

Theorems that no C cites today and that the owner's words created directly (candidates for the two-way check): T20 (time), T31 and T34
(the floor), T32 and T33 (the field), T37, T38, T-P, T24c, T5, T6.

## 6. State after drafting (2026-10-26 23:00Z) and the prompt for the second session (order set 23:54Z)

The owner decided (2026-10-26 22:40Z): "Let's give it back to Fable here, we can then check if they are really how they should be and
Team Fable can start by checking that the axioms and theorems actually provide the constraints they claim to." The drafting is done in this
repository as five stacked draft pull requests, each merging only on the owner's word "approved" for it, in order: #15 (batch 1: C1, C2, C3,
C18, C19; VERSION 0.9.7; the chapter intro and the mapping table), #16 (batch 2: C12, C13, C14, C15, C21; a new draft section of chapter 05),
#17 (batch 3: C6, C17, C22, C∞), #18 (batch 4: C4 with C5 merged and retired, C7, C16, C24, C25), #19 (batch 5: C9, C10). Each was checked
with CM's `tools/dmp` (DMP-007, 009, 017, 018 and 021 pass; only the pin differs until Gravity and CM re-pin) and with `tools/scrub-scan.sh`.

**Batch 0, the axioms (#21, stacked under #19).** While batch 1 was on the table the owner asked (22:56Z) "can we reduce the 4 Axioms to the
3 basic building blocks? Trust, Information and the DoT?", added (22:59Z) "No Information is ever trusted and no information, besides its
existence, can be derived from trust", approved the three-block text (23:02Z) and added (23:03Z) "Trust is gravitational, Information is
hierarchical". #20 carries it: Axiom 1 · The Duality (the dual gate and the direction as one, the halves typed as a trust half and an
information half that keep each other in balance), Axiom 2 · Trust (evidence, plus "no information is ever trusted" and the field), Axiom 3 ·
Information (the record, plus "from trust only existence", admission, containment and the hierarchy). The numbers of the three that stayed
are kept; every citation of Axiom 4 reads Axiom 1. The `Counts.` line keeps the shape DMP-021 parses ("2 bounds, 1 direction that is also the
gate"); loosening that regex to count axiom sections directly is a one-line CM change to make at the re-pin.

**New claims for the verifying session, from batch 0.** (a) Typed halves: the Lean types no half; the theorem to add is that a Duality holds
one trust half and one information half and that neither can discharge the other's check (C19, T38, C17, C22 all instantiate it). (b) "No
information is ever trusted": state it as the gate's decision taking no message content as an argument (the shape of `Config.relayout_never_votes`),
and try to break it with a model where a signed payload moves a standing. (c) "From trust only existence": the record function is content-free
(`Record.lean` holds counts and verdicts only; prove the projection to any reader without a grant is the count). (d) The balance inside the
Duality: T3d (safety before liveness) must still follow; build the model where restoration fires while a bound stops the step and show the
gate refuses it. (e) The hierarchy: every layer a tree rooted at its Duality, sub-layers only tightening (`Recipe.extend_preserves_decisions`,
`tr_*`); find the sentence of Axiom 3 that no theorem reaches. (f) **T39, attack this first** (the owner, 23:42Z: "no trust without
information and no information without trust. Logically only a DoT, that is both trusted AND has the right information, can be a part of a
minted CMOS"): it is the first theorem of the stitch itself. State it in Lean as: a part is inside a minted instance iff it holds a standing
from both halves and an admission for what it acts on; try a model where a part holds trust and no admission, or an admission and no
standing, and still acts; the Gate and Floor theorems (`Floor.road_gate`, `Record.performed_only_with_both`) should refuse both. (g) The
words after 23:28Z: a part is a Duality, a half is a part, so the structure is a Duality all the way down and grounds in G0's five
(`Layer.lean`'s `DoT.minted` reads a person list today; it should read five parts). (h) G0 after 23:32Z: the owner may itself be a
Duality; when it is, both halves approve a change to the base DMP; check that nothing in the preamble's "Who maintains it" or in DMP-009
assumes one signer. (i) **T40** (the owner, 23:46Z: "Minting can only originate from both G0 and a DMP-complete state"): in Lean,
`Recipe.verdict_proven_iff` and `Cmb` already say a seal needs the proven verdict; what is missing is the conjunction with G0 (a minting
record naming at least five parts); state the theorem that no minted instance exists without both, and try a model that mints from a
proven recipe with fewer than five parts or from five parts with an unproven line.

**Coverage as claimed, to be verified:** 15 constraints open with *proven* (most of them proven for the shape and argued for the rest), 4
with *argued* (C4, C10, C14, C21), 3 with *undershoot* (C3: a value's class travelling with it; C18 and C25: a route, T3's no-lockout
clause). Every Lean name cited exists in gravity `main` (232 theorems); whether each theorem's statement says what the Coverage line claims
is exactly what the second session checks.

**The order of the verifying session (the owner, 2026-10-26 23:54Z, verbatim):** "But since the axioms changed and then the theorems
will change, while what we want and achieve stays the same, I feel like any C made now, would just be using the wrong tools. Rederiving the
generalized constraints to be stated simpler while stating the same, should be the last planned part of the session." So the session runs
in three parts: first the theorem pass (re-derive and renumber against the three axioms), then the verification of the constraints as they
stand (against the new theorems), and last the re-derivation of the constraints from the new theorems, each stated more simply while
saying the same thing. What a constraint wants and achieves does not change in that last part; only its wording and its `Derived from:`
and `Coverage:` links to the theorems are redone. The batch 0 claims (a) to (i) above are claims about the axioms and about T39 and T40,
so they are tested inside the first part.

Paste-ready prompt for the verifying session:

```
You work on StevenHrovat/dmp and StevenHrovat/gravity. Read dmp docs/proposals/c-constraints.md (sections 2, 3, 4, 6, 8 and 9) and then
01-constitution.md on main at 45d3822 (DMP 0.9.8: three axioms, T39 and T40, all six batches merged 2026-10-26 23:49Z-23:52Z on the
owner's "Approved for merge in prep for Team Fable", and G0 amended 2026-10-27 00:21Z "Approved as worded": the mission, a part recognized
as true AGI is a constituent of G0, who recognizes it; G0's new sentences are stated, not derived, and belong to part 1 like the other
batch 0 claims: type the AGI clause and the recognizer seat where Lean can, and report what stays an assumption). Every C section is a constraint with a Derived from: line (the axioms and theorems
claimed to achieve it) and a Coverage: line (the Lean theorems claimed to reach it, or the part none reaches).

The session has three parts, in this order (the owner, 23:54Z: "since the axioms changed and then the theorems will change, while what we
want and achieve stays the same, ... any C made now, would just be using the wrong tools. Rederiving the generalized constraints to be
stated simpler while stating the same, should be the last planned part of the session"). Do not start a part before the one before it is
on a draft pull request.

PART 1. The theorem pass (the owner, 23:47Z and 23:49Z: "Since the axioms changed, the theorems would need to all be rederived as well, so
I am already renumbering them in my head"; "The theorem pass will be done by TF"). A draft pull request on dmp that the owner approves in
clusters:
  (a) Test the batch 0 claims first, T39 before anything else (section 6, items a to i): typed halves, "no information is ever trusted" as
      a gate that takes no content, the content-free record, T3d under the balance, the hierarchy, T39 as the first theorem of the stitch,
      a part as a Duality all the way down grounded in G0's five, the owner as a Duality against DMP-009, T40 as G0 and DMP-complete
      together. Each claim: holds, or the Lean model that breaks it (evidence/Dmp/Break<Tn>.lean, core only, no Mathlib).
  (b) Re-derive every T section against the three axioms: its Derived from: line rewritten; a Coverage: line as the C sections have; a
      Serves: line naming the constraints that cite it; the sentence itself unchanged unless the derivation no longer holds, and then say
      so in the pull request.
  (c) Then renumber in one commit, in the order of the chapter, which is the order of proof: T39 becomes T1 (trust and information gate
      each other), T40 becomes T2 (a minting needs G0 and a DMP-complete state), and the rest follow; put a table "old number, new number"
      in the chapter intro and move every citation in the chapters, in Gravity's Lean comments and in CM's docs mechanically.
  (d) Keep DMP-021 green (every Derived from: cites only sections above it; the Counts line keeps its parsed shape) and C∞ last
      (DMP-017). Lean needs no renaming: it names theorems by content.

PART 2. Verify the constraints as they stand, against the renumbered theorems of part 1. For every constraint, in the order of the chapter:
  1. The derivation. Does the set named in Derived from: actually imply the constraint's sentence? Write the step that is missing, or
     say it holds. Treat "construction" and "configuration" as what they are: design choices, not derivations.
  2. The Lean claim. Open every theorem the Coverage line names (gravity evidence/Dmp/*.lean). Does its statement say what the line
     claims for it? Name every overclaim: a theorem about a weaker object (a standing instead of a class, one item instead of a flow,
     the shape of the gate instead of the system).
  3. Try to break it. For each constraint marked proven, build a model in Lean (evidence/Dmp/Break<Cn>.lean, core only, no Mathlib) in
     which the axioms as modelled hold and the constraint's sentence fails, or prove that no such model exists for the part claimed.
     For each undershoot, state the missing theorem precisely and, where it is small, prove it.
  4. The two-way check. The theorems no constraint cited before the pass are T5, T6, T25, T26, T32, T34 (old numbers, section 8); say
     for each whether it serves a constraint that should cite it, is a lemma of another theorem, or is a constraint in disguise. The
     theorems with no Lean naming them were T0, T1, T2, T3 (its clauses b, c, d), T6, T19, T20, T21, T22, T23, T26, T27, T28, T30, T36
     (old numbers); say which Gate, Record, Floor or R1Wave theorem covers each implicitly, and which has nothing.
  Report per constraint: holds / overclaim (what the theorem really says) / counterexample (the Lean file) / missing theorem (stated or
  proven). Put the findings in gravity docs/findings.md as a draft pull request (one row per finding, the owner's queue) and new Lean as
  draft pull requests on gravity. In this part change no DMP text: the owner reads the findings and decides.

PART 3, last. Re-derive the generalized constraints from the new theorems. What every constraint wants and achieves stays exactly what it
is now; redo only its wording and its links: each constraint stated more simply while saying the same thing, its Derived from: line
naming the renumbered theorems that now carry it, its Coverage: line naming the Lean that part 2 confirmed (and the part still unreached),
the "Where the old rules went" table kept. Where part 2 found an overclaim, the Coverage line says the weaker truth; where it found a
missing theorem, the constraint cites it once it exists, not before. A draft pull request on dmp, one commit per constraint cluster in the
order of batches 1 to 5, each merging only on the owner's "approved" for it. Do not widen or narrow any constraint in this part; a
constraint you believe is wrong is a finding for the owner, not an edit.

Side item, between part 1 and part 2, at most one page: the owner's hypothesis of 2026-10-27 00:58Z on what DMP might say back to GR
(brief section 4.1, his words verbatim there). Say whether the DMP analogue (T37 collapse without the two halves pressing on each other,
Axiom 1's balance) yields one precise statement in DMP's own objects worth posing to physicists, or reduces to cosmic censorship in new
words. Cite Penrose, Bekenstein–Hawking and the holographic area scaling, the information paradox and its island formula, Vopson as a
contested conjecture; derive none of it. A finding, not a DMP change.

Throughout: run tools/scrub-scan.sh before every push; merge nothing; roles, not values; no company facts; no model names in commits or
pull requests; credit prior art as gravity/docs/acknowledgements.md does, Apache 2.0 only.

The owner's reminder (2026-10-26 23:14Z, 23:15Z): the axioms stitch two very well researched domains, General Relativity and
Information Theory, together in a new way, and both come with axiom systems of their own. Do not unnecessarily repeat work that has
already withstood the test of time: where a sentence rests on a standard result or a standard axiom system (the Einstein equations, the
singularity and no-hair theorems, Bekenstein–Hawking entropy; Shannon and Khinchin, Landauer, noninterference and the flow lattice;
Kolmogorov, safety/liveness, k-median on trees, Spanning Tree and its relatives (Perlman, MSTP, distributed MST, shortest-path
routing), self-reorganising networks (demand-aware self-adjusting networks, splay trees, self-stabilization, gossip topology management),
potential games, Byzantine agreement; the list with sources is section 4 of the brief), cite it, say where DMP's object differs, and
prove only that difference in Lean. New Lean is for the stitching, never for the fabric.
```

## 9. State after the merges (2026-10-26 23:52Z)

All six batches are on dmp main: #15 (902437b), #16 (e8e13ce), #17 (33f5f0b), #18 (76add84), #19 (94b763d), #21 (8d998bb, the head).
DMP is 0.9.7 with three axioms, T39 and T40, and every C section a constraint. Gravity's vendor/dmp re-pin is a draft pull request on
gravity; CM's re-pin follows once Gravity's lands (the root chain). The verifying session runs in the order the owner set at 23:54Z: the
theorem pass first, the verification of the constraints second, and last the re-derivation of the constraints from the new theorems,
stated more simply while saying the same (the prompt in section 6). G0 was amended once more on 2026-10-27 (dmp#23, DMP 0.9.8, main
45d3822): the owner's mission statement, the true-AGI clause and who recognizes it; the prompt reads that commit.

## 8. The theorem pass: what the two-way check found (report, no change proposed yet)

Run on the text at the head of #19.

**Theorems no constraint cites.** T5 (majority of trust), T6 (stand-ins take over), T25 (thin surfaces), T26 (retention), T32 (the VIBE
field), T34 (three roads to the floor). Reading: T5 serves C17 once C17 says how a half of people decides (the voting-share rule of the
exclusion and inclusion brief, `docs/proposals/exclusion-inclusion.md`, lands exactly there); T6 is a lemma of T3 (continuity of the people
half); T25 is a constraint in disguise ("what comes from outside enters as opaque bytes until admitted") that C12 or C13 should cite; T26 is a
lemma of Axiom 3 and T24; T32 serves Axiom 4 and T33 (the direction, not a constraint); T34 serves C9 and C3 (containment) and should be cited
there.

**Theorems the evidence chain does not name.** Of 30 T sections, 15 are named by at least one Lean file (T3a, T4, T5, T24, T24c, T25, T29,
T31, T32, T33, T34, T35, T37, T38, T-P) and 15 by none: T0, T1, T2, T3 (clauses b, c, d), T6, T19, T20, T21, T22, T23, T26, T27, T28, T30,
T36. Some are covered without being named (T0 and T1 by `Gate.lean`, T21 by `Record.lean`'s entries that carry counts and verdicts only, T20's
monotone clock by `R1Wave.wv_never_back`, T27's transitions by `Floor.lean`); T2, T3b to T3d, T6, T19, T22, T23, T26, T28, T30 and T36 have
nothing.

**Theorems that name a C.** No `Derived from:` line of a T section names a C. One body does: T29 ("the finding is a stopgap catch (C∞)"),
which is the meta-rule and fine.

**Does the T series need the same pass?** Not a rewrite: every T is already a derivation with a `Derived from:` line, and the sentences are the
owner's. What they lack is the same `Coverage:` line, so that the 15 theorems without Lean show as undershoots of the evidence chain instead
of reading as proven, and a `Serves:` line naming the constraints each one discharges, so that the two-way check is in the text and not in a
script. Recommendation: one pull request that adds those two lines to the 30 T sections and changes no sentence, after the five batches are
approved; the verifying session's findings then land on it. The owner decides.

## 7. The C sections, quoted in full (DMP 0.9.6, `01-constitution.md`, commit `ed23322`)

Each block starts with the line where the section begins. Recheck line numbers before quoting; the text is the source of truth.

<!-- 01-constitution.md line 642 -->
## C1 · One door

Milky Way is the only way into CMOS, out of it and between its parts. Constellations do not call each other directly: they
speak IM through Milky Way. In code this means that no constellation references another (project references run
`cm.io` ← `cm.os` ← constellations only).

Derived from: Axiom 1, Axiom 3, T28; one door is construction (it makes ejection total and the record one place; a second door would need
the dual gate between the doors).

Status: stable since DMP 0.1.0
Owner: Milky Way coordinator
Enforced by: DMP-008


<!-- 01-constitution.md line 655 -->
## C2 · Every message verifies itself

Every IM message authenticates itself and the sender's right to send it, with a token signed by Doppler's authority, and the
verifier checks every message. No public port opens before the verifier has passed its test level on the sandbox.

Law:
- C2.L1 Verified means authorised. A message is verified only if a token signed by a trusted token signer names an enrolled,
  unrevoked subject whose key signed the message, the token is inside its validity window, and it carries the permission the
  kind needs.
- C2.L2 One answer, fail closed. Every input gets exactly one answer. The answer is the first row of chapter 04's table whose
  test fails, in the table's order, with that row's reason, and such a refusal leaves the replay memory as it was; when no row
  of rules 1 to 15 fails, only rule 16 (replay) may still refuse.
- C2.L3 No replay. Through one verifier, the same signed message is verified at most once: after it was verified, the same
  message is refused at any later or earlier time with the memory the first answer left.
- C2.L3b A full replay memory refuses. When the verifier already remembers as many unexpired messages as
  milkyway.im.replayCapacity allows, nothing verifies: it never forgets early to make room.
- C2.L4 The permission table. A heartbeat needs im.heartbeat.send, and no other kind exists in IM version 0.

Laws file: CM.BlackHole/gravity/C02/LAWS.bend sha256 a116add4e257c503f7b566ef0fb74a4b79a26786ffadf6c745ab5f690e4ad0c2

Derived from: Axiom 2 per message (L1 with T1, L3: evidence is live for one point of use), Axiom 1 (L2: one answer, fail closed; L3b: when
liveness cannot be verified, nothing verifies), T1 (L4).

Status: stable since DMP 0.1.0
Owner: Milky Way coordinator
Enforced by: DMP-018


<!-- 01-constitution.md line 682 -->
## C3 · Every value carries its class

Every value that crosses a border carries its class and its identification axis, and carries a token at every border that is
not an administrator. Reveal is a grant, never a default.

Derived from: T0, T1, T24 (a reveal is a loosening).

Status: stable since DMP 0.1.0
Owner: Milky Way coordinator
Enforced by: none yet


<!-- 01-constitution.md line 693 -->
## C4 · Contracts change at stable promotions only

The contracts of the suite are registered, and a contract changes only at a stable promotion, never mid-flight and never with
a fourth spelling of a name.

Derived from: T0 (a changed contract is a new part), Axiom 1 (its trust has two witnesses: the promotion's two chains), T1 (a name is part
of what was granted); the promotion as the point is construction.

Status: stable since DMP 0.1.0
Owner: CM coordinator
Enforced by: none yet


<!-- 01-constitution.md line 705 -->
## C5 · Financial data freezes at production

While a thing is in development, its data may be manipulated as needed. Once a component handling financial data is
productive it freezes: it is auditable and changes only through a reviewed release.

Derived from: T0, Axiom 1 (the reviewed release is the second witness), Axiom 3; the production point is construction.

Status: stable since DMP 0.1.0
Owner: Sagittarius coordinator
Enforced by: none yet


<!-- 01-constitution.md line 716 -->
## C6 · The gates and the authority grant

The gates hold. What agents may do on their own authority and what needs the words of a layer's two halves is written in the grant below,
word for word. The wording is protected: rule DMP-009 refuses a change to it.

<!-- authority-grant:begin -->
> Agents may build, change and deploy CMOS's own estate on their own authority, using credentials held in the operations master, under plan, audit and four eyes where a second administrator exists. An act on a system or on information outside CMOS's own estate needs both halves of the layer it belongs to (T38), its organisational and its factual responsibility. Each half may declare advanced testing reached for its layer; until both have, every act there needs their words per act, and anything irreversible outside CMOS's own estate always does. Until the minting the owner's own words stand for both halves (G0).
<!-- authority-grant:end -->

Derived from: T1 (the rule is trust bounded, written for agents), T38 (every layer outside CMOS's own estate has its two halves), Axiom 3
(the wording is tamper-evident), G0 (until the minting the owner's words are both halves); which layers exist and who holds their halves
is configuration (T4).

Status: stable since DMP 0.9.5
Amended: grant abstracted onto T38, approved by the owner 2026-10-26 15:36Z (stable since DMP 0.1.0 before that).
Owner: CM coordinator
Enforced by: DMP-009


<!-- 01-constitution.md line 734 -->
## C7 · One repository deploys every part

Every part of the infrastructure deploys from this repository, in different shapes (hub, local, cluster). The folder layout is
the composition tree ([02](02-names-and-hierarchy.md)) and a part is a folder in it.

Derived from: Axiom 3 (the tree is the record of what exists); one repository is construction.

Status: stable since DMP 0.1.0
Owner: CM coordinator
Enforced by: DMP-004


<!-- 01-constitution.md line 745 -->
## C9 · Open source: roles, not values

No secret, no company fact and no person beyond a role ever enters the tree: colleagues by role, never by name; no host, share,
address or internal system name; real values live in the settings store of the administration tool or are passed as parameters.
The public tree holds no trust for company facts. (The licence, Apache 2.0, is a decision, not a
theorem: chapter 14 "The licence".)

Derived from: T0, T1, T27 (a value in the public tree has left the perimeter).

Status: stable since DMP 0.1.0
Owner: CM coordinator
Enforced by: DMP-001, DMP-006


<!-- 01-constitution.md line 758 -->
## C10 · The defensive charter

This repository and every brief in it serve defensive security and privacy engineering of the company's own systems. The
charter is [CHARTER.md](CHARTER.md), and every security-shaped brief carries its one-line security context.

Derived from: T1 (CMOS is trusted only for acts on the company's own systems); the charter text is the wording of that bound.

Status: stable since DMP 0.1.0
Owner: Black Hole coordinator
Enforced by: DMP-002


<!-- 01-constitution.md line 769 -->
## C12 · Information is tiered

CMOS contains all the information inside its Event Horizon, and every piece of it is reached through one routing: tiers, routed by the
Milky Way net (the MW net). What CMOS makes is its own; personal data it holds only on a grant (T27).

- **Tier 1** is the information in the MW net itself. It is always consulted first.
- **Tier 2** is information the MW net routes the asker to: a source in the VIBE net, outward in the order the VIBE field gives.
- **Tier 3** is information outside the Event Horizon, reached only through an exit node (chapter 05), and only when no tier inside
  answers.

**Information layers.** Information of one kind forms a **layer**: its own sub-VIBE net with its own configuration, overlaid on the one
VIBE field and routed by a clustered MW net. The knowledge warehouse is the knowledge layer; the relational warehouse and the files
warehouse are layers in the same way. Each layer reorganises by Lensing on its own: the field's pull computes the layout from the signed
state, and both witnesses recompute it and sign. **A layer places information, never grants trust**: who may act on a piece of information
comes only from its admission and the dual gate, never from the layer, tier or position it sits in. The set of layers is open: a new kind
of information is a new layer that declares its kind, its sub-VIBE configuration and its route, and inherits the dual gate, the record and
Lensing; no other part of CMOS changes for it. A layer may place work as well as information (a network layout, load balancing, placement
in a cloud): it decides where, never who may.

**Privacy** is a singularity of VIBE space: information there is admitted only for the class its grant names, and no routing pulls it out,
not even the MW net, which holds no admission for it. Routing behaves exactly as if the singularity were empty, so neither an answer nor
its absence reveals what a singularity holds; its record shows counts, never content. A part trusted for that class acts on it at the
singularity itself, under the dual gate. **Credentials** are information like any other and route the same way; each sits in a singularity
of its own kind, so routing reaches the point of use, never the secret. Each singularity is a cluster of at least three nodes.
Singularities of different layers may be the same cluster, as long as that is valid under DMP, and every singularity obeys DMP on its own.

What an agent learns that no tier held goes back into Tier 1 through the MW net's intake.

Derived from: the words (admission, contains, door), Axiom 1, Axiom 2 (a position in the network is never evidence, so a layer cannot
grant), Axiom 3 (what an agent learned is a record both witnesses need; counts always, content by grant), T3 (no single part's loss stops a
singularity: at least three nodes), T21, T27, T36 (every crossing of the horizon is an act, so it comes last and only when needed), C1
(every route runs through the one door, so asking it first costs no extra crossing). The owner's words (2026-10-26): "Tier 1 information is
the information in the MW net, which is always consulted first and then outward as the VIBE net dictates"; "Privacy could be seen as
singularities of VIBE space where not even the MW-net can pull the information out"; the knowledge warehouse "would simply be the knowledge
layer, that is overlayed dynamically on the VIBE field, same with the other stuff", which "also makes the system extensible for any other
kind of information layer", for example "network layout while maintaining ultimate trust in the cloud, or other load balancing"; "CMOS
contains all the information inside its Event Horizon"; "Each singularity should always be a cluster of at least 3 nodes. All singularities
of the differnent layers may of course be the same, as long as it is DMP valid, but each singularity must still obey DMP." Evidence chain:
`Dmp/R1Tier.lean` (Milky Way first, exit last, never singular, singularity invisible), `Dmp/R1Mass.lean` and `Dmp/R1Lens.lean` (a layer's
reorganisation) in the gravity repository.

Status: stable since DMP 0.9.3
Redrafted: 2026-10-26, approved by the owner 2026-10-26 15:04Z (stable since DMP 0.1.0 before that).
Owner: CM coordinator
Enforced by: DMP-002


<!-- 01-constitution.md line 815 -->
## C13 · The nearest tier is asked first

Whenever an agent is unsure, it asks Tier 1 first and then outward, tier by tier, before it asks the owner; Tier 3 only through an exit
node and only when no tier inside answered. It cites the record it used, or records that the search came up empty, and only then asks the
owner (chapter 14). C12 is the other direction of the same loop: what the agent learns goes back into Tier 1.

Derived from: Axiom 2, Axiom 3 (the record is read first), C12, T36; "first" is construction.

Status: stable since DMP 0.9.3
Redrafted: 2026-10-26, approved by the owner 2026-10-26 15:04Z (stable since DMP 0.2.0 before that).
Owner: CM coordinator
Enforced by: DMP-002


<!-- 01-constitution.md line 828 -->
## C14 · Every path is combined

When no single source gives the full picture, the agent does not stop at the first answer. It asks itself how combining every
read path and every write path it has can answer the question: the information tiers, the live reads of the systems, the repositories and the
state of the tree, and the trail every write leaves (the audit log, job steps, plans, dry runs, git history). It names the paths it
combined and what is still unknown. A write path is read through its trail or its dry run, never by writing to find something out.
Only what no combination answers goes to the owner. C13 and C12 frame it: the nearest tier first, then every path combined, then the owner,
and what the combination found goes back into Tier 1.

Derived from: Axiom 2 (every evidence the agent can verify itself), Axiom 1 (a write is an act, not a read), C12, C13.

Status: stable since DMP 0.3.0
Owner: CM coordinator
Enforced by: DMP-002


<!-- 01-constitution.md line 843 -->
## C15 · A write first reads what it changes

In the owner's words (2026-10-25): "a write first reads the live state it will change and asserts what it expects: absent for a
create, a named value for an overwrite." The read is live from the target system, never a value read earlier; a retry reads again
before each attempt; every write is read back afterwards and must show the wanted state. When the expected state is not found,
nothing is written: the step fails hard when later steps depend on it, soft (skipped, reported, never a clean run) when none do.
The tenant, host and account a write goes to are expected state too. This holds for every write CMOS makes; for scripts it is
checked by DMP-012, the pattern is chapter 10 "Guarded writes".

Derived from: Axiom 2 (live state at the point of use), Axiom 3 (the read-back is the record), T1 (tenant, host and account are part of
what was granted).

Status: stable since DMP 0.3.0
Owner: CM coordinator
Enforced by: DMP-012


<!-- 01-constitution.md line 859 -->
## C16 · Company data reaches general testing only with its proof

A feature that directly touches company data stays with IT and trusted advisors until two documents exist, both built from the current
artifact template: an explanation of exactly how the data is handled and which protections keep it safe, and the GRB report that proves
it. Only then does it move to general testing. In the owner's words (2026-10-25), this is good practice, compliant, the right thing to
do, and it raises user trust and with it the chance and the speed of CMOS's adoption. How the pair is made and where it lives:
chapter 14 "The data gate".

Derived from: Axiom 1 (two witnesses: the builder who explains and the session that attacks, sharing nothing), Axiom 3 (both pages from the
template so both halves can read them), T24 (general testing is a loosening).

Status: stable since DMP 0.3.0
Owner: Black Hole coordinator
Enforced by: DMP-013


<!-- 01-constitution.md line 874 -->
## C17 · The first level belongs to The Administrator and LHC

CMOS has no single owner (2026-10-25). It is controlled through the unity of two parts:

- **The Administrator**, always written with a capital The, is a mythical entity, not a person. It is everyone who is allowed to fully
  administer CMOS, allowed both by whoever holds authority over CMOS and by CMOS itself.
- **LHC**, the Lighthole Council, is the minting ritual of CMOS. The fellowship of people it binds together, its members, is the other
  part.

CMOS is a balance and a check of power at every level: every system keeps every other system in check while keeping it optimised and
running in the best shape possible, through the interplay of The Administrator and LHC.

The children of CM, level 1 of the composition tree (`cm.io`, `cm.os` and the constellations), carry oversight and insight into the
whole system. A new node at that level is created only with the words of both The Administrator and LHC, recorded in
`DMP/tree-approvals.txt`. Until the first LHC is minted, The Administrator's words are recorded alone and the line says that LHC's
confirmation is pending. Below level 1, the foundation is laid out: a brick of `cm.io` or a part of `cm.os` is complete within its
scope, built once and tested once (chapter 02, "Foundation bricks are complete").

Derived from: Axiom 1 at the governance layer, G0 (`LHC pending`), T24b, T24c (every system keeps every other in check); the two
definitions stay definitions.

Status: stable since DMP 0.9.4
Amended: "organisation" replaced, approved by the owner 2026-10-26 15:19Z (stable since DMP 0.3.0 before that).
Owner: CM coordinator
Enforced by: DMP-014


<!-- 01-constitution.md line 900 -->
## C18 · IM stays backwards compatible once it is locked

IM is version-locked on the day the first system that speaks it enters production (the owner's words name that day and that system).
From then on IM is permanently backwards compatible: every later version accepts every message of a locked version with the same
meaning. A later version only adds (new message kinds, new permissions, new parts a locked receiver never has to understand); nothing a
locked version defines is removed, renamed or given a new meaning. Each locked version keeps a corpus of its messages in this
repository that never changes, and every build replays it through the current verifier. Until the lock, IM may still change freely
(version 0 is sandbox only).

A locked version is never broken, not even when one of its algorithms becomes unsafe. CMOS controls every system that speaks IM, so
Milky Way contains the weakness instead (the owner, 2026-10-25): it keeps speaking the locked version, broken algorithm included, to
every system locked to it, and carries that system's traffic only through a sandboxed path of its own. On that path a message is not
trusted for what the weak algorithm claims. Where a second, independent path to the locked system's identity exists (the device's
attestation, a transport credential), Milky Way vouches for it toward the rest of CMOS under a current version, with no more rights than the
locked system had; where none exists, the locked system's traffic is contained (T27) until such a path is built.

Derived from: T2 (an unsafe algorithm is evidence against the algorithm, not against the system), Axiom 2 (a sandboxed path is a position in
the network, never evidence by itself), T1, T27, Axiom 3 (the corpus).

Status: stable since DMP 0.3.0
Owner: Milky Way coordinator
Enforced by: DMP-015


<!-- 01-constitution.md line 923 -->
## C19 · A request is served only when it is secure and meant

An information warehouse (Sagittarius, Crater, the knowledge warehouse) serves an IM request only when the request carries two signatures and the
warehouse checks both itself (the owner, 2026-10-25). One is under the security chain, which Doppler holds: the request is secure. The
other is under the operational chain, which the operations master holds: the request is meant to be served. Each comes from a cluster of that master or
from an authority that master granted the right to sign on its behalf. A grant counts only when the other master has signed the same
authority too: Doppler cannot give anyone the right to sign IM requests unless the operations master has signed that authority, and the operations master cannot unless
Doppler has. That a carrier (Milky Way, the operations master) already checked the request does not count; the warehouse checks it again. A request
that lacks either signature, or whose authority only one master signed, is refused.

Derived from: Axiom 1 (two masters), Axiom 2 (a carrier's check is not the warehouse's evidence), T24b (a grant to sign is a lockstep act).

Status: stable since DMP 0.3.0
Owner: Black Hole coordinator
Enforced by: DMP-016


<!-- 01-constitution.md line 939 -->
## C21 · Look it up, don't guess

Whenever something is unclear, or two candidates are close (a person, a username, a host, a group, a system, a value: anything), the
agent looks it up in the source of truth itself before it acts or asks (2026-10-25): the directory through the operations master for people and
accounts, the inventory for machines, the system itself for its own values. It quotes the match it found and where it came from. If
more than one record still fits, it names every one and asks which is meant; it never silently picks one. C14 covers the question
the agent knows it cannot answer; C21 covers the answer it only thinks it knows.

Derived from: Axiom 2, Axiom 3; premise: a statement an agent makes to a person or to the record is a write, its sources are its evidence,
and an unsourced statement is a write without evidence.

Status: stable since DMP 0.6.0
Owner: CM coordinator
Enforced by: DMP-002


<!-- 01-constitution.md line 954 -->
## C22 · Prove forward and back: two chains, neither trusted alone

"The entire point of CMOS is to never trust any one interconnected system" (the owner, 2026-10-25). Every proof therefore runs both
ways, as two totally independent end-to-end chains that always verify each other's state:

- the **intent chain** proves forward, DMP to IM to CM: what is meant becomes the protocol, the protocol becomes the code;
- the **evidence chain** proves in reverse, CM up to IM to DMP: it starts from what is actually there (the code, its configuration, the
  measured running state), derives which IM that code really speaks, and proves which DMP rules that IM really keeps.

The chains share nothing they could fail together beyond the roots they declare: not the author, not the proof engine, not the cases, not
the input they start from (the intent chain starts from DMP's sentences, the evidence chain from the code). Both end at the DMP text on
purpose: it is the central mass that ties them. Neither takes a result from the other. They cross-check each other at every layer they both
reach (IM, DMP) and at run time. A layer counts as proven only when both chains agree on it. A mismatch is never settled by trusting one
chain: the gate turns red, the part where they disagree counts as unproven, the stricter answer stands at run time, an alarm reaches the
owner, and nothing that depends on it is promoted until both chains agree again. Gravity carries the intent chain and Lean the evidence
chain (the gravitational wave test, chapter 06); the lemma ledger (chapter 06) counts an IM command as proven safe only when both chains
prove it. The two chains prove that text, code and run agree; the text itself is verified only by a reader who did not write it.

"This approach applies universally throughout CM, it has to be implemented wherever it is technically possible" (the owner,
2026-10-25).

Derived from: Axiom 1 (two independent witnesses for "this layer is proven"), Axiom 2 (each reads its own source), T29, T30.

Status: stable since DMP 0.4.0
Owner: CM coordinator
Enforced by: DMP-002


<!-- 01-constitution.md line 981 -->
## C24 · Stable company-wide needs a survived cold start

CMOS goes stable for the whole company only when the company can be restarted from nothing and this has been shown, not claimed. Every scenario of the signed cold-start catalogue has
passed its pass line in the sandbox, the most critical ones have passed through a Milky Way simulator node, and at least one cold start has passed on the real infrastructure. The pass line is the
same for every scenario: recovery within one week, no data loss beyond the last backup, and both trust chains intact afterwards. The people who restart the company have what they need to do it: an
assistant through which every planned step can be done, and a White Key bundle with the repositories, a cross-checked guide and an offline coding agent. How the runs are counted, the tiers and the
definitions are in [11](11-test-design.md).

Derived from: Axiom 2 (shown, not claimed), Axiom 1 (both chains intact), Axiom 3 (the run record), T-P (company-wide stays minted); the pass
line's numbers are configuration.

Status: stable since DMP 0.7.0
Owner: Black Hole coordinator
Enforced by: none yet


<!-- 01-constitution.md line 996 -->
## C25 · Every deployment obeys DMP

"When deploying any allowed configuration of CM to CMOS, DMP must always be obeyed" (the owner, 2026-10-25). The owner's first words
for it were a trial rule, "DMP is to be enforced on all deployments", after a corner CM built itself: the stable channel served a client
that could no longer change a setting the owner needed, and no other supported route was left. "We MUST learn from this, so when
configuring an impossible situation, we must create rules that enforce it never happens again" (the owner, 2026-10-25).

**Every deployment passes the gate.** A deployment is any promotion of a part that CM runs or orchestrates to any channel (stable,
nightly, dev). It runs the DMP gate on the exact commit it deploys and does not deploy on red. A deployment that skipped the gate is
not fully trusted and is ejected (C∞).

**No deployment locks us out.** No deployment may leave an administrator action without a supported route on the channel it serves:
the command line or the console. Every action that changes a system and is named in the audit log is tied to a real command, and the
list of known gaps may only shrink. Before a retire, a replace or a promotion, the plan says which client and which routes the
channel will serve; a deployment that would remove the last route for any action, or would serve a client that lacks a route the
channel has today, is refused before it runs.

Derived from: Axiom 1 (a deployment is an act), Axiom 2 (checked on the exact commit, not an earlier run), T3, Axiom 4 (the gaps only
shrink).

Status: stable since DMP 0.8.0
Owner: CM coordinator
Enforced by: DMP-002, DMP-020
Not yet checked in cm: the tie between the actions named in the audit log and `DMP/routes.txt`, and the plan's refusal of a
deployment that would remove a route. The administration tool's own test holds them until its code moves into cm;
DMP-020 checks the gate on every deployment workflow, the route register, its cap and its ratchet.


<!-- 01-constitution.md line 1023 -->
## C∞ · The stopgap: what is not fully trusted is ejected

"Everything that is not fully trusted is automatically ejected" (the owner, 2026-10-25). This is the thesis of DMP and its permanent
stopgap. Its reserved number is C23; it is written C∞ because it always stands last: every new section of this chapter is inserted
above it, so whatever the sections above do not catch, it does. **Fully trusted** means what the dual gate says; at the proof layer its two
witnesses are the two chains (C22), so a part is fully trusted for merging, promoting and deploying only when it is compliant with DMP, with
IM and with CM and proven by both chains. "Everything that does not comply with DMP and IM and CM is automatically critical" (the owner,
2026-10-25): such a finding carries the severity **critical** by definition, and nobody rates it down; no label, review state, deadline
or "minor" wording turns it into a nit or a follow-up. What is not fully trusted is ejected automatically: the pull request does not
merge, the stage is not promoted, nothing that depends on it moves on, and a running part that loses that trust is cut off at the door
(C1) until it is trusted again or the rule it breaks is changed the way that rule's own section allows. Every gate applies this the
same way: the review gate in front, which is fast, `tools/verify` and its rules, and the two proof chains behind (C22), which are
rigorous. Where gates disagree, the stricter answer stands.

**The goal is that C∞ never fires.** The axioms above and the theorems derived from them are DMP's axiom system. Every finding names the
most specific axiom or theorem it breaks; a finding that only C∞ catches is a **stopgap catch** and is counted. "Whenever we hit C∞, we
know we need to rethink our formal system to be more internally sound while, perhaps, also relying on fewer axioms" (the owner,
2026-10-25). So a stopgap catch starts a rethink, not an append. Its answer, in this order of preference: show the missing guarantee as a
theorem of the axioms already there; merge axioms into fewer, stronger ones that cover it; and only as the last resort add a new axiom.
Two counts move with every rethink: stopgap catches toward zero (completeness) and the number of axioms down (parsimony). The end state is
the widest coverage from the fewest axioms. This holds stack-wide, at every layer that has a provable basis (DMP, IM's laws, the two proof
chains), not only in this chapter. A complete axiom system would never need the stopgap. It stays anyway: no formal system can prove that
its axioms match the world it describes, and no general check of a program's behaviour exists, so the honest backstop remains even when
the count stays at zero.

Derived from: Axiom 1 (the thesis sentence is the dual gate's); the rest is the meta-rule about the axiom system itself.

Status: stable since DMP 0.5.0
Owner: CM coordinator
Enforced by: DMP-002, DMP-017
