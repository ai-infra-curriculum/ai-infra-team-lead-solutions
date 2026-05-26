# SOLUTION_OVERVIEW — Team Lead Track

> Read this *after* you have skimmed the module solutions. This file
> explains the design philosophy across the team-lead track and how
> to read the deliverables.

## What this track is teaching

A team lead operates at the intersection of three pressures:

1. **The team** — keeping engineers productive, growing, and not
   burning out.
2. **The work** — landing the right things, in the right order, with
   measurable outcomes.
3. **The org** — translating between the team and the rest of the
   company.

Most failure modes for new leads are dropping one of the three. The
solutions in this track are deliberately structured around all three
simultaneously.

## How the modules relate

| Module | Pressure addressed |
|---|---|
| `mod-701-team-operations` | The work (rituals, on-call, planning cadence). |
| `mod-702-people-management` | The team (1:1s, performance, growth, hard conversations). |
| `mod-703-project-roadmap` | The work + the org (defending priorities upward). |
| `mod-704-cross-team-coordination` | The org (managing dependencies without owning them). |
| `mod-705-hiring-onboarding` | The team + the org (talent flow). |

Read in module order. The most common mistake is reading
`mod-702-people-management` first because it sounds most "leadership-y";
the operational discipline in `mod-701` is what creates the *space* to
do good people management. Without it, every 1:1 becomes a triage
meeting.

## How a "solution" looks in this track

A team-lead solution typically contains:

- **A template** — for a recurring artifact (1:1 agenda, sprint plan,
  hiring rubric, on-call schedule).
- **A worked example** — the template applied to a realistic
  scenario.
- **A discussion of failure modes** — what the template *doesn't*
  catch, when to abandon it, what to do when it goes sideways.

The closest analog elsewhere in the curriculum is the senior-engineer
and principal-engineer tracks — but those center on technical
leadership. This track centers on *team* leadership.

## Cross-cutting principles

### Defaults that survive bad days

A lead's best work is invisible: the systems they set up that produce
reasonable outcomes even when the lead (or anyone on the team) is
having a rough week. Most templates here are designed for
robustness on a bad day, not for elegance on a good one.

### Decisions explicit and revisitable

A team where decisions live in chat history will re-litigate them
every quarter. Solutions emphasize lightweight ADRs, written
operating decisions, and easy-to-find ownership.

### People conversations are owned, not delegated

Hiring, performance, and growth conversations cannot be outsourced to
HR. The solutions show what's the lead's job versus what's HR's job,
and what the lead must do even when HR has a process for it.

### Defending priority upward is not optional

A team lead who cannot defend the team's roadmap to higher-leveled
stakeholders becomes a transmission layer for shifting priorities.
The solutions in `mod-703` show how to disagree productively
without becoming an obstacle.

## What's deliberately *not* in this repo

- **Universal management frameworks** — this track is concrete and
  context-specific. Generic management content lives in many books
  already.
- **HR-policy templates** — your HR org has these; this track shows
  what a lead does *around* them.
- **Compensation philosophy** — outside the scope of a single
  team lead.

## Cross-references

| Topic | Deeper reference |
|---|---|
| Technical leadership (force-multiplication) | `principal-engineer-solutions/SOLUTION_OVERVIEW.md` |
| Architectural leadership | `architect-solutions/projects/project-301/SOLUTION.md` |
| Org-change at scale | `principal-architect-solutions/SOLUTION_OVERVIEW.md` |
| On-call patterns + incident response | `engineer-solutions/mod-108 exercise-09` |

## Time budget for the track

- **Surveyor read**: 1 week.
- **Practitioner read**: ongoing — these are templates you reuse,
  refine, and replace over a multi-year arc as a lead.
