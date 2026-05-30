# SOLUTION — Project 04: Cross-Functional Platform Project

> Read this *after* you have attempted the deliverables. The solution
> is not a model submission. It is an opinionated walk-through of
> what each of the seven artifacts is actually trying to do, the
> trade-offs you face when filling them in, and the bar a reviewer
> is grading against. The synthetic project context (MERIDIAN —
> multi-tenant inference gateway for regulated verticals) referenced
> below is the brief in the learning repo's `playbook.md` §1; treat
> it as the local exercise context.

## 1. Solution overview

### What this project is teaching

Cross-functional project leadership is the first skill where being
*right about the work* is no longer enough. Five team leads will not
deliver a 16-week initiative because the technical plan is sound.
They will deliver it because:

- a single name is on the hook with the authority to make trade-offs;
- partner-team commitments are negotiated, dated, and surfaced when
  they slip;
- risks drive action weekly instead of sitting in a register;
- status communication produces decisions rather than read-outs;
- the launch ships against pre-committed criteria, not the room's
  mood; and
- the postmortem extracts learning that genuinely changes the next
  project.

Everything else — the templates, the cadences, the matrices — is in
service of those six behaviours. A submission that has all the
artifacts but is missing the behaviours scores at L2-L3 on the
rubric. A submission with leaner artifacts that visibly drove
decisions scores L4-L5.

### How the seven deliverables hang together

The deliverables are not independent. They form a chain:

1. **Charter (D1)** sets scope, success criteria, and decision rights.
   Every later artifact references it.
2. **Stakeholder map (D2)** turns charter sign-offs into a weekly
   engagement plan.
3. **Dependency tracker (D3)** is the operational extension of the
   stakeholder map — who owes us what, by when, and what happens if
   they slip.
4. **Risk register (D4)** is what you do with the *un-owned* failure
   modes. Dependencies are owned by partner teams; risks are owned
   by you (or your staff engineer).
5. **Communication plan + status updates (D5)** is the loop that
   keeps the charter alive — every weekly update should be readable
   against the charter's success criteria and the top risks from D4.
6. **Launch plan (D6)** is the operational endgame. It exists so
   that on launch day no one is making novel decisions.
7. **Postmortem (D7)** closes the loop and produces process change
   that survives the project.

The two structural failure modes are (a) producing each artifact in
isolation, so cross-references rot, and (b) producing the artifacts
as documents rather than as the *operating system* for the project.
The reviewer looks for evidence that the artifacts were used.

### Reviewer reading order

A reviewer reads in this order: **summary → charter → postmortem →
status updates → launch plan → risk register → dependencies →
stakeholder map**. If charter or postmortem is weak, no other
dimension can score above ~3. Invest accordingly.

## 2. Worked answer or implementation

This section walks each deliverable, explains the design decisions
that separate L3 ("complete and operational") from L4-L5 ("visibly
drove the project"), and shows where most learners will leave points
on the table. Templates themselves live in the learning repo's
`playbook.md` — do not copy them into your deliverable verbatim
without adaptation.

### D1 — Charter (`01-charter.md`)

**What good looks like.**

A charter that a sponsor can read in 60 seconds and then describe
the project, the success bar, and the decision rights without
referring back to the doc. The single highest-leverage section is
**non-goals**, which is also the most-skipped.

**Decision rationale — the parts that distinguish L4-L5 from L3:**

- *Success criteria phrased as acceptance tests, not aspirations.*
  "Audit logging meets the schema in §X across all gateway requests
  with ≥ 99.99 % capture rate, verified by a 7-day log audit before
  GA" is verifiable by someone other than you. "Improve compliance
  posture" is not. The rubric's M-CH2 caps the score at L2-L3 if
  criteria are activities. Write three criteria, each in
  acceptance-test form.
- *Non-goals that *would otherwise be assumed in scope*.* The test
  is: if you removed the non-goal, would a partner-team lead or
  customer eventually argue it was implied? For MERIDIAN, the
  default-assumed-but-out-of-scope items typically include
  non-EU residencies, BYOK for customers beyond the three named
  accounts, and a partner-team's request to also adopt the gateway
  for an unrelated workload. Name them.
- *DACI with one Approver per decision class.* "Approved by team
  consensus" is the rubric's most-flagged anti-pattern. The five
  classes that must each have a single A are: technical architecture
  (staff eng or DRI), scope changes (sponsor / VP), launch go/no-go
  (DRI within rollback criteria, VP outside them), customer
  commitments (DRI + PM, with VP approver), and escalation triggers
  (DRI is driver and approver — escalating is not a decision that
  needs approval from the person being escalated to).
- *A "what would cause us to cancel" statement.* Two sentences. The
  point is to give the sponsor permission, in advance, to stop
  rather than push through. Example shape: "If the SOC2 control
  catalog is not finalized by week 6, or if Customer A's procurement
  signals contract slip beyond week 16, the DRI will convene a
  scope-or-stop conversation with the sponsor within 5 business
  days." Concrete trigger; concrete next step.
- *Sign-offs from all five team leads + sponsor.* In simulation,
  document who would sign, who would push back, and what their
  objection would be. The L5 evidence cited in the rubric is a
  charter that "has survived first contact with a difficult
  stakeholder objection" — even in simulation, naming a realistic
  objection and how you adjusted is the signal of L4-L5 work.

**Where points are typically lost:** generic goal statements, success
criteria as activities, DACI with multiple Approvers, charters that
read like project descriptions rather than authority documents.

### D2 — Stakeholder map (`02-stakeholder-map.md`)

**What good looks like.**

≥ 12 stakeholders plotted on an influence × interest 2×2, with a
per-stakeholder engagement row that names cadence, channel, what
they need from you, and what you need from them.

**Decision rationale:**

- *Differentiated engagement is the point.* "Weekly status to all"
  is the rubric's named anti-pattern (M-SM4, W-SM1). The four
  quadrants drive four different cadences: Manage Closely =
  weekly 1:1; Keep Satisfied = monthly + immediate ping on
  surprise-class events; Keep Informed = biweekly written; Monitor
  = customer-facing comms only.
- *The high-influence + low-interest quadrant is where surprise
  damage happens.* A VP or CFO who has not been thinking about
  your project will not block you on a normal week, but they will
  block you on the week a cost projection lands or a customer
  escalates. The rubric L4 evidence is a named anti-surprise plan
  for at least one such stakeholder. Typical shape: "CFO partner:
  monthly 1-paragraph email + immediate ping if cost-per-request
  projection exceeds 110 % of baseline."
- *Engagement that produces decisions, not just touchpoints, scores
  L5.* The cited evidence pattern in the rubric — a stakeholder
  originally Keep Informed surfacing a risk you would not have
  discovered — is what to look for in your own arc. If your map
  shows every stakeholder where you would have predicted, the map
  is probably descriptive rather than active.
- *Stakeholder concerns annex (S-SM1).* A two-column table of "top
  concern per stakeholder" + "how the project addresses it" is
  cheap to write and disproportionately reads as L4 evidence
  because it shows you ran the 1:1s.

**Where points are typically lost:** stakeholder map as a list
rather than a matrix; no per-stakeholder engagement strategy; no
named high-influence + low-interest stakeholder; treating the map
as one-and-done rather than something you revise after week 4 1:1s.

### D3 — Dependency tracking system (`03-dependency-tracking.md`)

**What good looks like.**

A table where every row carries: ID, description, source team,
named owner on the source team, target date, status (On Track / At
Risk / Blocked / Delivered), consequence-if-slipped, escalation
path, last-updated date. Plus a cross-team RACI per major
deliverable, an identified critical path, and an inverse map ("we
are *their* dependency").

**Decision rationale:**

- *Status without a verification mechanism is hearsay.* "They said
  it's on track" (W-DP1) caps at L2. The L4 pattern is a weekly
  dependency-review cadence with each partner team lead, with the
  rule that an At Risk status that persists 3+ weeks without a
  status change triggers an escalation conversation within 5
  business days.
- *Critical path is identified and called out.* For MERIDIAN, the
  typical critical-path chain is: SOC2 control catalog finalized
  (security) → audit-log schema (data platform) → gateway integration
  with audit log (your team) → customer-A auditor sign-off (you +
  security + compliance). A movement on any of those four moves
  GA. Naming the chain explicitly is what the rubric calls out at
  L4.
- *Inverse map ("we are their dependency").* Two-column list:
  what does each partner team need *from you* and when. Most
  learners forget this — it shows up at L5 because it demonstrates
  symmetry of accountability. Examples from MERIDIAN: DX team
  needs the gateway interface contract by week 6 to start Q4
  planning; data platform team needs your storage estimates by
  week 4 to size persistence.
- *External vendor dependencies tracked with the same rigour
  including fallbacks (M-DP5).* Cloud provider, observability
  vendor, KMS provider — each should have a row with a documented
  fallback. The rubric L4-L5 distinction includes "external
  vendor dependencies handled with the same rigour."
- *Decoupling investments annex (S-DP1).* Where would you spend a
  week of engineering time to *remove* a dependency rather than
  manage it? For MERIDIAN, a typical candidate is replacing a
  hand-coded control-evidence packet with a generated report
  driven off the control catalog — removes the manual sync between
  you and security on every customer auditor cycle.

**Where points are typically lost:** dependencies without
consequence-if-slipped (you cannot then prioritise escalations);
RACI rows with no A or with multiple As; no critical path; missing
inverse map; vendor dependencies treated as background context
rather than tracked rows.

### D4 — Risk register (`04-risk-register.md`)

**What good looks like.**

≥ 8 risks across ≥ 4 categories (typically technical, schedule,
dependency, personnel, political, regulatory), each with leading
indicator, mitigation, kill criteria, owner, and a score (likelihood
× impact). A weekly review cadence. Evidence that the register is
*live* — at least one risk demoted and at least one new risk added
mid-arc.

**Decision rationale:**

- *Leading indicators, not lagging.* The single highest-leverage
  field is the leading indicator. "Auditor signs off" is not a
  leading indicator for R01 (Customer A auditor risk); "first
  auditor pre-call feedback in week 10" is. The leading indicator
  is what you watch to know the risk is materialising before
  damage is done.
- *Kill criteria, not just mitigations.* A risk without kill
  criteria turns into permanent worry. The format is "if [signal]
  then [action]" — for example, "if Asha's start slips past week 5,
  escalate to VP and replan the integration sprint." The rubric
  treats absence of kill criteria as the L2 marker.
- *Owner is the manager or staff engineer, not the engineer doing
  the related work (S-RR1).* This is for conflict-of-interest
  reasons: the engineer working on the EU residency implementation
  cannot also be the owner of the risk that it slips, because
  marking their own work At Risk is socially expensive and they
  will under-report. Owners should be one role above the work.
- *The register must be live (M-RR5).* The cited L4 evidence is a
  risk score moving over time — for MERIDIAN, R02 (data platform
  engineer start) typically starts at 16, rises to 18 when the
  slip materialises in week 4, and falls to 9 by week 8 once
  mitigation lands and Asha is on track. Show the arc.
- *One politically uncomfortable risk (L5).* The rubric specifically
  rewards naming a risk that is awkward to write down. Examples:
  "Customer A's CEO has publicly committed to a date; failure will
  produce a board-visible escalation"; "Two partner team leads
  have a pre-existing disagreement about audit-log ownership that
  will surface if scope grows." If every risk in your register is
  technically neutral, you have not run a real risk-ID session.
- *No padding.* W-RR1 explicitly forbids low-likelihood +
  low-impact entries for visual coverage. A register of 8 active
  risks is stronger than a register of 18 with half as padding.

**Where points are typically lost:** missing leading indicators;
no kill criteria; owners chosen for proximity rather than
authority; register frozen at kickoff and never revised; padding
with cosmetic risks; no integration with weekly status.

### D5 — Communication plan + status updates (`05-communication-plan.md`, `05-status-updates.md`)

**What good looks like.**

A plan that names audience, cadence, format, length, channel,
owner per row. Templates that differ by audience tier: the VP
gets a one-page TL;DR + top 3 risks; the team gets task-level
updates; the customer gets customer-friendly language without
internal jargon. Four worked status updates simulating weeks 1, 4,
8, 12 of the 16-week arc, each with realistic variation (green →
yellow → yellow-with-bruises → yellow-trending-green).

**Decision rationale:**

- *Audience-specific templates are the L3 floor.* If your VP
  status and team status are the same content reformatted,
  reviewer caps at L2-L3 (M-CO2).
- *Every status names top 3 risks with change since last week
  (M-CO6).* The change column is what makes the register live in
  the reader's mind. "R02: 16 → 18 (impact materialised)"
  communicates more than the absolute score.
- *Every status has a "decisions needed" section, even if empty
  (S-CO2).* Empty is acceptable; absent is not. The discipline of
  asking the question every week is what surfaces decisions
  earlier than they would otherwise come up. The rubric's L4
  evidence is a status that produced a documented decision from
  a stakeholder.
- *Realistic arc.* All-green status updates score L1-L2 regardless
  of completeness. The reviewer is looking for week 4 to be
  yellow when the data-platform engineer start slips, for week 8
  to surface a new mid-arc risk (the synthetic brief's R09 —
  Customer B's auditor wanting an additional control — is the
  intended shape), and for week 12 to show customer validation
  data driving a rollout-sequence decision.
- *Escalation protocol (M-CO5).* When to escalate, in what format,
  how soon after a signal. The L4-L5 pattern is escalation that
  happens 2-3 days *before* a problem becomes visible to the
  sponsor, with a recommended decision attached. "I want to give
  you a heads-up rather than surprise you in next week's status"
  is the canonical opener (playbook §19).
- *Customer-facing register differs from internal (L5).* Customer
  language: no team-internal names, no jargon, named contact for
  questions, commitment to follow-up cadence on change. The L5
  evidence is that a customer-facing update reads naturally when
  forwarded outside engineering — no redaction needed.
- *No "no changes since last week" without examination (W-CO2).*
  When the status is truly unchanged, the implicit question is:
  why is signal stale? Is the work blocked, is the cadence wrong,
  or is no one paying attention? Status updates are expected to
  surface that.

**Where points are typically lost:** identical templates for all
audiences; status updates as status read-outs without
risks/asks/decisions; all-green simulated arcs; no escalation
protocol; customer-facing updates that contain internal jargon.

### D6 — Launch plan + LRR template (`06-launch-plan.md`, `06-lrr-template.md`)

**What good looks like.**

Phases (dark launch → canary → phased rollout → GA) with explicit
entry and exit criteria per phase. Rollback criteria that are
pre-committed in writing and decidable without consulting the
room. An LRR template with ≥ 7 gates. Customer-specific validation
for each of the three named accounts. A war-room structure with
named slots, comms lead, and decision-logging format. A scheduled
or completed rollback dry-run. Post-launch monitoring plan.

**Decision rationale:**

- *Rollback criteria must be decidable from the criteria alone
  (M-LP2, W-LP2).* The test: hand the criteria to the rollback
  DRI and walk away. Can they decide? "If p99 latency exceeds
  baseline + 30 % for 5 consecutive minutes, roll back" passes.
  "If things look bad, roll back" fails. The rubric is unambiguous
  here — rollback that requires room judgement caps at L2.
- *Rollback dry-run before launch (W-LP1, S-LP1).* The first
  successful rollback in production is rarely the first time the
  rollback path has been exercised. Schedule the dry-run in week
  14 or 15, before phased rollout. Even in simulation, document
  the dry-run script and what you would have learned.
- *Rollback is not a failure of the team.* Failing to roll back
  when criteria are met is the failure. State this explicitly in
  the launch plan and in the closing message to the team
  (playbook §19 has the canonical script). This is a cultural
  artifact, not just an operational one — communicating it before
  launch is what gives the on-call DRI permission to actually
  pull the trigger.
- *Customer-specific validation (M-LR4).* Each of the three named
  customers has a different validation profile. Customer A needs
  the auditor packet reviewed and accepted; Customer B needs their
  own legal team to sign off on the control mapping; Customer C
  needs technical integration testing in their staging
  environment. The launch plan must enumerate each customer's
  validation requirement, owner, and current status — not "all
  customers validated."
- *Sequence the rollout by blast radius, not by customer
  importance.* The synthetic brief is constructed so that Customer
  C (smallest, noisiest) is the natural first canary candidate.
  When their bug volume materialises in week 12 (R05), the
  defensible decision is to push C *last* in the rollout despite
  the original plan. The status update in week 12 should flag
  this; the LRR should ratify it. Showing this judgement call
  visibly is L4-L5 evidence.
- *War-room is structured, not vibes.* Named slots by timezone,
  named comms lead, decision-logging format, daily summary email
  by 5 PM ET. The L1 anti-pattern is "the team will be around if
  needed."
- *LRR is decision-producing, not status-reading.* The output of
  the LRR is GO / NO-GO / DELAY in writing with sign-offs. Walking
  through the gates in the meeting and finding three unchecked
  at the end is the entire point — that is when you discover the
  launch is not actually ready.

**Where points are typically lost:** rollback criteria that
require judgement; missing dry-run; war-room as informal coverage;
launch plan that lists phases without entry/exit criteria;
identical validation expectations across customers; LRR template
without sign-off lines.

### D7 — Project postmortem (`07-postmortem.md`)

**What good looks like.**

A project-level (not incident-level) postmortem. Blameless
framing. Factual timeline. What went well + what didn't (≥ 3
items each), with at least one item naming one of *your own*
leadership behaviours. A "what we'd do differently" section that
distinguishes process / people / structural changes. A "decisions
I'd unmake" section that is specific and honest. Action items
with named owners and dates. A scheduled 6-week follow-up.

**Decision rationale:**

- *"Everything went well overall, here are some minor
  improvements" is a 1-2 (W-PM1).* This is the most-graded
  characteristic of the postmortem. The reviewer is looking for
  honesty about specific things you would now decide differently.
- *Name your own behaviour (M-PM3).* Examples from MERIDIAN
  shape: "I let the dependency-confirmation meeting with the data
  platform team end without pushing for a real start date for
  Asha; I accepted 'we'll see' as a status for two weeks before
  re-escalating. Next project I will refuse to leave that meeting
  without a date or a commitment to provide one by Friday."
  Specific, behavioural, repeatable.
- *"Decisions I'd unmake" (S-PM1) is the highest-signal section
  per the reviewer guidance.* Two examples are typical. The
  cited evidence pattern is decisions that were defensible at the
  time but, with the benefit of hindsight, you would now reverse.
  "I sequenced Customer C first in the original rollout plan
  because their bug rate would be a useful canary; with hindsight,
  starting with the noisiest customer also primed them to find
  bugs in scope they would not have exercised in production, and
  that consumed disproportionate team capacity in launch week."
- *Distinguish process / people / structural (M-PM4).* The three
  categories produce different action items. Process: cadence,
  templates, working agreements. People: training, mentoring,
  pairing. Structural: charter format, dependency tracking,
  RACI. Lumping them together means the action items end up
  un-actionable.
- *Action items ≤ 5, each with owner + date (M-PM2).* Postmortems
  with 18 action items produce zero changes. Five is the rough
  ceiling for what survives 6 weeks of contact with normal work.
- *6-week follow-up scheduled (M-PM6).* Without it, the action
  items evaporate. The follow-up is a 30-minute sync to ask: did
  this happen? If not, why? The rubric L5 evidence is action
  items specific enough that the 6-week follow-up can produce a
  clear yes/no per item.
- *Blameless, named-and-anonymised behaviours (W-PM2).* "The data
  platform team did not deliver on time" is blame. "The
  cross-team dependency-confirmation meeting failed to surface
  a real start date because the format allowed soft commitments
  to pass" is structural. Same fact; different frame; different
  next-quarter outcome.

**Where points are typically lost:** "we shipped, here are some
minor improvements"; naming individuals; no action items with
owners; no 6-week follow-up; no "decisions I'd unmake" section;
no behavioural item about the learner themselves.

### Kickoff deck (`08-kickoff-deck.md`) and summary (`00-summary.md`)

Both are short; both punch above their length.

The **kickoff deck outline** is the artifact your sponsor sees you
operate from in the kickoff meeting. It should follow the agenda
in `playbook.md` §3 (frame, goal, success criteria, stakeholder
map walkthrough, resource confirmation, top risks, cadence,
action items). One Markdown section per agenda block; bullet-level
content; explicit facilitation notes for "ask each partner team
lead to confirm in their own words" beats.

The **one-page summary** is the cover sheet for any stakeholder
read-out. Five sections, each one short paragraph: what is the
project, what is success, who owns it, where we are today (in
simulation: "as of week N of 16"), what we need from the reader.
A reviewer reads this first; it sets expectations for the whole
package.

## 3. Validation steps

The validation gates are at three levels. Walk them in order.

### Per-artifact validation (apply to each deliverable)

Use the validation-gate checklists in `STEP_BY_STEP.md`. Each
artifact's "Validation gate" subsection lists the boxes that must
all check before moving on. For example, the charter must have:
goal + ≥ 3 measurable success criteria + ≥ 3 explicit non-goals +
DACI matrix + resource commitments + timeline + milestones + 5
sign-offs (real or simulated).

In addition, every artifact must include:

- the metadata header (Owner / Project codename / Last updated /
  Project arc / Status / Reviewed by) from `deliverables/README.md` §2;
- a `## When This Design Would Fail` section near the bottom with
  3-5 bullet enumeration of conditions under which the artifact
  stops working (M-DL2);
- cross-references to the other artifacts by ID (e.g. risk
  register entries reference dependency IDs; status updates
  reference risk IDs; launch plan references LRR template) (M-DL3).

### Cross-artifact integrity check

Read the package end-to-end and verify:

- Risk register entries reference the dependency IDs they are
  derived from. Example: R02 ("Asha cannot start until week 5")
  should reference D02 ("Audit log schema"), since R02 is what
  makes D02 fragile.
- Status updates reference risk IDs and dependency IDs explicitly
  by ID, not by paraphrase. "R02 → score 16 → 18" is the format.
- Launch plan references the LRR template by section name. The
  LRR template references rollback criteria by phase from the
  launch plan.
- Postmortem timeline events tie back to specific status-update
  weeks ("Week 4: status flagged R02 materialising"). A
  postmortem timeline that disagrees with the simulated status
  updates is a sign the documents were written in isolation.

### Reviewer-simulation check

Read the deliverables in the reviewer's stated order
(`deliverables/README.md` §5): summary → charter → postmortem →
status updates → launch plan → risk register → dependencies →
stakeholder map. After each, ask the question the reviewer asks:

- After **summary**: can I describe the project in three sentences?
- After **charter**: do I know who owns what, what success is, and
  what is *not* in scope?
- After **postmortem**: did the learner name a behaviour of their
  own they would change?
- After **status updates**: did weekly communication produce
  decisions, or just describe state?
- After **launch plan**: would I, as the rollback DRI, know what
  to do without asking?
- After **risk register**: are risks live, or paper?
- After **dependencies**: is the critical path identified and is
  the inverse map present?
- After **stakeholder map**: is there a named anti-surprise plan
  for at least one high-influence + low-interest stakeholder?

A "no" answer to any of these is below L4 on the corresponding
rubric dimension.

### Time-budget check

`STEP_BY_STEP.md` notes that a submission < 65 hours probably
skipped stakeholder 1:1s or the rollback dry-run, and > 95 hours
over-built the tracking system or templates. Both are deductions
in the rubric's "Bonus considerations" section. A well-shaped
submission lands in the 75-85 hour band; the leadership is the
work, not the documents.

## 4. Rubric or review checklist

Grading happens on the six dimensions in `rubric.md`. The pass
bar is average ≥ 4.0 with no dimension < 3. Below is the
review checklist mapped to those dimensions.

| Dimension | L4 evidence to look for | L5 evidence to look for |
|---|---|---|
| 1. Charter clarity | Sign-offs from all 5 team leads + sponsor. Success criteria verifiable by someone other than the DRI. Non-goals address things stakeholders would assume in scope. "What would cause cancellation" statement present. | Sponsor can describe the project, success bar, and decision rights in 60 seconds without referring to the doc. Charter has survived a difficult stakeholder objection (real or simulated). Pre-mortem reference present. |
| 2. Stakeholder management | ≥ 1 high-influence + low-interest stakeholder has a named anti-surprise plan. Stakeholder 1:1s have been conducted; concerns logged. | Engagement has produced visible scope or risk adjustments. A Keep-Informed stakeholder surfaces a risk you would not have caught. |
| 3. Dependency rigor | Confirmation meetings completed with all partner teams. Critical path identified. Weekly review embedded in cadence. At-risk dependencies trigger documented escalation within 5 business days. | Inverse map present. External vendor dependencies tracked with same rigour + fallbacks. Decoupling investments named. ≥ 2 dependency status changes triggered re-planning; ≥ 1 escalation prevented downstream miss. |
| 4. Risk discipline | Risks have been demoted or escalated over the arc. Mitigations have owners + due dates. Top 3 risks in every weekly status. | One politically uncomfortable risk is present. One risk closed because mitigation worked and leading indicator is clean. One new risk identified mid-arc from signal the original register wouldn't have surfaced. |
| 5. Communication effectiveness | Each status update names top 3 risks + changes. "Decisions needed" section in each. Midpoint stakeholder review structure documented. | Status updates produced documented decisions. Customer-facing register differs from internal. A skip-level reading any single update can describe current state in 60 seconds. |
| 6. Launch & postmortem | Customer-specific validation documented. War-room has named slots + comms + decision logging. Rollback dry-run scheduled or done. Postmortem names ≥ 1 of the learner's own behaviours to change. | Rollback criteria tested in dry-run. Postmortem distinguishes process / people / structural. "Decisions I'd unmake" is honest and specific. 6-week follow-up scheduled. Action items implementable next quarter. |

**Bonus considerations** (not scored, noted in feedback):

- (+) Made a visible leadership choice (escalation, scope-tightening,
  rollout-sequence change) that was uncomfortable but right.
- (+) Conducted the rollback dry-run.
- (+) Postmortem names ≥ 1 of the learner's own behaviours.
- (−) Over-engineered the dependency tracker or status templates
  (> 95 hours total).
- (−) Skipped stakeholder 1:1s, the risk-ID session, or the
  postmortem.

## 5. Common mistakes

The mistakes below recur across submissions. None is a single
deliverable failure — each is a pattern that, if present, cascades
across multiple dimensions.

1. **Producing the artifacts as documents rather than as the
   operating system for the project.** The reviewer is grading on
   evidence the artifacts were used, not on completeness. A
   complete-but-passive tracker scores 2; a less-complete but
   actively-driven tracker scores 4 (rubric "Common reviewer
   mistakes").

2. **All-green simulated arc.** Status updates that report "on
   track" every week miss the entire point of the simulation. The
   synthetic brief is deliberately seeded with realistic
   slippage (data platform engineer's late start, the mid-project
   discovery of an additional auditor control, the noisy customer
   surfacing bugs in launch week). A submission that smooths these
   over is grading itself at L1-L2.

3. **Charter with success criteria stated as activities.** "Build
   the audit logging pipeline" is an activity. "Audit logging
   meets schema X across all gateway requests with ≥ 99.99 %
   capture rate" is a verifiable outcome. The rubric caps at L2-L3
   if criteria are activities.

4. **Treating partner-team slippage as the learner's failure.**
   The learner is graded on how they responded to the slippage,
   not on whether partners delivered. A slippage that is escalated
   early, results in a renegotiated scope, and is reflected in
   the next status update is a *win*, not a failure.

5. **Skipping stakeholder 1:1s because "I know what they think."**
   You do not. The 1:1s are where you discover what your DX lead
   actually cares about (likely the gateway interface contract,
   not the launch), what your data platform lead's other-project
   load actually is, and what your sponsor's red lines actually
   are. Skipping them produces a stakeholder map that reads
   plausible but does not survive contact with week 4.

6. **Risk register as historical worry.** Risks accumulate but
   never close. No risk demoted, no risk added mid-arc. Caps at
   L2. The fix is the 3-week rule: a risk does not sit on the
   register more than 3 weeks without an owner-driven action; if
   it does, either escalate it or close it.

7. **Status updates that read like project descriptions.** "This
   week the team continued work on the audit logging integration"
   is a paraphrase of the work; it produces no decisions. The
   format that produces decisions is: TL;DR colour, on-track
   bullets, at-risk bullets, decisions needed, top 3 risks with
   change, next 2 weeks.

8. **Rollback criteria that require judgement.** "If things look
   bad, roll back" is the rubric's named L1 anti-pattern. The
   correct shape is "if [metric] exceeds [threshold] for
   [duration], roll back" or "if [customer named contact]
   requests revert in writing, comply within [time]."

9. **Postmortem that does not name a behaviour of the learner.**
   The single most-flagged postmortem failure mode. The reviewer
   guidance explicitly says: "Missing the postmortem's 'decisions
   I'd unmake' section — this is often the highest-signal part of
   the entire submission." A postmortem without one is graded as
   not-honest, regardless of how complete the rest of the document
   is.

10. **Producing 12+ files because "I thought of another artifact
    that might help."** The deliverables README is explicit: 11
    files. A 12th file is over-building. The leadership is the
    work, not the documents about the work.

## 6. References

### Local exercise context (primary)

The following live in the paired learning repo at
`ai-infra-team-lead-learning/projects/project-04-platform-project/`
and are the authoritative source for templates, the synthetic
project brief, and the rubric. Cite them by section.

- `README.md` — project framing, learning outcomes, deliverable
  inventory.
- `requirements.md` — MoSCoW-prioritised requirements (M / S / C /
  W) per artifact. The "must" rows are the rubric L3 floor.
- `playbook.md` — templates and facilitation scripts:
  - §1 — synthetic project brief (MERIDIAN, the three named
    customers, partner teams, allocation, constraints)
  - §2 — project charter template
  - §3 — kickoff agenda + facilitation script
  - §4 — stakeholder map + worked example
  - §5 — stakeholder 1:1 script + interview questions
  - §6 — dependency tracking system templates (3 formats)
  - §7 — cross-team RACI template
  - §8 — dependency confirmation meeting script
  - §9 — risk register template + risk-ID session structure
  - §10 — weekly risk review structure
  - §11 — communication plan template + audience-specific status
    templates
  - §12 — worked-example weekly status updates (weeks 1, 4, 8, 12)
  - §13 — midpoint stakeholder review structure
  - §14 — launch plan template
  - §15 — LRR template
  - §16 — rollback criteria patterns
  - §17 — launch-day war-room structure
  - §18 — project postmortem template + facilitation
  - §19 — difficult-conversations scripts
- `STEP_BY_STEP.md` — week-by-week guide with per-week time
  budgets and validation gates.
- `rubric.md` — six-dimension rubric with L1-L5 sample evidence
  per dimension, plus reviewer guidance and bonus considerations.
- `deliverables/README.md` — submission inventory, structural
  requirements (metadata header + "When This Design Would Fail"
  section), reviewer reading order.

### Cross-track references in this repo

- `SOLUTION_OVERVIEW.md` — track-level design rationale for the
  team-lead solutions, including the framing of operations as the
  foundation that creates space for the rest of leadership work.
- `modules/mod-701-team-operations/SOLUTION.md` — operating-rhythm
  rituals that the launch plan's war-room and post-launch
  monitoring sit on top of.
- `modules/mod-703-project-roadmap/SOLUTION.md` — roadmap-level
  context for why MERIDIAN was a Q3 commitment.
- `modules/mod-704-cross-team-coordination/SOLUTION.md` — the
  cross-team coordination patterns that this project applies to a
  single 16-week arc.
- `modules/mod-702-people-management/SOLUTION.md` — the team-side
  people work (parental leave coverage, KT planning) that the
  risk register and status updates depend on.

### Recommended outside reading (referenced in learning repo §9)

- Tom DeMarco, *The Deadline* — narrative-form treatment of
  project leadership trade-offs.
- Mike Cohn, *Agile Estimating and Planning* — for the planning
  cadence that the dependency tracker and status updates ride on.
- Edmond Lau, *The Effective Engineer*, ch. 8-10 — high-leverage
  activities relevant to cross-team work.
- Will Larson, *An Elegant Puzzle*, ch. 8-9 — organisational
  debt and cross-team patterns.
- David Marquet, *Turn the Ship Around* — for the delegated-
  decision-making patterns that DACI formalises.

## When This Design Would Fail

This solution document is calibrated against the synthetic
MERIDIAN project and the rubric as written. It would no longer
serve as the right reference if:

- The learning-repo brief changes substantially — new partner
  teams, different customer mix, different regulatory regime —
  in which case the worked rationale (R02 about Asha, R09 about
  the Customer B auditor, the rollout-resequencing decision in
  week 12) would need to be re-anchored against the new brief.
- The rubric is revised — the L4/L5 evidence patterns in §4
  reference specific rubric language that would drift.
- The deliverables inventory in `deliverables/README.md` is
  restructured — file names and the reviewer reading order are
  referenced explicitly throughout.
- The learner is leading a *real* cross-functional project
  rather than the simulation, in which case the worked examples
  here are still useful for what-good-looks-like but should not
  override real-project constraints (timelines, named people,
  customer specifics).
- The track is being applied outside the AI-infra context — the
  artifact shapes generalise, but the specific failure modes
  (auditor controls, EU residency, GPU-cost dashboards) are
  AI-infra-flavoured and would need substitution.
