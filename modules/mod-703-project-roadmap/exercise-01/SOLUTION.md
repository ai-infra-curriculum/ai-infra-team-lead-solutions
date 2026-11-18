# SOLUTION — Exercise 01: Roadmap Case Study

> Read this *after* you have attempted the exercise. The worked
> example below uses a synthetic AI-infra team ("Fleet-Serving")
> as a vehicle for the diagnosis. Treat the scenario as **local
> exercise context** — it is deliberately not a public company or
> incident, because the module's source policy forbids inventing
> real cases. Substitute your own real or case-study team when
> you apply the rubric.

## 1. Solution overview

### What this exercise is really testing

The exercise asks you to walk into a team mid-quarter and
diagnose what is wrong with its current roadmap. The grading bar
is **diagnosis quality, not fix quality**. A learner who proposes
a flashy reset without first naming the structural failures
scores at the lower end of the rubric. A learner who correctly
names "padded estimates on three items, no non-goals section,
one silent dependency slip" scores at the top, even if their
proposed reset is modest.

The module's own argument (see the parent
[`SOLUTION.md`](../SOLUTION.md#what-this-module-is-really-teaching))
is that a roadmap is a **negotiated commitment** — a
communication artifact, not a schedule. The five failure modes
the diagnosis has to look for are the inversion of that
argument:

1. Estimates presented without confidence levels.
2. A plan that pretends team capacity is a single number.
3. An artifact that is tracked internally but never surfaces to
   the dependent orgs in a form they can act on.
4. No replanning cadence, so reality drifts away from the
   document.
5. No explicit list of what the team is **not** doing.

Your diagnosis should walk each of those lenses and state, for
each one, "present" / "partial" / "absent," with a one-line
piece of evidence for the call.

### Why this is harder than it looks

The surface of a bad roadmap usually looks fine. The commitments
read as reasonable, the slide deck is tidy, the team is "mostly
on track" according to the weekly status email. The failure mode
is almost never bad engineering — it is a roadmap the team
quietly knew was unachievable and did not renegotiate in time
(see the learning-repo
[module README](https://github.com/ai-infra-curriculum/ai-infra-team-lead-learning/blob/main/lessons/mod-703-project-roadmap/README.md)).
A diagnosis that stops at "the deck is clean" is not a
diagnosis.

## 2. Worked answer or implementation

### Scenario (synthetic, labeled as such)

**Team:** Fleet-Serving (illustrative). 7 engineers, 1 team lead,
owns the shared inference serving stack for mid-size models in
a mid-size AI-infra org. Q3 roadmap committed 11 weeks ago.
You arrive in week 6 of a 13-week quarter.

**Published Q3 roadmap** (synthesized for this walkthrough —
treat as the artifact under diagnosis, not a real company's
plan):

| # | Goal | Owner | Target | Confidence stated |
|---|------|-------|--------|-------------------|
| 1 | Launch gateway v2 with per-tenant quotas | Alice + Bob | wk 10 | — |
| 2 | Cut p99 on the hot inference path | Carol | wk 8 | — |
| 3 | Migrate three training pipelines to the new cluster | Dan + Eve | wk 12 | — |
| 4 | Finish the audit-log schema overhaul | Frank | wk 11 | — |
| 5 | On-call reliability upgrades | Grace + rotation | ongoing | — |
| 6 | "Stretch: BYOK for two more customers" | TBD | wk 13 | — |

**Current state at week 6:** items 1, 3, and 4 are green on the
status page. Item 2 is yellow ("investigating"). Item 5 is
untracked. Alice has been on-call three of the last six weeks.
Frank joined the team in week 2. The audit-log item has a
dependency on the Governance org that has not been confirmed.

### Diagnosis

Walk the five lenses from §1 against this artifact.

**Lens 1 — estimates and confidence.** All six items are
presented as deadlines, not probabilistic commitments. No
best/expected/worst framing, no confidence percentage.
*Verdict: absent.* **Evidence:** the "Confidence stated"
column is empty. Even where the lead has an internal sense
("item 2 is risky"), it does not reach the artifact; it only
reaches the status page as a late-signal yellow.

**Lens 2 — honest capacity.** The plan assumes a 7-engineer
team at nominal throughput. In reality:

- Frank joined in week 2, so his first 60-90 days are at
  significantly reduced effective capacity (per the module's
  estimation framing — see parent
  [`SOLUTION.md`](../SOLUTION.md#estimation-discipline-exercise-03)).
- Alice carries three weeks of on-call across a six-week window,
  consuming roughly a fifth of her available time.
- Item 5 ("on-call reliability upgrades") is listed as a goal
  *and also consumes the capacity that should be funding the
  other goals*. Double-counting.

*Verdict: absent.* **Evidence:** the plan sums as if the team
has ~280 person-weeks in the quarter; a capacity-honest sum is
closer to ~175 after on-call, onboarding, and interrupt tax
(see the module's estimation framing). The gap is where the
silent overcommitment hides.

**Lens 3 — communication layer.** The roadmap is published as
a slide shared once at the start of the quarter. No adjacent-
team review. The Governance dependency on item 4 was not
confirmed because no one from Governance was in the
publication loop.

*Verdict: partial.* **Evidence:** the artifact exists and is
shared upward, but it does not reach the sibling orgs whose
teams are chained on it. The dependency slip on item 4 will
surface as a surprise in week 9 or 10 — too late to replan
without a scramble.

**Lens 4 — replanning cadence.** No explicit cadence. The
status email ("mostly on track") is doing the work that a
monthly roadmap review should be doing.

*Verdict: absent.* **Evidence:** six weeks in, no formal
revision to the published roadmap even though item 2 has been
yellow and item 5 is untracked.

**Lens 5 — explicit non-goals.** No "what we are not doing this
quarter" section. Two other sibling teams have raised asks in
weeks 3 and 5 under the assumption that they can be
accommodated.

*Verdict: absent.* **Evidence:** the artifact is silent on
non-goals; adjacent teams are interpreting silence as
availability.

### Proposed reset (bounded)

A good reset at week 6 is **small and surgical**, not a full
replan. The team has already spent five weeks of calendar time;
burning a sixth on a full rebuild is its own mistake. The
specific reset:

1. **Add confidence levels to the surviving commitments this
   week.** Alice/Bob (item 1) gets "high"; Carol (item 2) gets
   "low, decision needed by week 8"; Dan/Eve (item 3) stays
   "high"; Frank (item 4) drops to "low, dependency unconfirmed";
   on-call upgrades (item 5) stay "ongoing, best effort."
2. **Cut the stretch (item 6) publicly.** A stretch on a roadmap
   that is already carrying hidden overcommitment is noise.
   Announce the cut; adjacent teams can replan.
3. **Open the Governance dependency on item 4 this week.** If
   it cannot be confirmed by week 8, item 4 slips to Q4. State
   that trigger publicly.
4. **Schedule a mid-quarter review for week 8.** Decision gate
   for items 2 and 4.
5. **Publish an explicit non-goals section this week.** The two
   late asks are the first two items on it.

Note what is *not* in the reset: no re-estimation of items 1
and 3 that are already green, no reorganization of owners, no
"hero push" plan to try to save item 2. The module's framing
(parent [`SOLUTION.md`](../SOLUTION.md#common-mistakes-graders-see))
explicitly warns against hero-dependent recovery plans; the
reset above produces honest signal, which is the point.

## 3. Validation steps

To check that your diagnosis holds up, run the following
against your own case study (real or synthetic):

1. **Can an outside reader, reading only your diagnosis and the
   roadmap artifact, reach the same verdict on each of the five
   lenses?** If the verdicts depend on tacit context the reader
   does not have, the diagnosis is under-evidenced.
2. **For every "absent" verdict, is there a specific piece of
   evidence cited?** "No non-goals section" is evidence. "The
   plan feels overcommitted" is not.
3. **Does the proposed reset avoid the three anti-patterns
   named in the parent
   [`SOLUTION.md`](../SOLUTION.md#common-mistakes-graders-see)
   — hero-dependent estimates, replanning by extension, and
   generic goal restatements?**
4. **Is the reset sized to the time remaining?** A week-6 reset
   that needs three weeks of planning is not a reset. Week-11
   resets are different from week-3 resets; your diagnosis
   should name where in the quarter you are.
5. **For AI-infra teams specifically, does the diagnosis
   account for capacity-planning cadence being separate from
   delivery cadence** (training vs. inference capacity, GPU
   supply, framework upgrade cycles)? If your team's roadmap
   mixes these on one artifact, the diagnosis should flag it.
   This is the AI-infra specialization the module's README
   calls out.

## 4. Rubric or review checklist

A reviewer scores a submission on five dimensions, each 1-5:

| Dimension | L1-L2 | L3 | L4-L5 |
|---|---|---|---|
| **Diagnosis coverage** | Names 0-1 of the five lenses. | Names all five, with a verdict per lens. | Names all five, with specific evidence citations for each verdict, and identifies at least one lens-specific AI-infra wrinkle. |
| **Evidence quality** | "The plan feels wrong." | Each absent verdict has at least one concrete evidence item. | Evidence items are from the artifact itself (dates, confidence columns, owner lists, dependency graph) rather than from tacit team knowledge. |
| **Reset proportionality** | Proposes a full rebuild, or no reset at all. | Proposes a reset sized to the calendar time remaining. | Reset avoids all three anti-patterns (hero plans, extension, restatement) and names a specific decision gate with a date. |
| **Stakeholder awareness** | Only the team is named. | Names leadership, the team, and one adjacent team. | Explicitly names the upward, sideways, inward, and customer audiences, and what each needs from the reset. |
| **AI-infra specificity** | Generic project-management diagnosis. | Mentions at least one AI-infra factor (GPU supply, model-family mix, training-vs-serving split). | Diagnosis correctly separates capacity-planning cadence from delivery cadence, and flags where the roadmap conflates them. |

**Caps.** A submission that treats the roadmap as a schedule
rather than a communication artifact caps at L2 regardless of
other dimensions. A submission that proposes a hero-dependent
reset caps at L3.

## 5. Common mistakes

- **Treating "mostly on track" status emails as evidence of
  health.** They are usually the opposite — status theater that
  defers the honest conversation to the week-11 miss.
- **Proposing a full rebuild at week 6 or later.** The calendar
  time is already spent; the reset should be surgical.
- **Diagnosing only the artifact, not the process that
  produced it.** A roadmap with no confidence levels is a
  symptom; the cause is usually an estimation ritual that does
  not produce them.
- **Overweighting "the deck is tidy."** The deck is the easy
  part. The missing parts — confidence, non-goals, dependency
  confirmations — are the ones that matter.
- **Assuming the team lead can unilaterally cut items.**
  Especially cuts that affect adjacent orgs. The cut has to be
  run through the stakeholder map (see
  [exercise-03](../exercise-03/SOLUTION.md)) or it burns trust
  instead of building it.
- **Writing the diagnosis as a scorecard without a reset
  proposal, or a reset proposal without a diagnosis.** Both
  halves are required.
- **Treating on-call reliability work as free capacity.** It is
  team-member time; if it is on the roadmap as a goal and also
  being consumed as overhead, something is double-counted.

## 6. References

- **Local exercise context — module SOLUTION.** The parent
  [`modules/mod-703-project-roadmap/SOLUTION.md`](../SOLUTION.md)
  is the canonical framing of the five lenses used in the
  diagnosis above. Specifically:
  [What this module is really teaching](../SOLUTION.md#what-this-module-is-really-teaching),
  [Estimation discipline](../SOLUTION.md#estimation-discipline-exercise-03),
  and [Common mistakes graders see](../SOLUTION.md#common-mistakes-graders-see).
- **Local exercise context — learning module README.**
  [`lessons/mod-703-project-roadmap/README.md`](https://github.com/ai-infra-curriculum/ai-infra-team-lead-learning/blob/main/lessons/mod-703-project-roadmap/README.md)
  carries the AI-infra specialization, in particular the
  argument that capacity planning is a separate ritual from
  delivery planning.
- **NIST AI Risk Management Framework** —
  <https://www.nist.gov/itl/ai-risk-management-framework>.
  The RMF's MAP function ("categorize the context and
  identify risks") is the official-standard analogue of the
  diagnosis step: before you can decide how to respond, you
  have to inventory where risk is actually sitting. Use it
  when the case study's slipping items carry AI-risk
  implications (model-behavior changes, serving-SLA breaches,
  governance-evidence gaps).

### Known research gap

A documented public case study of an AI-infra team roadmap
reset at the mid-quarter mark would strengthen the diagnosis
and reset-plan pattern above. No verifiable candidate was
identified at the time of writing; graders and contributors
should add one only if it can be cited with attribution.
Fabricated case studies are not acceptable here.
