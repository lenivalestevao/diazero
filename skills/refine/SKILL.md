---
name: refine
description: Revise the plan when scope, stack or deadline changes. Checks PROJECT.md, ARCHITECTURE.md, TASKS.md and CLAUDE.md for consistency, shows the impact of the change, and updates them. Use when the user wants to add, cut or re-plan something, or runs /diazero:refine. Revisa e atualiza o plano.
argument-hint: [what changed] [--add TEXT] [--cut TEXT] [--stack TEXT] [--deadline TEXT] [--dry-run]
---

# Dia Zero: refine

Keep the four plan files consistent with each other and with reality. Change as little as possible, and show the impact before changing anything.

What changed, as given with the command, if anything: $ARGUMENTS

## Options

Flags may appear in `$ARGUMENTS` before or after the free text. Unknown flags: say so and ignore them. A flag always beats the default and the interview.

| Flag | Effect |
|---|---|
| `--add TEXT` | A feature to add. |
| `--cut TEXT` | A feature or task to remove or move to Won't. |
| `--stack TEXT` | A stack change. |
| `--deadline TEXT` | A new deadline. |
| `--dry-run` | Show the impact and the proposed edits (steps 1 to 5), change nothing. |

Without a flag, treat the free text as the change, as before.

## Language

Use the language the existing files are written in. If the user writes in another language, answer in theirs and keep the files as they are unless asked.

## Steps

1. **Read** PROJECT.md, ARCHITECTURE.md, TASKS.md and CLAUDE.md in the current folder. If none exist, say so and suggest `/diazero:new`.
2. **Find out what changed.** If `$ARGUMENTS` is empty, ask one short question: new feature, removed feature, different stack, shifted deadline, or "just review it".
3. **Measure the impact.** For the change, list:
   - which Must, Should or Could entries move;
   - which tasks are added, removed, resized or re-ordered, and which dependencies break;
   - which decisions in ARCHITECTURE.md are affected;
   - the effect on the deadline, in relative terms (sizes are guesses, not promises).
4. **Check consistency.** Look for:
   - features with no task, and tasks that serve no feature;
   - stack or data-model details that disagree across files, or with CLAUDE.md;
   - Won't items that crept into TASKS.md;
   - finished work that is not checked, and checked work with no evidence in the repo.
5. **Propose** the changes as a short list: file, what changes, why. If the change makes version 1 much bigger, say so and suggest moving something to a later phase. Ask for confirmation.
6. **Apply** only the confirmed changes, with minimal edits and keeping the user's own wording.
7. **Record** a dated line in the Change log of PROJECT.md. When a decision changed, update the Decisions table in ARCHITECTURE.md too.
8. **Report** in a few lines what changed and which open questions remain.

## Rules

- Never delete the user's content without confirming.
- Never mark a task done on your own here. That is `/diazero:next`.
- Keep completed tasks in TASKS.md. Add new tasks after them.
