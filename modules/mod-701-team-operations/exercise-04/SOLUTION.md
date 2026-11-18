# exercise-04 — Quarterly Roadmap (Solution)

> Reference solution for the learning exercise
> `lessons/mod-701-team-operations/exercises/exercise-04-roadmap.md`
> in `ai-infra-team-lead-learning`. Attempt the exercise before reading this.

## 1. Solution overview

The exercise asks the learner to produce a **team-lead-owned
quarterly roadmap** for an AI infra team. The module overview
(`modules/mod-701-team-operations/SOLUTION.md` § "Roadmap") lists
the five required elements: goals as outcomes, confidence
assessments, work breakdown, risks and dependencies, stretch
goals.

A good roadmap is a *commitment* document and a *forecast*
document at the same time. Goals the team commits to appear with
their confidence level and the tradeoffs that make them
committable; forecast-only items appear as stretches or as
explicit risks. The lead's job is to make each column honest.

The worked example continues the fictional **"InferEdge"** team
(carried from exercises 02 and 03) and is labeled as local
exercise context.

## 2. Implementation — InferEdge Q3 roadmap

> *Fictional team used as worked-example context.*

**Team:** InferEdge (6 engineers + lead)
**Quarter:** Q3 (13 weeks)
**Capacity:** ≈ 70 engineer-weeks after on-call, vacation (2 wk),
and 20 % slack for maintenance and incident response.

### 2.1 Goals (outcomes, not activities)

| # | Goal | Confidence | Owner | Est. effort |
|---|---|---|---|---|
| G1 | p99 inference latency ≤ 180 ms at current QPS across the 3 highest-traffic models | High | Tech lead + E2 | 15 eng-wk |
| G2 | Gateway supports 2 new internal product teams onboarding end-to-end, with an onboarding guide signed off by model platform | High | Lead + E3 | 10 eng-wk |
| G3 | Prompt-injection and model-abuse detection v1 shipped at gateway edge, aligned to OWASP ML Top 10 (ML04/ML06) and MITRE ATLAS (AML.T0043, AML.T0051) | Medium | E4 + ML security partner | 14 eng-wk |
| G4 | Observability: request logging + per-model error budget reporting, aligned to NIST AI RMF *Measure* function | High | E5 | 9 eng-wk |
| G5 | On-call MTTA and MTTR cut by ≥ 30 % via runbook refresh and alert tuning | Medium | On-call rotation | 6 eng-wk |

Total committed effort: 54 eng-wk of 70 → 23 % headroom.

Goals are stated as **outcomes** (what will be true at the end of
the quarter) rather than activities (what we will work on).

### 2.2 Confidence rationale

- **G1 (High):** continuation of Q2 work; bottleneck is
  identified; team has shipped similar before.
- **G2 (High):** onboarding guide is partially drafted; both
  product teams have stable traffic forecasts.
- **G3 (Medium):** detection scope is well-defined, but
  false-positive tolerance for internal callers is unknown; may
  require a second iteration.
- **G4 (High):** pattern is standard; no unknown unknowns.
- **G5 (Medium):** depends on paging data from previous quarter
  being clean enough to drive tuning decisions; also depends on
  on-call engineers finding time during their shift to update
  runbooks.

### 2.3 Work breakdown (per engineer)

| Engineer | Primary | Secondary | Buffer |
|---|---|---|---|
| Tech lead | G1 | G3 architecture review | On-call, design reviews |
| E2 | G1 | G5 | On-call |
| E3 | G2 | G4 | On-call |
| E4 | G3 | G4 | On-call |
| E5 | G4 | G5 | On-call |
| E6 (new hire, start wk 3) | Ramp-up + G2 | — | Onboarding buddy pairing |
| Lead | Cross-team coordination for G2 and G3; governance review for G3; 1-1s; retros; roadmap | — | — |

### 2.4 Risks and dependencies

| Risk / dependency | Impact if realized | Mitigation | Owner |
|---|---|---|---|
| Model platform team's eval signoff for G3 slips | G3 moves to Q4 | Biweekly sync already in place; pre-commit eval harness drafted | Lead |
| GPU capacity does not land for the 2 new onboardings (G2) | G2 scope cuts to 1 team | Forecast shared with capacity team monthly; escalation path to director | Lead |
| New-hire ramp is slower than planned | G2 slips by 1–2 wk | Pair with E3; 30/60/90 plan; explicit stretch, not commitment | Lead |
| New AI governance guidance from legal changes signoff process for G3 | G3 shape changes mid-quarter | On-demand channel to legal; NIST AI RMF *Govern* review scheduled wk 2 | Lead |
| On-call volume spikes (incident-heavy quarter) | Up to 15 % of capacity shifts to incidents | 23 % headroom; if exceeded, G5 absorbed first | Tech lead |

### 2.5 Stretch goals (only if main goals land early)

- **S1:** Multi-region failover PoC.
- **S2:** Shadow-mode canary tooling for new models.
- **S3:** Second iteration of G3 lowering false-positive rate.

Stretches are not communicated to leadership as commitments; they
are communicated to the team so that a lead-early scenario does
not result in under-utilized capacity.

### 2.6 Review cadence

- Monthly roadmap check-in with stakeholders (per exercise-03
  stakeholder map).
- Confidence re-scored at the month boundary. A confidence drop
  from High → Medium triggers a conversation with the lead's
  manager.
- Full re-plan at quarter boundary.

## 3. Validation steps

Before submitting, the learner should verify:

1. **Outcomes, not activities.** Every goal is stated so the team
   could tell, at quarter-end, whether it is done. If any goal
   reads as "work on X," rewrite.
2. **Explicit confidence.** Every goal has a High / Medium / Low
   confidence rating with a one-sentence rationale.
3. **Capacity math.** Total committed effort ≤ available capacity
   after on-call, vacation, and slack. If the math doesn't close,
   cut a goal or drop its confidence.
4. **Named owners.** Every goal has a named engineer (not a team
   name).
5. **Risks are real and mitigated.** At least three risks; each
   has an impact statement, a mitigation, and an owner.
6. **AI-infra-specific coverage.** The roadmap references the
   NIST AI RMF functions that apply (at least *Measure* for
   observability goals, *Govern* for any launch with regulated
   use). Security goals, if any, cite OWASP ML Top 10 or MITRE
   ATLAS categories by ID so the review audience can verify scope.
7. **Stretch section exists and is labeled.** Stretch goals are
   explicitly *not* commitments.
8. **Fits on 2 pages** as rendered.

## 4. Rubric / review checklist

Score each row 0 / 1 / 2 (missing / partial / strong). Passing
roadmap: ≥ 12/18 with no zeros on rows 1–4.

| # | Criterion | 0 | 1 | 2 |
|---|---|---|---|---|
| 1 | Goals as outcomes | Mostly activities | Mix | All outcomes, measurable |
| 2 | Confidence set per goal | Missing | Rating only | Rating + one-sentence rationale |
| 3 | Capacity math closes | Not shown or over-commits | Shown, tight | Shown, with named headroom |
| 4 | Named owners | Team names only | Mostly named | Every goal has a named owner |
| 5 | Risks and dependencies | ≤ 1 row | 2 rows | ≥ 3 rows, each with impact + mitigation + owner |
| 6 | AI governance alignment | None | Mentioned | Specific NIST AI RMF function tags on relevant goals |
| 7 | Security coverage (if applicable) | Missing | Mentioned | OWASP ML Top 10 / MITRE ATLAS IDs cited where in scope |
| 8 | Stretch goals labeled | Missing or mixed with commitments | Present | Present, clearly separated, with "not a commitment" note |
| 9 | Review cadence stated | Missing | Mentioned | Review cadence + re-plan trigger defined |

## 5. Common mistakes

- **Goals stated as activities.** "Build feature X" doesn't tell
  you if you're done. Rewrite as "X ships, serving ≥ Y requests
  per day, with Z latency."
- **No confidence assessment.** All goals look like commitments.
  Low-confidence items that slip then look like failures when they
  were always experiments.
- **No stretch goals.** A team that lands all main goals at 60 %
  of the quarter has under-committed; by the time this is
  obvious, half the quarter is gone.
- **Capacity math doesn't close.** 100 % of nominal engineer-weeks
  committed, zero room for on-call, interrupts, or incident
  response. Predictable slip.
- **Unnamed risk owners.** Risks without owners are not mitigated;
  they are listed.
- **AI governance invisible.** Goals affecting regulated or
  high-risk AI use cases ship without a *Govern*-aligned review.
  Discovery happens at launch time, which is the worst time.
- **Roadmap never revisited.** A quarterly plan that doesn't move
  for 12 weeks has drifted from reality; it just hasn't been
  updated.

## 6. References

- NIST. *AI Risk Management Framework (AI RMF 1.0)*. NIST AI 100-1,
  January 2023 — functions *Govern* and *Measure* are directly
  relevant to roadmap governance and observability goals.
  <https://www.nist.gov/itl/ai-risk-management-framework>
- NIST. *AI RMF Playbook*.
  <https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook>
- MITRE ATLAS. <https://atlas.mitre.org/>
- OWASP Machine Learning Security Top 10.
  <https://owasp.org/www-project-machine-learning-security-top-10/>
- Module overview: `modules/mod-701-team-operations/SOLUTION.md`
  (sections "Roadmap" and "Common mistakes graders see").
- Companion exercises: exercise-02 (operating doc defines who owns
  the roadmap ritual), exercise-03 (stakeholder map drives the
  review cadence in §2.6), exercise-05 (presentation reports
  against this roadmap).
