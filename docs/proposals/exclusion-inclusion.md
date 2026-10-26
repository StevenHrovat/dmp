# Proposal brief: exclusion and inclusion by voting share

Status: **brief for a drafting agent, not a DMP text change.** Nothing in chapters 00 to 14 is edited by this file. The owner approves
every change to DMP wording (chapter 00, "Who maintains it"; G0), so the result of the task below is a **draft pull request** that the
owner reads and approves or rejects. Do not merge.

## 1. The task

Replace the fixed "two signatures" that DMP uses to lock a part out and to let it resume (isolate and lift, exclusion and inclusion) with
the owner's rule in section 2, which counts **voting share**, not a fixed number of keys.

Do these, in this order, and stop after step 5:

1. Pull request on `dmp` (draft): the DMP text change. Show the **old rule and the new rule quoted in full** and **every changed passage
   side by side** (old text, new text, file and section). Do not paraphrase a rule in place of quoting it. Use the passages in section 4 as
   the list of places to check; add any place you find that states a threshold and is not listed.
2. In the same pull request, a short **consistency check against T24** (`01-constitution.md`, "Tighten down on one witness, loosen with
   two") and against **dmp#11** (the IM chapter's lift and override text, quoted in section 4). Say for each: still true, or changed, and why.
3. Pull request on `gravity` (draft, opened after step 1 so it can cite it): a **Lean statement** in `evidence/Dmp/`, see section 5, with
   worked examples for: equal shares, a 70/30 split, and one dominant voter. Gravity vendors DMP by pin, so the Lean file states the
   **proposed** wording and says so; it is re-pinned only after the owner approves the DMP text.
4. List what is still ambiguous (section 3 has the known ones) as questions for the owner, each with your recommendation. One recommendation,
   not a menu.
5. Do not merge anything. The owner approves the DMP text in his own words; until then the change is a proposal.

Rules that apply: roles, not people; no company, host, address or account anywhere; run `tools/scrub-scan.sh` in each repository before
opening the pull request; Apache 2.0 content only, with credit for prior work as `gravity/docs/acknowledgements.md` does.

## 2. The owner's words (verbatim)

2026-10-26 21:42Z:

> The simple majority of one side of a DoT, but never while being the simple majority of the DoT, in which case it must logically work to
> restore balance above all, can initiate exclusion. An inclusion must be approved by two sides DoT, who can, as they would have to restore
> balance above all, also not vote with a simple majority which also holds the total simple majority.

2026-10-26 21:43Z (measure):

> It is about is percentage of the voting share, whichever value that happens to be.

2026-10-26 21:38Z (background, summarised): the current "2" is a remnant of an assumption of five White Key holders (WKHs); five is only the
**minimum**, so a fixed 2 is wrong as the number of holders grows.

Terms: **DoT** is the Duality of Trust, the two independent witnesses (halves, "sides") of a layer (`01-constitution.md`, Axiom 1, T38).
**Voting share** is each voter's weight on its side, whatever value the configuration gives it. At the default every White Key holder
has one equal share, so share reduces to a seat count.

## 3. Reading of the rule (the coordinator's, to be confirmed by the owner)

This is a reading, not a ruling. Write the draft from it, mark it as a reading in the pull request, and ask the owner the questions below.

Let `S` be one side's total share, `T` the whole DoT's total share (both sides), and `share(C)` the combined share of a set `C` of voters.

- **Exclusion.** A coalition `C` inside **one side** may initiate an exclusion when `share(C) > S/2` (a simple majority of that side's
  share) **and** `share(C)` is **not** a simple majority of the whole DoT (`share(C) <= T/2`). A coalition that does hold the majority of
  the whole DoT may not initiate it: it must work to restore balance first.
- **Inclusion.** Needs **both** sides. Each side approves by a simple majority of its own share. Neither side's approving coalition may, by
  itself, hold a simple majority of the whole DoT (`share(approvers) <= T/2`), for the same reason: a coalition that already holds the
  total majority must restore balance, not extend itself.
- **Consistent with T24** (tighten on one witness, loosen with two): exclusion is the tightening direction and starts from one side;
  inclusion is the loosening direction and needs both sides.

Open points for the owner (answer each with a recommendation):

- **Q1 Ties.** Is "never while being the simple majority" strict (`> T/2` is barred, exactly `T/2` is allowed) or not? A simple majority
  is more than half, so the reading above bars only `> T/2`.
- **Q2 Inclusion, what exactly is capped.** The cap on the approving coalition: does it apply to the coalition that actually voted yes
  (so extra yes votes could void an approval), or to the smallest approving coalition (an approval stands if some qualifying coalition
  within the yes votes is at most half of the total)? Recommendation: the second, because more agreement must never make an act invalid.
- **Q3 Initiating versus completing.** "Can initiate exclusion" says who may start it. Who completes it: the dual gate and T5 as today,
  or the same share rule? The reading above covers initiation only.
- **Q4 Unweighted majorities (T5, T32).** `R1Mass.lean` proves that the trust mass (a part's pull in the Milky Way field) never votes, and
  T5 counts seats. The voting share here is a different quantity (a configured weight per holder, equal by default). Say in the draft that
  the two are not the same quantity and that the default (equal shares) gives back T5's seat counts.
- **Q5 Where the thresholds live.** T4 puts "the thresholds above a majority" in the minting's configuration. State which parts of the
  new rule are fixed by DMP and which are configuration.
- **Q6 Floors.** T3a keeps at least two seats per side and one onboarded stand-in per seat. The draft must show the rule still works at
  the floor (two seats per side) and at the five-holder minimum.

## 4. Where DMP states the current thresholds

All paths are in this repository unless a repository is named. Line numbers are as of DMP 0.9.6 (`ed23322`); recheck before quoting.

**T24, `01-constitution.md` lines 335 to 350, "Tighten down on one witness, loosen with two"**

> a witness may tighten its own trust in the parts it gates on its own, at once (refuse, isolate, hold); everything that loosens needs both
> witnesses (lift, unlock, override, promote, admit, release). An act on another part's standing, and every act on the Duality's own
> composition (seats, witnesses, roots, the pinned set), is an act under the dual gate and T5 in either direction: one half can never remove
> the other.

Bullets follow: isolating with one White Key; restoring a signed state needs one key only when the record shows no tightening since;
every tightening names its lift condition. Its derivation line records "Decision D4: lift, unlock and override on two signatures change the
owner's written White Key rule of 2026-10-25 07:16Z." The sentence about acts on the Duality's composition is the closest DMP text to
"exclusion and inclusion"; the words themselves do not appear in DMP.

**T5, `01-constitution.md` lines 260 to 270, "Majority of trust"**

> Wherever DMP asks for a majority of the White Key holders, it means both: **M2**, at least half of each side's seats, rounded up (an act
> without a side was not witnessed by that side); and **M1**, more than half of all pinned seats (the smallest threshold that never lets
> two disjoint sets carry contradicting acts and survives one refusal). Seats are counted from the pinned set in the record, never from who
> answers. A stricter threshold for acts on the seat set itself is configuration.

**T3a, `01-constitution.md` line 227, the floors**

> The smallest numbers that keep the dual gate satisfiable after any single loss: at least two seats per side, at least one onboarded
> stand-in per seat, and a cluster of at least three nodes per system half ... Every number above a floor (the owner's two stand-ins per
> side, five seats, an odd count) is configuration (T4).

**T4, `01-constitution.md` line 250:** the failure classes, windows, floors, "the thresholds above a majority" are fixed by both halves at
the minting and changed only by a majority of trust, never below a floor.

**T6, `01-constitution.md` line 273:** a stand-in takes a seat at once; "a majority of trust may stop it only by revoking the stand-in on
evidence against it (T2)". This is the existing exclusion path for a stand-in.

**`04-im.md` lines 439 to 470, "Orders and the White Key" (the text changed by dmp#11, owner 2026-10-26: "you have my permission to
override DMP-04 with the stricter rule")**

> Isolate is a tightening and needs one signature. Lift and override are loosenings and need **two** signatures from two different keys
> (constitution T24: "everything that loosens needs both witnesses"; decision D4). A White Key holder may read everything while the key
> exists, but never loosens or writes permanently alone.

Also in that section: the order body is "followed by a list of one or two signatures ... Two signatures must come from two different
keys" (line 449); an isolate order verifies under Doppler's security leaf or a White Key; **pick a winner** "needs **two** signatures: a
White Key and either the winning master's leaf or a second, different White Key" (lines 454 to 457). These are the fixed "2" for isolate/lift in
IM version 1.

**`00-preamble.md` lines 49 to 61, owner and minting:** the owner stands for both halves (G0) until the minting, "the owner alone may
withdraw [a grant], as a tightening (T24)", and after the minting "ultimate authority rests with the White Key holders under a majority of
trust (T5)".

**G0, `01-constitution.md` lines 124 to 140:** the ground; the minting forms the LHC and makes the White Keys; a pressed instance is G0 as a
standing mode.

**`11-test-design.md`, the five-holder assumption behind the "2":**
line 28, "The system is armed: at least three White Keys"; line 53, check C5, "the count is at least three"; line 109, "Decided (owner,
09:53Z): five White Keys at arming, the two sysadmins and three members of the C-suite, majority three."

**`14-process.md` line 172, the override:** "The holders of the cold-start keys can always keep the system in its current state." Check that
the new rule does not weaken this.

**Outside this repository** (the `cm` repository, `CM.BlackHole/docs/ca-plan.md`, "Once armed, the majority rules", about line 243): "adding
or revoking a White Key ... need **a majority of all White Keys of that system**, so two of three"; and "five keys make a majority of three
and survive two losses". Quoted here because a drafting agent may not see that repository. The White Key section just above it also says
"Why not every write: in a total lockout, one admin alone must be able to act ... If a lift needed two origins, a lockout with one
reachable holder could not be ended", which the new rule must be checked against (a lift under the new rule still needs the share rule, and
`04-im.md` already overrode the one-signature lift).

## 5. Where the Lean statement goes (gravity repository)

The evidence chain is `evidence/Dmp/*.lean`, Lean 4 core only (no Mathlib), imported from `evidence/Dmp.lean`, described row by row in
`evidence/README.md`, with findings in `docs/findings.md`. Suggested placement:

- New file `evidence/Dmp/Exclusion.lean`: voter shares, the two predicates (can initiate exclusion, inclusion approved), and theorems:
  a coalition holding the whole-DoT majority never initiates exclusion; a side-majority coalition below the total majority does; an
  inclusion needs both sides; equal shares reduce to T5's seat counts. Add `import Dmp.Exclusion` to `evidence/Dmp.lean` and a row to the
  table in `evidence/README.md`.
- Model on `evidence/Dmp/Standing.lean` (T24: `update`, `one_witness_never_loosens`, `loosening_needs_both`), which already has the
  old threshold as theorems and must be re-read against the new rule, and on `evidence/Dmp/Layer.lean` (`DoT`, `Witness`, the halves).
- Read `evidence/Dmp/R1Mass.lean` for the existing statement that weight never votes (T5, T32), see Q4.
- Do not edit `vendor/dmp` in gravity (a vendored copy is never edited); re-pin with `tools/pin.sh` only after the owner approves the DMP text.

Expected outcomes for the worked examples, to be proved and not assumed (side A and side B shares, `T = A + B`; the reading of section 3):

| Case | Shares | Who may initiate exclusion | Reason |
|---|---|---|---|
| Equal | A: three voters of 1, B: three voters of 1 (T = 6) | any two voters of one side | 2 > 1.5 and 2 <= 3 |
| 70/30 | A = 70, B = 30 (T = 100) | on A: a coalition with share above 35 and at most 50; on B: any coalition above 15 | all of A (70) is the total majority and must restore balance |
| Dominant voter | A: one voter of 60 plus one of 10, B = 30 (T = 100) | nobody on A; on B any coalition above 15 | the voter of 60 is the total majority; the voter of 10 is not a majority of A |

Report the pull request links when the draft is ready.
