# 00 · Preamble

What DMP is, how a pull request is judged against it, and who keeps it.

## What DMP is

**The mission of CM** (the owner, 2026-10-25, verbatim): "It turns Information into Insight through provably safe and compliant, near-infinite composability, while maintaining absolute Observability." DMP is how CM keeps that promise: every rule below serves it.

DMP is the rule book of CM. It has two parts that age differently. The **constitution** ([01](01-constitution.md)) is one
page of rules that hold from the first day and do not bend. The **chapters** describe how each part is built; they are living
text that the CM coordinator keeps current while CMOS is being built, each section marked stable or draft.

Status: stable since DMP 0.1.0
Owner: CM coordinator
Enforced by: DMP-007

## The marks

Every `##` section of every chapter carries a `Status:` line: `Status: draft`, or `Status: stable since DMP x.y.z`. A stable
section also carries an `Owner:` line (a role, never a name) and an `Enforced by:` line that lists the rule ids of the `dmp`
group that check it, or the words `none yet` when no check exists. A section that says `none yet` is printed by the
`dmp` runner on every run, so nobody mistakes prose for a gate. A stable section without a check is a defect in DMP, not a
rule; the fix is a check, or the mark goes back to draft.

A section may also carry a `Law:` block: numbered sentences (`- C2.L1 ...`) that Gravity proves, followed by a line
`Laws file: <path> sha256 <hex>` that locks the formal laws (`CM.BlackHole/docs/gravity.md`, "How a section gets laws"). The
laws file quotes every sentence word for word, and changes only together with the section.

The constitution has no draft sections. The CM coordinator changes a mark only in a pull request whose title says so.

Status: stable since DMP 0.1.0
Owner: CM coordinator
Enforced by: DMP-007, DMP-018

## How a pull request is judged

A pull request is judged against the constitution and the stable sections, and only those. It is refused when the `dmp`
group of `tools/verify` fails, or when a reviewer finds that it breaks a stable section no check covers yet (and the review
then opens the missing check as an issue). Draft sections are guidance and never a reason to refuse. Every pull request goes
through the CM coordinator, who runs the pipeline, tests it and merges it (chapter 14).

Status: stable since DMP 0.1.0
Owner: CM coordinator
Enforced by: DMP-007

## Who maintains it

DMP, IM, CM and Gravity are the **root repositories**. They are text and code, never an instance of CMOS, and they are never minted: they
stay under G0 for good, with `LHC pending` in their record. In them the **owner**, the person who holds a copy of the root repositories,
stands for both halves (G0). Every change to the constitution or to a stable section, and every grant of authority, is an act of the owner,
and its record is the merged pull request the owner approved.

- **Grants.** The owner may grant part of this authority to other parts (an agent, a coordinator, a person) for named acts. A grant is a
  record (Axiom 3) with a bound (T1); the owner alone may withdraw it, as a tightening (T24); it is never passed on unless it says so. Rule
  DMP-009 refuses a change to the wording of a grant the owner did not approve.
- **The standing grants here.** The CM coordinator keeps DMP and its marks (status, owner, enforcing rule) and merges what the owner
  approved; a constellation coordinator proposes changes to its own chapter; a change to the constitution needs the owner's approval.
- **Clone, press, mint.** Any organisation may copy the root repositories onto its own systems. Whoever holds that copy is its owner, with
  the same standing as above, and nothing in the copy depends on the copy it came from. The owner presses an instance (G0, T-P), and once
  a pressing of the same configuration has passed, the organisation mints it (C17). The minting is a trust rotation: every key rotates,
  the owner role ends, and ultimate authority rests with the White Key holders under a majority of trust (T5). The minted instance is
  contained on its own: trust never crosses instances, so it shares none with any other CMOS, the root repositories included; a newer
  DMP reaches it only as information through an entry path its own two witnesses opened (T-P).

Derived from: G0, T-P, Axiom 1, Axiom 3, T1, T5, T24, C17. The owner (2026-10-26): "As the root DMP/IM/CM repos, they are in a permanent
non-minted state, so the ultimate authority goes to the owner (which is already defined and can from there be passed down/extended to
agents/people etc.), until a minting takes place, at which point ultimate authority rests with the WKHs"; "So theoretically any company
can git clone the repos to their own server, become the owner, then mint and have their own, fully contained, CMOS."

Status: draft (proposed 2026-10-26; replaces the text stable since DMP 0.1.0)
Owner: CM coordinator
Enforced by: DMP-009

## The version

`DMP/VERSION` holds the DMP version, `MAJOR.MINOR.PATCH`. It moves only in a pull request that promotes a section to stable
or changes the constitution, so a frozen component can say which DMP it was built against. A section cannot be stable
since a version newer than `VERSION`.

Status: stable since DMP 0.1.0
Owner: CM coordinator
Enforced by: DMP-007

## How DMP hardens

Until CMOS runs an organisation in production, DMP is best-effort and always changing. When it does, the chapters harden: many
hands from that organisation go over them with great effort, and once final they are set in stone. Until then "written once"
is true of the constitution only.

Status: stable since DMP 0.1.0
Owner: CM coordinator
Enforced by: none yet
