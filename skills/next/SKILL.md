---
name: next
description: Do the next task from TASKS.md. Picks the first unchecked task whose dependencies are done, implements it in small steps, runs the project's checks, verifies its "done when", and marks it done. Use when the user wants to build the next piece of the plan, or runs /diazero:next. Executa a próxima tarefa do plano.
argument-hint: [task id] [--phase N] [--count N] [--dry-run] [--tdd] [--commit] [--no-checks]
disable-model-invocation: true
---

# Dia Zero: next

Build one task from the plan, properly, then stop. The plan is the contract: do what the task says, nothing more.

Task requested with the command, if any: $ARGUMENTS

## Options

Flags may appear in `$ARGUMENTS` before or after the free text. Unknown flags: say so and ignore them. A flag always beats the default and the interview.

| Flag | Effect |
|---|---|
| `--phase N` | Work through the unchecked tasks of phase N, one at a time, stopping at the first failure or open decision. |
| `--count N` | Do up to N tasks in a row, same stop rules. |
| `--dry-run` | Do steps 1 to 3 only: pick the task and restate it, change nothing. |
| `--tdd` | Write the failing test from the "done when" first, then the code. |
| `--commit` | After a task passes its checks, make one commit per task with the task ID in the message. |
| `--no-checks` | Skip the test, lint and build commands. Say that the result is unchecked. |

## Language

Use the language of the plan files. Default to Brazilian Portuguese.

## Steps

1. **Load the plan.** Read CLAUDE.md, TASKS.md and ARCHITECTURE.md. If TASKS.md is missing, say so and suggest `/diazero:new`.
2. **Pick the task.** Use `$ARGUMENTS` when it names a task ID. Otherwise take the first unchecked task whose dependencies are all checked. If none qualifies, explain what blocks the next ones.
3. **Restate it** in 3 lines: what you will build, which files you expect to touch, and how you will know it is done. If the "done when" is vague or the task is bigger than L, stop and propose splitting it. Do not guess.
4. **Implement** in small steps, following the conventions in CLAUDE.md and the structure in ARCHITECTURE.md. Do not add features, refactor unrelated code or change the stack.
5. **Check.** Run the test, lint and build commands from CLAUDE.md. If they are TBD, say so and verify the "done when" another way you can name. Fix failures that you caused. Report failures that you did not cause, without hiding them.
6. **Verify the "done when"** against the real result, not against your intention. Say plainly what you checked.
7. **Update the plan.** Mark the task `[x]` and add a one-line note under it (what was done, anything notable). If you found work the plan missed, add it as a new unchecked task and tell the user. Do not edit other tasks.
8. **Close.** Summarize in a few lines, then name the next task. Do not commit unless the user asks.

## Stop and ask when

- the task needs a decision that is not in the plan;
- the scope turns out larger than the task says: stop and suggest `/diazero:refine`;
- a check fails for a reason you cannot fix within the task.

Never mark a task done when its checks fail or its "done when" is not met. Say what is left.
