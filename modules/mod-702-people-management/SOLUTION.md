# SOLUTION — People Management

> Read this *after* you have attempted the deliverables. The
> "solutions" are managerial rubrics, not code. This document
> explains *why* people management is what differentiates a
> tech-lead from a manager-of-engineers, and what the right
> defaults look like.

## What this module is really teaching

People management at the first-line level is a job most
engineers transition into badly. The reasons are predictable:

- Engineers are trained to optimize *systems*; people aren't
  systems.
- Engineers are trained for *precise* communication; people
  management requires ambiguity tolerance.
- Engineers are rewarded for *output*; managers are rewarded
  for *outcomes via others*, which is a longer feedback loop.
- Engineers default to *fixing the problem themselves*; managers
  who do this fail to grow their reports.

The module exists to make these transitions less painful. The
material isn't novel — there are thousands of books on
management — but the AI infra context has specifics worth
calling out.

The truths the module teaches:

1. **1-1s are the most important meeting.** If you do them
   well, most other things work; if you skip them, nothing
   else compensates.
2. **Feedback withheld is feedback denied.** The cost of
   silent dissatisfaction compounds.
3. **Career conversations are separate from performance
   conversations.** Conflating them produces neither.
4. **Performance management requires documentation.** This
   sounds bureaucratic until you're trying to support a
   performance case in front of HR.
5. **Hiring and onboarding are people management.** They're
   covered in mod-705 specifically because they're large
   enough to deserve their own module.

## What the deliverables should actually look like

### Case study (exercise 01): a management story

Pick a documented or personal management story. Good examples:

- An engineer who was struggling and turned around (what did
  the manager do?).
- A high-performer who got promoted and then struggled at the
  next level (what was missing in their growth plan?).
- A team that lost trust in its manager (what was the
  sequence of incidents?).
- A team that thrived under unusual constraints (what did the
  manager do differently?).

Common failure modes:
- **Treating outcomes as predictable**: most management
  outcomes are noisy. The same intervention works on one
  engineer and fails with another. Process matters more than
  any single move.
- **Hero narrative**: "the manager saw their potential and
  unlocked it." Sometimes; often the work was unglamorous.

### The 1-1 (exercise 02): the foundational ritual

A good 1-1 has shape:

1. **The report's agenda first.** They drive. If they don't
   have anything, that's a flag worth probing.
2. **Status updates last, if at all.** Status belongs in
   async tools. 1-1 time is for what status updates can't
   capture.
3. **Specific feedback when it's needed.** Withhold neither
   praise nor concern.
4. **Career conversation every 4-6 weeks.** Not every 1-1, but
   regularly. What growth direction? What's the next
   stretch?
5. **The manager's questions are mostly "tell me more."**
   You're trying to learn what's actually happening on the
   team, not give a status report yourself.

Cadence: weekly for direct reports, 30 minutes. Bi-weekly is
the floor; monthly is too slow.

Common failure modes:
- **Cancelling 1-1s when busy**: signals to the report that
  they're low priority. Reschedule, don't cancel.
- **Manager-driven agenda**: turns the 1-1 into a status
  update. Wrong shape.
- **Feedback only at perf review time**: a year-late
  feedback delivery is useless. Feedback at the next 1-1 is
  useful.

### Feedback frameworks (exercise 03)

Many feedback frameworks exist (SBI, COIN, FAST). Pick one,
internalize it, use it. The framework that works for you is
less important than *using* one consistently.

The structural elements common to all good feedback:

1. **Specific moment** — "in Tuesday's design review" not "in
   general."
2. **Observable behavior** — what they said or did, not your
   interpretation of why.
3. **Impact** — what happened as a result. (For positive
   feedback, the good outcome; for corrective, the cost.)
4. **The ask** — what would you like them to do differently?
   Or, for positive feedback, what to keep doing.

Common failure modes:
- **Sandwich feedback**: positive-negative-positive often
  obscures the negative and undermines both positives. Be
  direct.
- **Generic praise**: "great job" without specifics is empty
  calories.
- **Feedback that wasn't requested**: in the middle of a
  sprint, drive-by feedback feels like an attack. Time it.

### Performance management (exercise 04): the harder conversations

When an engineer's performance is not meeting expectations,
the manager's job is to:

1. **Name the gap clearly**, with examples.
2. **Make the bar concrete** — what does meeting expectations
   look like?
3. **Co-create a plan** with milestones and check-ins.
4. **Follow up consistently** — weekly or biweekly check-ins.
5. **Document everything** — privately, but consistently.

If performance does not improve, the next step (PIP, role
change, separation) is in partnership with HR. The
team-lead's job is to have surfaced the issue early enough
that the report has a real chance to recover.

Common failure modes:
- **Avoiding the conversation**: hope is not a management
  strategy. The earlier the conversation, the better the
  outcome.
- **Vague gap description**: "you need to step up" tells the
  report nothing. Be specific about what's missing.
- **No documentation**: when HR asks for evidence, you have
  none.
- **No co-creation**: a plan dictated to the report has no
  buy-in.

### The career conversation (exercise 05)

Career conversations are different from performance
conversations:

- **Performance**: are you meeting the bar for your current
  level?
- **Career**: where do you want to go, and what does the path
  look like?

A good career conversation:

1. **Asks**, doesn't tell. "What's energizing you right now?
   What direction interests you?"
2. **Explores honestly** — including paths that take the
   report away from your team.
3. **Maps the next 12-24 months** — what would the next role
   require? What experience or skill gaps need filling?
4. **Captures next concrete steps** — what stretch project
   could move them in that direction?

Common failure modes:
- **Selling the report on staying**: a manager who only
  pitches paths within their team comes across as
  self-interested.
- **Promotion-only framing**: "next level" is one direction;
  lateral moves, scope changes, and deeper specialization are
  others.
- **No follow-through**: the career conversation produces
  goals; the next 1-1 should reference them.

## Trade-offs we deliberately accepted

### Default-on documentation

The framework biases toward writing things down. Some teams
operate effectively with less documentation; most don't. The
default should be more documented than feels natural.

### Western corporate norms

Direct feedback culture is more accepted in the US/UK than
in some other regions. Adapt the form; the content
(specific, actionable, timely) is universal.

### Manager-of-engineers, not manager-of-managers

The exercises target first-line management. Managing managers
is a different skill (the focus shifts to systems and
incentives over direct intervention). The skip-level dynamics
are addressed lightly here and more deeply in the
senior-architect / VP tracks.

## Common mistakes graders see

1. **No 1-1 notes**: 1-1 conversations evaporate without
   notes. Take notes — yours, not theirs.
2. **Feedback only when something is wrong**: positive
   feedback is feedback. Without it, reports interpret
   silence as displeasure.
3. **Promoting people for being good at the previous level**:
   the next-level signal is "what they've shown at the new
   level," not "great at the current level."
4. **Underweighting team health**: a manager who lets a
   high-performer behave badly trades short-term output for
   medium-term team breakdown.
5. **Career conversations only at perf review time**: too
   late.
6. **Skip-level meetings only for problems**: if your manager
   only meets your reports when something's wrong, that's
   the signal the reports will read.

## When to go beyond this module

- Take a real management situation you're navigating and
  apply the rubrics. Where do you have a habit gap?
- Read **"High Output Management"** (Grove), **"The Manager's
  Path"** (Fournier), **"Resilient Management"** (Hogan).
  Different lenses on the same job.
- Find a **management mentor** at your company or outside.
  The first 12 months as a manager are unusually high-value
  for outside perspective.

## Related curriculum touchpoints

- `team-lead/mod-701-team-operations` — the rituals and
  systems that 1-1s and feedback live inside.
- `team-lead/mod-705-hiring-onboarding` — the front end of
  the people-management cycle.
- `principal-engineer/mod-502-mentorship-leadership` — the
  staff-IC view of the same engineers.
- `senior-architect/mod-402-executive-leadership` — the
  higher-altitude view of people leadership.
