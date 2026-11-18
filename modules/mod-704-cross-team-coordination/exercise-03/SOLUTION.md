# SOLUTION — exercise-03: Cross-Team Stakeholder Mapping

> Read this *after* attempting the exercise. The deliverable is a
> stakeholder map and a routing table showing *who to talk to
> about what*. The worked example is a labeled teaching scenario.

## 1. Solution overview

At the team-lead altitude, a stakeholder map is not a political
org chart — it's a **routing table**. For each neighboring team,
the map answers one question: when I need X, who do I talk to?

The module SOLUTION lays out four roles per adjacent team:

- **Their team lead** — your peer; primary contact.
- **Their senior engineers** — technical co-owners.
- **Their manager (your peer-manager)** — escalation.
- **Their PM** — roadmap impact (if they have one).

The failure modes the module calls out drive the design of the
deliverable:

- Going to the engineer for schedule → unenforced commitments.
- Going to the lead for technical detail → slow and often wrong.
- Escalating too early → burns political capital.

A strong submission produces (a) a named graph of adjacent teams
and their four roles, and (b) a routing table mapping request
types to the right first contact.

This mapping implements the "roles and responsibilities"
clarity NIST AI RMF `GOVERN 2` names as a baseline for AI
system accountability.<sup>[1]</sup>

## 2. Worked answer

> **Local exercise context (fictional).** Teams and names are
> labeled teaching placeholders.

### 2.1 The home team

**Team Fraud-Detect (home).**
Mission: production fraud model.
Lead: me.
Senior engineers: eng-F1 (modeling), eng-F2 (serving).

### 2.2 Adjacent teams (the map)

**Team Feature-Store (Platform).**
- Lead: lead-P
- Senior engineers: eng-P1 (schema / storage), eng-P2 (serving tier)
- Manager (peer-manager): manager-X (also my manager — shared)
- PM: none

**Team Model-Platform (Platform).**
- Lead: lead-MP
- Senior engineers: eng-MP1 (training infra), eng-MP2 (inference infra)
- Manager (peer-manager): manager-Y
- PM: pm-MP

**Team Risk-Decisioning (Consumer).**
- Lead: lead-R
- Senior engineers: eng-R1, eng-R2
- Manager (peer-manager): manager-Z
- PM: pm-R

**Team Compliance (Oversight).**
- Lead: lead-CMP
- Senior engineers: n/a (counsel instead of engineers)
- Manager: director-level, not my peer
- PM: n/a

The "Oversight" row is important: compliance is a stakeholder
even when you have no technical dependency on them.

### 2.3 The routing table

| I need... | First contact | Fallback | Notes |
|---|---|---|---|
| Technical clarification on a feature definition | eng-P1 | eng-P2, then lead-P | Engineer-to-engineer; lead-P copied on decisions only |
| Schedule commitment on a new feature | lead-P | peer-manager if lead-P unavailable | Never from an engineer — they can't commit the team |
| Prioritization dispute with Platform | lead-P → peer-manager | Director if peer-manager blocked > 2 days | Go to peer first; escalation is a budgeted move |
| Model-platform infra bug | eng-MP1 / eng-MP2 | lead-MP | Normal engineering workflow |
| Infra cost conversation | lead-MP + pm-MP | peer-manager | Cost is usually joint lead+PM |
| Consumer impact of a change we're making | lead-R, pm-R | eng-R1/R2 | Lead for impact, engineers for detail |
| Compliance review of a new feature | lead-CMP | — | Early; don't surprise compliance |
| Cross-team incident during on-call | On-call of affected team, then lead | Peer-manager if lead unavailable | Page the right team's on-call, not the lead directly |

The table is what makes the map useful. The graph alone tells
you who exists; the table tells you who to talk to.

### 2.4 Decision rationale

**Why a routing table and not just a graph.**
The map's value is operational, not visual. A pretty graph on a
slide doesn't answer "who do I ping right now?" The routing
table does.

**Why "first contact" and "fallback" separately.**
The lead is the default routing target for schedule and
priority. For technical detail, the lead is the *wrong*
default. Separating first-contact from fallback makes the
distinction explicit and matches the module's failure modes.

**Why compliance is on the map despite no technical dependency.**
Compliance surprises are among the most expensive. A team lead
who only maps engineering teams leaves out stakeholders who can
block a launch at the last minute. For AI-adjacent teams
specifically, NIST AI RMF `GOVERN 1` calls out legal/compliance
integration into governance as a baseline practice.<sup>[1]</sup>

**Why peer-managers not directors are the escalation row.**
Directors are a second-step escalation. Going to the director
first signals the peer-manager layer failed, which (a) is
usually untrue and (b) burns trust with the peer-manager when
it isn't.

**Why PMs for some teams and not others.**
Platform teams with a strong roadmap discipline have PMs;
infrastructure sub-teams often don't. Pretending every team has
a PM creates phantom contacts.

## Implementation

To produce a submission that matches the worked answer above:

1. **List your home team.** Lead, senior engineers, one line per
   role. This is the anchor the rest of the map routes to.
2. **Enumerate adjacent teams.** Start from the teams you have
   sent or received work from in the last quarter; do not map
   the whole org. Include one oversight stakeholder (compliance,
   security, legal, or privacy) even without a technical
   dependency.
3. **Fill all four role slots per adjacent team.** Lead, senior
   engineers, peer-manager, PM. If a slot does not exist, write
   `n/a` with a one-line reason.
4. **Build the routing table.** At minimum six rows covering:
   technical clarification, schedule commitment, prioritization
   dispute, infra bug, cross-team incident, cross-team
   compliance review.
5. **Fill first-contact and fallback separately.** The columns
   must be distinct. If first-contact and fallback are the
   same, the row has no fallback plan.
6. **Validate the split.** No row routes schedule/priority
   through an engineer; no row routes technical detail through
   a lead by default; escalation uses peer-manager before
   director.
7. **Reality-check against three recent requests.** Pick three
   cross-team asks you actually sent last month. If the table
   does not match where you routed them, fix the table (or the
   habit — but write down which).

## 3. Validation steps

Self-check before submission:

- [ ] Every adjacent team has all four role slots filled, or is
      explicitly marked "n/a" with a reason.
- [ ] The map includes at least one oversight stakeholder
      (compliance, security, legal, privacy) even if there's no
      technical dependency.
- [ ] The routing table has at least 6 rows covering: technical
      clarification, schedule, prioritization, infra bug,
      cross-team incident, cross-team compliance review.
- [ ] For each row, the first contact is distinct from the
      fallback.
- [ ] No row routes schedule/priority questions through an
      engineer.
- [ ] No row routes deep technical questions through a lead by
      default.
- [ ] The escalation path uses the peer-manager layer before
      directors.

Then validate the map against reality: pick three real requests
you've recently sent to another team; does the routing table
match where you actually routed them? Where it doesn't match,
one of the two is wrong — either your routing habit, or the
table.

## 4. Rubric / review checklist

Scored 0–2 per dimension. Passing bar: 10/14.

| # | Dimension | 0 | 1 | 2 |
|---|---|---|---|---|
| 1 | Completeness of adjacent teams | < 2 teams | 2–3 teams, missing oversight | 3+ teams including oversight stakeholder |
| 2 | Role slots per team | Lead only | Lead + engineers | All four slots or explicit n/a |
| 3 | Routing table coverage | < 4 rows | 4–5 rows | ≥ 6 rows covering the key categories |
| 4 | First-contact / fallback split | Not present | Present but inconsistent | Consistent, with rationale |
| 5 | Schedule questions routed to lead, not engineer | Wrong default | Mixed | Consistent correct routing |
| 6 | Technical questions routed to engineer, not lead | Wrong default | Mixed | Consistent correct routing |
| 7 | Escalation uses peer-manager before director | Missing | Implicit | Explicit in table |

Additional reviewer flags:

- **Map omits compliance/security/legal.** Flag for revision
  before grading — it is a specific failure the module warns
  about.
- **Routing table that always routes to the lead.** The
  submitter has not internalized the engineer-vs-lead split.
- **Routing table with no fallback column.** The map is one
  vacation away from being useless.

## 5. Common mistakes

- **Treating the map as an org chart.** It is a routing table.
  Org charts are for HR; routing tables are for work.
- **Omitting oversight stakeholders.** Compliance, security,
  legal, and privacy belong on the map even without a
  technical dependency, especially for AI teams.
- **Routing everything to the lead.** Burns the lead and
  slows the team down. Engineers should be the first contact
  for engineering questions.
- **Routing schedule to an engineer.** Produces commitments
  the team won't keep because the engineer didn't have
  authority to make them.
- **Over-broad maps.** Mapping every team in the org produces
  a diagram no one uses. Map only teams you actually interact
  with.
- **Escalating straight to directors.** Peer-managers exist for
  a reason; using them is the first move, not the fallback.
- **One-time mapping.** The map needs the same review cadence
  as the contract (see [exercise-02](../exercise-02/SOLUTION.md)).
  People change teams; roles move.

## 6. References

1. NIST AI Risk Management Framework (AI RMF 1.0) — `GOVERN 1`
   (integration of legal/compliance/oversight) and `GOVERN 2`
   (roles and responsibilities).
   <https://www.nist.gov/itl/ai-risk-management-framework>
2. Module SOLUTION: [../SOLUTION.md](../SOLUTION.md), section
   "Stakeholder mapping (exercise 03)".
3. Related exercises:
   [exercise-02](../exercise-02/SOLUTION.md) (the contract that
   names the roles this map routes to),
   [exercise-05](../exercise-05/SOLUTION.md) (the review where
   these stakeholders appear).

<sup>[1]</sup> The stakeholder map and routing table are a
team-lead-altitude concretization of the governance roles and
oversight integration NIST AI RMF `GOVERN 1`/`GOVERN 2`
describe. The framework prescribes the *control objective*;
this exercise teaches one practical artifact that meets it.
