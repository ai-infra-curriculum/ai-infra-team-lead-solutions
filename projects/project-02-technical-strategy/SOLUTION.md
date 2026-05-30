# SOLUTION — Project 02: Technical Strategy & Roadmap

> Read this *after* you have attempted the project. The
> "solution" is a structured rubric plus a worked outline for
> the deliverable bundle, not a single canonical answer. The
> goal is to make every grading judgment defensible against
> the project brief in
> `ai-infra-team-lead-learning/projects/project-02-technical-strategy`.

> Provenance note: the section structure below derives from
> the team-lead track design (see `SOLUTION_OVERVIEW.md`) and
> from `mod-703-project-roadmap`, which is the closest
> module-level analog. Once the paired learner-facing brief in
> `ai-infra-team-lead-learning/projects/project-02-technical-strategy/README.md`
> is published, align section titles to its deliverable list
> rather than rewriting this file from scratch.

## 1. Solution overview

This project is the team-lead-tier capstone for translating a
team's situation into a **written technical strategy** plus a
**defendable roadmap** for the next planning horizon
(typically one to two quarters). It sits at the seam of three
modules in this track:

- `mod-703-project-roadmap` — the roadmap artifact itself and
  the estimation discipline behind it.
- `mod-704-cross-team-coordination` — the dependencies the
  strategy assumes and the commitments it implies.
- `mod-701-team-operations` — the operating cadence that
  executes the roadmap once it is approved.

The deliverable bundle a learner produces should make three
distinct readers comfortable signing off:

1. **The team** — engineers can see themselves in the plan,
   know what is in and out, and trust the load.
2. **Leadership** — a manager or director can see the strategic
   bet being made, the confidence level, and the risks.
3. **Adjacent teams** — dependent teams can see the timing of
   the interfaces that affect them.

A solution that satisfies one of those readers but not the
other two is incomplete, no matter how polished. The most
common failure pattern is a "strategy" that reads as upward
storytelling but does not survive a question from inside the
team about who picks up which piece on Monday morning.

Cross-track reference: principal-engineer track
`mod-501-technical-strategy` covers the *strategic frame* a
team lead's plan should slot into. A team lead writing strategy
without that frame typically inflates the deliverable into
something it cannot support. Treat the team-lead version as a
**translation layer** between principal-tier strategy and the
team's quarterly work.

## 2. Worked answer / implementation outline

A complete deliverable bundle for this project has five
artifacts. Each is short on purpose — the discipline is in the
choices, not the page count.

### 2.1 Strategy memo (1–2 pages)

Written in prose, not bullets-only. Structure:

1. **Context.** Two paragraphs: what the team owns, what has
   changed in the last quarter, what is forcing a strategy
   decision now. Avoid generic mission statements.
2. **The bet.** One paragraph stating the technical bet for
   this horizon. A bet is falsifiable; "improve reliability"
   is not a bet, "halve the on-call page rate for the
   inference platform by end of Q3" is.
3. **Why this bet now.** The reasoning — what evidence makes
   this the right bet versus the next-best alternative. This
   is the section graders read most carefully.
4. **What we are explicitly NOT betting on.** The cut list.
   Without this section adjacent teams interpret the strategy
   as "you have time for my thing too."
5. **Confidence and kill criteria.** Honest confidence level
   (high / medium / low) and the conditions under which the
   team would abandon or de-scope the bet mid-quarter.

A memo that reads more like advocacy than analysis is a red
flag — the lead is asking leadership to *approve* rather than
to *decide*.

### 2.2 Roadmap artifact (one page)

Use the structure from mod-703-project-roadmap:

| Section | What it says |
|---|---|
| Goals (3–5) | Outcomes with measurable targets. |
| Confidence | High / medium / low per goal. |
| Work streams | Rough timing, named engineers. |
| Dependencies | What we need from whom, when. |
| Risks | What could derail us. |
| Stretch goals | Done only if main goals land early. |
| Explicit cuts | What we are NOT doing, and why. |

The roadmap is the **commitment artifact**. It is what gets
referenced in a quarterly review when the team has shipped two
of five goals and needs to explain the other three. If the
artifact is shaped so that any miss can be reframed as a
success, the artifact is wrong.

### 2.3 Defense narrative (1 page or 5–7 slides)

The lead-facing-leadership version of the roadmap. This is the
artifact that goes into a roadmap review with the manager's
manager. Structure mirrors the memo plus:

- **The ask.** What the team needs from leadership (headcount,
  budget, scope protection, escalation support). If there is
  no ask, the meeting is status theater.
- **Trade-off framing.** "We can do A by date X, or B by date
  X, but not both" — phrased so the decision is visible.
- **Probabilistic commitments.** "80% confident on goal 1,
  60% on goal 3" rather than precise deadlines without
  uncertainty. See mod-703 SOLUTION.md §"Estimation
  discipline" for the reasoning.

### 2.4 Dependency / commitment register

A short table of cross-team commitments the roadmap assumes:

| Direction | Team | Commitment | Owner | Date | Status |
|---|---|---|---|---|---|
| Inbound | Data platform | Feature-store v2 read API | their-lead | mid-Q3 | confirmed in writing |
| Outbound | Eval team | Stable model registry IDs | our-lead | start-Q3 | proposed |

This is the artifact that survives a team reorg. mod-704
SOLUTION.md covers the durability mechanics. The minimum bar
is that every commitment has a named human owner on each side
and a written acknowledgement, not a conference-room handshake.

### 2.5 Operating-cadence delta

The strategy and roadmap usually imply a small change to how
the team operates day to day: a new on-call rotation, a
dedicated reliability week, a moved planning meeting, a
stricter scope-cut policy. List the changes explicitly so the
team operating doc (mod-701) can absorb them, and so the cost
of the new cadence is visible alongside the work.

If the strategy bundle does not produce *any* operating-cadence
delta, the team is implicitly being asked to deliver new work
on the same time budget, which is almost always the silent
failure mode.

## 3. Validation steps

Before the bundle is submitted (or graded), run these checks
in order. Stop at the first failure and fix before continuing.

1. **The bet is falsifiable.** Can you describe what evidence
   at the end of the horizon would make you say "we lost the
   bet" rather than "we should have done more"? If not, the
   strategy is unfalsifiable and graders should mark it down
   regardless of polish.
2. **The "what we are NOT doing" list has at least three
   items.** A cut list with one entry is usually a fig-leaf;
   strategy is mostly subtraction.
3. **Every roadmap goal has a confidence level and a named
   engineer.** Goals attributed to "the team" with no named
   driver default to nobody owning them.
4. **Every dependency in the register has a human owner on
   both sides and a written acknowledgement.** Verbal
   commitments do not count.
5. **The defense narrative contains an explicit ask.** If the
   only ask is "approve the plan," there is no ask.
6. **The operating-cadence delta is documented or marked as
   "none, deliberately."** Silent overload is the most common
   way these plans fail.
7. **No precision without uncertainty.** Any specific date or
   number should have a confidence interval or a confidence
   level attached. "Ship by July 15" without a confidence is
   a fiction.
8. **Cross-track coherence.** The strategy does not contradict
   the principal-engineer-tier strategy it nests inside, and
   does not commit cross-team work that mod-704's dependency
   discipline would flag as unsafe.

A bundle that passes all eight checks is at least a "meets bar"
solution. Distinction-level solutions also surface a
**counter-strategy** — the strongest alternative the lead
considered and rejected, and the evidence that decided it.

## 4. Rubric / review checklist

Score each row 0 (missing) / 1 (partial) / 2 (clear). A
passing bundle scores ≥ 16 / 24; a distinction bundle
scores ≥ 21 / 24 and has a non-zero counter-strategy row.

| # | Criterion | 0 | 1 | 2 |
|---|---|---|---|---|
| 1 | Strategy memo states a falsifiable bet | absent | bet present but vague | sharp, testable bet |
| 2 | Memo explains why this bet, not the alternatives | absent | asserted | argued from evidence |
| 3 | Cut list (≥ 3 items, with rationale) | none | a list, no reasons | items + rationale per item |
| 4 | Confidence levels honestly stated | none | "high" everywhere | calibrated, mixed levels |
| 5 | Roadmap is one page, structured per mod-703 | over-long or off-template | structurally complete | tight and complete |
| 6 | Goals are outcomes with measurable targets | activities only | mixed | outcomes throughout |
| 7 | Dependencies in writing, named owners | informal | partial | every row complete |
| 8 | Defense narrative has an explicit ask | none | ambiguous | concrete and actionable |
| 9 | Operating-cadence delta is named or "none, deliberately" | implicit overload | mentioned, vague | concrete and revisitable |
| 10 | Counter-strategy considered and documented | absent | a sentence | argued and rejected with reason |
| 11 | Risks include a top-3 with mitigations or "accept and watch" | none | listed only | each with response |
| 12 | Kill criteria for the main bet are written down | none | "we will reassess" | named conditions |

Reviewer hint: graders should ask one open question after the
review — "what would change your mind about this bet?" A lead
who can answer with a specific signal is calibrated; a lead
who restates the bet has not yet internalized the falsifiability
discipline.

## 5. Common mistakes

These are the failure patterns that show up most often in
team-lead-tier strategy submissions. The ordering reflects how
frequently graders should expect to see them.

1. **Strategy as upward marketing.** The memo reads as "here is
   the great work we will do" rather than "here is the choice
   we made and why." Fix: rewrite the "why this bet now"
   section starting from the alternatives.
2. **A roadmap that cannot miss.** Goals stated so loosely that
   any outcome can be called success. Fix: bind each goal to a
   measurable target and a date with confidence.
3. **Estimates without uncertainty.** Precise dates implying
   confidence the lead does not have. Fix: add 80/60/40
   confidence labels or three-point ranges (best / expected
   / worst).
4. **No cut list.** Or a cut list with one symbolic item. Fix:
   force three real cuts, including one that will be
   unpopular.
5. **Cross-team commitments only in chat.** Mid-quarter the
   dependency owner reorgs and the commitment evaporates.
   Fix: every commitment in writing with named owners on both
   sides, in the register.
6. **Strategy invisible to the team.** The lead writes upward
   and assumes the team will pick it up. The team only sees
   the roadmap output and disagrees in the hallway. Fix: walk
   the team through the strategy memo *before* the defense
   narrative goes up; capture team objections in the risks
   section.
7. **No operating-cadence delta.** New work added with no
   change to how the team plans, on-calls, or runs retros.
   Silent overload follows. Fix: state the delta explicitly,
   or state "no delta, deliberately" with the reasoning.
8. **No counter-strategy.** A strategy the lead never
   compared against an alternative is rarely the right
   choice; it is just the one that came to mind first. Fix:
   write the strongest opposing strategy in one paragraph and
   the evidence that rejected it.
9. **Mis-altitude.** The team-lead bundle attempts
   principal-engineer-tier strategy across many teams, or
   tactical sprint planning that should stay in the operating
   doc. Fix: re-read SOLUTION_OVERVIEW.md §"How a 'solution'
   looks in this track."
10. **Strategy that ignores on-call.** Capacity assumed at
    100% while the team has a 20–30% on-call tax. Fix: subtract
    on-call (and known new-hire ramp) from capacity before
    sizing the bet.

## 6. References

Official / project-internal references — these are the canonical
documents to ground judgments against. Paths inside the
curriculum repositories are stable; everything else is a
generally accepted practitioner concept linked to a primary
source where one exists.

- `ai-infra-team-lead-solutions/SOLUTION_OVERVIEW.md` — design
  philosophy across the track; in particular §"How a 'solution'
  looks in this track" and §"Defending priority upward is not
  optional."
- `ai-infra-team-lead-solutions/modules/mod-703-project-roadmap/SOLUTION.md`
  — the roadmap-artifact rubric this project depends on,
  especially §"The roadmap (exercise 02): the artifact itself"
  and §"Estimation discipline (exercise 03)."
- `ai-infra-team-lead-solutions/modules/mod-704-cross-team-coordination/SOLUTION.md`
  — the dependency-register discipline used by §2.4 above.
- `ai-infra-team-lead-solutions/modules/mod-701-team-operations/SOLUTION.md`
  — the operating-cadence baseline that §2.5 modifies.
- `ai-infra-team-lead-learning/projects/project-02-technical-strategy/`
  — the learner-facing brief this solution responds to. When
  the brief is published, align §2's deliverable list and any
  named scenario or fictional company to it rather than
  rewriting this file.

Cross-track references — read these when the bundle needs to
nest inside a wider strategic context:

- `ai-infra-principal-engineer-solutions/modules/mod-501-technical-strategy/SOLUTION.md`
  — the principal-tier strategic frame the team-lead bundle
  translates from. The team-lead track references it by name
  in `SOLUTION_OVERVIEW.md`; confirm the exact filename in the
  principal-engineer solutions repo before linking from a
  graded submission.
- `ai-infra-principal-architect-solutions/` — the multi-year
  investment view that the quarterly roadmap aggregates into;
  relevant when the team's bet implies architectural change
  beyond one horizon.

External concepts and primary sources — referenced by name in
the sections above. Use these for grounding rather than
secondary summaries:

- Architectural Decision Records (ADRs) — https://adr.github.io/
  and Michael Nygard's original post,
  https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions
- OKR-style outcome framing — https://en.wikipedia.org/wiki/Objectives_and_key_results
- RACI responsibility assignment —
  https://en.wikipedia.org/wiki/Responsibility_assignment_matrix
- Three-point estimation (best / expected / worst) —
  https://en.wikipedia.org/wiki/Three-point_estimation
- Reference-class forecasting (Flyvbjerg / Kahneman) —
  https://en.wikipedia.org/wiki/Reference_class_forecasting

No specific external case study, metric, or incident is
asserted in this solution; if a grader or learner wants to
ground a section in a published postmortem or engineering
blog, that source should be cited inline at the point of use
and must be verifiable.
