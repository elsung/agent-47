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

## Where it came from

The method itself: [BUTTON_MASH_METHOD.md](BUTTON_MASH_METHOD.md). The sources it draws on are in [REFERENCES.md](REFERENCES.md).
Changes are in [CHANGELOG.md](CHANGELOG.md).
