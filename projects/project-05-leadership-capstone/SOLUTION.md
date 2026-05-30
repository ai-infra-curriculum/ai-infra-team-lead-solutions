# SOLUTION — Project 05: Leadership Capstone

> Read this *after* you have completed (or seriously attempted) modules
> `mod-701` through `mod-705`. The capstone is not a new topic — it is
> the integration of the five modules into a single coherent
> team-operating portfolio that a real lead could carry into their
> first 90 days on a team. This document explains what "integration"
> means here, what the deliverable looks like, how to grade it, and
> the failure modes that consistently appear when learners attempt
> it.

## 1. Solution overview

### What the capstone is

The capstone simulates a team lead's first quarter on a new AI infra
team. The learner produces a **leadership operating portfolio** — a
bound set of artifacts that, taken together, demonstrate that the
learner can run all three pressures of the role simultaneously:

- **The team** — people management, growth, hiring, onboarding.
- **The work** — operating rhythm, roadmap, delivery.
- **The org** — defending priorities upward, coordinating sideways.

Every artifact in the portfolio is something a real lead would carry
into their first week. Nothing is purely academic. The grading bar is
not "is the document well-written" but "would I hand this to a peer
team lead and ask them to use it on Monday?"

### Why integration matters

Each module in the track teaches one pressure in isolation. A team
operating doc with no people-management plan starves the team of
growth conversations; a hiring rubric with no onboarding plan produces
strong hires who flounder for the first 90 days; a roadmap with no
cross-team commitment register collides with neighbouring teams every
quarter.

The capstone exists because **most lead failures are
between-modules**, not within them. A lead who has each individual
ritual handled but never reconciles them produces a team that is
busy but not coherent. The portfolio forces reconciliation.

### Scope and altitude

This is a **first-line manager / team lead** altitude:

- Team size: 4–10 engineers (the realistic span for a team lead).
- Horizon: one quarter (one OKR cycle, two-to-six sprints).
- Authority: hiring input, roadmap proposal, on-call shape — yes;
  comp setting, org design, cross-org budget — no.

If your portfolio assumes you set headcount budget or run a
50-person org, you have drifted into the principal-engineer or
director track. Re-scope.

### What you must produce

The portfolio is a single directory containing six artifacts. Each
artifact maps to one module plus the integration narrative that ties
them together:

| Artifact | Module | What it demonstrates |
|---|---|---|
| `team-operating-doc.md` | `mod-701` | Operating rhythm: rituals, on-call, decision framework |
| `people-plan.md` | `mod-702` | 1:1 cadence, growth conversations, performance handling |
| `roadmap-defense.md` | `mod-703` | One-quarter roadmap with explicit upward narrative |
| `cross-team-register.md` | `mod-704` | Dependencies in, dependencies out, with named owners |
| `hiring-onboarding-kit.md` | `mod-705` | Interview rubric + 90-day onboarding plan |
| `integration-narrative.md` | capstone | How the five above reconcile into one coherent lead operating system |

The integration narrative is the capstone-specific artifact. The
other five are extended versions of the module deliverables — but the
portfolio is graded on the *coherence* across them, not the quality
of each in isolation.

## 2. Worked answer or implementation

This section walks through what each artifact should look like at
capstone quality, then shows what the integration narrative ties
together. It is intentionally a worked example, not a fill-in
template — a learner submitting only the headings below has not
demonstrated capstone-level work.

### 2.1 The team operating doc (`team-operating-doc.md`)

At capstone quality this doc is the artifact a new hire reads on day
one and understands what the team does and how it works. It contains:

1. **Mission** — one sentence. "We own the GPU training platform for
   the model org's foundation-model team." Anything longer than two
   sentences is a sign the team's scope is unclear and needs to be
   negotiated with the manager chain before the doc is written.
2. **Scope boundaries** — in/out. The "out" list is the more
   important one; it is the contract with adjacent teams.
3. **Operating rhythm** — daily / weekly / monthly / quarterly. Be
   specific: ritual name, when, who attends, what the output is. A
   ritual without a written output is a meeting without a purpose.
4. **Roles** — actual responsibilities, not titles. Who runs the
   incident channel? Who triages incoming requests? Who reviews
   on-call handoffs?
5. **Decision framework** — when does the team vote, when does the
   lead decide, when does the team disagree-and-commit? The default
   should be "lead decides after consultation"; voting is rare and
   reserved for things like ritual changes.
6. **On-call shape** — rotation length, escalation, handoff format.
   For AI infra teams, also: GPU-job triage, model-training failure
   triage, capacity-eviction policy. Generic SRE on-call docs miss
   these because they assume request-response workloads.
7. **Communication channels** — Slack channels, paging tools, async
   docs. When to use each. The most common omission is the
   "what-not-to-Slack" policy — without it, the team's signal-to-noise
   degrades.

A capstone-quality version explicitly notes **revision history** at
the bottom. The team operating doc is not finished on day one; it
gets updated when a ritual is added, removed, or reshaped. The
revision history is how the team remembers why a ritual exists.

### 2.2 The people plan (`people-plan.md`)

At capstone quality this is **per-report**, not generic. For each
direct report:

- **Current state** — what they're working on, where they are in
  their career, what they want next.
- **1:1 cadence** — weekly is the default; biweekly only with
  written justification.
- **Growth direction** — what skill the next six months are aimed at
  developing. This is *not* a promotion plan, which is a separate
  thing — it is a skill plan.
- **Standing 1:1 agenda items** — what gets carried week to week
  (current project, blockers, growth area, feedback in both
  directions).
- **Quarterly checkpoint** — when the lead does a longer
  career-conversation 1:1, separate from weekly tactical 1:1s.

The plan must also include:

- **Performance escalation path** — what the lead does when a
  report's performance is below bar. The order is: clarify the gap
  in writing in a 1:1 → 30-day check-in → involve HR /
  manager-chain → formal PIP. Skipping steps creates either a hostile
  surprise (jumping to PIP) or an unresolved problem (talking around
  it for six months).
- **Feedback mechanism** — how the lead solicits upward feedback
  from the team. Anonymous quarterly survey is a low-effort default;
  a 1:1 question ("what's one thing I should do more of, one less
  of") is higher-effort but higher-signal.

A common gap at capstone level is the **departing-engineer plan**:
what the lead does when someone resigns or moves teams. The plan
should name the knowledge-transfer steps and the on-call rotation
backfill, both of which are usually rushed when the resignation is
real.

### 2.3 The roadmap defense (`roadmap-defense.md`)

At capstone quality this is the *upward* version of the team's
roadmap — the version the lead presents to their manager and to the
manager's peers.

It contains:

1. **The team's top 3 outcomes for the quarter**, each with a
   measurable definition of done. Not features; *outcomes*.
2. **The mapping from outcomes to projects** — which engineering
   workstreams contribute to each outcome.
3. **The capacity model** — engineers × weeks available, minus
   on-call load, minus support load, minus expected
   interruption load. The result is the actual capacity for new work.
   Most lead-presented roadmaps fail because they assume 100%
   capacity.
4. **The trade-off narrative** — what the team is *not* doing this
   quarter, and what would have to change for it to be added back.
   This is the most important section; it is the section that
   protects the team from quarterly priority shifts.
5. **Dependencies** — what the team is waiting on from other teams,
   and what other teams are waiting on from this team. Cross-reference
   `cross-team-register.md`.
6. **Risk register** — top three risks to the quarter, each with a
   mitigation and a "we'll know we have to escalate by [date]"
   trigger.

The doc should be presentable in 30 minutes with 15 minutes of
discussion. If it requires a 60-minute readout, the priorities are
not clear enough.

A capstone-quality version also includes a **rejected alternatives**
appendix: the projects the lead considered and explicitly chose not
to do, with the reasoning. This is what makes the defense robust
when a stakeholder asks "why aren't you doing X?" — the answer
already exists.

### 2.4 The cross-team commitment register (`cross-team-register.md`)

At capstone quality this is a live document, not a static one. The
shape is a table:

| Direction | Counterparty team | Commitment | Owner (us) | Owner (them) | Status | Next checkpoint |
|---|---|---|---|---|---|---|

`Direction` is `in` (they are providing to us) or `out` (we are
providing to them). `Commitment` is one sentence with a measurable
outcome. `Status` is `on-track`, `at-risk`, or `blocked`. `Next
checkpoint` is the next time the two owners sync.

The capstone-quality version distinguishes:

- **Hard commitments** — written, dated, with a named on-call owner
  on both sides.
- **Soft commitments** — best-effort, with explicit "we will tell
  you if it slips" expectations.
- **Asks** — things the team has requested from a counterparty but
  not received commitment on.

A common gap is treating all three as the same thing in
conversation. The register's job is to make the difference
explicit so that when a quarterly priority shift happens, the lead
can tell their manager which commitments are now at risk.

### 2.5 The hiring and onboarding kit (`hiring-onboarding-kit.md`)

At capstone quality this contains two sub-artifacts:

**Interview rubric**:

- One signal per interview slot. Loop covers at minimum: coding,
  system design, collaboration, role-specific (e.g., distributed
  training, model serving), and communication.
- Each signal is assessed by at least two interviewers. Calibration
  notes describe what a `4` versus `5` looks like, with examples.
- A debrief script that opens with each interviewer's
  conclusion before discussion (to prevent anchoring), then moves
  to evidence, then to a decision.
- A "no-hire by default" decision rule: positive evidence is
  required to hire, not negative evidence required to reject.

**90-day onboarding plan**:

| Week | Milestone |
|---|---|
| Week 1 | Environment set up; first trivial PR merged |
| Week 2-3 | First small project; pairing on real work |
| Week 4 | First retrospective 1:1: how's it actually going? |
| Week 5-8 | Owning a small piece of work end-to-end |
| Week 9-12 | Integrated into rotations; primary owner of one workstream |

Per new hire:
- **Buddy** (peer, daily questions).
- **Mentor** (senior, weekly growth conversation; may overlap with
  buddy).
- **First project** that is real, bounded, and recoverable. "Make
  the lint config consistent" is fine; "redesign the inference
  layer" is not.
- **Check-in cadence** above and beyond normal 1:1s for the first
  four weeks.

A capstone-quality kit also includes the **role-leveling note** —
what `IC4`, `IC5`, `IC6` look like for this specific team. Without
it, hiring loops default to "I would hire them" without specifying
*at what level*, and the offer process becomes ad hoc.

A note on the leveling rubric: leveling is organization-specific and
should not be invented here. Capstone learners should link to their
own org's leveling guide, or, if none exists, to a published example
as the reference shape — e.g., Rent the Runway's engineering ladder
(<https://docs.google.com/spreadsheets/d/13gx3yf8AKK6PFh76gJoEcJL4xgshmrnxZjL8gXSb-aA/edit>),
Jorge Fioranelli's *Engineering Ladders*
(<https://github.com/jorgef/engineeringladders>), or the curated
collection at <https://www.progression.fyi/>.

### 2.6 The integration narrative (`integration-narrative.md`)

This is the capstone-specific artifact. The other five could (in
principle) be produced by a learner who scored well in their
respective modules but never thought about how they fit together.
The integration narrative makes the fit explicit. It is short — two
to four pages — and covers:

1. **The team's operating shape this quarter.** One paragraph that
   ties the operating doc, the people plan, and the roadmap into a
   single story. "Our team of seven engineers is delivering three
   outcomes this quarter, on a two-week sprint cadence, with weekly
   1:1s and a quarterly growth checkpoint, while supporting an
   on-call rotation of five and onboarding one new hire in week
   four."
2. **The reconciliation points.** Where do the five artifacts touch
   each other, and how is the touch handled?
   - The roadmap's capacity model must subtract the onboarding load
     for the new hire (the team plan says they start in week four;
     the capacity model must reflect their ramp-up, not full
     productivity).
   - The cross-team register's hard commitments must appear in the
     roadmap's project list (otherwise the team is committing to
     work it hasn't planned capacity for).
   - The hiring rubric's "what we're hiring for" must match a gap
     identified in the people plan (otherwise the team is hiring
     against an undefined target).
   - The on-call rotation in the operating doc must reflect the team
     composition the people plan describes (you cannot rotate four
     engineers through a 24/7 schedule).
3. **The trade-offs the lead has made.** Each module's deliverable
   has an implicit ideal; the integration forces compromises.
   Surface the top three explicitly. Example: "the people plan
   calls for monthly skip-level 1:1s, but the cross-team register's
   incident commitments mean we have triaged that down to
   quarterly skip-levels for this quarter; we will re-evaluate at
   week six."
4. **The escalation triggers.** When does the lead escalate to their
   manager? When does the team know to pull the lead in versus
   handle it themselves? When is a "we'll know we're in trouble by
   X" trigger fired?
5. **The first 90-day plan for the lead themselves.** Not the
   team's plan — the *lead's* personal plan: what they will learn,
   who they will meet, what they will not commit to until they have
   seen the team operate through one full sprint cycle.

The integration narrative is the artifact a peer team lead or
manager reads to decide whether the learner is *ready to lead a
team*. It is judged on coherence, honesty about trade-offs, and the
absence of magical thinking.

## 3. Validation steps

### 3.1 Self-check the learner runs before submission

Run each check against the assembled portfolio. Each check has a
binary outcome.

1. **Does every artifact name a real owner?** No "the team" or
   "the lead" without a person attached (for the lead's own
   artifacts, the lead's name is fine).
2. **Is every commitment dated?** "By end of quarter" is acceptable
   only if the quarter is named ("by end of Q3 2026").
3. **Does the capacity model balance?** Sum of work assigned to
   engineers in the roadmap, plus on-call load, plus expected
   support load, ≤ available engineer-weeks. If it exceeds, the
   roadmap is over-committed.
4. **Are the cross-team commitments reflected in the roadmap?**
   Every `out` commitment in the register must correspond to a
   project line in the roadmap.
5. **Does the people plan cover every direct report?** No
   placeholder rows. If a report is missing, the plan is incomplete.
6. **Is there a documented escalation path for at least one
   plausible failure mode in each module?** (on-call escalation,
   performance escalation, roadmap slip, dependency slip, hiring
   slip).
7. **Does the integration narrative name the top three trade-offs
   the lead has actually made?** Not "we plan to balance everything"
   — actual trade-offs with the thing that gave way.

A portfolio that fails any of checks 1–5 is structurally incomplete.
A portfolio that fails 6 or 7 may pass module-level grading but
fails the integration bar of the capstone.

### 3.2 Peer review the grader runs

A peer team lead (real, in-organization) reads the portfolio for 30
minutes and answers three questions:

1. **Could I run this team starting Monday using only these
   documents?** If no, what's the first thing I would have to
   make up?
2. **Where do the artifacts contradict each other?** Even one
   contradiction (the operating doc says biweekly sprint planning;
   the roadmap assumes monthly) indicates the integration has not
   been done.
3. **Where is the lead lying to themselves?** Magical thinking
   (full capacity for new work; everyone on the team is performing;
   no cross-team risks) is the most common failure of capstone
   portfolios.

A pass means the peer answers "yes, with minor gaps" to (1) and "no
material contradictions" to (2) and "honest about the soft spots"
to (3).

### 3.3 Static checks on the artifacts themselves

These can be done mechanically:

- All six artifact files exist at the expected paths.
- Each artifact has a revision-history footer with at least one
  entry.
- Each artifact has a "last reviewed" date within the last 30 days
  of submission (the lead has actually reviewed it as one document,
  not stitched together from five separate efforts months apart).
- Every internal cross-reference resolves (the roadmap references
  the cross-team register; the register references the roadmap).
- No artifact exceeds ten pages of body text. Longer than that
  means the lead has not distilled.

## 4. Rubric or review checklist

The capstone is graded on five dimensions, each on a 1–4 scale.
A passing portfolio scores ≥ 3 on every dimension and ≥ 16 total.

### 4.1 Coherence (weight: 30%)

| Score | Description |
|---|---|
| 1 | The artifacts read as five independent documents. No reconciliation. |
| 2 | Some cross-references but they are mechanical (links, not consequences). One artifact contradicts another. |
| 3 | The artifacts reconcile. The integration narrative names the trade-offs explicitly. |
| 4 | The artifacts compose into a single operating system. A peer lead could pick this up and run the team. |

### 4.2 Realism (weight: 25%)

| Score | Description |
|---|---|
| 1 | The portfolio assumes ideal conditions: full capacity, no attrition, no priority shifts, no incidents. |
| 2 | The portfolio acknowledges risk but does not plan for it. |
| 3 | The portfolio names the top risks, has triggers for escalation, and the capacity model is conservative. |
| 4 | The portfolio reads like a real lead's working document: it is honest about what is hard and what the lead is uncertain about. |

### 4.3 People-side substance (weight: 20%)

| Score | Description |
|---|---|
| 1 | People plan is generic — same template for every report. |
| 2 | Per-report plan exists but skips growth direction and feedback mechanism. |
| 3 | Per-report plan covers growth, feedback, and escalation. |
| 4 | Per-report plan plus departing-engineer playbook plus a documented approach to underperformance. |

### 4.4 Defensibility upward (weight: 15%)

| Score | Description |
|---|---|
| 1 | Roadmap is a project list; no narrative; no trade-off section. |
| 2 | Narrative exists but the trade-offs are vague ("we'll balance priorities"). |
| 3 | Roadmap has explicit trade-offs and a rejected-alternatives appendix. |
| 4 | Roadmap survives a hostile read: every "why aren't you doing X" has an answer already in the doc. |

### 4.5 Cross-team honesty (weight: 10%)

| Score | Description |
|---|---|
| 1 | Cross-team register is empty or only lists `out` commitments. |
| 2 | Register lists both `in` and `out` but doesn't distinguish hard / soft commitments. |
| 3 | Register distinguishes hard / soft / ask, with named owners. |
| 4 | Register tracks status and next-checkpoint, and is integrated into the roadmap and risk register. |

### 4.6 Scoring

- 18–20: capstone pass with distinction.
- 16–17: capstone pass.
- 13–15: revise and resubmit. Identify the lowest-scoring
  dimension and rework only that.
- < 13: portfolio is not yet at capstone level; return to the
  module material for the weakest area before re-attempting.

## 5. Common mistakes

These are the mistakes graders see repeatedly. None of them are
about prose quality; all of them are about how a lead thinks.

### 5.1 The five-module split brain

The most common capstone failure is producing five excellent
module-level artifacts that have not been reconciled. The roadmap
assumes a new hire is productive from week one; the onboarding plan
correctly says they take ten weeks to ramp. The people plan
schedules weekly 1:1s on Mondays; the operating doc puts sprint
planning on Mondays. These are not subtle — they appear in the first
read. The integration narrative is supposed to catch them.

### 5.2 The over-committed roadmap

The roadmap assumes 100% engineering capacity. Real capacity, after
on-call (typically 15–25% of an engineer-week during their week on
rotation), support and interruption load (typically 10–20% per
engineer), and meeting load (typically 10–15%), is closer to
50–70% for new feature work. A roadmap built on 100% capacity is
either lying to the manager chain or lying to the team.

A note on the percentages above: they are rules of thumb commonly
cited in engineering-management writing (see, e.g., Will Larson's
essays at <https://lethain.com/> and Camille Fournier's writing at
<https://skamille.medium.com/>) rather than constants from a single
official source. Capstone learners should refine them against their
own team's measured data — actual on-call interrupt counts, support
queue volume, and meeting load — rather than treating them as fixed.

### 5.3 The performance conversation gap

The people plan describes the standard case (engineer is doing
fine, growing as expected) but has no path for the
below-bar case. The grader will ask: what do you do in week three
if a report is clearly struggling? Capstones without an answer to
this question are deferring a hard conversation onto their future
self, which is the canonical lead failure mode.

### 5.4 Cross-team commitments that float

The cross-team register lists commitments but does not assign owners
on either side, or assigns owners without a next-checkpoint date.
Floating commitments degrade silently: nobody is responsible for
checking on them, so they only surface as a problem when the
counterparty team explicitly asks. The register is the artifact
that prevents this; if it does not have owners and dates, it is
decoration.

### 5.5 Onboarding plans that aren't followed

The 90-day plan is written but the lead has no calendar mechanism
for actually running it. Capstones often submit a beautiful
onboarding plan that has no associated lead actions — no calendar
hold for the week-four retro, no buddy assignment process, no
first-project queue. The plan is the artifact; the lead's calendar
is the implementation.

### 5.6 No personal first-90-day plan for the lead

The portfolio is for the team; the integration narrative often
omits the lead's own ramp-up. A new lead who does not have a plan
for *their own* first 90 days will commit to things they should
have deferred and will miss the meet-everyone-in-the-team-and-on-
adjacent-teams pass that is the highest-leverage thing they can do
in their first month.

### 5.7 Treating the capstone as a writing exercise

The portfolio is graded on whether it would work, not on whether
it reads well. A polished portfolio that crumbles on the first
"could a peer pick this up and run the team?" question scores worse
than a roughly-edited portfolio that survives the peer-read. The
grader bias is toward operational reality.

### 5.8 Compromise hiring under headcount pressure

A surprisingly common capstone failure is to write a hiring rubric
that holds the bar in principle but, in the integration narrative,
admit that the lead will lower the bar to fill the role this
quarter because the headcount expires. The cost of a compromise
hire compounds over years; the cost of a delayed hire compounds
over months. The portfolio should reflect this trade-off honestly,
which usually means deferring the hire.

### 5.9 No revision history

The portfolio reads as if it was written at one point in time and
never updated. Real lead artifacts are continuously revised; a
portfolio with no revision history is a portfolio the lead has
never operated. Even a synthetic revision history ("v0.1 — initial
draft, week 1; v0.2 — updated capacity after on-call load
recalibrated, week 4") tells the grader the lead is thinking
about iteration.

### 5.10 Magical thinking about cross-team incidents

The cross-team register assumes the counterparty team will deliver
on schedule. The roadmap depends on that delivery. There is no
mitigation. When the counterparty slips (they will; cross-team
slip is the modal case), the team's roadmap slips with no buffer.
The capstone-level approach is to either pull the dependency in
(do it on-team) or build a fallback that does not require the
counterparty's delivery.

## 6. References

The capstone draws on the five modules in the track. The module
solutions are the primary reference; this artifact integrates
their guidance rather than repeating it.

### Internal — module solutions in this repository

- `modules/mod-701-team-operations/SOLUTION.md` — operating
  rhythms, on-call shape, decision frameworks.
- `modules/mod-702-people-management/SOLUTION.md` — 1:1 cadence,
  growth conversations, performance handling.
- `modules/mod-703-project-roadmap/SOLUTION.md` — roadmap
  defense, capacity modeling, trade-off narrative.
- `modules/mod-704-cross-team-coordination/SOLUTION.md` —
  commitment register, dependency tracking, escalation.
- `modules/mod-705-hiring-onboarding/SOLUTION.md` — interview
  loops, debriefs, 90-day onboarding plans.

### Internal — track-level design rationale

- `SOLUTION_OVERVIEW.md` — the cross-cutting principles
  (defaults-that-survive-bad-days; decisions-explicit-and-revisitable;
  people-conversations-owned-not-delegated;
  defending-priority-upward-is-not-optional). The capstone is
  the practical exam for these principles.
- `LEARNING_GUIDE.md` — the recommended reading order for the
  track and the relationship between learning and solutions
  repos.

### Adjacent tracks (for learners going broader)

- `principal-engineer-solutions/SOLUTION_OVERVIEW.md` —
  technical force-multiplication; relevant if the capstone
  learner is a tech-lead-manager rather than a pure people lead.
- `principal-architect-solutions/SOLUTION_OVERVIEW.md` — org-
  change at scale; relevant for leads operating in larger orgs.
- `architect-solutions/projects/project-301/SOLUTION.md` —
  architectural leadership at the project level.

### External — primary sources useful at capstone altitude

The capstone tests the learner's ability to *select and adapt* a
framework, not to recite one. The following primary sources are
useful reference shapes — learners should link to them (and note the
adaptation they made for the AI infra team context) rather than
copying them wholesale:

- Will Larson, *An Elegant Puzzle: Systems of Engineering Management*
  — essays at <https://lethain.com/>; capacity modeling, on-call
  load, organizational structure at small-team altitude.
- Camille Fournier, *The Manager's Path* — author essays at
  <https://skamille.medium.com/>; first-line manager rituals,
  skip-levels, and performance conversations.
- Basecamp, *Shape Up* — <https://basecamp.com/shapeup>;
  appetite-based scoping, useful when adapting the roadmap-defense
  artifact away from sprint-based planning.
- John Doerr, *Measure What Matters* — <https://www.whatmatters.com/>;
  OKR mechanics, useful when the capstone roadmap uses OKRs as its
  outcome framing.
- Henrik Kniberg, *Scaling Agile @ Spotify* (the original "Spotify
  model" paper) —
  <https://blog.crisp.se/2012/11/14/henrikkniberg/scaling-agile-at-spotify>;
  the source of the squads/tribes/chapters/guilds vocabulary that is
  frequently misquoted in secondary write-ups.
- Project Management Institute, *RACI* responsibility-assignment
  reference — <https://www.pmi.org/>; the canonical source for
  Responsible / Accountable / Consulted / Informed framing used in
  the cross-team commitment register.
- Jorge Fioranelli, *Engineering Ladders* —
  <https://github.com/jorgef/engineeringladders>; a published,
  copy-adaptable leveling rubric appropriate for a small AI infra
  team that does not yet have its own.
- Progression.fyi public ladders archive —
  <https://www.progression.fyi/>; curated collection of public
  engineering ladders from companies of varying sizes, useful as
  comparative reading.
- Google SRE Book, on-call and toil chapters —
  <https://sre.google/sre-book/table-of-contents/>; the primary
  source for the 50%-toil / 25%-interrupt budgeting heuristics that
  capstone roadmaps often cite second-hand.

Other published frameworks (DACI, Shape Up variants, FAST, etc.) are
widely available; the requirement is that any external reference in
the learner's portfolio resolves to a primary source rather than a
secondary summary.

A note on citation quality: if a learner cites a specific external
framework as authoritative (e.g., a FAANG company's published
engineering ladder, or a specific blog post as the source of an
on-call rotation pattern), the citation should resolve to a primary
source. Citations to secondary summaries (roundup blog posts, slide
decks) are not sufficient at capstone level.

---

**Revision history**

- v0.1 — initial capstone solution authored as the integrating
  artifact across `mod-701`–`mod-705`.
