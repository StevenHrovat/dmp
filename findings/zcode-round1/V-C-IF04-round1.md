# V-C-IF04-round1.md — Verifier report for claim C-IF04 (round 1)

- Verifier: V (C-IF04), independent verification team, DMP.
- Date of checks: 2026-10-26 (fresh `date`: Mon Oct 26 23:29:24 WEST 2026).
- Claim under test: "`closure`'s statement is only `s.shape.lawfulB = true`: its docstring claims it ties
  in the universal laws (L1, L5, I6) but the conclusion contains neither; one conjunct (`kind ∈ Kind.all`)
  is a tautology of the closed type with zero discriminating power, so the docs' 'every shape keeps the
  laws above' overstates what is machine-carried (list completeness + 12 kind names + 32 sample
  round-trips)."

## 1. What I checked (commands + results)

### 1.1 Textual — `closure`'s statement vs its docstring

Read `C:\zcode\CMOS\src\im\proof\Im\Closure.lean` in full. Key lines:

- L22–24, the entire predicate (quote):
  ```lean
  def Shape.lawfulB (sh : Shape) : Bool :=
    nameOk sh.kind.wire && sh.kind ∈ Kind.all &&
    (!sh.wfB || (Sentence.decode sh.kind sh.sample.encode == some sh.sample))
  ```
- L29–31, docstring vs statement vs proof term:
  ```lean
  /-- The closure: every sentence keeps the decidable laws (through its shape) and the universal ones (through Laws.lean and Wire.lean). -/
  theorem closure (s : Sentence) : s.shape.lawfulB = true :=
    (List.all_eq_true.mp all_shapes_lawful) s.shape (Shape.all_complete s.shape)
  ```
  The proof term uses only `all_shapes_lawful` and `Shape.all_complete`. The module docstring (L9)
  also says "`closure` ties both".

- [proven] No theorem of Laws.lean or Wire.lean appears anywhere in Closure.lean:
  `grep -nE "pass_needs|one_grant|write_says|read_execute|decode_encode|decode_wf|decode_kind|Grants|decideSentence|permissions_distinct|nothing_granted" Im/Closure.lean`
  → no matches (exit=1), run on my copy.
- [proven] `closure` is used nowhere else in the project — no theorem composes it with the law
  theorems: `grep -rn "closure" Im/*.lean Im.lean Table.lean` → only its own docstring (L4, L9, L29)
  and its definition (L30).
- [argued; from targeted grep of signatures in my copy, needed by checklist item 1] The "universal"
  laws live elsewhere and are hypothesis-gated on well-formedness:
  `Laws.lean` L62: `theorem write_says_expect (s : Sentence) (hwf : s.wfB = true) (hw : s.kind.verb = .write) : s.expect ≠ .any`;
  `Wire.lean` L67: `theorem decode_encode (s : Sentence) (hwf : s.wfB = true) : Sentence.decode s.kind s.encode = some s`;
  `Laws.lean` L34/L40: L1's theorems are parameterized over abstract `Grants`. None is instantiated
  at `s` inside `closure`.

Conclusion of 1.1: the conclusion of `closure` contains neither L1, nor L5, nor I6's `decode_encode`,
directly or via a folded-in helper — `lawfulB` is self-contained (nameOk, membership, `!wfB ||` sample
round-trip). The docstring's tie-in claim is prose only. Claim element (b) holds.

### 1.2 Machine — the tautology charge and the vacuous-40 count

Setup: copied the buildable project `C:\zcode\CMOS\work\verify\im-proof\` to
`C:\zcode\CMOS\work\v-cif04\im-proof\` (original untouched; original `src\` never modified).
Build: `cd /c/zcode/CMOS/work/v-cif04/im-proof && PATH="$HOME/.elan/bin:$PATH" lake build`
→ "Build completed successfully (8 jobs)."
Checks: `PATH="$HOME/.elan/bin:$PATH" lake env lean ScratchCIF04.lean` → EXIT=0, output `72`, `32`,
`40`, `12`. Scratch file: `C:\zcode\CMOS\work\v-cif04\im-proof\ScratchCIF04.lean`. All axioms are the
project's own; my additions use no new axioms (`decide`, `simp`, term-mode `closure` only).

- [proven] Tautology, proven WITHOUT the project's own `Kind.all_complete`, by pure case enumeration
  of the closed types:
  ```lean
  theorem kind_mem_tautology : ∀ k : Kind, k ∈ Kind.all := by
    rintro ⟨l, v⟩; cases l <;> cases v <;> simp [Kind.all, Layer.all, Verb.all]
  ```
  Compiles. So the membership conjunct is true of every term of `Kind` — it is a tautology of the
  closed type, exactly as charged. `Kind.all` is pure Lean data (`Grammar.lean` L67:
  `Layer.all.flatMap fun l => Verb.all.map fun v => ⟨l, v⟩`), not read from the C# table at run time.
- [proven] Zero discriminating power at the Bool level, two ways:
  `theorem membership_conjunct_never_false (sh : Shape) : (sh.kind ∈ Kind.all : Bool) = true`
  via `Kind.all_complete` and again via my independent tautology. For every `Shape` term the conjunct
  decides to `true`, so `lawfulB` effectively reduces to
  `nameOk sh.kind.wire && (!sh.wfB || decode…=some…)`.
- [proven] The L5-violating shape is lawful and `closure` certifies it, for every path and mode:
  ```lean
  example : Shape.lawfulB ⟨⟨.file, .write⟩, .dry, .any⟩ = true := by decide
  example (p : Name) (m : Mode) :
      (⟨⟨.file, .write⟩, p, m, .any⟩ : Sentence).shape.lawfulB = true :=
    closure ⟨⟨.file, .write⟩, p, m, .any⟩
  ```
  Both compile (term mode in the second: `closure` alone is the entire proof — confirming its
  predicate accepts a write-expects-`any` sentence, i.e. one that does not keep L5/C15).
- [proven] Counts by kernel evaluation (`#eval`): `Shape.all.length = 72`, `Shape.allWf.length = 32`,
  `(Shape.all.filter (fun sh => !sh.wfB)).length = 40`, `Kind.all.length = 12`.
  So 40 of 72 shapes are ill-formed and satisfy the third conjunct via `!sh.wfB` alone. [proven]
  Additionally: for any ill-formed shape, `Shape.lawfulB sh = nameOk sh.kind.wire && (sh.kind ∈ Kind.all : Bool)`
  — the decode result is immaterial (compiles; checklist item 3). `lawfulB` is therefore trivially
  satisfied on ill-formed shapes by construction (the `!sh.wfB ||` disjunct, quoted in 1.1).

### 1.3 Docs wording vs what I verified

`C:\zcode\CMOS\src\im\docs\language.md`:

- L98 (law table, closure row): "`closure`: every sentence keeps the decidable laws through its shape;
  `space_size` 72, `wf_space_size` 32, `kinds_size` 12, computed by the kernel".
- L111: "**What the closure proves and what it does not.** It proves that every shape of the closed
  space keeps the laws above, and that the wire has one spelling."
- L111–116's hedge covers only the time axis (HRU/JLS/Sandhu, attenuation theorem missing). L96
  attaches a qualifier ("for every well-formed sentence with any legal path") to `decode_encode` only.
  Nothing hedges the law-coverage gap or the docstring tie-in.

## 2. Refutation attempts and outcomes

1. "The laws are carried somewhere the claim missed." — Attempted: grepped Closure.lean for every
   Laws.lean/Wire.lean theorem name (none present) and the whole project for uses of `closure`
   (only its own definition/docstring). `lawfulB` is fully defined in Closure.lean and references no
   law theorem; Lean definitions cannot secretly import theorems. **Refutation failed.**
2. "The membership conjunct is a real guard, not a tautology (it would catch a list drifting from the
   type)." — Attempted: machine-proved `∀ k : Kind, k ∈ Kind.all` independently by case enumeration.
   It holds for every term; the conjunct cannot fail on any current sentence. Its residual value is
   cross-edit consistency (the completeness proof breaks if the list lags the type) — but that value
   is exactly the "list completeness" item the claim already credits as machine-carried. Within
   `closure`'s conclusion it adds nothing beyond `Shape.all_complete`, which the proof already uses.
   **Refutation failed** (nuance recorded).
3. "The docs hedge; 'keeps the laws above' means the whole proof package, not `closure` alone." —
   Attempted: even on the charitable reading (the closure section = Closure+Laws+Wire), the 40
   ill-formed shapes do not keep L5: `write_says_expect` requires `hwf : s.wfB = true`, and a
   write+`any` shape violates L5 by construction; the package proves such shapes are refused
   (`decode_wf`, malformed per docs L79), not that they keep the law. And `closure`'s own theorem
   docstring (not the section) explicitly claims the tie-in to Laws.lean/Wire.lean. **Refutation
   failed.**
4. "Maybe L1/L5/I6 are wrong labels and the docstring means other 'universal' results." — Checked the
   law table (language.md L91–96): L1 = `pass_needs_both_grants`/`one_grant_never_passes` (Laws.lean),
   L5 = `write_says_expect`/`read_execute_expect_any` (Laws.lean), I6 = `decode_encode` et al.
   (Wire.lean). The labels match; none appears in `closure`. **Refutation failed.**

## 3. Verdict

**SURVIVES.**

Strongest single reason: the theorem's own docstring (Closure.lean L29) asserts "every sentence keeps
… the universal ones (through Laws.lean and Wire.lean)", while both the statement
(`s.shape.lawfulB = true`) and its one-line proof term reference only `all_shapes_lawful` and
`Shape.all_complete` — and I machine-proved the membership conjunct true of every `Kind` term and
`closure` itself true of an L5-violating sentence, so the docs' "every shape … keeps the laws above"
(language.md L111) is not what the theorem carries.

What would flip it: (a) any theorem in the project that composes `closure` with L1/L5/I6 (I grepped;
none exists), or (b) a doc hedge at language.md L96–98/L111 that conditions "keeps the laws above" on
well-formedness and discloses that the tie-in is by-package rather than by-theorem (no such hedge
exists; the existing hedges cover paths (IF2), the time axis (HRU), and the C# evidence chain (IF6)
only).

Per-element: statement content [proven, this run]; docstring-vs-statement mismatch [proven by read +
grep]; tautology/zero discriminating power [proven, this run]; doc overstatement at L111 [argued on
the doc's own words, backed by my machine results]; the "40 lawful vacuously" figure [proven: kernel
`#eval` = 40] belongs to C-IF03 and is cited here only as supporting context — it is correct.

## 4. Severity assessment

Sustained at **high** as a documentation/proof-integrity finding, with the boundary stated:

- For high: language.md is the spec-facing document and L111 sits in the section whose entire purpose
  is to prevent overstatement ("What the closure proves and what it does not"); `closure` is the
  proof's headline deliverable (it carries the owner's directive quote, Closure.lean L6); DMP's
  governance (C22, the lemma ledger of DMP ch. 06, IF6's argued/proven discipline) depends on honest
  proof attribution, and a docstring that claims more than its statement contradicts the project's
  own audit standard (`#print axioms`, check.sh) at the most visible point.
- What keeps it from critical: no law is unproven — L1 (universal over abstract `Grants`), L5 and
  I6's `decode_encode` (universal over paths for well-formed sentences) exist as separate theorems;
  the defect is attribution and quantifier wording, not a missing security property; the fix is
  textual (a conjunction theorem instantiating the universal theorems at `s`, plus rewording L111,
  as C suggests). Read as a functional-security severity it would be medium; as the spec-facing
  claim of a proof-carrying protocol, high is right.

## 5. Questions for the owner

- None blocking. For the record: severity calibration above is mine — if the team grades findings
  strictly by security impact (not doc integrity), C-IF04 would sit at medium alongside C-IF05/C-IF06;
  I kept C's high because the overstated sentence is the doc's own honesty section.
