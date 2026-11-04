# Setup: how each layer is run, and why

This page says how each layer of Agent 47 is set up and why it is set up that way. It is written for someone who
wants to run the same stack. It names no hosts, addresses, paths or people: a machine is "the controller", "a GPU box",
"the board host". The layers and their jobs are in [README.md](README.md#the-stack-one-job-each); the principles and
the six layers are in [AGENT_47.md](AGENT_47.md).

The rule under all of it: **one home for each fact, and every layer runs on the machines it owns.** The stack keeps
working when the internet is down. The internet is an off-site mirror, never the source of truth.

## 1. The work list (board)

**What it is.** A ranked list of cards: what to do, in what order.

**How it is set up.**

- **The record is local.** Each card is a small file, written by one command-line tool. Every change appends one event
  to a local outbox file. The card files are the record.
- **A local view.** A self-hosted kanban app (Vikunja, one binary with an SQLite database) runs as a user service and
  is reachable only on the private network. It has one project with four buckets (Now, Next,
  Pinned, Later), a rank by position, and labels for phase and lane. It is a view of the cards, not a second record.
- **An off-site mirror.** GitHub Projects receives the same cards, best effort. Its writes are throttled, and a GraphQL
  budget is checked before each write. When the internet is down the outbox waits; nothing is lost.
- **One outbox, two targets.** A sync tool drains the outbox to each target, keeps per-target sync state, and merges
  edits per card. Inbound owner edits come from either target; on a clash the newest edit wins and gets one line in
  the inbox.

**Why.** A single hosted board fails when the network or the account does. Local files survive both, and the views can
be rebuilt from them. Throttling the mirror keeps it under the platform's limits.

## 2. Compute (GPUs)

**What it is.** The GPU boxes, and the rule that a run waits its turn.

**How it is set up.**

- **Slurm is the scheduler.** A controller runs the Slurm daemon. The local GPU host is a compute node of its own
  partition. Each remote GPU box with a ComfyUI server is registered as a node of its own, and all of them also sit in one shared partition.
- **One licence per remote box.** Slurm `Licenses=` holds one token per remote ComfyUI box. A job for a remote box
  asks for that box's licence, so two jobs cannot use the same box at once. The job runs its client on the local host
  and its GPU work on the remote box. The job name carries the licence label so the completion log shows which box
  did the work.
- **The pause is a flag file.** While a pause flag exists, the job-submit wrapper refuses every new start and says why.
  A sweep holds the pending jobs of the owner's account and records their ids, so release resumes exactly those.
- **Munge is the trust.** Every node authenticates with a munge key. The key is copied from the controller, never
  regenerated, and kept out of temporary directories.
- **The job log has a slurm-owned home.** The job-completion record is written to a directory the Slurm service user
  can write to.

**Why.** Slurm turns "who holds the GPU" into a queue that every agent reads the same way. Licences make the one-job-per-box
rule a scheduler fact, not a convention. The pause flag gives the owner one switch that works even when the scheduler is
busy.

## 3. Conductor (Temporal)

**What it is.** The loop that keeps each long-running lead going, and the questions and deadlines around it.

**How it is set up.**

- **User services.** The Temporal dev server, the Agent 47 worker and the link page each run as a user systemd unit,
  enabled for the account. Nothing needs root. The server is reachable only from its own host.
- **One rotation workflow per lead.** A workflow holds each lead's rotation state. A signal asks it to rotate; a hold
  flag stops rotation for a lead; a release clears it. Rotation runs as a continue-as-new step, so the workflow
  history stays short.
- **Rotation needs a fresh note.** A lead rotates only when its handoff note carries a `HANDOFF READY` line written in
  the last 20 minutes. If the note is stale, the workflow asks the lead to rewrite it, once every 30 minutes, and does
  nothing else. The fresh session then reads the note first.
- **Questions carry deadlines.** Every open question has a stated default and a deadline. When the deadline passes, the
  default is applied. The four boundaries (spend, publish, delete, accounts) never take a default; they wait for a human.
- **Two sweeps.** A stuck check raises one alert line when a card in "Now" has not changed for an hour. A reconcile
  sweep every 30 minutes fixes what the events missed.

**Why.** A lead's context fills up and degrades, so it has to be replaced, and the replacement is only as good as the
note it reads. Requiring a fresh note means a rotation never resumes from a stale plan. The 20-minute window is what
makes the note mean "this is where we are now".

## 4. Budgets: one caps file

**What it is.** One YAML file that holds every limit the stack obeys. Nothing else sets a cap.

**What it holds.**

- GitHub API budgets per hour (GraphQL points and REST calls), shared by the board sync and every `gh` call.
- Token budgets per model per day. A lane past 80% gets one line; past 100% its new reads route one tier down. Running
  jobs are never stopped by a budget.
- Question deadlines by audience (owner, orchestrator, lead).
- Retries: a render job retries once, then its card goes to failed with a note; a builder retries once, then the
  orchestrator narrows the task; a rotation retries once, then one inbox line.
- Queue depths: GPU jobs pending per box, and builders running at once.
- The stuck check and the reconcile interval.

**Why.** Every unattended loop needs a cap set before the run, and one file means one place to read them and one place
to change them. The tools read the file; they do not carry their own numbers.

## 5. The toolbook (MCP)

**What it is.** Every shared tool (the board, queue and status commands) exposed to Claude Code and to the other agent runtimes
through one Model Context Protocol server. GPU starts and anything that spends, publishes or deletes stay out.

**How it is set up.**

- **Stdio only.** The server speaks MCP over standard input and output. It opens no network port.
- **One row per tool.** Each row names a fixed subcommand, a working directory and a list of allowed flags. The server
  shells out to the real command; it holds no copy of the logic.
- **Allow-listed flags.** Every token that starts with a dash must be on that row's list. Anything else is refused with
  a message. Rows that write files are left out until they have their own review.
- **Registered per client.** Each client adds the server once, at user scope, with its own configuration command.

**Why.** One server means each tool is written once and every agent gets the same one. Stdio means there is no listener
to secure. The allow-lists mean an agent cannot pass a flag the row did not intend.

## 6. Memory

**What it is.** What the crew knows: plain Markdown files, each with a source, a date and a last-used stamp.

**How it is set up.**

- **Plain files in git.** Every memory file is versioned. Each change is committed automatically, so nothing is lost
  and every edit has an author and a time.
- **Tiers.** Core memory is always loaded; active and reference memory load per task; stashed memory is kept but not
  loaded. A daily review promotes or stashes. It moves stale text out; it never deletes it.

**Why.** A plain file survives any tool change, and git gives the history that a memory system needs to be trusted.

## 7. Lessons from the first full bring-up (2026-11-03)

- **Restart munge after any key swap.** Nodes kept rejecting each other's credentials after a new key was copied in,
  until the munge service was restarted on every node. A key change is not finished until the daemon restarts.
- **Put the job log where the Slurm service user can write.** The controller refused to start while its job-completion
  file sat in a directory owned by the account that runs the tools. The log belongs in a directory the service owns.
- **Rotate only on a fresh note.** The rotation workflow now refuses to rotate on a note older than 20 minutes and asks
  the lead to rewrite it. The note is the only thing the next session reads, so a stale one is a wrong starting point.

## 8. Before you push

This repository is public. A check runs before every push and refuses any push that names a private
project, host, address or home path. The patterns live in a private file on the maintainer's machine, not here. If that
file is missing, the check fails, and nothing is pushed unchecked.
