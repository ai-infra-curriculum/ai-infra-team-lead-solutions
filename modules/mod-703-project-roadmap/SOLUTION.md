# SOLUTION — Project Roadmap

> Read this *after* you have attempted the deliverables. The
> "solutions" are roadmap rubrics, not code. This document
> explains *why* team-level roadmapping is harder than it
> looks and where most team leads get it wrong.

## What this module is really teaching

A team-level roadmap is the artifact most often produced and
least often well done. The reasons:

- Engineers default to **bottom-up** roadmaps that list tasks.
- Leadership defaults to **top-down** mandates that ignore
  capacity.
- The team lead's job is the **synthesis** that neither side
  produces on its own.

A good roadmap is not a Gantt chart. It is a **negotiated
commitment** between the team, leadership, and dependent teams
about what will be done by when, with explicit acknowledgement
of what won't.

The truths the module teaches:

1. **A roadmap without confidence levels is fiction.** Every
   commitment has a probability; pretending otherwise produces
   surprise misses.
2. **Capacity is finite and lumpy.** Team velocity is not a
   single number — it varies with on-call, vacation, new hires,
   incidents.
3. **The roadmap is a communication artifact, not a planning
   artifact.** The plan is in the team's head; the roadmap is
   how the team communicates the plan to the rest of the
   world.
4. **Replanning is the rule, not the exception.** A roadmap
   that doesn't get revised has stopped reflecting reality.
5. **The most important question is "what are we NOT doing?"**
   Roadmaps that don't surface the cuts are dishonest.

## What the deliverables should actually look like

### Case study (exercise 01): a roadmap that succeeded or failed

Pick a public roadmap exposed in a postmortem, retro, or
engineering blog. Examples:

- An infrastructure migration that landed on time (rare; the
  reasons it worked are instructive).
- A product launch that slipped multiple quarters (more
  common; the reasons usually predictable in hindsight).
- A team that consistently lands ~90% of roadmap items (what
  makes them different?).

Analyze:
- The **estimation discipline**: how were estimates produced?
  Bottom-up? Reference class?
- The **buffer**: was unallocated time visible in the plan?
- The **kill criteria**: when did things get cut, and how?
- The **replanning cadence**: did they revisit the roadmap as
  it slipped, or pretend nothing changed?

Common failure modes:
- **Survivorship in retrospective accounts**: postmortems are
  usually written about failures; successes go un-documented.
- **Conflating individual heroics with system success**: a
  roadmap that lands because two engineers worked weekends
  isn't a system, it's a personnel failure waiting to happen.

### The roadmap (exercise 02): the artifact itself

A team's quarterly roadmap should fit on one page. Structure:

1. **Goals (3-5)**, stated as outcomes with measurable
   targets.
2. **Confidence** per goal (high / medium / low) — be
   honest.
3. **Major work streams** with rough timing (which weeks,
   which engineers).
4. **Dependencies** — what we need from whom, when.
5. **Risks** — what could derail us.
6. **Stretch goals** — what we'd do if main goals land
   early.
7. **What we're NOT doing this quarter** — explicit cuts
   and rationale.

The "what we're NOT doing" section is the most often
omitted. Without it, every adjacent team interprets the
roadmap as "you'll have time to do my thing too."

Common failure modes:
- **More than 5 goals**: signal that the team is committing to
  everything, which means committing to nothing in
  particular.
- **Goals stated as activities** ("work on inference
  optimization") rather than outcomes ("inference p99 < 200ms
  at 10k QPS").
- **No risks section**: makes leadership think it's smooth
  sailing; reality surfaces only on miss.
- **No explicit cuts**: every team in the org thinks they're
  on the list.

### Estimation discipline (exercise 03)

Estimates at the team-lead level should be:

1. **Reference-class first** — find a similar past project,
   start from its actual duration.
2. **Three-point** when uncertainty is high — best /
   expected / worst case, with reasons for each.
3. **Plus 30% buffer** for the integration / polish work
   that consistently takes longer than expected.
4. **Plus team-specific multipliers** for new hires (slower
   first 6 months), on-call (10-20% capacity tax), interrupts
   (10-30% depending on team).

The estimate is a **probabilistic commitment**, not a
deadline. If you can't say "we're 80% confident we hit this,
60% confident on this stretch," your estimates aren't
calibrated.

Common failure modes:
- **Best-case estimation**: everyone's best-case estimate
  compounds into a roadmap that slips on day one.
- **No reference class**: estimating from scratch each time.
- **Estimates without uncertainty**: precision implies
  confidence that doesn't exist.

### Stakeholder mapping (exercise 04): the dependent teams

For a roadmap, the stakeholders are:

- **Upward**: my manager, leadership. They need confidence
  levels and risks.
- **Sideways**: teams that depend on us, or that we depend
  on. They need timing and interfaces.
- **Inward**: the team itself. They need clarity on what's
  in, what's out, what's stretch.
- **Customers**: people who use the team's output.

Each gets a different version of the roadmap:
- Leadership: 1-pager with confidence and asks.
- Adjacent teams: detail on the interfaces and timing of
  their dependencies.
- The team: full detail.
- Customers: outcome timing, no internal jargon.

Common failure modes:
- **One roadmap to rule them all**: a single artifact tries
  to serve all audiences and serves none well.
- **No adjacent-team review**: dependencies surface as
  surprises mid-quarter.

### The roadmap review (exercise 05)

A monthly or quarterly roadmap review is the synchronization
ritual. It covers:

1. **What we shipped** vs. what we planned.
2. **What slipped, why, and what we did about it.**
3. **Current confidence in remaining goals.**
4. **Asks**: anything we need to unblock.

Common failure modes:
- **Status theater**: heavy slides, no actual updates on
  uncertainty.
- **Defensiveness about slips**: leadership respects honest
  reporting; they punish surprises later.
- **No ask**: if you're not asking for anything, why is
  leadership in the meeting?

## Trade-offs we deliberately accepted

### Quarterly cadence as the default

Some teams plan in 6-week shapes (Shape Up) or 2-week sprints
without quarterly bundling. The principles transfer. The
exercises bias toward quarterly because that's the most
common cadence in the AI infra space.

### Outcome-stated goals

The bias toward outcomes ("p99 < 200ms") rather than
activities ("work on perf") is deliberate. Activity-stated
goals can't be falsified — the team "worked on" perf no
matter what.

### OKR-adjacent framing

The rubric is compatible with OKRs but doesn't require them.
OKR theater is its own failure mode; if your org has it,
adapt the rubric to look OKR-like; if not, don't add
ceremony for its own sake.

## Common mistakes graders see

1. **Estimating without uncertainty**: produces precise
   deadlines that miss.
2. **Roadmaps that don't revise**: monthly roadmap reviews
   that say "still on track" for 12 weeks straight, then a
   surprise miss.
3. **No what-we're-not-doing section**: everyone in the org
   thinks their request is on the list.
4. **Replanning by extension**: pushing dates without cutting
   scope. Eventually the team is committed to a year of work
   in a quarter.
5. **Hero-dependent estimates**: "if Alice can crank for two
   weeks we'll make it." Alice gets sick, the plan fails.
6. **Roadmaps that ignore on-call**: a team with 25% on-call
   load that estimates as if at 100% capacity slips
   consistently.

## When to go beyond this module

- Take a real team roadmap and run the rubric against it.
  Where's the uncertainty? Where are the implicit cuts?
- Sit in on a **roadmap planning meeting** at a team known
  for honest planning. The conversation patterns are the
  curriculum.
- Cross-reference the **principal-architect mod-603** for the
  multi-year-investment view of roadmapping.

## Related curriculum touchpoints

- `team-lead/mod-701-team-operations` — the operational
  cadence the roadmap lives in.
- `team-lead/mod-704-cross-team-coordination` — the
  cross-team integration the roadmap surfaces.
- `principal-engineer/mod-501-technical-strategy` — the
  strategic frame the roadmap executes against.
- `principal-architect/mod-603-multi-year-investment` — the
  multi-year horizon the quarterly roadmap aggregates into.
