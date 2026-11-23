---
name: doctor
description: Check that the four plan files are well formed and consistent before building. Validates task IDs, sizes, dependencies, "done when", placeholders, the Must-to-task trace and the length of CLAUDE.md. Read-only. Use before the first task or after hand-editing the plan, or runs /diazero:doctor. Valida os arquivos do plano.
argument-hint: [--fix-list] [--strict]
allowed-tools: Read Grep Glob
---

# Dia Zero: doctor

A quick health check of the plan files. Read only; change nothing.

Arguments given with the command, if any: $ARGUMENTS

## Options

| Flag | Effect |
|---|---|
| `--fix-list` | End with the exact edits that would fix each problem, one line each. |
| `--strict` | Treat warnings as errors and end with PASS or FAIL. |

## Language

Use the language of the plan files. Default to Brazilian Portuguese.

## Checks

Report each as OK, WARN or ERROR, with the file and line when there is one.

1. **Files.** PROJECT.md, ARCHITECTURE.md, TASKS.md and CLAUDE.md exist. Missing is ERROR.
2. **Placeholders.** No leftover `<...>`, `TODO` or `TBD` outside an "Open questions" section. WARN.
3. **Task format.** Every task has an ID, a size (S, M or L), dependencies and a "done when". ERROR when one is missing. WARN when a "done when" is vague ("works", "is done") or a task is larger than L.
4. **Unique IDs.** No duplicates. Dependencies point to IDs that exist and never to a later phase. ERROR otherwise.
5. **Walking skeleton.** Phase 1 ends with something running end to end. WARN if not.
6. **Trace.** Every Must feature has a task. Tasks that serve no feature, foundation or release work are WARN.
7. **Scope.** At most 5 Musts. No Won't item appears in TASKS.md.
8. **Consistency.** Stack, project name and the run, test and build commands match across the four files. ERROR on a mismatch.
9. **CLAUDE.md.** Under about 60 lines, with real commands or an explicit TBD.

## Report

One line per check, a total of errors and warnings, and one suggestion: `/diazero:refine` for plan problems, `/diazero:next` when all is OK. Say "I could not verify" for anything you could not check.
