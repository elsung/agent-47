# Agent 47

Always on target. Loose tolerances, cheap, lasts decades.

## What it is

Agent 47 is a harness for running many AI agents on real work. An orchestrator leads a crew of agents, each in a long-running
thread, and they share tools instead of each writing their own one-offs. It runs on the
[Button Mash Method](BUTTON_MASH_METHOD.md): push hard toward the goal behind the goal, with assessment loops (look at the
real output, against the intent), not tests or gates.

## The five principles

1. **Aim.** Know the why: the goal, and the intent two levels up from the task. Assess the real output against it.
2. **Move.** Take the best reversible default and keep going. Don't wait on a choice you can make and undo. Don't stop
   other people's work. Stop when nothing is left.
3. **Record.** One ranked list, one home for each fact. The record is the memory, not the chat.
4. **Tool.** Do a job with a model once or twice, then make it a tool. Re-check the tools when the models change.
5. **Learn.** Fix what caused the mistake, not with a new rule. Every review feeds the tools, the principles and the memory.

Boundaries sit apart from the principles: no spending, no publishing, no deleting someone's work, no switching accounts
without a human's go, and a cap on every unattended loop.

## How the crew is led

The method borrows from *The Art of Action* (Bungay): a leader closes three gaps: between intent and detail, between
what is said and what is understood, and between the plan and the moment. Our answers: give intent, not detail; brief two
levels up and ask for a three-line back-brief; give freedom within boundaries. Errors of omission count more than errors of
commission: the thing nobody did is the costlier miss.

Roles come from *Team Topologies*: stream leads own a goal, a platform crew owns the tools and the machines, and an enabling
role owns the method.

## The stack: one job each

```
GitHub Projects  ->  Temporal  ->  Slurm
  what to do         who does it,     which GPU,
  and in what        and what         and when
  order              happens next
```

| System | Its one job | The loops it runs | State |
|---|---|---|---|
| **GitHub Projects** | What to do, in what order. The owner steers here. | Ranking, pinning, the owner's run / pause / stop | building |
| **Temporal** | Who does it, and what happens next. Work survives crashes and restarts. | Rotation (continue-as-new), questions with deadlines, the tool flywheel, the daily review, the stuck check | next (today: hooks do rotation) |
| **Slurm** | Which GPU, and when. | GPU jobs in rank order, the owner first; job timing | live on the first box |
| **Routing model** | Which tool or model answers. | Tool first, then a cheap model, then a frontier one | partly live |
| **Claude Code + omp** | The agents that do the work. | Orchestrator, leads, builders, readers | live |
| **The toolbook** | The tools, shared by every agent. | Grows from the flywheel | live, growing |
| **Memory files** | What we know, in tiers: core, active, reference, stash. | Promoted or stashed by the daily review | next |

People run roles, not loops: the orchestrator ranks the work; a toolsmith keeps the tools; a machinist keeps the boxes; a
method keeper runs the review; the owner steers. Every stack change updates this table and the CHANGELOG.

## Runs on events, not timers

Things trigger when they happen. One slow reconcile sweep and a dead-man's switch catch what the events miss.

## Never waits on the human

Every question carries a default and a deadline. A run can be run, paused, stopped or steered at any point. It stops when the
list is empty or the budget is spent, and it never invents work to stay busy.

## Where it stands

- **Built:** rotation at the end of a turn for every thread; the GPU scheduler's controller and first lane; parked work
  is never handed out; idle agents holding for a named reason aren't pinged; a question router that tries a tool first.
- **In progress:** the rest of the GPU lanes; the ranked work list on GitHub Projects; ~1,600 old rules collapsed into the
  five principles.
- **Next:** the durable conductor (one lead first), the tool flywheel and daily reviews on it, memory in tiers.

## The repo

- [AGENT_47.md](AGENT_47.md): the harness, the principles, the layers.
- [BUTTON_MASH_METHOD.md](BUTTON_MASH_METHOD.md): the method, with its examples and results.
- [skills/button-mash](skills/button-mash/SKILL.md): the skill that runs the method.
- [FIELD_GUIDE.md](FIELD_GUIDE.md): an earlier chapter on cutting model cost.
- [STEERING.md](STEERING.md), [PRACTICES.md](PRACTICES.md): steering briefs and everyday practice.
- [REFERENCES.md](REFERENCES.md): the sources. [CHANGELOG.md](CHANGELOG.md): every revision.
