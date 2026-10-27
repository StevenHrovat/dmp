# Proposal brief: two axioms (the owner, 2026-10-27)

Status: **brief, not a DMP text change.** The owner approves every change to the constitution (chapter 00, "Who maintains it"; G0). This
file records his proposal of 2026-10-27 and Team Fable's attack on it, so that he can decide with the refuters in front of him. The
theorem pass of this pull request stays on the three axioms of DMP 0.9.8: changing the base while the pass runs would be, in his own
words about the constraints (2026-10-26 23:54Z), using the wrong tools; the two-axiom form is for the pass after this one, if he chooses it.

## 1. The owner's words (verbatim)

> Deriving and abstracting from QG and DMP give us the actual axioms: Two: 1. Information 2. No information without existence in a
> self-balancing duality. Which gives us the equations to solve any possible probability space simply by proving it's existence in DoE
> (Duality of existence) with a vector field that can span it. Both automatically fall out and I can not think of any possible refusions.

And the correction, a few minutes later: "actually: self-propagating duality, since even an event horizon leaks something, so some
propagation is unavoidable."

## 2. What holds

The reduction is the move C∞ asks for ("merge axioms into fewer, stronger ones"), and its shape is already in the text: T39 (T1 after the
renumbering) says no trust without information and no information without trust, and Axiom 3 says that from trust nothing follows about
information but its existence. The owner's second axiom takes T39 as the axiom and eliminates the word *trust*: to be trusted is to exist
in a Duality that propagates itself. Read that way the three axioms of 0.9.8 fold as follows.

| DMP 0.9.8 | In the two-axiom form | What the words must then carry |
|---|---|---|
| Axiom 3 · Information (the record, counts and content, from trust only existence, admission, containment, the hierarchy, the evolution) | Axiom 1 · Information | unchanged, plus the sentence "everything that exists is information" (the converse direction of T39) |
| Axiom 1 · The Duality (the gate: both halves, the stricter answer; the balance: works towards the declared trust, bounds before balance) | the "self-propagating duality" of Axiom 2 | *duality*: two halves, independent under the declared failure classes, each with full reach and gated only by the other; *self-propagating*: it propagates its existence (the field outward from the pair, T32; a Duality in every layer, T38; the clone that mints, chapter 00) and never its content (gravity contains; what leaves is the floor's counts, T31), within its declared boundary and by evidence only (the balance's bound, Axiom 1; bounds before balance, T3d) |
| Axiom 2 · Trust (evidence verified live at the point of use; never a carrier, an earlier read, a claim, a memory, a position; no information is ever trusted; the field; gravity contains) | the "existence" of Axiom 2 | *existence at a time*: both halves hold a live standing for it then (the words, "inside"); a standing is evidence with a validity; the absence of evidence moves nothing; the field is the shape of existence over the grant graph |

So the reduction is sound in the sense that matters: every theorem of the chapter still has a derivation, from the two axioms and the
words. What moves is the load: the sentences of Axiom 1 and Axiom 2 do not vanish, they become the definitions of *duality*, *self-propagating*
and *existence*.

The correction from *self-balancing* to *self-propagating* is right in DMP's objects and the reason given for it is the floor. A horizon
leaks (Hawking 1975), and DMP's horizon leaks exactly the counts (T31: size, staleness, rotation interval; `Physics.Entry.ext`): that is the
propagation that is unavoidable, and it is the propagation of existence, which Axiom 3 already names as the one thing trust yields. So the
word is safe only with its object stated: a duality propagates its *existence* (outward along the field, into every layer, into the next
instance) and contains its *content*. Without that object "self-propagating" would also name a duality that spreads its content or widens
itself, which the balance forbids (no part widens a grant or moves the boundary to get there). The count drops from three to two; the text of the words grows by about what the two merged axioms said. That is a real gain
only where a definition is clearer than an axiom, and the owner's method rule says it usually is.

The probability-space sentence has one exact reading in DMP's objects. The "vector field that can span it" is the VIBE field (T32) over the
grant graph, and "proving its existence in the DoE" is the statement that every item of the space is held by both halves and reached by
routing (T39 with C12: `inside_iff`, `tr_milky_way_first`, `tr_exit_last` in Gravity). The probability space itself is Axiom 3's
"representative composition of requests", the demand D over the items; the equations that come out of it are the two the physics pass found
(gravity `docs/physics.md`, section 2): the expected hops of the layout are at least H(D) / log₂ b (Shannon 1948; Huffman 1952 attains it),
and the fan-out b is bounded by the Duality's budget of live checks (`Physics.lean`). Nothing more falls out, and nothing more is needed.

## 3. The refuters (the owner asked for them)

1. **Independence does not fall out.** "A self-balancing duality" is satisfied by one person holding both halves and keeping them in
   balance with each other; nothing in the two sentences says the halves share no failure cause. Under the two axioms as worded, a pressed
   instance exists in a DoE and is sound; Gravity's `Ground.pressed_collapse` and `DoT.not_minted_collapses` show that one influence then
   passes any act alone. The fix is one word in the definition of *duality* (independent under the declared classes, the person always among
   them, finding F1), and without it the reduction admits the naked singularity that T-P forbids.
2. **The converse direction does not fall out.** "No information without existence" gives information ⇒ existence in a DoE. T39 needs the
   other direction too: no existence (trust) without information, so that a standing with nothing to act on is not inside. That direction
   must sit in Axiom 1 (everything that exists is information: a standing is a record) or the chapter loses the half of T39 that keeps a
   trusted part with no admission outside.
3. **A spanning field does not solve a probability space.** Two demand distributions with the same support give the same reachability (the
   same "existence in the DoE", the same spanning field) and different optimal layouts (different Huffman trees, different expected hops).
   The field spans the support; the measure is an input (the demand, configuration under T4), never a consequence. So "the equations to solve
   any possible probability space" holds for the support and the bounds above, and fails for the measure: produce such a pair and the strong
   reading falls, while the exact reading of section 2 stands.

4. **Propagation without its bound.** A duality that propagates itself without the declared boundary as its limit would add standings or
   admissions by its own act: `Standing.loosening_needs_both` and `Field.k4_refresh_never_raises` refuse that (nothing the system does
   alone loosens or raises the potential), and T3d ranks the balance below the bounds. So the definition of *self-propagating* must say
   "within the declared boundary, by evidence, and only its existence": state it, and the refuter is answered; leave it out, and the two
   axioms admit a duality that grows past its declaration.

A fifth, weaker: "QG" (quantum gravity) is cited as a source. The physics pass found that DMP's objects sit on classical results (the horizon,
no hair, the area theorem, Chandrasekhar) and touch quantum gravity only where it is open (the information paradox, spin networks); a
derivation from QG would be a derivation from conjecture. The two axioms stand or fall on DMP's own objects, which is where section 3 tests them.

## 4. Recommendation

One recommendation, not a menu: keep the three axioms for this pass, and after the owner has approved the renumbered theorems, run one more
pass on the two-axiom form with the four refuters as its test: (1) write the words for *duality*, *self-propagating* and *existence* so that
independence, the converse direction and the bound of propagation (existence outward, content contained, within the declaration) are in them; (2) re-derive T1 to T29 and T-P from the two; (3) show in Lean that `Ground.pressed_collapse`
is still refused and that `inside_iff` still has both directions. If all four pass, the reduction is the parsimony C∞ asks for and the
chapter gets its shortest form; if one fails, the sentence that fails is the next definition to challenge.
