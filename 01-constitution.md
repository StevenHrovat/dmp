# 01 · Constitution

The rules that are true from the first day and do not bend. Every section is stable. A pull request that breaks one is
refused; the owner of the framework alone decides to change this chapter (until the first minting the owner's words stand for both
halves of the Duality, G0).

**How this chapter is built (DMP 0.9.0).** The owner asked (2026-10-25 19:38Z) for DMP to be reduced to its axioms about trust: "every
axiom just has to state how trust relates to the system ... if we can define trust, we can define all other theorems from it." So the
chapter is an axiom system. It opens with **the words** (names only; a definition forbids nothing), then the **three building blocks** as
three axioms (the Duality, Trust, Information; until DMP 0.9.7 they were three bounds and one direction, see "The three building blocks"
below), then **the ground** G0 (the minting, stated, not derived). Everything after
that is a **theorem**: the T sections are the theorems found while distilling the axioms, the C sections are the **constraints**. Every
theorem carries a `Derived from:` line that names only axioms, G0, the words and sections above it, so the order of the chapter is the order
of proof (rule DMP-021). C∞ stands last, as it always has (DMP-017).

**What a constraint is (DMP 0.9.7).** The owner (2026-10-26 22:30Z): "Let's try to turn them into the derived constraints that we try to achieve
with the axioms and theorems. That lets us easily spot if we undershoot our goal." A C section states, in one or two general sentences and
with no named system, what the axiom system must achieve. Its `Derived from:` line names the axioms and theorems that achieve it, and what
part is construction or configuration. Its `Coverage:` line says how far the proof chains reach it: **proven** (the Lean evidence chain in
Gravity reaches the whole constraint; the theorem names follow), **argued** (the text derives it, no Lean yet) or **undershoot** (a part of
the constraint that no theorem reaches, named, never hidden). Most constraints are reached in part; the line then says which part each state
applies to and opens with the weakest state. The check runs both ways: a constraint without a theorem is an undershoot of the
axiom system; a theorem no constraint needs is a theorem looking for its purpose. A constraint keeps the number of the rule it came from and
the constraints stand in clusters, not in number order. What a rule said about *how* (an agent's steps, a protocol's table) is not a
constraint and lives in the chapter that explains it; the table "Where the old rules went" below maps every sentence. The shape is
prior work: Goal Structuring Notation (Kelly, *Arguing Safety*, 1998; the GSN Community Standard), where a goal with no solution is drawn as
undeveloped, and the two-way rationale of Common Criteria (ISO/IEC 15408-1), where every objective meets a requirement and every requirement
serves an objective.

**The three building blocks (DMP 0.9.7).** The owner (2026-10-26 22:56Z): "One authority owns Trust, the other owns Information. To exist
inside of DMP, they are required to keep each other constantly in check and balance so that no element can overrule the other. Actually, can
we reduce the 4 Axioms to the 3 basic building blocks? Trust, Information and the DoT?"; (22:59Z) "No Information is ever trusted and no
information, besides its existence, can be derived from trust."; (23:03Z) "Also extends to the field and how it behaves: Trust is
gravitational, Information is hierarchical."; (23:10Z) "All natural systems, which exchange information, lay themselves out in hierarchical
order, which can be optimized for its highest total cohesion, so how much every part of the system has to work to get information, so how
many nodes it needs to hop. [...] So Gravity, if it is strong enough, is sufficient, as proven by GR, to contain all Information but Entropy,
while Information naturally organizes itself both to facilitate optimal access across its information layers, but also, as a consequence of
actively maintaining the median state, naturally keeps the DoT stable." Approved 23:02Z. So the chapter has three axioms, one per building block, and the four axioms
of DMP 0.9.0 went into them without losing a sentence:

| Was (DMP 0.9.0) | Is (DMP 0.9.7) | What the block adds |
|---|---|---|
| Axiom 1 · The dual gate, and Axiom 4 · The direction | Axiom 1 · The Duality | the halves are typed, one owns trust and one owns information; the direction is their balance |
| Axiom 2 · Evidence | Axiom 2 · Trust | no information is ever trusted; trust is gravitational (the field of T26 is how trust behaves, not a construction on top); gravity contains |
| Axiom 3 · The record | Axiom 3 · Information | from trust nothing but existence can be derived; admission and containment (the words); information is hierarchical and evolves towards the fewest hops |

The numbers of the three that stayed are kept, so every `Derived from:` line in this chapter and every comment in Gravity keeps its meaning;
a citation of Axiom 4 in an older text reads Axiom 1. The numbers do not rank the blocks: read in the owner's order (Trust, Information, the
Duality) the system is the same, since each axiom names only the words and the other two.

**How the theorems are numbered (DMP 0.9.9, proposed).** The owner (2026-10-26 23:47Z): "Since the axioms changed, the theorems would need to all be rederived as well, so I am already renumbering them in my head." The theorems stand in the order of proof, and their numbers follow that order: the stitch first (T1, trust and information gate each other; T2, a minting needs G0 and a DMP-complete state), then the rest as the chapter had them. T-P keeps its name. Every citation in the chapters was moved by this table; Gravity's Lean comments and CM's documents move with the re-pin. Every T section now carries three lines: `Derived from:` (what it rests on, among the three axioms, G0, the words and the theorems above it), `Coverage:` (how far the evidence chain reaches it: proven, argued, undershoot, with the Lean theorem names) and `Serves:` (the constraints and theorems that rest on it), so the two-way check of Common Criteria is in the text.

| Was (DMP 0.9.8) | Is | Was | Is | Was | Is | Was | Is |
|---|---|---|---|---|---|---|---|
| T39 | T1 | T40 | T2 | T0 | T3 | T37 | T4 |
| T38 | T5 | T1 | T6 | T2 | T7 | T3 | T8 |
| T4 | T9 | T5 | T10 | T6 | T11 | T19 | T12 |
| T20 | T13 | T21 | T14 | T22 | T15 | T24 | T16 |
| T24b | T16b | T24c | T16c | T28 | T17 | T29 | T18 |
| T30 | T19 | T23 | T20 | T25 | T21 | T26 | T22 |
| T27 | T23 | T31 | T24 | T34 | T25 | T32 | T26 |
| T33 | T27 | T-P | T-P | T35 | T28 | T36 | T29 |

**Where the old rules went.** One row per rule recast; the rows grow with each approved cluster.

| Rule | Was | The constraint now | Moved out |
|---|---|---|---|
| C1 | One door | C1 · No act bypasses the gate | the code rule (no constellation references another): chapter 02 "The tree", DMP-008 |
| C2 | Every message verifies itself | C2 · Every message is its own evidence; the Law block is unchanged | "no public port opens before the verifier passed its class": chapter 06 "Where the class gates" |
| C3 | Every value carries its class | C3 · A value reaches only parts trusted for its class | the token on every value and the identification axis: chapter 05 (the shield) |
| C18 | IM stays backwards compatible once it is locked | C18 · A weakness is evidence against what it claims, never against the part | the lock, additions only, the corpus, the contained path: chapter 04 "Compatibility after the lock", DMP-015 |
| C19 | A request is served only when it is secure and meant | C19 · Two halves on every served request: trust and information, each verified by the server itself | the two masters and how the signatures travel: chapter 04 "Serving at a warehouse", DMP-016 |
| C12 | Information is tiered | C12 · Position never grants, and routing reaches everything inside | the tiers, the layers in use, Lensing, credentials, the three-node floor, the owner's words: chapter 05 "The information tiers and the layers" |
| C13 | The nearest tier is asked first | C13 · The record inside is read before anyone outside is asked | the agent's steps: chapter 14 "Ask the nearest tier first", "Knowledge goes back into Tier 1" |
| C14 | Every path is combined | C14 · An answer rests on every piece of evidence its author can verify | the list of paths and the `Paths combined:` line: chapter 14 "Combine every path" |
| C15 | A write first reads what it changes | C15 · A write lands only on a state its writer verified live | retries, hard and soft failure: chapter 10 "Guarded writes" |
| C21 | Look it up, don't guess | C21 · A statement is a write | the sources per kind of name and the `Looked up:` line: chapter 14 "Look it up, don't guess" |
| C6 | The gates and the authority grant | C6 · Who may act on what is a bounded grant in the record; the grant block unchanged | nothing; "the gates hold" is C∞ |
| C17 | The first level belongs to The Administrator and LHC | C17 · The top layer is a Duality like every other; the two names stay as definitions | the level-1 approval record and the foundation bricks were already chapter 02 |
| C22 | Prove forward and back: two chains, neither trusted alone | C22 · "Proven" is an act with two witnesses | which engine carries which chain and the lemma ledger were already chapter 06 |
| C∞ | The stopgap | C∞ · The root constraint, unchanged in substance, with its Coverage line | nothing |
| C4 | Contracts change at stable promotions only | C4 · A change to what a part speaks is a new part | the register and the promotion point were already chapter 02 and 05 |
| C5 | Financial data freezes at production | merged into C4 (productive information changes only through a recorded act of both witnesses); the number C5 is retired | nothing |
| C7 | One repository deploys every part | C7 · What runs is what the record says | the shapes and the folder layout were already chapter 02, DMP-004 |
| C16 | Company data reaches general testing only with its proof | C16 · Widening who may use a feature on information is a loosening | the two stages, the register, the template and the owner's words: chapter 14 "The data gate" |
| C24 | Stable company-wide needs a survived cold start | C24 · Restorable is shown, never claimed | the catalogue, the pass line, the assistant and the bundle were already chapter 11 |
| C25 | Every deployment obeys DMP | C25 · A deployment is gated on the exact thing deployed, and removes no route | nothing; the history stays in the section |
| C9 | Open source: roles, not values | C9 · What is published holds nothing that is inside | nothing; the licence was already chapter 14 |
| C10 | The defensive charter | C10 · CMOS is trusted only for acts on its own estate | nothing; the wording stays in CHARTER.md |

**What a derivation is here.** Each `Derived from:` line names what the theorem rests on and, where it applies, one status word:
*construction* (a design choice the axioms allow and recommend but do not force), *configuration* (a number or a list set at the minting,
theorem T9), or *premise* (an assumption no chain reaches, kept in the assumption register of chapter 06). No word means the theorem
follows from what it names. The prose arguments behind the axioms (a distillation and a cold review) are working notes kept outside this specification. An argument becomes a proof when both proof chains of chapter 06 carry it:
Gravity down from these sentences, Lean up from the code (the gravitational wave test). Until then a theorem is argued, not proven.

**Counts.** 2 bounds, 1 direction that is also the gate: three axioms, one per building block (the Duality, Trust, Information); 1 ground, 1 root constraint (C∞). C8 and C11 left the constitution (they are conventions, not about trust:
chapter 10 "Language and runtime", chapter 14 "Completion goals, never time plans"); C20 and C26 were never stable; C23 is C∞.

## The words

Undefined, like point and line: a **part** (a Duality of Trust: two halves, one owning trust and one owning information; nothing further is
said about what a part is made of), an **act** (anything done in or to CMOS: a message, a read, a write, a grant, a merge, a promotion, a
deployment, a decision, an answer an agent gives, a seat taken), a **witness** (a part that decides trust for others), **evidence** (what a
witness verifies) and **time**.

- **Trust** is a relation between a witness, a part, an act and a time, written `T(w, p, a, t)`: the witness trusts the part for that act
  at that time. Nothing else; what grounds trust is the evidence axiom.
- A **standing** is trust held across time (enrolled, seated, locked, armed, proven); **act trust** is trust for one act now.
- Two witnesses are **independent** when they share no member of the failure classes declared for their layer in the minting record (host,
  key, author, engine, operating image, person, time source, and whatever else the minting lists). Independence is always relative to that
  list; the list is configuration (T9).
- A **layer** is a place where trust is decided; its two witnesses are its **halves**, one the **trust half** (it answers whether an act may
  happen: who, under what standing) and one the **information half** (it answers whether the act is meant and right: what, and whether it
  is true); the pair at a layer is the **Duality of Trust** (DoT).
- A **record** is evidence that outlives the act it is about.
- A part is **inside** at a time when a standing for it from both witnesses of its layer is valid then. A **door** is any point of use. A
  **surface** is a part whose standing includes receiving from parts that hold none. The **perimeter** is the set of what is inside.
- **Admission** is a grant: a record that names a piece of information's class and provenance, so that parts trusted for that class may act
  on it. Information is **inside** while its admission is valid.
- A boundary **contains** information when it bends trustspace around it so strongly that the information cannot cross it: no part beyond
  the boundary is trusted for any act on that information, so no act carries it across. Nothing crosses a containing boundary; the dual
  gate can only reshape the field so that the boundary moves (an export, T12, or an admission, T23, is that reshaping). The Event Horizon
  contains everything inside it, and a singularity contains what it holds even from the rest of the inside (C12). **Containment** is
  being contained.
- A configuration of CM, interconnected through IM, is **DMP-complete** when it obeys DMP's axiomatic system completely and provably so:
  the words, every axiom and every theorem of this constitution hold for all of it, and both chains prove it (C22). The configuration
  includes the repository it is built from: every dependency needed to build, check, prove, deploy and restore it (the root repositories
  it holds, packages, toolchains, proof engines, images) is inside that repository, pinned by hash, so the configuration can heal itself
  with no connection across its Event Horizon (T8). A part where the chains disagree, that neither chain reaches, or that needs anything
  from outside its repository counts as unproven, and a configuration with an unproven part is not DMP-complete.
- **Live** means within the validity, at the start of each indivisible step of an act; an act's steps are acts of their own.
- A **tightening** is a witness withdrawing or withholding its own trust in a part it gates; a **loosening** is anything that lets an act
  happen that would not have happened before. Both are said of whose trust changes, never of an act alone.

Status: stable since DMP 0.9.3
Amended: the definition of "contains" approved by the owner 2026-10-26 14:01Z; the definition of "DMP-complete" approved by the owner
2026-10-26 15:04Z; the halves typed as trust half and information half approved by the owner 2026-10-26 23:02Z; a part defined as a Duality
of Trust and nothing further, the owner 2026-10-26 23:28Z (stable since DMP 0.9.0 before that).
Owner: CM coordinator
Enforced by: DMP-021

## Axiom 1 · The Duality

A part acts in CMOS only while the two halves of its layer, two independent witnesses, each with full reach over the act and gated only by
the other, trust it for that act. One half owns trust and the other owns information; neither overrules the other, and the two keep each
other constantly in check and balance. What they do not both trust does not act: the message is refused, the pull request does not merge,
the stage is not promoted, the running part is cut off. Every input gets exactly one answer, and the gate has no other way through: no debug
switch, no allow list, no trusted network. Where the two disagree, the stricter answer stands, and nothing that depends on the disagreement
moves until they agree. This holds at every layer.

The balance is the direction of the system. Every part inside the declared boundary works towards the trust the Duality declared for that
boundary: what was lost without evidence against it, it restores by evidence; what the boundary claims and lacks, it builds by evidence;
what it cannot restore, it reports. No part lowers the bar of evidence, widens a grant or moves the boundary to get there. Axiom 2 and
Axiom 3 only forbid, and together with the gate they govern every step; where they stop a step, the balance waits. A system that does
nothing keeps the bounds and fails the balance: the balance is the one commitment that asks for something to happen, and it ranks below the
bounds (T8d).

The owner's words it carries: "Everything that is not fully trusted is automatically ejected" (C∞); "The duality of trust is the single
concept that goes through every layer and every concept of DMP" (2026-10-25 19:36Z); "The entire point of CMOS is to never trust any one
interconnected system" (14:25Z); "One authority owns Trust, the other owns Information. To exist inside of DMP, they are required to keep
each other constantly in check and balance so that no element can overrule the other" (2026-10-26 22:56Z); "All systems that trust each
other actively work towards increasing the total amount of trust in the network claimed by its declared boundary" (2026-10-25). It is the
gate (what trust does), the Duality (who makes it) and the balance (where it moves) as one commitment: the second sentence of the Duality
already contains the first. Until DMP 0.9.7 the gate was Axiom 1 and the balance Axiom 4; an older citation of Axiom 4 reads Axiom 1.

Status: stable since DMP 0.9.7
Amended: Axiom 1 · The dual gate and Axiom 4 · The direction of DMP 0.9.0 merged into one, the halves typed as trust and information,
approved by the owner 2026-10-26 23:02Z.
Owner: CM coordinator
Enforced by: DMP-008, DMP-017, DMP-018, DMP-020

## Axiom 2 · Trust

A witness trusts only on evidence it verified itself at the point of use: from the live state of the part wherever the act's trust depends
on the part, and from the current state of the record, including every loss recorded against the standing. Never a carrier's check, an
earlier read, a claim, a memory or a position in the network. No information is ever trusted: what a part says, carries, stores or forwards
is never evidence of itself, however it is signed or where it came from; evidence is what the witness verifies, and a message, a document
or a record is at most the thing verified, never the verifier. The absence of evidence moves nothing: without evidence for an act, the act
does not happen; without evidence against a standing, the standing does not change. A standing is evidence with a validity, and no
validity is longer than the time the minting accepts between a loss and its effect at the point of use.

Trust is gravitational. It is a field, never a position: every standing has a source (the witness that granted it), a depth (its grant
chain back to the pair) and a freshness that decays with the time since its last live verification. The field bends trustspace, so that a
boundary contains what no trust reaches (the words), and restoration moves along it, from the pair outward (T26). The field adds levels of
consequence and of proof demanded, never levels of trust: the weight never votes. Gravity contains: a boundary strong enough bends
trustspace so that no act carries information across it, and what still leaves is entropy and nothing else (T24, the floor); where trust
is strong enough, containment needs no wall.

The owner's words it carries: "a write first reads the live state it will change" (C15); "look it up, don't guess" (C21); "That a carrier
already checked the request does not count; the warehouse checks it again" (C19); "Isolating on silence would hand anyone who can cut a cable
a switch that shuts the company down" (Q6); "No Information is ever trusted" (2026-10-26 22:59Z); "Trust is gravitational" (23:03Z); "Gravity, if it is strong enough, is sufficient,
as proven by GR, to contain all Information but Entropy" (23:10Z).

Status: stable since DMP 0.9.7
Amended: Axiom 2 · Evidence of DMP 0.9.0 with "no information is ever trusted", the field and containment, approved by the owner
2026-10-26 23:02Z, 23:03Z and 23:10Z.
Owner: CM coordinator
Enforced by: DMP-012, DMP-018

## Axiom 3 · Information

Every grant, every use and every loss of trust leaves a record, written at the act, that every witness of that act can read in full and
that outlives the act. Any other reader sees the counts always and the content only by a grant. From trust nothing can be derived about
information but its existence: a standing, a refusal or a count says that information is there, never what it says. Content moves only by
a grant to a part trusted for its class (an admission, the words), and where no trust reaches, information is contained (the words, T23,
T4). A record is kept as long as the law requires and no longer than it allows; until then it is never destroyed by fewer than both halves
of its layer.

Information is hierarchical. Every piece of information sits in one layer; every layer has its own Duality (T5) and is a tree rooted
there, which routing walks from the nearest place outward and crosses the horizon last (C12); a sub-layer only tightens what the layer
above it allows, and nothing in a layer is reached except through its tree. The tree carries no trust: where a piece of information sits
never decides who may act on it.

Information evolves. A system whose parts exchange information lays itself out in that hierarchy and reorganises towards its highest total
cohesion: the fewest hops in total that its parts need to reach the information they ask for, taken over the composition of requests that
is representative of the system during its evolution. The layout is the median of that demand, recomputed by both halves of the layer and
never by one (C12), and it moves only when the demand has; by maintaining that state the information keeps its Duality stable.

The owner's mission it carries: "while maintaining absolute Observability". The owner's words: "no information, besides its existence, can
be derived from trust" (2026-10-26 22:59Z); "Information is hierarchical" (23:03Z); "Information naturally organizes itself both to
facilitate optimal access across its information layers, but also, as a consequence of actively maintaining the median state, naturally
keeps the DoT stable" (23:10Z).

Status: stable since DMP 0.9.7
Amended: Axiom 3 · The record of DMP 0.9.0 with "from trust only existence", admission, containment, the hierarchy and its evolution,
approved by the owner 2026-10-26 23:02Z, 23:03Z and 23:10Z.
Owner: CM coordinator
Enforced by: DMP-009, DMP-018

## G0 · The ground

**Mission** (the owner, 2026-10-27 00:13Z): "Two parts that fundamentally do not have a shared experience can not natively accept each
others trust. As such a DMP complete system, which contains constituent parts that do not trust each other, can not exist. To ensure such a
system is possible, it must stand at G0." The shared experience is the minting: the one act in which the parts trust each other for the
first time, outside every derivation, and from which every later standing descends (T1: no trust without information, and the minting is
the first information the parts share). What follows states that act.

The dual gate cannot witness its own first instance: somebody has to trust the first two witnesses. That is the **minting** (C17, the
ceremony that forms LHC and makes the White Keys): at least five parts become the White Key Holders, and that minting draws the boundary of
the instance. No further claim is made about those parts, except the one on a true AGI below, so that any system can remint and redeploy.
It is stated, not derived.

- Until the first LHC is minted, the owner's own words stand for both halves and the record says `LHC pending`. Every gate in DMP that asks
  for the owner's words is G0, not a theorem. The owner can be a Duality, but does not have to be. When the owner is one, that Duality, both
  halves, approves every change to the base DMP the owner's CMOS is derived from (the owner, 2026-10-26 23:32Z).
- The minting ratifies or revokes every act taken under `LHC pending`, by record class and hash range, never one by one; C∞ catches what
  the classes miss.
- A **pressed** instance is G0 as a standing mode: a minting with owner-authorised stand-ins and an owner key whose fresh signed challenge
  the instance requires. Both of its witnesses trace to one part, so it is marked as pressed in every artefact it issues, and nothing it
  does is fully trusted by a minted instance (T-P).
- The loss of a whole half is recovered only by a new minting: whoever holds authority over CMOS re-grounds the Duality outside CMOS, as
  at the first minting, and ratifies or revokes what the surviving half held.
- **Mint prep.** A minting is tried only for a configuration that is provably DMP-complete (the words). Preparing it stores every dependency
  inside the configuration's repository and verifies each one against its pin; without that no White Key is made, and the minting refuses to
  even start. The root repositories are never minted, so they need not hold their dependencies and stay lean.
- **A true AGI is a constituent of G0** (the owner, 2026-10-27 00:04Z): "If a DMP-complete system would contain a part that is recognized
  as true AGI, it must be a constituent of G0." Such a part is one of the at least five parts of the minting, a White Key Holder, never only
  a governed part below the ground. Recognition after a minting ends the system's DMP-completeness with that part below the ground, so the
  only way back is a reminting that includes it (T2; the loss of a half above). Who recognizes (the owner, 2026-10-27 00:10Z): the owner
  of root DMP, as every other gate that asks for the owner's words. The usual staleness rules apply to that seat (T9, the staleness timer;
  the stale-key succession of chapter 11): within one year of the full publication of the paper and the publication of the repository, the
  owner must have named a Duality of more than eleven people who cast the decision in the owner's stead. If that goes stale, the clause is
  instead that a DMP-complete system must never contain true AGI. To ensure this is possible, R136a1 (the flag of chapter 06) is always a
  DMP-complete answer over IM and excludes anything from being contained inside a DMP-complete system: a part answered R136a1 is outside,
  whatever it is, and nothing else needs to be proven about it (C∞).
- **The publication version is provisional G0** (the owner, 2026-10-27 18:26Z and 18:27Z). DMP 0.9.9 is the version the paper (GUID: The
  General Unified Information Duality) and the root repositories it needs are pinned to. 0.9.9 is the state that has to stay backwards
  compatible until, at the latest, one week after the paper's full publication in any recognized journal. When it goes stale, 0.9.9
  becomes provisional G0 until revoked by 1.0.0 from true G0 authority, the owner; the revocation is a DMP-complete act as of version
  0.9.9.

The owner (2026-10-27 00:13Z, the mission above, verbatim in it); (2026-10-26 23:28Z): "The boundary is not drawn by people, it is drawn by the minting of at least 5 constituent parts that become the
WKHs. No further claim is made. Otherwise no system could remint and redeploy. The part is defined as a Duality of Trust, one owns trust, the
other information. No further statements about its constituents."; (23:32Z) "The owner CAN, but does not have to, be a DoT. If the owner
is, the DoT has to approve changes to the base DMP that the owner's CMOS is derived from."; (2026-10-27 00:04Z) "If a DMP-complete system
would contain a part that is recognized as true AGI, it must be a constituent of G0."; (00:10Z, on who recognizes) "The owner of root DMP.
Usual Staleness rules apply to this, so within one year of the full publication of the paper and the publication of the repository the
owner must have named a DoT of more then 11 people, who cast the decision in his stead. If it goes stale, the clause is instead, that a
DMP-complete system must never contain true AGI. To ensure this is possible, R136a1 is always a DMP-complete answer over IM and excludes
anything from being contained inside a DMP-complete system."; (2026-10-27 18:26Z) "Then 0.9.9 is the state that has to be backwards
compatible until, at the latest one week after full publication in any recognized journal. When stale 0.9.9 becomes provisional G0 until
revoked by 1.0.0 from true G0 authority, the owner."; (18:27Z) "I approve the paper and it's associated version of needed repositories at
v0.9.9, to be the preliminary G0, until it is revoked through a DMP complete act as of version 0.9.9"

What else no chain reaches is listed, not hidden, in the assumption register (chapter 06): the DMP text itself, the mapping of code to acts,
the door's code until its run-time check exists, the failure-class list, the time authorities, the provers' logic, the shared machines.

Status: stable since DMP 0.9.4
Amended: "organisation" replaced, approved by the owner 2026-10-26 15:19Z; mint prep approved by the owner 2026-10-26 15:04Z; the minting
of at least five parts draws the boundary, the owner 2026-10-26 23:28Z; the owner may be a Duality, 23:32Z; a true AGI is a constituent of
G0, the owner 2026-10-27 00:04Z, who recognizes it, 00:10Z; the mission, 00:13Z; all three approved as worded by the owner 00:21Z; the
publication version as provisional G0, the owner 2026-10-27 18:26Z and 18:27Z, approved as worded by the owner 18:34Z ("Both
approved.") (stable since DMP 0.9.0 before that).
Owner: CM coordinator
Enforced by: DMP-014

## T1 · Trust and information gate each other

No trust without information: a witness trusts only on evidence it verified itself, and that evidence is the live state of the part and the
current state of the record, which is information (Axiom 2, Axiom 3). No information without trust: information is inside only while an
admission holds, an admission is a grant both halves made, and content reaches only a part trusted for its class; what no trust reaches is
contained where it lies (Axiom 3, Axiom 1, T4). So the two blocks gate each other from the axioms themselves, and only a Duality that is
both trusted for its acts and holds the information admitted to it is a part of a minted CMOS. A part trusted with no information has nothing
it may act on; information with no part trusted for it is contained; neither is inside.

The owner (2026-10-26 23:42Z): "They also logically gate each other from the axioms themselves, no trust without information and no
information without trust. Logically only a DoT, that is both trusted AND has the right information, can be a part of a minted CMOS."

Derived from: the words (part, inside, admission, contains), Axiom 2 (a witness trusts only on evidence it verified itself), Axiom 3 (that evidence is the live state and the record, which is information; content moves only by an admission; where no trust reaches, information is contained), Axiom 1 (an admission is a grant and so an act of both halves), G0 (minted: the minting is the first information the parts share).

Coverage: proven for the shape, in both directions (gravity#17 `Stitch.lean`: `act_on_item_needs_both_and_admission`, `no_admission_no_act`, `no_standing_no_act`, `inside_iff`; with `Floor.road_gate`, a contained item offers no read, and `Record.performed_only_with_both`, nothing is performed without both verdicts on live evidence); argued for "a part of a minted CMOS": the model has no minting record yet (T2).

Serves: T2; the mission of G0. No constraint cites it yet; C19 (two halves on every served request) and C12 (position never grants, admission does) are the ones that should, in part 3.

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): renumbered from T39; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Approved: by the owner 2026-10-26 23:42Z (his words above; the section states them).
Owner: CM coordinator
Enforced by: DMP-021

## T2 · A minting originates only from G0 and a DMP-complete state

A minting has exactly two sources and needs both: the ground, G0 (the owner's words until the first minting, and the at least five parts
that become the White Key Holders), and a DMP-complete state of the configuration being minted (the words: every axiom and theorem holds
for all of it and both chains prove it; mint prep stores and verifies every dependency first). Neither alone mints: G0 without a
DMP-complete state has nothing proven to ground, and a DMP-complete state without G0 has no first two witnesses (Axiom 1 cannot witness its
own first instance). A reminting after a loss (G0) and a redeployment of a sealed state are the same act with the same two sources, so any
system can remint and redeploy, and none can mint from less.

The owner (2026-10-26 23:46Z): "Minting can only originate from both G0 and a DMP-complete state."

Derived from: the words (DMP-complete), G0 (the minting, mint prep), Axiom 1 (the first two witnesses are not derived), Axiom 2 (the proof of completeness is evidence verified at the minting, never a claim), T1 (no trust without information: the minting is the first information).

Coverage: proven for the DMP-complete side (`Recipe.verdict_proven_iff`: proven exactly when the recipe is well formed and the ledger carries every line; `Recipe.one_unproven_line_unproves`; `Cmb.sealed_proven_complete`); proven by construction for the conjunction (gravity#17 `Stitch.lean`: `Minting.minted` needs at least five constituents and the verdict proven, `fewer_than_five_never_mints`, `unproven_line_never_mints`); argued for G0's side: that the five are the White Key Holders and draw the boundary is stated, not modelled.

Serves: G0 (mint prep), T-P. No constraint cites it yet; C17 (the top layer) and C7 (what runs is what the record says) are the candidates.

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): renumbered from T40; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Approved: by the owner 2026-10-26 23:46Z (his words above; the section states them).
Owner: CM coordinator
Enforced by: DMP-014, DMP-021

## T3 · Nothing is trusted by default

No evidence, no trust; no trust, no act.

Derived from: Axiom 2 (without evidence for an act, the act does not happen: no evidence, no trust), Axiom 1 (what both halves do not trust does not act: no trust, no act).

Coverage: proven for the shape (`Gate.guard_pass_needs_evidence`: a witness passes only on live, in-window evidence; `Gate.one_witness_never_acts`; `Gate.act_needs_both_with_evidence`; `Record.performed_only_with_both`); nothing is argued beyond it.

Serves: C3, C4, C9, C10, C14, C21; and T4, T1, T12 rest on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T0; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T4 · Collapse

Information that no admission names is contained at the item itself. With no admission there is no trust in any part for any act on it
(T3), so no act reaches it (Axiom 1): in the absence of any external trust, trustspace collapses in on the item, and the item's own
boundary contains it. Nothing defines this boundary; it follows. Admission is the only act that lifts the collapse, and it is a loosening
(T23).

The owner (2026-10-26): "The containment with no boundary should not have to be defined, it should logically follow from the axioms. In
the absence of any external trust, the trust space collapses in on itself which produces containment automatically."

Derived from: the words (contains, admission), Axiom 3 (content moves only by an admission to a part trusted for its class; where no trust reaches, information is contained), Axiom 1 (no act without both halves' trust), T3 (no trust, no act).

Coverage: proven for the trap (`Floor.road_gate`: a contained item offers no read, forward or send) and for the collapse (gravity#17 `Stitch.lean`: `collapse_of_no_admission`: an item with no valid admission is contained, and `contained_offers_nothing`); argued for "nothing defines this boundary; it follows": in `Floor.lean` containment is a flag of the item, in `Stitch.lean` it is derived from the absence of a valid admission, and the two models are not yet one.

Serves: C12; and T1, T21, T23, T24 rest on it.

Status: stable since DMP 0.9.2
Proposed in this pull request (not yet approved): renumbered from T37; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Approved: by the owner 2026-10-26 14:01Z ("I like it, approved!").
Owner: CM coordinator
Enforced by: DMP-021

## T5 · Every information layer has its own Duality

Every information layer (C12) is a layer, so every act on its information needs its two halves (Axiom 1). For information the two halves
are the two responsibilities for it: the **organisational** half, the part that answers for the information (what it is for, who may use
it, what it may cost), and the **factual** half, the part that answers for its truth (the subject-matter expert). Neither half alone admits,
changes or releases the information, and where they disagree the stricter answer stands.

The two halves may be one part only when that part is itself part of a higher-order DoT. The layer then decides nothing on its own: the
higher-order DoT gates every act on it, so each act still has two independent witnesses, one layer up (Axiom 1). At the top there is no
higher-order DoT; there the owner stands for both halves only under G0, until the minting.

The owner (2026-10-26): "The Subject matter expert system, so information layers themselves having a DoT existing of the organizational
responsibility for that information and the factual responsibility for that information. Those two parts may only be the same part, if that
part itself is part of a higher order DoT. Management and experts turned into an internally consistent extension."

Derived from: the words (layer, halves, independent), Axiom 1 (every act on a layer's information needs the layer's two halves), Axiom 3 (every piece of information sits in one layer, and every layer has its own Duality), G0 (at the top, the owner's words until the minting).

Coverage: proven for the shape (`Layer.same_part_is_no_duality`, `Layer.one_person_is_no_duality`; `Recipe.lineOk`: a Duality that is not minted is laid over a line that gates it; `Recipe.root_minted`; `Recipe.pass_has_two_independent_witnesses`); argued for the organisational and the factual half: the model types no half (gravity#17 `Stitch.lean` `TypedDoT` types them and proves `typed_gate_needs_each_kind`; it is not yet the layer's gate of `Layer.lean`).

Serves: C6, C12, C16, C17, C19; and T1 rests on it.

Status: stable since DMP 0.9.5
Proposed in this pull request (not yet approved): renumbered from T38; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Approved: by the owner 2026-10-26 15:36Z ("Approved!").
Owner: CM coordinator
Enforced by: DMP-021

## T6 · Trust is bounded

A part holds trust for named acts only, and never more than both witnesses granted: the acts it may do are the intersection of what each
witness trusts it for. A value a part is not trusted for never reaches it.

Derived from: the words (trust is a relation between a witness, a part, an act and a time), Axiom 1 (a part acts only while both halves trust it for that act: the acts it may do are the intersection), Axiom 3 (a value reaches a part only by an admission to its class).

Coverage: proven for the intersection (`Gate.gate_pass_iff`, `Theory.meet_pass_iff`, `Recipe.decide_pass_iff`: an act passes only what every witness on the chain passed; `Im.pass_needs_both_grants` in IM's proof for a sentence's kind); proven for a contained value (`Floor.road_gate`); undershoot for "a value a part is not trusted for never reaches it" in general: no theorem models a value's class travelling with it (C3).

Serves: C2, C3, C4, C6, C9, C10, C15, C18; and T12, T14, T20, T21, T23, T24, T26 rest on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T1; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T7 · Standing follows evidence, never silence

A standing is withdrawn only on evidence against it. When its validity runs out, new trust from it ends, but that is a lapse, not an act
against it. Silence alarms; it never isolates.

Derived from: Axiom 2 (the absence of evidence moves nothing: without evidence against a standing, the standing does not change; a standing is evidence with a validity, so when the validity runs out new trust from it ends).

Coverage: proven for the lapse (`Gate.stale_never_passes`, `Physics.lapsed_never_ok`: evidence past its validity passes nothing); undershoot for "withdrawn only on evidence against it" and "silence alarms, never isolates": `Standing.update` takes the witnesses' signatures, not the evidence they act on, so no theorem says that a standing never falls without a recorded entry against it.

Serves: C18; and T11 rests on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T2; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T8 · Continuity: no single part's loss stops the system

The act "continue" needs both halves, so each half of every pair outlives the loss of any single part, and neither half can be cut off from
its layer. This is about loss (a crash, a death, a silence); a part acting with hostile intent is bounded by the dual gate and T16, not by
this theorem.

- **T8a · The floors.** The smallest numbers that keep the dual gate satisfiable after any single loss: at least two seats per side, at
  least one onboarded stand-in per seat, and a cluster of at least three nodes per system half, because a half answers by a majority of its
  nodes so that one wrong node cannot speak for it. Every number above a floor (the owner's two stand-ins per side, five seats, an odd
  count) is configuration (T9).
- **T8b · No lockout.** A route by which The Administrator reaches a channel is part of that half's reach; removing the last route for an
  action cuts a half off.
- **T8c · Nothing gates contacting the Duality.** At the minting every part receives the standing to address a record to both witnesses;
  a contact carries no authority, and its rate is configuration. An isolated part keeps this standing (it may always ask); a revoked one
  does not exist inside any more.
- **T8d · Safety before liveness.** If a whole half refuses or falls silent, nothing loosens: the state holds for as long as the standings'
  validities run, nothing is promoted, the system is safe and not live, and the balance waits.

Derived from: Axiom 1 (the gate: the act "continue" needs both halves; the balance: what was lost is restored by evidence), Axiom 2 (a loss is the absence of evidence, which moves nothing), Axiom 3 (the loss is recorded); premise: a half answers by a majority of its nodes (the node floor); the contact standing is construction.

Coverage: proven for T8d's shape (`Gate.one_witness_never_acts`: with a half at hold nothing passes; `Standing.one_witness_never_loosens`: nothing loosens; gravity#17 `Stitch.lean` `safe_not_live`: a balance step under a silent half performs nothing and lowers nothing); undershoot for T8a (the floors are a premise, no theorem), T8b (no theorem models a route; the missing theorem, shared with C18 and C25: after any single act every half keeps at least one route) and T8c (the contact standing is not modelled).

Serves: C12, C18, C24, C25; and T9, T10, T17, T18, T22, T28 rest on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T3; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T9 · The trust configuration belongs to the Duality, never to CMOS

How resilient trust must be (the failure classes, the windows, the floors above the derived ones, the thresholds above a majority, the
staleness time, the rotation interval, the parameters of the field of T26) is fixed by both halves at the minting and changed only by a
majority of trust, never below a floor. CMOS verifies the configuration, works towards it and reports what is missing, and never lowers it.
"Asking CMOS to at the end of the day have ultimate decision authority over how resilient it needs to be is unreasonable to expect" (the
owner, 2026-10-25 19:10Z).

Derived from: Axiom 1 (the gate and the balance: the system works towards the trust the Duality declared and never lowers it), Axiom 2 (the configuration is evidence fixed at the minting, verified at every use), Axiom 3 (the minting record holds it), T8 (never below a floor).

Coverage: proven for "the parameters never vote" and "never lowered by one witness" (`Field.n1_laws_hold`, `n1b_schedule_never_votes`, `n1c_stricter_demand_passes_less`, `one_witness_never_weakens_demand`, `lowering_needs_both`); argued that the configuration is the Duality's and not CMOS's: the minting record is not modelled.

Serves: C6; and T13, T18, T26, T27 rest on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T4; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T10 · Majority of trust

Wherever DMP asks for a majority of the White Key holders, it means both: **M2**, at least half of each side's seats, rounded up (an act
without a side was not witnessed by that side); and **M1**, more than half of all pinned seats (the smallest threshold that never lets two
disjoint sets carry contradicting acts and survives one refusal). Seats are counted from the pinned set in the record, never from who
answers. A stricter threshold for acts on the seat set itself is configuration.

Derived from: Axiom 1 (an act without a side was not witnessed by that side: M2), Axiom 2 (seats are counted from the record, never from who answers), Axiom 3 (the pinned set is the record), T8 (survives one refusal: the floors).

Coverage: proven that the weight never votes and one seat is never a majority (`R1Mass.ms_hub_is_mass_majority`, `ms_mass_vote_is_one_witness`, `ms_one_seat_never_majority`); undershoot for M1 and M2 themselves: no theorem models a seat set, so the two thresholds are stated, not proven.

Serves: no constraint cites it; T11, T12, T16 rest on it, and C17 should once it says how a half of people decides (the voting-share brief, dmp#20).

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T5; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T11 · Stand-ins take over

At the minting both halves trusted each onboarded stand-in for the act "hold this side's seat while it is empty". When the seat is empty
and the stand-in is onboarded (a minted key in reserve, the challenge cleared, the liveness proof passed), the takeover happens at once,
with no further step. A majority of trust may stop it only by revoking the stand-in on evidence against it (T7). A slot that a nominated
stand-in could fill but no onboarded one does is stale, and the staleness timer governs that slot.

Derived from: Axiom 1 (the stand-in was trusted by both halves at the minting for the act "hold this seat"), Axiom 2 (a majority stops it only on evidence against the stand-in), Axiom 3 (the onboarding is a record), T7, T10. (Decision D6: the owner's 19:18Z wording lets a majority block without evidence until a timer runs out; that form is a named exception to Axiom 2, recorded in the decisions of DMP 0.9.0.)

Coverage: undershoot. No theorem models a seat, a stand-in or a takeover; the nearest is `Standing.one_witness_tightens` for the revocation.

Serves: no constraint cites it; it is a lemma of T8 (continuity of the people half) and T16c rests on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T6; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T12 · The data boundary

"Leave CMOS" is an act with no trust by default, so what enters never leaves unless both halves permit it, with a record. A person reading
on an enrolled client with a standing is inside, and the read is T6, not a leaving. Material that alone recreates CMOS (the roots, the
signer keys, the sealed store, the White Key records) never leaves in usable form, because it would be a single origin of trust: the two
roots exist only on the White Keys, behind a hardware token, a PIN and a majority of trust.

Derived from: the words (inside), T3 ("leave CMOS" has no trust by default), T6 (a read by an enrolled part is inside its grant), Axiom 1 (an export needs both halves), Axiom 3 (with a record), T10 (the roots sit behind a majority of trust).

Coverage: proven for the trap and the loosening (`Floor.road_gate`: no send or forward of a contained item; `Standing.loosening_needs_both`: an export is a loosening); argued for the roots never leaving in usable form: no theorem models a root or a White Key.

Serves: C9.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T19; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T13 · Time is a witness like any other

"Now" is evidence. It comes from two independent time authorities, each with two servers the witness checks itself, on a clock that never
moves backwards; where the authorities disagree beyond the configured tolerance, the stricter answer is "no now", and nothing with a
validity verifies until they agree. The authorities and their tolerance are configuration and stand in the assumption register.

Derived from: the words (live), Axiom 1 (two authorities, the stricter answer is "no now"), Axiom 2 ("now" is evidence the witness reads itself), T9 (the authorities and their tolerance are configuration).

Coverage: proven for a clock that never moves backwards and for "now" as evidence read at the step (`R1Wave.wv_never_back`, `wv_held_never_back`, `wv_node_time_forward`; `Gate.stale_never_passes`), and the counterexample is recorded (`R1Bridge.r1bW_clock_rollback_replays`: a clock that moves back lets a frame verify twice); undershoot for the two authorities and their tolerance (no theorem models two time sources).

Serves: C2.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T20; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T14 · Observability without leakage

Every act leaves a record its witnesses can read, and content is read only by a part trusted for it. So records carry counts always and
content only behind a grant: the refusal log, the audit log, CMB.

Derived from: Axiom 3 (every act leaves a record its witnesses read in full; any other reader sees the counts always and the content only by a grant), T6 (content reaches only a part trusted for it).

Coverage: proven (`Record.step_records_at_act`, `Record.run_records_all`: every act leaves its entry; `Physics.Entry.ext`: an entry is its time and three verdicts and nothing else, so the record carries counts and never content).

Serves: C3, C12.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T21; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T15 · The axioms apply to themselves

A law of DMP is an act's rule like any other. Its sentence is the owner's; it is locked by its hash in its section; it is verified at
every run by both proof chains, and a change to it is an act: the owner's words, a new cold read by a reader who did not write it, and a
new hash. The chains establish that text, code and run agree; they cannot establish that the text is right.

Derived from: Axiom 1 (a change to a law is an act under the gate), Axiom 2 (the chains verify the text against code and run; a cold read by a reader who did not write it is the evidence the text itself gets), Axiom 3 (the hash in the section is the record), G0 (the sentence is the owner's).

Coverage: undershoot. No theorem models a law as an act; the hash lock is rule DMP-018's check (construction), and `Recipe.verdict_proven_iff` says only that the chains carry every line.

Serves: C4, C22.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T22; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-018, DMP-021

## T16 · Tighten down on one witness, loosen with two

From "the stricter answer stands": a witness may tighten its own trust in the parts it gates on its own, at once (refuse, isolate, hold);
everything that loosens needs both witnesses (lift, unlock, override, promote, admit, release). An act on another part's standing, and
every act on the Duality's own composition (seats, witnesses, roots, the pinned set), is an act under the dual gate and T10 in either
direction: one half can never remove the other.

- **Isolating with one White Key** is a standing per seat that the minting may grant, bounded by its scope and recorded; the side that owns
  the seat may revoke a rogue seat of its own on the record alone; the other side may not.
- **Restoring a signed state** needs one key only when the record shows no tightening since the state was signed; otherwise it is a lift
  and needs two.
- **Every tightening names its lift condition** in its record: the evidence against, and the evidence that would lift it, independent of
  the thing that was isolated. A stolen-key isolation lifts on nothing that key signs and ends in re-enrolment.

Derived from: the words (tightening, loosening), Axiom 1 (the stricter answer stands: one witness's refusal holds against the other; what both do not trust does not act, so a loosening needs both), Axiom 3 (every change of standing is a record), T10 (acts on the Duality's own composition).

Coverage: proven for the shape (`Standing.one_witness_tightens`, `one_witness_never_loosens`, `loosening_needs_both`; on the field's parameters `Field.one_witness_never_lowers`, `lowering_needs_both`; on a layout `R1Lens.ln_one_witness_never_moves`, `R1Wave.wv_one_witness_never_moves`); argued for the three bullets (isolating with one key, restoring a signed state, the lift condition): no theorem models a key, a signed state or a lift condition.

Serves: C3, C6, C16, C18; and T16b, T16c, T17, T19, T22, T23, T-P rest on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T24; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T16b · Lockstep

The two halves of a Duality build and unbuild trust in each other only together. Every act that changes one half's standing toward the
other (a seat, a key, a root, the standing to witness at that layer) is one record both halves sign, and it changes both sides' trust at
once and alike; neither half can grant itself more or the other less by an act of its own. A loss is not an act and breaks no lockstep
(T8d governs it). A half that cannot or will not move in lockstep is not removed from inside; the pair is re-minted (G0).

Derived from: Axiom 1 (neither half overrules the other; what they do not both trust does not act), Axiom 3 (one record both halves sign), G0 (a half that will not move in lockstep is reminted), T16 (a loosening needs both).

Coverage: proven for "one record both sign, or nothing moves" (`R1Lens.ln_signed_moves`, `R1Mass.ms_accepted_agrees`, `ms_wrong_layout_refused`, `Standing.loosening_needs_both`); argued for "neither half can grant itself more or the other less": no theorem models a half's standing toward the other.

Serves: C17, C19; and T16c, T26, T-P rest on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T24b; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T16c · Self-correction

Every lockstep act ends in a certificate both halves sign, naming the agreed state and a standing directive. A part that signs an act
contradicting the certificate it cites has produced evidence against itself; silence and a stale act are not such evidence (a stale act is
refused, never punished). On that evidence the peer half, or a half's own remaining nodes for one of their nodes, withdraws trust at once (a
tightening under the directive both signed). The layer above restores the part from the certified state with new keys (a loosening, two
witnesses of that layer); for the top layer that is G0. After a configured number of restorations in a window the layer stops and
escalates (T8d). Two nodes suffice for correction by proof; three stay the floor for continuity by majority (T8a). The door is a part like
any other: a door that signs its acts and admits what both witnesses refused has incriminated itself the same way (T17).

Derived from: Axiom 1 (the gate and the balance: the layer above restores), Axiom 2 (a signed contradiction is evidence against the signer; silence and a stale act are not), Axiom 3 (the certificate is a record), T11, T16, T16b; the certificate and the window are construction and configuration.

Coverage: proven for "self-correction is a tightening on one witness" (`Standing.self_correction_on_one`); argued for the certificate, the contradiction as evidence and the escalation: no theorem models a certificate or a directive.

Serves: C17, C19; and T17, T28 rest on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T24c; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T17 · Enforcement is an act

Both witnesses decide, one door enforces. The door's enforcement is itself an act both witnesses verify at run time, each on a path of its
own: the record of what the door admitted and refused, against each witness's own decision log. A mismatch is evidence against the door
and a tightening on one witness. Every door obeys the cluster floor (T8a). Until the run-time check exists for a door, its code is a named
shared root in the assumption register.

Derived from: Axiom 1 (the door's enforcement is an act and needs both witnesses' verification), Axiom 2 (each witness verifies the door on a path of its own, against its own log), Axiom 3 (the door's record of what it admitted and refused), T8 (the cluster floor), T16, T16c.

Coverage: proven that the act and its record are one step (`Record.step_records_at_act`, `step_records_once`); argued for the run-time check: the model has no door distinct from the gate, so a door that admits what both witnesses refused is not representable yet.

Serves: C1; and T28, T29 rest on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T28; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T18 · A shared cause turns a layer into one witness

Discovering that two witnesses share a failure cause the minting record does not declare (one library, one cloud, one person) is evidence
against the layer's independence. Until a witness is re-minted, the layer is a one-witness layer: every loosening at it stops (T8d), and
the finding is a stopgap catch (C∞). The failure-class list is part of the minting record (T9).

Derived from: the words (independent), Axiom 1 (two witnesses that share a cause are one), Axiom 2 (a discovered cause is evidence against the layer's independence), T8 (its clause d: every loosening at the layer stops), T9 (the list is the minting's).

Coverage: proven (`Layer.shared_cause_breaks_independence`, `independent_of_superlist`: a longer list only removes independence; `not_minted_has_shared_cause`; `DoT.not_minted_collapses`: a shared cause passes any act alone).

Serves: C22; and T-P rests on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T29; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T19 · "Wherever technically possible" is a record, never an escape

A place where the Duality cannot yet be built is an exception only as a record both witnesses approved, with a validity; it is counted as a
stopgap catch until it closes, and it must be approved again when its validity runs out. An exception that is not such a record is a breach.

Derived from: Axiom 1 (an exception is approved by both witnesses), Axiom 2 (it has a validity and is approved again when it runs out), Axiom 3 (it is a record), T16 (it is a loosening).

Coverage: undershoot. No theorem models an exception record; its validity is the shape of `Gate.stale_never_passes`.

Serves: C22.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T30; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T20 · The horizon

Absolute trust inside needs an absolute gate outside. Inside, a part is, for the act it is doing now, either fully trusted or not acting:
there is no partial trust, and nodes with varying levels of trust exist only outside. Inside, every point of use is a door; a fully trusted
part passes every one of them and never meets a refusal for what it is trusted for, so for it a forbidden act does not exist as an option;
any other part is refused at the first door it reaches. A value moves to any part trusted for its class with no further negotiation, which
is the near-infinite composability of the mission. The inside is ruled by the axioms, never by a party. An inside with no gate would be the
inside trusting itself, one witness for every act: the horizon and the Duality need each other.

The owner (19:52Z): "True information freedom can only exist under absolute rule, just like the infinite information-density of a
singularity can only occur inside the Event Horizon, because nature abhors a naked singularity."

Derived from: the words (inside, door), Axiom 1 (inside, for the act at hand a part is either fully trusted or not acting: the gate has one answer and no partial), Axiom 3 (a value moves to a part trusted for its class by its admission, with no further negotiation), T6.

Coverage: proven for the shape (`Recipe.decide_pass_iff`: a trusted part passes every door on its chain; `Gate.gate_pass_iff`: pass or not, no partial trust); argued for "a forbidden act does not exist as an option" and for the near-infinite composability (no theorem models a value's move).

Serves: C1; and T21, T26 rest on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T23; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T21 · Thin surfaces

An outside party holds no trust and needs none to deliver information. A surface's receipt of information into quarantine, and its record of
the receipt, are a dual-gated act of the surface part under its standing; admission is a separate dual-gated act, later. Until it is
admitted, the information is held as opaque bytes: stored and recorded, never interpreted, indexed or forwarded. The record of a receipt
cannot be made later than the receipt. Nothing at a surface drops an axiom; the owner's "two of three" (20:35Z) names which one cannot wait:
the record.

Derived from: the words (surface, admission, contains), Axiom 1 (the receipt and the admission are two dual-gated acts), Axiom 2 (an outside party holds no trust and needs none to deliver), Axiom 3 (the record of the receipt is written at the receipt), T6, T20, T4.

Coverage: proven that the record is written at the act (`Record.step_records_at_act`) and that what is not admitted is not read, interpreted or forwarded (`Floor.road_gate`); argued for the surface part's standing (`Recipe.Kind.surface` is a line kind; nothing models receiving from a part that holds no standing).

Serves: no constraint cites it; T23 rests on it. It is a constraint in disguise (what comes from outside enters as opaque bytes until admitted) that C12 or C13 should cite in part 3.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T25; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T22 · Retention

With the Duality silent, nothing is admitted and nothing sealed changes: a standing does not lapse because the outside vanished, and nothing
is loosened (altered, released, destroyed) with fewer than two witnesses. A party on its own may hold and tighten, never admit, grant or
promote. It may always go dark (a tightening); it may never wipe what it holds (a loosening of the record). Re-wrapping sealed material
under roots both halves already approved is holding, and one party may do it; new roots are a trust rotation. The information holds as
long as one copy and its roots survive; the one bound the axioms do not reach is the roots' cryptographic lifetime, set at the minting.

Derived from: Axiom 1 (nothing is admitted, altered, released or destroyed with fewer than two witnesses), Axiom 2 (a standing does not lapse because the outside vanished: the absence of evidence moves nothing), Axiom 3 (the record is never destroyed by fewer than both halves), G0 (new roots are a trust rotation), T8 (safety before liveness), T16.

Coverage: proven for "hold and tighten alone, never loosen" (`Standing.one_witness_tightens`, `one_witness_never_loosens`, `loosening_needs_both`); argued for re-wrapping, the roots' lifetime and "as long as one copy survives": no theorem models a key wrap or a copy.

Serves: no constraint cites it; T23 and T24 rest on it. It is a lemma of Axiom 3 and T16.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T26; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T23 · Containment

Non-CMOS information never interacts directly with CMOS information. Inside the perimeter it is admitted or contained. Admission (contained
to admitted) is a loosening: both witnesses, and only while a grant for it holds. Withdrawal (admitted to contained) is a tightening and
needs one witness, so no half can keep hostile content admitted; a lapse (a grant's validity running out) is not an act and ends the
admission by itself. Contained to outside is an export and needs both halves (T12). Contained to destroyed is the act
scheduled at containment: each contained item sits under a key of its own, and destroying that key on the date the law sets destroys the
item and nothing else; where an item cannot be re-wrapped under its own key (an append-only ledger), the contained copy is destroyed on
the date by a two-witness act scheduled at containment. Revoking a root does not destroy what it wraps. CMOS holds personal data only on
a grant with a validity; when the grant lapses the data is contained and destroyed by the legal date.

Derived from: the words (admission, contains), Axiom 1 (admission needs both halves), Axiom 2 (a lapse of the grant's validity ends the admission by itself), Axiom 3 (a record is destroyed by its date, by both halves), T6, T16 (withdrawal is a tightening on one witness), T21, T22, T4.

Coverage: proven for the transitions of a contained item (`Floor.road_gate`: only re-admission and destruction are offered; `Floor.road_evidence`: a lapsed key yields ciphertext; `Floor.road_record`: destroyed at its date; `Floor.destroyed_stays`) and for admission as a loosening and withdrawal as a tightening (`Standing.loosening_needs_both`, `one_witness_tightens`); argued for exports and for the key per item (no theorem models an export or a key wrap).

Serves: C3, C9, C12, C18; and T24, T25, T-P, T29 rest on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T27; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T24 · The trap, and the floor

Information inside the boundary reaches a part outside only by an export (both halves, a grant, a record). Contained information reaches no
part at all: no part is trusted for any act on it, so it is neither read, interpreted, forwarded nor exported; its only transitions are
re-admission and destruction. Nothing trapped crosses the horizon by any act; it remains until it is destroyed inside.

The substrate still radiates (electromagnetic emanation, timing, power, the designed counts of Axiom 3). Emission is not an act, so the
axioms cannot make it zero; the design makes it **minimal** (no channel beyond the counts) and **thermal** (encrypted or aggregated, so it
carries entropy and no information). This is the **entropy floor**: what an outside observer can learn of contained information is what
it can learn of random bytes of the same length, and of the inside as a whole only its size, its staleness and its rotation interval. The
horizon's evaporation time is the cipher's lifetime: whatever must never come out is destroyed before then, and the roots' cryptographic
lifetime is longer than the longest legal retention of anything they wrap, or the retention plan destroys first.

Derived from: the words (contains), Axiom 1 (no part is trusted for any act on contained information), Axiom 3 (the designed counts are all that leaves; the record is destroyed by its date), T6, T22, T23, T4; the floor is premise (physics, the cipher).

Coverage: proven for the trap and the decay (`Floor.road_gate`, `Floor.road_evidence`: once the key's validity ran out no read yields plaintext under any gate; `Physics.Entry.ext`: the record carries counts and never content); the floor itself (ciphertext is random bytes of the same length; emission is thermal) is premise and has no theorem.

Serves: C9; and T25 rests on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T31; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T25 · Three roads to the floor

Each of the three axioms alone brings contained information to the entropy floor of T24, by a road of its own:

- **By the dual gate alone:** no part is trusted for any act on contained information, so no act reads it (the trap). It stays at the floor
  where it lies.
- **By evidence alone:** the standing of the item's own key is evidence with a validity that is never renewed (contained items are
  excluded from every re-wrapping and rotation), and the key is released only on a live check of that standing. When the validity runs
  out the key can no longer be used, and the engine destroys keys whose standing lapsed. The item decays to ciphertext.
- **By the record alone:** containment is a record that carries its destruction date, bounded by the law's longest retention; the record
  outlives the act, and the engine executes every destruction its record schedules. The item is destroyed by its date.

Each road needs a construction of the engine (which acts it offers on an item, how keys are released, how scheduled destructions run).
Which engines must prove which roads is chapter 06 "The gravitational wave test".

Derived from: Axiom 1 (the gate road), Axiom 2 (the evidence road: the key's standing is evidence with a validity never renewed), Axiom 3 (the record road: the destruction is scheduled in the record), T23, T24; each road is construction of the engine.

Coverage: proven, one theorem per road (`Floor.road_gate`, `Floor.road_evidence`, `Floor.road_record`), each from its own construction only.

Serves: no constraint cites it; C9 and C3 (containment) should, in part 3.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T34; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T26 · The trust field (the VIBE field)

Only Milky Way members carry a vector: "Only actually Milky Way members have a vector, and every other node is just a node" (the owner,
2026-10-26). A **member** is a part whose standing includes contributing to Milky Way, granted by both witnesses. Every member inside the
declared boundary has a **depth**: the length of its shortest grant chain back to the pair, in the grant graph the record holds (never
network hops). Its **mass** is one plus the number of members that derive through it. Every other part inside is a **node** of the member
it derives through: it has no vector of its own and extends that member's boundary. A standing's **freshness** is the share of its
validity left since a witness last verified it live: the witness stamps it, the stricter witness counts, and nothing is fresher than its
grantor. A member's **shortfall** is what the boundary declares for it and its nodes minus what they hold, weighted by freshness. The
**VIBE field** (Variable Influence Balancing Expression, the owner's name, 2026-10-26) is mass times shortfall, per member; its sum is the
**potential**, zero exactly when the boundary holds what it declares.

- The balance follows the field downhill: refresh before a lapse, heaviest and stalest first, grantor before child. Restoration moves
  outward from the pair one layer per verification round.
- The evidence a part must give (chapter 06) rises with its nearness to the pair; windows lengthen with depth; a surface is the field's
  edge.
- **Member isolation.** The witnesses' refresh capacity is shared out by the members' vectors only, and a node is refreshed only out of
  its own member's share: nothing done to one member's nodes, however many it gathers, changes what another member's nodes receive.
- **The weight never votes.** Witnessing, majorities and lockstep are unweighted; the field adds levels of consequence and of proof
  demanded, never levels of trust (T20).
- Under the bounds the system's own acts never raise the potential; only losses and ageing do. The system is stable when the witnesses can
  verify at least as often as the standings age; below that it refreshes by the field and lets the edge go stale first.
- The two witnesses read the field per member; every other reader reads one number, the boundary's **temperature** (its mass-weighted
  staleness).

The formulas and their parameters are Gravity's constant (`CM.BlackHole/docs/gravity.md`, "The constant"); the parameters are
configuration (T9).

Derived from: the words (standing, record), Axiom 1 (the gate and the balance: restoration moves along the field), Axiom 2 (the field: source, depth, freshness; trust is a field, never a position), Axiom 3 (the grant graph is the record), T6, T9 (the parameters are configuration), T20 (the weight never votes), T16b; the graph, the readout and the members' shares are construction.

Coverage: proven for the laws over the parameters (`Field.n1_laws_hold`, `n1b_schedule_never_votes`, `n1c_stricter_demand_passes_less`), for the potential (`Field.k4_refresh_never_raises`, `n2_bounded`, `phi_zero_of_all_fresh`, `Theory.k4_stack_never_raises`, `stackPhi_zero_iff`), for depth and mass as functions of the recipe (`Recipe.digest_congr`), for member isolation (`Recipe.sibling_never_votes`) and for the weight never voting (`R1Mass.ms_hub_is_mass_majority`, `ms_mass_vote_is_one_witness`); argued for the freshness formula, the refresh order (heaviest and stalest first, grantor before child) and the temperature readout: no theorem models them.

Serves: no constraint cites it; it is the balance of Axiom 1 in numbers, and T27 rests on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T32; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T27 · The VIBE test

Two CMOS instances deployed from the same recipe span the same VIBE field, up to identity: an isomorphism of their grant graphs that keeps
declared roles, depths and masses, with the same shortfall per role. In the simulator on one injected clock the two fields are equal; in
the two proof chains the forward chain's expected field and the reverse chain's measured field agree layer by layer; and a pull request
moves the field only where its declaration moved. Each stable publishes a VIBE digest (the canonical field under role names, hashed) next
to its proof-run hash.

Derived from: Axiom 1 (the two proof chains are two witnesses; the balance), Axiom 3 (the digest is published next to the record of the run), T9, T26; the digest is construction.

Coverage: proven that the expected field is a function of the recipe (`Recipe.digest_congr`, `Cmb.file_determines`) and that the digest identifies the field, not the recipe (`Cmb.digest_not_injective`, `digest_alone_cannot_identify`: finding F7); argued for the simulator and for a pull request moving the field only where its declaration moved (no theorem models a declaration).

Serves: C7.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T33; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T-P · The pressing

A pressed instance (G0) is a one-witness system by construction, and its mark is the record that the second witness is missing.

- **Trust never crosses instances; information does.** Keys, signatures, tokens and standings of one instance are no evidence in another,
  pressed or minted. Information crosses only through an entry path the receiving instance's two witnesses opened, with provenance in the
  record, and can be traced and ejected later.
- Inside a pressed instance, loosening needs a fresh owner-signed challenge and tightening none: a policy that mirrors T16 so that the
  pressing rehearses the real rule.
- A pressed instance may run the stable channel's code, with the pressed mark on every artefact it issues, and it never claims to be
  DMP-compliant (T28); **stable company-wide** (C24) stays minted.
- The minting is a trust rotation: every key rotates, everything trusted before is untrusted until it regains trust under the new roots,
  the owner key is revoked everywhere and the owner role ends; there is no state in which some acts carry one witness and others two under
  the same roots.
- No minting without a passed pressing of the same configuration.
- **Never axiomatically sound; Gravity abhors it.** "Can a pressed CMOS instance ever be axiomatically sound. I say no, so Gravity abhors
  it" (the owner, 2026-10-26). The two proof chains check text against code and run, so each component of a pressed instance is proven
  exactly as a minted one's. The instance is not: every theorem that rests on the independence in Axiom 1 needs two witnesses that trace to
  two people, and in a pressed instance both trace to one, so one influence can bend the whole trust space onto a single point and expose
  the singularity (the one person who holds both witnesses). A configuration in which any influence can do that is out of spec for DMP.
  Gravity's verdict on a pressed instance is therefore "out of spec", never "proven" and never "proven relative to the pressing"; the
  pressing is a rehearsal of the real rule, not a weaker form of it.

Derived from: Axiom 1 (a one-witness system is out of spec), Axiom 2 (keys and standings of one instance are no evidence in another), Axiom 3 (information crosses only with provenance in the record), G0, T16, T16b, T23, T18; the mirror policy and "no minting without a pressing" are construction.

Coverage: proven for the collapse and the verdict (`Ground.pressed_single_control`, `Ground.pressed_collapse`, `Layer.DoT.not_minted_collapses`, `Recipe.pressed_root_not_wf`, `Recipe.pressed_root_collapses`, `Complete.Recipe.verdict_outOfSpec_iff`) and for "trust never crosses instances" (`Cmb.plan_refused_elsewhere`: a file is evidence only under its own pins); argued for the mirror policy and the trust rotation.

Serves: C24; and T28 rests on it.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): number unchanged; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T28 · Compliance is assembled, never claimed

"CMOS is, as a standalone appliance, not necessarily in a DMP compliant state. The right solution comes from proveably working system
components never claiming they are compliant when they are not, combined with a recipe for how to assemble them to form a self balancing
CMOS galaxy" (the owner, 2026-10-26).

- **A component proves what it does, and claims nothing more.** A component's proof covers its own behaviour at its own doors. It never
  states, on any surface, a compliance it has not been shown to have in the configuration it runs in; a claim beyond its proof is a
  refusal-worthy claim, not a description (Axiom 2: a claim is not evidence).
- **Compliance belongs to an assembly.** An instance of CMOS is DMP-compliant only as an assembly: proven components, put together by a
  recipe whose every step is itself checked (both witnesses of every gate trace to two people, every record written at its act, every
  boundary in place). A standalone appliance, an instance assembled off the recipe, and a pressed instance (T-P) are not compliant, and say
  so on every surface where they would otherwise be read as compliant.
- **The galaxy balances itself.** The recipe is written so that the assembled instance stays in spec without a person holding it there: a
  part that drifts out of spec tightens on its own (T16c) and is ejected at its door (T17), and the assembly's compliance is re-shown, never
  carried over (T8).

Derived from: Axiom 1 (compliance is the verdict of two chains on an assembly), Axiom 2 (a claim is not evidence: a component claims nothing beyond its proof), Axiom 3 (the recipe is the record of the assembly), T8, T16c, T17, T-P.

Coverage: proven for the assembly (`Recipe.verdict_proven_iff`: compliance is the verdict on the whole recipe; `Complete.Recipe.proven_extend`: it is assembled one checked line at a time; `Recipe.one_unproven_line_unproves`: no component is proven by its neighbours); argued for "says so on every surface" and for the self-balancing of the galaxy (the recipe is modelled, the running assembly is not).

Serves: C7, C24.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T35; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: CM coordinator
Enforced by: DMP-021

## T29 · The horizon is the one boundary between information and data

"Anything that can transition the event horizon without permission, no matter which surface it is erected against, is an immediate CVSS
10.0, because that is the ONE boundary separating information from data" (the owner, 2026-10-26).

Inside the Event Horizon is information: held under the dual gate, with its record and its provenance. Outside is data. A crossing in
either direction is an act (T17) and needs the dual gate's permission; a crossing without it, on any surface the horizon stands against (a
network boundary, an IM door, a store, a log, a model prompt, a file share, a backup, a side channel that carries content), breaks Axiom 1
at the boundary every other guarantee depends on. Such a finding is critical by definition, scored CVSS 10.0 where a score is reported,
and no class, scope, mitigation or exposure estimate rates it down.

Derived from: Axiom 1 (a crossing of the horizon is an act and needs the gate's permission), Axiom 3 (inside is information under the record and its provenance; outside is data), T23, T17.

Coverage: proven that a contained item crosses by no act (`Floor.road_gate`: send is not offered) and that nothing is performed without both verdicts (`Record.performed_only_with_both`); the severity rule (CVSS 10.0, never rated down) is a convention and has no theorem.

Serves: C12, C13.

Status: stable since DMP 0.9.0
Proposed in this pull request (not yet approved): renumbered from T36; Derived from rewritten against the three axioms; Coverage and Serves lines added; the sentence is unchanged.
Owner: Black Hole coordinator
Enforced by: DMP-021

## C1 · No act bypasses the gate

Every act, inside CMOS, into it or out of it, passes a door the dual gate decides and the record covers; there is no path the gate does not see, between parts or to the outside.

Derived from: Axiom 1 (the gate has no other way through), Axiom 3 (every use leaves a record), T20 (inside, every point of use is a door),
T17 (enforcement is itself an act both witnesses verify). That the door is **one** door (one universal I/O layer; parts never call each other
directly) is construction: it makes ejection total and the record one place, and a second door would need the dual gate between the doors.

Coverage: proven for the gate and the stack (`Gate.one_witness_never_acts`, `Record.performed_only_with_both`: nothing is performed without
both verdicts in the record; `Recipe.decide_pass_iff`: an act passes a line only when every layer on its chain passed it); argued for a running
system: that no component reaches another beside its door is shown per component by the evidence chain (chapter 06), not by the theory.

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:29Z (stable since DMP 0.1.0 before that).
Owner: Milky Way coordinator
Enforced by: DMP-008

## C2 · Every message is its own evidence

A receiver trusts a message on nothing but what it carries and what the receiver verifies itself, live: who sends it, that their key signed it, that they may send that kind, and when. One answer per input, failing closed; no message acts twice; where liveness cannot be verified, nothing verifies.

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

Derived from: Axiom 2 per message (L1 with T6; L3: evidence is live for one point of use), Axiom 1 (L2: one answer, fail closed; L3b:
when liveness cannot be verified, nothing verifies), T6 (L4), T13 (the validity window is "now" as evidence). The laws above are the
constraint stated for IM version 0 and lock its instance (one kind, one permission, one signer role); the general sentence is the constraint.

Coverage: proven for the laws, from the sentences (`r1l_L2_gives_L1`, `r1l_L1_gives_L4`, `r1l_L2_gives_L4`, `r1l_verify_table_order`, and
the counterexamples `r1l_alwaysRefuse_L1` to `r1l_alwaysRefuse_L4`) and from the model of the code (`r1b_L1`, `r1b_L2_clean`, `r1b_L3`,
`r1b_L3b`, `r1b_L4`), and at most once over any sequence of calls under the wave clock and under Lensing (`wv_verified_at_most_once`,
`ln_verified_at_most_once`); argued for the general sentence beyond version 0. Known and recorded, not hidden: a clock that moves back
lets the same frame verify twice (`r1bW_clock_rollback_replays`); L3 holds as worded and T13 forbids the clock.

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, the Law block unchanged, approved by the owner 2026-10-26 23:29Z (stable since DMP 0.1.0 before that).
Owner: Milky Way coordinator
Enforced by: DMP-018

## C3 · A value reaches only parts trusted for its class

A value carries its class and its provenance wherever it goes. A part not trusted for the class receives only the count, never the value, and revealing a value to a further class is a loosening, never a default.

Derived from: the words (admission names the class and the provenance), T3, T6 (a value a part is not trusted for never reaches it), T14
(counts always, content by grant), T16 (a reveal is a loosening), T23. A token on every value at a border, and the identification axis a value
carries, are construction of the shield (chapter 05). T1 (content reaches only a part trusted for its class; nothing is inside without both trust and admission).

Coverage: proven for the shape in a model with a class (gravity#17 `Flow.lean`: `value_reaches_only_trusted`, `untrusted_gets_count`, `no_delivery_outside_class`: no path delivers a value to a part outside its class; `widening_needs_both`: a reveal to a further class needs both witnesses; `Floor.road_gate` for a contained item); argued for the token on every value and the identification axis (construction, chapter 05). Why the gate alone could not carry it: `BreakC3.lean` (gravity#17), a delivery outside the class passes a gate that has no class.

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:29Z (stable since DMP 0.1.0 before that).
Owner: Milky Way coordinator
Enforced by: none yet

## C4 · A change to what a part speaks is a new part

A contract, what a part promises on its surface, changes only through the dual gate at a point both witnesses named, never mid-act and never silently, and a thing has one name. The information a productive part holds changes the same way; before production it carries no trust and is shaped freely.

Derived from: T3 (a changed contract is a new part, trusted by nothing by default; information before production has no standing), Axiom 1
(its trust has two witnesses: the promotion's two chains, the reviewed release), Axiom 3 (the change and the data are auditable because they
are records), T6 (a name is part of what was granted), T15 (a change to a law is an act in the same shape). The stable promotion as the point,
the register of contracts and the production point are construction (chapter 02 "Foundation bricks are complete", chapter 05 "Settings").

Coverage: argued. The nearest theorems are the frame rule (`Recipe.extend_preserves_decisions`: what is added changes nothing that exists), `Standing.loosening_needs_both`, and at the wire `R1Model.r1m_envelope_unknown_version` and `r1m_oversize_refused` (a frame of another version or size is refused: one name); nothing models a contract or its version.

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint and merged with C5 (financial data freezes at production), approved by the owner 2026-10-26 23:49Z (both stable since
DMP 0.1.0 before that).
Owner: CM coordinator
Enforced by: none yet

## C6 · Who may act on what is a bounded grant in the record

No part acts beyond its grant, a bounded record both witnesses can read. Outside CMOS's own estate an act needs both halves of its layer, anything irreversible their words per act, and widening what a part may do alone is a loosening. The standing grant to agents is the record below, word for word; rule DMP-009 refuses a change to it.

<!-- authority-grant:begin -->
> Agents may build, change and deploy CMOS's own estate on their own authority, using credentials held in the operations master, under plan, audit and four eyes where a second administrator exists. An act on a system or on information outside CMOS's own estate needs both halves of the layer it belongs to (T38), its organisational and its factual responsibility. Each half may declare advanced testing reached for its layer; until both have, every act there needs their words per act, and anything irreversible outside CMOS's own estate always does. Until the minting the owner's own words stand for both halves (G0).
<!-- authority-grant:end -->

The grant's citation "(T38)" reads T5 in this numbering; the wording between the markers is the owner's record and changes only with his approval (rule DMP-009 records its hash), so the number inside it is not moved here.

Derived from: T6 (trust is bounded: the acts a part may do are what both witnesses granted), Axiom 3 (the grant is a record, tamper-evident),
T5 (every layer outside CMOS's own estate has its organisational and its factual half), T16 (declaring advanced testing reached, and every
other widening, is a loosening), G0 (until the minting the owner's words are both halves). Which layers exist, who holds their halves, and the
wording of the grant are configuration (T9).

Coverage: proven for the shape (`Gate.gate_pass_iff` and `meet_pass_iff`: an act passes only what every witness on the chain passed, the
intersection of the grants; `Recipe.pass_has_two_independent_witnesses`: whatever passes was passed by a minted Duality on its chain;
`Standing.loosening_needs_both`); argued for the grant as a readable record with a bound (no theorem models a grant's wording or scope).

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, the grant unchanged, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.1.0, grant abstracted 0.9.5 before that).
Owner: CM coordinator
Enforced by: DMP-009

## C7 · What runs is what the record says

Every running part is deployed from the recipe, one recorded, pinned description of the whole, in the shape its place needs. What exists is what both witnesses can read and the chains proved, and nothing else runs.

Derived from: Axiom 3 (the recipe is the record of what exists), the words (a DMP-complete configuration includes the repository it is built
from, every dependency pinned), G0 (mint prep verifies every pin), T27 (the same recipe spans the same field), T28 (compliance is assembled
from a recipe, never claimed). One repository, the folder layout as the composition tree and the shapes are construction (chapter 02, DMP-004).

Coverage: proven for the recipe (`Recipe.file_determines`: the recipe read back gives the same verdict, digest and every decision;
`Recipe.digest_congr`; `Cmb.redeploy_is_recipe_field`, `Cmb.bigBang_keeps_the_proof`; `Recipe.verdict_proven_iff`); argued that a running
system is the one its recipe describes (that is the evidence chain per deployment, C25).

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.1.0 before that).
Owner: CM coordinator
Enforced by: DMP-004

## C9 · What is published holds nothing that is inside

Nothing inside leaves except by an export. What CMOS publishes, its code, its text, its public tree, holds no secret, no fact about the organisation that runs it and no person beyond a role; real values stay inside and are passed as parameters; the public tree holds no trust for anything inside.

Derived from: T12 ("leave CMOS" is an act with no trust by default), T23 (contained to outside is an export and needs both halves), T24
(contained information reaches no part outside by any act), T3, T6. The scan of the tree, the settings store and the licence are
construction and decisions (DMP-001, DMP-006, chapter 14 "The licence").

Coverage: proven for the trap (`Floor.road_gate`: a contained item is never read, forwarded or sent; `Floor.destroyed_stays`); argued for
a publication being an export (no theorem models a public tree).

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.1.0 before that).
Owner: CM coordinator
Enforced by: DMP-001, DMP-006

## C10 · CMOS is trusted only for acts on its own estate

CMOS acts only on what whoever holds authority over it holds authority over: never on a third party's systems, never harvesting or evading on anyone else's, and never testing a productive system without a record naming the signatory, the targets and the window. A request that would break this is refused. The wording is the charter, [CHARTER.md](CHARTER.md).

Derived from: T6 (trust is bounded to named acts on named parts), T3 (an act outside the estate has no trust), G0 (authority comes from
whoever holds authority over CMOS, outside CMOS), Axiom 3 (the scope file is the record). That every security-shaped brief carries its
one-line context is construction (DMP-002).

Coverage: argued. The gate shape (`Gate.one_witness_never_acts`) is the only theorem that bears; nothing models the estate's boundary.

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.1.0 before that).
Owner: Black Hole coordinator
Enforced by: DMP-002

## C12 · Position never grants, and routing reaches everything inside

One routing reaches everything inside the Event Horizon: the nearest place first, across the horizon last and only when nothing inside answers. Where information sits, and how a layer places information or work, never decides who may act on it; only its admission and the dual gate do. A new kind of information is a new layer that inherits the gate, the record and the placement and changes nothing else. A private place is invisible to routing: neither an answer nor its absence reveals what it holds, its record shows counts and never content, and no single loss removes it.

Derived from: the words (admission, contains, layer, door), Axiom 1, Axiom 2 (a position in the network is never evidence, so a place cannot
grant), Axiom 3 (counts always, content by grant), T8 (no single part's loss stops a place that holds information), T14, T23, T29 (every
crossing of the horizon is an act, so it comes last and only when needed), T4 (what no admission names is contained where it lies), T5
(every information layer has its own Duality), C1 (every route runs through the one door). The tiers, the net that routes, the layers in use,
the reorganisation by the field, and the floor of three nodes per private place are construction and configuration (chapter 05 "The
information tiers and the layers", chapter 14 "Ask the nearest tier first"). T1 (who may act comes from the admission and the gate, which gate each other).

Coverage: proven for position never grants (`Config.relayout_never_votes`, by reflexivity: placement is not an argument of the gate; `Field.n1b_schedule_never_votes`), for the routing order and the invisible private place (`tr_milky_way_first`, `tr_exit_last`, `tr_never_singular`, `tr_singularity_invisible`, `tr_first_scrub`), for a new layer changing nothing existing (`Recipe.extend_preserves_decisions`, `Recipe.extend_wf`) and for a layer reorganising only on both witnesses' own recomputation and healing from any state (`ms_accepted_agrees`, `ms_wrong_layout_refused`, `ln_signed_moves`, `st_self_stabilizing`, `st_no_root_takeover`); argued for "reaches everything inside" (the routing theorems prove the order and what is never returned, not that every item is reached: gravity finding F21) and for "no single loss removes it" (the node floor is T8's premise and has no theorem).

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.1.0, redrafted 0.9.3 before that).
Owner: CM coordinator
Enforced by: DMP-002

## C13 · The record inside is read before anyone outside is asked

No question crosses the horizon or reaches a person before every record inside that could answer it has been read; the answer names the record it rests on or says that none held it; what was learned outside is written back inside, so the next asker finds it there.

Derived from: Axiom 2 (evidence the asker verified itself: the record first, never a memory), Axiom 3 (the record is there to be read), Axiom 1
(the balance: what the boundary lacks is built by evidence: the write-back), T29 (a crossing is an act and comes last), C12 (one routing, nearest first).
The order of the tiers and the steps an agent takes are construction (chapter 14 "Ask the nearest tier first", "Knowledge goes back into
Tier 1").

Coverage: proven for the order (`tr_milky_way_first`, `tr_exit_last`); argued for "names the record" and for the write-back (no theorem
models an asker or an intake).

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.2.0, redrafted 0.9.3 before that).
Owner: CM coordinator
Enforced by: DMP-002

## C14 · An answer rests on every piece of evidence its author can verify

An answer rests on every read path its author can verify itself, joined, and names what is still unknown; a write path is read through its trail or its dry run, never by writing to find something out.

Derived from: Axiom 2 (only evidence the author verified itself), Axiom 1 (the balance asks for the complete answer, the bounds only forbid
the unsourced one; and a write to find something out is an act with no trust behind it, T3), Axiom 3 (the trail of past writes is
the record). Which paths exist and the lines an agent writes are construction (chapter 14 "Combine every path").

Coverage: argued. No theorem models an author joining sources; the bound (no unsourced answer) is C21's, the completeness is the balance's.

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.3.0 before that).
Owner: CM coordinator
Enforced by: DMP-002

## C15 · A write lands only on a state its writer verified live

In the owner's words (2026-10-25): "a write first reads the live state it will change and asserts what it expects: absent for a create, a named value for an overwrite." The read is live at the point of use, never an earlier value; when the expected state is not found, nothing is written; every write is read back and must show the wanted state; the write's target (the system, the tenant, the host, the account) is part of the grant.

Derived from: Axiom 2 (live state at the point of use; an earlier read is never evidence; the absence of the expected state is the absence of
evidence, and nothing moves), Axiom 3 (the read-back is the record of the act), T6 (the target is part of the grant). Retries, hard and soft
failure and the script pattern are construction (chapter 10 "Guarded writes").

Coverage: proven for the shape (`Gate.stale_never_passes`: evidence past its validity never passes; `Gate.guard_pass_needs_evidence`;
`Record.step_records_at_act`: the act and its record are one step, no path performs one without the other); argued for the expected state and
the read-back (no theorem models a write's expected state).

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.3.0 before that).
Owner: CM coordinator
Enforced by: DMP-012

## C16 · Widening who may use a feature on information is a loosening

A feature on an organisation's information reaches a wider circle of users only through two independent witnesses: one that explains how the information is handled and protected, and one that attacked it and proved the protections, sharing nothing with the first. Both records are readable by both halves of the information's layer.

Derived from: Axiom 1 (two witnesses: the builder who explains and the session that attacks), Axiom 3 (both pages from one template so both
halves can read them), T16 (a wider circle is a loosening), T5 (the organisational and the factual half of the information's layer). The
two stages, the register and the template are construction (chapter 14 "The data gate", DMP-013).

Coverage: proven for the shape (`Standing.loosening_needs_both`); argued for the independence of builder and attacker (a failure class the
minting declares, T9).

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.3.0 before that).
Owner: Black Hole coordinator
Enforced by: DMP-013

## C17 · The top layer is a Duality like every other

CMOS has no single owner: whoever administers it is one half, checked by the other half, the body of people the minting binds, and neither acts on the composition of CMOS alone; a new part at the top needs both halves' words, recorded (until the first minting, the owner's, G0). Every system keeps every other system in check while keeping it running in the best shape it can.

The two halves at the top have names (2026-10-25). **The Administrator**, always written with a capital The, is a mythical entity, not a
person: everyone who is allowed to fully administer CMOS, allowed both by whoever holds authority over CMOS and by CMOS itself. **LHC**,
the Lighthole Council, is the minting ritual of CMOS; the fellowship of people it binds together, its members, is the other half.

Derived from: Axiom 1 at the governance layer, G0 (`LHC pending`), T16b (lockstep: neither half grants itself more), T16c (every system
keeps every other in check), T5 (the layer's two responsibilities). The approval record of a new top-level part, and what the levels below
it are, are construction (chapter 02 "Adding a node", "Foundation bricks are complete"); the two names are definitions.

Coverage: proven for the shape (`Ground.minted_no_single_control`, `Layer.one_person_is_no_duality`, `Layer.same_part_is_no_duality`,
`Recipe.root_minted`: the galaxy at the end of every chain is minted; `Recipe.pressed_root_not_wf`); argued for "a new part at the top needs
both halves' words" (the register is construction, DMP-014).

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.3.0, "organisation" replaced 0.9.4 before that).
Owner: CM coordinator
Enforced by: DMP-014

## C18 · A weakness is evidence against what it claims, never against the part

Nothing inside cuts a part off: a part locked to a contract keeps its route. When the contract's algorithm or format turns unsafe, what the part claims through it is no longer trusted (a tightening), but the part keeps its standing until evidence stands against the part itself; until an independent path vouches for its identity, its traffic is contained with no more rights than before.

Derived from: T7 (a standing is withdrawn only on evidence against it; an unsafe algorithm is evidence against the algorithm), T8 (its
no-lockout clause: removing the last route cuts a half off), T16 (the withdrawal is a tightening, one witness), Axiom 2 (a path the part sits on is a position in the
network, never evidence by itself; the second path is evidence the receiver verifies), T6 (no more rights than before), T23 (contained until
then). That a locked contract is never broken by its own side, that a later version only adds, and that a corpus of every locked version
replays through every build, are construction (chapter 04 "Compatibility after the lock").

Coverage: proven for the route (gravity#17 `Routes.lean`: `after_single_act_route_remains`, `last_route_removal_refused`), for containment (`Floor.road_gate`) and for the tightening on one witness (`Standing.one_witness_tightens`); argued for the difference between evidence against an algorithm and evidence against the part (no model of a contract). The break without a route: `BreakC25.lean` (gravity#17).

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 22:56Z (stable since DMP 0.3.0 before that).
Owner: Milky Way coordinator
Enforced by: DMP-015

## C19 · Two halves on every served request: trust and information, each verified by the server itself

A part serves a request only with both halves of its layer on it, the trust half (who asks, under what standing) and the information half (what is asked, and that it is right to serve), each verified by the serving part itself at the point of use and never taken from a carrier. Neither half overrules the other, and a right to sign for one half counts only when the other half has signed it too.

The owner (2026-10-26): "One authority owns Trust, the other owns Information. To exist inside of DMP, they are required to keep each other
constantly in check and balance so that no element can overrule the other."

Derived from: Axiom 1 (two witnesses, each with full reach, gated only by the other, the stricter stands; the halves keep each other in
balance), Axiom 2 (a carrier's check is not the server's evidence), T16b (a grant to sign for a half is a lockstep act), T16c (a half
that contradicts the state both certified has incriminated itself), T5 (the two responsibilities of an information layer). Which parts hold
the two halves, and how their signatures travel in a message, are construction (chapter 04 "Serving at a warehouse"). T1 (the trust half and the information half gate each other on every act).

Coverage: proven for the shape (`Gate.gate_pass_iff`, `Gate.act_needs_both_with_evidence`, `Layer.DoT.gate_pass_needs_both`, `Recipe.pass_has_two_live_witnesses`: a pass at any line means two independent halves both passed on live evidence) and for the halves being one of each kind (gravity#17 `Stitch.typed_gate_needs_each_kind`: a pass needs a verdict of the trust kind and one of the information kind); argued for "never taken from a carrier" (no model has a carrier; the nearest is `Stitch.content_never_suffices`) and for the co-signed right to sign.

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:30Z (stable since DMP 0.3.0 before that).
Owner: Black Hole coordinator
Enforced by: DMP-016

## C21 · A statement is a write

A statement to a person or to the record is an act: it rests on a source the part read itself and names, or it does not land; where several records fit, every one is named and none is picked. C14 covers the question the author knows it cannot answer; this constraint covers the answer it only thinks it knows.

Derived from: the words (an answer an agent gives is an act), Axiom 1 (an act needs trust), Axiom 2 (trust needs evidence the part verified
itself; a memory is not evidence), Axiom 3 (the source named is the record), T3. The lines an agent writes (`Looked up:`) are construction
(chapter 14 "Look it up, don't guess").

Coverage: argued. No theorem models a statement as an act; until DMP 0.9.7 this rested on a premise, now the words carry it.

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.6.0 before that).
Owner: CM coordinator
Enforced by: DMP-002

## C22 · "Proven" is an act with two witnesses

"The entire point of CMOS is to never trust any one interconnected system" (the owner, 2026-10-25). That a part is proven is decided by two independent chains, one from the intent down to the code and one from the code up to the intent, sharing nothing beyond their declared roots and taking no result from each other. Proven is where both agree; a mismatch leaves the part unproven, turns the gate red and lets the stricter answer stand at run time until both agree again. The chains show that text, code and run agree; the text itself is verified only by a reader who did not write it. "This approach applies universally throughout CM, it has to be implemented wherever it is technically possible" (the owner, 2026-10-25).

Derived from: Axiom 1 (two independent witnesses for the act "this part is proven"), Axiom 2 (each reads its own source), T15 (a change
to a law is an act with a cold read), T18 (a shared cause turns the proof layer into one witness), T19 (where the second chain cannot be
built yet is a record with a validity, never an escape). Which engine carries which chain, the lemma ledger and the alarm are construction
(chapter 06 "The gravitational wave test").

Coverage: proven for the verdict (`Recipe.verdict_proven_iff`: proven exactly when the recipe is well formed and the ledger carries every
line; `Recipe.one_unproven_line_unproves`; `Cmb.sealed_needs_both`, `Cmb.sealed_proven_complete`); argued for the chains' independence, which
is checked per engine (gravity finding F3: the exporter is one step both kernels share, T18).

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.4.0 before that).
Owner: CM coordinator
Enforced by: DMP-002

## C24 · Restorable is shown, never claimed

A configuration serves a whole organisation only once its restoration from nothing has been shown, never claimed: every scenario of a signed catalogue passed its pass line in a sandbox, the most critical through a simulator, at least one on the real infrastructure, and both witnesses stood intact afterwards. The people who restore have what they need without the system that failed. The pass line's numbers are configuration.

Derived from: Axiom 2 (shown, not claimed), Axiom 1 (both chains intact afterwards), Axiom 3 (the run record), T8 (continuity after a loss),
T28 (compliance is re-shown, never carried over), T-P (a whole organisation runs on a minted instance, never a pressed one). The catalogue,
the pass line, the assistant and the bundle are construction (chapter 11).

Coverage: proven for the cold start from a sealed record (`Cmb.redeploy_iff`, `Cmb.bigBang_keeps_the_proof`, `Cmb.plan_refused_elsewhere`:
the plan is chosen by the live field, never the proof, and refused under other pins); argued for the catalogue and the pass line (chapter 11;
gravity finding F10 is open on the restoring environment's capability).

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.7.0 before that).
Owner: Black Hole coordinator
Enforced by: none yet

## C25 · A deployment is gated on the exact thing deployed, and removes no route

"When deploying any allowed configuration of CM to CMOS, DMP must always be obeyed" (the owner, 2026-10-25). A deployment, any promotion of a part to any channel, runs the gate on the exact commit it deploys, never on an earlier run, and never deploys on red; one that skipped the gate is not fully trusted and is ejected. No deployment leaves an administrator action without a supported route on the channel it serves: the known gaps only shrink, and a deployment that would remove the last route for an action is refused before it runs.

The rule has a history (the owner, 2026-10-25): the stable channel once served a client that could no longer change a setting the owner
needed, with no other supported route left. "We MUST learn from this, so when configuring an impossible situation, we must create rules that
enforce it never happens again."

Derived from: Axiom 1 (a deployment is an act; the balance: the gaps only shrink), Axiom 2 (checked on the exact commit, not an earlier run),
T8 (its no-lockout clause: removing the last route cuts a half off). Channels, the route register, its cap and the workflow register are
construction (DMP-020).

Coverage: proven for no lockout in a model with a route (gravity#17 `Routes.lean`: `last_route_removal_refused`: the act that would remove the last route is refused before it runs; `after_single_act_route_remains`; `gaps_only_shrink`), and the break without one is `BreakC25.lean`; proven for the verdict on the exact thing (`Recipe.verdict_proven_iff`, `Recipe.one_unproven_line_unproves`: one line the chains do not carry unproves the whole); argued for "on the exact commit, never an earlier run" (`Gate.stale_never_passes` is the shape, evidence read at another step never passes; nothing models a commit).

Status: stable since DMP 0.9.7
Proposed in this pull request (not yet approved): restated more simply, saying the same (part 3 of the verifying session); Derived from and Coverage relinked to the renumbered theorems and to the Lean of gravity#17.
Amended: recast as a constraint, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.8.0 before that).
Owner: CM coordinator
Enforced by: DMP-002, DMP-020
Not yet checked in cm: the tie between the actions named in the audit log and `DMP/routes.txt`, and the plan's refusal of a
deployment that would remove a route. The administration tool's own test holds them until its code moves into cm;
DMP-020 checks the gate on every deployment workflow, the route register, its cap and its ratchet.

## C∞ · The root constraint: what is not fully trusted is ejected

"Everything that is not fully trusted is automatically ejected" (the owner, 2026-10-25). This is the thesis of DMP, the root constraint
that every other constraint refines, and its permanent stopgap. Its reserved number is C23; it is written C∞ because it always stands
last: every new section of this chapter is inserted above it, so whatever the sections above do not catch, it does. **Fully trusted** means what the dual gate says; at the proof layer its two
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

Coverage: proven for the thesis (`Gate.one_witness_never_acts`, `Gate.act_needs_both_with_evidence`, `Record.performed_only_with_both`: nothing
acts, and nothing is performed, without both witnesses on live evidence); the meta-rule is not a theorem and has no coverage to claim.

Status: stable since DMP 0.9.7
Amended: named the root constraint and given its Coverage line, approved by the owner 2026-10-26 23:49Z (stable since DMP 0.5.0 before that).
Owner: CM coordinator
Enforced by: DMP-002, DMP-017
