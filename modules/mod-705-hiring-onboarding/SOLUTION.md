# SOLUTION — Hiring and Onboarding

> Read this *after* you have attempted the deliverables. The
> "solutions" are hiring and onboarding rubrics, not code. This
> document explains *why* hiring and onboarding deserve their own
> module — and where the biggest team-lead failure modes hide.

## What this module is really teaching

Hiring and onboarding compound over years. A team lead who hires
well builds momentum that lasts; one who hires poorly carries
that cost forever. The pipeline is also one of the most
expensive things the team-lead spends time on — typically
20-30% of a team-lead's calendar in a growth phase.

The truths the module teaches:

1. **The interview loop is the signal you'll act on.** Bad
   loops produce bad hires. Investing in the loop is
   investing in the team.
2. **Speed matters more than people think.** Strong candidates
   have multiple offers; a loop that drags 6 weeks loses
   them.
3. **Onboarding is a 90-day commitment, not a week.** New
   hires take 60-90 days to reach productivity. The team-lead
   underestimates this consistently.
4. **Hiring decisions are rarely close calls.** "I'm not sure
   about them" almost always means "no." Train yourself to
   trust the signal.
5. **Diversity is operational, not aspirational.** Inclusive
   hiring requires deliberate changes to sourcing, the loop,
   and the decision process.

## What the deliverables should actually look like

### Case study (exercise 01): a hiring or onboarding story

Pick a documented hiring practice (Stripe's "hiring bar"
blog posts, Lever / Greenhouse case studies, Google's "rule
of 4 interviews" data) and analyze:

- The **stage flow**: source → screen → loop → offer.
- The **decision rule**: how is the hire/no-hire decision
  made?
- The **signal collection**: what questions, what scoring,
  what calibration?
- The **outcome data**: did this approach produce
  high-performing hires? At what cost?

For onboarding stories, look for published "first week,"
"first month," "first quarter" plans. Companies publish these
because they're surprisingly hard to get right.

Common failure modes:
- **"Our process works because we're successful"**: confounds
  hiring quality with the broader company brand.
- **No retrospective data**: companies that don't measure
  "did this hire work out at 12 months?" are flying blind.

### The interview loop (exercise 02): the rubric

A well-designed loop covers these signals:

1. **Coding ability** — can they write working code with
   acceptable quality?
2. **System design** — can they reason about non-trivial
   systems at the level we need?
3. **Collaboration** — can they work in our team's mode?
4. **Domain skill** — specific to the role (ML systems,
   distributed systems, etc.).
5. **Communication** — can they explain their thinking?

Each signal should be assessed by **at least two interviewers**
to control for individual variance. Each interviewer should
take **structured notes** — what was asked, what the candidate
said, the interviewer's interpretation. Generic ratings ("4
out of 5") without context are unusable in the debrief.

The loop should be **calibrated**: when an interviewer rates
a candidate's coding "5", that should mean the same thing as
when another interviewer rates a different candidate "5."
Calibration happens through joint debriefs, written rubric,
and periodic recalibration sessions.

Common failure modes:
- **Pattern-matching to "people like me"**: produces a
  homogeneous team and misses strong unconventional
  candidates.
- **Asking trivia**: "what's the time complexity of X" tests
  recall, not engineering.
- **Vague debrief discussions**: "I liked them" is not data.

### The debrief (exercise 03)

A good debrief follows a strict shape:

1. **Each interviewer states their conclusion first**, before
   discussion. (Prevents anchoring.)
2. **Discussion follows** — focus on specific evidence, not
   feelings.
3. **The hiring manager decides**, but with explicit
   weighting of the loop's signal.
4. **No-hire is the default**. The default should be "we
   need positive evidence to hire" — not "we need negative
   evidence to reject."

Common failure modes:
- **Halo effect**: one strong interview overshadows three
  mediocre ones. The bar should be on every signal.
- **Compromise hiring**: "they're not great but we need
  someone." Almost always wrong; the cost of a bad hire is
  much higher than the cost of an empty seat.
- **No documented rationale**: 6 months later, when the
  hire underperforms, no one remembers what we thought we
  saw.

### Stakeholder mapping (exercise 04): the hiring partners

For hiring, the stakeholder map includes:

- **The recruiter**: your operational partner. They drive
  the pipeline.
- **The interviewers**: the team members who will run loops.
  They need training and time.
- **HR / People ops**: legal compliance, comp negotiation,
  offer mechanics.
- **The manager chain**: budget approval, level decisions.

Each gets a different relationship: the recruiter is daily;
the interviewers are weekly; HR is per-offer; the manager
chain is per-headcount-approval.

Common failure modes:
- **Treating the recruiter as a vendor**: produces transactional
  service, not partnership. Invest in the relationship.
- **No interviewer training**: junior interviewers default
  to vibes; the loop's quality degrades.

### The 90-day onboarding plan (exercise 05)

A new hire's first 90 days should have explicit milestones:

| Week | Milestone |
|---|---|
| Week 1 | Environment set up; first PR merged (even trivial) |
| Week 2-3 | First small project; pairing on real work |
| Week 4 | First 1-1 retrospective: how's it going? |
| Week 5-8 | Owning a small piece of work end-to-end |
| Week 9-12 | Integrated into team rotations; primary owner of one workstream |

Per new hire, the team-lead assigns:
- A **buddy** (peer) for daily questions.
- A **mentor** (senior, may or may not be the buddy).
- A **first project** that's real but bounded and recoverable.
- A **regular check-in cadence** above and beyond normal 1-1s.

Common failure modes:
- **No first project**: the new hire flounders trying to
  pick something up cold.
- **First project too large**: the hire is set up to fail.
- **No buddy**: the hire doesn't know who to ask the small
  questions, and waits to surface them in 1-1s where they
  feel weightier.
- **No check-in retros**: the hire is struggling but doesn't
  surface it.

## Trade-offs we deliberately accepted

### Slow hiring is wrong; rushed hiring is worse

The framework biases toward speed *within* the loop (quick
debriefs, fast offer turnaround) and against rushing the
bar (no compromise hires). Both can be true.

### Senior-skewed assumptions

The exercises bias toward hiring at the senior+ level, which
is the common case for AI infra teams. Junior hiring has
different dynamics (more emphasis on raw ability, less on
production experience).

### English-speaking corporate norms

Direct interview feedback, written debriefs, and "no-hire by
default" are more accepted in some cultures than others.
Adapt the form; the structural principles (multiple signals,
calibrated debrief, documented rationale) are universal.

## Common mistakes graders see

1. **Hiring for "culture fit"**: usually a euphemism for
   "people like us." Replace with specific behaviors
   (collaboration style, feedback handling) that are
   testable.
2. **Asking the same question across the loop**: redundant
   signal. The loop should have minimal overlap between
   interviews.
3. **No structured note-taking**: makes calibration
   impossible.
4. **Compromise hires under headcount pressure**: the
   short-term win is a long-term loss. Hold the bar.
5. **Onboarding plans that aren't followed**: written but not
   referenced. The plan needs ownership.
6. **No 90-day check-in**: the new hire's first quarter is
   the highest-value time for honest feedback; missing the
   check-in misses the window.
7. **Underweighting the buddy / mentor selection**: a
   strong buddy makes onboarding work; a busy or
   uninterested buddy makes the new hire feel adrift.

## When to go beyond this module

- Conduct a **post-hire retro** at the 6-month and 12-month
  mark for each hire: did the loop's signal predict their
  performance? Where was it right or wrong?
- Run a **bar-raiser calibration session** with peer team
  leads: read the same anonymized debrief notes, see if you'd
  reach the same decision.
- Cross-reference the **diversity / inclusion literature**
  — specifically, the work on how interview structures
  affect outcomes for under-represented candidates.

## Related curriculum touchpoints

- `team-lead/mod-702-people-management` — the relationship
  that begins on day 91 once onboarding ends.
- `team-lead/mod-701-team-operations` — the operational
  rituals the new hire enters.
- `principal-engineer/mod-502-mentorship-leadership` — the
  long-term development that follows on from successful
  onboarding.
- `senior-architect/mod-402-executive-leadership` — the
  hiring-at-scale view from higher altitudes.
