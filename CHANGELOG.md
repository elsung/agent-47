# Changelog: the Button Mash Method and skill

One entry per revision. Semantic versions:
- **patch**: wording;
- **minor**: a new guideline or worked example;
- **major**: a change of approach.

Each entry names the real incident or owner note that taught it.


## 1.71.6 (2026-11-02)

Patch, wording only. Five method lines from a lead rotation: name the real output before reading a result; verify an
input reached the graph before reading a difference; report cold and warm timings apart; open the board before naming a
framing; check the live queue before launching on an owner box.


## 1.71.5 (2026-11-02)

Patch, wording only. A broad search over the repo root or `/` times out and leaves a stray job: scope it to one folder
with a timeout, and check for stray jobs with the process listing. Owner note from two lead rotations (Pixel, Smithy).


## 1.71.4 (2026-11-02)

Patch, wording only. Three lines from one lead's rotation: read the board before calling a take clean; pick a replay
target whose board has been read; when blocked on other leads, post one blocked line with owner and time, then wait on a
real signal. Owner #2532 (keeper learnings).


## 1.71.3 (2026-11-02)

Patch, wording only. A speed claim needs a before and after number, measured the same way, read cold from the real output
rather than a status line. Owner #2532 (keeper learnings).


## 1.71.2 (2026-11-02)

Patch, wording only. Method body pass: the rule words (never, must, always) in the rules and principles reworded as plain
reasons, so each rule reads with its why (139 hits down to 75; the rest are owner quotes and incident descriptions, which
stay as written). Context loads: one file per hook, sized where it is written. Owner #2538/#2543. Skill unchanged (1.69.1).


## 1.71.1 (2026-11-02)

Patch, wording only. Prompt hygiene: MUST/NEVER/all-caps and "think carefully" habits reworded as plain reasons, in the
skill summary and the method summary (rule words 66 to 47). Three keeper learnings from a lead rotation added: open
builder briefs with the ask; a long-lived process keeps old code, so list the restarts for any target change; verify a
builder's claim before --go. Handoff notes are rewritten whole under 8K (owner #2538/#2543). Skill to 1.69.1. Owner
#2526 (prompt hygiene), #2532 (keeper learnings), #2543 (handoff size).


## 1.71.0 (2026-11-02)

**Minor: a toolsmith thread keeps the set of standing tools small (owner, 2 November).** The build-once section gains the
role: one thread owns the toolbox (the picker's table and examples, the standard, the shared helpers, the miner, the
daily retro and the weekly prune), thinks on a strong model and leaves the code to cheap builders. Every other thread
follows one rule: use a standing tool, else extend it with a flag or mode, else build one once to the standard. The
owner's words are quoted in the section. SKILL.md is unchanged at 1.69.0.

## 1.70.0 (2026-11-02)

**Minor: the standard for a tool (owner #2520: fast to write and iterate, lean, effective, less buggy).** The
"Build a tool once, then refine it" section gains the standard: Python 3 with the standard library first (measured
startup about 0.01 s, our tools 0.06 to 0.2 s, the time is I/O; Rust or Go only for a measured CPU-bound hot path); one
file, one job, `--help`, `--json`; a shared helper module and one use line per run; typed, small functions and no bare
`except`; a fast linter on every edit as a note, never a gate; search and extend before building; three to five example
questions per tool. The lookup picker follows the standard. SKILL.md is unchanged at 1.69.0.

## 1.69.0 (2026-11-02)

**Minor: build a tool once, then refine it; a picker chooses, code runs (owner, 2 November).** A new section in
BUTTON_MASH_METHOD.md, "Build a tool once, then refine it". The owner asked that agents stop rebuilding the same tools
each time, and that a picker choose among existing tools with code doing the work. The section carries the owner's words,
the miner's evidence (22,707 hand-run shell calls in one day, the most repeated shapes), the seven-step loop (mine, build
once, name with examples, pick then run, misses feed the miner, daily retro, weekly prune), and the language call (Python
by default; port only a hot path a measurement shows is CPU-bound). The skill changes by one line: its "Forward and
clean" bullet now says to build a tool once and refine it, and that a picker chooses while code runs it. SKILL.md is 1.69.0.

## 1.68.3 (2026-11-02)

**Patch: two lessons on the context budget and continuity (owner #2502, #2506, #2508).** Added to BUTTON_MASH_METHOD.md
under "Context and continuity". (A) "Context is a budget: spend it on judgment, not transport": leads started at 44 to 58K
of a 100K window and grew about 4.4K a minute, mostly raw tool output; the good move is a lean launch, tools/ask.py,
output caps and subagents that return conclusions. (B) "Continuity is the agent's own note at a seam, not a scrape or a
/clear": a /clear behind six working leads lost their threads and six owner asks; the good move is an 80K transition
window, a hand-off note written by the lead itself, a lean relaunch that loads it first, and STALE-LAUNCH flags. The skill
SKILL.md is unchanged at 1.68.2 (owner #2508: it was just cut to 8KB on purpose and stays small).

## 1.68.2 (2026-11-02)

**Patch: a shorter skill (owner #2492, too much bloat in every session).** The skill is loaded into every session's system
prompt, so SKILL.md shrinks from 26,675 to 7,979 bytes (-70%). The north-star section, hard guidelines and strong steering
stay in SKILL.md with the same meaning in fewer words. The 38 worked examples that were in SKILL.md moved to
references/EXAMPLES.md, read on demand, next to the 18 older examples already there. Counts checked: 38 and 18, none lost.

## 1.68.1 (2026-11-02)

**Patch: lesson 262.** Guidance reaches a worker only through the brief it is started with. Builder and lead briefs carry the model-stack pointer; subagents started from a session did not, so each spawner pastes the pointer and the weekly toolbook pass samples subagent prompts.

## 1.68.0 (2026-11-02)

**Minor: fifteen lessons (247-261) and the gates-to-notes rule.** Follows 1.67.0. The owner's process lessons from the last day, written
generally, each with its story and the good move: a goal-gap pass every heartbeat (247); three living documents from one
source (248); test a model at its recipe first (249); a fair comparison (250); a result watchable from its own record
(251); real links and a no-login copy (252); a sensible default never waits (253); read every comment (254); ration the fast
models by urgency and difficulty (255); judge the whole scene (256); check a claim against the record (257); learn from
non-commercial tools, ship your own rebuild (258); repeated patterns become tools, pruned weekly, guidance in every brief
(259); the cure for pressure is notes and defaults (260); no hard rules, no gates, no coding tests, experiments stay (261).
The skill's "No gates" bullet now names coding tests and says every guideline is a reason, not a rule to enforce.

## 1.67.0 (2026-11-01): three worked examples: a speed pack that held the frame, a default kept by measure and eye, the best face not the first
- **Method doc:** three worked examples in "Spend where it counts, in practice": a speed pack approved only where its frame
  held (about 4.4x on the same shot, the reference mode dropped); a newer checkpoint kept out by a rerun at each side's own
  settings, the default changed only where measure and eye agree; a face check that now scores every face and keeps the
  best, with the score as a note. From the night of 2026-11-01.
- **Method doc header:** the version line read 1.63.0 while the changelog was at 1.66.1; it now matches this entry.

## 1.66.1 (2026-11-01): hardware is a lane too
- **Method doc:** one line in "Spend where it counts, in practice": the same board job measured 2 min 17 s on the big
  workstation card and 16 min 58 s on a small box (~7.4x), so time each hardware lane once in the real system, route
  heavy board work to the big card when it is free, and treat the small-box time as the bar for speed variants. From
  the 2026-11-01 timed S10 drafts.

## 1.66.0 (2026-11-01): a worker missing its asset fails the job, not the batch
- **Method doc:** one more worked example in "Spend where it counts, in practice": the board fan-out spread ~31 board
  jobs across idle boxes and 24 failed twice because their boxes lacked the one control model the boards need. The fix
  is a claim-time rule — a job whose card names an asset the worker does not list goes back to the queue and that
  worker is skipped on the next claim, while a refusal on the job's own card still fails the job. From the
  2026-11-01 board-spread failures and the same-day fix.

## 1.65.0 (2026-11-01): land the ordering fix, then re-measure on a controlled run
- **Method doc:** one more lesson in "Spend where it counts, in practice": the ordering fix from the work-vs-wait
  split (timed scene's board first under its own lane) was landed and re-measured the same day — a controlled
  single-scene rerun cut board-release-to-draft from 37.8 to 7.5 minutes on identical board and seed. The next
  sink moved with it: a full scene's ~26 boards would still queue on one card, so the next lever is spreading
  boards across idle boxes. From the 2026-11-01 timed-shot-first run.

## 1.64.0 (2026-11-01): a distilled variant wins only with the frame anchored
- **Method doc:** one more worked example in "Spend where it counts, in practice": a distilled speed variant drew the
  same board 645 s → 146 s (4.4x, same seed) and held framing by eye and typed-model read, so it was approved for the
  production path the same day — but its reference mode (identity from references, no first-frame anchor) kept faces
  and dropped the framing from about frame 24. Lessons: a speed claim is only true for the mode and anchor that was
  timed; promote on the paired control read, not the clock. From the 2026-11-01 speed-variant approval.

## 1.63.0 (2026-11-01): split work vs wait per stage before tuning anything
- **Method doc:** one more lesson in "Spend where it counts, in practice": a timed end-to-end run carried a 23-minute
  stage that was pure waiting on its own scene's intermediate render, stuck behind ~20 others in an exclusive-render
  queue; the per-stage work-vs-wait table showed it in one read, and the fix is ordering (current scene's jobs first
  under their own lane), not a faster GPU or a new route. From the 2026-11-01 timed-run work-vs-wait note.

## 1.62.0 (2026-11-01): speed settings are decided on paired by-eye frames
- **Method doc:** one more lesson in "Spend where it counts, in practice": finals speed settings are read on paired
  frames by eye (single-frame numbers swing); an int8 VAE matched fp16 and saved 10–14 s of decode per take, while a
  4-step speed LoRA that drifted framing was dropped as a final. From the 2026-11-01 finals A/B (desk item
  speed-default-s3s4-2296e).

## 1.61.0 (2026-11-01): faster lanes, more takes on the feel per hour
- **Method doc:** one more worked example in "Spend where it counts, in practice": a render previz that waited on one card
  (boards on one box, a test run's shot held behind a busy card), and a run that queued nothing with no note. Two small
  patches fixed the routing and the note, and the scene was timed again.
- **Strong steering:** measure the slow step in the real system before changing anything, and keep the owner's opt-ins.

## 1.60.0 (2026-11-01): draft tiers need a control arm before they win
- **Method doc:** one more worked example in "Spend where it counts, in practice": a render-speed A/B where the
  fastest lane (4 steps) lost to the mid lane (5 steps + VAE 2x) because it failed the by-eye read, and the mid
  lane could not be promoted until a control arm (fp16 VAE) closed the loop on the int8 VAE.

## 1.59.0 (2026-11-01): a local decision model
- **Method doc:** how a sister team runs open-weights decision models locally: one forward pass, option-letter logits
  and a softmax over the listed options, under llama.cpp with the same wire format as the hosted API. Covers
  benchmark parity, determinism, prefill-bound latency and a real CI-triage trial with its confidence thresholds, plus
  what to know before building one.
- **Skill:** the decision-model steering says hosted or local.

## 1.58.0 (2026-11-01): decide fast, read locally, ration the cloud
- **Strong steering, "Mash, but spend where it counts":**
  - a fast decision model answers typed questions before an LLM is asked;
  - research reading moves to a local model once a bake-off on real tasks shows it reads well enough.
- **Two worked examples:**
  - the token budget that ran out, and how the lanes were moved (decision model, local reader by bake-off, the
    hosted model rationed, shared machines treated as live work);
  - the speed test whose control paid a cold reload (time each stage).
- **Method doc:** new section "Spend where it counts, in practice", with the lane table, the reading bake-off table
  and its lessons.
## 1.9.1 (2026-10-21)

**Patch: wording in the research digest.** Trimmed `research/FORWARD_AND_CLEAN.md` to the 1500-word budget without
dropping a source, a practice or a signal: the weekly fitness-function report detail, one repeated quote and three
loose phrases went; every link, figure and starting-point verdict stayed.

## 1.57.0 (2026-10-26)

**Patch-level lesson (246, owner #1644: no gates, no coding tests).** Builders report the real output (the page, the file,
the render, the run) and not a test run. A "tests pass" report is not progress, so none counts as evidence.

## 1.56.0 (2026-10-26)

**Minor: five lessons from the drive loop (241-245, owner #1642).** Idle means an empty prompt over an unchanged pane, not
"no child processes". A watch that re-flags the same cards without acting is motion, not progress, so each flag is acted
on or closed. Grep the inbox and the other lead's posts before starting a builder. Read a file's reader before writing a
new shape into it. A "done" report is checked on the live endpoint before it is posted.

## 1.55.0 (2026-10-26)

**Minor: two lessons (239-240).** Fix the writer as well as the file: a status file rewritten on a timer undoes a hand
edit unless the writer's prompt carries the same rule. And when the owner's named source cannot be read, use the copy
the owner pointed to, say which one, and do not create the missing file.

## 1.54.0 (2026-10-25)

**Minor: two lessons (237-238).** Read why a worker exited before relaunching it with the same brief: four builders
relaunched unchanged exited the same way, and the first one checked had a path the job guard refuses. A retrospective
row that cites a fix you cannot read cites the record that announced it and is marked unconfirmed until the commit is
seen.

## 1.53.0 (2026-10-25)

**Minor: two lessons (235-236).** A standing rule is checked for reach in the running agent's transcript, not in the file
that carries it: a system prompt is read at start and a prompt hook fires on the next prompt, so the file alone proves
nothing. Each runtime needs its own per-turn hook and its own probe; an omp session read no Claude hook, and the probe
ran on a fresh session, never on a live lead.

## 1.52.0 (2026-10-25)

**Minor: the north star comes first (owner #1480, renamed #1482).** A new section in the skill: every project has one
north star, the goal behind every goal in the owner's own words. Read it at the start of every session, round and brief;
assess results against it before the spec; treat rules as hypotheses that retire when they stop serving it; keep the
owner's voice. A worked example shows a creative pipeline that grew narrow rules and got more correct without moving.

## 1.51.0 (2026-10-25)

**Minor: one lesson (234).** A caller imports a new shared module only after the module is on the engine it runs on; a
lab tool that imported it early would have failed for every caller in that window.

## 1.50.0 (2026-10-25)

**Minor: two lessons (232-233).** A check writes no cache, so nothing is left to delete (the same slip as lesson 230, a
second time: the fix is in the check, not the cleanup); a record of what a picture was made from is written by the step
that makes it, from the files on disk.

## 1.49.0 (2026-10-25)

**Minor: three lessons (229-231).** A check that cannot pass still hands over its best result, with the count and the
tries beside it; a removal goes to the trash folder even for a file made a minute earlier; a redraw loop writes beside
the original and never over it.

## 1.48.0 (2026-10-25)

**Minor: four lessons (225-228).** A folder named for the step that moved it, so a check misread a run's pictures; a
measure blamed before its recorded input was replayed; a flat trend read as a result before the pixels were compared; a
measure trusted before a control showed it could move.

## 1.47.0 (2026-10-25)

**Minor: four lessons (221-224).** A regression shot shown with a stale score and no reason; a cache window that hid a
test's own write; a "idle" status for a box rendering between prompts; a proof builder that exited silently and was taken
as done.

## 1.46.0 (2026-10-25)

**Minor: four lessons (217-220).** A stall watch that reported errors and missed an 80-minute silence; a verdict counted
on any dip instead of the protected number; a command chain that committed past a failing test; a copied record that
kept a skim's identity and drew a card twice.

## 1.45.0 (2026-10-24)

**Minor: four lessons (213-216).** A module whose import replaced a core check; a loop starved by a busy owner's queue;
an alert that counted pings as intrusions; a test guard its child process went around.

## 1.44.0 (2026-10-24)

**Minor: five lessons (208-212).** A regression set re-rendered after each change, shown not gated; a cleanup that took
back live work it guessed was orphaned; a refresh slow from one call per working copy; a proof's false defects from its
own clock; a per-run cross-disk copy.

## 1.43.0 (2026-10-24)

**Minor: four lessons (204-207).** A retry that lived in one scheduler's branch; a model's right answers dropped over a
plural; test runners stacking work beside a live run; a cost blamed on a setting by comparing cold loads with warm ones.

## 1.42.0 (2026-10-24)

**Minor: three lessons (201-203).** A test called stale that was guarding a real break; a test suite that "hung"
because the data disk was saturated; a merge step that reported success when git had refused.

## 1.41.0 (2026-10-24)

**Minor: three lessons (198-200).** Reordering two serial jobs that brought the first episode forward but not the
last; a "renders after previz" gate that held every take for a review copy no take reads; an early animatic that looked
like the result but had one voice.

## 1.40.0 (2026-10-24)

**Minor: five lessons (193-197).** A three-day-old wrong path revealed when a fallback was removed; a linked folder
missing the files beside it; a shared clip read while being written; one log format for every test; a stop tool that
sent the restart signal.

## 1.39.0 (2026-10-24)

**Minor: three lessons (190-192).** A relaunch that would have started a second run from a stale brief; an allow-list
written as sentences that matched no job; a compared setting that was a code constant.

## 1.38.0 (2026-10-24)

**Minor: seven lessons (183-189).** The crew's two phases, read by every rule; a test copy that re-planned itself; a
test stub bypassed by a direct address; paused work moved as idle; a stale file read as a result; one machine with
three locks; a watchdog rule that would have cancelled the owner's runs.

## 1.37.0 (2026-10-24)

**Minor: five lessons (178-182).** A worker handed an owner machine's address; a stopped worker's half-made change
landed; a run's idle first twenty minutes; a picture called unused that most boards started from; workers parked on
waiters that died with their session.

## 1.36.0 (2026-10-23)

**Minor: five lessons (173-177).** Board jobs that kept a processor slot while waiting for the card; a split whose
scheduler still read the old flag; a wait for a prop nothing made; two writers in one status file; an urgent line
read 30 minutes late.

## 1.35.0 (2026-10-23)

**Minor: five lessons (168-172).** A test copy that wrote 7 GB it only read; a fix that did not reach a pinned runner;
an agent that searched the disk for a file it was never given; a branch switched in a shared checkout; a wait that
did not use the run's own rule for made.

## 1.34.0 (2026-10-23)

**Minor: five lessons (163-167).** A cleanup that moved a live session's working folder; a name two stages spelled
two ways; a retry rule whose pattern missed the real error; one word, paused, that carried two orders; a draft split
from its boards that mixed too early and was never made again.

## 1.33.0 (2026-10-23)

**Minor: four lessons (159-162).** A pool checked before the lock, so later episodes re-voiced every line; a status
job whose due time ignored its tick; a cut promised from the plan while retries made the cost; a removed card whose
silent readers were left behind.

## 1.32.0 (2026-10-23)

**Minor: five lessons (154-158).** A wrapper's lock its own child waited on; a disk priority the scheduler ignored; a
note file that a worker committed; an A/B run on a shared card; relabels counted as revisions.

## 1.31.0 (2026-10-23)

**Minor: three lessons (151-153).** Builders that stopped at a verified cause outside their scope; a copy that kept a
production-only setting; worktrees that grew back because the maker checked out everything.

## 1.30.0 (2026-10-23)

**Minor: five lessons (146-150) from the night.** A launcher stopped while its worker ran on; two movers on one
folder; a rank that could not hold back work that was not waiting; a switch cost hidden in the first sampling step; a
memory guard on the wrong resource.

## 1.29.0 (2026-10-22)

**Minor: lesson 145 and a worked example: retrospectives as standing practice.** Every run ends with a retrospective
in the repository: result, where the time went, causes and fixes, a pre-flight checklist and a regression table. It
links back, has a rolling index, is updated through prep, and is checked before the next run.

## 1.28.0 (2026-10-22)

**Minor: three lessons (142-144) from the history rewrite.** The rewrite moved every release checkout's HEAD; a
prune judged idle by process and caught a branch waiting to land; a move across disks was a copy that a cleaner
broke halfway.

## 1.27.0 (2026-10-22)

**Minor: lesson 141 and a worked example on repository hygiene.** A code repository grew to gigabytes of
committed evidence media, copied into every worktree and release. The fix: ignore media at setup, move evidence to a
data drive with links at land, check the size in the doctor, then rewrite the history once, behind a mirror alternate.

## 1.26.0 (2026-10-22)

**Minor: five lessons (136-140) and a worked example from the evening.** A no-redo switch that judged "made" by the
job and skipped first makes; downstream readiness left waiting for an upstream nobody would remake; a fix applied in
part and caught by a dry run of the pinned code; test copies at new code that restaled everything; a leak check that
held its own private list.

## 1.25.0 (2026-10-22)

**Minor: five lessons (131-135) and a worked example from the afternoon.** Breakers that leaned on what the stall
broke; a premise checked in the data before building; a builder's prose request the lander never read; test jobs
lowered below production on the CPU; a grace for heavy models that starved light ones.

## 1.24.0 (2026-10-22)

**Minor: five lessons (126-130) and a worked example from the afternoon.** Shared files broken by a writer the safety
proof never ran; a full and a shortened hash compared as equals; a stage that recorded its own product as input;
per-source write numbers that pointed away from the obvious suspect; a failed judge nobody retried.

## 1.23.0 (2026-10-22)

**Minor: five lessons (121-125) and a worked example from the late morning.** Workers that served one box while
work was spread over three; a free-memory figure read the wrong way on shared-memory machines; copies born with their
source's pause; copies duplicating read-only media; idle loops re-reading unchanged files.

## 1.22.0 (2026-10-22)

**Minor: five lessons (116-120) and a worked example from the morning.** A rule that only new code applied, on a card
where every process ran old code; a cancel that needed a dead runner to deliver it; a folder taken as proof of a
builder; a fix for one stale reason while the class still failed; idle decided by declared states while the disk
filled.

## 1.21.0 (2026-10-22)

**Minor: five lessons (111-115) and a worked example from the early morning.** A live head that never took its turn;
one job run by two processes; one name with two meanings; a record read under the wrong name; what comes back after a
reboot as a list you can check.

## 1.20.0 (2026-10-22)

**Minor: a strong-steering line and lesson 110 (owner, standing rule).** Fix where the wrong thing is decided, once;
remove the workarounds it makes unneeded; stack no new guard; say the core cause in the change note. Lesson 110: a
stack of patches that each correct the one before means the fix sits below the cause.

## 1.19.0 (2026-10-22)

**Minor: three lessons (107-109) and a worked example from the small hours.** A long-running loop that ran its start-up
code for ten hours, so six reported checks never ran; a new check silent on a wrong match; a watch that matched an old
mention instead of what the live work targets.

## 1.18.0 (2026-10-21)

**Minor: six lessons (101-106) and a worked example from the night.** Decisions revisited while work waits; shared
resources measured where they are shared; one name per thing; every fence honouring a deliberate opening; exceptions
that survive a restart; services restarted when their code changes.

## 1.17.0 (2026-10-21)

**Minor: five lessons (96-100) and a worked example from the evening.** Checking a reported cause before fixing it; a
fixed-size list that dropped the urgent item; a left state's fields that kept saying it; hand cleanup made the
system's; editing a hand-written file as text.

## 1.16.0 (2026-10-21)

**Minor: six lessons (90-95) and two worked examples from the afternoon.** A held box reached through a pinned name;
failed work showing its last progress line instead of its cause; a default expiry silently undoing a person's hold;
a reader watch blind to jobs with no declared output; backing off on the same model instead of a silent switch; and
freeing idle resources.

## 1.15.1 (2026-10-21)

**Patch: public-safety scrub.** The method's worked log named private project, mission and character names and run
ids; they are now plain roles ("the UI mission", "a character", "a run"). A check (scripts/public_check.sh) now runs
before every push and refuses one that names the private project.

## 1.15.0 (2026-10-21)

**Minor: "Staying smart through a very long run", the owner's observation, as a method section and a worked example.**
Living sources of truth kept current (board, review desk, research docs, pipeline spec), watched closely, checked on
every heartbeat by a regression watch that fixes safe drift and flags the rest, and old documents archived with an
index instead of rotting or being deleted.

## 1.14.0 (2026-10-21)

**Minor: one worked example in the skill, method lessons 84-89.**

- **A long-lived process runs the code it loaded:** reload rules on change.
- **"List what is left" erases what is done:** keep finished items, send changes.
- **A citation must be about the claim:** quote the source beside it.
- **A copy inherits its source's state:** decide what comes along.
- **A per-worker file must not live in a shared place:** one report file caused most merge conflicts.
- **The rules you give agents bind you too.**

## 1.13.0 (2026-10-21)

**Minor: one worked example in the skill, method lessons 78-83.**

- **Check before spending:** stale inputs were found only after four-minute renders.
- **A real need without a door goes around the fence:** give it a door, then fence.
- **Stopping a worker takes back what it sent:** a stopped job's request kept rendering.
- **Writer and reader agree on a contract's shape:** a guard misread the window file it was meant to honour.
- **Reverse a wrong rule cleanly:** in code and briefs at once, saying what it replaces.
- **A checklist is not a ladder:** independent milestones are checked together each round.

## 1.12.0 (2026-10-21)

**Minor: one worked example in the skill, method lessons 74-77 (the rest of the roll night).**

- **A new rule meets the old ones:** two right rules together moved a lab run onto the main card mid-roll.
- **A hold must not wait on what it holds:** a hold until the cut blocked what the cut needed.
- **A waiting job must not hold capacity:** waiting jobs filled every slot.
- **One state, one owner:** two watchers resumed and held the same runs.

## 1.11.0 (2026-10-21)

**Minor: one worked example in the skill, method lessons 69-73 (the roll night).**

- **A rule enforced by the asker's code fails while older code runs:** enforce where every version passes, sweep too.
- **A sweep reacts; a guard at the door prevents:** refuse at start, keep the sweep as a backstop.
- **Your own automation must respect the owner's live work:** a routine restart hit the live roll.
- **Background work can die with its starter:** a timer's job was cleaned up every hour for four hours.
- **Read a declared output where the worker writes it:** relative paths read as absolute caused false failures.

## 1.10.0 (2026-10-21)

**Minor: one worked example in the skill, method lessons 64-68, and Forward and clean's first results.**

- **A rank means something only inside the queue that made it:** a cross-project cap kept a timed run off the card.
- **Mark at the moment it becomes true:** A run that started after its runner was never marked timed.
- **Check the effect, not the echo:** a collapsed long message made a delivery check resend it for half an hour.
- **A hang is silence on every meter at once:** watch the conjunction, then escalate in steps.
- **Count implementations, not names:** a name count missed a six-to-one consolidation.

## 1.9.0 (2026-10-21)

**Minor: "Forward and clean", the owner's question of moving fast without code rot.** A new method section with ten
practices (one commit one kind; tidy what the change needs; look it up at the second copy, consolidate at the third;
a map per area cited in briefs; one writer per hotspot; a signal-fed cleanup queue with a floor while trends worsen;
delete by moving only what evidence says is dead; small landings and migrations, never rewrites; rot as a trend;
outside eyes), a steering line in the skill, and the research digest (research/FORWARD_AND_CLEAN.md).

## 1.8.0 (2026-10-21)

**Minor: one worked example in the skill, method lessons 59-63 (the night's incidents and owner corrections).**

- **An environment pointer travels to everything spawned under it:** agents' lab-box pointer sent real runs there.
- **Guard the write, not the door:** a UI check reached live data through an unfenced path.
- **A cleanup check must recognise every shape of the thing:** a second launch form hid runners for seven hours.
- **Goals evolve; keep the path versioned:** judges revise milestones from the owner's newest words, history kept.
- **What a process starts, it stops:** leftover test children pushed the machine's load to 72.

## 1.7.1 (2026-10-20)

**Patch: public-safety scrub.** Session window names and a private config path in older method lessons are now
plain roles ("the orchestrator", "a lead").

## 1.7.0 (2026-10-20)

**Minor: two worked examples in the skill, two in EXAMPLES.md, method lessons 54-58 (the standing refinement pass).**

- **Count only what someone is waiting on:** an idle-GPU alert counted two dead research queues as owner work.
- **Two tools on one thing share one lock:** a prune during a move cost a worktree its git record.
- **A superseded run competes with its replacement:** an ownerless old run held the card the live run needed.
- **A delete is the owner's:** gather it in one folder, size it, give one command, remind weekly.
- **Report the number that didn't move:** the disk move barely changed disk load; renders were the cost.

## 1.6.0 (2026-10-20)

**Minor: one guideline line and six worked examples from the evening (the standing refinement pass).**

- **Reproduce on the real thing as it really runs:** two profiles on a cut-down copy found nothing; a full copy showed
  16 s of work in every 2 s tick.
- **A repeated reason is the code, not luck:** one job failed four times on the same error and was retried each time.
- **A fence guards a resource, not one door:** a 3D preview reached the GPU through the graphics driver.
- **Check for a live sibling before a restart:** a relaunch put two builders in one worktree.
- **Measure what idle costs:** idle processes re-read their whole history every two seconds.
- **Hand cheap agents the answer:** a judge searched a slow disk for outputs the system already knew.

## 1.5.0 (2026-10-20)

**Minor: one guideline line and four worked examples from the afternoon (the standing refinement pass).**

- **Move a signal's readers with it:** blocks that named a default began posting as decisions, and the tool that
  re-briefed scope stops only read blocks, so every out-of-area fix parked for an afternoon.
- **Quiet with nothing open is finished, not stalled:** A run that had finished every stage was flagged as stuck.
- **Bring back only what someone still owns:** 28 held test runs, days old and ownerless, were resumed at once.
- **Routine success isn't news:** restart notices put three lines in the owner's inbox every ten minutes.

## 1.4.1 (2026-10-20)

**Patch: shorter skill.** It's read at every start, so it holds the 8 most instructive worked examples, and the
other 8 moved to skills/button-mash/references/EXAMPLES.md. No guidance changed.

## 1.4.0 (2026-10-20)

**Minor: four worked examples from the afternoon's stalls (the standing refinement pass), and method lessons 42-44.**

- **Measure first:** ten rounds of unmeasured speed fixes left a speed milestone unmoved.
- **Restate a goal the loop can't satisfy:** "watched by ear" was read as needing a person.
- **Production first:** a test run went past its default and onto the production card.
- **One agent per task:** two measuring runs competed for one box.

## 1.3.1 (2026-10-20)

**Credit and completion of the ambition moves (owner note #551).**

- **Credit:** the ambition moves come from [Felix Rieseberg's "How to be more ambitious: a tutorial for humans with models"](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/), which names speed, altitude, depth and range and credits Tom Kelley's
  nouns-into-verbs. Ken Huang stays credited for the "literal request" framing.
- **Added as short steering:**
  - speed;
  - the four-question depth check before building;
  - unreasonable goals treated as reasonable;
  - checking beliefs against the raw data;
  - an outside check the agent runs on the real output (it feeds the assessment loop, never a gate);
  - durable workflows that let the human leave the loop;
  - a crew of specialists from the activity's fields, including a red team.

## 1.3.0 (2026-10-20)

**Minor: the ambition protocol moves into the skill, with "turn nouns into verbs" and two worked examples (owner note
#549).**

- **Ambition protocol:** altitude (the goal beyond the goal), depth (what the field's best professionals do, and the
  tools they actually use), range (a method from another field). Until now it lived only in the method doc and in
  briefs from one generator. Builders launched straight through the agent launcher, most of them today, never got it.
  The skill is appended to every agent, so now all of them do.
- **Turn nouns into verbs** (Tom Kelley, *The Art of Innovation*): design for the activity, not the object. Not "a
  review page" but reviewing, comparing, answering, sharing.
- **Taught by:**
  - the Dev desk's review page, where depth means how professional review tools put the media first with the note
    beside it;
  - voice-conversion tests, where depth means how a dubbing studio compares input, target and output.

## 1.2.0 (2026-10-20)

**Minor: a new steering line and a worked example (owner notes #530-#531).**

- **Keep the owner's view live.** When work supersedes something waiting on the owner (a review item, a card, a
  decision), archive it at once, with one line on what replaced it. When a newer write-up replaces an older one, mark
  the older one as superseded.
- **Taught by:** 36 items from earlier days sat in the owner's "needs you" list, all already superseded, and had to be
  cleared by hand.

## 1.1.0 (2026-10-20)

**Minor: a new steering line and two worked examples (owner note #525).**

- **Mash, but spend where it counts.** Burn tokens where they move the goal: the hard problem, the live blocker, the
  decision that unlocks others. Elsewhere use the cheapest capable model, short briefs with context and one agent per
  task. No duplicate work, no re-deriving what's known, no re-running long reports, and stop loops that make no
  progress.
- **Taught by:**
  - a judge that re-issued work on one stale shot for six rounds, while builders spent half an hour each finding
    nothing new;
  - long research handed to the expensive model by habit instead of the cheap reader.
- **Links** to the existing cost guidance in STEERING.md and PRACTICES.md instead of repeating it.

## 1.0.0 (2026-10-20)

The first versioned release of the method (BUTTON_MASH_METHOD.md) and the skill (skills/button-mash/SKILL.md).

**What the method is:** keep many agents moving hyper-aggressively toward the goal behind the ask, with assessment
loops (look at the real output against the intent), not evals, tests or gates, and iterate fast toward discovering and
refining what we want.

**The hard guidelines, each with its why in the skill:**
- never destroy the owner's work (move instead of delete);
- never spend or publish without the owner's OK;
- never stop someone's live work;
- while working toward a goal, push hard and never leave a run stuck without saying why;
- pace deliberately for power and heat, cost and rate limits;
- no gates;
- nothing private in public material.

**What changed on the way to 1.0.0:**
- **The method page was renamed** from METHOD_AGGRESSIVE.md, which now points to it, and it opens with the owner's
  definition.
- **Lessons 31-41 were added:**
  - order rules as priorities, not waits;
  - one owner per resource, and never hold one resource while waiting for another;
  - leave memory to its owner;
  - an idle resource with waiting goal work is a bug for a watcher to correct;
  - no gates;
  - replay real histories before changing the scheduler;
  - root fixes reach the live run at once, and services restart onto new code;
  - account switches cover background services;
  - limiting defaults are visible settings;
  - inherit, don't invent;
  - tell stale from important by owner and progress.
- **The skill was first written as rules, then reshaped** (owner notes #521-#522) into hard guidelines with their why,
  strong steering, and judgment taught by worked examples. The incidents behind the examples:
  - a builder that named a safe default and stopped anyway;
  - a take waiting for a draft that was never coming;
  - a merged fix that the pinned live run wasn't running;
  - an 11-minute control-loop pass;
  - a cleanup that went by path alone and stopped a live builder's runner;
  - an owner decision that was re-asked every round;
  - a "busy box" block.
- **"Never leave the GPU idle" became "push hard while working toward a goal"** (owner note #523). Idle capacity
  matters only when goal work waits for it; with no goal, idle is fine.
- **Today's measured results:**
  - a replay of real run histories took GPU idle time with runnable work from 2.9 h to 0, and deadlocks to 0;
  - the control loop's pass went from 11 min to under a minute.
