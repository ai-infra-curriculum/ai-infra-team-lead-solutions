# AI Infrastructure Team Lead — Solutions Repository

Reference solutions for [`ai-infra-team-lead-learning`](https://github.com/ai-infra-curriculum/ai-infra-team-lead-learning).

A team lead operates at the intersection of three pressures: the team
(keeping engineers productive, growing, not burning out), the work
(landing the right things in the right order), and the org
(translating between the team and the rest of the company).

Most failure modes for new leads are dropping one of the three. The
solutions in this repo are structured around addressing all three
simultaneously.

## Track Overview

| Track Tier | Level | Repo |
|---|---|---|
| Team Lead | 5 (people + delivery) | this repo |
| Senior Engineer | 5 (technical contribution) | [`ai-infra-senior-engineer-solutions`](https://github.com/ai-infra-curriculum/ai-infra-senior-engineer-solutions) |
| Engineer | 4 | [`ai-infra-engineer-solutions`](https://github.com/ai-infra-curriculum/ai-infra-engineer-solutions) |

Team-lead is a peer-tier role to senior engineer, not above it.
Some engineers move into a lead role; others stay on the IC track.

## Repository Structure

```
ai-infra-team-lead-solutions/
├── README.md
├── SOLUTION_OVERVIEW.md         # design philosophy across the track
├── SOLUTIONS_INDEX.md
├── LEARNING_GUIDE.md
├── CURRICULUM.md
├── CONTRIBUTING.md
├── modules/
│   ├── mod-701-team-operations/
│   ├── mod-702-people-management/
│   ├── mod-703-project-roadmap/
│   ├── mod-704-cross-team-coordination/
│   └── mod-705-hiring-onboarding/
├── projects/                    # capstone-level lead exercises
├── guides/
└── resources/
```

## Modules

| Module | Pressure addressed |
|---|---|
| [mod-701-team-operations](modules/mod-701-team-operations) | The work — rituals, on-call, planning cadence. |
| [mod-702-people-management](modules/mod-702-people-management) | The team — 1:1s, performance, growth, hard conversations. |
| [mod-703-project-roadmap](modules/mod-703-project-roadmap) | The work + the org — defending priorities upward. |
| [mod-704-cross-team-coordination](modules/mod-704-cross-team-coordination) | The org — managing dependencies without owning them. |
| [mod-705-hiring-onboarding](modules/mod-705-hiring-onboarding) | The team + the org — talent flow. |

Each module contains five exercise-level solutions. The shape of a
"solution" here is a team-operating-rhythm document, a 1:1 + growth
template, a project-defense narrative, a cross-team commitment
register, or a hiring scorecard — see
[`SOLUTION_OVERVIEW.md`](SOLUTION_OVERVIEW.md).

## Cross-Cutting Principles

1. **The team is the unit of delivery, not the individual.** A lead
   who out-ships their team has misunderstood the job.
2. **Lead by hypothesis, not by edict.** Every rhythm, ritual, and
   policy in this track is presented as a hypothesis with success
   criteria, not a "best practice."
3. **Hard conversations don't get easier with delay.** The 1:1
   templates here are designed to surface difficult topics on a
   predictable cadence, not avoid them.

## How to Read This Repo

- **Newly promoted lead**: read `mod-701` and `mod-702` first; they
  cover the rituals and people-side foundations.
- **Considering the move from IC**: read `mod-702` carefully — most
  of what surprises new leads is here.
- **Existing lead, struggling with delivery**: jump to `mod-703` and
  `mod-704`.

See [`LEARNING_GUIDE.md`](LEARNING_GUIDE.md) for a structured reading
plan.

## Prerequisites

- [Engineer track](https://github.com/ai-infra-curriculum/ai-infra-engineer-learning) (production engineering experience).
- Recommended companion: [Senior Engineer track](https://github.com/ai-infra-curriculum/ai-infra-senior-engineer-learning) for the technical-depth balance.

## Example Deliverables

- Team operating rhythm (sprint cadence, on-call rotation, retro
  format) with success criteria and revision history.
- 1:1 + growth plan template that surfaces career conversations on
  a predictable schedule.
- Project-defense narrative — the version of a roadmap a lead
  presents up the org chart.
- Cross-team commitment register that survives team reorgs.
- Hiring scorecard + structured-interview kit calibrated to the role.

## Contributing

See [`CONTRIBUTING.md`](CONTRIBUTING.md). PRs welcome for additional
case studies, alternative ritual designs, and anti-pattern writeups.

## License

See [`LICENSE`](LICENSE).
