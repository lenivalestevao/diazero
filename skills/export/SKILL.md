---
name: export
description: Export the task plan from TASKS.md to GitHub issues, a CSV file or a Markdown checklist, so it can be used in a tracker or shared. Use when the user wants the plan in GitHub, a spreadsheet or another tool, or runs /diazero:export. Exporta o plano de tarefas.
argument-hint: [--to issues|csv|checklist] [--phase N] [--out FILE] [--dry-run]
disable-model-invocation: true
allowed-tools: Read Grep Glob Write Bash(gh issue *) Bash(gh label *) Bash(gh repo view *)
---

# Dia Zero: export

Move the plan out of TASKS.md without changing it. TASKS.md stays the source of truth.

Arguments given with the command, if any: $ARGUMENTS

## Options

| Flag | Effect |
|---|---|
| `--to issues` | Create one GitHub issue per task with the `gh` CLI. |
| `--to csv` | Write `tasks.csv`: id, phase, title, size, depends_on, done_when, status. |
| `--to checklist` | Write a Markdown checklist grouped by phase, ready to paste anywhere. |
| `--phase N` | Export only phase N. |
| `--out FILE` | Output file for csv and checklist. Never overwrite an existing file without asking. |
| `--dry-run` | Show what would be created, create nothing. |

Without `--to`, ask which format, with CSV as the default.

## Language

Use the language of the plan files. Default to Brazilian Portuguese.

## Steps

1. **Read** TASKS.md. If it is missing, say so and suggest `/diazero:new`. Parse every task: ID, title, size, dependencies, "done when", checked or not.
2. **Skip finished tasks** unless the user asks for all. Say how many were skipped.
3. **Show the preview**: the number of items and the first three. For `issues`, also show the repository (`gh repo view`) and ask for confirmation, because issues are visible to others and cannot be undone in bulk.
4. **Write.** Issues: title `T1.2 <title>`, body with the "done when", the size and the dependencies, and labels `diazero`, `phase-N`, `size-S|M|L`. Create missing labels first. Do not assign people or milestones.
5. **Report** what was created, with the file path or the issue numbers, and anything that failed.

## Rules

- Never edit TASKS.md here.
- If `gh` is missing or not signed in, say so and offer the CSV instead.
- Do not export to a repository the user did not confirm.
