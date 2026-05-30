# SOLUTION — project-01-team-process

> Capstone-grade reference solution for the team-process project in
> [`ai-infra-team-lead-learning`](https://github.com/ai-infra-curriculum/ai-infra-team-lead-learning).
> Read *after* attempting the project. The "solution" here is a
> rubric and worked example, not a script to copy-paste.

Paired learning project: `projects/project-01-team-process` in the
team-lead learning repo. Confirm the paired learning README before
treating this document as authoritative; if the learning project's
scope drifts, this solution should be updated alongside it.
<!-- editorial note: confirm paired learning project slug and scope statement in ai-infra-team-lead-learning. -->

## 1. Solution overview

### What the project is

`project-01-team-process` is the team-lead track's first capstone:
the deliverable a newly promoted (or newly-arrived) lead would
produce in their first 30–60 days to *make the team's process
legible*. It is not a process-redesign exercise; it is an
**operating-state audit + minimum-viable-rhythm proposal** that the
team itself can ratify.

The capstone integrates three module-level skills:

| Module | What this project pulls from it |
|---|---|
| [`mod-701-team-operations`](../../modules/mod-701-team-operations/SOLUTION.md) | The operating rhythm, on-call shape, decision-making framework. |
| [`mod-702-people-management`](../../modules/mod-702-people-management/SOLUTION.md) | 1:1 cadence, growth-conversation hooks, performance signals. |
| [`mod-704-cross-team-coordination`](../../modules/mod-704-cross-team-coordination/SOLUTION.md) | Adjacent-team interfaces, commitment register, escalation. |

### What the deliverable looks like

A reference submission is a **single repository** (or shared doc
set) containing:

1. **`TEAM_OPERATING_DOC.md`** — the one-page team operating doc
   (mission, scope, rituals, roles, on-call, decision rules,
   doc expectations). See `mod-701` SOLUTION § "The team operating
   doc" for the rubric.
2. **`RITUAL_CALENDAR.md`** — concrete weekly/biweekly/monthly
   cadence with day, time, owner, expected duration, and
   stop-the-meeting condition for each ritual.
3. **`ONCALL.md`** — rotation shape, primary/secondary, escalation
   path, handoff format, severity definitions, and the "what
   pages whom for what" table.
4. **`DECISIONS/`** — at least three lightweight ADRs (Architecture
   Decision Records — Michael Nygard's original format is the
   most-cited reference) that capture decisions the team has
   already made implicitly. ADRs are *retrospective* for the
   capstone: the point is to externalize tribal knowledge, not
   to invent new decisions.
5. **`STAKEHOLDER_MAP.md`** — inward + outward + upward
   stakeholders with cadence per stakeholder.
6. **`AUDIT.md`** — a 1–2 page honest assessment: what the team
   currently does, what it doesn't, what the lead recommends
   changing, and the order they intend to change things. The
   audit is what makes this a capstone rather than a template
   fill-in.

The capstone is **not** a redesign. New leads who arrive and
rewrite everything in the first month tend to destroy the
implicit knowledge that was holding the team together. The
correct shape of this deliverable is:

- 70% **document what already exists** (rituals, decisions,
  ownership).
- 20% **fix what is obviously broken** (missing on-call
  escalation, no retros, undocumented critical decisions).
- 10% **propose** (with the team) one or two changes to trial in
  the next quarter.

That 70/20/10 split is the heuristic that separates a useful
capstone from a destructive one.

### What the grader is checking

The grader reads the deliverable looking for three signals:

1. **Did the lead listen first?** The artifacts should reflect
   what the team actually does, not what the lead wishes they
   did. Evidence: rituals are named the way the team names them;
   ADRs reference decisions made before the lead arrived.
2. **Is the proposed change small enough to actually happen?**
   Capstones that propose 12 simultaneous changes fail in
   practice. The grader looks for one or two changes with a
   trial period and a success/abandon criterion.
3. **Does the lead understand which artifacts are load-bearing?**
   The team operating doc, on-call escalation, and decision
   record are non-negotiable. Calendar prettiness, color-coding,
   and Notion-template polish are not.

## 2. Worked answer or implementation

This worked example is a *shape*, not a real team. Do not treat
the numbers as benchmarks — they are placeholders illustrating
the structure. A real submission must fill these in from the
candidate's actual (or scenario-provided) team.

### 2.1 `TEAM_OPERATING_DOC.md` — worked shape

```markdown
# <Team Name> — Operating Doc

**Last reviewed:** YYYY-MM-DD
**Owner:** <team-lead handle>

## Mission
One sentence. What problem does this team own?

## Scope
- In: <bullet list>
- Out: <bullet list — explicit non-goals>

## Operating rhythm

| Cadence  | Ritual                | Day / time           | Duration | Owner   |
|----------|-----------------------|----------------------|----------|---------|
| Daily    | Async standup (Slack) | by 10:30 local       | 5 min    | Each    |
| Weekly   | Sprint planning       | Mon 10:00            | 45 min   | TL      |
| Weekly   | 1:1s                  | per-pair             | 30 min   | TL      |
| Biweekly | Retro                 | every other Fri 15:00 | 45 min  | Rotates |
| Monthly  | Roadmap review        | first Wed 14:00      | 60 min   | TL      |
| Quarterly| Planning              | week 13              | 1/2 day  | TL      |

Stop-the-meeting condition: any ritual that lands "no action,
nothing surprising" three times in a row is up for cancellation
at the next retro.

## Roles
- TL — <responsibilities, not titles>
- Tech Lead — <responsibilities>
- On-call primary — <responsibilities>
- Project lead (rotates) — <responsibilities>

## Communication channels
- `#team-foo` — async work, default channel.
- `#team-foo-alerts` — paging only.
- `#team-foo-social` — opt-in.
- Email — external stakeholders only.

## Decision-making
- Reversible technical: tech lead decides, ADR if non-obvious.
- Irreversible technical: team consensus, ADR required.
- Process / cadence: team lead proposes, team ratifies at retro.
- Headcount / cross-team commitments: team lead, escalated up.

## Documentation expectations
- Decisions: ADR in `DECISIONS/` within 1 week of the decision.
- Incidents: postmortem within 5 business days.
- On-call handoff: written, in `#team-foo`, every Monday.
- Runbooks: in `runbooks/`, updated within the same PR as the
  code change that invalidates them.
```

This document is intentionally **one page**. The single-page
constraint is the discipline; longer docs become aspirational
and are not read.

### 2.2 `RITUAL_CALENDAR.md` — worked shape

```markdown
# Ritual Calendar

| Ritual             | Cadence  | When            | Length | Owner   | Stop condition |
|--------------------|----------|-----------------|--------|---------|----------------|
| Async standup      | Daily    | by 10:30 local  | 5 min  | All     | n/a, low cost |
| Sprint planning    | Weekly   | Mon 10:00       | 45 min | TL      | If backlog is empty 2 weeks running, switch to biweekly. |
| 1:1                | Weekly   | per-pair        | 30 min | TL      | Never cancel; reschedule. |
| Retro              | Biweekly | Fri 15:00       | 45 min | Rotates | If 2 consecutive retros yield zero action items, audit format. |
| Roadmap review     | Monthly  | first Wed 14:00 | 60 min | TL      | If roadmap unchanged 2 months running, switch to quarterly. |
| Quarterly planning | Quarterly| week 13         | 1/2 day| TL      | Permanent. |
```

The point of the "stop condition" column is to make it cheap to
cancel rituals that are no longer earning their keep. Most teams
accumulate rituals because adding is easy and removing is
political; making the abandon-criterion explicit at design time
makes removal procedural.

### 2.3 `ONCALL.md` — worked shape

```markdown
# On-Call

## Rotation
- One-week rotations, Monday handoff, primary + secondary.
- Rotation order is published one quarter ahead.
- Trades are allowed; the trade must be recorded in `#team-foo`
  and PagerDuty (or equivalent) before the rotation starts.

## Severity
- SEV-1: customer-facing outage or data loss risk. Page.
- SEV-2: degraded service, no data loss. Page during business
  hours, ticket out-of-hours.
- SEV-3: internal-only, low urgency. Ticket only.

## Escalation
1. On-call primary acknowledges within <ack target>.
2. If primary cannot resolve within <escalation target>,
   secondary joins.
3. If secondary cannot resolve, escalate to <named adjacent
   on-call> for <listed system boundary>.
4. SEV-1 spanning >1 hour pages the team lead.

(Ack and escalation targets must match the team's actual
SLO commitments and the org's incident-management policy.
Cite the SLO doc, do not invent targets.)
<!-- editorial note: confirm org-wide ack / escalation target
     policy before publishing as canonical for the team. -->

## Handoff format
- Monday standup post in `#team-foo`:
  - Open incidents at start of shift.
  - Pager noise count (number of pages, signal vs. noise).
  - Anything the incoming on-call should watch.

## Runbook expectations
- Every alert that has paged twice must have a runbook entry.
- Runbooks live in `runbooks/<alert-name>.md`.
- The on-call updates the runbook in the same PR that fixes the
  underlying issue (or files a follow-up if not fixed yet).
```

The single most-load-bearing element is the **escalation table**.
A new on-call engineer at 2am needs to know exactly who to call
for a problem outside their system. If that information is not
written down, the rotation is effectively staffed by whoever
happens to know the right phone numbers.

### 2.4 `DECISIONS/` — worked ADR shape

Use Michael Nygard's lightweight format (the most widely-cited
ADR template). One file per decision:

```markdown
# ADR-NNNN — <Short title>

- **Status:** Accepted | Superseded by ADR-NNNN | Deprecated
- **Date:** YYYY-MM-DD
- **Deciders:** <names / roles>

## Context
<What was the situation? What forces were in play?>

## Decision
<What we decided. One paragraph.>

## Consequences
- Positive: ...
- Negative: ...
- Neutral / follow-ups: ...
```

For the capstone, write at least three ADRs that **document
decisions already made implicitly** — for example, "we standardize
on framework X for training pipelines," "we keep model
evaluations off the critical-path CI," "we own model rollout but
not feature-flag plumbing." The point of the exercise is to
surface tribal knowledge into a reviewable artifact, not to
invent new decisions during the capstone.

### 2.5 `STAKEHOLDER_MAP.md` — worked shape

```markdown
# Stakeholder Map

## Inward (direct reports)
| Person | Cadence | Primary topic | Notes |
|--------|---------|---------------|-------|
| A      | weekly  | growth, project X | new to senior level |
| B      | weekly  | scope, on-call load | considering staff path |
| ...    |         |               |       |

## Adjacent teams
| Team | Cadence | Forum | Surface area |
|------|---------|-------|--------------|
| Training infra | biweekly TL 1:1 | Slack DM | shared GPU pool, rollout coordination |
| Eval | monthly sync | meeting | eval pipeline ownership boundary |
| Product | biweekly | meeting | roadmap inputs |
| ...  |          |       |              |

## Upward
| Stakeholder | Cadence | Forum | What they want |
|-------------|---------|-------|----------------|
| Eng manager | weekly 1:1 | meeting | risk + ask |
| Director    | monthly review | meeting | shipped + at-risk |
| ...         |         |       |                |

## Customers (downstream consumers)
| Customer | Cadence | Forum | What we promise them |
|----------|---------|-------|----------------------|
| Inference team | monthly | meeting | <SLA / SLOs by name> |
| ...      |         |       |                      |
```

Each adjacent-team and upward stakeholder must have a **named
cadence**. The most common failure is "we'll sync as needed,"
which decays to "we sync when something breaks." A standing
biweekly is cheap to cancel and expensive to forget.

### 2.6 `AUDIT.md` — worked shape

This is the artifact that distinguishes a capstone from a
template fill-in. Recommended structure:

```markdown
# Team-Process Audit — <YYYY-MM-DD>

## Method
- Period observed: <e.g. weeks 1–4>.
- Sources: standups, retros, 1:1 themes, incident channel,
  PR review history, last quarter's planning artifacts.
- I did NOT survey, change cadence, or propose new rituals
  before producing this audit. (Listen before acting.)

## What the team does today
- Rituals actually run: <list, with frequency observed>.
- Rituals nominally scheduled but routinely skipped: <list>.
- Decisions made but not documented: <list>.
- On-call: <shape, gaps>.

## What's working
- <2-4 items, with evidence>

## What's broken
- <2-4 items, with evidence and severity>
  - Severity = "fix this quarter" vs. "next quarter" vs.
    "monitor, not yet a problem."

## Proposed changes (next 90 days)
1. <Change 1>
   - Trial period: <duration>.
   - Success criterion: <observable>.
   - Abandon criterion: <observable>.
2. <Change 2 — at most one or two more>

## Explicit non-changes
Things I considered changing and decided to leave alone, with
reason. This list is as important as the change list — it shows
the grader that the lead chose restraint.
```

The "explicit non-changes" section is the most under-used
element of a good audit. Listing the things you decided not to
touch demonstrates judgment more clearly than the things you
decided to touch.

## 3. Validation steps

Before submitting the capstone (or grading it), the deliverable
should pass each of these checks. Run them locally, then have a
trusted reader run them blind.

### 3.1 Structural validation

- [ ] All six required artifacts are present (`TEAM_OPERATING_DOC`,
      `RITUAL_CALENDAR`, `ONCALL`, `DECISIONS/`, `STAKEHOLDER_MAP`,
      `AUDIT`).
- [ ] `TEAM_OPERATING_DOC.md` is one page or less when rendered.
- [ ] At least three ADRs in `DECISIONS/`, each using a consistent
      format (Nygard ADR template or equivalent), each with a
      `Status` field that is one of {Proposed, Accepted,
      Superseded, Deprecated}.
- [ ] Every ritual in `RITUAL_CALENDAR.md` has an owner and a
      stop-the-meeting condition.
- [ ] `ONCALL.md` has an escalation table that names a specific
      adjacent on-call or runbook for each system boundary; "ask
      in Slack" is not an escalation step.
- [ ] Every adjacent team and every upward stakeholder in
      `STAKEHOLDER_MAP.md` has a named cadence.
- [ ] `AUDIT.md` has an "explicit non-changes" section that is
      not empty.

### 3.2 Reality-check validation

- [ ] Hand the docs to a (real or roleplay) teammate and ask
      "does this match how we work?" Capture corrections. If
      corrections exceed ~20% of the doc, the lead has not
      listened enough; restart the audit.
- [ ] Hand `ONCALL.md` to the current on-call and ask "if you
      were paged at 2am for incident X, what would you do?"
      Walk the escalation path with them. If they need to ask
      "who do I call," the doc has a gap.
- [ ] Hand `STAKEHOLDER_MAP.md` to one adjacent-team lead and
      ask "do we have the right cadence and the right surface
      area listed?" Capture corrections.

### 3.3 Restraint validation

- [ ] The capstone proposes at most **two** trial changes in the
      next 90 days. More than two is almost always a sign that
      the lead is changing things to demonstrate activity.
- [ ] Each proposed change has a written **abandon criterion**.
      If there is no way to know whether the change failed, it
      will not be abandoned and will accumulate.
- [ ] The lead can answer, in writing, "what did I decide not
      to change, and why?" If the answer is "nothing, I changed
      everything that looked broken," fail the capstone and
      restart.

### 3.4 Sustainability validation

- [ ] Every document includes a `Last reviewed` date and a named
      owner.
- [ ] The team operating doc references a review cadence (e.g.
      "reviewed at quarterly planning, week 13"). Documents that
      do not declare when they will be re-checked drift silently.
- [ ] Each ADR has a clear `Status`. Live decisions and
      superseded decisions are distinguishable at a glance.

## 4. Rubric or review checklist

This is the grading rubric. Each row is scored 0 (absent),
1 (present but weak), or 2 (present and strong). A passing
capstone scores ≥ 18 out of 26, with no zero in any
load-bearing row.

| # | Dimension | What strong looks like | Load-bearing? |
|---|-----------|------------------------|---------------|
| 1 | Operating doc — completeness | Mission, scope, rhythm, roles, channels, on-call, decision rules, doc expectations. | Yes |
| 2 | Operating doc — concision | One page. Reads cleanly. No filler. | No |
| 3 | Ritual calendar — owners and stop conditions | Every ritual has both. | Yes |
| 4 | On-call — escalation specificity | Named systems and named adjacent on-calls or runbooks. | Yes |
| 5 | On-call — handoff format | Written, scheduled, low ceremony. | No |
| 6 | ADRs — historical capture | At least three retrospective ADRs that externalize tribal knowledge. | Yes |
| 7 | ADRs — format discipline | Consistent template, with `Status` lifecycle. | No |
| 8 | Stakeholder map — coverage | Inward, adjacent, upward, customer — all four quadrants. | Yes |
| 9 | Stakeholder map — cadence | Every stakeholder has a named cadence. | Yes |
| 10 | Audit — honesty | Lists broken things without sugar-coating. | Yes |
| 11 | Audit — restraint | ≤ 2 proposed changes; explicit non-changes listed. | Yes |
| 12 | Audit — abandon criteria | Each proposed change has a way to fail safely. | No |
| 13 | Overall — would I onboard a new hire with these docs? | Yes, day-1 productive in ≤ 1 week of reading. | Yes |

Failing any **load-bearing** row at zero is an automatic restart.
Strong scores in nice-to-have rows do not compensate for a
missing escalation table or an empty stakeholder quadrant.

## 5. Common mistakes

These are recurring failure modes graders see. Each is paired
with the cheaper correct path.

### 5.1 Rewriting the team's process in the first 30 days

The most common, most damaging failure mode. A new lead arrives,
finds the rituals confusing or the artifacts incomplete, and
proposes a redesign. Two months later the team has lost the
implicit knowledge that the old (messy) system encoded, and the
new (clean) system is missing the special-case handling that
was load-bearing.

Correct path: 70/20/10. Document what exists, fix what is
obviously broken (missing escalation, absent on-call handoff,
no documentation of critical decisions), propose at most one or
two trial changes with the team's consent.

### 5.2 Adopting a public methodology verbatim

"We will do Shape Up." "We will do Spotify squads." Public
methodologies are reported from the inside of the team that
invented them, after a multi-year evolution that does not
transfer with the blog post. Spotify itself publicly stepped
back from the canonical "Spotify model" description; the blog
post outlived the practice.
<!-- editorial note: cite Spotify's own retrospective on the
     "Spotify model" (Henrik Kniberg / Joakim Sundén materials)
     before quoting specifics. -->

Correct path: borrow elements, name the *adaptation* explicitly,
and write down the parts you intentionally did not adopt.

### 5.3 Calendar prettiness instead of decision recording

A Notion workspace with color-coded ritual calendars, emoji
status pills, and beautifully tagged stakeholders — but no ADRs,
no escalation table, no audit. The visible polish is the
substitute for the load-bearing work.

Correct path: invert the time allocation. ADRs and escalation
first, presentation last.

### 5.4 1:1s as project status

The team operating doc lists weekly 1:1s, but the 1:1s
themselves are 30 minutes of "what are you working on?" — which
the lead already knows from standup. The 1:1 has become a
duplicate status meeting, the report has nothing to say, and the
ritual decays into a cancelled meeting six weeks later.

Correct path: the 1:1 agenda is the report's, not the lead's.
The lead's job is to listen for blockers, growth signals, and
the quiet "things are not okay" cues. See
[`mod-702-people-management`](../../modules/mod-702-people-management/SOLUTION.md).

### 5.5 On-call escalation as "ask in Slack"

The on-call doc names a primary, a secondary, and then
"escalate to the team." This is not an escalation path; it is
the absence of one. At 2am, the engineer paged for a
cross-system issue does not know whose phone to ring.

Correct path: enumerate the system boundaries, name the
adjacent on-call (or named runbook) for each, and pressure-test
the path by walking it through with the current on-call.

### 5.6 Stakeholder cadence as "as needed"

Adjacent-team relationships listed in the stakeholder map with
"sync as needed" instead of a named cadence. The cadence decays
to "sync when something breaks," which is also when both teams
have the least slack to coordinate.

Correct path: a standing biweekly 1:1 with each adjacent lead is
cheap to skip when nothing is pending and expensive to schedule
under pressure. Schedule it; skip it freely.

### 5.7 Audit with no "explicit non-changes" section

The audit lists ten things the lead intends to fix, with no
mention of what they considered and chose to leave alone. This
reads to the grader as "the lead has not made a real
judgement," because every part of the team's process was either
adopted or proposed for change — there is no evidence of
selection.

Correct path: the non-changes list is as important as the
changes list. Treat it as a graded artifact.

### 5.8 Documents with no review date and no owner

`TEAM_OPERATING_DOC.md` with no `Last reviewed` line and no
named owner. The doc is born current and decays silently. Six
months later it no longer matches reality, the new hire reads
it on day 1, and is set up for repeated small surprises.

Correct path: every artifact has a `Last reviewed` date, a
named owner, and a review cadence. The quarterly-planning
ritual is the natural anchor.

## 6. References

### Internal — track and module solutions
- [`SOLUTION_OVERVIEW.md`](../../SOLUTION_OVERVIEW.md) — track-level design philosophy.
- [`modules/mod-701-team-operations/SOLUTION.md`](../../modules/mod-701-team-operations/SOLUTION.md) — operating doc, ritual, on-call rubric.
- [`modules/mod-702-people-management/SOLUTION.md`](../../modules/mod-702-people-management/SOLUTION.md) — 1:1, growth, performance conversations.
- [`modules/mod-703-project-roadmap/SOLUTION.md`](../../modules/mod-703-project-roadmap/SOLUTION.md) — roadmap and project defense (referenced by the audit's "proposed changes" rigor).
- [`modules/mod-704-cross-team-coordination/SOLUTION.md`](../../modules/mod-704-cross-team-coordination/SOLUTION.md) — adjacent-team interfaces and commitment register.
- [`modules/mod-705-hiring-onboarding/SOLUTION.md`](../../modules/mod-705-hiring-onboarding/SOLUTION.md) — the onboarding consumer of the operating doc.

### External — official and widely-cited references

These are the references the deliverable can lean on. Cite
specifics directly from the source; do not paraphrase numbers
or claims that are not in the linked material.

- **Architecture Decision Records (ADRs).** Michael Nygard's
  original 2011 essay "Documenting Architecture Decisions" is
  the canonical lightweight ADR template referenced throughout
  this solution. The [`adr/madr`](https://adr.github.io/madr/)
  project also maintains a more elaborate variant; either is
  acceptable as long as it is used consistently.
  <!-- editorial note: confirm canonical URL for Nygard's
       original essay (currently hosted via Cognitect /
       thinkrelevance archives) before publication. -->
- **Incident response and on-call structure.** Google's *Site
  Reliability Engineering* book (O'Reilly, 2016) is the most
  widely-referenced public source on on-call structure,
  rotation shape, paging severity, and runbook discipline. The
  chapters on "Being On-Call" and "Managing Incidents" are the
  baseline this solution's `ONCALL.md` rubric is consistent
  with. Cite specific chapters by name when borrowing.
  <!-- editorial note: confirm exact chapter titles and page
       references before quoting specifics. -->
- **Retro facilitation.** Esther Derby and Diana Larsen,
  *Agile Retrospectives: Making Good Teams Great* (Pragmatic
  Bookshelf, 2006) is the standard reference. The five-step
  arc (set the stage, gather data, generate insight, decide
  what to do, close) is what the "stop-the-meeting condition"
  in the ritual calendar is calibrated against.
- **Postmortem culture.** Google's SRE book chapter on
  "Postmortem Culture: Learning from Failure" is the standard
  reference for the blameless-postmortem framing that the
  `ONCALL.md` documentation expectations assume.
- **Spotify-model retrospective.** The original Henrik Kniberg
  / Anders Ivarsson "Scaling Agile at Spotify" paper (2012) and
  the later retrospectives by Kniberg and Joakim Sundén are
  the canonical source for the "do not adopt the model
  verbatim" caution in § 5.2.
  <!-- editorial note: locate primary-source URLs for both the
       2012 paper and the later retrospective material before
       quoting specifics. -->

### External — practitioner examples

VeriSwarm's internal team-process artifacts (where published)
are usable as **implementation examples** illustrating how the
rubric in this solution maps to a working team. They are not
authoritative sources for the rubric itself; treat them as
worked examples of one valid instantiation.
<!-- editorial note: confirm whether any VeriSwarm
     practitioner-example artifacts are publicly linkable
     before adding a direct reference. -->

### Cross-track touchpoints
- `principal-engineer-solutions/SOLUTION_OVERVIEW.md` — the
  staff-IC perspective on the same team's process; useful for
  the lead to read alongside this capstone to understand what
  the team's senior IC sees.
- `architect-solutions/projects/` — the architectural-leadership
  altitude for cross-team decisions referenced by the
  stakeholder map's adjacent-team quadrant.

---

*Maintained as part of [`ai-infra-team-lead-solutions`](../../README.md).
Update this solution when the paired learning project's scope or
artifact list changes.*
