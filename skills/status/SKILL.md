---
name: status
description: Report where the project stands against its plan. Counts tasks per phase, shows what is next, what is blocked, and where the code and the plan disagree. Read-only. Use when the user asks for progress or "where are we", or runs /diazero:status. Mostra o progresso do projeto.
allowed-tools: Read Grep Glob Bash(git log *) Bash(git status *)
---

# Dia Zero: status

Give an honest, compact picture of progress. Read only; change nothing.

## Language

Use the language of the plan files. Default to Brazilian Portuguese.

## Steps

1. **Read** TASKS.md, PROJECT.md and CLAUDE.md. If TASKS.md is missing, say so and suggest `/diazero:new`.
2. **Count, do not estimate.** Count checked and unchecked tasks per phase with Grep on `- [x]` and `- [ ]`. Report the real numbers. Weight by size only if you say so.
3. **Look at the repo.** Run `git log --oneline -15` and `git status --short` if the folder is a git repository. Say when it is not.
4. **Find drift.** Flag, with evidence:
   - tasks marked done that have no matching files, tests or commits;
   - recent commits that match no task;
   - code or folders that belong to a Won't item or to no planned feature;
   - Must features still without any started task.
5. **Report** in this shape:
   - **Progress:** one line per phase, with done/total and a short bar.
   - **Next up:** the next 3 unchecked tasks whose dependencies are done.
   - **Blocked or at risk:** with the reason.
   - **Drift:** the flags from step 4, each with its evidence, or "none found".
   - **Suggestion:** one concrete next action (`/diazero:next`, `/diazero:refine`, or `/diazero:review`).

## Rules

- Say "I could not verify" instead of guessing.
- Keep the whole report to about 25 lines.
