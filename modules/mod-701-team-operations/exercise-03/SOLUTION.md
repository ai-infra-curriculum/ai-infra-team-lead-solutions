# exercise-03 — Stakeholder Mapping (Solution)

> Reference solution for the learning exercise
> `lessons/mod-701-team-operations/exercises/exercise-03-stakeholder-mapping.md`
> in `ai-infra-team-lead-learning`. Attempt the exercise before reading this.

## 1. Solution overview

The exercise asks the learner to produce a **stakeholder map** for
their team: who they interact with, in which direction, with what
information need, at what cadence. The deliverable is a table or
diagram plus a short explanatory memo.

Stakeholder mapping is the discipline that keeps "surprises" out of
the team's work. New team leads consistently under-invest in
outward-facing cadences and are then surprised by dependency slips
or unmet customer needs.

The worked example continues the fictional **"InferEdge"** team
from exercise-02 and is labeled as local exercise context. The map
below is the artifact; the memo explains why the cadences are set
where they are.

## 2. Implementation — InferEdge stakeholder map

> *Fictional team used as worked-example context.*

### 2.1 Axes of the map

Stakeholders are classified on two axes:

- **Direction** — inward (direct reports), lateral (peer teams),
  upward (management chain), outward (customers, external
  partners, governance bodies).
- **Interaction mode** — *decision partner* (I need their signoff
  or vice versa), *dependency* (they block my work or I block
  theirs), *consumer* (they use my output), *informant*
  (background context only).

### 2.2 The map

| Stakeholder | Direction | Mode | What they need from us | What we need from them | Cadence | Channel |
|---|---|---|---|---|---|---|
| 5 InferEdge engineers | Inward | Reports | Clarity, feedback, growth | Status, flags, honesty | Weekly 1-1 (30 min) | 1-1 agenda doc |
| Model platform team lead | Lateral | Dependency (both ways) | New-model onboarding slots, eval signoff | Model artifact SLAs, eval reports | Biweekly sync (30 min) | Calendar + shared tracker |
| Data platform team lead | Lateral | Dependency | Request log sinks, schema stability | Data retention policy, schema change notice | Monthly sync (30 min) | Calendar + Slack channel |
| SRE / platform reliability | Lateral | Decision partner | SLO review, incident review | Infra capacity, incident support | Biweekly SLO review (30 min) | Calendar + runbook repo |
| ML security team | Lateral | Decision partner | Gateway-side security controls, abuse reports | ATLAS-aligned threat guidance, incident response | Monthly sync + on-call page path | Calendar + PagerDuty |
| Product team A (highest-traffic consumer) | Outward (internal) | Consumer | Latency, availability, model menu | Traffic forecasts, feature asks | Monthly check-in (30 min) | Calendar + status report |
| Product team B, C, D (long tail) | Outward (internal) | Consumer | Same as above | Same as above | Quarterly office hours | Office-hours calendar invite |
| Director (lead's manager) | Upward | Decision partner | Honest status, asks, risk flags | Priorities, air cover, headcount decisions | Weekly 1-1 (30 min) | 1-1 agenda doc |
| VP engineering | Upward | Informant / decision partner | Roadmap confidence, risks | Org priorities | Quarterly review (60 min) | Deck + written pre-read |
| Legal & Compliance (AI governance) | Outward | Decision partner | Deployment risk profile aligned to NIST AI RMF *Govern* and *Measure* | Policy interpretation, regulated-use signoff | Quarterly review; on-demand for new high-risk use cases | Written pre-read + review meeting |
| Finance / Capacity | Outward | Informant | Forecast GPU spend | Capacity trends, budget reality | Quarterly | Shared sheet |

### 2.3 Why these cadences

- **Weekly 1-1 with reports** — the single highest-leverage
  management ritual. Non-negotiable.
- **Biweekly with dependency teams** — frequent enough that
  surprises surface within a sprint, light enough that it does not
  become overhead.
- **Monthly with consumers** — the highest-traffic consumer gets
  the explicit slot; the long tail gets office hours, which keeps
  the lead's calendar from being a queue.
- **Quarterly with VP, legal, finance** — matches planning
  cycles; legal/compliance gets an on-demand channel for
  high-risk use cases because *waiting a quarter* to flag an AI
  governance issue would violate the Govern function's intent of
  continuous oversight.
- **Lateral decision partners (SRE, ML security) biweekly** —
  tight enough to catch reliability and security drift; the
  gateway sits directly in the blast radius of a MITRE
  ATLAS-class incident so the cadence is faster than a pure
  product consumer.

### 2.4 Anti-patterns the map is designed to prevent

- Dependency teams discovered mid-sprint ("we didn't know you
  needed that from us").
- Consumers who first surface via an escalation to the lead's
  manager.
- Legal / governance discovered after a launch, forcing a rollback.
- Direct reports who have not had a career conversation in two
  months because their 1-1 has become status triage.

## 3. Validation steps

Before submitting, the learner should verify:

1. **Coverage.** Every direction (inward, lateral, upward,
   outward) has at least one stakeholder.
2. **Named individuals or roles, not abstractions.** "The product
   org" is not a stakeholder; a named product lead is.
3. **Bidirectional information flow.** Every row has both *what
   they need from us* and *what we need from them*. One-way rows
   are a smell.
4. **Cadence is justified.** The learner can defend each cadence
   in one sentence (why not more frequent, why not less).
5. **AI-governance coverage.** If the team's work falls under the
   NIST AI RMF (any AI system with meaningful risk), there is at
   least one row for governance / compliance with an explicit
   on-demand path.
6. **Security partner coverage.** If the team runs production AI
   infra, there is an ML security row with an incident path
   aligned to MITRE ATLAS tactics and OWASP ML Top 10 categories.
7. **The map fits on a page** (plus the memo on a second page).
8. **No ritual contradicts the operating doc** from exercise-02.
   Cadences in the two documents match.

## 4. Rubric / review checklist

Score each row 0 / 1 / 2 (missing / partial / strong). Passing
map: ≥ 10/16 with no zeros on rows 1–4.

| # | Criterion | 0 | 1 | 2 |
|---|---|---|---|---|
| 1 | Direction coverage | Only one direction | 3 of 4 directions covered | All 4 directions covered, each with ≥ 1 row |
| 2 | Named stakeholders | Abstract groups only | Mostly named | Named individuals/roles for every row |
| 3 | Bidirectional needs | One-way | Mostly two-way | Every row has *need from us* and *need from them* |
| 4 | Cadence set & justified | Cadences missing or arbitrary | Cadences set | Cadences set and defended in the memo |
| 5 | AI governance coverage | Missing | Mentioned | Governance stakeholder with Govern-aligned cadence + on-demand path |
| 6 | Security partner coverage | Missing | Mentioned | ML security row with ATLAS/OWASP ML-aware incident path |
| 7 | Consistency with operating doc | Contradicts ex-02 | Mostly aligned | Fully aligned; shared rituals cross-referenced |
| 8 | Format discipline | Narrative without a map | Map or diagram present | Map + one-page memo, both readable at a glance |

## 5. Common mistakes

- **No regular touchpoints with adjacent teams.** Dependencies
  then surface as surprises inside sprint week.
- **No regular touchpoints with customers.** The team ships what
  it *thinks* is needed, not what is needed. Monthly check-ins
  with the highest-traffic consumer cost less than one rollback.
- **Treating "upward" as only the lead's own manager.** The
  director's manager also has information needs, usually at
  quarterly cadence. Skipping this layer looks political; it is
  actually operational.
- **No governance row for AI work.** For teams whose systems fall
  under the NIST AI RMF's scope, a quarterly-only cadence with
  legal/compliance is insufficient for new high-risk launches.
  Add an on-demand path.
- **Over-crowded calendar.** Every stakeholder set to weekly
  cadence destroys the lead's time. Cadence must be rationed.
- **Static map.** Stakeholder maps drift as the team's work
  changes. Review every quarter alongside the operating doc.
- **Map without a memo.** The table alone does not explain *why*
  the cadences are where they are; without the memo, the map
  cannot be defended to a skeptical manager or successor.

## 6. References

- NIST. *AI Risk Management Framework (AI RMF 1.0)*. NIST AI 100-1,
  January 2023 — in particular the *Govern* function on
  stakeholder engagement and oversight.
  <https://www.nist.gov/itl/ai-risk-management-framework>
- MITRE ATLAS (stakeholder-relevant tactics include initial
  access, model access, exfiltration). <https://atlas.mitre.org/>
- OWASP Machine Learning Security Top 10.
  <https://owasp.org/www-project-machine-learning-security-top-10/>
- Module overview: `modules/mod-701-team-operations/SOLUTION.md`
  (section "Stakeholder mapping").
- Companion exercises: exercise-02 (operating doc — cadences must
  match) and exercise-04 (roadmap — informed by what stakeholders
  told you).
