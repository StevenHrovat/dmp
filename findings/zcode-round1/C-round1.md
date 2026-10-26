# C-round1 — IM attacker, round 1 (independent verification of DMP / IM)

- Role: C (IM attacker), static analysis only. Date of work: 2026-10-26 (fresh `date` readings taken at start and end; end 2026-10-26T21:45:58Z).
- Inputs used: `C:\zcode\CMOS\src\im\docs\` (language.md, findings.md, acknowledgements.md) and `C:\zcode\CMOS\src\im\proof\` (Im.lean, Im\*.lean, table\shapes.tsv, lakefile.toml, lean-toolchain, tools\check.sh). Nothing outside the walls was read; `src\im\src`, `src\im\tests`, `src\dmp`, `src\gravity`, `out\ORCHESTRATION.md` untouched and unread.
- Method upgrade: the pinned Lean toolchain (leanprover/lean4:v4.34.0) was already installed at `~/.elan`, so — within the brief's allowance for tiny standalone experiments — I copied `proof/` byte-for-byte (`cp`, not pin-verified) to `C:\zcode\CMOS\work\cr1\proof-scratch\` and machine-checked attack theorems there. Scratch evidence: `work\cr1\proof-scratch\Im\Attack.lean` + `work\cr1\proof-scratch\CheckAx.lean`. All scratch theorems rest only on `[propext, Quot.sound]` (some on nothing) — no `sorryAx` (kernel-checked, `#print axioms` output retained in the scratch dir). The repo itself was never modified.
- Claim tags: [proven] = machine-checked by me in the scratch copy (source identical to the repo by `cp`) or read directly off a statement; [argued] = derived from cited rules/theorem statements without machine assistance; [guess] = speculation, labeled.

## Verdicts at a glance

Counterexample hunt: I found no sentence that defeats the payload checker `Sentence.decode` on its own terms — it is strict and its strictness is real (magic/version, canonical u16 length, exactly two adjective bytes, byte alphabets, C15, boundaries 1..1024 all verified [proven] in scratch; the ill-formed space of 40 of 72 shapes never decodes). The failures are one layer out: the grammar accepts sentences whose *act* escapes the layer the kind names (C-IF01), and the spec's own prose contradicts its own grammar (C-IF02). Closure audit: the theorem is true but much narrower than the docs' headline — see the dedicated section.

Severity counts: critical 0, high 2, medium 4, low 5. (Matches with known findings IF1–IF9 are marked inline; no finding below duplicates a known one at equal scope.)

---

## Findings

### C-IF01 (high) — Path grammar admits `..` traversal; no containment or canonicalization rule exists anywhere in the docs, so a sentence of kind `file.read` can name (and act on) a noun outside the file layer

Where: `docs/language.md` line 19 (`path := 1 to 1024 bytes of a-z 0-9 . - /`), line 36–37 ("The layer places the noun"), `proof/Im/Grammar.lean` `pathByte` (a name byte or `/`, nothing else checked).

Counterexample sentence (literal):

```
file.read ../record/g apply any
```

Walk through the documented rules:
1. Alphabet: every byte is in `a-z 0-9 . - /` — `.` = 46, `/` = 47, the rest letters. `pathByte` accepts each unconditionally [proven: scratch `dotdot_path_ok`].
2. Length 11, within 1..1024 [proven: scratch `dotdot_path_ok`].
3. Verb/expect: read says `any` — well formed [proven: scratch `dotdot_wf`].
4. Wire: encodes and decodes round-trip via the package's own `decode_encode` [proven: scratch `dotdot_decodes`].
5. Permission: the door consults only the kind (`decideSentence` on `g.security kind && g.operational kind`); both tokens carrying the plain kind `file.read` pass it [proven: scratch `dotdot_passes_with_plain_grant`, kernel-evaluated, no axioms].

So the sentence is fully COMPLIANT per the docs' own rules and ACCEPTED, yet its act is a read addressed at `../record/…` — outside the layer whose name the permission was checked against. The spec's own semantic claim — the path is "the item inside the layer" (language.md line 19) — is defeated by the sentence, and no documented rule forbids that: there is no ban on `..`/`.` segments, leading `/`, empty segments, or double `/`, no normalization rule, and no statement of who owns containment (IM? the cm.os handle?). Note the door CANNOT catch this by design: "The layer places the noun and never grants (C12): who may act on it comes only from the grants", and grants are per-kind, never per-path — so the permission system is structurally blind to the escape [argued from language.md lines 35–37 + Laws.lean].

Why it matters: any conforming implementation that resolves `..` against a per-layer root (the Fuchsia/Capsicum/WASI shape the acknowledgements say the file layer follows) grants cross-layer access under a `file.*` grant; one that refuses `..` instead silently over-restricts legal paths. Two conforming doors decide the same sentence differently — breaking the spec's own headline "every door decides every act the same way" (language.md lines 4–5). This is the classic path-traversal hole admitted by the alphabet, with the check-out placed nowhere.

Related (same root, folded here per noun-vs-sentence spelling): `a//b`, `a/./b`, `./a` are distinct sentences naming at most one noun; I6's "one canonical spelling" is proven per-sentence on the wire (encode∘decode), never per-noun. Machine-checked accepted: boundary 1024 accepted / 1025 refused [proven: scratch `len1024_accepted`, `len1025_refused`] — the length rule is exact, the canonicality rule is absent.

Suggested fix: add to the grammar: no `.` or `..` segment, no empty segment, no leading `/`; require the path be canonical-relative; add `pathCanonical` to `pathOk` and one theorem `decode_preserves_canonical`. State in DMP 04 (IF8's candidate alphabet) that the path names a noun inside the layer *syntactically*, and put the sandbox contract (resolve against the layer handle, never above it) in the chapter.

### C-IF02 (medium) — The spec's own example sentences are not sentences of its own grammar (over-restriction / self-contradiction)

Where: `docs/language.md` lines 43, 32–33 vs. the grammar at lines 14–23.

Counterexample sentences (literal, from the doc itself):
- `setup.read toolchain/lean` (line 43, "First sentences") — missing mode AND expect.
- `setup.execute check apply` (line 43) — missing expect.
- `write job/x/control` (line 32, the `pause` spelling) — no layer, so not a `kind` at all.
- `read job/x/plan` (line 33, the `explain` spelling) — same.

Walk: the grammar (line 15) is `sentence := kind path adjectives` with `adjectives := mode expect` — both adjectives mandatory, and the wire table (lines 74–77) encodes a mode byte and an expect byte unconditionally: there is no payload for a two- or three-token sentence [argued from the grammar + wire table; structurally, `Sentence` has four fields]. The doc says these strings are "First sentences" and that each spelling "is exactly one sentence" — but under the grammar none of them is a sentence. COMPLIANT per the doc's examples layer, REFUSED by the doc's grammar and by any wire codec: an instance of (b) over-restriction created by the spec contradicting itself.

Why it matters: IM's entire value proposition is "the one shape every act is spoken in" (line 4). The examples also imply a `job/…` noun family that no layer in the closed list (setup/board/file/record) names, and no documented rule says which layer `pause`/`explain` map to — two implementers can choose `board` vs `file` and produce doors that accept different kinds for the same act.

Suggested fix: rewrite the examples in full four-token form (`setup.read toolchain/lean apply any`, `board.write job/x/control apply present` — or whichever layer owns `job`), and name the layer of `job/x` explicitly.

### C-IF03 (medium) — `closure` calls an L5-violating sentence "lawful": the lawfulB predicate passes all 40 ill-formed shapes vacuously

Where: `proof/Im/Closure.lean` lines 22–31 (`Shape.lawfulB`, `closure`); `docs/language.md` line 98 and line 111.

The gap, walked: `lawfulB sh := nameOk sh.kind.wire && sh.kind ∈ Kind.all && (!sh.wfB || (decode … sample … = some …))`. For a sentence violating L5/C15 — a write that expects `any`, e.g. `file.write a/b dry any` — the third conjunct is satisfied by `!wfB = true`, i.e. by the sentence being invisible to a strict door, not by keeping the law. Machine-checked: `closure` applied to exactly that sentence yields `lawfulB = true` [proven: scratch `closure_true_on_l5_violation`; the same sentence's payload is refused by `decode`, scratch `badWrite_never_decodes`]. 40 of the 72 shapes are "lawful" this way (72 − 32 [argued arithmetic: 12 kinds × 2 modes × 3 expects; 8 non-write kinds contribute 1 wf expect each, 4 write kinds contribute 2]).

Why it matters: language.md line 111 — "It proves that every shape of the closed space keeps the laws above" — is false for `closure` as a theorem: a write+any shape does not keep L5; it is excluded from door visibility by a disjunction that also makes the predicate incapable of failing on any sentence of the type. "Lawful" is a misnomer for "name-legal ∧ (invisible ∨ round-trips)". The material content of the kernel check is only the 32 sample round-trips plus the 12 kind names.

Suggested fix: split the predicate — `lawfulWf` over `Shape.allWf` only (round-trip), and a separate `illFormedNeverDecodes` — and reword line 111 to "every well-formed shape keeps the laws; ill-formed shapes are refused by the strict decoder."

### C-IF04 (high) — Closure-theorem audit: the theorem says substantially less than the docs claim; the docstring overstates its own statement

Where: `proof/Im/Closure.lean` lines 29–31 (docstring vs statement); `docs/language.md` lines 96–98, 111–116; `proof/Im/Grammar.lean` (`Shape.all_complete`); `proof/Im/Laws.lean`; `proof/Im/Wire.lean`.

Audit findings, each walked:
1. **Docstring–statement mismatch** [proven by reading]: the docstring says "The closure: every sentence keeps the decidable laws (through its shape) **and the universal ones (through Laws.lean and Wire.lean)**." The statement is `theorem closure (s : Sentence) : s.shape.lawfulB = true` — the universal laws (L1 both-grants, L5, `decode_encode`) appear nowhere in the conclusion. They exist as separate theorems; `closure` neither cites nor composes them. The claimed tie-in is by comment only.
2. **One conjunct is a tautology** [argued from Grammar.lean]: `sh.kind ∈ Kind.all` is provable for every possible `Kind` term by `Kind.all_complete` — the closed type leaves nothing outside the list, so this conjunct has zero discriminating power. The *actual* table a door consults (version-0's 1-row `ImKinds.Required` / version-1's 12-row table, both in the forbidden-to-me C#) is invisible to the proof: the closure cannot catch a C# table with 13 rows or different permissions. (Adjacent to IF7/IF2, but distinct: this is the vacuity of the table-law *inside the proof*, which neither finding states.)
3. **Quantifier scope** [argued]: `closure` quantifies over all `Sentence` terms — that is genuinely "every sentence" in the type-theoretic sense, and IF2 already says honestly that paths are not enumerated. The gap is the other direction: the *predicate* quantified over is too weak to be the "laws above" (see C-IF03), so "every sentence keeps the decidable laws through its shape" is true only because the predicate cannot fail.
4. **What is machine-carried vs separate** [proven/argued]: kernel-carried by `closure`'s chain: 72-shape list completeness (`Shape.all_complete`, structural), 12 legal kind names (`nameOk`, `decide`), 32 sample round-trips (`decide +kernel` at path `"a"`). NOT in `closure`: L1/L2 (parameterized over abstract `Grants`, universal — fine, but separate), L5 (via `wfB`, see C-IF03), I6 round-trip for arbitrary paths (`decode_encode`, separate, universal [proven]), the negative wire theorems (sample-only, see C-IF07), and all of Compose (see C-IF05).
5. **Hidden hypotheses / vacuity** [argued]: the HRU/take-grant hypotheses (closed table, attenuating tokens, no authority-creating sentence) are honestly disclosed (language.md lines 111–116, IF9) and the attenuation theorem is admitted missing. Degenerate cases are benign: `Layer`/`Verb` are non-empty by construction; `Net.galaxy []` is trivially robust (no outputs) in Compose. The counts check out by hand: 72 = 12·2·3, 32 = 8·2·1 + 4·2·2 [argued arithmetic; `space_size`/`wf_space_size` kernel-computed in the package].
6. **Doc headline vs theorem** [argued]: the owner's directive quoted in Closure.lean line 6 — "generate the whole possibility space of IM commands and prove every one of them DMP-compliant" — is realized as: generate every *shape*, prove 3 conjuncts per shape (one tautological, one vacuous for 40 shapes), plus separate theorems for the rest. That is a real and decently honest partial result; the one-sentence summaries at language.md line 111 and Closure.lean line 9 claim more than the statement delivers.

**Verdict**: the closure theorem, as stated in Lean, proves "the shape list is complete, kind names are legal, and each well-formed shape's sample sentence round-trips on the wire" — it does NOT prove "every sentence keeps the laws above" as language.md's prose asserts; the laws live in separate, partially universal, partially sample-level theorems that `closure` does not tie together. The docs' honest hedges (IF2, the HRU paragraph, IF6's "argued, not proven") cover enumeration-vs-paths and time, but not the law-coverage gap or the docstring overstatement. Suggested fix: make `closure` a conjunction that actually instantiates the universal theorems at `s` (L1 is parameterized, L5 and `decode_encode` apply directly), or rename/reword to match the statement.

### C-IF05 (medium) — The composition theorems' "door" is not the IM door: no kind, no grants, no sentence, no well-formedness

Where: `proof/Im/Compose.lean` (whole file); `docs/language.md` line 97 (law table row "the door makes the composition sound"); DMP 04 quotes in the file docstring.

Gap: Compose's `Msg` is `{sec, op, body : Nat}`; `door ins = ins.filter Msg.ok` checks only that both signature bits are true. It never consults `Kind`, `Grants`/`decideSentence`, or `Sentence.decode` — the body is an opaque `Nat` in which a sentence cannot even be represented, so "soundness" propagated through `galaxy_robust`/`sound`/`galaxy_is_a_node` is exactly "outputs carry both signature bits", i.e., authentication presence, not sentence lawfulness and not authorization. language.md's law table cites these theorems in the same table as L1–L5 under the unqualified phrase "the door makes the composition sound", inviting the reading that the L1 door is what makes galaxies sound; the file is honest about the abstraction in its docstring, the citation is not. (Also: `echo_preserves`/`im_makes_echo_sound` correctly demonstrate the door is load-bearing *for signature bits* — the model was built for C19, which is all DMP 04 asks of it per the quotes; the mismatch is in the doc's framing.) Vacuity: `Net.galaxy []` and `Built.galaxy []` make `galaxy_robust` hold with no members — harmless but worth a sentence in the docstring.

Why it matters: the spec's security story ("every boundary between scales is an IM door: a message passes only with both signatures" per the DMP 04 quotes) is proven for signature bits only; the reader of language.md cannot tell that grant-checking, decoding, and sentence shapes are unmodeled in the composition result. Suggested fix: one qualifying clause at language.md line 97 ("the door of the composition model checks the two signatures only"), and a roadmap line for re-proving composition over `Sentence`-carrying messages.

### C-IF06 (medium) — No bridge theorem: bytes → decode → grants → door → galaxy is never composed; the envelope kind mapping is unmodeled and is where the payload guarantees are conditionalized

Where: the three proof islands `Wire.lean` (bytes→sentence given a kind), `Laws.lean` (kind→verdict given grants), `Compose.lean` (signature bits→robustness); `docs/language.md` lines 4–5, 70 ("the envelope's `kind` field already names the kind").

Gap: the headline "every door decides every act the same way, with both witnesses' grants" (lines 4–5) is not a theorem anywhere — there is no definition that takes wire bytes plus two grant sets to a verdict, and no composition of `decode_wf` + `decideSentence` + `galaxy_robust`. Moreover the payload carries no kind field: the sentence's kind is whatever the envelope says, and the proof takes the kind as a *typed* parameter [proven: scratch `same_payload_two_kinds` — one payload, two envelope kinds, two different well-formed sentences, both accepted by `decode`; `decodes_both`]. Every payload-level guarantee is therefore conditional on the envelope kind being parsed to the right table row by code the proof never sees (the string→row mapping's alphabet, case rules, and exactness are in no file I was given). Within my inputs a verifier that matched kind strings loosely (prefix/case-insensitive) would accept kinds outside the 12 — nothing documented forbids it; DMP 04's encoding section is outside my walls, so this may be answered there (question for the owner below).

Why it matters: this is precisely the seam an attacker works, and the docs' own honesty (IF6: "argued, not proven" for the sentence evidence chain) covers the C# side but not the absence of an in-proof bridge. Suggested fix: one definition `admit (g : Grants) (kStr : List Nat) (b : List Nat) : Verdict` wiring a (proved-total) kind-string parser to `decode` and `decideSentence`, plus one theorem "admit = refuse unless both grants ∧ well-formed", and the composition re-run over admitted sentences.

### C-IF07 (low) — The negative wire theorems are proven only for the sample path `"a"`; the universal versions are cheap (machine-checked), so the limitation was a choice

Where: `proof/Im/Wire.lean` lines 131–141 (`trailing_byte_malformed`, `wrong_version_malformed`, `ill_formed_never_decodes`, all over `Shape.all` with `Shape.sample` = path `[97]`); `docs/language.md` line 96 lists them under I6 with the "any legal path" qualifier attached only to `decode_encode`.

Gap: universality over paths for trailing-byte/wrong-version refusal holds by structure — `tail2` is strict on the post-length remainder, and the header pattern is exact — but is not what the theorems say. Machine-checked in scratch: the universal statements `∀ s, decode s.kind (s.encode ++ [0]) = none` and `∀ s, decode s.kind ([73,77,83,0] ++ s.encode.drop 4) = none` both compile at trivial cost [proven: scratch `trailing_none_all`, `wrong_version_none_all`; axioms propext+Quot.sound only]. `ill_formed_never_decodes` is subsumed for all inputs by the universal `decode_wf`, so no substance gap there. Suggested fix: commit the universal versions (they are short); align language.md line 96.

### C-IF08 (low) — Endianness of the `u16` path length is unstated in the language doc; the proof fixes big-endian

Where: `docs/language.md` line 75 ("`bytes16`: `u16` length, then the bytes" — no byte order) vs `proof/Im/Wire.lean` line 6 ("a `u16` length, big-endian") and `encode` (`length / 256, length % 256`).

Gap: the normative doc for door implementers underspecifies; a door reading little-endian mis-decodes any path ≥ 256 bytes (a plausible payload: the setup/table layers have no such paths, `file` will). Two doc-conforming doors decide the same payload differently — the same-decision claim again. One-word fix.

### C-IF09 (low) — The error taxonomy (Malformed vs UnknownVersion) asserted by the doc is unrepresentable in the proof

Where: `docs/language.md` lines 79–80 (`ImFormatError.Malformed`, `UnknownVersion`) vs `Wire.lean` (`decode : … → Option Sentence` — every refusal is `none`).

Gap: the doc's wire row cites theorems for I6, but the model cannot distinguish the two refusal classes the doc promises, so nothing pins which byte error yields which class. Not unsound; a fidelity gap between doc and model. Fix: either an `Either ImFormatError Sentence` model or a note in language.md that the taxonomy is C#-side only.

### C-IF10 (low) — C15's second clause ("a write first reads what it changes") is cited for L5 but not captured by it

Where: `docs/language.md` line 28 (verb table, write row) vs `Laws.lean` `write_says_expect` and law table line 95.

Gap: L5 captures only "the sentence says what it expects"; "first reads" is sequencing across sentences, unenforceable at the one-sentence level the closure covers, and the citation does not note the drop. If "first reads" is a rule, an act consisting of a lone `file.write … apply absent` complies with every per-sentence rule while skipping half of C15 — the language has no way to say so. [argued; ambiguous whether C15's clause is semantics-of-write rather than a rule — question for the owner.]

### C-IF11 (low) — check.sh's escape-hatch scan misses `Table.lean` and `partial`

Where: `proof/tools/check.sh` line 16–17 (`grep -rEn "$hatch" Im Im.lean`), hatch regex lacks `\bpartial\b`.

Gap: `Table.lean` (which regenerates the C#-replayed table) is not scanned for `sorry`/`axiom`/`native_decide`; `partial def` is not in the regex. Mitigation: Table.lean declares no theorems, and the `#print axioms` gate (lines 20–31) covers every `theorem` in `Im/*.lean`, so a sorry could not hide in the audited theorems — the residual risk is a tampered table generator or a `partial`-based non-theorem definition. One-line fix.

### Rediscoveries of known findings (through my own analysis, for the record)

- IF2 (shapes vs paths): confirmed and sharpened — the sharper instances are C-IF04(2) (table-membership tautology) and C-IF07 (negative theorems sample-only); the doc's IF2 hedge covers `decode_encode` but not those.
- IF5 (orders, 1 vs 2 signatures): visible to me only via findings.md's own report (DMP 04 and T24 are outside my inputs). My addition: orders are not IM sentences at all (no grammar production), so the closure says nothing about them; see Questions.
- IF8 (path alphabet): confirmed — and C-IF01 is a hole *inside* the alphabet as currently specified (`.` and `/` combine into `..`), which the IF8 candidate text should be written to exclude.
- IF9 (attenuation theorem missing): confirmed; it is the time-axis half of why `closure` cannot say "no part ever acquires a kind it was not granted".
- IF1, IF3, IF4, IF6, IF7: no independent addition beyond what the findings file already records (IF6's honesty materially bounds several of my findings' severity).

## Closure-theorem audit — dedicated section (verdict)

**Verdict (one line):** The Lean `closure` theorem is true but proves only "the 72-shape list is complete, the 12 kind names are legal, and each of the 32 well-formed shapes' sample sentences round-trips on the wire" — with one conjunct a tautology of the closed type and 40 shapes "lawful" vacuously — while the laws the docs list (L1, L5, universal I6, composition) live in separate theorems it never composes; therefore language.md's "every shape of the closed space keeps the laws above" (line 111) and Closure.lean's own docstring overstate the theorem, and the honest statement is the narrower one, plus the separately-proven universals.

Supporting detail is C-IF03, C-IF04 (audit items 1–6), C-IF05, C-IF06, C-IF07. Quantifier scope: "every sentence" is honest type-theoretically; "every path" is honest only for `decode_encode`/`decode_wf`/`decode_kind` (universal) and false for the negative wire theorems (sample-only, cheaply fixable). Hidden hypotheses (HRU set) are disclosed in the docs and admitted incomplete (attenuation theorem). Vacuity: empty galaxy trivially robust (benign); no empty-table or empty-layer degeneracy is expressible (types non-empty by construction).

## Questions for the owner

1. Envelope kind field: what alphabet/length/exactness rules govern it, and must a verifier map it to a table row by exact string equality only (no case-folding, no prefix)? This is the one unguarded input to every payload guarantee (C-IF06); if DMP 04 already answers it, IM's proof should model the answer.
2. Path containment: is the `..`/canonicality ban to live in IM's grammar (my recommendation, so doors are uniform) or in the cm.os handle resolution contract? Who owns the fix for C-IF01?
3. `job/x`: which layer do the `pause`/`explain` spellings belong to (board? file? a future layer)? The examples imply a noun family the closed layer list does not name (C-IF02).
4. Are `lift`/`override` orders intended to stay outside IM's grammar permanently (so the closure claim never has to cover them)? IF5's signature-count conflict is decided, but their absence from the grammar is nowhere stated as a rule.
5. Is C15's "a write first reads what it changes" a per-act rule (needs an enforcement story beyond one sentence) or a description of write semantics (then the law-table citation should say so)? (C-IF10.)
6. May the universal versions of the negative wire theorems (C-IF07) be committed in place of the sample-only ones? They compile today at trivial cost (scratch evidence available).
