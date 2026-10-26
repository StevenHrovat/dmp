# E — Prior-art research, round 1: DMP (the Dark Matter Protocol)

Reviewer E, round 1, independent verification team. Date of report: 2026-10-26. I did not write DMP; my value is independence and knowledge of the literature.

**Inputs read in full:** `src/dmp/README.md`, `CHARTER.md`, `00-preamble.md`, `01-constitution.md`, `02-names-and-hierarchy.md`, `04-im.md`, `05-milky-way.md`, `06-black-hole.md`, `10-code-quality.md`, `11-test-design.md`, `14-process.md`, `SETUP.md`. Chapters 03, 07–09, 12–13, 15–16 do not exist in the tree (reserved numbers).

**Method:** idea inventory built from DMP's own text in its own priority order; per idea, 2–3 nearest published/deployed prior-art candidates, the precise delta, and a verdict (genuinely-new / new-combination / already-standard) with 0–100% confidence. Web use was read-only citation identification and verification (search engines, arXiv, publisher/standards pages); no authentication, no writes, no GitHub repository access, nothing installed. Citations marked *(verified)* were re-checked this session; ones marked *(knowledge)* are standard works cited from domain knowledge whose venue I did not re-open this session. Novelty is never provable; verdicts are argued judgements.

---

## Idea inventory (DMP's own priority order)

| # | Idea | Where DMP states it |
|---|---|---|
| I1 | The Duality of Trust / dual gate: two independent witnesses per layer, stricter answer stands | 01 §Axiom 1, §the words, T1, T38, C19; 04 §IM v1 |
| I2 | Evidence and record axioms: live evidence at the point of use; records written at the act; counts, never content | 01 §Axiom 2, §Axiom 3, T2, T21; 04 §refusal log |
| I3 | Monotone trust: default-deny; tighten with one witness, loosen only with two; lift conditions named | 01 §T0, §T24, §Axiom 4; 04 §v1 orders |
| I4 | Axiom-terminated trust chains; G0 the stated, not derived, ground; the axioms apply to themselves | 01 §the words, §G0, T22, C∞ |
| I5 | Machine-checked compliance of a configuration (Gravity/Lean; two independent proof chains C22; second kernel; DMP-complete; lemma ledger) | 01 §words (DMP-complete), C22, T35; 00 §Law blocks; 06 §lemma ledger; SETUP.md |
| I6 | IM: closed action language; every message verifies itself; ordered fail-closed verifier; one door; composition closure ("a network of nodes is a node"); version lock | 04 (whole chapter), 01 §C1, C2, C18, C19 |
| I7 | Minting, pressed instances, White Keys, trust rotation; dwarf galaxies (tenant isolation) | 01 §G0, T-P, T5, C17; 00 §who maintains it; 11 §arming |
| I8 | Root chain, vendoring-by-hash, self-contained configuration, universal SETUP.md with hashes | 00 §the root chain; SETUP.md (whole) |
| I9 | Containment / Event Horizon: data boundary, privacy and credential singularities, entropy floor, CVSS 10.0 by definition, T37 collapse | 01 §T19, T25–T27, T31, T34, T36, T37, C12 |
| I10 | Two-body governance: The Administrator + LHC; organisational + factual halves per information layer; SME weigh-in | 01 §C17, T38; 14 §rules need the expert |
| I11 | Risk-tiered assurance (Supernova classes) and AI-agent red-teaming (GRB, R136a1 flag, escape ring, independent session) | 06 (whole chapter); 11 §tiers |
| I12 | Continuity, lockstep, self-correction, split-brain orders, time as a witness | 01 §T3, T6, T20, T24b, T24c, T28, T29; 04 §isolated state |
| I13 | The VIBE trust field (depth, mass, shortfall, potential, temperature) and restoration scheduling; VIBE isomorphism test | 01 §T32, T33, Axiom 4 |
| I14 | C∞ stopgap: counted catches, axiom-refinement loop, parsimony | 01 §C∞ |
| I15 | Agent authority: word-locked grants, plan/audit/four-eyes, guarded writes (read-expect-verify), advanced testing, data gate | 01 §C6, C15, C16, C21; 10 §guarded writes; 14 §advanced testing |

---

## I1 · The Duality of Trust / dual gate

**DMP's claim:** A part acts only while two *independent* witnesses, each with full reach and gated only by the other, trust it; where they disagree the stricter answer stands; this holds at every layer, including information layers (T38) and the proof layer (C22). Independence is defined relative to a declared failure-class list (01 §words; T29). Axiom 1, 01-constitution.md; the owner calls the Duality "the single concept that goes through every layer and every concept of DMP."

**Nearest prior art:**

1. J.H. Saltzer, M.D. Schroeder, "The Protection of Information in Computer Systems," *Proceedings of the IEEE* 63(9), 1975 — the *separation of privilege* principle ("where feasible, a protection mechanism that requires two keys to unlock is more robust and flexible than one that allows access with only a single key") and the two-person rule, on the same page as fail-safe defaults and complete mediation. https://web.mit.edu/saltzer/www/publications/protmult.pdf (verified)
2. PCI DSS v4.0, PCI Security Standards Council, 2022 — Requirements 3.6–3.7 mandate dual control and split knowledge for cryptographic key custodianship; NISPOM / 32 CFR Part 117 mandates two-person integrity (TPI) for classified material. (verified, secondary sources)
3. A. Shamir, "How to Share a Secret," *Communications of the ACM* 22(11):612–613, 1979 — the (m,n)-threshold formalism underlying every "majority of trust" (T5) and 3-of-5 White Key rule. https://doi.org/10.1145/359168.359176 (verified)

**Delta [argued]:** Dual control, maker-checker, TPI and m-of-N quorums are among the oldest ideas in security administration; nothing in "two must agree" is new, and DMP's own toolchain (threshold White Keys, dual signatures) instantiates them. What is DMP's own: (a) the *axiomatisation* — dual agreement is the gate from which theorems are derived rather than a control checklist item; (b) *universality across layers*, including information governance (organisational + factual halves, T38) and the proof layer (C22 makes two proof chains the two witnesses of "this layer is proven" — that last move has no standard counterpart); (c) independence defined operationally against a *declared failure-class list* that is itself configuration (T4), with a discovery procedure when it is violated (T29); (d) the trust configuration owned by the Duality, never by the governed system (T4).

**Verdict: new-combination — confidence 80%.**

---

## I2 · Evidence and record axioms (verify live; counts, never content)

**DMP's claim:** A witness trusts only on evidence it verified itself at the point of use — never a carrier's check, an earlier read, or network position (Axiom 2); every act leaves a record written at the act, readable by the witnesses, with retention bounded by law and destruction only by both witnesses (Axiom 3); readers without a grant see counts only (T21; 04 §refusal log). Silence alarms but never isolates (T2).

**Nearest prior art:**

1. NIST SP 800-207, S. Rose et al., "Zero Trust Architecture," August 2020 — tenets: no implicit trust from network position or asset ownership; access decisions per-session; dynamic policy; continuous monitoring; PDP/PEP separation. https://csrc.nist.gov/pubs/sp/800/207/final (verified). "Verify explicitly at the point of use, never trust a carrier's check" is substantially the zero-trust posture.
2. B. Schneier, J. Kelsey, "Secure Audit Logs to Support Computer Forensics," *ACM TISSEC* 2(2):159–176, 1999 — forward-secure, tamper-evident audit records; foundation of the secure-logging literature. (verified)
3. B. Laurie, A. Langley, E. Kasper, "Certificate Transparency," RFC 6962, June 2013 — public append-only Merkle logs as verifiable records outliving the acts they record; A. Haeberlen, P. Kuznetsov, P. Druschel, "PeerReview: Practical Accountability for Distributed Systems," *SOSP 2007* — records that let peers re-derive and challenge each node's behaviour. (verified)

**Delta [argued]:** Each ingredient is standard: point-of-use verification (zero trust), tamper-evident records (Schneier-Kelsey, CT), aggregate/metadata-only telemetry (standard privacy-by-design practice, and DMP's CHARTER.md itself uses canary tokens, a Thinkst-popularised standard). DMP's own part is the packaging as axioms with specific teeth: the record must be *written at the act* (not reconstructible later); *every* witness of the act can read it in full; destruction requires both witnesses; retention is a two-sided legal bound; and a standing is defined as "evidence with a validity," so expiry is a lapse, not evidence (T2) — a precise refusal of the common "silence = failure" heuristic of heartbeating systems.

**Verdict: new-combination — confidence 70%.**

---

## I3 · Monotone trust: tighten alone, loosen with two

**DMP's claim:** Default is no trust and no act (T0). A witnessing half may tighten its own trust at once; *everything that loosens needs both witnesses* (T24); every tightening must name its lift condition in its record; the system's own acts never raise the potential / never loosen (Axiom 4, T32). In IM v1 the same asymmetry is on the wire: an isolate order needs one signature, lift/override two (04 §orders and the White Key).

**Nearest prior art:**

1. Saltzer & Schroeder 1975 — *fail-safe defaults* ("base access decisions on permission rather than exclusion"; default is no access), the grandfather of T0; *complete mediation* underlies "every input gets exactly one answer." https://web.mit.edu/saltzer/www/publications/protmult.pdf (verified)
2. A. Ferreira, D. Chadwick, P. Farinha et al., "How to Securely Break into RBAC: The BTG-RBAC Model," 2007 — break-the-glass: emergency overrides are permitted, logged and audited after the fact, i.e., loosening is exceptional and always recorded, tightening/restriction is the default state. (verified; venue from knowledge: IEEE ICTAI 2007)
3. Shamir 1979 (see I1) — every "unseal/unlock needs k-of-n" design in HSMs, escrow and break-glass accounts (e.g., cloud "break-glass" emergency accounts with dual approval — Microsoft/AWS guidance, knowledge) is the two-to-loosen rule for specific doors. (verified for Shamir)

**Delta [argued]:** Default-deny and "unlocking needs two keys" are standard; break-glass literature already treats loosening as the recorded exception. DMP's own contributions: the *explicit monotonicity axiom over witnesses* (one witness may tighten its own gating unilaterally, no witness may loosen without the other — including that neither half can remove the other, T24); the *named lift condition* requirement on every tightening, independent of the isolated part ("a stolen-key isolation lifts on nothing that key signs" — an unusually crisp anti-deadlock/anti-self-release rule); and the theorem that a one-sided loosening attempt is itself evidence (T24c).

**Verdict: new-combination — confidence 75%.**

---

## I4 · Axiom-terminated trust chains and the G0 ground

**DMP's claim:** Every trust chain ends at an axiom; the minting (G0) that creates the first witnesses is "stated, not derived" and happens outside CMOS, by people the owner already trusts; until then the owner's words stand for both halves with `LHC pending`; the assumption register lists everything no chain reaches (the DMP text itself, the prover's logic, time authorities, shared machines). The axioms apply to themselves: a law change is an act under the gate (T22).

**Nearest prior art:**

1. Trusted Computing Group, "TPM 2.0 Library Specification," 2019 (and the earlier root-of-trust-for-measurement chain of TCG 2004+) — hardware root of trust, measured boot: every chain of trust terminates in an implicit, unprovable root. https://trustedcomputinggroup.org (knowledge)
2. IANA DNSSEC Root KSK key ceremonies (https://www.iana.org/dnssec/ceremonies) and CA root ceremonies under CA/Browser Forum Baseline Requirements + NIST SP 800-57 Part 1 Rev.5 / SP 800-133 — the operational practice of installing a self-signed, self-asserted trust anchor by multi-party ceremony. (verified)
3. Trusted Computer System Evaluation Criteria (DoD "Orange Book," DoD 5200.28-STD, 1983) — the Trusted Computing Base concept: every assurance argument rests on a named, non-verified base of hardware/software plus assumptions; and epistemically, K. Gödel, "Über formal unentscheidbare Sätze…," *Monatshefte für Mathematik und Physik* 38, 1931 — no sufficiently strong formal system certifies its own axioms (which DMP's C∞ openly concedes). (knowledge/verified)

**Delta [argued]:** "Chains must terminate somewhere unproven" is the standard situation of all PKI/TCG systems, and every theorem prover has a trusted kernel. DMP's own moves: the termination point is *a text of axioms about trust itself* (not a key or a chip), the ground is a *named, explicitly non-derived* axiom (G0) rather than a quietly assumed root, everything the chains cannot reach is enumerated in an assumption register rather than hidden, and the constitution's self-application rule (T22: changing a law is an act gated by the law) plus the C∞ concession that "no formal system can prove that its axioms match the world" is an unusually honest version of what TCG documents as vendor assertions.

**Verdict: new-combination — confidence 65%.**

---

## I5 · Machine-checked compliance of a configuration (Gravity, two chains, DMP-complete)

**DMP's claim:** A configuration is DMP-complete when every theorem holds for all of it and *both proof chains* carry it: the intent chain proves forward (DMP → IM → CM), the evidence chain proves in reverse from what is actually there (code, running state) up to DMP; neither takes results from the other; they share nothing they could fail together; a layer counts as proven only when both agree (C22). The proof toolchain itself runs each proof through two independent kernels (Lean + a second kernel: lean4export + nanoda, SETUP.md). A component proves only its own behaviour; compliance belongs to the assembly, never claimed by a component (T35). Sections carry `Law:` blocks with hash-locked law files (00 §the marks); every proven IM command is a lemma in a ledger (06).

**Nearest prior art:**

1. G. Klein et al., "seL4: Formal Verification of an OS Kernel," *SOSP 2009* — machine-checked refinement chain abstract spec → design → C code; the canonical "proven configuration of a whole system stack, continuously re-checkable." https://sigops.org/s/conferences/sosp/2009/ (verified)
2. A. Pnueli, M. Siegel, E. Singerman, "Translation Validation," *TACAS 1998*, LNCS 1384, pp. 151–166 — instead of trusting the compiler, validate each produced artifact pair against the source; the direct ancestor of DMP's "evidence chain" (prove from the artifact upward that it obeys the spec). https://dblp.org/rec/conf/tacas/PnueliSS98 (verified). Companion: G.C. Necula, "Proof-Carrying Code," *POPL 1997* — artifacts shipping with machine-checkable proof obligations. (verified)
3. Y. Bartal, A. Mayer, K. Nissim, A. Wool, "Firmato: A Novel Firewall Management Toolkit," *IEEE S&P 1999*, pp. 17–31 — high-level policy compiled into a verified concrete configuration, with conformance enforced; extended journal version ACM TOCS 22(4), 2004. (verified). Near-miss for the "compliance is evaluated per assembly, not claimed by components" rule: Common Criteria (ISO/IEC 15408) EAL1–7 evaluation of a TOE in its intended environment. (verified)

**Delta [argued]:** All three lines exist: verified stacks (seL4), artifact-upward validation (translation validation), policy-to-config conformance (Firmato), and per-assembly evaluation (Common Criteria); two-kernel proof checking is established practice (DMP itself uses the community's second Lean kernel; Metamath's set.mm has independent verifiers — knowledge). DMP's own combination: (a) the compliance target is a *trust constitution* (axioms + theorems) rather than functional correctness or a firewall policy, applied to an entire AI-run company stack; (b) the two-chain rule makes *verification itself* subject to the dual gate (two independent engines as the two witnesses of "proven" — the strictest form of the two-kernel idea, elevated to an axiom); (c) compliance is continuous (every pull request, `tools/verify`) rather than a periodic certification; (d) `DMP-complete` is a *predicate over a configuration* (repository + pins + provers included), which is a new demand on what counts as "the system under proof."

**Verdict: new-combination — confidence 70%.**

---

## I6 · IM: the closed action language and its closure theorem

**DMP's claim:** Every action between parts is spoken in IM; a message passes only with both signatures (C19); the verifier applies 16 ordered rules, fails closed, has no debug switch or allow list (04 §verify rules); every message verifies itself (signed envelope carrying its token); a version is IM only with its own composition proof; the stated theorem: "a network of nodes that meet DMP is itself a node that meets DMP," proved in the evidence chain, with the door abstraction as the load-bearing element and inductive carry across scales; IM is forever backwards-compatible once locked (C18); no negotiation, one algorithm, canonical encoding.

**Nearest prior art:**

1. R. Canetti, "Universally Composable Security: A New Paradigm for Cryptographic Protocols," *FOCS 2001*, pp. 136–145 — the composition theorem: protocols proven secure in isolation remain secure under arbitrary composition with arbitrary other protocols. This is the literature's gold standard for "a network of secure nodes is a secure node." https://eprint.iacr.org/2000/067 (verified)
2. M. Jones, J. Bradley, N. Sakimura, "JSON Web Token (JWT)," RFC 7519, May 2015 — the self-contained signed claims token verified without the issuer (IM's token is the same pattern with ECDSA P-256 and a permission list); A. Birgisson, J.G. Politz, Ú. Erlingsson, A. Taly, M. Vrable, M. Lentczner, "Macaroons: Cookies with Contextual Caveats for Decentralized Authorization in the Cloud," *NDSS 2014* — attenuatable credentials with caveats. (verified; venue corrected from my first guess — it is NDSS, not NSDI)
3. D. Dolev, A.C. Yao, "On the Security of Public Key Protocols," *IEEE Transactions on Information Theory* 29(2), 1983 — the default adversarial model (attacker controls the network, messages are checked per message) behind every ordered fail-closed verifier; near-miss for ordered rule evaluation with reasons: firewall/IDS rule-base design and verification literature (see Firmato, I5). (knowledge/verified)

**Delta [argued]:** The parts are thoroughly standard: signed self-contained tokens (JWT; DMP itself cites GitHub's stateless tokens in 10 §credentials), replay caches, ordered fail-closed rule tables, mTLS, strict canonical encodings, PKI with EKU-like roles (IM's certificate roles are X.509 EKU under a private arc). DMP's own parts: (a) the *closure claim stated as a theorem with a proof obligation in the repo* — "network of nodes is a node," with the door (both signatures at every boundary between scales) as the condition and a named counterexample lemma (`echo_alone_not_robust`) — this is a UC-flavoured composition result transplanted into an applied trust constitution, not a UC result itself; (b) C18's *permanent backwards compatibility with contained degradation* (a locked version is never broken; the weakness is contained by a proxy path, re-signed with no more rights) — I know no standard that commits to keeping a cryptographically broken wire version spoken forever with containment, and that is a genuinely distinctive design stance; (c) the dual-chain token intersection (security + operational chains co-signed by the two masters, permission = intersection) — dual-CA attestations exist (attestation plus inventory), but the co-signature rule ("A grant counts only when the other master has signed the same authority too") is DMP-specific.

**Verdict: new-combination — confidence 60%.**

---

## I7 · Minting, pressed instances, White Keys, trust rotation

**DMP's claim:** The minting is a ceremony that forms the LHC and creates the White Keys; it is a total trust rotation (every key rotates, the owner role ends, ultimate authority moves to White Key holders under a majority); a *pressed* instance is a rehearsal with both witnesses tracing to one person, marked on every artifact, and the prover's verdict on it is "out of spec," never "proven"; pre-mint acts are ratified or revoked by record class, never one by one; no minting without a passed pressing; a dwarf galaxy trusts its main galaxy and never its siblings (multitenancy).

**Nearest prior art:**

1. IANA DNSSEC Root KSK ceremonies (https://www.iana.org/dnssec/ceremonies) — scripted, witnessed, audited multi-party creation/rotation of the root trust anchor, with Recovery Key Share Holders (a literal 3-of-7-style quorum of smart cards); NIST SP 800-57 Part 1 Rev.5 and SP 800-133 codify key-generation ceremonies, multi-person control and rotation. (verified)
2. Shamir 1979 (see I1) + break-glass account practice (BTG-RBAC, Ferreira et al. 2007; cloud break-glass accounts, knowledge) — k-of-n hardware-token override with PINs is the standard recovery-root pattern; DMP's 5 White Keys / majority 3 is an instance. (verified)
3. NIST SP 800-145, P. Mell, T. Grance, "The NIST Definition of Cloud Computing," 2011 — multitenancy as the norm: tenants trust the provider and never each other; isolation between tenants is the provider's core guarantee (dwarf galaxies). (knowledge)

**Delta [argued]:** Ceremonies, quorum hardware keys, rotation and multitenant isolation are standard practice, and DMP does not materially change them. The genuinely novel pieces are definitional, not cryptographic: (a) the *pressed/minted distinction as a first-class trust state* — an instance whose two witnesses trace to one person is formally "out of spec" even if every component is proven, because every theorem resting on Axiom 1's independence fails; marking that status on every artifact is a designed novelty; (b) *ratification/revocation of all pre-mint acts by record class and hash range* at the minting, rather than replay or blanket acceptance; (c) the minting defined as the one act that re-grounds the Duality from outside after loss of a whole half (T3/G0) — the split-brain "pick a winner" and override orders (04 §orders) are the operational complement and again are DMP's own grammar, though break-glass arbitration itself is standard.

**Verdict: new-combination — confidence 70%.**

---

## I8 · Root chain, vendoring-by-hash, DMP-complete self-containment, universal SETUP.md

**DMP's claim:** Each root repository depends only on the ones before it, one direction; "to hold a repository" is a byte-for-byte copy plus a pin (source, commit, version, sha256 over files in ordinal path order); a copy that stops matching its pin is refused; a minted configuration carries *every* dependency (packages, toolchains, proof engines, images) inside its repository pinned by hash, so it can heal itself with no network (T3, the words "DMP-complete"); SETUP.md lists every toolchain with version, source and hash and every host, and `check-setup.sh` fails a repository needing something unlisted.

**Nearest prior art:**

1. E. Dolstra, "The Purely Functional Software Deployment Model," PhD thesis, Utrecht University, 2006 — Nix: every package identified by a cryptographic hash over *all* its inputs; components immutable; deployments reproducible and hermetic; the direct ancestor of "the configuration is complete in itself and pinned by hash." https://edolstra.github.io/pubs/phd-thesis.pdf (verified)
2. C. Lamb, S. Zacchiroli, "Reproducible Builds: Increasing the Integrity of Software Supply Chains," *IEEE Software* 39(2):62–70, 2022 (arXiv:2104.06020, 2021) — bit-for-bit reproducibility and verifiable correspondence of artifacts to sources. (verified; venue corrected — IEEE Software, not CSUR)
3. S. Torres-Arias, H. Afzali, T.K. Kuppusamy, R. Curtmola, J. Cappos, "in-toto: Providing Farm-to-Table Guarantees for Bits and Bytes," *USENIX Security 2019*, pp. 1393–1410; and SLSA (Google, 2021, slsa.dev) — signed attestations over every supply-chain step, with SLSA build levels explicitly demanding pinned, hermetic builds. (verified; venue corrected — USENIX Security, not CCS; go.sum/Cargo.lock vendoring is the everyday form.)

**Delta [argued]:** The mechanism — hash-pinned, hermetic, offline-verifiable, self-contained configurations — is standard and mature; "already-standard" would be fair for the mechanism alone. DMP's additions are of degree and placement, not kind: (a) the *specification text itself* is what travels down the root chain byte-for-byte with its pins, so the constitution, the prover and the code are one pinned unit (spec-as-vendored-artifact is the unusual part); (b) self-containment is elevated to a *gate predicate* ("DMP-complete") with the refusal "needs anything from outside its repository counts as unproven"; (c) a universal setup register with a *completeness check on the register itself* (a repo needing an unlisted thing fails) — a constitutionalisation of the SBOM idea (SBOM frameworks such as SPDX/CycloneDX describe; DMP's check refuses).

**Verdict: new-combination (mechanism already-standard) — confidence 80%.**

---

## I9 · Containment and the Event Horizon (data boundary, singularities, entropy floor)

**DMP's claim:** Nothing enters that does not leave unless both halves permit, with a record (T19); unadmitted information is contained *at the item itself* — containment follows from absence of trust, no boundary definition needed (T37 collapse); until admission, material is opaque bytes (T25); contained items sit under per-item keys with scheduled destruction (T27); the only escape of information to an outside observer is a "thermal" entropy floor (T31); any unauthorised crossing of the horizon, on any surface, is critical by definition, CVSS 10.0, never rated down (T36); privacy and credentials are "singularities" — routing behaves as if they were empty, neither an answer nor its absence reveals content, and a part trusted for the class acts at the singularity itself (C12).

**Nearest prior art:**

1. J.A. Goguen, J. Meseguer, "Security Policies and Security Models," *IEEE S&P 1982*, pp. 11–20 — noninterference: one group's actions must not affect what another group can observe; the formal ancestor of "neither an answer nor its absence reveals what a singularity holds." (verified)
2. Data-loss-prevention egress control and data diodes (hardware one-way gateways, e.g., Owl Cyber Defense; NIST-aware DLP literature) plus PCI tokenization (PCI Security Standards Council tokenization product security guidelines, 2013ff) — "credential/secret routes to the point of use, the secret itself never moves" is exactly tokenization/vaulting practice; opaque-until-admitted quarantine is standard DLP staging. (knowledge/verified-secondary)
3. L. Spitzner, "Honeytokens: The Other Honeypot," SecurityFocus, July 2003; Thinkst Canarytokens (canarytokens.org) — the canary-token mechanism DMP's CHARTER.md and shield adopt verbatim as a leak detector is itself a standard, which DMP openly uses (so this is not an overstatement risk, but shows the lineage). (verified)

**Delta [argued]:** The ingredients (egress default-deny, tokenization, quarantine, canaries, noninterference as the privacy property) are all standard. DMP's own contributions are formal and policy-shaped: (a) T37 *derives* containment from the axioms (no admission → no trusted part → no act → the item's own boundary contains it) instead of stipulating a container — an elegant inversion of DLP, which needs a container product; (b) the *entropy floor* framing (emission is non-zero but must be indistinguishable from random bytes; evaporation time = cipher lifetime; retention destroys before that) is a coherent crypto-agility/retention policy stated as physics, which I have not seen spelled out this way in standards; (c) T36's *severity-by-definition* (any horizon crossing is CVSS 10.0, immune to rating-down) is a governance rule, not a technical mechanism — CVSS as a standard does not permit policy overrides of its score bands, so this operates inside DMP's own reporting only [argued; see Questions]. The dwarf-galaxy multitenancy (00 §who maintains it) is standard SaaS isolation restated.

**Verdict: new-combination — confidence 65%.**

---

## I10 · Two-body governance; organisational + factual halves per information layer

**DMP's claim:** CMOS is controlled by the unity of The Administrator and the LHC (C17); every information layer's DoT is one organisational half (accountability: purpose, cost, who may use) and one factual half (truth: the subject-matter expert), neither alone admits, changes or releases information (T38); two halves may merge only under a higher-order DoT; hand-written rules additionally need the SME's weigh-in, a rejection cannot be overridden, and tacit approval is abolished (14 §rules need the expert, D5).

**Nearest prior art:**

1. DAMA International, *Data Management Body of Knowledge (DMBOK)*, 2nd ed., 2017 — data governance separates the *data owner* (accountable for decisions about data: purpose, access, risk) from the *data steward* (subject-matter custodian of meaning and quality). T38's organisational/factual split is this pairing made into a theorem. (verified, secondary sources)
2. Maker-checker / four-eyes control in banking and SOX separation-of-duties practice (initiate vs. authorise vs. review split across persons) — the operational version of "neither half alone acts." (verified, secondary sources)
3. ITIL 4 change enablement (AXELOS, 2019) — Change Advisory Boards seat both accountable managers and subject-matter experts before a change is authorised; the SME-weigh-in rule with escalation is a parliamentary-strengthened CAB. (knowledge)

**Delta [argued]:** The governance content is standard data-governance and SoD practice; "already-standard" is fair for the substance. DMP's distinct moves: making the pairing a *derived theorem of the trust axioms* (so it is enforced by the same gates as everything else, not by a governance manual), the *higher-order DoT nesting rule* (two halves may be one part only when a higher DoT gates it — a structural anti-concentration rule I have not seen stated elsewhere), the *veto asymmetry* (an active SME rejection with a reason cannot be overridden, only replaced by a later fully informed approval, and the rejection stays in the record), and the abolition of tacit approval as a direct consequence of Axiom 2 (silence moves nothing).

**Verdict: already-standard (substance) / new-combination (formalisation) — confidence 75%.**

---

## I11 · Risk-tiered assurance (Supernova classes) and AI-agent red-teaming (GRB, R136a1, escape ring)

**DMP's claim:** Four assurance classes assigned by graph distance from the trust core plus function (door/trust-decision/credential = IIb wherever it sits), each additive (deterministic tests + second check of a different kind; reverse suites; property tests; mutation testing; fuzzing with kept corpora; GRB run by an independent session that has only the specification; differential testing against a second implementation built from the spec; assumption audit). A GRB run is an authorised test under a signed scope file; success criterion is a planted flag (R136a1) that waves as high as it can; an escape ring (isolated network answering everywhere with the flag banner) catches broken-out agents.

**Nearest prior art:**

1. RTCA DO-178C (with EUROCAE ED-12C), 2011 — Design Assurance Levels A–E by failure severity, each level additive in verification objectives, with independence requirements for verification; the structural template for "assurance effort proportional to criticality." Common Criteria ISO/IEC 15408 EAL1–7 is the security analogue. (verified)
2. NIST SP 800-115, K. Scarfone, P. Mell?? — actually: K. Scarfone, W. Souppaya, A. Cody, A. Orebaugh, "Technical Guide to Information Security Testing and Assessment," NIST SP 800-115, 2008 — rules-of-engagement/scope authorisation for testing one's own systems (GRB's scope file). (knowledge; standard) 
3. E. Perez, S. Huang et al., "Red Teaming Language Models with Language Models," arXiv:2202.03286, EMNLP 2022 — automated/AI red-teaming of models predates GRB's agent attackers; honeytokens/canaries (Spitzner 2003) anticipate the flag mechanism; honeynet containment gateways (The Honeynet Project's Honeywall, 2003ff) anticipate the escape ring. (verified / knowledge)

**Delta [argued]:** Risk-tiered assurance with additive objectives (DO-178C DAL, CC EAL) and signed testing scopes (SP 800-115, pentest RoE) are standard; flags and containment rings are honeytoken/honeynet practice. DMP's own combination: (a) class assignment by *graph distance from the trust core* plus function override, rather than safety severity (DAL) or declared claims (EAL) — a topological rule new to me; (b) the attacker being an *AI agent* with a single binary success criterion and an instruction to stop on reaching it — operationalising LLM red-teaming (Perez et al.) with a capture-the-flag contract; (c) the *independent session with specification only* as the differential-verification witness ("someone who never saw the build"), which imports the independence idea of C22 into testing; (d) the assumption audit as a formal class requirement (every assumption becomes a runtime check or a test).

**Verdict: new-combination — confidence 65%.**

---

## I12 · Continuity, lockstep, self-correction, split-brain orders, time as a witness

**DMP's claim:** Every half outlives any single loss; floors (two seats per side, stand-ins, 3-node clusters deciding by majority) (T3); silence alarms but never isolates (T2/Q6); the two halves change their mutual trust only in lockstep, one record both sign (T24b); a part that signs an act contradicting the certificate it cites has produced evidence against itself, and its peers tighten at once (T24c); enforcement is itself a witnessed act checked against each witness's own decision log (T28); a shared undeclared failure cause demotes a layer to one witness (T29); "now" comes from two independent time authorities, each with two servers, disagree → "no now" (T20); the gate isolates only on verified orders or its own evidence, never on silence (04 §isolated state); White Key orders settle splits (lift/pick-a-winner/override, two signatures for loosening).

**Nearest prior art:**

1. L. Lamport et al.'s lineage via D. Ongaro, J. Ousterhout, "In Search of an Understandable Consensus Algorithm" (Raft), *USENIX ATC 2014*, and M. Castro, B. Liskov, "Practical Byzantine Fault Tolerance," *OSDI 1999*, pp. 173–186 — majorities of nodes, one wrong node cannot speak for the half (DMP's floor premise), configuration-change quorums, and leader-mismatch evidence. (verified)
2. J.C. Corbett et al., "Spanner: Google's Globally-Distributed Database," *OSDI 2012* — TrueTime: time as an infrastructure service with *bounded uncertainty* returned as an interval; "wait until certain" is Spanner's core discipline, the closest published form of T20's "where authorities disagree beyond tolerance, the stricter answer is no now." (verified)
3. Windows Server Failover Clustering's *witness* resource (Microsoft Learn) and Haeberlen's PeerReview (SOSP 2007, see I2) — the witness/quorum node that breaks ties and the accountability model where peers re-check each other's logs and produce proofs of misbehavior, the ancestor of T24c's self-incrimination. (knowledge/verified)

**Delta [argued]:** All mechanisms have standard homes: majorities (Raft/PBFT), stand-ins for failed nodes (consensus reconfiguration), split-brain fencing/STONITH and witness quorums (HA practice), bounded-uncertainty time (TrueTime), failure detection that never acts on a single silent peer (accrual detectors; Raft keeps serving with a majority), misbehavior evidence (PeerReview). DMP's own parts: *lockstep as a formal mutual-commitment protocol between the two authorities* (T24b — neither half can grant itself more or the other less, not even in the name of recovery); the *certificate-contradiction rule* (signing against the certificate you cite is evidence against yourself — a crisp, auditable definition of misbehavior that makes self-correction evidence-driven rather than vote-driven); and the *isolation grammar* (isolate = one signature/tightening, lift = two, no timeout, no automatic recovery, silence never isolates) — a deliberately conservative policy that I have not seen stated as a closed grammar elsewhere.

**Verdict: new-combination of standard mechanisms — confidence 70%.**

---

## I13 · The VIBE field and restoration scheduling

**DMP's claim:** Milky Way members carry vectors: depth (shortest grant chain to the pair), mass (one plus members deriving through them), freshness (share of validity since last live verification), shortfall (declared minus held, freshness-weighted); the VIBE field is mass × shortfall per member; its sum, the potential, is zero exactly when the boundary holds what it declares; restoration follows the field downhill (refresh heaviest-and-stalest first, grantor before child); refresh capacity is shared per member so one member's gathering cannot starve another (member isolation); the weight never votes (majorities stay unweighted); outsiders read one number, the temperature (T32). Two instances from the same recipe must span isomorphic fields (T33), checked by a hashed VIBE digest.

**Nearest prior art:**

1. S.D. Kamvar, M.T. Schlosser, H. Garcia-Molina, "The EigenTrust Algorithm for Reputation Management in P2P Networks," *WWW 2003*, pp. 640–651 — global trust values computed over a trust graph; the canonical "trust as a numeric field over a graph" prior art. https://doi.org/10.1145/775152.775242 (verified)
2. B. Beyer, J. Jones, J. Petoff, N.R. Murphy (eds.), *Site Reliability Engineering: How Google Runs Production Systems*, O'Reilly, 2016 (ch. 3, "Embracing Risk") — error budgets and burn-down prioritisation: a measured "shortfall against declared SLO" driving remediation order (heaviest burn first) is SRE's error-budget discipline; "temperature" is an SLO dashboard readout. (verified)
3. Trust decay/freshness weighting (e.g., R. Guha, R. Kumar, P. Raghavan, A. Tomkins, "Propagation of Trust and Distrust," *WWW 2004*; time-decay variants in reputation literature) — freshness-weighted trust is standard reputation-model fare. (knowledge)

**Delta [argued]:** Numeric trust over graphs, freshness weighting, shortfall-prioritised remediation and capacity shares are each established. DMP's own formulation: the field is *derived from the grant graph and the record* (not from behaviour ratings — nobody earns VIBE, they hold or owe it), anchored at the Duality pair; the *anti-gaming member-isolation rule* (nothing a member's nodes do changes another member's share) directly addresses collusion, the classic EigenTrust weakness; "the weight never votes" is an explicit firewall between the field and the trust decisions; and T33's *isomorphism test between two deployments* (same recipe ⇒ same field up to identity, hashed digest) is a determinism/equivalence guarantee on a trust metric that has no counterpart I can cite — though it is essentially differential testing applied to a configuration metric, so its machinery is standard.

**Verdict: new-combination (formalisation) — confidence 60%.**

---

## I14 · The C∞ stopgap and the axiom-refinement loop

**DMP's claim:** C∞ ("everything not fully trusted is ejected") is the permanent last-resort rule; every finding names the most specific axiom/theorem broken; a finding only C∞ catches is a *stopgap catch*, counted; a catch triggers a rethink — show it as a theorem, merge axioms, and only as last resort add one; two counters track completeness (catches → 0) and parsimony (axiom count down); C∞ concedes no formal system can prove its axioms match the world or decide all program behaviour, so the backstop stays.

**Nearest prior art:**

1. E.M. Clarke, O. Grumberg, S. Jha, Y. Lu, H. Veith, "Counterexample-Guided Abstraction Refinement," *CAV 2000*, LNCS 1855 — the CEGAR loop: a failure of the current abstraction drives refinement of the model, iteratively; the closest published shape of "a catch drives the formal system to be more internally sound." (verified)
2. S.G. Simpson, *Subsystems of Second Order Arithmetic* (Perspectives in Logic, 2nd ed. 2009) and H. Friedman's programme (1975) — *reverse mathematics*: for each theorem, find the minimal axioms needed; the mathematical practice corresponding to "the widest coverage from the fewest axioms." (knowledge)
3. Gödel 1931 (see I4) — the incompleteness concession DMP's own C∞ text makes explicitly. (verified/knowledge)

**Delta [argued]:** CEGAR refines *abstractions of one system*; reverse mathematics minimises axioms for mathematical theorems; neither is an *engineering governance loop for a living trust constitution*, with counted catches, promotion rules (theorem > merge > add) and enforced parsimony across a stack. As a meta-process this is DMP's own; its intellectual ancestry (CEGAR, reverse mathematics, Gödel) is acknowledged in spirit by the text itself. The honesty of the concession clause is noteworthy: most governance frameworks do not name their own incompleteness.

**Verdict: new-combination (process) — confidence 55%.**

---

## I15 · Agent authority: word-locked grants, guarded writes, advanced testing, data gate

**DMP's claim:** Agents build and change the estate on their own authority under a grant whose *wording is hash-protected* (C6; DMP-009 refuses unapproved wording changes); writes outside the own estate need both halves of the owning layer, and irreversible acts always do; writes go live only after the owner declares "advanced testing" for the system, on evidence (passed Supernova class, attended write through plan/gate/audit, two shadow runs for data lanes) (14 §advanced testing); every write first reads live state, asserts expectations, reads back (C15, `Invoke-GuardedWrite`); agents look up instead of guessing and cite their records (C21), ask the nearest tier first and return knowledge to it (C12/C13); company-data features reach general testing only with a proof pair (C16, data gate).

**Nearest prior art:**

1. Regulation (EU) 2024/1689 (EU AI Act), Article 14 — high-risk AI systems must be effectively overseen by natural persons, with override, reversal and stop capability; Article 9/15 logging and accuracy requirements — the regulatory version of "agents act only within declared, overseen bounds." (verified)
2. E. Debenedetti, I. Shumailov, T. Fan, J. Hayes, N. Carlini, D. Fabian, C. Kern, C. Shi, A. Terzis, F. Tramèr, "Defeating Prompt Injections by Design" (CaMeL), arXiv:2503.18813, 2025 — capability and control-flow policies enforced *outside* the model so untrusted content cannot trigger sensitive actions; the closest recent academic system for DMP's "the agent never decides trust; the gate does." (verified)
3. Optimistic concurrency / compare-and-swap discipline (database practice: read-modify-write with expected-value assertions) — C15's read-expect-write-verify is CAS applied to administrative writes; guarded-script patterns (dry-run, `-WhatIf`, idempotence) are standard PowerShell/Ansible/Terraform practice (e.g., Terraform plan/apply separation). (knowledge)

**Delta [argued]:** Human oversight of automated actors (EU AI Act), capability gates outside the model (CaMeL; earlier: DLS/object capabilities, knowledge), and plan/dry-run/apply write discipline are all established. DMP's own parts: the *wording-locked grant as a tamper-evident constitutional object* (the grant's authority lives in its exact sentence, whose hash the gate checks — authority and its text are one artifact); the *graduated write-authority ladder* (own estate on plan/audit/four-eyes → other estates under dual halves → irreversible acts always dual → everything per-act until the owner declares advanced testing, with named entry criteria); and the epistemic rules for agents (C21 "quote the match you found," C14 "combine every path, name what is still unknown," C13 tiered escalation with recorded empty searches) — an unusually concrete, auditable epistemology for agents, which the agent-safety literature mostly still states as guidance rather than as enforced gates.

**Verdict: new-combination — confidence 60%.**

---

## Summary table

| Idea | Verdict | Confidence | Closest citation |
|---|---|---|---|
| I1 Duality of Trust / dual gate | new-combination | 80% | Saltzer & Schroeder, Proc. IEEE 1975 (separation of privilege, two-person rule) |
| I2 Evidence & record axioms | new-combination | 70% | NIST SP 800-207 (verify explicitly); Schneier & Kelsey, ACM TISSEC 1999 |
| I3 Tighten alone, loosen with two | new-combination | 75% | Saltzer & Schroeder 1975 (fail-safe defaults); Ferreira et al., BTG-RBAC 2007 |
| I4 Axiom-terminated chains + G0 | new-combination | 65% | TCG TPM 2.0 root of trust; IANA DNSSEC KSK ceremonies |
| I5 Machine-checked compliance (Gravity, two chains) | new-combination | 70% | seL4, SOSP 2009; Pnueli et al., Translation Validation, TACAS 1998 |
| I6 IM closed language + closure | new-combination | 60% | Canetti, UC Security, FOCS 2001; JWT RFC 7519; Macaroons, NDSS 2014 |
| I7 Minting / pressing / White Keys | new-combination | 70% | IANA KSK ceremonies; NIST SP 800-57; Shamir, CACM 1979 |
| I8 Root chain / vendoring-by-hash | new-combination (mechanism already-standard) | 80% | Dolstra, Nix thesis 2006; Lamb & Zacchiroli, IEEE Software 2022; in-toto, USENIX Sec 2019 |
| I9 Containment / Event Horizon | new-combination | 65% | Goguen & Meseguer, IEEE S&P 1982 (noninterference); PCI tokenization; DLP/data diodes |
| I10 Two-body governance, org/factual halves | already-standard (substance) / new-combination (form) | 75% | DAMA-DMBOK 2nd ed. 2017 (data owner/steward); maker-checker four-eyes |
| I11 Supernova tiers, GRB, R136a1 | new-combination | 65% | DO-178C DAL 2011; NIST SP 800-115; Perez et al., EMNLP 2022 |
| I12 Continuity, lockstep, self-correction, time | new-combination of standard mechanisms | 70% | Raft ATC 2014 / PBFT OSDI 1999; Spanner TrueTime OSDI 2012; PeerReview SOSP 2007 |
| I13 VIBE field | new-combination (formalisation) | 60% | EigenTrust, WWW 2003; Google SRE error budgets, O'Reilly 2016 |
| I14 C∞ stopgap / refinement loop | new-combination (process) | 55% | Clarke et al., CEGAR, CAV 2000; reverse mathematics (Simpson 2009) |
| I15 Agent authority, guarded writes | new-combination | 60% | EU AI Act Art. 14 (2024/1689); CaMeL, arXiv:2503.18813 (2025); CAS/plan-apply practice |

**Overall reading [argued]:** No DMP headline idea is wholly without ancestry; equally, none is a mere repackaging. The consistent pattern is: mechanism standard, *constitutional form* new — trust rules stated as axioms with derived theorems, gated by machine checks, with the trust machinery itself (verification, release, time, enforcement) placed under the same dual gate as everything else. The strongest genuinely distinctive elements: C22's dual proof chains as witnesses of "proven"; the pressed/minted distinction with "out of spec" verdicts (T-P); T37's containment-by-collapse; C18's locked-version-forever-with-containment stance; and the T24c certificate-contradiction rule.

---

## Novelty claims that look overstated

How I used severity: how much the overstatement misleads a reader about DMP's contribution. DMP rarely says "we are first" in so many words; these are places where the framing implies it.

1. **Severity: high — "never trust any one interconnected system" / the dual gate as the thesis.** Where: `01-constitution.md` §C∞ ("This is the thesis of DMP"), §Axiom 1 (carries "The duality of trust is the single concept that goes through every layer"), `00-preamble.md` (owner quotes). Prior art: separation of privilege and the two-person rule are 1975 canon (Saltzer & Schroeder); dual control is a standing PCI DSS 3.6–3.7 and NISPOM TPI requirement; m-of-N is Shamir 1979. Suggested rewording: "DMP universalises separation-of-privilege: dual agreement at *every* layer — including information governance (T38) and the proof layer (C22) — with independence defined against declared failure classes, instead of as a control on named doors."
2. **Severity: high-medium — default-deny, verify-at-point-of-use, "no trusted network."** Where: `01-constitution.md` §T0, §Axiom 2, §C2 ("no debug switch, no allow list, no trusted network"), `04-im.md` §verify rules. Prior art: NIST SP 800-207's zero-trust tenets state no implicit trust by network location, per-session verification, continuous monitoring; fail-safe defaults are Saltzer & Schroeder 1975. Suggested rewording: "an axiomatisation of zero-trust tenets, strengthened from 'the PDP decides' to 'two independent witnesses must both trust.'"
3. **Severity: medium — "DMP-complete": self-contained, hash-pinned, heal-without-network configurations.** Where: `00-preamble.md` §the root chain and §who maintains it, `01-constitution.md` §the words (DMP-complete), `SETUP.md`. Prior art: Nix (Dolstra 2006), reproducible builds (Lamb & Zacchiroli 2022), in-toto (USENIX Sec 2019), SLSA (2021), go.sum-style hash pinning. Suggested rewording: "DMP applies supply-chain hermeticity to the specification text itself and makes completeness a machine-checked gate predicate (the standard SLSA/Nix mechanism, extended to the constitution)."
4. **Severity: medium — two totally independent proof chains (C22) as a new rigor standard.** Where: `01-constitution.md` §C22. Prior art: translation validation (Pnueli et al. 1998) validates the produced artifact against the spec; independent proof checkers/second kernels are established practice (DMP's own toolchain uses nanoda; Metamath has independent verifiers — knowledge); differential testing is in DMP's own class list. Suggested rewording: "translation-validation discipline raised to the constitution level, with the two validators sharing no root beyond those declared."
5. **Severity: low-medium — the self-verifying message (signed envelope carrying its token).** Where: `04-im.md` §the envelope ("every message verifies itself without any session state"). Prior art: JWT (RFC 7519), macaroons, and the stateless-token pattern DMP itself cites in `10-code-quality.md` §credentials. Suggested rewording: DMP is fair in chapter 10; chapter 04 could cross-reference that the token instantiates the standard stateless pattern under dual-chain constraints.
6. **Severity: low-medium — the Event Horizon as "the ONE boundary separating information from data" (T36).** Where: `01-constitution.md` §T36, §T27, C12. Prior art: DLP egress boundaries, data diodes, noninterference (Goguen-Meseguer 1982). The *policy* (any crossing is critical by definition) is a strong governance stance; the *concept* of a single egress boundary is standard. Suggested rewording: keep the policy; avoid implying the boundary concept is new ("we make one named boundary the unique information/data divide and attach severity-by-definition to it").
7. **Severity: low — minting/White Keys as distinctive.** Where: `01-constitution.md` §G0, C17; `11-test-design.md` §arming. Prior art: IANA KSK ceremonies, NIST SP 800-57/800-133, k-of-n hardware-token break-glass. DMP's real novelty is the pressed/minted distinction and ratification-by-class; suggested rewording: name those, and present the ceremony itself as standard practice adopted.
8. **Severity: low — gating stable rollout on tested cold start (C24).** Where: `01-constitution.md` §C24, `11-test-design.md`. Prior art: ISO 22301:2019 clause 8.5 and NIST SP 800-34 require tested, exercised recovery before reliance; RTO/RPO-style pass lines are the norm. The trust-chain-intact criterion (P3) is the specific new part. Suggested rewording: "a DR-exercise gate in the ISO 22301 sense, with an added trust-chain-intact pass line."
9. **Severity: low — counts-never-content observability.** Where: `01-constitution.md` §Axiom 3, T21; `04-im.md` §refusal log. Prior art: standard privacy-preserving telemetry, data minimisation, aggregate-only logging. Suggested rewording: "an enforced interface (enum-only) that makes content leakage unrepresentable" — the enforcement is the point, not the idea of counts-only.
10. **Severity: low — "compliance is assembled, never claimed" (T35).** Where: `01-constitution.md` §T35. Prior art: Common Criteria evaluates a TOE in its operational environment; assurance documents distinguish component vs. system claims as a matter of course. DMP's continuous re-shown-compliance (T3) is the sharper part. Suggested rewording: "per-assembly, continuously re-evaluated compliance, in the sense of Common Criteria's operational-environment scoping but machine-checked per pull request."

---

## Questions for the owner

1. **Scope of Gravity's proofs today.** SETUP.md's lesson note says `evidence/tools/check.sh` runs 232 theorems. Which propositions do they cover — the IM verify rules (C2's laws) only, or any of the constitution's T-theorems? This decides whether I5's closest prior art is protocol verification (Tamarin/Paulson-style) or policy-conformance proving (Firmato-style), and it is the difference between "novel in kind" and "novel in degree."
2. **Shared roots of the two chains.** C22 says the chains share nothing beyond declared roots. What are they concretely (author, engine, hardware)? Since independence is relative to the failure-class list (T4/T29), a reader of a future novelty claim will need that list to evaluate the claim.
3. **Missing chapters.** Chapters 03, 07–09, 12–13, 15–16 are reserved. Do they carry headline ideas (CMB's design, the shield, the galaxy group) that would add or change the inventory? If yes, this report needs a round 2.
4. **VIBE field status.** Is T32/T33 implemented (scheduler + digest) or spec-only? Prior-art delta differs: as spec it is a formalisation (EigenTrust/SRE analogy); as an implemented scheduler it approaches operational novelty and deserves its own round-2 pass.
5. **T36 severity-by-definition.** CVSS as a standard does not accept policy overrides of scoring; is T36 intended to bind only internal reporting, or will external CVE requests be expected to carry it? If the latter, the text should say how disputes are handled.
6. **Priority/publication.** Is DMP publicly disclosed anywhere (registry, paper, timestamped archive)? If novelty/priority matters, the corpus should record the disclosure date; this report treats only external prior art.

---

## Method note

Idea inventory and priority order taken from DMP's own emphasis (Axiom 1 as "the single concept", C∞ as thesis, the constitution's derivation order, the four-repo root chain). Citation verification this session covered: Saltzer/Schroeder 1975; NIST SP 800-207; PCI DSS 4.0 dual control; NISPOM TPI; Shamir 1979; Schneier/Kelsey 1999; RFC 6962; PeerReview SOSP 2007; seL4 SOSP 2009; Necula PCC POPL 1997; Pnueli et al. TACAS 1998; Firmato S&P 1999; Canetti FOCS 2001; Macaroons NDSS 2014; RFC 7519; Goguen/Meseguer 1982; Lamb/Zacchiroli (IEEE Software 2022); in-toto (USENIX Security 2019); SLSA; Dolstra 2006; EigenTrust WWW 2003; IANA KSK ceremonies; NIST SP 800-57/-133; DO-178C; CC EAL/ISO 15408; CaMeL arXiv:2503.18813; EU AI Act Art. 14; Perez et al. EMNLP 2022; BTG-RBAC (Ferreira et al. 2007); DAMA-DMBOK roles; CEGAR CAV 2000; NIST SP 800-34; ISO 22301; Spanner OSDI 2012; Raft ATC 2014; PBFT OSDI 1999; Google SRE 2016. Items marked *(knowledge)* (TCG TPM specs, Honeywall, Windows cluster witness, Metamath verifiers, NIST SP 800-115 author list, Dolev-Yao 1983, NIST SP 800-145, Miller's robust composition) were not re-opened this session and their venue details should be double-checked before external use. No GitHub repository was opened; no authentication, download, submission or installation occurred.

