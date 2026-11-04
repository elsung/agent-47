# Agent 47: the harness

We are the Hitman: always on target. Agent 47 is the name of the harness, and the Button Mash Method is the method it runs.
The name is an easter egg, tongue in cheek: the engineering lineage is loose tolerances, a design that runs dirty in any
field, parts stripped to what matters, anyone can keep it running, cheap to make, and it lasts decades. The design year is 1947.
Why 47? Ask an engineer about loose tolerances.

## The five principles

1. **Aim.** Know the why: the goal, and the intent two levels up from the task. Assess the real output against it.
   Assessment loops, not tests or gates.
2. **Move.** Take the best reversible default and keep going. Don't wait on a choice you can make and undo. Don't stop
   other people's work. Stop when nothing is left to do.
3. **Record.** One ranked list, one home for each fact. The record is the memory, not the chat. Talk on the record, directly.
4. **Tool.** Do a job with a model once or twice, then make it a tool. Models change, so re-check the tools when they do.
5. **Learn.** Fix what caused the mistake, not with a new rule. Every review feeds the tools, the principles and the memory.

Boundaries stay separate from the principles: no spending, no publishing, no deleting someone's work, no switching
accounts without a human's go; and a cap on every unattended loop.

Vocabulary: assessment, check-in, alignment, experiment. Not test, eval or judge.

## The six layers

1. **Work list:** one ranked list, kept on GitHub Projects.
2. **Compute:** GPUs are scheduled through Slurm; a run waits its turn and does not reach around the lock.
3. **Routing:** a small, fast routing model in front of every model call routes it to a frontier model or a local one, and answers
   the yes/no and typed checks itself, so the model sees only what it is unsure of.
4. **Conductor:** a durable workflow engine (Temporal) keeps the loop going. A long-running lead is rotated by
   continue-as-new: it lands its step, writes its note, and a fresh session picks up from the note.
5. **Tool flywheel:** a repeated hand job becomes a tool; a retrospective is generated from the records, not written from memory.
6. **Memory:** tiers (always-on, per-task, archived) and a daily review that moves stale text out, never deletes it.

## Who runs what: the loops

Every loop has one owner, one trigger and one place its result lands. Roles, not people: the orchestrator; stream leads
(each owns a goal stream); the platform crew (a toolsmith for tools, a machinist for machines); the method keeper (the
enabling role); the owner.

| Loop | Trigger | Who runs it | Result lands in |
|---|---|---|---|
| Rotation | A thread's context reaches its window, at a natural break | The thread writes its handoff and marks it ready; the conductor (today the end-of-turn hook) clears and restarts it in the quiet moment; the owner can hold or call it | The handoff / progress file the fresh session reads first |
| Ranking the work | A card added, finished or moved; a milestone closes | The orchestrator owns the order; the owner can move anything | The ranked board |
| GPU work | A job submitted | The scheduler, in rank order; the machinist keeps the boxes healthy | Job timing record + the card |
| Routing a call | Every model call | The routing model: tool, cheap model or frontier model; the toolsmith keeps the router | The ask log |
| Tool flywheel | The same ask seen 2-3 times, or a tool that fell short | The toolsmith builds, improves, forks or merges the tool (a model helps when the tool must change) | The toolbook; the ask log shows tool hits rising |
| After-action review | Daily, and at each milestone close | The method keeper: what was meant, what happened, why, what next | Tool cards, principle edits (owner picks), memory moves, the changelog |
| Memory | The review; use counts | The method keeper promotes or stashes; nothing is deleted | Core / active / reference / stash |
| Scaffold re-check | A model changes | Toolsmith + method keeper re-read each tool and rule written for the old model | Kept, changed or retired, with a date |
| Questions | Anyone needs a call | Asked with a default and a deadline; the default runs when the deadline passes | The decisions list (reversible) |
| Steering | Whenever the owner wants | The owner: run, pause, stop, steer, and the four boundaries | The board and the switch |
| Stuck check | Nothing moved for an hour while work is in Now | The dead-man's switch alerts; the reconcile sweep fixes missed events | One alert line |

## Where it came from

The method itself: [BUTTON_MASH_METHOD.md](BUTTON_MASH_METHOD.md). The sources it draws on are in [REFERENCES.md](REFERENCES.md).
Changes are in [CHANGELOG.md](CHANGELOG.md).
