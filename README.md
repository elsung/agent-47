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

## The six layers

1. **Work list.** One ranked list on GitHub Projects, tagged now / pinned / quick / stash.
2. **Compute.** GPUs are scheduled through Slurm, so a run waits its turn.
3. **Routing.** A small, fast routing model sits in front of every call. It picks a tool, a cheap model or a frontier model,
   and answers the yes/no and typed checks itself, so the expensive model sees only what it is unsure of.
4. **Conductor.** Temporal keeps the loop durable. A long-running lead rotates by continue-as-new: it lands its step, writes
   a progress file, and a fresh session reads that file first.
5. **Tool flywheel.** A model does a job once or twice, then it becomes a tool. Models evolve, so tools are forked, merged
   and retired.
6. **Memory.** Tiers: core, active, reference, stash. Items are promoted or stashed by use. A daily after-action review
   reads the day's records.

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
