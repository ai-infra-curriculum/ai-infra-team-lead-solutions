# SOLUTION — Exercise 02: Strategy Memo

> Read this *after* you have attempted the exercise. The worked
> memo below justifies a specific roadmap decision — a scope cut
> — to a skeptical adjacent-team lead. Names, dates, and the
> technical specifics are synthetic and should be treated as
> **local exercise context**, not as a real company's facts.

## 1. Solution overview

### What this exercise is really testing

The exercise asks you to write a short memo justifying one
concrete roadmap decision — a cut, a re-sequencing, a date
push, or a headcount ask — to a skeptical stakeholder. The
grading bar is **precision about tradeoffs**, not persuasion
quality. A memo that lists three reasons to do the thing scores
mid-rubric; a memo that lists the two reasons against the
decision, shows why those reasons still do not clear the bar,
and names what the stakeholder *actually loses* scores at the
top.

Four properties separate a trust-building memo from a
trust-burning one:

1. It names the specific decision in one sentence at the top.
2. It presents the choice the stakeholder is being asked to
   accept and the alternatives that were rejected, with reasons.
3. It is honest about what the stakeholder loses. A memo that
   dresses a loss as a win reads as either naive or manipulative;
   either is bad.
4. It leaves a defined off-ramp — "if X changes, we revisit."

The parent [`SOLUTION.md`](../SOLUTION.md#the-roadmap-exercise-02)
and the module README's framing on the "cuts conversation" are
the canonical source for this.

### Why "cut" is the default decision to walk

A cut is the hardest version of this memo. Re-sequencing can
be dressed as "doing the same work in a different order";
date-push can be dressed as "same scope, more time"; headcount
ask is a decision for the person above the stakeholder. A cut
says to the stakeholder: your thing is not getting done.
Getting cut-memos right is what trains the reflex for the
easier cases. The worked example below is therefore a cut.

## 2. Worked answer or implementation

### Scenario (synthetic, labeled as such)

**Your team:** Fleet-Serving (same synthetic team as
[exercise-01](../exercise-01/SOLUTION.md)).

**The decision:** Cut the "audit-log schema overhaul" from the
Q3 roadmap. The target completion was week 11 of 13. At the
week-8 mid-quarter review, the dependency on the Governance
org's new control catalog is still unconfirmed, and the one
engineer on the item (Frank) joined the team at week 2 and is
still ramping. Three other committed items are high-confidence
green and would be put at risk by re-sequencing to keep this
one in.

**The stakeholder:** Governance Lead ("Mina," synthetic). They
had told the audit committee that the new schema would be in
place for the Q4 audit cycle. The schema was downstream of the
control catalog their own team owed us, which has slipped.
They did not want to be the reason it slipped; a cut on our
side gives them a convenient narrative and they will push
back.

### The memo (worked example)

Target length is ~500 words. One page. Written to the
stakeholder, not about them.

---

**To:** Governance Lead, Platform-Governance team\
**From:** Team Lead, Fleet-Serving\
**Date:** Week 8, Q3 (synthetic)\
**Subject:** Q3 cut: audit-log schema overhaul

**Decision.** Fleet-Serving is cutting the audit-log schema
overhaul (Q3 item 4) and re-committing it to Q4 week 4, with
a decision gate at Q3 week 11 to confirm the Q4 start is
viable. This is a one-quarter slip of a single scoped item,
not a cancellation.

**Why now.** At week 8 the item is low-confidence for a Q3
landing for three reasons, any one of which would be
recoverable but which compound:

1. *Dependency.* The schema was designed against the next
   control catalog your team owns; the catalog has not been
   finalized. Building against a draft and re-cutting later
   costs us roughly as much engineering time as starting in
   Q4 against the finalized version.
2. *Capacity.* The item is single-owner. The owner is five
   weeks into the team; the module's estimation framing (see
   `../SOLUTION.md#estimation-discipline-exercise-03`) prices
   new-hire capacity at roughly 50-70 % through the first
   60-90 days. The Q3 estimate did not account for this; a
   recalibrated estimate lands past week 13.
3. *Opportunity cost.* Items 1 and 3 on the Q3 roadmap (the
   gateway v2 launch and the training-pipeline migration) are
   high-confidence green and would be put at risk by a
   re-sequence that moves owners onto item 4. Those two items
   have dependent teams already planning against them.

Together, these push the item below the 30 % confidence bar
the team uses for a public Q3 commitment.

**Alternatives considered and rejected.**

- *Hero plan.* Put two engineers on it from week 8, with
  weekend coverage. Rejected: the module's framing (parent
  `SOLUTION.md`) names hero-dependent estimates as a
  predictable future miss. Even if it landed, it would
  compromise items 1 and 3.
- *Scope-shrink.* Ship a partial schema that covers only the
  three highest-volume request classes. Rejected because the
  audit committee's requirement (per your team's own brief)
  is schema coverage across all gateway traffic; a partial
  ship does not meet the governance bar.
- *Push to Q3 week 13.* Rejected because it preserves the
  surprise-at-the-end failure mode the module explicitly
  warns against. A week-13 miss gives you no replanning time
  ahead of the Q4 audit.

**What you lose.** The schema is not in place for the Q4 audit
cycle. If the audit committee had already been told it would
be, that is a renegotiation your team owns with them; we can
provide the technical justification above in writing if
useful. We also lose two weeks of partial work the team has
already done against the draft catalog; that work carries over
into the Q4 start and is not wasted.

**What you gain.** A Q4 start against a finalized catalog is
estimated at ~6 weeks to a committed landing (reference-class
anchored against the previous schema migration, which took
7 weeks). That is a higher-confidence landing than any Q3
recovery plan the team can offer at week 8.

**Decision gate.** The next review of this cut is Q3 week 11.
If the control catalog has been finalized by then and we have
confirmed the Q4 week-4 start, we close the gate; otherwise
we reopen the conversation with you and with your sponsor
about further slip or scope change.

**Ask.** Please confirm by end of week whether the Q4 week-4
restart works for your team's commitments, and whether you
want us to co-write the audit-committee update or handle it
separately.

---

### Why this memo works

- **First sentence is the decision.** No burying the lede.
- **Three reasons, not seven.** Each is independently
  sufficient to drive the cut; together they clear the bar
  with margin. The module's framing is that any single
  reason is a one-point-of-failure argument.
- **Alternatives named and rejected.** The stakeholder cannot
  come back with "but did you consider X?" — you did, and
  here is why it was not enough.
- **"What you lose" is explicit.** No euphemisms. This is the
  line that builds trust; without it the memo reads as
  spin.
- **Reference-class estimate for the Q4 landing.** Not a wish.
  A grounded prediction, which the stakeholder can test
  against their own history.
- **Decision gate with a date.** The cut is not an open-ended
  slip; it is a move to a new commitment with a specified
  check-in.
- **Ask ends with a yes/no action.** The memo is answerable,
  which is what makes it a decision document rather than a
  broadcast.

## 3. Validation steps

1. **One-sentence decision test.** Can a reader who reads only
   your subject line and first sentence state the decision
   back to you? If not, rewrite.
2. **Alternatives test.** Name at least two rejected
   alternatives with reasons. If you cannot name one, you have
   probably not considered any; go think longer.
3. **Loss test.** Point to the sentence where the stakeholder
   loses something concrete. If your memo does not contain
   one, you are either not actually cutting anything or you
   are hiding the cost.
4. **Reference-class test.** Any date in your memo should be
   anchored to a past data point (same team's previous
   similar project, or a documented org-wide benchmark). A
   date pulled from the ceiling is a date the stakeholder can
   dismiss.
5. **Decision-gate test.** Does the memo specify a date at
   which the decision is re-opened? Without one, the cut is
   open-ended and the stakeholder cannot plan against it.
6. **Ask test.** Does the memo end with a specific yes/no
   question? If it ends with "let me know what you think,"
   it is not a decision memo, it is a conversation starter.
7. **AI-infra specificity test.** Where the cut implicates
   AI-risk exposure (governance evidence, serving SLAs,
   model-behavior commitments), does the memo name it? If
   the stakeholder is Governance, cost, or safety, the
   NIST AI RMF category the commitment maps to is usually
   worth citing explicitly (see §6).

## 4. Rubric or review checklist

| Dimension | L1-L2 | L3 | L4-L5 |
|---|---|---|---|
| **Decision clarity** | Decision stated vaguely or buried in the body. | Decision stated in the first two sentences. | Decision stated in one sentence at the top, with scope bounded (one-quarter slip vs. cancellation, etc.). |
| **Reason triangulation** | Single reason. | Two or three reasons, each independently sufficient. | Reasons are independent (not three framings of the same one) and anchored in data the stakeholder can test. |
| **Alternatives** | None named. | At least two rejected alternatives with reasons. | Alternatives include the obvious hero/shrink/push options and name why each fails against the specific stakeholder. |
| **Honesty about loss** | Loss not named. | Loss named. | Loss named, quantified where possible, and distinguished from reversible vs. irreversible cost. |
| **Decision gate** | None. | Date and trigger specified. | Date, trigger, *and* the counterfactual (what happens if the trigger fires) specified. |
| **Ask** | None or vague. | Specific ask ending the memo. | Ask is answerable yes/no, with a stated deadline. |

**Caps.** A memo with no "what you lose" section caps at L3.
A memo that presents the cut as a shared decision when it is
actually your team's unilateral call caps at L2.

## 5. Common mistakes

- **Writing a memo that reads as an apology.** Apologies are
  appropriate when you missed a committed date. This is a
  renegotiation ahead of the miss; the tone should be matter
  of fact, not apologetic.
- **Framing the cut as a benefit to the stakeholder.** It
  isn't. Say what they lose.
- **No reference-class anchor for the new date.** "We'll get
  to it in Q4" with no supporting estimate is the same
  commitment quality that produced the Q3 miss.
- **Bundling the cut with other news.** A memo about one
  decision. If you have three decisions, write three memos.
- **No decision gate.** An open-ended slip erodes trust worse
  than a hard cut.
- **Writing in the passive voice.** "A decision has been made
  to cut" hides the owner. Name yourself as the decision
  owner.
- **Overlong.** If the memo is over one page, you are hiding
  the argument. Cut until the argument stands on its own.
- **No AI-infra context where it matters.** Governance,
  safety, or cost cuts that do not reference the frameworks
  the stakeholder's org is accountable to (NIST AI RMF, the
  team's internal risk register) read as technically naïve.

## 6. References

- **Local exercise context — module SOLUTION.** Parent
  [`SOLUTION.md`](../SOLUTION.md#common-mistakes-graders-see)
  on hero-dependent estimates and replanning by extension.
- **Local exercise context — learning module README.**
  [`lessons/mod-703-project-roadmap/README.md`](https://github.com/ai-infra-curriculum/ai-infra-team-lead-learning/blob/main/lessons/mod-703-project-roadmap/README.md)
  — specifically the "Cuts and slips" subsection on surfacing
  risk early and bringing options rather than a verdict.
- **NIST AI Risk Management Framework** —
  <https://www.nist.gov/itl/ai-risk-management-framework>.
  Use the GOVERN function to name the governance accountability
  your cut affects: who owns the policy commitment, what the
  evidence requirement is, and what the decision chain looks
  like. If the cut touches audit evidence, the RMF is the
  public-standard framing a Governance stakeholder expects.
- **OWASP Machine Learning Security Top 10** —
  <https://owasp.org/www-project-machine-learning-security-top-10/>.
  Only applicable if the item you are cutting has an ML-security
  dimension (e.g., a serving-stack control that defends against
  one of the listed risks). Cite the specific risk ID in the
  memo so the stakeholder can look it up.

### Known research gap

An attested public example of a published scope-cut memo
from an AI-infra team would be a useful style reference for
the memo shape above. No verifiable candidate was identified
at the time of writing. Contributors should cite one only if
it can be attributed to a named author and organization;
invented examples are not acceptable.
