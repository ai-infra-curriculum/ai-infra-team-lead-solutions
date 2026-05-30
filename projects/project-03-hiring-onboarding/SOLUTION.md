# SOLUTION — Project 03: Hiring & Onboarding Pipeline

> Read this *after* you have attempted the project. The "solution" is
> not source code — it is the worked reference set, the decision
> rationale behind each design choice, and the grading rubric you can
> hold your own submission against.
>
> **Owner:** Team-lead solutions
> **Tracks against:** `ai-infra-team-lead-learning/projects/project-03-hiring-onboarding/`
> **Reading order:** start with §1 to align on what passing looks like;
> use §2 as a worked answer set; use §4 (rubric) and §3 (validation
> steps) before you self-grade; use §5 as a pre-mortem.

## 1. Solution overview

### What the project is asking for

The project asks the learner to design and write the team's full
hiring and onboarding pipeline for the same hypothetical 8-engineer
ML infrastructure team carried through Projects 01 and 02. The
output is a set of nine production-ready Markdown artifacts the
learner could hand to a recruiter, hiring panel, or new hire
tomorrow.

Submission inventory (from `deliverables/README.md` §1):

| # | File | Artifact |
|---|---|---|
| 0 | `00-summary.md` | One-page summary of the pipeline |
| D1 | `01-job-ladder-and-roles.md` | Job ladder + ≥2 role profiles |
| D2 | `02-competency-rubrics.md` | 5-7 competencies with E4-E7 anchors |
| D3 | `03-interview-loop.md` | Loop design + per-stage purpose + question banks |
| D4 | `04-bar-raiser-calibration.md` | Bar-raiser + calibration + 6-month look-back |
| D5 | `05-onboarding-30-60-90.md` | 30/60/90 + day-1 + 1:1 + buddy/mentor |
| D6 | `06-scorecard-and-debrief.md` | Scorecard + debrief protocol + anti-bias prompts |
| Ops | `07-hiring-ops.md` | Sourcing, recruiter partnership, interviewer load |
| CX | `08-candidate-experience.md` | Pre-onsite brief + rejection templates + FAQ |

Each artifact must carry the metadata header and the
`## When This Design Would Fail` closer specified in
`deliverables/README.md` §2.

### What a passing submission looks like

The bar set by `rubric.md` is **average ≥ 4.0 across the six
dimensions, with no dimension < 3**. The six dimensions are:

1. Role specificity
2. Ladder calibration
3. Interview loop validity
4. Bar-raiser & calibration mechanics
5. Onboarding rigor
6. Operational realism

A passing learner has produced artifacts that satisfy four
concurrent stakeholders, named in `requirements.md`:

- A skip-level engineering director who needs the calibration story
  to hold across hiring managers.
- A recruiting partner who is shared at ~25% across 6 teams and
  needs the role profiles to make their pipeline cheap to filter.
- A peer team lead who could pick up the ladder and use it.
- A senior ML infra candidate whose decision to accept or decline
  will be shaped by the loop's coherence and the rejection
  experience for the candidates they will tell.

### Design philosophy (why these choices, not others)

The pipeline this solution recommends is built on five load-bearing
choices, each of which is explicitly defended in `requirements.md`
or `README.md`:

1. **Competency-based, not credential-based.** `requirements.md`
   §3 W-RP2 forbids "years of experience" as a primary filter and
   §4 M-CR2 requires level-by-level behavioral anchors per
   competency. The learner builds the loop around 5-7 named
   competencies with anchors observable in interview signal — not
   tenure proxies.
2. **Structured interviews, scored before the debrief.** The
   debrief protocol (`playbook.md` §7) requires written scorecards
   *before* the meeting and least-senior-first voice order during
   it. This is the single highest-leverage anti-anchoring
   mechanic the project teaches.
3. **Cross-team bar-raiser with a documented qualification path.**
   `requirements.md` §6 M-BR1 / M-BR5 require the bar-raiser to be
   from outside the hiring team. `playbook.md` §8 sets the
   observe-3 / co-run-2 / lead-supervised-1 qualification path.
   The point is not Amazon mimicry; it is preventing in-group bias.
4. **Calibration with a 6-month feedback loop.** `requirements.md`
   §6 M-BR3 requires a 6-month post-hire look-back; the loop's
   anchors get revised based on whether the interview score
   predicted actual performance. Without this, the loop is
   theater — graded `rubric.md` D4 explicitly checks for it.
5. **Candidate experience graded as a hard operational
   requirement.** §13 of the project `README.md` makes it
   explicit: "a hiring loop that produces 'good hires' and a
   terrible candidate experience is a failed loop." `rubric.md`
   D6 caps at 3 if the candidate-experience kit is missing.

The single most common failure mode (`README.md` §11) is
*template-copying*. A learner who lifts Square's or Patreon's
public ladder verbatim gets a 2 on Dimension 2. The work is
specificity, grounded in the team's actual ML infra context: GPU
scheduling, inference gateway, capacity coupling with finance.

## 2. Worked answer or implementation

This section gives a reference outline for each of the nine
required files — what content they must include, what a strong
example of each piece looks like, and where in `playbook.md` the
canonical template lives. Use this as a model. Do not paste it in
verbatim — `rubric.md`'s reviewer guidance penalises
copy-paste submissions.

### 2.0 `00-summary.md` — one-page summary

**Purpose:** make the whole pipeline legible in 3 minutes for an
executive or peer team lead (`requirements.md` §11 S-DL1).

**Required structure (≤ 1 page):**

- One-sentence statement of what the pipeline produces.
- The two open roles, each in one sentence (level + capacity gap
  filled).
- The loop in one diagram or list (8 stages, ≤ 8 hrs candidate
  time, named bar-raiser stage).
- The onboarding promise in one sentence ("on-call ready at day
  90; primary owner of one workstream").
- The candidate-experience commitment in one sentence ("5
  business days to any decision; substantive written feedback to
  every rejected onsite candidate").
- A "When This Design Would Fail" closer (3-5 bullets).

A reviewer reading only `00-summary.md` should be able to
correctly predict the structure of every other artifact.

### 2.1 `01-job-ladder-and-roles.md` — D1

**Worked role profile (GPU/serving senior, E5 target):**

The strong example states the seat in one paragraph, references
the Project 02 capacity model, and grounds the first-year
outcomes in concrete observable behaviors:

```
## Role: Senior Engineer — GPU/Serving Performance (E5)

What this person will own
-------------------------
The GPU memory management and serving co-tenancy subsystem of the
inference gateway. Currently absorbed in fragments by the staff
engineer and one senior; this seat consolidates ownership. Will
partner with the model team on per-variant memory budgets and
with finance on the capacity reservation model.

What success looks like in 12 months
1. p99 cold-start latency on the top-10 model variants is < 600ms
   measured weekly, with a runbook the on-call can execute.
2. The team has shipped one published internal design doc on the
   serving co-tenancy strategy that the platform team adopts as
   the default for any team running >2 model variants.
3. A documented capacity-reservation model is in place that
   finance reviews quarterly; FY savings vs. the FY-1 spend
   trajectory are measurable.

Must-have competencies (≤ 5)
- Distributed systems judgment (at E5 anchor)
- Debugging (at E5 anchor; specifically GPU + memory)
- Reliability / operational mindset (at E5 anchor)
- ML literacy (at E5 anchor; specifically serving, not training)
- Collaboration (at E5 anchor)

Nice-to-have competencies
- Technical writing at E6 anchor (would up-level over time)
- Direct vendor experience with NVIDIA Triton or vLLM in
  production (not a prerequisite; not a tiebreaker)

Non-attributes (signals that disqualify or down-level)
- Cannot articulate the latency / throughput / accuracy
  tradeoff of dynamic batching from first principles
- Has only operated systems they did not own end-to-end
- Treats GPU as interchangeable with CPU for cost modelling

Who this role is wrong for
- Engineers whose strongest work has been on offline batch
  training systems — the failure modes are not the same.
- Engineers who want to lead a team within 6-9 months — this is
  an IC seat with deep area ownership.
- Engineers who need a high-cadence ticket queue — the work is
  longer-arc, more design-doc-heavy, more cross-functional.

Growth profile (24 months)
Promotion track to E6 / Staff is realistic if the person grows
multi-team multiplicative influence: setting platform defaults
that other teams adopt without a forcing function. Lateral move
to the model-platform team is available if their interest skews
to model lifecycle. Off-ramp: if the seat turns out to be more
research-adjacent than the candidate wants, the cross-team
acceleration team has an open seat at the same level.

Why this seat exists
Project 02 capacity model shows ~1.0 FTE-equivalent of GPU
performance work currently being absorbed across staff + one
senior. That is unsustainable through the planned 2x request
volume in the back half of the year. This seat consolidates the
work and creates the design-doc surface area we currently lack.
```

A second role profile (gateway/distributed-systems senior, also
E5) follows the same structure but anchors against gateway
sharding, multi-region routing, and the staff engineer's
overflow load.

**Worked job ladder — E5 → E6 transition (the most-graded piece):**

`rubric.md` D2 specifically grades whether the most-confused
transition is written up. The strong example anchors each
behavioral difference in ML infra work, not abstract engineering:

```
## Most-Confused Transition: E5 → E6 (Senior → Staff)

What concretely changes:

- Scope of ownership. E5 owns a major area inside the team
  (one or two subsystems). E6 owns a concern that spans
  multiple teams' contributions (e.g., the inference stack
  across model serving, gateway, and capacity reservation).

- Time horizon of decisions. E5 sets quarterly direction
  within their area. E6 sets multi-quarter direction that
  other teams' staff engineers build off of.

- Form of influence. E5 influence is through design review
  feedback and project leadership. E6 influence is through
  setting defaults that other teams adopt without a forcing
  function. "Their position becomes the team's position" is
  E5; "their position becomes the org's default" is E6.

What new behaviors must appear:

- Authors a document that becomes another team's reference.
  Not "we read it" — "we follow it."
- Drives a roadmap conversation that crosses team boundaries
  and ends with named owners on other teams.
- Identifies a problem the manager has not seen yet, then
  drives alignment on the right response.

Common trap: "most experienced senior" mistaken for staff.
Tenure isn't staff scope; cross-team multiplicative influence is.
```

**Coverage check.** The strong artifact also includes:

- Each level (E4-E7) covers the 4 dimensions named in
  `requirements.md` §3 M-JL1 (technical scope, autonomy,
  influence, leadership/mentorship), with ≥ 3 behavioral anchors
  per dimension per level.
- A "common traps" section per level (`requirements.md`
  M-JL3).
- A "what this level does NOT do" annotation per level (S-JL1).
- A `## When This Design Would Fail` closer.

Cross-references to D2 (rubrics), D3 (loop), D5 (onboarding).
**Length target:** 4-6 pages.

### 2.2 `02-competency-rubrics.md` — D2

The strong artifact defines exactly the five required minimum
competencies plus 1-2 chosen ones, with E4-E7 behavioral
anchors and a miscalibration risk note per competency.

**Worked anchor — Debugging, E5:**

> Given an ambiguous failure scenario (e.g., "p99 spiked from 80ms
> to 220ms over the last 6 hours, no deploy"), identifies 2-3
> hypotheses ranked by likelihood and articulates an investigation
> order with explicit cost (developer-minutes to test) and value
> (probability of being the cause × magnitude of impact) reasoning.
> Knows when to stop investigating and ask for help (typically
> 30-60 minutes of independent investigation before escalating).
> Uses uncommon tools (eBPF, kernel traces, GPU profilers) when
> warranted by the hypothesis, not by reflex.

**Worked miscalibration risk — ML Literacy:**

> This is the most often-faked competency. Candidates name-drop
> frameworks (Triton, vLLM, Ray) without having shipped the
> system. The probe is not "have you used X"; it is "what failure
> mode did you see in production that you would not have predicted
> from the docs, and what did you do about it." If the candidate
> cannot produce one such moment, the depth claim is unsupported.

**Other anti-bias inclusions:**

- A competency-to-stage map (S-CR1): which stage primarily tests
  which competency. No two stages test the same competency the
  same way.
- An anti-pattern bank (S-CR2): 3-5 behaviors that look like
  signal but aren't (e.g., "speaks confidently about distributed
  systems but cannot explain CAP tradeoffs from first principles
  when asked to derive them"; "credits team for outcomes
  uniformly, never names a personal decision they made").

**Coverage check:**

- 5-7 competencies named (must include distributed systems
  judgment, debugging, reliability mindset, ML literacy,
  collaboration; per M-CR1).
- E4 / E5 / E6 / E7 anchors per competency (M-CR2).
- Each anchor is concrete and observable in an interview signal
  (M-CR3).
- Miscalibration risk note per competency (M-CR4).
- "Culture fit" is explicitly **not** a competency (W-CR1).
- `## When This Design Would Fail` closer.

**Length target:** 3-5 pages.

### 2.3 `03-interview-loop.md` — D3

The strong loop is the eight-stage structure in `playbook.md` §4,
totalling ~6.5 hours of candidate time (under the 8-hour cap from
M-IL5). The strong artifact restates the loop, then for each
stage provides:

- Purpose statement (M-IL2)
- Target competencies (M-IL1)
- Time and format
- Interviewer "what to look for" guide (M-IL6)
- Question bank ≥ 3 questions with **strong / weak / red-flag
  response signals** per question (M-IL3, supported by
  `playbook.md` §5)
- Scoring rubric mapped to the competency anchors from D2

**Worked stage purpose — Stage 6 (Cross-Functional, 60 min):**

> This stage tests whether the candidate can work effectively with
> people who are not engineers — ML researchers, product, finance.
> The decision it supports is: would a research scientist who has
> worked with this person say their infra partner *listened* and
> *negotiated* rather than *educated*? No other stage tests this.
> We would not learn this from the system-design stage (technical
> peer collaboration) or from the pair-debugging stage (real-time
> co-execution). The risk this guards against is producing a hire
> whose technical depth is real but who cannot operate at the
> seam between research and infra — which is exactly where ML
> infra work lives.

**Worked question (cross-functional stage), with response signals:**

> "Tell me about a time you disagreed with a research team's
> choice that affected the infrastructure you owned. What
> happened?"
>
> Strong: specific situation, specific stakes, acknowledgement
> of the other team's legitimate concerns, evidence of a
> compromise or shifted position (theirs or yours), discussion
> of what they would do differently now.
>
> Weak: "we worked it out" without specifics, all-blame-on-the-
> other-team narrative, cannot name what they would change.
>
> Red flag: frames the other team as technically inferior ("they
> didn't understand the systems side"); no examples of being
> wrong; describes the other team in tribal "they / us" terms.

**Coverage check:**

- 5+ stages including recruiter screen, technical screen,
  multi-stage onsite, HM loop, **bar-raiser stage** (M-IL4).
- Total candidate time ≤ 8 hours (M-IL5).
- A cross-functional stage exists (M-IL7).
- A pair-programming or system-design stage that resembles real
  work, not LeetCode (S-IL1).
- No trivia, no whiteboard-under-time-pressure, no unstructured
  "chat" interviews without rubrics (W-IL1 / W-IL2 / W-IL3).
- A candidate-facing "what to expect" doc referenced from D8
  (S-IL3).
- `## When This Design Would Fail` closer.

**Length target:** 6-8 pages.

### 2.4 `04-bar-raiser-calibration.md` — D4

The strong artifact uses `playbook.md` §8 / §9 / §10 verbatim as
templates but ground each in the team's actual operating reality:
8 engineers today, 2 new hires planned, shared 25% recruiter.

**Worked bar-raiser veto escalation:**

> Bar-raiser veto triggers a hiring-committee review (hiring
> manager, bar-raiser, recruiting leader, one other bar-raiser).
> Committee decides by majority. Bar-raiser veto is not unilateral
> (M-BR1, W-BR1). Bar-raiser veto rate is a tracked metric;
> bar-raisers whose veto rate exceeds 3x the average are
> themselves reviewed for calibration drift (`playbook.md` §8).

**Worked calibration round agenda:** quarterly, 90 minutes
(`playbook.md` §9), with anonymized scorecards, recent passes,
and the 6-month look-back data as the three inputs.

**Worked 6-month look-back template** (`playbook.md` §10): each
hire reviewed at the 6-month mark for whether the interview
score predicted actual performance. Anchor revisions and
individual interviewer feedback come out of this.

**Coverage check:**

- Bar-raiser role: who, training path, veto power, escalation
  (M-BR1).
- Cross-team requirement (M-BR5).
- Calibration ≥ quarterly (M-BR2).
- 6-month look-back template (M-BR3).
- Level-down offer mechanics (M-BR4).
- Pre-debrief independent scoring documented (S-BR1).
- Shadow-3 / co-run-2 / supervised-1 qualification pipeline
  (S-BR2).
- `## When This Design Would Fail` closer.

**Length target:** 2-3 pages.

### 2.5 `05-onboarding-30-60-90.md` — D5

The strong onboarding plan follows the template in `playbook.md`
§11, applied to the worked sample (Senior GPU/Serving Engineer).
Each milestone has *observable* success criteria — not "be
productive."

**Worked Day-30 milestone:**

```
Day-30 success criteria
- Can explain the inference gateway's hot path on a whiteboard
  unprompted.
- Has shipped ≥ 3 PRs of increasing scope (typo / runbook / small
  feature).
- Has scoped a starter project with the manager (e.g., "evaluate
  vLLM as a serving backend for model X — 2-week scoped
  investigation").
- "What surprised me" exercise written up (S-ON2).
- 30-day self-evaluation submitted; manager evaluation returned
  (S-ON1).
```

**Worked manager 1:1 cadence (M-ON8):**

- Week 1: daily 15 min ("how's it going, what's confusing, what
  do you need?").
- Weeks 2-4: 30 min biweekly + async check-in.
- Weeks 5-12: standard weekly 30 min 1:1.

Topics shift by phase: orientation → settling-in → contribution
(`playbook.md` §13).

**Buddy / mentor / manager distinction (M-ON6):**

| Relationship | Owns | Cadence | Performance role |
|---|---|---|---|
| Manager | Goals, growth, performance, compensation | Weekly | Primary |
| Buddy | Practical integration, codebase navigation, social context | Weekly for 4 wks then biweekly | None |
| Mentor | Career, technical growth (longer arc) | Monthly | None |
| On-call shadow | On-call competence | Per rotation × 2 | Competence sign-off only |

**Coverage check:**

- Day-1 inventory: laptop, accounts, charter, ladder, on-call
  playbook, working agreements, buddy meet, manager 1:1
  (M-ON2).
- 30-day / 60-day / 90-day milestones each have observable
  criteria (M-ON1, M-ON3, M-ON4, M-ON5).
- Buddy + mentor + manager are explicitly distinct (M-ON6).
- Week-1 reading list curated (M-ON7).
- Manager 1:1 cadence + structure for first 90 days (M-ON8).
- New hire does **not** go primary on-call before week 8 (W-ON2).
- Two 30/60/90 variants — one per role profile — referenced
  (S-ON3).
- `## When This Design Would Fail` closer.

**Length target:** 3-4 pages.

### 2.6 `06-scorecard-and-debrief.md` — D6

The strong artifact reproduces the scorecard template
(`playbook.md` §6) and the debrief script (`playbook.md` §7).

**Decision rule (M-DB3):**

> Hire = majority of interviewers vote hire AND bar-raiser
> approves AND hiring manager approves. Split panel default =
> NO-HIRE. The asymmetry is deliberate — hires are 10x harder to
> reverse than declines.

**Anti-bias prompts (M-DB5), read aloud at every debrief:**
similarity, halo / horns, anchoring, recency, confirmation
(verbatim list from `playbook.md` §7).

**Reject-reasons taxonomy (M-DB4):**

- "Below bar on [competency] with specific evidence [X]" — the
  preferred form.
- Not allowed: "didn't feel like a fit"; "vibes-based"; "culture
  fit"; "team chemistry."

**Coverage check:**

- Scorecard: competency-by-competency, evidence-cited verbatim
  or paraphrased, hire/no-hire vote, level recommendation
  (M-DB1).
- Debrief order of voice (least-senior first), evidence-before-
  conclusion, anti-bias mechanics, split-panel decision rule
  (M-DB2).
- HM does **not** state position first (W-DB1).
- Time-boxed 45 min (S-DB1).
- Written debrief summary stored (S-DB2).
- `## When This Design Would Fail` closer.

**Length target:** 2 pages.

### 2.7 `07-hiring-ops.md` — Ops doc

The ops doc captures the operational rhythm that holds the loop
together with one shared recruiter at 25% FTE.

**Worked recruiter intake (`playbook.md` §16):** role profile
link, comp band, target start date, top-5 sourcing companies,
top-3 communities, anti-fit signals, pass-along feedback from
recent declines so the recruiter knows the bar.

**Worked interviewer load policy (M-OP3):**

> Maximum 2 interview hours per engineer per week, averaged over
> 4 weeks. The hiring manager owns balancing across the team
> using a shared rotation board. Interviewers can opt out for a
> sprint by declaring the conflict.

**Worked training requirement (M-OP4):**

> No one interviews without (a) one calibration round and (b)
> shadowing ≥ 2 interviews of their stage with feedback from a
> calibrated interviewer. "They were senior at their last
> company" is not training (W-OP1).

**Coverage check:**

- Sourcing channels + expected mix (M-OP1).
- Recruiter weekly sync structure, intake template, feedback
  loop after each loop (M-OP2).
- Interviewer load policy (M-OP3).
- Interviewer training requirement (M-OP4).
- Diverse-slate consideration where jurisdictionally
  appropriate (S-OP1).
- `## When This Design Would Fail` closer.

**Length target:** 1-2 pages.

### 2.8 `08-candidate-experience.md` — CX kit

The strong artifact is the most-differentiated piece. It treats
candidate experience as an operational commitment.

**Worked response SLA (M-CE1):**

> Candidates hear back within 5 business days of any stage and
> within 10 business days of final decision. Misses are tracked
> as ops debt and reviewed in the weekly recruiter sync.

**Worked rejection template (M-CE2; from `playbook.md` §15):**
the post-onsite rejection contains at least one sentence of
substantive, specific feedback. Generic "we've decided to go a
different direction" language is explicitly forbidden by
`deliverables/README.md` §6.

**Worked accommodations stance (M-CE5):**

> Candidates can request any timing, format, or break
> accommodation by emailing the recruiter. We do not ask the
> reason. The loop is designed to support remote, asynchronous,
> and otherwise accommodated formats without prejudice.

**Worked compensation transparency (M-CE4):**

> The compensation band is stated in the role profile and
> communicated again in the pre-onsite brief. Specifics are
> discussed at the close-out conversation or post-offer,
> whichever comes first. We do not ask compensation history
> (W-CE2).

**Coverage check:**

- Response SLA (M-CE1).
- Written substantive rejection (M-CE2).
- Pre-onsite candidate brief (M-CE3).
- Compensation transparency policy (M-CE4).
- Accommodations provision (M-CE5).
- Candidate FAQ (`playbook.md` §15).
- No ghosting at any stage (W-CE1).
- No compensation-history questions (W-CE2).
- `## When This Design Would Fail` closer.

**Length target:** 2-3 pages.

### 2.9 Optional appendices (encouraged, not required)

`deliverables/README.md` §1 encourages three optional appendices:

- `appendix-difficult-conversations.md` — scripts for bar-raiser
  veto, down-level offer, calibration-drift conversation, 30-day
  off-track conversation (`playbook.md` §17 has the canonical
  set).
- `appendix-loop-flowchart.md` — Mermaid flowchart of the loop.
- `appendix-anti-patterns.md` — what *not* to do, with examples.

These move the submission from "competent" to "differentiated"
and are noted as **bonus considerations** in `rubric.md`
("Did the learner include something they explicitly chose *not*
to test, with reasoning?" +).

## 3. Validation steps

### 3.1 Submission completeness gate

Run through the `deliverables/README.md` §4 checklist:

- [ ] All 9 prescribed files present and named exactly.
- [ ] Each file has the metadata header (Owner / Last updated /
  Status / Reviewed by).
- [ ] Each file has the `## When This Design Would Fail` section.
- [ ] Cross-references present: ladder ↔ rubrics ↔ loop ↔
  debrief ↔ onboarding.
- [ ] 2+ role profiles each grounded in a specific capacity gap
  from Project 02 (or stated alternative).
- [ ] Ladder distinguishes E4 through E7 with concrete
  behavioral anchors.
- [ ] Loop totals ≤ 8 hours candidate time.
- [ ] Onboarding milestones are observable, not aspirational.
- [ ] Rejection templates contain substantive feedback (not
  generic).
- [ ] No artifact > 10 pages (W-DL1).

A submission missing any of these does not yet meet the bar for
review.

### 3.2 Week-by-week validation gates

The `STEP_BY_STEP.md` validation gates are the right
intermediate check. The learner cannot move to the next week
until the prior gate is met:

- **Week 1 gate:** 2 role profiles each tracing to capacity gap;
  ladder covers E4-E7 with 4 dimensions and ≥ 3 anchors per
  dimension; most-confused transition written up; a peer can
  articulate the E5/E6 difference in 30 seconds after reading.
- **Week 2 gate:** 5-7 competencies with E4-E7 anchors and
  miscalibration risk notes; loop with explicit stage sequence,
  time, format, target competencies; each stage has a unique
  purpose; question banks with strong / weak / red-flag
  response notes; total candidate time ≤ 8 hours.
- **Week 3 gate:** bar-raiser role + qualification path
  documented; calibration ≥ quarterly; 6-month look-back
  template exists; scorecard with evidence-cited requirement;
  debrief protocol with anti-bias prompts and split-panel rule;
  reject-reasons taxonomy normalized.
- **Week 4 gate:** 30/60/90 with observable milestones; Day-1
  checklist concrete; manager 1:1 cadence varies by phase;
  buddy / mentor / manager roles distinct; candidate brief,
  rejection templates, FAQ all written and substantive;
  recruiter partnership norms documented; interviewer load and
  training requirements documented.

### 3.3 Functional self-tests (steal these for the submission)

Run each of these self-tests against the finished submission:

1. **Recruiter filter test (D1).** Hand the two role profiles to
   someone who has never read about your team. Ask them, after 2
   minutes of reading, which of 8 plausible candidate
   one-liners they would advance. If they can't sort them, the
   profiles are too generic.
2. **Ladder distinction test (D1).** Ask the same reader, in
   their own words, what's different between a strong E5 and a
   weak E6. If they can't, you have one level pretending to be
   two.
3. **Loop reconstruction test (D3).** Without showing the
   `00-summary.md`, ask a peer team lead to list the 8 stages
   after reading the loop doc once. Mid-stage drift means the
   loop's structure isn't clear enough.
4. **Debrief simulation test (D6).** Run a 20-minute mock
   debrief with two colleagues using the protocol. Observe
   whether the anti-bias prompts produce visible behavior
   changes (e.g., someone walks back a number).
5. **Onboarding-self-narration test (D5).** Find a friendly
   senior engineer. Ask them, after reading the 30/60/90 plan,
   to describe their first 90 days back to you in 2 minutes
   *without re-opening the doc*. The `README.md` §8 success
   criterion is this exact test.
6. **Candidate-experience read-aloud test (D8).** Read the
   post-onsite rejection template aloud as if you were the
   candidate receiving it. If it would make you bitter, rewrite.
   If it would make you grateful, ship.
7. **Bar-raiser external-runnability test (D4).** Ask a peer
   team lead from another team whether they could run your
   bar-raiser stage using only what you've written. If they ask
   any clarifying question about scope of authority or veto
   escalation, you have a gap.

### 3.4 Cross-reference completeness pass

`requirements.md` §11 M-DL3 requires cross-references between
artifacts. Do a final pass to confirm at least:

- D1 (ladder) references the D2 anchors.
- D2 (rubrics) is mapped to D3 stages (the
  competency-to-stage map).
- D3 (loop) references the D6 scorecard and D4 bar-raiser
  stage.
- D5 (onboarding) references Project 01's on-call playbook for
  the on-call shadow step (`requirements.md` §11 M-DL3 example).
- D6 (scorecard) references the D2 competencies.
- D8 (CX) references the D3 loop for "what to expect."
- D7 (ops) references D3 (load), D2 (training), D4 (recruiter
  feedback from declines), and D8 (response SLA).

## 4. Rubric or review checklist

This rubric is a direct re-statement of `rubric.md` so the
learner can self-grade without flipping between repos.

### Dimension 1 — Role Specificity

| Level | What earns it |
|---|---|
| 1 | Generic JDs. "Years of experience" as a primary filter. |
| 2 | Lists responsibilities and technologies but no concrete seat. |
| 3 | Must-have / nice-to-have competencies, target level, concrete 12-month outcomes. |
| 4 | Profiles trace to capacity gaps from Project 02. Include "who this role is wrong for" with concrete anti-fit signals. |
| 5 | L4 *plus* growth profile, pre-screen self-assessment, redacted strong-candidate persona. A recruiter can immediately filter their pipeline. |

### Dimension 2 — Ladder Calibration

| Level | What earns it |
|---|---|
| 1 | Copied from a public source or generic. |
| 2 | Per-level expectations exist but anchors are paraphrases of each other. |
| 3 | ≥ 3 behavioral anchors per dimension. Anchors observable in interviews. |
| 4 | Anchors are ML-infra-specific. "Common traps" per level. Most-confused transition explicitly written. |
| 5 | L4 *plus* "what this level does NOT do" annotations, promotion-calibration narratives, visual ladder reference. |

### Dimension 3 — Interview Loop Validity

| Level | What earns it |
|---|---|
| 1 | Unstructured. No scoring rubric. |
| 2 | Stages exist but overlap or don't test the role's competencies. |
| 3 | 5+ stages, explicit competency targets, question banks, scoring rubrics. Total candidate time ≤ 8 hours. |
| 4 | L3 *plus* strong / weak / red-flag response signals. Bar-raiser stage. Cross-functional / behavioral stage. |
| 5 | L4 *plus* a stage that resembles real work (pair-debug on real codebase or grounded design). Candidate-empowerment mechanism (reverse-interview slot). |

### Dimension 4 — Bar-Raiser & Calibration Mechanics

| Level | What earns it |
|---|---|
| 1 | No bar-raiser; no calibration. HM decides alone. |
| 2 | Bar-raiser exists but undefined; calibration informal. |
| 3 | Bar-raiser + training path + veto mechanics. Calibration cadence ≥ quarterly. Hiring scorecard with evidence-cited requirement. |
| 4 | L3 *plus* 6-month post-hire look-back feeding calibration. Bar-raisers cross-team. Pre-debrief independent scoring. |
| 5 | L4 *plus* anti-bias mechanics in debrief, split-panel default of no-hire, down-level offer mechanics, bar-raiser veto-rate monitoring. |

### Dimension 5 — Onboarding Rigor

| Level | What earns it |
|---|---|
| 1 | No plan or aspirational language only. |
| 2 | Day-1 + week-1 covered; 30/60/90 vague. |
| 3 | 30/60/90 with observable milestones. Day-1 checklist. Manager 1:1 cadence. |
| 4 | L3 *plus* distinct buddy and mentor roles. Manager 1:1 cadence varies by phase. On-call shadow before primary. |
| 5 | L4 *plus* role-specific 30/60/90 variants. Self-evaluation paired with manager evaluation at each checkpoint. "What surprised you" feedback loop. 6-month onboarding review. |

### Dimension 6 — Operational Realism

| Level | What earns it |
|---|---|
| 1 | No ops plan, or assumes infinite recruiter / interviewer bandwidth. |
| 2 | Ops plan exists but missing components. |
| 3 | Sourcing channels + recruiter partnership + interviewer load + training requirement. |
| 4 | L3 *plus* candidate-experience kit (brief, substantive rejection templates, FAQ, accommodations, response SLA). Loop debrief → recruiter feedback loop. |
| 5 | L4 *plus* a CX commitment that costs the team operational time AND a measurement of whether it's being met. Diverse-slate goals where appropriate. Compensation transparency. |

### Bonus considerations (not scored; noted)

- (+) Built a feedback loop from post-hire performance back to
  interview design.
- (+) Included something the team explicitly chose *not* to
  test, with reasoning.
- (+) Identified a commonly-faked competency and added a
  specific probe for it.
- (–) Over-engineered the ladder (> 75 hours total).
- (–) Skipped the candidate-experience kit.

### Reviewer reading order (from `rubric.md`)

1. Role profiles. If generic, every other dimension caps at ~3.
2. Job ladder.
3. Interview loop.
4. Onboarding (most-skipped artifact; high signal).
5. Bar-raiser and ops.

## 5. Common mistakes

The failure modes below are drawn from `STEP_BY_STEP.md`,
`rubric.md`, `deliverables/README.md`, and the module SOLUTION at
`modules/mod-705-hiring-onboarding/SOLUTION.md`.

1. **Template-copying the job ladder.** Lifting Square's,
   Patreon's, or CircleCI's published ladder verbatim is a
   guaranteed 2 on Dimension 2 (`README.md` §11). The work is
   specificity. Anchors must reference ML infra work — GPU
   scheduling, inference gateway, capacity coupling — not
   abstract software engineering.

2. **Generic role profiles.** "Senior software engineer with
   strong distributed-systems skills" describes nothing.
   Specific seat, specific work, specific 12-month outcomes,
   traceable to a capacity gap from Project 02.

3. **Levels that don't distinguish.** If E5 anchors and E6
   anchors are paraphrases of each other, you have one level
   pretending to be two. The E5 → E6 transition is the most
   commonly mis-graded; write it up explicitly.

4. **Anchors written as values.** "Acts with ownership" is a
   value, not an anchor. "Owns outcomes through to production
   rollout including monitoring and follow-up" is an anchor.
   The test is whether two interviewers, with the same
   evidence, would score the same.

5. **Stages with overlapping purposes.** If two stages test the
   same competency the same way, you have one stage doing two
   interviewers' work. Each stage must have a unique purpose
   statement.

6. **Question banks without response signals.** Interviewers
   will score inconsistently. Anchor scoring with explicit
   strong / weak / red-flag signals per question.

7. **"Culture fit" as a competency.** Unmeasurable, biased, and
   in some jurisdictions illegal (`requirements.md` §4 W-CR1).
   Replace with specific behavioral competencies.

8. **Bar-raiser without a training path.** "Anyone senior can
   be a bar-raiser" produces calibration drift. Document the
   observe-3 / co-run-2 / supervised-1 path
   (`requirements.md` §6 S-BR2).

9. **Calibration without post-hire data.** Calibration becomes
   opinion-based, not evidence-based. The 6-month look-back is
   the single most important feedback signal (`README.md` §12).

10. **Hiring manager speaks first in debrief.** Anchoring
    ensures the rest of the panel justifies the HM
    (`requirements.md` §7 W-DB1). Reverse the order:
    least-senior first, HM closes.

11. **Split panel defaults to hire.** Inversion: split panel
    defaults to NO-HIRE (`playbook.md` §7). Hires are 10x
    harder to reverse than declines.

12. **Aspirational onboarding milestones.** "Be productive in
    30 days" is not a milestone. "Has shipped ≥ 3 PRs and can
    explain the gateway hot path on a whiteboard" is.

13. **On-call before week 8.** Anti-pattern. Unsafe for both
    the new hire and the customers (`requirements.md` §8
    W-ON2).

14. **Buddy = mentor = manager.** Different roles, different
    cadences, different scopes (`requirements.md` §8 M-ON6).
    Collapsing them removes the very distinction that makes
    onboarding work.

15. **Generic rejection templates.** "We've decided to go a
    different direction" is the worst experience and is
    explicitly forbidden (`deliverables/README.md` §6).
    Substantive feedback is the bar.

16. **Asking compensation history.** Illegal in many
    jurisdictions, biased everywhere (`requirements.md` §9
    W-CE2). Don't.

17. **Ghosting candidates at any stage.** Response SLA of 5
    business days is a hard requirement (`requirements.md`
    §9 M-CE1, W-CE1).

18. **"We don't do leetcode" without making the choice
    explicit.** `rubric.md` reviewer guidance notes that an
    omission counts as deliberate only if explicit. State what
    you chose not to test and why.

19. **Over-building the ladder past 75 hours.** Rubric notes
    this as a negative consideration. The project's time
    budget is 60 hours; ±10% is the band.

20. **Missing the "When This Design Would Fail" section** at
    the bottom of each artifact (`deliverables/README.md` §2).
    Reviewers grade against its presence and quality.

## 6. References

### Project-local sources (authoritative for this solution)

- `ai-infra-team-lead-learning/projects/project-03-hiring-onboarding/README.md`
  — project framing, business context, deliverables list,
  success criteria, and the two grading notes on specificity
  (§11) and calibration (§12).
- `ai-infra-team-lead-learning/projects/project-03-hiring-onboarding/requirements.md`
  — MoSCoW requirements (M / S / C / W) used as the authoritative
  per-artifact coverage checklist throughout §2 above.
- `ai-infra-team-lead-learning/projects/project-03-hiring-onboarding/playbook.md`
  — canonical templates for role profile, ladder, competency
  anchors, loop structure, scorecard, debrief, bar-raiser,
  calibration, look-back, onboarding plan, day-1 checklist,
  manager 1:1, buddy/mentor, candidate brief, rejection
  templates, recruiter partnership, and difficult-conversations
  scripts (sections 1-17 referenced inline above).
- `ai-infra-team-lead-learning/projects/project-03-hiring-onboarding/STEP_BY_STEP.md`
  — the 4-week breakdown and per-week validation gates used in
  §3.2 above.
- `ai-infra-team-lead-learning/projects/project-03-hiring-onboarding/rubric.md`
  — the six-dimension grading rubric re-stated in §4 above and
  the reviewer guidance used in §5.
- `ai-infra-team-lead-learning/projects/project-03-hiring-onboarding/deliverables/README.md`
  — submission inventory, metadata header requirement, and the
  "When This Design Would Fail" closer requirement.
- `ai-infra-team-lead-solutions/modules/mod-705-hiring-onboarding/SOLUTION.md`
  — the module-level rationale doc for the hiring/onboarding
  module, which the project capstone applies in concrete form
  (interview-loop, debrief, stakeholder-mapping, and
  90-day-onboarding sections especially).
- `ai-infra-team-lead-solutions/SOLUTION_OVERVIEW.md` — the
  track-level design philosophy ("defaults that survive bad
  days", "decisions explicit and revisitable", "people
  conversations are owned, not delegated") that informs how the
  artifacts are written, not just their content.

### Practitioner sources named in the project README §9

The project's README §9 names the following published sources
as the suggested reading. They are referenced here at name only;
factual claims in this solution are grounded in the project's
own documents above, not extracted from these sources.

- Lou Adler, *Hire With Your Head* — competency-based
  interviewing methodology referenced in `STEP_BY_STEP.md`
  pre-work and `requirements.md` §4 prerequisites.
- Geoff Smart & Randy Street, *Who* — structured-interview
  framework referenced in §4 prerequisites.
- Camille Fournier, *The Manager's Path*, ch. 4 — first-time
  manager hiring chapter.
- Will Larson, *An Elegant Puzzle*, ch. 4 — engineering hiring
  systems.
- Amazon's publicly-available Bar Raiser primer — referenced as
  the canonical published bar-raiser model in `playbook.md` §8
  and `STEP_BY_STEP.md` pre-work.
- Project Include's hiring guides — referenced as the canonical
  source for inclusive hiring practice in §9.
- Public engineering ladders (Square, Patreon, CircleCI) —
  referenced in `README.md` §11 only as **counter-examples** of
  what to translate from, not what to copy.

### Practitioner reference policy

Per `.aicg/audit-report.json` source policy: "VeriSwarm sources
may be used only as practitioner implementation references, not
standards authorities." No VeriSwarm-specific claims are made in
this solution. Where a practice (e.g., the bar-raiser
qualification path, the 90-min calibration cadence, the
6-month post-hire look-back) is presented as a concrete number,
the number is taken verbatim from the project's own
`playbook.md` / `requirements.md` — not from external
practitioner sources.

## When This Design Would Fail

The solution above is itself a designed artifact. It would stop
working under any of these conditions, and a learner using it as
a reference should be alert to them:

1. **The team's actual context departs from the stated profile.**
   `requirements.md` §1 fixes the scenario at 8 engineers, 2 new
   senior hires, ~25% recruiter time, 6-level company ladder. A
   submission for a 200-engineer org, or a fully-remote
   distributed team, or a team without any recruiter, will
   need to adapt the recruiter cadence, interviewer load policy,
   and calibration cadence to fit. Copy the rationale; rebuild
   the numbers.
2. **Compliance jurisdiction differs.** Several W-requirements
   (no comp-history, accommodations stance, salary
   transparency) are framed against jurisdictions with
   structured-interview and anti-discrimination law. Local
   counsel review is required before deployment outside the
   default jurisdiction. `requirements.md` §12 calls out the
   constraint.
3. **The Project 02 capacity model is absent.** The role
   profiles' specificity grade depends on tracing to that model
   (`rubric.md` D1 L4). A learner submitting in isolation must
   substitute an equally specific capacity story — fabricated
   numbers do not satisfy the source policy.
4. **The reviewer reads only `00-summary.md`.** The summary is
   designed to be skimmable, but the rubric grades the
   underlying artifacts. A submission that puts all its
   substance in the summary and leaves the deliverables shallow
   will fail Dimension 3-6 even with a polished cover page.
5. **The candidate-experience kit is treated as optional.**
   `rubric.md` D6 caps at 3 without it, and the README §13
   makes the operational nature of CX explicit. Skipping it is
   not a length-saving move; it is a scoring concession.
