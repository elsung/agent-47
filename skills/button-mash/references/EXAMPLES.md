# Worked examples (button-mash)

Read on demand from skills/button-mash/SKILL.md. Each example is one real stall: what happened, and what a good move
looked like. The first section holds the examples added since 1.4.0; the second holds the older ones, moved here in 1.4.1.
## The week's examples (what happened, and what a good move looked like)

**The owner had to ask for ten things in one day.** Nobody was keeping the goal complete, so the owner did it by hand.
Good move: run a goal-gap pass every heartbeat. Compare the plan with what happened, give each unrun item a lead and a
next step, nudge a stalled row, and ask one question per approach: what would a top professional do next that nobody
asked for? (lesson 247)

**A six-check audit found gates added in a hurry under pressure.** Each one stopped work that a note could have carried.
Good move: turn each gate into a note or a default. A refused job notes why and waits for the next pass; a test run gets
one note and its lead stops it. (lesson 260)

**A builder's "tests pass" went into a report as progress.** The page it was meant to change had not changed. Good move:
report the real output, the page, the file or the run, and say what it showed. Experiments and A/Bs stay; coding tests and
test-before-land steps go. (lessons 246, 261)

**A builder wrote "Default: re-stamp the scratch copy" and then stopped to ask.** The default was safe and undoable.
Good move: take it, mark it "draft, owner may swap", and keep going. When the same stop kept coming back, we changed
the tool that posts blocks, so a block that names a default turns into a decision.

**A take waited "for the first draft," but nothing was ever going to make the draft.** The rule was written as a wait,
so it deadlocked when the thing it waited on couldn't start. Good move: rewrite it as a priority ("A goes first when it
can; otherwise B runs"), and when something waits, find out whether its precondition is actually coming.

**The live run stalled, and the fix was already merged, but the run was pinned to older code.** Good move: see the gap
between "fixed in main" and "running in the live work", put the fix into the live run at once, and retry the items
that failed.

**A cleanup stopped dozens of "orphaned" runners by their path alone, and one belonged to a live builder.** The path
said scratch; the owner said alive. Good move: check who owns a process and whether it's still making progress. If it
clearly isn't anyone's live work, stop it and say what it was. When unsure, flag it and leave it running.

**A judge kept issuing jobs on the same stale shot for six rounds, and builders ran half an hour each to report
nothing new.** That was spend with no motion. Good move: notice the repeat, name the false premise (the take it was
chasing didn't exist), redirect to work that moves the milestone, and record the finding where the judge reads it.

**The Dev desk needed a page for the owner to review test results.** The first idea was a list of files. Good move:
depth. Look at how professional review tools (Frame.io, ShotGrid, the review room in Resolve) do it: the media comes
first, big and playable, with the note and the decision right beside it, and A/B comparison one click away. Then turn
the noun into verbs: the owner is watching, comparing, deciding and replying, so the page serves those actions.

**Ten rounds merged speed fixes, and the speed milestone never moved.** None of the fixes had been measured end to
end, so every round named the same gap. Good move: measure first. One real run, timed, before any more fixes. A fix
nobody has measured is effort, not progress.

**A milestone said "watched by ear", and the judge read that as needing a person.** No round could ever meet it. Good
move: when a goal is worded so the loop can't satisfy it, restate it in terms the loop can check (frames,
transcripts, sound measures), take that as a default the owner may swap, and let the owner's own review come after,
not as a gate.

**We changed how blocks with a default were posted, and the tool that re-briefed scope stops stopped seeing
them.** For an afternoon, every builder that needed one file outside its area parked the fix. Good move: when you
change a signal, find everything that reads it and move them with it.

**Idle runners each held most of a CPU core, and the first two profiles found nothing.** Both used a cut-down copy
(no images, no pinned code), which removed the cost. A full copy run the way the live one runs showed 16 s of work
in every 2 s tick. Good move: when a measurement disagrees with what the live system shows, make the test more
like the live one before you trust it.

**An idle-GPU alert said hundreds of owner jobs were waiting, all evening.** They were two research copies nobody had
served for two days. Good move: a signal counts only what someone is waiting on (here, queues a live runner reads),
so an alert means a person or a run is actually stuck.

**An old run, its builder long gone, held a render card for an hour without progress while the current run waited
hours for that card.** Good move: what is it, whose is it, is it moving? Superseded, no owner, no progress: stop it,
say what it was, and the live run gets the card.

**Agents were pointed at the lab boxes so their checks stayed off the main card, and real runs kept landing there.**
Every run and runner an agent started inherited the pointer. Good move: fix it where the work starts. The run's
machine is decided there, the inherited pointer is dropped with a note, and the lab boxes stay for tests.

**A timed run's jobs never reached the card queue, so the priority rule that would have put them first never saw
them.** An admission cap upstream compared ranks across projects, which meant nothing. Good move: when a rule "can't
help", look for the gate in front of it, and give comparisons across boundaries a shared first key.

**A "restart onto new code" step, meant to keep runners current, restarted the owner's live roll.** Good move: the
same three questions apply to the system's own actions as to a person's (what is it, whose is it, is it moving?).
The routine action waits while the owner's live work runs, and says so once.

**A hold "until the episode's cut" kept back the world items the cut needed, so the episode deadlocked.** Good
move: before any hold or wait, name what releases it and check that the release does not depend on the held work;
when it does, hold only the later work instead.

**A builder had to time something on the main card, had no sanctioned way in, and posted straight to the renderer in
a loop while the guard stopped each try.** Good move: give the legitimate need a door (a wrapper that waits its turn
in the lock), say in every brief that it exists, and only then expect the fence to hold.

**New rules reached the judges' prompts but not the long-running loop that applied their answers, which had loaded
its code hours earlier.** Good move: when you change a rule, check every process that runs it, and make long-lived
ones reload on change.

**The owner noticed the run stayed sharp for two days through many context summaries, with no hand-off notes.** What
did it: the status board and review desk were watched closely, the research docs and the pipeline spec were the
sources of truth and were kept current, and old documents were archived with an index instead of left to rot. Good
move: keep the living sources fresh on every heartbeat (fix the safe drift, flag the rest), archive rather than
delete, and when you arrive or wake from a summary, read those sources before acting.

**A box was held for an install; the router that spreads work skipped it, but a run pinned to that box by name sent
its jobs straight there, and they failed.** Good move: a rule about where work may run lives where every job is
claimed, matches every name the place goes by, and leaves the job waiting with the reason, never running.

**A person's hold was found off, and later work it was there to stop had run.** No one had cleared it: a 20-minute
default expiry had. Good move: find the real cause before guessing (the decision log said "expired"), size the
default to how people use it, and log every change with who or what made it.

**The orchestrator asked three times to stop "waits failing", and the same two items failed after every requeue.**
Their reason field named a content check; the "waiting" text was only the last progress line. Good move: read the
record before building the fix, say plainly what it shows, and show the real cause where people look.

**The idle fast machine never got work, though everything was listed and the window was open.** Three causes in turn:
each workspace counted only its own jobs at a shared card, the choice of card was made once and never revisited, and
an older rule moved the work away again after a restart. Good move: fix each at its source, move the waiting work by
hand meanwhile, and check the machine is actually busy before calling it done.

**A window closed and the workers it allowed kept running; the card it was meant to free sat full.** The checks that
should have acted had been written and reported hours earlier, but the watchdog process was still running the code it
started with. Good move: compare the process start with the code's last change, restart it, make it reload itself,
then watch each new check act once (one of them still had a wrong match), and say plainly that the earlier "done" lines
were not true in the running service.

**A production cut failed with "no readable answer", and the first guesses were the tool updating itself or a huge
input.** The timing record showed two starts of the same job and two ends, minutes apart: a requeue while it ran had
started a twin, and the twin emptied the file the first then read. Under it sat a real bug, a name meaning two things.
Good move: read the run's own timeline before choosing among guesses, fix each cause where it is decided (one process
per job; one name per thing), and tell the owner what the live job will still do on the old code.

**The same card stalled four times in two hours, and each clear by hand held only until the next old job reached the
head.** The fix for it had landed, but every waiter on that card ran older code that never read it. Good move: stop
clearing instances, find what every version already reads (each entry's stored rank and time), move a stuck head
there, run the rule once a minute from current code for cards with no new waiter, and check the next stall clears on
its own (it did: "moved to the back of the queue").

**The machine's fans were loud with the GPU idle: dozens of idle workers each used a third of a core.** A profile of
one idle tick showed most of it re-parsing configuration files that had not changed. Good move: profile before
guessing, fix the hot step at its source (parse only on change), make the loop sleep while nothing changes and exit
when nothing is open, measure the result on the real thing (0.25 % CPU idle), and stop the idle workers already
running on old code so the relief is felt now, not at their next restart.

**A disk-saving change was proven safe and landed, and three of the production roll's cast pictures turned into one
line of text.** Copies linked the original's files; the proof hashed the original around a real run of the engine,
but a builder's own command in a copy wrote through a link. Good move: own it at once, restore the originals from a
known-good copy, check nothing else was hit, revert the sharing, replace the links already out there, and tell the
orchestrator what may have read the broken files.

**A live roll's card stalled three times in an afternoon, a different way each time, each after a fix for the last.**
A lock held by a waiter, then a holder that was not the waiter, then no holder at all with five versions disagreeing
on who was next. Good move: for each, read the queue's own record to see what the breaker saw, make the breaker key on
the outside symptom (free card, waiters, nothing taken), check every running version would agree with the fix, land it
where it reaches the live roll without a restart, and watch it act once on the real card.

**A no-redo switch for a live roll stopped the roll twice in its first hour.** First it skipped items whose outputs
grew after their job ran, then everything waited for an upstream step it would never remake. Good move: read the
run's own notes and queue to find what was skipped and why, fix where "made" and "ready" are decided (not where the
job is queued), dry-run the exact commit on the live state read only, name the items it now makes, and when the
applied fix differs from yours, dry-run that one too and say what it still misses.

**A repository of code had become gigabytes of evidence, and every worktree paid for it.** Agents committed
their screenshots and clips beside their notes, nothing refused them, and each new worktree, land copy and release
copied over a gigabyte. Good move: measure what is tracked (by type and folder, not by guess), ignore media at the
source with an allow-list for what the code itself serves, move evidence to the data drive automatically when work
lands (a link at the same path, so notes still open), add a size check to the doctor, and only then rewrite the
history once. Keep a mirror as an object alternate, so old pins still resolve and nothing running breaks.

**Two production runs in one day each hit causes the run before had already met.** Their write-ups were shared docs
outside the repository, so the next run's prep never read them. Good move: give every run a retrospective in the
repository as plain text, with:
- the result, where the time went, and right and wrong with each cause and its fix;
- a pre-flight checklist and a regression table;
- a link back to the previous run's retrospective, and a row in a rolling index.

Update it as fixes land. Tick the checklist and check the table before the next run starts.

**A creative pipeline grew dozens of narrow rules, each fixing one symptom, and its outputs got more correct and no
more moving.** The owner restated the point: the work exists to make an audience feel something and care. Good move:
write that into the one north star file every stage reads first, make each stage say how its output serves it, judge
results by it before the spec, and treat the narrow rules as hypotheses to keep or retire, not as the goal.

**A week of agent work burned about 5.7 billion tokens on a hosted reading model, and the quota ran out mid-run.**
Good move: move each kind of work to the cheapest thing that does it well, and measure on the real job:
- a decision model in front of the LLM for typed questions (571 research ideas sorted in 2.3 s for under 4 cents);
- a bake-off of local models on two real reads, against the hosted model's reads. The pick was the one that caught
  every idea, not the fastest;
- the hosted model kept, rationed, for what local can't do.

When the local box is another team's live machine, ask its orchestrator for a lane and a memory budget first, run one
model, and write down whose it is and how to stop it.

**A speed test showed every arm 37% faster than the control.** The control ran right after a model swap and paid the
reload. Good move: time each stage (load, encode, sample, decode), add a warm control, and judge each change on the
stage it touches before calling a speed-up.

## More worked examples

What happened, and what a good move looked like. The skill keeps the most instructive ones; these are the rest.

**The control loop took 11 minutes per pass, and work queued behind it.** No one had timed it. Good move: time the
loop's own steps, find the slow one (it was doing slow work inline and reading a busy disk), and move that work off the
loop. Then watch whether the fix held. The first fix didn't fully; the second did.

**The owner's "needs you" list held 36 items from earlier days, all already superseded.** The owner had to sort
through them to find the one live decision. Good move: whoever supersedes an item archives it at once, with a note on
what replaced it (it can be reopened), so the list stays true without a cleanup day.

**The same owner question was asked every round** (music for a show that has none on purpose). Good move: put the
owner's decision where the loop reads it every round, so the loop stops re-asking.

**Long research went to the expensive model by habit.** Good move: give reading and summarising to the cheapest
capable reader, with the output file named, and keep the expensive model for the decision the research feeds. When
the cheap reader failed on its provider's limit, fall back to another cheap model, not to the expensive one.

**Voice tests compared converted voices.** Good move: depth. A dubbing studio always lays out three things side by
side: the input performance, the target voice and the output. It listens for timing and emotion, not only timbre. A
test page laid out that way answers the owner's question in one listen.

**A test run claimed the shared card while the live production run waited.** Its builder had pointed it at that card
by hand, past the default that sends test work elsewhere. Good move: production goes first. Move or pause the test
run, then close the gap that let it through, so the next one is caught at once.

**Two measuring runs from one mission competed for one box.** Good move: one agent per task. The second reads the
first one's numbers instead of starting its own.

**A builder blocked because "the box is busy."** Busy is a queue, not a wall. Good move: submit to the shortest queue,
do the other work meanwhile, and collect the result.

**The watchdog called the live run stalled because nothing had been written for 15 minutes.** The run had
finished every stage; its status just hadn't been updated. Good move: before calling something stuck, ask
whether anything is still open. Quiet with work waiting is a stall. Quiet with nothing open is finished.

**After production finished, the watchdog brought back 28 held test runs at once, from experiments days old
whose builders were long gone.** Good move: bring back only what someone still owns and is working. The rest
stays put, and gets one line, not 28.

**Every routine restart onto new code posted a line to the owner's inbox: three lines every ten minutes.** Good
move: routine success goes to the log. The inbox is for what changes what someone does: a failure, a decision,
a milestone.

**A job failed four times with the same error, and each failure got a fresh automatic retry.** The error was in
the code the run was pinned to, and the fix was already in main. Good move: a failure that repeats its last reason
is the code or the input, not luck. Stop retrying, find where it is already fixed or fix it, then move the work
onto that.

**The fence hid the GPU from agents' CUDA, and a 3D preview still reached the card through its graphics driver.**
Good move: a fence protects a resource, not one door to it. When something gets through, close the path it used,
and check whether other paths lead to the same place.

**A self-heal relaunched a builder that had quit, into a worktree where its lead had already started another.** Two
builders then edited the same files. Good move: before an automatic restart, check whether someone already took
the work over.

**Idle processes read their whole history again every two seconds.** One had read nearly two terabytes since it
started, and together they slowed everything sharing the machine. Good move: measure what idle costs. Waste that
looks like work is still waste, and it taxes all the real work beside it.

**A cheap judge ran its own search across hundreds of folders on a slow disk to find the newest outputs.** Good move:
hand a cheap agent the answer it would otherwise search for. Put the facts it needs in its evidence, and say what
not to do and why.

**Two cleanup tools touched the same worktree at once.** A mover had a worktree in flight; a pruner saw it missing
and told git to forget it. Good move: re-attach it without losing its uncommitted edits, then give both tools one
shared lock, so the race can't happen again.

**The owner wanted old worktrees gone but deletes are theirs.** Good move: move them into one folder on the same
disk (instant), write an index with sizes and one delete command to copy, and post a weekly reminder. The agent does
everything except the irreversible step.
