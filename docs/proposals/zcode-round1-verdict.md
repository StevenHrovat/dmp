# Verdict on the Z code verification run, round 1 (dmp#22)

Team Fable, 2026-10-27. Read: every file of `findings/zcode-round1/` on the branch of dmp#22 (the README, C, D, E, the two V reports, the
orchestration log, and the high findings of A1 and A2). `SUMMARY.md` does not exist on that branch; the run was still in progress when the
snapshot was taken, so this verdict stands in for it until the orchestrator writes one. Everything below was re-checked against DMP 0.9.8
(`45d3822`), the IM proof and the Gravity evidence chain at their current heads; the machine checks were run with the pinned Lean toolchain. Theorem numbers below are those of DMP 0.9.8, which the reports cite; the table in the intro of `01-constitution.md` maps them to the proposed numbering (T37 is T4, T33 is T27).

## The straight verdict

The run is competent and honest, and its method (blind formalisers, an attacker, an advocate, a prior-art reader, a verifier per severe claim
that defaults to "refuted") is the right one. Its three findings rated high are all **real and none is a hole in a DMP guarantee**: two are
gaps in IM's text and proof documentation (C-IF01, C-IF04) and the third (D-F7) is Gravity's own finding F7, already in the owner's queue
with its remedy built into the model. After attack: C-IF01 medium (was high), C-IF04 medium (was high), D-F7 low for DMP's text (was high).
Nothing critical. The two blind formalisers found the gaps that matter most for part 1 of this session: "information" is not among the
words (A2-F02); T37's derivation line does not cite Axiom 3, which since 0.9.7 carries the bridge it needs (A2-F03); Axiom 1's "full reach"
and "gated only by the other" are undefined and "the two" is read canonically by every model (A2-F04); "DMP-complete" has no satisfaction
relation beyond Gravity's checker (A2-F12); the label "theorem" covers constructions and premises (A1-F01); about eighteen stable sections
say `none yet` (A1-F02); C2's hash-locked laws name a draft table by reference (A1-F03). The prior-art pass (E) rates every headline idea
"new-combination" and none "genuinely new", which is also this session's reading: DMP's text rarely claims novelty, and the physics pass
(gravity `docs/physics.md`) credits prior art the same way.

**For the owner to decide** (one recommendation each): (1) C-IF01, who owns path containment: IM's grammar, with a canonical-path predicate
(recommended; machine-checked below), or the `cm.os` handle contract. (2) A2-F02, add *information* to the words; recommended wording: "a
**piece of information** is what an admission names and a record holds; it is acted on only through acts, so every sentence about it is a
sentence about the acts that reach it". (3) A1-F03, freeze the verify table inside C2's laws file (recommended) or mark L2 and L4 draft.
(4) D-F7, the T33 sentence Gravity's F7 proposes: "The digest identifies the field, not the recipe; a stable publishes its recipe next to the
digest."

## The attacks on the three high findings

**C-IF01, the path grammar admits `..` (survives, downgraded to medium).** Every machine-checked leg reproduces in a fresh scratch copy of
`proof/`: `../record/g` is a legal path, the sentence is well formed, it round-trips through `decode_encode`, and the door's verdict is
path-independent for every grant, by `rfl` (the door never reads the path, which is C12 by design and correct: the layer places the noun,
the grant names the kind). The leg that carried the severity, "a conforming implementation resolves `..` against a per-layer root and
reads outside the layer", has no system behind it: no file layer exists in `cm.os`, nothing in IM resolves a path, and `docs/language.md`
says where resolution would live. So the hole is in the text, not in a running part. What survives is sharper than the report states:
the grammar gives one noun several spellings (`a//b`, `a/./b`, `../x`, `/a`), so the one-spelling invariant I6 holds per sentence and fails
per noun. The fix is one predicate and one sentence: `pathCanonical` (legal bytes and length, every `/`-separated segment non-empty and
neither `.` nor `..`, which also bars a leading and a trailing `/`), with `pathCanonical → pathOk` and six kernel-checked examples (the four
spellings above refused, `record/g` and `setup/toolchain/lean-4.34.0/bin` accepted), all resting on `propext`, `Quot.sound`,
`Classical.choice` only; and in DMP 04 the fourth alphabet of IF8 stated as canonical. Recommended owner: IM's grammar, so every door is
uniform.

**C-IF04, the closure proves less than its docstring says (survives at medium).** Not refutable: the verifier's checks reproduce. `lawfulB`
is true of a write that expects `any` (an L5-violating shape), the membership conjunct is a tautology of the closed type, and the docstring
claims a tie-in to Laws.lean and Wire.lean that the statement `s.shape.lawfulB = true` does not carry. No law is unproven: L1, L5 and
`decode_encode` exist as universal theorems, and `decode_wf` already says universally that a door never sees an ill-formed sentence, which
subsumes the sample-only `ill_formed_never_decodes`. The fix is five lines, compiled in scratch: `closure'` as a conjunction that
instantiates L1, L5 and the round trip at the sentence (axioms `propext`, `Quot.sound`), plus a rewording of `docs/language.md` line 111.
Severity medium: a proof-integrity defect in the honesty section, not a security property missing.

**D-F7, the VIBE digest is not injective (known, mitigated, low for DMP's text).** The finding is `digest_not_injective` in Gravity's own
`Cmb.lean` and row F7 of `docs/findings.md`: the model found it, states it, and builds around it. The model never decides from the digest:
`Cmb.plan` uses the digest only to choose between the redeploy and the Big Bang path, and both paths start from the recipe the file carries
(`redeploy_is_recipe_field`, `bigBang_keeps_the_proof`), while `Recipe.file_determines` proves the file read back gives the same verdict,
digest and every decision. So the owner's sentence of 18:19Z ("proves its recipe through DoT hashing of the produced VIBE field") is wrong
as a mechanism, the model already does not rely on it, and D's "high" assumes a digest-only restore nobody built. What is left is the one
T33 sentence above; it is the owner's decision, not a defect to fix.
