# SOLUTION — exercise-05: Cross-Team Review Presentation

> Read this *after* attempting the exercise. The deliverable is a
> facilitator-ready presentation / agenda for a recurring
> cross-team review. The worked example is a labeled teaching
> scenario.

## 1. Solution overview

The cross-team review is the mechanism that keeps the contract
([exercise-02](../exercise-02/SOLUTION.md)) and the joint
roadmap ([exercise-04](../exercise-04/SOLUTION.md)) from
decaying. The module SOLUTION lists four agenda items:

1. Where are we on the integration?
2. What's at risk?
3. What do we need from each other?
4. Any incidents or surprises since last review?

The presentation's job is to make a 30–45 minute meeting
reliably produce **decisions and follow-ups**, not status
updates. If the submission produces a deck that reads like a
status report, it has failed the exercise.

This review is also the standing mechanism that keeps
accountability and oversight current — the kind of ongoing
governance NIST AI RMF `GOVERN` and `MANAGE` describe as
lifecycle controls for AI systems.<sup>[1]</sup>

## 2. Worked answer: the facilitator-ready agenda

> **Local exercise context (fictional).** Teams and prior-
> meeting references are labeled teaching examples.

### 2.1 Metadata (slide 1)

```
Cross-Team Review: Feature Store ↔ Fraud Detection
Date:       2026-Q2 Month 1, Week 3
Cadence:    Monthly (or biweekly during active migration)
Duration:   30 min hard-stop; 45 min only during cutovers
Owners:     lead-P, lead-C (rotate facilitator each month)
Required:   lead-P, lead-C
Optional:   eng-P1, eng-P2, eng-F1, eng-F2 (based on agenda)
Doc:        link to persistent cross-team review doc
Next:       date of next review
```

The metadata is load-bearing: it names the owners, the
cadence, the required vs optional attendees, and the
persistent doc. A review without a persistent doc is a review
no one can refer back to.

### 2.2 Agenda (slide 2)

```
1. Where are we on the integration?   (5 min)
   — Status of each row of the joint roadmap.
   — "On track", "At risk", or "Slipped" only.
   — Any "Slipped" item moves straight to item 2.

2. What's at risk?                    (10 min)
   — Each at-risk item named by its owner.
   — For each: impact, decision needed, owner of decision.
   — Decisions marked [D]. Follow-ups marked [FU] with owner + date.

3. What do we need from each other?   (10 min)
   — New requests surfaced here, not via DM.
   — Each request: who, what, by when, acceptance criterion.

4. Incidents or surprises since last? (5 min)
   — Any cross-team incident in the last period.
   — Anything that should have been in the plan and wasn't.

5. Follow-ups and decisions recap     (last 2 min)
   — Read back [D] and [FU] markers.
   — Confirm owner and due date on each.
```

The time budget is strict. If item 2 runs long, items 3 and 4
get cut and rolled into a short written update instead. This
rule keeps the review from degenerating into "whoever filibustered
best got heard."

### 2.3 Status slide template (slide 3)

```
Joint roadmap status — current quarter
┌────────┬──────────────┬───────────┬───────────┐
│ Row    │ Dependency   │ Status    │ Owner     │
├────────┼──────────────┼───────────┼───────────┤
│ Q2-row │ API v2 beta  │ On track  │ lead-P    │
│        │ staging      │           │           │
│ Q2-row │ Read-path    │ At risk   │ lead-C    │
│        │ migration    │           │           │
└────────┴──────────────┴───────────┴───────────┘

At-risk items trigger drill-down in agenda item 2.
```

Three statuses only: `On track`, `At risk`, `Slipped`. No
yellow/green/red proliferation. Fewer categories force honest
calls.

### 2.4 Follow-ups / decisions slide template (slide 4)

```
Open from last review
[FU-2026-M0-01] lead-C: confirm feature-X semantic
                mapping   — due 2026-M1 wk2  — STATUS
[FU-2026-M0-02] lead-P: publish v2 migration guide
                        — due 2026-M1 wk3  — STATUS

New this review
[D-2026-M1-01] Decided: sunset v1 at end of Q3 with
               60-day window.
[FU-2026-M1-01] lead-P: draft deprecation notice by wk4.
```

The IDs (`FU-YYYY-Mn-NN` and `D-YYYY-Mn-NN`) are not optional.
They make follow-ups re-citable across reviews; a follow-up
that cannot be referenced gets forgotten.

### 2.5 Facilitation notes (slide 5, speaker notes only)

- Start on time. End early when possible; never late.
- Facilitator talks ≤ 20% of the time.
- If a discussion goes technical and loses the room, timebox
  it to 2 minutes and move it to an offline thread with
  named participants.
- **Watch for domination.** If one team's engineers are doing
  most of the talking, call on the other team's lead
  directly. The module SOLUTION flags this (usually the
  platform team patronizing the consumer team) as a watch
  item.
- Capture decisions and follow-ups *live* in the doc. Not in
  chat, not in slack, not "I'll write it up later."
- Rotate facilitator each quarter so no team owns the
  framing.

### 2.6 Decision rationale

**Why a presentation and not just a running doc.** The deck is
scaffolding for the facilitator; the persistent doc is the
system of record. In the review, the deck drives the flow; the
doc captures the output. Both exist. A deck-only review has
nothing to refer back to; a doc-only review has no structure
and runs long.

**Why 30 minutes hard-stop.** The review must fit under the
cost of attendance. Two leads + a few engineers at 30 min is
affordable monthly indefinitely; at 60+ min it will get
dropped within six months. Short cadence → long survival.

**Why three status colors only.** Multi-color status (R/A/G,
sometimes with "amber-red" sub-shades) encourages posturing.
"On track / At risk / Slipped" has a sharp edge: "At risk"
triggers drill-down, "Slipped" triggers a decision. No fourth
option.

**Why rotate facilitator each quarter.** Framing is power.
If lead-P always facilitates, the review optimizes for Team P's
anxieties. Rotation forces both perspectives into the agenda
over time.

**Why recap decisions at the end.** The single most common
failure of a review is that participants leave with different
memories of what was decided. Reading the [D] and [FU] markers
back closes that gap before anyone leaves the room.

**Why incidents come last, not first.** Incidents are the
loudest topic; placing them first means they eat the room and
the planning items (which need the review *more*) get
starved. Incidents 5 minutes at the end means they get
discussed when the energy is appropriate for recap rather than
debate.

## Implementation

To produce a submission that matches the worked answer above:

1. **Draft five slides and no more.** Metadata, agenda, status
   template, follow-ups/decisions template, facilitation notes.
   A standing-review deck longer than five slides will not
   survive the first quarter.
2. **Fill the metadata slide.** Owners, cadence, duration,
   required vs optional attendees, link to persistent review
   doc, next date. The persistent doc is the system of record;
   the deck is scaffolding.
3. **Lay out the agenda with time budgets.** Four topics (status,
   risks, needs, incidents) plus a 2-minute recap. Time budgets
   must sum to the meeting duration. Incidents go last, not
   first.
4. **Define the status model as three states.** `On track`,
   `At risk`, `Slipped`. Attach the rule: `At risk` triggers
   drill-down in item 2; `Slipped` triggers a decision.
5. **Prepare the decisions / follow-ups template.** Use
   referenceable IDs (`D-YYYY-Mn-NN`, `FU-YYYY-Mn-NN`), an
   owner per entry, and a due date. No ID → will be forgotten.
6. **Write the facilitation notes as speaker notes.** Include
   the domination-watch item, the facilitator-rotation rule,
   the 20%-talking-ceiling, and the live-capture rule.
7. **Dry-run with a peer who is not on either team.** If they
   cannot follow the status slide cold, the status slide is
   not doing its job — tighten it before the first real
   review.

## 3. Validation steps

Self-check before submission:

- [ ] Metadata slide present with owners, cadence, duration,
      required vs optional attendees, persistent doc link.
- [ ] Agenda slide has time budgets that sum to the meeting
      duration.
- [ ] Status template uses exactly three statuses.
- [ ] Follow-ups and decisions have IDs.
- [ ] Facilitation notes include a domination-watch item and
      a facilitator rotation.
- [ ] The final 2 minutes are reserved for recap.
- [ ] A persistent doc for review history is referenced.
- [ ] The deck fits ≤ 5 slides for a standing review.

Dry-run the deck with a peer who isn't on either team. Ask:
"If you dropped into this meeting cold, could you follow it?"
If the answer is "I'd need the backstory," the status slide is
not doing its job.

## 4. Rubric / review checklist

Scored 0–2 per dimension. Passing bar: 10/14.

| # | Dimension | 0 | 1 | 2 |
|---|---|---|---|---|
| 1 | Agenda structure | Missing / status-only | Covers all 4 topics | 4 topics + recap + time budgets |
| 2 | Status model | Open-ended categories | R/A/G with no rules | 3-state with explicit drill-down rule |
| 3 | Follow-up / decision capture | No mechanism | Captured, no IDs | Captured with IDs + owner + date |
| 4 | Facilitation rules | Absent | Generic ("be fair") | Domination-watch + rotation + timebox |
| 5 | Persistent doc link | Not referenced | Referenced | Named as system of record |
| 6 | Time budget | None | Total only | Per-agenda-item, with slack rule |
| 7 | Attendance plan | "Everyone" | Required/optional listed | Required/optional + rotating engineers |

Reviewer flags:

- **Deck ends with "questions?"** Replace with the decisions
  recap. A review without recap is a review without an
  output.
- **Status column has > 4 categories.** Collapse to three.
- **Agenda starts with incidents.** Reorder. Incidents last.
- **Owners are missing from follow-up template.** Follow-ups
  without owners are not follow-ups.

## 5. Common mistakes

- **Status update, not decision forum.** The single most
  common failure. Reviews that only report status should
  either be cancelled or shrunk to an async written update.
- **Running long.** Every long review loses a half-dozen
  attendees over the next quarter. Hard-stop at duration.
- **One team dominates.** Usually the platform team
  patronizing the consumer team. The facilitator's job is to
  pull the other team in, actively.
- **Follow-ups without IDs.** Follow-ups that can't be
  referenced in next month's deck will not be followed up.
- **No retrospective after a milestone.** A successful
  cross-team interface should be reviewed for *what worked*
  as well as what didn't; else the lessons are lost on the
  next pair of teams.
- **Fixed facilitator forever.** The agenda tilts toward that
  team's priorities. Rotate.
- **Incidents hijack the room.** If incidents consistently eat
  the agenda, fire a separate cross-team incident review and
  reclaim the planning review.
- **No written decision at the end.** If the recap is
  verbal only, the [D] markers don't exist and nothing was
  actually decided.

## 6. References

1. NIST AI Risk Management Framework (AI RMF 1.0) — `GOVERN`
   and `MANAGE` functions on ongoing oversight and lifecycle
   management of AI systems.
   <https://www.nist.gov/itl/ai-risk-management-framework>
2. Module SOLUTION: [../SOLUTION.md](../SOLUTION.md), section
   "The cross-team review (exercise 05)".
3. Related exercises:
   [exercise-02](../exercise-02/SOLUTION.md) (the contract
   this review maintains),
   [exercise-04](../exercise-04/SOLUTION.md) (the joint
   roadmap this review drives off of).

<sup>[1]</sup> NIST AI RMF 1.0's `GOVERN` and `MANAGE`
functions describe ongoing oversight across the AI system
lifecycle. The cross-team review is a lightweight mechanism
that implements that oversight at the team-lead altitude.
