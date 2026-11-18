# SOLUTION — exercise-02: Cross-Team Strategy Memo (Cross-Team Contract)

> Read this *after* attempting the exercise. The deliverable is a
> one-page strategy memo that functions as a **cross-team
> contract** between two team leads. The worked example below is
> a labeled teaching scenario; no real teams or incidents are
> cited as evidence.

## 1. Solution overview

A cross-team contract is the single most durable artifact a team
lead can produce for a cross-team relationship. The module
SOLUTION describes its six required sections:

1. Scope
2. Owner per team
3. The interface
4. The cadence
5. The escalation
6. The lifecycle

The memo must fit on one page. The one-page constraint is load-
bearing: a longer document will not be read by the people who
need to read it (the other team's engineers, the on-call, the
newly joined manager).

A solid submission produces a memo that the *other* team lead
would sign off on without edits. The exercise is not about
unilateral scope-setting; it is about producing a document that
survives peer review by the counter-party.

The interface and accountability structure the memo encodes
directly implements the "roles and responsibilities" control
family from NIST AI RMF `GOVERN 2` for AI systems and is
compatible with a lightweight RACI-style assignment at the
team-lead altitude.<sup>[1]</sup>

## 2. Worked answer: a one-page cross-team contract

> **Local exercise context (fictional).** The scenario — a
> Platform Team and a Consumer Team collaborating on a shared
> feature store — is a labeled teaching example. Use it as a
> template, not as an attested case.

### 2.1 The memo itself

```
================================================================
CROSS-TEAM CONTRACT: Feature Store ↔ Fraud Detection
Owners: lead-P (Platform Team), lead-C (Consumer Team)
Effective: 2026-Q1    Next review: 2026-Q2 planning
Status: Active        Version: 1.0
================================================================

SCOPE
The Platform Team's feature store serves the Consumer Team's
fraud detection model. "Serves" means both batch training
export and online lookup serving at <50 ms p99. Any feature
consumed by fraud detection is in scope; features not consumed
are out of scope.

OWNER PER TEAM
Platform (lead-P): decisions on feature schema, SLA,
  deprecation policy, on-call rotation.
Consumer (lead-C): decisions on which features to depend on,
  model release cadence, rollback criteria.

INTERFACE
1. Schema: enumerated in feature-store/schemas/fraud_v2.yaml.
2. Semantic contract: each field has a one-line semantic
   description committed to the same file. A change in semantics
   is a breaking change even if the type is unchanged.
3. SLA: <50 ms p99 online, <6h batch freshness.
4. Deprecation policy: 30-day written notice, acknowledgment
   required from lead-C before removal.

CADENCE
Biweekly cross-team sync, 30 min, agenda-driven. lead-P and
lead-C rotate ownership of the agenda each quarter. Single
shared doc; decisions marked [D], follow-ups marked [FU].

ESCALATION
Disagreement between lead-P and lead-C escalates to the shared
director within 2 business days. Platform-side on-call escalates
to lead-P; model-side on-call escalates to lead-C. Cross-team
incidents fire a joint incident with both leads paged.

LIFECYCLE
Reviewed at the start of every quarter during joint planning.
Rewritten in full once per year or whenever either team
materially changes scope. Deprecated when the integration is
retired; deprecation is a decision at the joint review.
================================================================
```

That is the artifact. One page, six sections, dated, signed by
both leads, version-controlled.

### 2.2 Decision rationale per section

**Scope.** Narrow intentionally. "Any feature consumed by
fraud detection is in scope; features not consumed are out of
scope" prevents scope creep when the Platform Team adds new
features for other consumers. A broad scope ("all shared
infrastructure") produces a contract that isn't invoked when it
needs to be.

**Owner per team.** Named roles, not people. `lead-P` and
`lead-C` are the roles; the people fulfilling them change. A
contract that names people goes stale on the first promotion.
The list of what each role decides prevents the two most common
failures: Consumer asking Platform engineers directly for
schedule commitments (schedule is the lead's call), and Platform
asking Consumer engineers directly about rollback criteria
(rollback criteria are a product decision, not a technical one).

**Interface.** Four items: schema, semantic contract, SLA,
deprecation. The *semantic contract* is the item learners most
often omit. A schema-only interface is where the case study in
[exercise-01](../exercise-01/SOLUTION.md) failed. Spell out
what each field *means*, not just its type.

**Cadence.** Biweekly, 30 min, rotating agenda ownership.
Weekly is a common default and is fine; biweekly is the right
cadence once the relationship is mature. Rotating agenda
ownership prevents one team from dominating the sync — the
module SOLUTION flags this (platform-team patronizing the
consumer-team) as a watch item.

**Escalation.** Two-business-day budget to the shared
director. Writing a time budget prevents stalemates from
becoming structural. The joint-incident clause is important:
incidents that cross teams are the ones most likely to get
double-paged or worse, orphaned.

**Lifecycle.** Quarterly review + annual rewrite + explicit
retirement path. Without the retirement clause, contracts
accumulate; teams end up supporting legacy relationships they
no longer need because no one has permission to end them.

### 2.3 What makes this memo defensible

- **Specific numbers.** "<50 ms p99", "30-day notice", "2
  business days", "biweekly 30 min". Vague commitments are
  non-commitments.
- **Named roles with scoped decisions.** The reader can tell
  from the memo who to talk to about what.
- **A review cadence.** The memo includes the mechanism that
  keeps it current. Without that, the memo is a snapshot and
  will be stale in two quarters.

## Implementation

To produce a submission that matches the worked answer above:

1. **Scope the relationship.** One sentence on what is covered
   and one sentence on what is explicitly out of scope. Narrow
   beats broad.
2. **Draft the six sections in a single page.** Scope, owner per
   team, interface, cadence, escalation, lifecycle. Use the
   fenced template as a layout starting point.
3. **Name roles, not people.** `lead-P`, `lead-C`, `on-call`.
   Attach the list of decisions each role owns next to the role
   name.
4. **Write specific numbers.** SLA (`<50 ms p99`), notice window
   (`30 days`), escalation budget (`2 business days`), review
   cadence (`biweekly 30 min`). Vague commitments do not count.
5. **Spell out the semantic contract.** Not only schema. One
   line per field describing what it *means*. This is the item
   most submissions skip.
6. **Send the draft to the counter-party lead for sign-off.**
   If they would negotiate anything, absorb that negotiation
   before submitting — the exercise asks for a *contract*,
   not a proposal.
7. **Version and date the memo.** `Version: 1.0`, `Effective:`,
   `Next review:`. A memo without a version is a draft, not a
   contract.

## 3. Validation steps

Self-check before submission:

- [ ] The memo fits on one printed page.
- [ ] All six sections (scope, owners, interface, cadence,
      escalation, lifecycle) are present and non-empty.
- [ ] Each ownership assignment lists what that owner *decides*,
      not just a title.
- [ ] The interface section includes a semantic contract, not
      only a schema.
- [ ] The cadence section specifies frequency, duration,
      agenda ownership.
- [ ] The escalation section includes a time budget.
- [ ] The lifecycle section includes both a review cadence and
      a retirement path.
- [ ] The memo is dated and versioned.
- [ ] The memo would be signed off by the counter-party lead
      without modification.

Hand the draft to a peer and ask: *"If I were lead-C, would I
sign this?"* If the answer is "I'd negotiate X first," the
memo is not done — the exercise is to produce a memo that has
already absorbed that negotiation.

## 4. Rubric / review checklist

Each section is scored 0–2 (0 = missing, 1 = present but weak,
2 = solid). The one-page constraint is scored separately.
Passing bar: 10/14.

| # | Section | 0 | 1 | 2 |
|---|---|---|---|---|
| 1 | Scope | Missing / vague | Present, broad | Narrow, enumerable, in/out of scope explicit |
| 2 | Owner per team | Names only | Roles with titles | Roles with scoped decision authority |
| 3 | Interface | Absent | Schema only | Schema + semantic contract + SLA + deprecation |
| 4 | Cadence | Absent | Frequency only | Frequency + duration + agenda owner |
| 5 | Escalation | Absent | Named escalation target | Target + time budget + on-call interaction |
| 6 | Lifecycle | Absent | Review date only | Review cadence + rewrite trigger + retirement path |
| 7 | One-page constraint | > 2 pages | 1–2 pages | ≤ 1 page |

Reviewer flags (zero out the related dimension if any apply):

- **Fictional-looking commitments** (no numbers, no named
  owners). Dimensions 2, 3, 4, 5 should all suffer.
- **No counter-party involvement.** If the draft reads like it
  was written in a vacuum, send it back for counter-party
  review before grading.
- **Hero narrative in roles.** "Senior engineer X will
  coordinate" is not a role. Name the role, not the person.

## 5. Common mistakes

- **Writing it alone.** A cross-team contract drafted without
  the other team's lead is a wish list. Draft, share, revise.
- **Over-long memos.** Five pages means no one will read it
  when the pager goes off. Keep it to one.
- **Schema contract only.** The most common failure mode; see
  [exercise-01](../exercise-01/SOLUTION.md) for the full
  pattern.
- **Named people, not roles.** Goes stale on the first
  promotion or team change.
- **No retirement path.** Contracts without lifecycle clauses
  accumulate. A team that holds a dozen stale contracts has
  approximately zero contracts in practice.
- **Vague SLAs.** "Fast" is not an SLA. "<50 ms p99" is.
- **Escalation without a time budget.** A disagreement with
  no deadline turns into structural stalemate.
- **Framework worship.** Pulling in ITIL/RACI/ISO terms the
  other team doesn't use makes the memo harder to read for
  no gain. The memo should use the counter-party's vocabulary.

## 6. References

1. NIST AI Risk Management Framework (AI RMF 1.0) — `GOVERN 2`
   on accountability structures, roles, and responsibilities.
   <https://www.nist.gov/itl/ai-risk-management-framework>
2. Module SOLUTION: [../SOLUTION.md](../SOLUTION.md), section
   "The cross-team contract (exercise 02)".
3. Related exercises:
   [exercise-01](../exercise-01/SOLUTION.md) (the case study
   this memo would have prevented),
   [exercise-03](../exercise-03/SOLUTION.md) (the stakeholder
   map the memo references implicitly),
   [exercise-04](../exercise-04/SOLUTION.md) (the joint
   roadmap this memo scopes).

<sup>[1]</sup> NIST AI RMF 1.0 `GOVERN 2` names accountability
structures, roles, and responsibilities as a baseline
governance control. The cross-team contract is one concrete
team-lead-altitude implementation of that control; the exercise
teaches the artifact, not the framework.
