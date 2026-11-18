# exercise-01 — Team Operations Case Study (Solution)

> Reference solution for the learning exercise
> `lessons/mod-701-team-operations/exercises/exercise-01-case-study.md`
> in `ai-infra-team-lead-learning`. Attempt the exercise before reading this.

## 1. Solution overview

The exercise asks the learner to pick a **publicly documented team
operating pattern** (not a vendor sales pitch), reconstruct how it
works, and reason about where it would transfer to an AI infra team
and where it would break. The output is a short written case study.

A successful case study does four things:

1. Names the pattern concretely and cites where it is documented.
2. Describes the pattern as a *system* — rituals, cadence, roles,
   information flow — not just a slogan.
3. Identifies the structural conditions that made the pattern work
   in its original setting (team size, product cadence, customer
   type, failure cost).
4. Assesses transfer to an AI infra context: what maps, what
   breaks, what has to be added back in.

The underlying skill the exercise trains is **structural reading**:
seeing an operating pattern as a shape that depends on preconditions,
not as a recipe that works everywhere.

## 2. Implementation — worked answer

Below is a worked example using a pattern that is widely documented
and widely cargo-culted: **Basecamp's "Shape Up"** (Ryan Singer,
2019; book published by Basecamp and available free at
<https://basecamp.com/shapeup>). The same structure applies to any
pattern the learner picks.

### 2.1 Pattern as a system

| Element | Shape Up |
|---|---|
| Unit of work | A *pitch* (1–2 page shaped problem + rough solution). |
| Cadence | 6-week *cycles* followed by a 2-week *cool-down*. |
| Team shape | Small (1 designer + 1–2 programmers), self-directed. |
| Planning | *Betting table* at cycle boundary picks pitches; no backlog. |
| Scope control | *Hill chart* + *appetite* (fixed time, variable scope). |
| Escape hatch | A cycle can be killed, not extended. |

The pattern is explicit that there are **no sprints, no stand-ups,
and no backlog grooming**. The cost of those rituals, Basecamp
argues, is higher than their yield for a small product team with
long attention spans and a fixed appetite for each piece of work.

### 2.2 Why it works at Basecamp

- Small company (~60 people when the pattern was codified).
- A single product with low regulatory exposure and no hard SLAs.
- Mature engineers who can shape their own work.
- No external dependency teams blocking cycles.
- The CEO is a co-author of the methodology — leadership backs it.

### 2.3 Transfer to an AI infra team

Where Shape Up partially maps:

- **Appetite over estimates.** AI infra work (training runs, eval
  pipelines, inference latency projects) has high estimation noise;
  fixing time and flexing scope is a better default than the
  reverse.
- **Pitches as shaped work.** Writing a 1–2 page pitch before
  committing a cycle filters half-baked ideas, which is especially
  valuable when a bad bet costs weeks of GPU budget.
- **Cool-down.** An explicit cool-down maps well to the catch-up
  weeks that AI infra teams need after a big launch or model
  rollout.

Where Shape Up breaks and must be adapted:

- **On-call does not pause for cool-down.** An AI infra team with a
  production inference service still needs a rotation, incident
  response, and a non-dormant runbook — the pattern is silent on
  this. Add a persistent on-call ritual outside the cycle.
- **Cross-team dependencies.** AI infra teams rarely own the full
  stack. If platform, data, or model teams run on quarterly OKRs
  while your team runs on 6-week cycles, the phase mismatch
  produces missed handoffs. Either align the cadence or add an
  explicit interface meeting.
- **Governance and risk review.** For systems covered by the NIST
  AI Risk Management Framework (AI RMF 1.0, 2023), the *Govern* and
  *Measure* functions require *continuous* risk assessment, not
  only at cycle boundaries. A Shape-Up team must bolt on a
  standing risk-review ritual — typically monthly — or the
  Govern function silently decays.
- **Security incident cadence.** Threats catalogued in MITRE ATLAS
  (e.g., model evasion, data poisoning, model extraction) can
  surface mid-cycle. "Kill or finish" is the wrong framing for a
  live security incident; teams need a documented out-of-cycle
  incident path.

### 2.4 Conclusion of the case study

Shape Up transfers partially: its *shaping and appetite* primitives
are directly useful; its *ritual-minimalism* is not safe for AI
infra teams that carry a production service, dependencies, or
regulated AI risk. The right adoption is a hybrid — 6-week cycles
for net-new work, a standing on-call rotation, a standing risk
review tied to NIST AI RMF functions, and a cross-team interface
meeting whose cadence matches partner teams.

## 3. Validation steps

A learner (or grader) can self-check a case study by answering:

1. Can I point to the **primary source** that documents this
   pattern, rather than a blog summary of it? (If no, re-read the
   source.)
2. Could a new engineer on the team **reconstruct the rituals**
   from my write-up without re-reading the source?
3. Have I named at least **three structural preconditions** that
   held in the original setting?
4. For each precondition, have I checked whether it holds for an
   AI infra team?
5. Have I identified at least one **AI-infra-specific risk**
   (production inference service, GPU capacity, model security per
   MITRE ATLAS, regulated AI risk per NIST AI RMF) that the pattern
   does not address on its own?
6. Does my recommendation end with a **concrete adoption plan**
   (what to adopt, what to modify, what to add), not a verdict?

If every answer is yes and the case study fits on 2–3 pages, it is
ready for review.

## 4. Rubric / review checklist

Graders score each row 0 / 1 / 2 (missing / present / strong). A
passing case study scores ≥ 8/12 with no zeros on rows 1–4.

| # | Criterion | 0 | 1 | 2 |
|---|---|---|---|---|
| 1 | Source identified and cited | No source or only a secondhand blog | Primary source cited | Primary source cited plus at least one critical commentary |
| 2 | Pattern described as a system | Slogan-level summary | Rituals and cadence enumerated | Rituals, cadence, roles, and information flow all enumerated |
| 3 | Structural preconditions named | None | 1–2 preconditions | ≥ 3 preconditions, each tied to a ritual |
| 4 | Transfer analysis to AI infra | Hand-wave | At least one specific mismatch | Mismatches tied to on-call, dependencies, or AI risk frameworks |
| 5 | Concrete adoption plan | Verdict only | General recommendation | What to adopt / modify / add, each with a reason |
| 6 | Length and clarity | > 5 pages or incoherent | Readable, 3–5 pages | Tight, 2–3 pages, grader could hand to a new lead |

## 5. Common mistakes

- **Cargo-culting the most-blogged-about pattern.** "We'll do what
  Spotify does." Spotify itself moved on from the Squads/Tribes
  model years ago; the blog post lives on. Case studies that stop
  at the slogan miss the preconditions that made the pattern work.
- **Treating a pattern as a complete system.** Every operating
  pattern leaves things out. Shape Up has no on-call model. Scrum
  has no explicit career-growth loop. A good case study names what
  the pattern omits, not only what it includes.
- **Confusing success at the origin with transferability.** "It
  works at Basecamp" is not evidence it will work at a 200-engineer
  org with quarterly OKRs. Preconditions matter.
- **Verdicts instead of adoption plans.** "This would not work for
  us" is not actionable. Name what *would* adapt, under what
  conditions.
- **No reference to AI-specific risk.** For AI infra teams, an
  operating pattern that does not touch model risk, data integrity,
  or incident response is incomplete. Reference NIST AI RMF
  functions and/or MITRE ATLAS tactics where relevant.

## 6. References

- Ryan Singer. *Shape Up: Stop Running in Circles and Ship Work That
  Matters*. Basecamp, 2019. <https://basecamp.com/shapeup>
- NIST. *AI Risk Management Framework (AI RMF 1.0)*. NIST AI 100-1,
  January 2023. <https://www.nist.gov/itl/ai-risk-management-framework>
- MITRE ATLAS (Adversarial Threat Landscape for Artificial-Intelligence
  Systems). <https://atlas.mitre.org/>
- OWASP Machine Learning Security Top 10.
  <https://owasp.org/www-project-machine-learning-security-top-10/>
- Module overview: `modules/mod-701-team-operations/SOLUTION.md`
  (sections "Case study (exercise 01)" and "Common mistakes").
