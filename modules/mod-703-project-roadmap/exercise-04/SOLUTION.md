# SOLUTION — Exercise 04: The Roadmap

> Read this *after* you have attempted the exercise. The worked
> roadmap below is for the synthetic Fleet-Serving team used in
> earlier exercises. Treat all dates, names, and estimates as
> **local exercise context**, not as a real plan. Substitute
> your own team's concrete numbers when you apply the rubric.

## 1. Solution overview

### What this exercise is really testing

The exercise asks you to produce the roadmap artifact itself —
not a diagnosis or a memo, but the one-page document a team
actually publishes. The grading bar is **completeness on seven
specific sections**, with calibrated confidence levels and an
explicit non-goals section. The parent
[`SOLUTION.md`](../SOLUTION.md#the-roadmap-exercise-02-the-artifact-itself)
names the seven sections; this exercise is where they land in
one artifact and are grading-pressure-tested.

The seven required sections, from the parent framing:

1. Goals (3-5), stated as outcomes with measurable targets.
2. Confidence per goal (high / medium / low).
3. Major work streams with rough timing.
4. Dependencies, in both directions.
5. Risks.
6. Stretch goals.
7. What we are **not** doing this quarter.

### The two "load-bearing but usually missing" sections

Sections 2 (confidence levels) and 7 (non-goals) are the ones
the module argues decide whether the roadmap is honest. A
roadmap without confidence levels is a wish list; a roadmap
without non-goals is a surface every adjacent team paints their
own ask onto.

The AI-infra specialization adds a few load-bearing additions:
cost commitments are first-class alongside delivery
commitments, the mid-quarter replanning moment is named
explicitly, and the capacity-planning view is kept separate
from the delivery view (two artifacts, same source of truth).

## 2. Worked answer or implementation

### Q3 roadmap — Fleet-Serving (worked example, synthetic)

**Team.** Fleet-Serving, 7 engineers + 1 team lead. Owns the
shared inference serving stack for mid-size models.
**Quarter.** Q3 (synthetic, 13-week quarter).
**Last updated.** Week 0 of Q3. **Next scheduled update.**
Mid-quarter review, Q3 week 7. **Standing replanning
cadence.** Weekly sprint review; monthly roadmap review (weeks
4, 8, 12); mid-quarter decision gate (week 7).

---

**Capacity for the quarter.**

- Nominal: 7 engineers × 13 weeks ≈ 91 engineer-weeks.
- On-call tax (20 % of 2 engineers on rotation): −5.2.
- Onboarding (1 engineer at 60 % effective capacity for 10 weeks): −2.6.
- Interrupt tax (20 % team-wide): −18.2.
- **Honest available capacity: ≈ 65 engineer-weeks.**

The reference-class anchor is the last three quarters, during
which this team's actual delivered scope averaged 63 engineer-
weeks. This quarter's plan is sized to 65, not to 91.

---

**1. Goals (4).** Each is an outcome with a measurable target.

- **G1 — Gateway v2 with per-tenant quotas.**
  Target: 100 % of gateway traffic routed through v2 with
  per-tenant quota enforcement at ≥ 99.9 % accuracy, measured
  by a 7-day shadow comparison.
  Timing: ship ready for GA week 10; GA cutover week 11.
  Owners: Alice (lead), Bob.
- **G2 — Hot-path p99 reduction.**
  Target: p99 latency on the hot inference path from 240 ms
  to ≤ 180 ms at the committed 10k-QPS line.
  Timing: decision gate at week 7 (keep or cut), land week 10.
  Owner: Carol.
- **G3 — Training-pipeline migration (3 pipelines).**
  Target: three named training pipelines cut over to the new
  cluster with regression ≤ 5 % on run time and zero
  correctness regressions, verified by a side-by-side run.
  Timing: pipeline 1 week 6, pipeline 2 week 9, pipeline 3
  week 12.
  Owners: Dan (lead), Eve.
- **G4 — Fleet cost commitment.**
  Target: per-request cost at or below the Q2 baseline × 0.90
  by end of quarter, measured on the tenant-weighted traffic
  mix.
  Timing: mid-quarter checkpoint week 7; final measurement
  week 13.
  Owners: Alice + Carol (joint, with Finance partner on the
  measurement methodology).

---

**2. Confidence per goal.**

| Goal | Confidence | Rationale (ref-class + risk) |
|---|---|---|
| G1 Gateway v2 | **High (≥ 80 %)** | Alice shipped v1 in 9 weeks last year; v2 scope smaller. Dependency on the auth team confirmed. |
| G2 Hot-path p99 | **Medium (≈ 55 %)** | Unknown unknowns in the kernel-side profile. If week-7 gate fails, we ship the gains we have and defer the rest. |
| G3 Training-pipeline migration | **High (≈ 80 %)** | Three pipelines sized against the previous two migrations (6 and 7 weeks each). Cluster readiness confirmed. |
| G4 Fleet cost commitment | **Medium (≈ 60 %)** | Modeled on the Q2 trajectory and two confirmed optimizations. Risk: tenant mix shifts during the quarter. |

Confidence here is a calibrated best guess, not a wish. A goal
that would be below 30 % confidence is a goal that should not
be on the committed list; it goes to the stretch section
([§6](#6-stretch-goals)) or is dropped entirely.

---

**3. Major work streams with rough timing.**

Compact Gantt-ish view, in weeks:

```
Week:                  1  2  3  4  5  6  7  8  9 10 11 12 13
G1 Gateway v2          [-------- design --------][--- impl ---][GA]
G2 Hot-path p99        [--- profiling ---][gate][--- opt ---][land]
G3 Pipeline migration  [P1-----][        ][P2-------][       ][P3---]
G4 Cost commitment     [---- modeling + opts ----][chk][----- measure -----]
Capacity ritual        [---- monthly fleet-planning review ----]
```

Owners by week are tracked in the team wiki (link omitted in
this synthetic example); the public roadmap carries the stream
view, not the individual week-by-week assignments.

---

**4. Dependencies (both directions).**

- **G1 ← Auth team** (upstream): per-tenant identity service
  v2 contract confirmed, delivery week 5. Trigger if slips:
  G1 GA pushes two weeks.
- **G1 → AI Engineering** (downstream): AI Eng's product
  launch in Q4 is planned against G1 GA week 11. Interface
  contract shared week 4; rollback plan at week 9.
- **G2 ← Framework team** (upstream): kernel upgrade in
  framework N+1 planned for week 3. Trigger if slips: G2
  confidence drops to Low.
- **G3 ← Hardware/infra** (upstream): new-cluster capacity
  confirmed for weeks 5-12. Trigger if slips: G3 scope
  reduces to two pipelines.
- **G3 → ML Engineering** (downstream): ML Eng waiting on
  pipeline 3 cutover before their Q4 run. Communicated
  week 2; weekly sync starting week 8.
- **G4 ← Finance / Workforce** (upstream + review):
  methodology sign-off by week 2; measurement review at the
  monthly fleet-planning meeting.
- **G4 → Startup/Finance** (downstream): per-request cost
  trajectory is already in the board-level narrative.
  Monthly 1-pager per the [stakeholder map](../exercise-03/SOLUTION.md).

Each dependency has a named owner on the other side and a
trigger that escalates if it slips.

---

**5. Risks.**

A short, honest list (five entries):

- **R1 — G2 kernel profile deeper than expected.** Likelihood:
  medium. Impact: cuts G2 or pushes landing to Q4. Watch
  signal: week-5 profiling results. Owner: Carol + team lead.
- **R2 — On-call load spikes from an incident pattern not yet
  understood.** Likelihood: medium. Impact: 10-20 % capacity
  erosion across the quarter. Watch signal: weekly on-call
  retro. Owner: Grace + team lead.
- **R3 — Frank's ramp slower than modeled.** Likelihood: low.
  Impact: reduces G3 pipeline 3 confidence from high to
  medium. Watch signal: biweekly 1:1 + first pipeline
  landing. Owner: team lead.
- **R4 — Tenant mix shift away from the Q2 baseline.**
  Likelihood: low-medium. Impact: G4 target becomes
  non-comparable. Watch signal: monthly traffic mix review.
  Owner: Alice + Finance partner.
- **R5 — AI-security pressure from an external finding that
  requires a serving-side mitigation.** Likelihood: low.
  Impact: unplanned-but-expected work consuming the 20-30 %
  headroom. Watch signal: Governance partner channel +
  public AI-security advisories (see
  [MITRE ATLAS](https://atlas.mitre.org/)).
  Owner: team lead + Governance partner.

The list is bounded to five. The module's framing explicitly
warns against risk registers so long nothing on them drives
weekly action. Five is the number that keeps attention.

---

**6. Stretch goals.**

- **S1 — BYOK for two additional named tenants.**
  Target: BYOK coverage extended to two named tenants.
  Trigger to start: G1 reaches GA by week 11 **and** one of
  the medium-confidence goals (G2 or G4) has already landed
  by week 11. Otherwise, S1 does not start in Q3.
- **S2 — Observability upgrade on the serving pipeline.**
  Target: new structured-logging schema in place with
  dashboards. Trigger: capacity frees up from G2 by week 9.

Stretch goals are honest about their trigger conditions. If
the trigger does not fire, they are not debt that rolls
automatically to Q4 — they are revisited in Q4 planning.

---

**7. What we are NOT doing this quarter.**

- Not taking on the "gateway v3 architecture" scoping. Q4
  planning item.
- Not building a new per-tenant pricing dashboard requested
  by AI Workforce; the interim CSV export remains.
- Not expanding BYOK beyond the two named tenants in S1, and
  not starting S1 until the gate conditions fire.
- Not accepting the mid-quarter request from the research
  team to host an experimental model-family variant on the
  current serving stack; routed to Q4 planning.
- Not tackling framework N+2 migration (framework N+1 only).

This section is the most load-bearing part of the roadmap.
Every adjacent team reads it and knows what not to expect
from Fleet-Serving this quarter. Without it, every adjacent
team assumes their ask is on the list.

---

### Companion artifact — capacity-planning view

The AI-infra specialization (module README) calls out that
capacity planning needs a **separate** ritual and artifact. A
short capacity-planning view sits alongside the roadmap:

- Current fleet composition and utilization at Q3 start.
- Forecasted demand curve for Q3 and Q4.
- Hardware delivery schedule (confirmed with procurement).
- Training-vs-inference capacity split and the trigger to
  rebalance.
- Mid-quarter decision gate for ordering ahead of Q4.

Updated at the monthly fleet-planning meeting, not at sprint
review. Linked from the roadmap, not inlined into it.

### Mid-quarter replanning protocol (named explicitly)

- **Cadence.** Weekly sprint review; monthly roadmap review
  (weeks 4, 8, 12); dedicated mid-quarter decision gate at
  week 7.
- **Off-cadence trigger.** Any goal moving from high to low
  confidence between formal reviews triggers an immediate
  update, not a wait for the next review.
- **Decision rights.** Scope changes inside a quarter: team
  lead decides, with manager sign-off for anything crossing a
  committed interface. Date pushes crossing a quarter
  boundary: team lead + manager + affected stakeholder lead.
- **Communication.** Any replan is published in the same
  artifact (the roadmap document), with the previous version
  archived; adjacent teams are notified within 48 hours.

## 3. Validation steps

1. **Seven-section test.** Does your roadmap have all seven
   sections, in the order listed in the parent
   [`SOLUTION.md`](../SOLUTION.md#the-roadmap-exercise-02-the-artifact-itself)?
   Missing any one caps your score.
2. **Outcome-statement test.** For each goal, is the measured
   target phrased so a non-owner could verify it? "Work on
   perf" fails; "p99 ≤ 180 ms at 10k QPS" passes.
3. **Confidence-calibration test.** Are your "high" / "medium"
   / "low" labels anchored to a rough probability (≥ 80 %,
   50-70 %, 30-50 %)? Labels without anchors drift to mean
   whatever the reader wants.
4. **Capacity-honesty test.** Does the sum of committed work
   fit inside a capacity number that discounts on-call,
   onboarding, and interrupt tax? If the sum equals nominal
   capacity, you are overcommitted.
5. **Dependency-bidirectional test.** For every dependency,
   are both the upstream owner and the downstream consumer
   named? Single-direction dependencies are where surprises
   originate.
6. **Trigger test.** For every risk, is there a named watch
   signal and an owner? Risks without signals are not risks,
   they are worries.
7. **Non-goals test.** Does the "what we are NOT doing"
   section include at least one item that an adjacent team
   has asked for? If every item on the non-goals list is
   something no one wanted, the section is not doing its
   job.
8. **Mid-quarter-gate test.** Is there a named decision date
   for each medium-confidence goal? Medium-confidence goals
   without a gate drift to the end of the quarter where
   recovery is impossible.
9. **AI-infra separation test.** Is the capacity-planning
   view separate from the delivery roadmap, linked but not
   merged? Merging the two is the common failure mode.
10. **One-page test.** Does the committed roadmap view fit on
    one page? Views for different audiences differ (see
    [exercise-03](../exercise-03/SOLUTION.md)), but the
    canonical one-page view should exist.

## 4. Rubric or review checklist

| Dimension | L1-L2 | L3 | L4-L5 |
|---|---|---|---|
| **Section completeness** | ≤ 4 of 7 sections present. | All 7 sections present. | All 7 sections present + explicit mid-quarter protocol + capacity-planning companion. |
| **Outcome goals** | Goals phrased as activities. | Each goal is an outcome with a measurable target. | Targets include method of measurement and the data source, not just a number. |
| **Confidence calibration** | Labels present, not anchored. | Labels anchored to rough probabilities. | Labels anchored and justified by a reference-class anchor to past team data. |
| **Capacity honesty** | Nominal capacity used. | On-call, onboarding, and interrupts discounted. | Discounts justified with recent-quarter data, and sum committed ≤ honest capacity. |
| **Dependencies** | Listed one-way. | Bidirectional, with owners. | Bidirectional, with owners, timing, and a named escalation trigger for each. |
| **Risks** | Long generic list. | 3-5 named risks with signals and owners. | Risks tied to watch signals already in the team's weekly ritual (not new ceremonies invented for the roadmap). |
| **Non-goals** | None. | Present, with 3+ items. | Present, with items that correspond to real adjacent-team asks that were declined, with rationale. |
| **AI-infra fit** | Generic. | Mentions cost or governance explicitly. | Cost is a first-class commitment with a target and owner; AI-security risks reference the public standards where applicable (MITRE ATLAS, OWASP ML Top 10); capacity view is separate. |

**Caps.** A roadmap without confidence levels caps at L2
regardless of other dimensions. A roadmap without non-goals
caps at L3. A roadmap that merges capacity planning into the
delivery view caps at L3 for AI-infra teams.

## 5. Common mistakes

- **Too many goals.** More than 5 is a tell that the team is
  committing to everything, which means committing to
  nothing in particular (parent
  [`SOLUTION.md`](../SOLUTION.md#the-roadmap-exercise-02-the-artifact-itself)).
- **Goals as activities.** "Work on inference optimization"
  can't be falsified. "p99 ≤ 180 ms at 10k QPS" can.
- **Labels without probability anchors.** "Medium confidence"
  can mean 20 % or 70 %; without an anchor, it will drift.
- **Nominal-capacity summation.** Planning against 91
  engineer-weeks when the team's actual delivered scope has
  averaged 60-65 for three quarters running.
- **One-way dependencies.** Only upstream or only downstream
  is tracked; the other is where the surprise comes from.
- **Risk register as broadcast list.** A register with 15
  entries, none driving weekly action, is noise.
- **Stretch items without triggers.** Stretch that
  automatically rolls to Q4 is backlog, not stretch.
- **No non-goals section.** The most common and most costly
  omission. Every adjacent team thinks their ask is in.
- **Capacity planning merged into the delivery roadmap.**
  For AI-infra teams, capacity needs its own ritual and
  artifact.
- **No cost commitment.** For AI-infra, the roadmap without
  a cost target has a hole where Startup/Finance will later
  stand.
- **No mid-quarter decision gate.** Medium-confidence goals
  drift to week 13 and miss with no recovery window.

## 6. References

- **Local exercise context — module SOLUTION.** Parent
  [`SOLUTION.md`](../SOLUTION.md#the-roadmap-exercise-02-the-artifact-itself)
  is the canonical source for the seven-section structure and
  the non-goals requirement. Also:
  [Estimation discipline](../SOLUTION.md#estimation-discipline-exercise-03).
- **Local exercise context — learning module README.**
  [`lessons/mod-703-project-roadmap/README.md`](https://github.com/ai-infra-curriculum/ai-infra-team-lead-learning/blob/main/lessons/mod-703-project-roadmap/README.md)
  — capacity-planning-as-separate-ritual, cost as first-class
  commitment, and the AI-infra sibling-org dependency list.
- **Local exercise context — sibling solutions.**
  [`exercise-03/SOLUTION.md`](../exercise-03/SOLUTION.md) for
  the stakeholder map this roadmap serves; the four audience
  views are projections of the single roadmap source of
  truth.
- **NIST AI Risk Management Framework** —
  <https://www.nist.gov/itl/ai-risk-management-framework>.
  The MAP function (contextualize + inventory risks) is the
  standard framing for section 5 (risks) of the roadmap when
  AI-system-specific risks are on the list. MANAGE is the
  framing for the mid-quarter decision gates.
- **MITRE ATLAS** — <https://atlas.mitre.org/>. If an item on
  the roadmap defends against adversarial AI threats
  (data poisoning, model extraction, prompt-side attacks for
  generative models), reference the specific ATLAS tactic by
  ID in the risks or goals section rather than describing it
  in prose.
- **OWASP Machine Learning Security Top 10** —
  <https://owasp.org/www-project-machine-learning-security-top-10/>.
  Use when a serving-stack commitment on the roadmap
  corresponds to defending against a listed risk; cite the
  risk ID so the Governance stakeholder can map coverage.

### Known research gap

A public, attested example of an AI-infra team's quarterly
roadmap document that carries explicit confidence levels and
a named non-goals section would be a strong style reference
for the seven-section structure above. No verifiable
candidate was identified at the time of writing.
Contributors should cite one only if it can be attributed to
a named team and organization; invented examples are not
acceptable.
