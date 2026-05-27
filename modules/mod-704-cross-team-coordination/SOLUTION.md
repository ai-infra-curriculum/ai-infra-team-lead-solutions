# SOLUTION — Cross-Team Coordination

> Read this *after* you have attempted the deliverables. The
> "solutions" are coordination rubrics. This document explains
> *why* cross-team coordination at the team-lead level is its own
> skill — distinct from both the principal-engineer's cross-org
> initiative work and from internal team operations.

## What this module is really teaching

When your team's work touches other teams, you've inherited a
coordination problem. The team-lead version is smaller than the
principal-engineer's cross-org initiative — fewer teams, less
political weight required — but it shows up far more often.

The truths the module teaches:

1. **Most cross-team problems are coordination problems
   pretending to be technical problems.** "Their API doesn't
   support our use case" is usually solvable; the team-lead's
   job is to make that conversation happen.
2. **Adjacent teams are not your enemies.** They're your peers
   with different incentives. Coordination is about finding
   the seam where both teams' incentives align.
3. **Async coordination beats meeting coordination at scale.**
   Once you have 5+ teams in the loop, synchronous coordination
   collapses. Async docs + clear decisions become essential.
4. **The interface is the contract.** Cross-team work
   succeeds when the interface between teams is well-defined
   and stable; it fails when the interface is implicit.
5. **Coordination decays.** A coordination that worked last
   quarter requires maintenance to keep working this quarter.

## What the deliverables should actually look like

### Case study (exercise 01): a coordination story

Pick a known coordination challenge:

- **Two teams shipping an integration** that worked or
  didn't. What did they get right?
- **A platform team and a consuming team** that had a long-
  running interface mismatch. How did it resolve?
- **A migration that crossed teams** — both teams had to move
  in lockstep. What happened when one fell behind?

Analyze:
- The **interface** between teams: was it explicit? When did
  it get formalized?
- The **incentive alignment**: did both teams benefit, or was
  one carrying the other?
- The **communication cadence**: was it weekly check-ins,
  monthly reviews, ad-hoc?
- The **escalation path**: when teams disagreed, who decided?

Common failure modes:
- **Single-team postmortems**: most published postmortems
  cover one team. Cross-team postmortems are rare and
  unusually valuable.
- **Hero-dependent fixes**: "X heroically aligned the
  teams." Not a system, not transferable.

### The cross-team contract (exercise 02)

When two teams' work integrates, the team leads should jointly
own a **cross-team contract**:

1. **Scope**: what's the integration? In one paragraph.
2. **Owner per team**: who decides on each side?
3. **The interface**: API, data format, schedule — whatever
   the integration is built on.
4. **The cadence**: how often do we sync? Weekly is the
   common default; biweekly if the work is mature.
5. **The escalation**: who decides if we disagree? (Usually
   our shared manager.)
6. **The lifecycle**: when does this contract get reviewed?
   What ends it?

This is a one-page doc, jointly owned. Both team leads sign
off. It lives somewhere both teams can find it.

Common failure modes:
- **Verbal-only contracts**: 3 months in, the original
  agreement has been remembered differently by each side.
- **No named owners**: requests fall into a black hole.
- **No review cadence**: the contract gets stale; reality
  diverges.

### Stakeholder mapping (exercise 03): the network of teams

For cross-team work at the team-lead altitude, the
stakeholder map is mostly **other team leads**. Per other team:

- **Their team lead**: your peer; the primary contact.
- **Their senior engineers**: the technical co-owners.
- **Their manager (your peer-manager)**: the escalation if
  team-lead-to-team-lead doesn't resolve.
- **Their PM, if they have one**: roadmap impact.

The map's value is **knowing who to talk to about what**.
For technical clarification, talk to their senior engineers.
For schedule or priority, talk to their team lead. For
unresolvable conflict, escalate to the shared manager.

Common failure modes:
- **Going to the engineer instead of the lead** for
  schedule/priority — produces commitments the lead doesn't
  honor.
- **Going to the lead for technical detail** — slow and
  often inaccurate.
- **Escalating too early** — peer-manager intervention should
  be the exception, not the default.

### Roadmap (exercise 04): the joint plan

When two teams' work depends on each other, the roadmap
should be **jointly visible**:

| Quarter | Team A | Team B | Dependency point |
|---|---|---|---|
| Q1 | API v2 design | Consumer prototyping | API draft by mid-quarter |
| Q2 | API v2 implementation | Migration of read paths | API beta available |
| Q3 | API v2 GA | Full migration | API v1 deprecation |
| Q4 | API v1 removed | All paths on v2 | Final cleanup |

The joint roadmap forces both teams to surface their
dependencies on each other publicly. Surprises about timing
become rare.

Common failure modes:
- **Each team has its own roadmap, dependencies are implicit**:
  the dependency point falls in a gap.
- **Joint roadmap but no joint review**: the doc exists but
  isn't checked; both teams drift.
- **No deprecation in the joint plan**: the old system never
  gets retired.

### The cross-team review (exercise 05)

A recurring cross-team review (monthly is the common
cadence) covers:

1. **Where are we on the integration?**
2. **What's at risk?**
3. **What do we need from each other?**
4. **Any incidents or surprises since last review?**

Both team leads should be present. Engineers from both teams
should attend if there's substantive technical work. The
review's output is **decisions and follow-ups**, not status
updates.

Common failure modes:
- **Review becomes status update**: no decisions, no follow-
  ups. Drop it or shrink it.
- **One team dominates**: usually the platform team
  patronizing the consumer team. Watch for this.
- **No retro**: the cross-team interface that worked for 6
  months should be reviewed; what's still serving us?

## Trade-offs we deliberately accepted

### Two-team focus

The exercises target 2-4 team coordination, which is the
common case. Larger coordination (10+ teams) is more like a
program management problem and lives in mod-503 (cross-org).

### Manager-up assumed

The framework assumes both team leads have a shared manager
or VP within 1-2 levels who can adjudicate. Coordinations
that cross organizational boundaries (different VPs,
different orgs) have different dynamics and benefit from
principal-engineer or principal-architect involvement.

### Tooling-agnostic

The rubric works with Slack channels, Linear/Jira projects,
shared docs, or whatever your org uses. The principles
(written interface, regular review, clear escalation) are
universal.

## Common mistakes graders see

1. **Implicit interfaces**: "they'll know what we mean."
   They won't. Write it down.
2. **No regular review**: cross-team coordination decays
   without maintenance.
3. **Escalating prematurely**: bringing the manager in
   before exhausting peer-to-peer options burns political
   capital and trust.
4. **Treating the platform team as a vendor**: leads to
   demand without partnership. Platform teams have their own
   constraints; treating them as a contracted service breaks
   the relationship.
5. **No retro after a milestone**: cross-team work is
   high-stakes; the lessons should be captured.
6. **Roadmap mismatch detected late**: the moment you notice
   your team's plan depends on their plan in a way you
   hadn't verified, surface it immediately. Late surfacing
   is much more painful than early.

## When to go beyond this module

- Take a real cross-team relationship you own. Where's the
  written contract? When was it last reviewed?
- Sit in on a **cross-team review** that's known to work
  well. The facilitation patterns are the curriculum.
- Cross-reference the **principal-engineer mod-503** for
  larger-scale coordination patterns.

## Related curriculum touchpoints

- `team-lead/mod-701-team-operations` — the team operations
  the cross-team coordination plugs into.
- `team-lead/mod-703-project-roadmap` — the planning
  artifact that surfaces cross-team dependencies.
- `principal-engineer/mod-503-cross-org-initiative` — the
  larger-scale version of the same problem.
- `principal-architect/mod-604-stakeholder-coalition` — the
  political execution at scale.
