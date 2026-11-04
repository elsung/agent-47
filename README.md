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
| **GitHub Projects** | What to do, in what order. The owner steers here. | Ranking, pinning, the owner's run / pause / stop | live: Agent 47 project, Phase B ranked (Now / Next / Pinned) |
| **Temporal** | Who does it, and what happens next. Work survives crashes and restarts. | Rotation (continue-as-new), questions with deadlines, the tool flywheel, the daily review, the stuck check | live: rotation workflows for every thread (deadlines and the stuck check next) |
| **Claude Code `/goal` + the orchestrator (the drive)** | What keeps the system moving. Today the forward motion comes from the orchestrator's session: `/goal` sets a done-condition and a stop hook that won't let the session end until it holds, plus the orchestrator's heartbeat. | Pressing toward the goal; picking the next step; refusing to stop early | live (tied to Claude Code) |
| **Slurm** | Which GPU, and when. | GPU jobs in rank order, the owner first; job timing | live on the first box |
| **JEV → Claude Code / omp** | Which tool or model answers. JEV is our small local routing model. | Tool first; omp models (MiniMax, GLM, local open models) for research and reading; Claude for orchestrating and building. The orchestrator sets each lane's budget; every call lands in the ask log | live: tool-first router, lane budgets that route a new job one tier down past 100% |
| **Claude Code + omp** | The agents that do the work. | Orchestrator, leads, builders, readers | live |
| **Git + one MCP server (the toolbook)** | The tools, shared by every agent. Code in git; one MCP server exposes every tool to Claude Code and omp alike. | The flywheel: a model does it twice, then it becomes a tool; tools are improved, forked or merged; tool work is a card on the board | live: one stdio MCP server, allow-listed and audited; registered in Claude Code, the other runtime after hardening |
| **Git + Markdown, in tiers (memory)** | What we know. Plain files with a source, a date and a last-used stamp, versioned so nothing is ever lost. | Core (always loaded), active, reference, stash; the daily review promotes or stashes | live: in git, auto-committed on every change; tiers next |

**One dependency to keep in view.** The drive is Claude Code's `/goal` plus the orchestrator's session. If we switch
harnesses or move the orchestrator off Claude Code, the forward motion has to move too: the plan is a Temporal workflow
that holds the goal and its done-condition, and wakes the orchestrator until it holds.

People run roles, not loops: the orchestrator ranks the work; a toolsmith keeps the tools; a machinist keeps the boxes; a
method keeper runs the review; the owner steers. Every stack change updates this table and the CHANGELOG.

## What we borrowed, and where it lives

Each idea comes from a source in [REFERENCES.md](REFERENCES.md) and is a hypothesis we keep only while it works.

- **The plan is a file, re-read first** (Anthropic's long-running agent harness): every thread keeps a progress file; a
  fresh session reads it before anything else, and it lists the approaches that failed. *Lives in:* rotation (Temporal).
- **Rotate, don't compact** (Anthropic's context-engineering guidance): a fresh context with a written handover beats a
  long, summarised one; save the plan before the window runs out. *Lives in:* rotation.
- **The record is a folder, not a chat** (OpenAI's harness writing): the context window is a cache that resets.
  *Lives in:* principle 3 (Record) and memory.
- **An open question is a record with a deadline** (durable-workflow practice): it falls to a stated default when the
  deadline passes. *Lives in:* Temporal.
- **The owner watches and redirects; they don't approve every step** (Anthropic's autonomy measurements): a live board
  and one switch. *Lives in:* GitHub Projects.
- **A narrow reviewer at the irreversible boundary** (OpenAI's guardrails): a small agent that sees only the proposed
  action and the policy. *Lives in:* the four boundaries.
- **Caps on every axis** (every system that runs unattended): budget, retries, queue depth, set before the run.
  *Lives in:* Temporal and the routing budgets.
- **A skill library is the whole effect** (Voyager; AlphaEvolve's keep-the-best loop): reusable tools that accumulate
  are what make the system improve. *Lives in:* the toolbook flywheel.
- **Re-check the scaffolding when the model changes** (Anthropic): every tool and rule carries the model and date it was
  written for. *Lives in:* the daily review.
- **Events, plus a reconcile sweep** (the Kubernetes controller pattern): react when things happen; a slow sweep fixes
  what events missed. *Lives in:* Temporal.
- **Intent, back-brief, freedom within boundaries** (Bungay, *The Art of Action*) and **stream, platform and enabling
  roles** (Skelton and Pais, *Team Topologies*). *Lives in:* how the crew is led.
- **Worse is better** (Gabriel): simple and working beats complete and perfect. *Lives in:* the name.

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

## Security

We publish the principles, not the map. Specifics (addresses, ports, services, versions, rules, accounts) stay in a
private record that the crew reads and the owner can always open.

- **Private by default.** Nothing in the stack is reachable from the open internet.
- **Least privilege.** Each part can do only its job. Agent tools have no network surface, allow-list what they accept,
  and leave out anything irreversible.
- **No secrets in the repo.** Credentials live outside it, readable only by the account that uses them.
- **Humans hold the irreversible.** Spending, publishing, deleting and account changes always wait for the owner.
- **Everything is recorded.** Tool calls, memory edits and decisions leave a trace that can be read and reverted.
- **Public text is checked.** Nothing is pushed until a check confirms it names no private project, host or person.

How each layer is set up, and why: [SETUP.md](SETUP.md).

## The repo

- [AGENT_47.md](AGENT_47.md): the harness, the principles, the layers.
- [SETUP.md](SETUP.md): how each layer is set up, and why.
- [BUTTON_MASH_METHOD.md](BUTTON_MASH_METHOD.md): the method, with its examples and results.
- [skills/button-mash](skills/button-mash/SKILL.md): the skill that runs the method.
- [FIELD_GUIDE.md](FIELD_GUIDE.md): an earlier chapter on cutting model cost.
- [STEERING.md](STEERING.md), [PRACTICES.md](PRACTICES.md): steering briefs and everyday practice.
- [REFERENCES.md](REFERENCES.md): the sources. [CHANGELOG.md](CHANGELOG.md): every revision.
