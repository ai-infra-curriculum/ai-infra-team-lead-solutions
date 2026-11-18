# SOLUTION — exercise-01: Cross-Team Coordination Case Study

> Read this *after* attempting the exercise. The deliverable is
> a case study analysis, not a code artifact. The worked example
> below is deliberately fictional and labeled as local exercise
> context so no uncited incidents are claimed as real.

## 1. Solution overview

The learner analyzes a real or representative cross-team
coordination episode and extracts the mechanisms that made it
work (or fail). A strong submission identifies four things
explicitly:

1. **The interface** between the teams (was it written down? when?)
2. **The incentive alignment** (did both teams benefit, or was one
   subsidizing the other?)
3. **The communication cadence** (how often did they sync, and
   who owned the meeting?)
4. **The escalation path** (who decided when the two team leads
   disagreed?)

Those four dimensions map directly to the "cross-team contract"
framework in the module SOLUTION and map further to the role and
responsibility clarity that NIST AI RMF `GOVERN 2` calls out as
foundational for AI system accountability.<sup>[1]</sup>

## 2. Worked answer

> **Local exercise context (fictional).** The following is a
> labeled teaching scenario. It is not based on any specific real
> organization, incident, or product and is not cited as evidence
> of any real event.

### 2.1 Scenario

Two teams at a mid-size company share a coordination relationship:

- **Team P (Platform):** owns a shared feature store serving all
  ML teams.
- **Team C (Consumer):** owns a fraud-detection model that
  depends on near-real-time feature freshness from Team P.

Six months ago, Team C shipped a model that started producing
false positives in production. Root cause: Team P had deprecated
a feature definition in favor of a slightly different one (same
name, new semantics). Team C's model trained on the old
semantics; serving used the new. The deprecation was announced
in Team P's internal release notes but never propagated to
Team C.

### 2.2 Analysis along the four dimensions

**Interface.** Explicit at the API-shape level (names, types, SLA)
but **not** at the semantic level. The feature-store team
documented "what the endpoints return"; they did not document
"what the field *means*." When semantics drifted, there was no
contract to break. This is the classic "schema contract, but no
semantic contract" failure.

**Incentive alignment.** Misaligned. Team P was measured on
feature-store uptime and schema velocity (how fast they could
iterate on new feature definitions). Team C was measured on
model precision/recall in production. A semantic change that
preserved schema gave Team P a "clean" change and gave Team C a
silent regression. Neither team's incentives rewarded catching
the mismatch before it shipped.

**Cadence.** Monthly office hours hosted by Team P, loosely
attended by Team C. Weekly standup within each team. **Zero**
standing cross-team sync. The deprecation announcement went
into Team P's channel; Team C's lead did not see it until the
regression was already in production.

**Escalation.** Ad hoc. Team C's lead escalated to his own
manager, who escalated to Team P's director. By the time the
decision ("roll back the deprecation, re-announce with a
deprecation window") was made, Team C had already shipped a
revert. The decision latency was roughly one week, with the
incident live the whole time.

### 2.3 What would have prevented it

Three changes, in order of leverage:

1. **A written cross-team contract** that included *semantic*
   guarantees, not just schema. Covered in [exercise-02](../exercise-02/SOLUTION.md).
2. **A deprecation policy** attached to the contract: no feature
   semantics change without a minimum N-day notice to named
   consumers and an explicit acknowledgment. This is the kind of
   "accountability structure, roles and responsibilities" that
   NIST AI RMF `GOVERN 2` flags as a baseline control.<sup>[1]</sup>
3. **A standing biweekly cross-team review**, owned jointly, with
   agenda items that force surfacing of upcoming changes. Covered
   in [exercise-05](../exercise-05/SOLUTION.md).

### 2.4 Decision rationale

A submitter may propose a different fix set (e.g., stricter
typing in the feature store, automated downstream tests, a
schema registry). All of those help, but none of them replace
the coordination layer:

- A schema registry catches *structural* drift. The failure here
  was *semantic*.
- Automated downstream tests require Team C to have authored a
  test that encoded the old semantics; they didn't, because
  the semantics were implicit.
- Stricter typing is a bandage on the same underlying problem:
  the contract was between systems, not between teams.

The coordination fix (contract + cadence + escalation) is the
root cause. Technical fixes are complementary but insufficient
on their own. This is the central point of the module SOLUTION's
truth #1: "Most cross-team problems are coordination problems
pretending to be technical problems."

## Implementation

To produce a submission that matches the worked answer above:

1. **Pick the case.** Choose a real or representative cross-team
   episode you can describe in two paragraphs. If composite or
   fictional, label it that way at the top.
2. **Name the two teams and their distinct roles.** One sentence
   each. If you can't state the role difference, the case is a
   single-team case in disguise.
3. **Walk the four dimensions in order.** Interface → incentives
   → cadence → escalation. One short paragraph per dimension.
   Each paragraph must name a concrete artifact or absence
   (e.g., "schema file existed, semantic doc did not").
4. **Separate the coordination fixes from the technical fixes.**
   Write a short "what would have prevented it" section whose
   top entry is a coordination artifact (contract, policy,
   cadence), not a tool.
5. **Add decision rationale.** For each proposed fix, state why
   the coordination fix is the root cause and the technical
   fixes are complementary.
6. **Self-grade against section 4.** If any dimension scores 0,
   rewrite that paragraph before submitting.

## 3. Validation steps

To self-grade the submission, the learner should be able to
answer **yes** to all of the following:

- [ ] Does the case study name the two (or more) teams and their
      distinct roles?
- [ ] Is the interface between the teams described concretely
      (API, data, schedule, something)?
- [ ] Is the incentive misalignment (or alignment) named
      explicitly, not implied?
- [ ] Is the communication cadence specified (frequency, owner)?
- [ ] Is the escalation path written down, even if the answer is
      "there wasn't one"?
- [ ] Are the proposed fixes separated into *coordination* fixes
      and *technical* fixes?
- [ ] Do the lessons generalize beyond this one case — would
      they apply to a different pair of teams?

If the submission is based on a real public postmortem or a
real past incident the learner lived through, the submission
should cite it. If it is a composite or illustrative example,
it should say so explicitly ("Scenario is a composite; not
drawn from a single organization").

## 4. Rubric / review checklist

Grade on five dimensions. Each is scored 0–3 (0 = missing,
1 = sketch, 2 = solid, 3 = exemplary). Passing bar: 10/15
with no dimension at 0.

| # | Dimension | 0 | 1 | 2 | 3 |
|---|---|---|---|---|---|
| 1 | Interface clarity | Not described | Named but not detailed | API/data/schedule given | Includes semantic contract, not just schema |
| 2 | Incentive analysis | Absent | Mentioned | Named for both teams | Explains the misalignment mechanism |
| 3 | Cadence description | Absent | "They talked sometimes" | Frequency + owner | Cadence tied to risk level |
| 4 | Escalation path | Absent | Named | Escalation ladder with roles | Escalation ladder + decision-latency commentary |
| 5 | Transferable lessons | None | Generic | Specific and generalizable | Specific, generalizable, and separated coord-vs-tech |

Reviewer should also flag two anti-patterns if present:

- **Hero narrative** ("X heroically aligned the teams"). Zero
  points for item 5 if the lesson is hero-dependent.
- **Blame narrative** ("Team P was negligent"). Rewrite as a
  system failure. Zero points for item 2 if the only
  incentive analysis is moral, not structural.

## 5. Common mistakes

- **Treating the case as a technical post-mortem.** The
  exercise is about *coordination*. "They should have used
  typed APIs" is a technical lesson; the coordination lesson
  is "the interface was implicit."
- **Single-team analysis.** Describes what Team C did wrong
  without describing what Team P did wrong, or vice versa.
  Cross-team cases need both sides.
- **Postmortem-as-blame.** A good cross-team case study
  assumes competence on both sides and asks what the system
  rewarded.
- **No written interface in the "what would have prevented it"
  section.** A fix proposal that doesn't include "we would
  have written X down" has missed the point of the module.
- **Over-reliance on process without owner.** "We should have
  had a weekly sync" without naming who runs it is as
  implicit as the original failure.
- **Confusing cross-team coordination with cross-org
  initiative.** If the case study involves 10+ teams or
  multiple VPs, it belongs in `principal-engineer/mod-503-cross-org-initiative`,
  not this module.

## 6. References

1. NIST AI Risk Management Framework (AI RMF 1.0) — `GOVERN`
   function, particularly `GOVERN 2` (accountability structures,
   roles and responsibilities for AI system risk). See
   <https://www.nist.gov/itl/ai-risk-management-framework>.
2. Module SOLUTION: [../SOLUTION.md](../SOLUTION.md) — the
   framework this exercise instantiates.
3. Related exercises:
   [exercise-02](../exercise-02/SOLUTION.md) (the written
   contract),
   [exercise-05](../exercise-05/SOLUTION.md) (the cross-team
   review cadence).

<sup>[1]</sup> NIST AI RMF 1.0 defines the `GOVERN` function as
including "accountability structures" and "roles and
responsibilities" across the AI system lifecycle. Cross-team
contracts are one concrete mechanism that implements that
control at the team-lead altitude.
