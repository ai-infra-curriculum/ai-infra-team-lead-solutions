# SOLUTION — Exercise 05: Roadmap Defense Presentation

> Read this *after* you have attempted the exercise. The worked
> presentation below defends the roadmap produced in
> [exercise-04](../exercise-04/SOLUTION.md). Content references
> the synthetic Fleet-Serving team; treat it as **local
> exercise context**, not a real company plan. Substitute your
> own roadmap when you apply the rubric.

## 1. Solution overview

### What this exercise is really testing

The exercise asks you to defend the roadmap you built in
[exercise-04](../exercise-04/SOLUTION.md) to a peer — another
team lead at the same level, not your manager. The grading bar
is **concreteness and defensibility under pressure**, not
comprehensiveness. A presentation that walks every section of
the roadmap at the same altitude scores mid-rubric; a
presentation that spends most of its time on the two or three
decisions the peer is likely to push on, with concrete answers,
scores at the top.

The module README's framing is clear: "the ask is to be
concrete and defensible, not comprehensive." A peer-defense
presentation is not a roadmap read-out. It is the compressed
form of the roadmap plus the answers to the questions another
lead would ask.

### The three questions a peer will ask

Peer team leads are not sponsors. They are not looking for
inspiration; they are looking for the weak points. In practice,
they will ask three things:

1. **Where are you overcommitted?** A roadmap that sums to
   nominal capacity triggers this question first.
2. **What are you betting on that could collapse?** The
   medium-confidence goals and their trigger conditions.
3. **What did you cut, and who is unhappy about it?** The
   non-goals section and the stakeholder posture around it.

A defense that answers these three unprompted, in that order,
with specific numbers, is a defense that scores well. A
defense that evades any of them scores poorly.

## 2. Worked answer or implementation

### Slide-by-slide script (10-12 slides, ~15 minutes)

Each slide is one idea. The speaker notes carry the argument;
the slide itself is minimal.

---

**Slide 1 — Title.**

"Fleet-Serving Q3 roadmap defense." Team lead name. Date.
Peer-review context. One sentence framing: "I am going to
spend most of this on the three commitments I am least
confident in and the ones I cut. Push hard on all of them."

The opening explicitly invites pushback. This changes the
conversation from read-out to review.

---

**Slide 2 — Capacity reality.**

One bar chart. Nominal 91 engineer-weeks, discounted to
~65 engineer-weeks after on-call (−5.2), onboarding (−2.6),
and interrupt tax (−18.2). Reference-class: last three
quarters averaged 63 delivered.

Speaker note: "We are planning to 65. Everything after this
slide is sized against that number, not against 91. If you
hear a goal estimate that only works at 91, interrupt me."

This slide pre-empts the first peer question.

---

**Slide 3 — Four committed goals, one line each.**

G1 Gateway v2, G2 Hot-path p99, G3 Training-pipeline
migration (3 pipelines), G4 Fleet cost commitment. Each with
one-line measurable target.

Speaker note: Walk each in ten seconds. Do not dwell.
This slide is orientation, not argument.

---

**Slide 4 — Confidence levels and why.**

Table: G1 High (≥ 80 %), G2 Medium (~55 %), G3 High (~80 %),
G4 Medium (~60 %). Each with one-line rationale and a
reference-class anchor.

Speaker note: "G2 is the one most likely to miss. G4 is the
one most likely to surprise. Here is why for each."

This slide is where peers usually dig in; be ready to defend
every probability.

---

**Slide 5 — The G2 bet.**

The one medium-confidence goal that could collapse. What we
know, what we don't, what the week-7 decision gate looks
like, what we do if the gate fails.

Speaker note: "If G2 kernel profiling at week 5 looks worse
than our reference class, we announce a de-scope at week 7,
not at week 12. Here is the specific signal and the specific
decision."

This slide pre-empts the second peer question.

---

**Slide 6 — The G4 bet.**

The cost commitment. Why this is treated as a first-class
goal and not an aside. The measurement methodology, the
baseline, the trigger if tenant mix shifts.

Speaker note: Finance partner is in the room on the methodology
(see [exercise-03](../exercise-03/SOLUTION.md)); mid-quarter
check is week 7.

---

**Slide 7 — Dependencies both directions.**

Short graph. Upstream: auth team (G1), framework team (G2),
hardware/infra (G3). Downstream: AI Engineering (G1), ML
Engineering (G3), Startup/Finance (G4), Governance
(ongoing).

Speaker note: "Each has a named owner on the other side and
a specific slip-trigger. Any of them going red triggers an
off-cadence replan, not a wait for monthly review."

---

**Slide 8 — What we cut.**

The non-goals section. Specifically: the gateway v3 scoping
(deferred), the AI Workforce pricing dashboard (deferred),
the research team's experimental model hosting (deferred),
framework N+2 (deferred). For each: who asked, who is
unhappy, and the memo that went to them.

Speaker note: Pointer to [exercise-02](../exercise-02/SOLUTION.md)
for the memo shape.

This slide pre-empts the third peer question.

---

**Slide 9 — Risks that drive weekly action.**

Five risks (see [exercise-04](../exercise-04/SOLUTION.md) §5).
Each with a signal and an owner. No risk register prose.

Speaker note: "These are the five things I will look at
every week. Anything that lands in week 1 as a risk and is
not on this list, I missed. Please flag."

---

**Slide 10 — Replanning protocol.**

Weekly sprint review; monthly roadmap review (weeks 4, 8, 12);
mid-quarter decision gate (week 7); off-cadence trigger for
any confidence-level change between reviews.

Speaker note: "The commitment here is not 'the plan is right.'
The commitment is that when the plan goes wrong, you will hear
about it inside two weeks."

---

**Slide 11 — AI-infra specifics.**

One slide. Capacity-planning companion is a separate artifact.
Cost is on the roadmap. AI-security risk flagged against
[MITRE ATLAS](https://atlas.mitre.org/) where applicable.
Governance view maps to NIST AI RMF GOVERN/MAP.

Speaker note: "If any of these feel light to you, that is
where I want to spend the Q&A."

---

**Slide 12 — Asks.**

What you want from the peer reviewer. Specifically:

1. Pressure-test the G2 confidence number.
2. Flag any stakeholder on my map (see
   [exercise-03](../exercise-03/SOLUTION.md)) you think is
   missing or mis-prioritized.
3. Tell me where the capacity math is wrong.

Speaker note: "If you leave this review without saying one
of those three things, we both wasted our time."

---

### Why this presentation works

- **Opens by inviting pushback.** Changes the conversation
  shape from read-out to review.
- **Spends ~60 % of the time on the weak commitments and the
  cuts**, which is where peer review adds signal.
- **Every probability has a reference-class anchor.** Peers
  cannot dismiss a probability if it is tied to the team's
  own past delivery.
- **Every dependency has a named owner on both sides.** The
  classic peer-review gotcha ("who on their side actually
  committed to this?") is pre-answered.
- **Ends with a specific ask.** Peer-review conversations
  without an ask drift to generalities.
- **AI-infra-specific risks are on their own slide**, so the
  peer can engage with them at the altitude they belong at,
  not as footnotes to delivery goals.

### Mapping to the three peer questions

| Peer question | Slide that answers it | What the answer contains |
|---|---|---|
| Where are you overcommitted? | 2 | Nominal vs. honest capacity, reference-class. |
| What are you betting on that could collapse? | 5, 6 | G2 and G4 bets, decision gates, counterfactuals. |
| What did you cut, and who is unhappy? | 8 | Non-goals, requester, posture, memo pointer. |

A presentation that lands all three pre-emptively earns the
peer's engagement on the remaining content. A presentation
that forces the peer to ask these as questions in the Q&A
burns time that should have been spent on second-order
feedback.

## 3. Validation steps

1. **Three-question test.** Does your presentation
   pre-emptively answer each of the three peer questions?
   For each, can you point to the specific slide?
2. **Reference-class test.** Does every probability in your
   confidence section cite a reference-class anchor? No
   anchor, no probability.
3. **Dry-run test.** Can you deliver the whole thing in
   ≤ 15 minutes with ≥ 10 minutes of Q&A budget? Peer-review
   presentations that eat Q&A time are failing the exercise.
4. **Non-goals test.** Does one of your slides show what you
   cut, with named requesters? If the cuts are missing, you
   are not defending a real roadmap.
5. **Ask test.** Does your last slide contain at least three
   specific asks the reviewer can act on? "Thoughts?" is not
   an ask.
6. **Minimalism test.** Is each slide one idea? Slides that
   carry the speaker's full argument in bullets replace the
   speaker, which turns the review into a read.
7. **Objection test.** For each probability you quote, do you
   have one sentence of defense when the peer says "I don't
   believe that number"? If not, the number is at risk.
8. **AI-infra test.** Does a dedicated slide cover the
   AI-infra specifics (capacity-planning companion, cost
   commitment, AI-security / governance mapping)? For an
   AI-infra team roadmap this is not optional.

## 4. Rubric or review checklist

| Dimension | L1-L2 | L3 | L4-L5 |
|---|---|---|---|
| **Pre-emption of peer questions** | ≤ 1 of 3 covered. | All 3 covered. | All 3 covered, in the first half of the deck, with concrete numbers. |
| **Confidence defense** | Probabilities quoted without anchors. | Each probability has a reference-class anchor. | Anchors are from the same team's past quarters; the peer can test them. |
| **Dependency clarity** | One-way dependencies. | Two-way with owners. | Two-way, with named escalation triggers, visible on-slide. |
| **Non-goals + cuts** | Missing or glossed. | Shown, with requesters. | Shown, with requesters, posture, and pointer to the memo artifact. |
| **Replanning protocol** | Not shown. | Shown. | Shown, with the off-cadence trigger defined. |
| **AI-infra specifics** | Generic. | Mentioned on at least one slide. | Dedicated slide covering capacity-planning separation, cost as first-class, and AI-security/governance mapping to public standards. |
| **Asks** | None or vague. | Three specific asks at the end. | Three asks, each with a stated form of answer the peer can give. |
| **Time discipline** | Over 15 minutes. | ≤ 15 minutes. | ≤ 15 minutes with the strongest material in the first 7. |

**Caps.** A presentation that treats peer review as a read-out
caps at L3. A presentation with no non-goals slide caps at L2.
A presentation that quotes probabilities without anchors
anywhere caps at L2.

## 5. Common mistakes

- **Reading the roadmap document aloud.** The peer has seen
  it (or can). Use the presentation for argument, not
  recitation.
- **Spending equal time on every goal.** The high-confidence
  goals need the least attention; the medium-confidence ones
  need the most.
- **Hiding the cuts.** A presentation that does not name the
  non-goals signals to the peer that you are afraid of them.
- **No pre-emptive ownership of the weakest probability.**
  If the peer has to pull the weakest number out of you, you
  are already on the defensive.
- **Overlong decks.** 20+ slides for a 15-minute slot is a
  sign that no slide is doing a full slide's worth of work.
- **Dense slides.** Bullet lists that carry the speaker's
  full argument make the speaker redundant.
- **No ask slide.** The review ends in generalities instead
  of actionable feedback.
- **Missing the AI-infra axis.** For an AI-infra team, the
  capacity-planning view, cost commitment, and governance /
  AI-security angle are not optional slides.
- **Treating the peer as an adversary.** The peer is trying
  to help; adversarial framing wastes the review.

## 6. References

- **Local exercise context — module SOLUTION.** Parent
  [`SOLUTION.md`](../SOLUTION.md#the-roadmap-review-exercise-05)
  on the roadmap-review ritual and its common failure modes
  (status theater, defensiveness about slips, no ask).
- **Local exercise context — learning module README.**
  [`lessons/mod-703-project-roadmap/README.md`](https://github.com/ai-infra-curriculum/ai-infra-team-lead-learning/blob/main/lessons/mod-703-project-roadmap/README.md)
  — "concrete and defensible, not comprehensive" as the
  explicit framing for this exercise.
- **Local exercise context — sibling solutions.**
  [`exercise-02/SOLUTION.md`](../exercise-02/SOLUTION.md)
  for the cut-memo shape referenced on slide 8;
  [`exercise-03/SOLUTION.md`](../exercise-03/SOLUTION.md)
  for the stakeholder map behind slide 7;
  [`exercise-04/SOLUTION.md`](../exercise-04/SOLUTION.md)
  for the source-of-truth roadmap the deck defends.
- **NIST AI Risk Management Framework** —
  <https://www.nist.gov/itl/ai-risk-management-framework>.
  The GOVERN/MAP functions are the public-standard framing
  for slide 11's governance mapping; cite them explicitly if
  a Governance peer is in the review.
- **MITRE ATLAS** — <https://atlas.mitre.org/>. Cite by
  tactic ID on slide 11 if an AI-security risk on the
  roadmap maps to a listed adversarial-AI tactic.
- **OWASP Machine Learning Security Top 10** —
  <https://owasp.org/www-project-machine-learning-security-top-10/>.
  Use for slide 11 only if a roadmap commitment corresponds
  to defending against a listed ML-security risk; cite the
  specific risk ID.

### Known research gap

A public, attested example of a peer-reviewed AI-infra team
roadmap defense deck would be a useful comparison artifact
for the eleven-slide outline above. No verifiable candidate
was identified at the time of writing. Contributors should
add one only if it can be cited with attribution; fabricated
decks are not acceptable.
