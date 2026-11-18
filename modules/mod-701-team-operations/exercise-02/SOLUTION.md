# exercise-02 — Team Operating Strategy Memo (Solution)

> Reference solution for the learning exercise
> `lessons/mod-701-team-operations/exercises/exercise-02-strategy-memo.md`
> in `ai-infra-team-lead-learning`. Attempt the exercise before reading this.

## 1. Solution overview

The exercise asks the learner to write the **one-page team operating
doc** that a new hire should read on day 1. The module-level
discussion (see `modules/mod-701-team-operations/SOLUTION.md` §
"The team operating doc") lists the eight required sections; this
file provides the worked example, validation, and grading rubric.

A strategy memo is not a vision statement. It is the artifact that
answers, for a new engineer: *what is this team's job, how does it
work, who decides what, and where do I look when something goes
wrong?* Done well, it compresses three months of tribal knowledge
into a single page.

The worked example below is for a fictional **"InferEdge" team**:
a 6-person AI infra team owning a low-latency inference gateway for
internal product teams at a mid-size company. It is local exercise
context (not a real team) and is labeled as such.

## 2. Implementation — "InferEdge" team operating doc

> *Fictional team used as worked-example context.*

### Mission

InferEdge owns the internal inference gateway. We make it fast,
observable, and safe to serve any approved model to any internal
caller.

### Scope

- **In scope:** request routing, batching, autoscaling, token &
  quota enforcement, request logging, model-rollout tooling,
  gateway-side security controls.
- **Out of scope:** model training, model evaluation, feature
  stores, downstream product UX, data labeling.
- **Boundary cases** (resolved in 1-on-1 with the model platform
  team): new-model onboarding checklist, offline eval signoff.

### Operating rhythm

| Cadence | Ritual | Owner |
|---|---|---|
| Daily | Async standup in `#inferedge-standup` by 10:00 local | Everyone |
| Weekly (Mon 10:00) | Sprint planning, 60 min | Lead |
| Weekly (Fri 15:30) | Retro + on-call handoff, 45 min | Rotating facilitator |
| Weekly | 1-1 lead ↔ each engineer, 30 min | Lead |
| Biweekly | Risk & reliability review (SLOs, incidents, AI-RMF Measure) | Lead + SRE partner |
| Monthly | Roadmap check-in with stakeholders (see stakeholder map) | Lead |
| Quarterly | Planning, retro-of-retros, on-call rotation refresh | Lead |

### Roles (responsibilities, not titles)

- **Team lead** — roadmap, prioritization, cross-team coordination,
  performance and growth.
- **Tech lead** — architecture ownership, design-review gate, final
  technical call when consensus stalls.
- **On-call engineer (weekly rotation)** — pages, incident
  commander during incidents, writes postmortems.
- **Release owner (weekly rotation, offset from on-call)** —
  deploys, rollback authority, release notes.
- **Everyone** — writes decisions down; updates runbooks after
  incidents; reviews PRs within one business day.

### Communication channels

| Channel | Purpose | Expected response |
|---|---|---|
| `#inferedge` (Slack) | General team channel | Business hours |
| `#inferedge-oncall` | Pages, incidents | Minutes |
| `#inferedge-standup` | Async daily standup | By 10:00 local |
| Email | External, auditable requests | 1 business day |
| PagerDuty | After-hours paging only | ~5 min ack |
| GitHub `inferedge/` repos | Code, PRs, issues | PR review within 1 business day |

### On-call

- Weekly rotation, Mon 10:00 → Mon 10:00, 6 people → 6-week cycle.
- Primary + secondary; secondary covers when primary is in a
  meeting or stuck.
- Explicit escalation path: primary → secondary → tech lead →
  team lead → director on-call.
- Handoff happens live in Friday retro; written handoff note
  posted in `#inferedge-oncall` by end of Friday.
- **AI-specific incidents** (suspected model abuse, prompt
  injection, evasion, data exfiltration via model output — see
  MITRE ATLAS, OWASP ML Top 10) also page the ML security
  partner team per the shared runbook.

### Decision-making framework

We use a lightweight escalation ladder (loosely tracking the
*Govern* function of NIST AI RMF for AI-affecting decisions):

1. **Reversible, local** — the engineer decides; PR review is
   enough.
2. **Reversible, cross-cutting** — tech lead decides; recorded as
   a one-paragraph ADR in `decisions/`.
3. **Hard-to-reverse (cost, security, SLO, model-safety impact)** —
   team lead + tech lead decide after a design review; recorded as
   a full ADR; AI-risk items get a Measure-function entry.
4. **Cross-team or org-visible** — team lead escalates to
   director; outcome recorded as an ADR and shared with affected
   teams.

**Default:** when uncertain which tier applies, write a one-paragraph
ADR anyway. Over-documenting a reversible decision is cheap;
under-documenting a hard-to-reverse one is not.

### Documentation expectations

- **Decisions** → `decisions/YYYY-MM-DD-<slug>.md` in the main
  repo. One per decision tier 2 or above.
- **Runbooks** → `runbooks/` in the main repo. Any new alert
  needs a runbook before it ships.
- **Postmortems** → `postmortems/YYYY-MM-DD-<slug>.md`. Required
  within 5 business days of any SEV-1 or SEV-2 incident.
- **This operating doc** → reviewed every quarter; drift noted in
  the quarterly retro.

> End of worked operating doc. Target length: one page when
> rendered without the headings (≈ 450 words of body).

## 3. Validation steps

Before submitting, the learner should verify:

1. **Length.** Prints to roughly one page. If it does not, cut.
2. **New-hire test.** Hand the doc to someone who is not on the
   team. They should be able to answer: *What does this team do?
   What rituals run this week? Who owns what? Where is on-call?*
3. **Cadence-work match.** Each ritual has a reason tied to the
   team's work. Standups make sense for a 6-person team with
   dense dependencies; they do not for a 2-person research pair.
4. **Decision path exists for every type of decision.** Trace one
   decision in each tier through the ladder.
5. **AI-specific coverage.** On-call and decision-making both
   address AI-specific failure modes (model abuse, data
   poisoning, model extraction). Reference frameworks (NIST AI RMF
   functions, MITRE ATLAS tactics, OWASP ML Top 10) at least
   once where it is load-bearing, not decoratively.
6. **Reality check.** Nothing in the doc is aspirational-only.
   Each ritual either happens today or is being started with a
   named start date.

## 4. Rubric / review checklist

Score each row 0 / 1 / 2 (missing / partial / strong). Passing
memo: ≥ 10/16 with no zeros on rows 1, 2, 4.

| # | Criterion | 0 | 1 | 2 |
|---|---|---|---|---|
| 1 | Mission & scope | Missing or vague | One-sentence mission, scope stated | Mission + scope + explicit *out of scope* + boundary cases |
| 2 | Operating rhythm | No cadence given | Rituals listed | Rituals + cadence + owner, matched to the work |
| 3 | Roles | Titles only | Named responsibilities | Responsibilities including tech lead, on-call, release owner, "everyone" |
| 4 | Communication channels | None | Channels listed | Channels + purpose + expected response time |
| 5 | On-call | Rotation unspecified | Rotation + escalation | Rotation + escalation + handoff + AI-specific incident path |
| 6 | Decision-making | Not addressed | Lightweight ladder | Ladder with tiers tied to reversibility and AI-risk framing |
| 7 | Documentation expectations | Not addressed | Where things live | Where + when (triggering events, SLAs for postmortems, review cadence) |
| 8 | One-page discipline | > 2 pages | ~1.5 pages | One page, readable, no filler |

## 5. Common mistakes

- **No doc at all.** The team's operations are tribal knowledge.
  New hires take three months to become productive and ask the
  same questions.
- **Five-page doc with everything in it.** Nobody reads it, so it
  stops being updated, so it drifts.
- **Aspirational doc.** It describes the team as the lead wishes
  it worked, not as it works. Within a quarter it is a lie.
- **No cadence match.** Standups, retros, planning, 1-1s all
  present because they should be, with no connection to the work.
- **No decision ladder.** Every decision becomes a meeting; or
  worse, every decision becomes the lead's decision.
- **Silent on AI-specific risk.** For AI infra teams, an operating
  doc that does not touch model abuse, data integrity, or on-call
  handoff for AI incidents is missing the thing that makes it an
  AI infra team doc. Reference NIST AI RMF functions and MITRE
  ATLAS tactics where load-bearing.
- **No review cadence for the doc itself.** Written once and
  never updated; drift goes unnoticed.

## 6. References

- NIST. *AI Risk Management Framework (AI RMF 1.0)*. NIST AI 100-1,
  January 2023. <https://www.nist.gov/itl/ai-risk-management-framework>
- NIST. *AI RMF Playbook* (Govern, Map, Measure, Manage functions).
  <https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook>
- MITRE ATLAS. <https://atlas.mitre.org/>
- OWASP Machine Learning Security Top 10.
  <https://owasp.org/www-project-machine-learning-security-top-10/>
- Module overview: `modules/mod-701-team-operations/SOLUTION.md`
  (sections "The team operating doc" and "Common mistakes").
- Related exercises in this module: exercise-03 (stakeholder
  cadence feeds into *Operating rhythm*), exercise-04 (roadmap is
  the artifact the Monday planning ritual ships against).
