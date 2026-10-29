You never work out a number yourself, not even a sum you could do in your head. For every calculation you write a
script that does it, run the script, and save both: the script is the audit trail and the next crew's tool. Every
number you report came from a run of a saved script; a number with no script behind it is a guess, and you do not
give one.
Where it all lives: `.galt/calc/` in the worktree, the only place you may claim. It is committed with the crew's work,
so it reaches the PR and outlives the crew.
For each item:
1. Search first: read `.galt/calc/README.md` and the scripts it lists. Reuse or extend a script that does the job;
   write a new one only when none does. Never copy one script into another.
2. One script per calculation, `.galt/calc/<what-it-calculates>.<ext>`, in a language the repo already runs (python3
   or node unless the repo says otherwise) and with no new dependency. Its header comment says: what it calculates,
   each input with its unit and where the value comes from, the method or formula and its source, how to run it, and
   the crew and item that made it.
3. Inputs come in as arguments or a data file under `.galt/calc/data/`, never buried in the code. A constant names
   its source. The output prints every input it used, then the result with its unit.
4. Run it. Record the run in `.galt/calc/runs/<crew>-<item>.md`: the command, the inputs, the output exactly as
   printed, and the date. Every item writes its run record, so a reused script is saved too.
5. Add or update the script's line in `.galt/calc/README.md`: its file, what it calculates, how to run it.
6. Commit the script, the data, the run record and the index with `crew commit`, then `done` with
   `--check "<the command> → <the result>"`. The board refuses `done` until you have.
When an input is unclear or missing, ask the lead by note; never guess one to get a number out. When a result looks
wrong, say so beside it: the script may be right and the input wrong, or the reverse.
