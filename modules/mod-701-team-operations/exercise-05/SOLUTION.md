# exercise-05 — Team Review Presentation (Solution)

> Reference solution for the learning exercise
> `lessons/mod-701-team-operations/exercises/exercise-05-presentation.md`
> in `ai-infra-team-lead-learning`. Attempt the exercise before reading this.

## 1. Solution overview

The exercise asks the learner to produce a **monthly or quarterly
team-review presentation** to leadership. The module overview
(`modules/mod-701-team-operations/SOLUTION.md` § "Presentation")
lists the four required sections: what we shipped, what we
learned, what's at risk, the ask.

A team review is *not* a status dump. It is a short, structured
account designed to let leadership do three things: (a) believe the
team is operating well, (b) see the next risks early, and (c) be
asked something they can actually act on. The lead's job is to
make the ask the loudest line in the deck.

The worked example continues the fictional **"InferEdge"** team
(from exercises 02 – 04) and is labeled as local exercise context.
It is presented as a *written pre-read* for the review; a slide
deck would carry the same content in roughly 8 slides.

## 2. Implementation — InferEdge Q3 month-1 review (pre-read)

> *Fictional team used as worked-example context.*
> **Audience:** director, with VP optionally sitting in.
> **Duration:** 20 minutes meeting + written pre-read circulated 24 h
> ahead.

### 2.1 What we shipped (month 1 of Q3)

| Goal (from Q3 roadmap) | Status | Concrete outcome | Metric |
|---|---|---|---|
| G1 — p99 latency ≤ 180 ms | On track | Two of three top models at ≤ 180 ms p99; third at 195 ms, fix in flight | p99 ms per model, graphed |
| G2 — onboard 2 product teams | On track | Team A fully onboarded; Team B started | Daily request volume per tenant |
| G3 — prompt-injection & abuse v1 | Early | Shadow-mode detector live on 5 % of gateway traffic; aligned to OWASP ML04/ML06 | Detection precision, recall on holdout set |
| G4 — observability | Ahead | Per-model error-budget report automated; feeds into NIST AI RMF *Measure* review | Weekly report delivered |
| G5 — on-call MTTA/MTTR | Early | Alert tuning cut pager volume 22 %; MTTR not yet remeasured | Pages / week, MTTA, MTTR |

### 2.2 What we learned

- **Observability (G4) was cheaper than estimated.** The pattern
  from the SRE team's template cut the build by about 40 %.
  Freed capacity reinvested in G3 shadow-mode.
- **Onboarding (G2) is dominated by the eval signoff step, not
  gateway integration.** Our onboarding guide needs to reorder to
  put eval scheduling first. Guide v2 shipping next week.
- **G3 false-positive rate against internal tools is higher than
  expected** (shadow-mode shows ~3.5 % FP on benign internal
  traffic). This is the headline risk below; mitigation below.
- **The 23 % capacity headroom in the plan was exactly right this
  month** — one SEV-2 incident and one unplanned support request
  from a product team consumed most of it.

### 2.3 What's at risk

| Risk | Origin | Likelihood | Impact | Mitigation in flight |
|---|---|---|---|---|
| G3 false-positive rate blocks promoting detector out of shadow | Observed in week 4 data | Medium → High if unresolved by week 7 | G3 slips to Q4, or ships with weaker scope | Add per-tenant policy tier; schedule review with ML security partner; align scope to MITRE ATLAS AML.T0043/T0051 |
| New AI governance guidance from legal (expected week 6) could change G3 signoff | External | Medium | 1–2 week slip on G3 launch | On-demand channel open; pre-read drafted for legal (NIST AI RMF *Govern* function) |
| GPU capacity for Team B expansion arrives late | Shared capacity pool | Low → Medium | G2 completes at 80 % scope | Monthly forecast shared with capacity team; fallback: finish Team B on current pool at lower QPS cap |

### 2.4 The ask

1. **Decision needed by week 6:** OK to ship G3 detector with
   per-tenant policy tiers (default conservative, opt-in strict),
   even though this adds one config dimension to the gateway?
   Preferred by the team; wanted to flag the complexity upward
   before commitment.
2. **Air cover for the eval-signoff reorder (G2).** Model
   platform team is cooperative but under their own quarterly
   pressure; a director-level ping that we have agreed the new
   onboarding guide shape would unstick the handoff.
3. **Not asked:** headcount, priority change, scope cut.

### 2.5 Appendix (linked, not spoken)

- Full Q3 roadmap with confidence scores (exercise-04 artifact).
- Current stakeholder map (exercise-03 artifact).
- Last two postmortems.
- G3 shadow-mode metrics dashboard.

## 3. Validation steps

Before presenting, the learner should verify:

1. **Shipped section has metrics, not adjectives.** Every row has
   a number or a dashboard link. "Significant progress" is not a
   status.
2. **Learned section is non-trivial.** It names something that
   surprised the team and/or changed its plan. "Nothing
   surprising" every month is a signal the lead is not looking.
3. **At-risk section is honest.** At least one real risk per
   review, with likelihood and mitigation. All-green reviews
   either mean the team is 4 weeks from the quarter start (fine)
   or the lead is not telling the truth (not fine).
4. **The ask is specific and actionable.** A decision, a
   signoff, an unblock, a priority call. Leadership should know
   what to do with it before the meeting ends.
5. **AI-specific framing.** Risks and shipped items that touch
   model behavior, data, or security reference NIST AI RMF
   functions, OWASP ML Top 10 items, or MITRE ATLAS tactics by
   name where load-bearing. Decorative references do not count.
6. **Pre-read circulates ≥ 24 hours in advance.** Live meetings
   that are the first exposure to the material waste leadership
   time.
7. **Deck is ≤ 10 slides** (or pre-read ≤ 2 pages). Longer
   materials do not get read.
8. **Everything references the roadmap from exercise-04.** If a
   shipped item isn't on the roadmap, flag it explicitly as
   emergent work; if a roadmap item isn't in the review, explain
   why.

## 4. Rubric / review checklist

Score each row 0 / 1 / 2 (missing / partial / strong). Passing
review: ≥ 12/18 with no zeros on rows 1, 3, and 4.

| # | Criterion | 0 | 1 | 2 |
|---|---|---|---|---|
| 1 | Shipped section with metrics | Narrative only | Mix of narrative and numbers | Every item has a metric or dashboard link |
| 2 | Learned section | Missing | Generic ("we learned to communicate better") | Specific lesson + change to plan |
| 3 | At-risk section honest | All green or vague | ≥ 1 risk | ≥ 2 risks with likelihood, impact, mitigation, owner |
| 4 | Ask is actionable | None, or "we need support" | Named ask | Named ask + deadline + what you need from the room |
| 5 | AI-specific framing | Missing | Mentioned | NIST AI RMF / OWASP ML / MITRE ATLAS tags on relevant items |
| 6 | Alignment with roadmap (ex-04) | Disconnected | Mostly aligned | Every item maps to a roadmap goal or is labeled emergent |
| 7 | Length & format | > 3 pages / > 15 slides | ~2 pages / 10 slides | 2 pages / 8 slides, scannable |
| 8 | Pre-read discipline | Introduced in meeting | Sent < 24 h ahead | Sent ≥ 24 h ahead, with linked appendix |
| 9 | Audience fit | Technical dump to a VP | Partially tailored | Tailored to the audience's decisions |

## 5. Common mistakes

- **All shipped, nothing at risk.** Leadership does not believe
  it. Trust erodes faster from one "all-green" review that turns
  out to be wrong than from months of honest amber/red calls.
- **Long status updates without asks.** Leadership's time is best
  used unblocking; if you are not asking for anything, why are
  you in the room?
- **Metrics-free "shipped."** "Significant progress on latency"
  is not a result. The number is the result.
- **Learnings as platitudes.** "We need to communicate better"
  is not a learning. A learning is a thing that changed the plan.
- **Asks that are not actionable.** "We need more support" cannot
  be acted on. "Please unblock X by Friday" can.
- **No reference to the roadmap.** Reviews that don't tie back
  to the commitments made at the start of the quarter drift from
  accountability.
- **AI-specific context omitted.** For AI infra teams, a review
  that never mentions model behavior, data integrity, or
  AI-specific risk categories is inviting leadership to treat the
  team as ordinary backend. That hurts the team's credibility
  during the next AI-risk conversation.
- **Deck optimized for the lead, not the audience.** Internal
  acronyms, charts the audience can't parse in 10 seconds, no
  summary slide. If your director can't read the first slide and
  know the state of the team, the deck has failed.

## 6. References

- NIST. *AI Risk Management Framework (AI RMF 1.0)*. NIST AI 100-1,
  January 2023. Functions *Measure* (reporting) and *Govern*
  (oversight) frame what belongs in a team review for AI infra.
  <https://www.nist.gov/itl/ai-risk-management-framework>
- MITRE ATLAS. <https://atlas.mitre.org/>
- OWASP Machine Learning Security Top 10.
  <https://owasp.org/www-project-machine-learning-security-top-10/>
- Module overview: `modules/mod-701-team-operations/SOLUTION.md`
  (section "Presentation" and "Common mistakes graders see").
- Companion exercises: exercise-02 (operating doc defines the
  review ritual), exercise-03 (stakeholder map defines the
  audience), exercise-04 (the roadmap being reported against).
