# SOLUTION — Team Operations

> Read this *after* you have attempted the deliverables. The
> "solutions" are operational rubrics. This document explains
> *why* team operations is the foundation skill of leadership and
> what the right defaults look like for an AI infra team.

## What this module is really teaching

Team operations is the unglamorous bedrock. New team leads
underestimate how much it matters because the work is invisible
when done well — the team just ships, on-call is calm,
everyone knows what's going on. The signal that it's *not* done
well is loud: missed deadlines, repeated re-planning, on-call
burnout, ambiguous ownership.

The truths the module teaches:

1. **Operations is a system, not a personality.** Good ops
   doesn't depend on the lead being a "good manager"; it
   depends on the rituals being in place.
2. **The defaults are mostly known.** Standups, 1-1s, sprint
   planning, retros — these aren't novel ideas. The skill is
   knowing which to keep, which to skip, and how to run each
   one well.
3. **AI infra teams have specific operational needs.** The
   workloads are GPU-expensive, model-training is bursty,
   incidents have different shapes than regular SRE incidents.
   Generic agile doesn't fit perfectly.
4. **The team's operating rhythm should match the team's
   work.** A platform team that ships every two weeks has a
   different cadence than a research team that runs 6-week
   experiments.
5. **Documentation is operations.** Decisions, on-call
   runbooks, postmortems — if they're not written down, they're
   not transferable.

## What the operational deliverables should actually look like

### Case study (exercise 01): a team operation pattern

Pick a team operation pattern that's documented somewhere
(GitHub, GitLab, Basecamp, Stripe engineering blogs). Analyze:

- What rituals does the team run?
- What rituals do they explicitly *not* run?
- How does the cadence match the work?
- What's the failure mode when their pattern is misapplied?

Good case studies surface the **specificity** of the pattern.
Basecamp's "shape up" methodology works for Basecamp because
Basecamp's product cadence and team size match it. Applied
verbatim to a 200-engineer team with quarterly OKR cycles, it
fails. Patterns transfer with adaptation.

Common failure modes:
- **Cargo-culting the most-blogged-about pattern**: "we'll do
  what Spotify does" — Spotify itself moved on from the model
  in 2018 but the blog post remains.
- **Treating a pattern as a complete system**: every team
  operation pattern leaves out things that need to be
  added back in.

### The team operating doc (exercise 02)

The team operating doc is the artifact that every new hire
should read on day 1. It includes:

1. **The team's mission** — one sentence; what problem do we
   own?
2. **The team's scope** — what's in, what's out.
3. **The operating rhythm** — what we do daily, weekly,
   monthly, quarterly. Be specific (Monday 10am sprint
   planning, Friday 4pm retros, etc.).
4. **The roles** — who owns what? Not titles — actual
   responsibilities.
5. **The communication channels** — Slack channels, mailing
   lists, paging tools. When to use each.
6. **The on-call shape** — rotation, escalation, handoff.
7. **The decision-making framework** — when do we vote, when
   does the tech lead decide, when does the team lead decide,
   when does it escalate?
8. **The documentation expectations** — what gets written
   down, where, and when.

The doc should be **one page or less**. Long docs don't get
read; they become aspirational.

Common failure modes:
- **No doc at all**: the team's operations are tribal
  knowledge. New hires take 3 months to become productive.
- **Five-page doc with everything in it**: nobody reads it.
- **Doc that doesn't match reality**: written 18 months ago,
  rituals have drifted, nobody noticed.

### Stakeholder mapping (exercise 03): the team's interfaces

The team-lead's stakeholder map is **inward-facing** plus
**outward-facing**:

- **Inward**: each direct report. What do they need from me?
  What do they need from each other?
- **Adjacent teams**: who do we depend on, who depends on us?
- **Up the chain**: my manager, their manager, the eng leadership.
- **Customers**: who uses the team's output?

Each stakeholder gets a **cadence**: 1-1s weekly with reports,
1-1s biweekly with adjacent leads, monthly check-in with the
team's primary customers, etc.

Common failure modes:
- **No regular touchpoints with adjacent teams**: dependencies
  surface as surprises.
- **No regular touchpoints with customers**: the team builds
  what it thinks is needed, not what is needed.

### Roadmap (exercise 04): the team's quarterly plan

A team-lead-owned quarterly roadmap covers:

1. **Goals** — 3-5 outcomes for the quarter. State them as
   outcomes, not activities. "Reduce p99 inference latency
   under 200ms" not "work on inference latency."
2. **Confidence** — how confident are we in each goal?
   (High / medium / low.) Be honest.
3. **The work breakdown** — which engineers, what stretches,
   estimated effort.
4. **Risks and dependencies** — what could go wrong, what do
   we depend on others for?
5. **Stretch goals** — what would we tackle if the main goals
   land early?

The roadmap should be reviewed monthly and re-planned at the
quarter break. Roadmaps that stay static for 12 weeks have
already drifted from reality.

Common failure modes:
- **Goals stated as activities**: "build feature X" doesn't
  tell you if you're done.
- **No confidence assessment**: low-confidence goals are not
  failures when they slip; they're learnings.
- **No stretch goals**: a team that lands all main goals at
  60% of the quarter has under-committed.

### Presentation (exercise 05): the team review

A monthly or quarterly team review with leadership covers:

1. **What we shipped** — concrete outcomes, with metrics.
2. **What we learned** — what surprised us, what we'd do
   differently.
3. **What's at risk** — what might miss, why, what we need.
4. **The ask** — what do we need from leadership? (Headcount,
   priorities, decisions.)

Common failure modes:
- **All shipped, nothing at risk**: leadership doesn't
  believe it. Be honest about the risks.
- **Long status updates without asks**: leadership's time is
  best used unblocking; if you're not asking for anything,
  why are you in the room?

## Trade-offs we deliberately accepted

### Agile-adjacent assumptions

The rubrics assume a roughly agile cadence (sprints, retros,
1-1s). Teams running waterfall, Shape Up, or pure
research-cycle workflows can adapt. The principles (clear
ownership, regular reflection, written decisions) are
universal.

### English-speaking corporate norms

Cadence and formality expectations vary by culture. Adapt.

### AI infra context

Some specifics are AI-infra-flavored (GPU capacity planning,
model rollout reviews, eval cadence). The structural rubric
applies to non-AI engineering teams too.

## Common mistakes graders see

1. **No retros, or retros without action items**: the team
   talks about problems but never fixes them.
2. **1-1s that become status updates**: 1-1s should be the
   report's agenda, not the manager's. If you're talking
   project status, do it elsewhere.
3. **Sprint planning without capacity awareness**: planning
   8 stories for a 4-person team in a 2-week sprint when one
   person is on call and one is on vacation produces
   predictable failure.
4. **On-call without clear escalation**: the on-call engineer
   doesn't know who to call when they're stuck. Document the
   escalation path.
5. **No documentation of decisions**: 3 months later, "why did
   we choose X?" is unanswerable; the team re-litigates the
   decision.
6. **Goals that are commitments to leadership but not to the
   team**: the team doesn't internalize the goal because they
   weren't part of writing it. Co-write.

## When to go beyond this module

- Take a real team's operating doc (yours or one a colleague
  shares) and run the rubric against it. What's missing?
  What's too much?
- Sit in on a **retro** at a team known for good ops. The
  difference between an effective retro and a checkbox retro
  is mostly the facilitation.
- Cross-reference the **mlops / engineer tracks** — they cover
  the technical SRE practices that team ops sits on top of.

## Related curriculum touchpoints

- `team-lead/mod-702-people-management` — the people side of
  the operating rhythm.
- `team-lead/mod-703-project-roadmap` — the planning artifact.
- `team-lead/mod-704-cross-team-coordination` — the outward-
  facing ops.
- `principal-engineer/mod-502-mentorship-leadership` — the
  staff-IC perspective on the same team.
