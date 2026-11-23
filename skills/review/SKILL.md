---
name: review
description: Audit the codebase against the plan. Finds scope creep, missing Must features, tasks marked done without evidence, drift from ARCHITECTURE.md and basic hygiene problems, with file paths as evidence. Read-only. Use before a release or after finishing a phase, or runs /diazero:review. Audita o código contra o plano.
allowed-tools: Read Grep Glob Bash(git log *) Bash(git status *) Bash(git ls-files *)
---

# Dia Zero: review

Check what was built against what was planned. Read only; change nothing.

## Language

Use the language of the plan files. Default to Brazilian Portuguese.

## Steps

1. **Load the plan.** Read PROJECT.md, ARCHITECTURE.md, TASKS.md and CLAUDE.md. If they are missing, say so and suggest `/diazero:new`.
2. **Delegate the audit** to the `diazero:scope-guardian` subagent with the Agent tool, giving it the folder to audit. If the subagent is not available, run the checks below yourself.
3. **Present the findings** as a table: severity (high, medium, low), finding, evidence (file paths, task IDs), suggested fix. Sort by severity. Drop anything you cannot back with evidence.
4. **Offer next steps:** `/diazero:refine` when the plan should change, `/diazero:next` when a task should be redone. Do not fix anything yourself.

## The checks

1. **Scope creep.** Code, routes, screens or dependencies that serve a Won't item or no planned feature.
2. **Missing Musts.** Must features with no implementation or no tests.
3. **False done.** Tasks marked `[x]` without matching files, tests or commits.
4. **Architecture drift.** Folder structure, data model, stack or libraries that differ from ARCHITECTURE.md.
5. **Hygiene.** Secrets or `.env` files committed, missing `.gitignore`, no tests for the core flow, commands in CLAUDE.md that do not work.
6. **Documentation.** README or CLAUDE.md out of date with the code.

Report what you checked and what you could not check. An empty result with a short list of checks run is a valid answer.
