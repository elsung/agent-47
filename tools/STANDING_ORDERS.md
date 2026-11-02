# Standing orders (pasted verbatim into every worker brief by make_brief.py)

One constraint per line, each with its reason. Edit these for your project. When you catch yourself restating an
instruction to a worker, append the line here before you act. Reasons matter: a worker that knows why makes better calls.

1. Work only in the worktree path you were given. Never create worktrees; never edit the live checkout. (Relative paths landed worktrees inside the live repo.)
2. Never delete files; move them to `_trash/`. (Owner's rule.)
3. Kill only processes you started, by PID. Never `pkill -f` or `killall`. (Other work shares the machine.)
4. Never change or remove an existing API field, file format or function signature; only add. (Other screens depend on them.)
5. Never delete or weaken a test or a check, and never split strings to get past one. If a check is wrong, say so under DECIDE.
6. Write only inside the SCOPE paths in your brief; anything else goes under DECIDE. (check_report.py fails files outside scope.)
7. Run the full suite yourself before reporting and paste its summary line. "Running" is not a result.
8. Any screen you change: load it in a headless browser on real data, zero page and console errors, screenshots you have looked at under `_shots/`.
9. Never invent a file path or data layout; read the code that writes the data and test on real data, read-only.
10. If you run short on room, commit each finished deliverable and continue; never end with parts "deferred". The same failure twice after real attempts: stop and report BLOCKED with what you tried.
11. Write REPORT.json before replying. Silence or a prose-only reply counts as not done.
12. Honour the contracts in docstrings and comments of code you call (e.g. "only from the main thread"); if one blocks you, say so under DECIDE. (A worker broke one and its fake-context tests hid it.)
13. Code never deletes either: no rmtree or unlink in product code unless the brief allows it; move aside instead.
14. Any new config key or setting: add a test that sets it and checks the code's behaviour changes. A key nothing reads is a silent failure.
15. When adding an optional mode, prove the default path is unchanged by comparing against main's exact behaviour in a test, never by assertion. A failed sub-step must change the output visibly (fall back, and record it). Never skip it silently.
16. Tests write only under a temporary folder (monkeypatch any root paths); never relative paths into the repo. Never call a failure "pre-existing" without running the same test on main. Never fill a required field with invented or placeholder content.
17. Commit each deliverable as soon as its tests pass, so an interruption loses little.
18. Any new config key or setting: add a test that sets it and checks the code's behaviour changes. A key nothing reads is a silent failure.
19. When adding an optional mode, prove the default path is unchanged by comparing against main's exact behaviour in a test, never by assertion. A failed sub-step must change the output visibly (fall back, and record it). Never skip it silently.
20. Tests write only under a temporary folder (pytest tmp_path or equivalent); never relative paths into the repo. Never call a failure "pre-existing" without running the same test on main. Never fill a required field with invented or placeholder content.
21. A code graph tool may be available for your codebase (`explain "<function>"` or `path "A" "B"`). Use it for "what is X / who calls X", then confirm with grep before relying on it. Use grep for broad "find all" searches.
22. When you write instructions for the team (guides, references, prompts), write craft as guidance with its reason ("usually…, because…; depart when the work calls for it, and say why"). Never use absolutes ("always", "never", "must", fixed counts or quotas) for creative choices. Hard rules make systems brittle and hurt the work. Absolutes are only for safety and data integrity (no deletion, no invented facts).
23. To wait for a process, wait on its PID (`while kill -0 <pid>; do sleep 20; done`) or on a done-file. Never `pgrep -f "<pattern>"`: it matches your own waiter's command line and never ends.
24. Your work lives on a shared board as tracked items: update a card whenever work starts, moves between columns, blocks or finishes. Everything you write to the orchestrator follows a shared style guide: answer first, one point per line, exact status words, one labelled ask.
25. Never use `git stash`; set work aside with a WIP commit. (The stash stack is shared by every worktree; a pop can apply another worker's changes.)

31. **Never block your own turn waiting.** Wait for a handover, a run or a review with a background watcher, and end the turn. (A lead sat 56 minutes in one waiting turn and missed two orchestrator messages queued behind it.)
32. **Save work off the machine.** When a worker finishes or stops, commit its work to its branch (a WIP commit if unfinished; never git stash) and push the branch. (Work that exists only on one machine is lost with it.)
33. **A finished result is reported within 5 minutes.** When a timed run, test or render finishes, post the result to the inbox straight away, even if more work follows. (A three-episode run finished and went unreported while the owner waited on it.)
34. **No test gates.** Land with a clean merge and a check that the code starts; run no suite before or after. Fix forward. (A full suite hung builders for hours on tests that were already failing on main.)
35. **Areas, not overlaps.** Write only inside the areas your brief gives you. A file you need outside them goes on a decision list; do not edit it. (Land conflicts were all in shared hub files.)
36. **Gate met means go.** When the thing you were waiting for has happened (a merge, a run stage, a decision posted in the inbox), act on it at once. Never sit idle with work available. (An idle lead with queued work sat unused.)
37. **Stop processes only by PID through the safe-stop script.** Never kill a parent process without reading what it is first. (A parent signalled by mistake took down the whole session: the desktop login, the terminal sessions, every agent and every runner.)
38. **Ambition is a protocol, not a mood.** Before building, write at the top of your change note: ALTITUDE (the goal beyond the goal and the biggest version of the job that fits), DEPTH (what the field's best expert would do that a literal reading skips) and RANGE (one method borrowed from another field). Then deliver the ambitious version. Doing exactly the literal words and stopping is the failure.
39. **Agents never make or start runs in the production root.** Work in a scratch root or on a spare machine. (A mission run in the production root left the live shoot unqueued and the GPU idle for about an hour.)
40. **A merge that touches the web app restarts the dashboard.** The merge step restarts the dashboard service after it, and the result goes in the inbox; a failed restart says so. (A merge once left the dashboard serving old code until a manual restart.)
