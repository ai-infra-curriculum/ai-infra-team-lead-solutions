# SOLUTION — Exercise 03: Stakeholder Mapping

> Read this *after* you have attempted the exercise. The map
> below is populated against the synthetic Fleet-Serving team
> used in [exercise-01](../exercise-01/SOLUTION.md) and
> [exercise-02](../exercise-02/SOLUTION.md). Substitute your
> own real or case-study team's stakeholders when you apply
> the rubric. Names and reporting lines are illustrative.

## 1. Solution overview

### What this exercise is really testing

Stakeholder mapping is the discipline of knowing, in advance,
who needs what from your roadmap, in what form, on what
cadence, and what bad happens if they do not get it. The
grading bar is **differentiated engagement** — four audiences,
four cadences, four different views of the same source of
truth. A map with one column of names and no differentiation
is a contact list, not a stakeholder map.

The parent [`SOLUTION.md`](../SOLUTION.md#stakeholder-mapping-exercise-04-the-dependent-teams)
argues for four axes:

1. **Upward** — manager, leadership. They need confidence
   levels and the top three risks.
2. **Sideways** — teams you depend on, teams that depend on
   you. They need timing and interfaces.
3. **Inward** — the team itself. They need clarity on what
   is in, out, and stretch.
4. **Customers** — external or internal consumers of what
   the team ships. They need outcome timing, no jargon.

A roadmap that fits one audience well is almost certainly
failing the other three. A roadmap that attempts to fit all
four in one artifact is failing all four, because the shape
is wrong for each.

### AI-infra specialization

For an AI-infra team, the sideways axis is bigger than it is
for a product team. You typically owe commitments to at least
five sibling orgs: AI Engineering (serving endpoints), ML
Engineering (training platform features), Governance (audit
evidence and controls), Startup/Finance (cost commitments),
and AI Workforce / platform-adopter orgs (operational
contracts). You also depend on sibling orgs for hardware
delivery, framework upgrades, and research artifacts. The
sideways axis therefore has to be the most structured part of
the map, not the thinnest.

The module README's AI-infra specialization section is the
canonical source for this framing.

## 2. Worked answer or implementation

### Stakeholder map (worked example)

For the synthetic Fleet-Serving team. The 2×2 is influence
(the stakeholder's ability to materially change the roadmap)
versus interest (how actively they are watching it this
quarter). The map has 14 rows below; the module's bar is "at
least a dozen named stakeholders."

| # | Stakeholder (role, synthetic) | Axis | Influence | Interest | Cadence | Channel | What they need from you | What you need from them |
|---|---|---|---|---|---|---|---|---|
| 1 | Your manager (eng director) | Upward | High | High | Weekly 1:1 + monthly roadmap review | 1:1, written review | Confidence levels, top 3 risks, asks | Air cover, trade-off calls, headcount decisions |
| 2 | VP AI Infra | Upward | High | Low | Monthly 1-pager + immediate ping on surprise-class events | Written | Outcomes and dates, dollar impact, escalations only | Priority tie-break, exec-level unblocking |
| 3 | AI Engineering lead | Sideways (consumer) | High | High | Biweekly sync + interface notes | Sync + written | Serving endpoint timing, API contract, rollback plan | Their product launch dates (your downstream risk) |
| 4 | ML Engineering lead | Sideways (consumer) | Medium | High | Biweekly sync | Sync + Slack channel | Training-platform feature timing, capacity windows | Expected training runs, framework-upgrade asks |
| 5 | Governance lead | Sideways (consumer + regulator) | High | Medium | Monthly + immediate on audit windows | Written | Audit-evidence schedule, control coverage, exception list | Finalized control catalogs, audit dates |
| 6 | Startup/Finance partner | Sideways (consumer) | High | Low | Monthly 1-pager + immediate on cost projection drift | Written | Fleet spend trajectory, per-token cost | Budget envelope, cost-tolerance thresholds |
| 7 | AI Workforce / platform-adopter team | Sideways (consumer) | Low | High | Biweekly written + office hours | Written + sync | Operational contracts, on-call handoff | Incident feedback, usage pain points |
| 8 | Hardware/infra procurement | Sideways (supplier) | Medium | Medium | Monthly capacity-planning meeting | Sync + written | Capacity forecast 2-4 quarters out | GPU delivery dates, inventory, framework-support matrix |
| 9 | Framework / research team | Sideways (supplier) | Medium | Low | Quarterly + ad hoc | Written + Slack | Upgrade adoption plan | Release schedule, compatibility notes |
| 10 | Peer team lead (adjacent infra) | Sideways (peer) | Low | Medium | Monthly peer review | Sync | Roadmap diff, shared-risk flags | Reciprocal flags on their roadmap |
| 11 | Team: senior ICs (Alice, Carol, Dan) | Inward | Medium | High | Weekly sync + continuous | Sync + written | Full detail, non-goals, rationale for cuts | Estimate quality, risk flags, dissent |
| 12 | Team: ICs onboarding (Frank) | Inward | Low | High | Weekly 1:1 | 1:1 | Simplified roadmap + ramp plan | Signals on where ramp is stuck |
| 13 | Team: on-call rotation | Inward | Medium | Medium | Weekly rotation handoff | Sync + runbook | Reliability-work slot, on-call load budget | Incident patterns, reliability asks |
| 14 | Platform customers (named internal tenants) | Customer | Low-Medium | Varies | Quarterly review + release notes | Written | Outcome timing, SLA changes, breaking-change notice | Usage signal, pain points, early-adopter validation |

### Differentiated views of the roadmap

The parent [`SOLUTION.md`](../SOLUTION.md#stakeholder-mapping-exercise-04-the-dependent-teams)
argues for four views; the map above tells you how each view
is produced. Concretely:

- **Upward view (leadership 1-pager).** Rows 1, 2. Goals as
  outcomes with dates, confidence per goal, top 3 risks, top
  1-2 asks, and the "what we are not doing" line. Fits on one
  page. Produced weekly for #1, monthly for #2.
- **Sideways view (adjacent-team interfaces).** Rows 3-10.
  Each sideways stakeholder gets a per-interface view: the
  specific endpoint / feature / audit item they consume from
  your roadmap, the timing, the dependency on their team, and
  the rollback or fallback plan. Published in one shared
  place; discussed per-team on their cadence.
- **Inward view (team detail).** Rows 11-13. Full detail
  including per-engineer load, non-goals, risk flags. The
  team view is the one that captures estimate uncertainty
  explicitly; the other views collapse it into confidence
  levels.
- **Customer view (tenant release notes).** Row 14. Outcome
  timing, SLA changes, breaking-change notice. No internal
  jargon, no capacity numbers, no team names.

All four are **projections of a single source of truth**, not
independently maintained artifacts. The common failure mode
(parent [`SOLUTION.md`](../SOLUTION.md#stakeholder-mapping-exercise-04-the-dependent-teams))
is four artifacts that drift apart from each other across
the quarter.

### Anti-surprise protocol for high-influence / low-interest

Rows 2 and 6 (VP AI Infra, Startup/Finance partner) are the
most dangerous quadrant. They do not watch your roadmap on a
normal week; they will block or escalate on the week a
projection lands or a customer escalates. Each needs an
**anti-surprise protocol**:

- **Row 2 (VP AI Infra).** Monthly 1-paragraph written
  update. Immediate ping on: (a) any cost projection drift
  ≥ 15 % from baseline, (b) any customer escalation that
  reaches their level, (c) any decision that implicates
  cross-org headcount.
- **Row 6 (Startup/Finance).** Monthly 1-pager tied to the
  fleet spend forecast. Immediate ping on: (a) per-request
  cost projection drift ≥ 10 %, (b) any commitment that
  carries a dollar number already told to the board, (c) any
  decision that changes the training-vs-inference spend mix.

The protocol is named explicitly on the map and in the
roadmap document; it is not an implicit expectation.

## 3. Validation steps

1. **Twelve-name test.** Does your map name at least 12
   stakeholders by role (not by individual name — role is more
   durable)? Below 12, you have probably missed a sibling org
   or a customer segment.
2. **Four-axis test.** Does every stakeholder sit on exactly
   one of the four axes (upward / sideways / inward /
   customer)? If a stakeholder sits on two, split them into
   two rows — each role gets its own expectations.
3. **Cadence test.** Does every row have a cadence that is not
   "as needed"? "As needed" is almost always a mistake; it
   turns into "never" or "in a panic."
4. **Differentiation test.** Can the same roadmap artifact be
   handed to all 14 rows unchanged? If yes, the map is not
   driving differentiation; rework it.
5. **Anti-surprise test.** For every row in the high-influence
   / low-interest quadrant, is there a specific trigger
   condition that converts "not watching" into "immediately
   notified"? Without it, those rows are the ones that block
   you.
6. **Reciprocity test.** For every sideways row, is there a
   column for what you need from them, not only what they
   need from you? If only one direction is populated, you are
   treating the stakeholder as a broadcast target, not a
   partner.
7. **AI-infra coverage test.** Does the map explicitly name
   AI Engineering, ML Engineering, Governance, Startup/Finance,
   and at least one platform-adopter org? If any is missing,
   your roadmap will almost certainly surprise them later.
   Reference the module README's AI-infra specialization
   section if you are unsure what to include.

## 4. Rubric or review checklist

| Dimension | L1-L2 | L3 | L4-L5 |
|---|---|---|---|
| **Coverage** | < 8 named roles or missing a sibling org. | ≥ 12 roles, four axes populated. | ≥ 12 roles, four axes, named AI-infra sibling orgs (AI Eng, ML Eng, Governance, Finance, Workforce), and an on-call rotation row. |
| **Differentiation** | One view, one cadence. | Four distinct views, four cadences. | Four views produced from a single source of truth, with an explicit note on how they are kept consistent. |
| **Anti-surprise protocol** | Not present. | Named for ≥ 1 high-influence / low-interest row. | Named for every high-influence / low-interest row, with specific trigger thresholds. |
| **Reciprocity** | "What you need from them" column empty. | Populated for every sideways row. | Populated with concrete deliverables and dates, not generic ("support"). |
| **AI-infra specificity** | Generic project stakeholder map. | AI-infra siblings named. | Includes capacity-planning cadence (hardware/framework suppliers) as distinct from delivery cadence, and names governance-evidence rows by control catalog or audit window. |

**Caps.** A map that lists stakeholders without cadence or
channel caps at L2. A map that treats the team itself as a
single row rather than as differentiated inward audiences
(senior ICs, onboarding ICs, on-call rotation) caps at L3.

## 5. Common mistakes

- **One roadmap document for all four axes.** The classic
  failure. Each audience gets a different shape; a single
  document is wrong for at least three of them.
- **Missing the "what you need from them" column.** Treats
  the stakeholder as a target, not a partner. Also loses the
  signal that lets you catch your own upstream dependencies
  slipping.
- **No high-influence / low-interest anti-surprise protocol.**
  This quadrant is where blow-ups originate.
- **Mapping individuals instead of roles.** Individuals change
  jobs; roles persist. Role-based maps survive personnel
  churn.
- **Collapsing the team into one inward row.** Senior ICs,
  onboarding ICs, and on-call rotation have different
  information needs. A single "the team" row means at least
  one of those audiences is being served badly.
- **Underweighting customer / tenant rows.** Internal
  platform tenants are often treated as permission-free
  broadcast targets. They are the stakeholders whose pain
  usually surfaces as escalations at your VP's level — i.e.,
  row 2 getting pinged because row 14 was neglected.
- **Treating hardware/framework suppliers as side notes.**
  For AI-infra teams they are load-bearing dependencies on
  the capacity-planning cadence; missing them means your
  delivery roadmap assumes supply that may not arrive.

## 6. References

- **Local exercise context — module SOLUTION.** Parent
  [`SOLUTION.md`](../SOLUTION.md#stakeholder-mapping-exercise-04-the-dependent-teams)
  on the four axes and the common failure of one-document
  roadmaps.
- **Local exercise context — learning module README.**
  [`lessons/mod-703-project-roadmap/README.md`](https://github.com/ai-infra-curriculum/ai-infra-team-lead-learning/blob/main/lessons/mod-703-project-roadmap/README.md)
  AI-infra specialization section — the canonical source for
  the sibling-org list and dependency framing.
- **NIST AI Risk Management Framework** —
  <https://www.nist.gov/itl/ai-risk-management-framework>.
  The GOVERN function defines roles and accountabilities for
  AI-system risk; use it to validate that every AI-risk-
  carrying commitment on your roadmap has an accountable
  stakeholder on the map (not just an engineering owner).
- **MITRE ATLAS** — <https://atlas.mitre.org/>. For
  AI-security-adjacent commitments (defenses against
  adversarial inputs, data poisoning, model extraction),
  ATLAS tactics map to risk register items that the
  Governance stakeholder row will expect to see cited by ID
  rather than described in prose.

### Known research gap

A public example of a published AI-infra stakeholder map
that survived a full quarter without a major surprise would
be a valuable counterfactual anchor for the four-axis map
above. No verifiable candidate was identified at the time of
writing. Contributors should add one only if it can be cited
with attribution; fabricated examples are not acceptable.
