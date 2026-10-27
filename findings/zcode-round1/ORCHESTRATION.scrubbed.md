# DMP verification — orchestration log

Protocol: independent verification team for DMP (Dark Matter Protocol), owner the owner.
Orchestrator: ZCode main session. Orchestrator does no task work; it sets up, spawns, routes,
verifies claim marking, and writes SUMMARY.md from V-agent verdicts only.

## Environment decisions (with fresh `date` readings)

- 2026-10-26 21:37–21:42: Owner redirected workspace root from the folders outside the work folder to `<work folder>`
  (rejected the first two tool calls). All walls otherwise unchanged. The folders outside the work folder
  remain forbidden reads (distinct from `<work folder>`).
- 21:42: clones created read-only: `src/dmp`, `src/gravity`, `src/im` (*).
- 21:43: `src/dmp/SETUP.md` read first, per protocol. Toolchains it lists for this work:
  Lean 4.34.0 (install L1, elan; host release.lean-lang.org) and .NET SDK 10.0.403 (D1 — already
  on PATH as 10.0.403, no install needed). No other toolchain installed. elan/Lean 4.34.0
  installed at 21:44–21:47 (`~/.elan/bin`), `lean --version` = 4.34.0. NOTE: SETUP.md pins a
  sha256 for the LINUX tarball; elan fetched the official Windows toolchain from
  release.lean-lang.org (SETUP.md hosts table explicitly lists that host for L1). Recorded as an
  orchestration note, not a finding.
- Subagents install nothing; they use ~/.elan/bin/lean, lake, and dotnet already present.

## Input corrections discovered during setup (recorded, protocol unchanged)

1. Task said D reads "gravity\docs\findings.md, IM findings IF6–IF9". Reality:
   `gravity/docs/findings.md` holds findings **F1–F10** (gravity/Lean side);
   `im/docs/findings.md` holds **IF1–IF9(+)** (IM side). D is given both files and advocates on
   F1–F10 and IF6–IF9 exactly as the task's numbering intends.
2. C's "im docs and grammar" inputs = `im/docs/` + `im/proof/` (the Lean grammar/closure files
   live in `im/proof/`; C's deliverable explicitly includes judging the closure theorem).
   `im/src/` (C# implementation) and `im/tests/` stay out of C's scope — C attacks the spec,
   not the implementation.

## Interpretations granted (flag to owner in final report)

- E (prior-art researcher) is allowed READ-ONLY public web search/fetch for citations. The task's
  "contact no service other than the downloads SETUP.md names" wall is read as banning
  state-changing or authenticated contact (push/PR/issues/login); role E is impossible without
  literature lookup. E must still never authenticate, never write to any service, never touch
  GitHub interactively.
- Severity: "severe" = critical or high. A claim reaches SUMMARY.md only if its V agent fails to
  refute it (V defaults to REFUTED when unsure).

## Round 1 — spawned 2026-10-26 21:49

| Agent | Role | Work dir | Output | Status |
|---|---|---|---|---|
| A1 | blind formaliser, axiom-first | work/a1r1 | out/A1-round1.md | running |
| A2 | blind formaliser, theorem-first | work/a2r1 | out/A2-round1.md | running |
| C | IM attacker | work/cr1 | out/C-round1.md | running |
| D | findings advocate (F1–F10, IF6–IF9) | work/dr1 | out/D-round1.md | running |
| E | prior-art researcher | work/er1 | out/E-round1.md | running |

Concurrency: 5/6 slots used during round 1 start. B starts when A1 AND A2 finish.
V agents spawn per severe claim (critical/high) from B, C, D as they arrive, max 6 total.

CONCURRENCY AMENDMENT (owner, 2026-10-26 ~22:25): **max 4 subagents at once** (was 6), and on
provider rate-limit failures ("Network connection failed for the provider request") back off
before resuming (wait for a free slot and a quiet period; no immediate retry loops). The
provider errors above were rate limits. Applied immediately: E's second resume attempt failed
(rate limit) and E is intentionally held stopped; running set is A1, A2, C, D = 4. E resumes
when the first of them completes. All later scheduling (B, V agents, rounds) obeys the cap of 4.

Buildable copies for verification (never touching src/):
`work/verify/gravity-evidence/` (from src/gravity/evidence), `work/verify/im-proof/` (from
src/im/proof). Toolchain smoke test 2026-10-26 ~21:52 (`lake build` with ~/.elan/bin on PATH):
gravity-evidence — Build completed successfully (23 jobs), one deprecation warning
(`if_neg` in Dmp/R2Stable.lean:115). im-proof — Build completed successfully (8 jobs).
Both projects have no external dependencies (no network fetch needed). B and V agents may
machine-check in these copies.

## Claim ledger

(severe claims and V verdicts are appended here as they arrive)

| Claim ID | Source | Severity | One-line claim | V verdict | V output |
|---|---|---|---|---|---|
| C-IF01 | C round 1 | high | `file.read ../record/g apply any` is grammar-compliant and accepted (pathOk/wfB/decode machine-checked in C's scratch Lean), yet escapes the layer the kind names; no `..`/canonicality/containment rule; two conforming doors decide it differently | **SURVIVES** (V added ∀-grant path-independence theorem, kernel-checked; caveat cleared) | out/V-C-IF01-round1.md |
| C-IF04 | C round 1 | high | `closure` proves only `s.shape.lawfulB = true`; docstring/docs claim law-coverage (L1, L5, I6) the statement does not carry; one conjunct tautological; 40/72 shapes "lawful" vacuously | **SURVIVES** (tautology + L5-violating-sentence certification machine-checked by V; high as doc/proof-integrity, medium as security impact) | out/V-C-IF04-round1.md |
| A1-F01 | A1 round 1 | high | "Everything after that is a theorem" contradicts the chapter's own derivation semantics; T3, T24c, T32–T34, C1, C4, C5 are constructions, inflating Gravity's proof obligation | pending | — |
| A1-F02 | A1 round 1 | high | ~18 stable sections carry "Enforced by: none yet", which 00 itself rules "a defect in DMP, not a rule" (incl. Axiom 4) | pending | — |
| A1-F03 | A1 round 1 | high | Stable, hash-locked law C2.L2/L4 defines its semantics by reference to draft chapter 04's verify table, which can change without changing C2's laws-file sha256 | pending | — |

A2 completed ~23:25 (5 high findings: A2-F01 C∞ circular; A2-F02 containment block unstatable from
"the words"; A2-F03 T37 missing admission→licence bridge — A2 had to invent a BRIDGE axiom;
A2-F04 Axiom 1 ambiguous canonical-halves vs any-pair, existential reading near-unfalsifiable;
A2-F12 DMP-complete gate has no satisfaction relation — only checkable half statable). NOTE per
protocol the V queue takes severe claims from B, C, D (A findings reach V through B's adoption).
B (comparator) launched ~23:30 as slot 4 (D, E, P still running). Running: B, D, E, P = 4/4.

D completed ~23:50: 14 advocated findings (F1–F10, IF6–IF9); 13 judged real holes, 1 not (F5);
severe: only **F7** at high (VIBE digest non-injective; kernel-checked counterexample in
Cmb.lean:219–239 refutes the owner's "proves its recipe through DoT hashing" sentence; T33
publishes the digest unqualified). 6 decision requests recorded. V-C-IF01 launched ~23:55
(slot 4). Running: B, E, P, V-C-IF01 = 4/4. V queue: C-IF04, D-F7 (+ B's when it lands).

## Round 2 — begins 2026-10-27 ~00:50 (fresh agents, new angles, walled from round-1 output)

Launched early where inputs are round-1-independent (rate-limit drag makes wall-clock overlap
worthwhile; no round-2 agent may read any round-1 file, so independence is structural):
| Agent | Role | Work dir | Output | Status |
|---|---|---|---|---|
| A3 | formaliser, semantics/model-first | work/a3r2 | out/A3-round2.md | running (launched 00:50) |
| A4 | formaliser, adversarial (vacuity/contradiction hunt) | work/a4r2 | out/A4-round2.md | queued |
| C2 | IM attacker, composition/substitution/encoding angle | work/c2r2 | out/C2-round2.md | queued |
| D2 | findings advocate, opposite-stance/low-confidence angle | work/d2r2 | out/D2-round2.md | queued |
| E2 | prior-art, remaining clusters (formal verification of infra config; attestation/measured boot; cert/trust chains; capability/confinement; dual control/two-person rule; policy machines ABAC/ReBAC) | work/e2r2 | out/E2-round2.md | queued |
B2 (comparator for A3+A4) after both land; V2 per severe claim.

V-C-IF01 verdict ~00:35: **SURVIVES**, high. V rebuilt from a clean byte-identical copy (no
doctored defs), added sharper theorems (∀-grant path-independence), axioms only
propext/Quot.sound/Classical.choice, no sorryAx. Caveat (containment rule might live in DMP
04/C12) cleared by orchestrator grep 00:40: DMP's "canonical" = byte encoding I6; T27 containment
= trust-space/records; line 468 "any path" = transport paths. No noun-path containment rule
exists in DMP. V-D-F7 launched ~00:40. Running: B, P, V-C-IF04, V-D-F7 = 4/4.

E completed ~00:10: 15 ideas, ~35 verified citations; every verdict "new-combination" (none
"genuinely-new"); high overstatement findings: C∞/Axiom-1 novelty framing (vs Saltzer & Schroeder
1975 / PCI DSS), default-deny framing (vs NIST SP 800-207). Per protocol E claims get no V agent
(V covers B/C/D severe claims); E feeds SUMMARY as prior-art context. V-C-IF04 launched ~00:15.
Running: B, P, V-C-IF01, V-C-IF04 = 4/4. V queue: D-F7 (+ B's when it lands).

## Side task: PR12 (owner-commissioned 2026-10-26 ~23:00)

- Owner: "look at docs/proposals/exclusion-inclusion.md in dmp draft PR12 and execute it when you have a
  free slot." Fetched PR12 head read-only into work/pr12-dmp (single new file, the brief).
- SCOPE CHANGE logged: the verification walls (no push/PR) are superseded BY THE OWNER for this one
  task only: draft PRs on dmp and gravity, never merge. gh CLI verified
  authenticated (the owner, repo scope). All verification agents keep the original walls.
- Owner decision recorded for the brief's Q2: inclusion cap = smallest approving coalition within the
  yes-votes (owner agreed with the brief's recommendation, 2026-10-26). Q1, Q3–Q6 stay open with one
  recommendation each from the drafting agent.
- Agent P launched ~23:05 (slot 4 of 4). Report → out/P-pr12-round1.md.

## Incident log

- ~22:00–22:10 2026-10-26: three round-1 agents (C, E, A1) each failed mid-run with
  "Network connection failed for the provider request" (agent-infrastructure outage, not task
  failures). All three resumed via SendMessage with context intact; no work lost.
- ~22:15 2026-10-26: the remaining two (A2, D) failed with the same provider outage and were
  resumed the same way. All five round-1 agents now running in resumed state.
- ~22:35–22:40 2026-10-26: while at 4 running, D and C failed again (rate limit). Applied the
  owner's rule: 5-minute backoff, then resumed only C → running set A1, A2, C = 3. D and E held.
  Resume order as slots free: D, then E. All agents told to prioritize writing their output file
  incrementally so interruptions lose less.


## Round 2 planning (fresh agents, new angles, no sight of round-1 output)

- A3: model/semantics-first formaliser (structures & invariants, not syntax-first).
- A4: adversarial formaliser (hunts vacuity, unfalsifiability, joint inconsistency; starts from
  the headline theorems in README/CHARTER).
- C2: attacks composition/substitution/encoding surfaces (round-1 C attacked acceptance &
  closure scope) — angle set by orchestrator without revealing C's round-1 results.
- D2: same both-sides advocacy, angled at the findings round-1 D marked undecided/low-confidence
  (chosen from the findings list itself, not from D's verdicts).
- E2: prior-art for idea clusters E did not cover (assigned as: formal verification of
  infrastructure/configuration, attestation & measured boot, certificate/trust-chain systems,
  capability systems & confinement, two-person rule / dual control, policy machines & ABAC/ReBAC).
- B2: comparator for A3+A4.
- Stop rule: two consecutive rounds adding nothing new → stop, write SUMMARY.md.
