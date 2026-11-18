# SOLUTION — exercise-04: Joint Cross-Team Roadmap

> Read this *after* attempting the exercise. The deliverable is a
> joint quarterly roadmap that makes cross-team dependencies
> visible. The worked example is a labeled teaching scenario.

## 1. Solution overview

The joint roadmap turns "we're integrating with Team P" into a
dated, shared artifact that both teams own. The module SOLUTION
emphasizes three properties:

- **Visibility of the dependency point** — the single calendar
  moment when one team's output becomes the other team's input.
- **Joint ownership** — both teams review the roadmap on a
  cadence; neither team can unilaterally change it.
- **Deprecation inclusion** — the old thing's retirement is on
  the roadmap, not implicit.

A strong submission produces a table that both leads could
present together without re-reconciling privately first.

## 2. Worked answer

> **Local exercise context (fictional).** Teams and dates are a
> labeled teaching example; `Q1`–`Q4` are abstract quarters, not
> a specific calendar year.

### 2.1 The joint roadmap

Scope: **Team P** (Platform, feature store) ↔ **Team C**
(Consumer, fraud detection). Migration from feature-store API
v1 to v2.

| Quarter | Team P deliverables | Team C deliverables | Dependency point | Status |
|---|---|---|---|---|
| Q1 | API v2 design doc; semantic-contract format; stakeholder review | Consumer prototyping against v2 mock; identify features in scope | **API v2 design frozen by end of Q1** — mock available by mid-Q1 | Planned |
| Q2 | API v2 implementation (dev + staging); SLA burn-in; migration guide | Migrate read paths of fraud model offline features | **API v2 beta available in staging by mid-Q2** | Planned |
| Q3 | API v2 GA; v1 placed in "deprecated" status in docs; SLA hardening | Full migration of fraud model to v2 in production; v1 shadow reads turned off | **v1 deprecation announced end of Q3, 60-day sunset window begins** | Planned |
| Q4 | API v1 removed after sunset; post-migration retro; roadmap close-out | All read/write paths on v2; any residual v1 consumers escalated | **API v1 removed end of Q4** | Planned |

### 2.2 How to read the table

- **Each row has a named dependency point.** The dependency
  point is the single artifact the other team is waiting on
  that quarter. If a row has no dependency point, the two
  columns aren't really cross-team work — they're just
  parallel projects.
- **Status column is mandatory.** "Planned / In-progress /
  Done / Slipped" tracked in a shared doc. When a status moves
  to "Slipped," both teams see it in the same place.
- **Deprecation is a row, not a footnote.** Row Q4 is as
  important as row Q1. Migrations that don't plan the removal
  live forever.

### 2.3 Decision rationale

**Why quarterly, not sprint-level.** Cross-team roadmaps live at
the quarter horizon because that's the horizon at which both
teams' managers plan. Sprint-level cross-team roadmaps are
noisy; the cadence doesn't match the planning layer that
controls commitments.

**Why only one dependency point per quarter.** More than one
turns the table into a wishlist. If three things need to happen
across teams in a quarter, either (a) it's really one thing with
sub-parts, (b) one of them is misassigned to the quarter, or
(c) the quarter is overcommitted. In cases (a) and (b), rework
the row; in case (c), rework the plan.

**Why sunset windows, not hard cutovers.** Hard cutovers
assume both teams hit their plan perfectly. Sunset windows
(30–90 days is typical) give the consumer team buffer without
giving indefinite reprieve to v1. The length should match the
estimated remediation cost on the consumer side.

**Why the roadmap is a shared doc, not two separate ones.**
The module SOLUTION's failure mode "Each team has its own
roadmap, dependencies are implicit" is the single most common
cause of missed cross-team milestones. One doc, co-owned, is
the fix. Quarterly review is covered in
[exercise-05](../exercise-05/SOLUTION.md).

**Why no RACI matrix here.** The ownership split is already
encoded in the two columns ("Team P deliverables", "Team C
deliverables") and in the cross-team contract
([exercise-02](../exercise-02/SOLUTION.md)). A RACI overlay
would duplicate information and add surface area without
adding fidelity.

### 2.4 How this slots into the team's own roadmap

Each team's single-team roadmap should reference this joint
roadmap, not duplicate it. If Team C's internal planning doc
says "Q2: migrate read paths," and the joint roadmap says
"Q2: migrate read paths of fraud model offline features," the
joint version is canonical. The single-team roadmap can link to
it.

This avoids the single most common drift: internal planning
docs that get updated without updating the joint plan, so the
two diverge and no one notices until a dependency point slips.

## Implementation

To produce a submission that matches the worked answer above:

1. **Scope the roadmap to one cross-team relationship.** Two
   teams, one integration (or migration). Multi-team roadmaps
   belong in the principal-engineer track.
2. **Draft the quarterly grid.** At least three future quarters,
   with one row per quarter. Each row has: Team A deliverables,
   Team B deliverables, dependency point, status.
3. **Name a dependency point per row.** A dependency point is a
   named artifact with a target date (`"API v2 beta available
   in staging by mid-Q2"`), not a quarter label. If a row has
   no dependency point, the two columns are parallel work, not
   cross-team work.
4. **Add a deprecation row.** The old thing's retirement is a
   first-class row, not a footnote. Include the sunset window
   length (30–90 days) and the removal date.
5. **Add the status column.** Three values only: `Planned`,
   `On track` / `In progress`, `Slipped`. Shared doc; both
   leads edit it.
6. **Link canonically from each team's internal roadmap.** The
   joint doc is the source of truth; single-team roadmaps link
   to it rather than duplicating.
7. **Name the review cadence.** Quarterly review minimum; mark
   the first review date on the doc.
8. **Get both leads to sign off on version 1.** Date and version
   the roadmap the same way as the contract
   ([exercise-02](../exercise-02/SOLUTION.md)).

## 3. Validation steps

Self-check before submission:

- [ ] The roadmap covers at least three future quarters.
- [ ] Each row has a named dependency point.
- [ ] Deprecation / retirement of the old thing appears as a
      row, not a footnote.
- [ ] Status column exists and tracks slips visibly.
- [ ] The doc is linked from both teams' internal plans as
      canonical for the cross-team work.
- [ ] Both leads have signed off on the current version.
- [ ] A review cadence is named (quarterly minimum).

Hand the roadmap to a third party (e.g., your shared manager)
and ask: "If Team P slips row Q2, what would Team C need to do?"
A good roadmap makes the answer immediate. A weak roadmap
requires private conversation to answer.

## 4. Rubric / review checklist

Scored 0–2 per dimension. Passing bar: 10/14.

| # | Dimension | 0 | 1 | 2 |
|---|---|---|---|---|
| 1 | Coverage | < 2 quarters | 2 quarters | 3+ quarters including a close-out quarter |
| 2 | Dependency point per row | Missing | Vague ("hand off") | Named artifact with target date |
| 3 | Deprecation in the plan | Not mentioned | Mentioned | Full sunset window with cutover date |
| 4 | Status tracking | None | Present, no slip handling | Present + slip surfacing mechanism |
| 5 | Joint ownership | Separate docs | Shared doc, one owner | Shared doc, both leads sign |
| 6 | Linkage to single-team roadmaps | Not linked | Linked one way | Canonical on both sides |
| 7 | Review cadence | Not stated | Stated | Stated + first review scheduled |

Reviewer flags:

- **"Dependency point: Q2."** A quarter is not a dependency
  point; the artifact is. Flag for revision.
- **No deprecation row.** The migration is only half-planned.
- **Bullet lists instead of a table.** Readable for one team,
  not for two. Push back to the table form.
- **Numbers of sub-milestones grow each quarter.** Sign the
  rows are not really dependency points but task lists.

## 5. Common mistakes

- **Each team authors their own column separately.** The
  dependencies become implicit; the joint roadmap is only
  nominally joint.
- **No deprecation row.** The old thing keeps running "just in
  case" for years. A migration without a sunset is not a
  migration; it's a parallel system.
- **Dependency points without owners.** "API v2 beta" without
  a named person who owns delivery means it will slip silently.
- **Quarter-boundary optimism.** Scoping dependency points to
  "end of Q2" (meaning the last day) leaves no room for
  consumer-side ramp. Target mid-quarter for upstream deliverables
  the consumer needs to integrate before quarter-end.
- **No slip-handling mechanism.** A joint roadmap without a
  status column is a wishlist. Status + slip surfacing is what
  makes it operational.
- **Treating the roadmap as a commitment artifact for the
  director, not a coordination artifact for the teams.** The
  roadmap is for the teams first; the director reads it as a
  consequence.
- **One row per team per quarter.** Noise. The joint roadmap
  should surface *only* the cross-team dependencies; parallel
  single-team work belongs in each team's internal roadmap.

## 6. References

1. NIST AI Risk Management Framework (AI RMF 1.0) — `MAP`
   function (identify dependencies and interactions in the AI
   system lifecycle).
   <https://www.nist.gov/itl/ai-risk-management-framework>
2. Module SOLUTION: [../SOLUTION.md](../SOLUTION.md), section
   "Roadmap (exercise 04): the joint plan".
3. Related exercises:
   [exercise-02](../exercise-02/SOLUTION.md) (the contract this
   roadmap executes under),
   [exercise-05](../exercise-05/SOLUTION.md) (the review that
   keeps the roadmap honest).
