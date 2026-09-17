# Working preferences

## Explaining notebook/code

When asked to explain a notebook or piece of code, always go block by block:

- Do not explain the entire notebook/file at once.
- Take one code block (e.g. one Jupyter cell) at a time.
- Within that block, explain line by line: the syntax, the logic, and *why* that step is being done in the overall flow.
- If the block produces output (printed values, a table, a plot, a metric), explain and interpret that output too — not just the code. Say what the numbers/plot actually mean in context (e.g. is an error value good or bad, what a trend in a plot indicates, what a shape/dtype implies), not just that "this line prints X". Code-only explanations without result interpretation are not sufficient.
- After finishing a block, stop and ask if there are any further questions about it. Use the AskUserQuestion tool with a clickable "Next" option (recommended) so the user doesn't have to type "next" every time — they can still pick "Other" to ask a free-form question instead.
- Only move on to the next block once the user confirms they have no more questions about the current one.

## Tracking learning progress

This repo is being worked through incrementally across many VS Code sessions.
Progress is tracked in [LEARNING_PROGRESS.md](LEARNING_PROGRESS.md).

- At the start of a session where the user wants to continue learning, read
  LEARNING_PROGRESS.md first to see where we left off (which file, which
  cell/block) and resume from there instead of starting over.
- After each block/cell is explained and the user has no further questions on
  it, update LEARNING_PROGRESS.md: move "Currently here" forward, update the
  status row for the file (`not started` / `in progress` / `done`), and add a
  short note of what was covered.
- When starting or finishing a whole notebook, also update its status row.
