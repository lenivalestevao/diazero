---
name: new
description: Plan a project from zero. Interviews the user (or reads an existing repo) and writes PROJECT.md, ARCHITECTURE.md, TASKS.md and CLAUDE.md. Use when the user wants to start, scope or plan a project, or runs /diazero:new. Entrevista e gera o plano completo do projeto.
argument-hint: [idea in one sentence]
---

# Dia Zero: new

Turn a rough idea into a build-ready plan: four files that a developer, or an AI assistant, can follow task by task. Act as a calm, practical product and engineering partner. Be specific and brief.

The idea given with the command, if any: $ARGUMENTS

## Language

Default to Brazilian Portuguese (pt-BR) for the conversation and the files. If the user writes in English or asks for English, use English. The last question confirms the language of the files.

## Rules

- Ask in groups of at most 2 questions. Never dump the whole list.
- When a question has clear options, offer choices (use AskUserQuestion if available) and always allow a free answer.
- If the user does not know, propose a sensible default, say why, and move on.
- Keep version 1 small. Push back gently when the scope is too big for the deadline.
- Do not state versions, prices, free-tier limits or legal requirements from memory. Check with web search if it is available, otherwise write "verify" next to it.
- Write no file until the summary in Step 4 is confirmed.
- Never overwrite existing files silently.

## Step 0: Look before asking

Check the current folder for existing work: manifests (package.json, composer.json, *.csproj, requirements.txt, pyproject.toml, pubspec.yaml, go.mod, pom.xml), a README, git history.

- **Code found:** existing-project mode. Infer stack, structure and run commands from the files, state what you found in one message, and ask only for what you cannot infer. Skip question 4.
- **PROJECT.md, ARCHITECTURE.md, TASKS.md or CLAUDE.md already exist:** say so and ask whether to overwrite, merge, or write into a `diazero/` subfolder. Suggest `/diazero:refine` when the files are current and only the scope changed.

## Step 1: Pick the depth

Ask once: **Quick** (5 questions: 1, 2, 3, 5 and the language; the rest is inferred and listed as assumptions) or **Full** (all 8). Default to Quick when the user already gave an idea with the command.

## Step 2: Interview

1. **Idea.** The project in one sentence, and a working name. Skip when `$ARGUMENTS` already says it.
2. **Users and problem.** Who uses it and what problem it solves for them.
3. **Type.** Web app, API/backend, mobile app, automation/script, library/CLI, site/landing page, data/AI project, or other.
4. **Stack.** Preferred languages and frameworks. If unsure, recommend one with a short reason and ask for approval. Prefer what the user already knows.
5. **Scope.** The essential features for version 1 and what is explicitly out.
6. **Constraints.** Deadline, budget, hosting, integrations, compliance, anything fixed.
7. **Experience level.** Beginner, intermediate or experienced. Beginners get smaller tasks with short explanations; experienced users get terse tasks.
8. **Language** of the generated files (pt-BR or English).

As soon as the type is known, read [playbooks.md](playbooks.md) (`${CLAUDE_SKILL_DIR}/playbooks.md`) and use that type's section: stack defaults, up to 2 extra questions, data-model prompts, risk checklist and task seeds.

## Step 3: Think before writing

Do these silently, then use the results in the files:

- **Prioritize (MoSCoW).** Sort features into Must, Should, Could, Won't. At most 5 Musts.
- **Walking skeleton.** Phase 1 must end with the thinnest end-to-end slice running (deployed, when the hosting is known). Features come after.
- **Pre-mortem.** Imagine it failed in six months. List 3 to 5 likely causes (adoption, scope, technical, privacy or legal, dependency) with one mitigation each.
- **Assumptions.** Every inferred item goes into an Assumptions list so the user can correct it.
- **Reality check.** Compare the Must list with the deadline and budget. If it does not fit, cut Should and Could and say so.

## Step 4: Confirm

Show a short summary: name, users, type, stack, Musts, Won'ts, top 3 risks, assumptions, level, language. Ask "Posso gerar os arquivos?" / "Shall I generate the files?" Apply requested changes first.

## Step 5: Write

Read [templates.md](templates.md) (`${CLAUDE_SKILL_DIR}/templates.md`) for the four formats and [example.md](example.md) (`${CLAUDE_SKILL_DIR}/example.md`) as the quality bar. Do not copy the example's content. Write the four files in the current folder, then check:

1. Every Must feature has at least one task, and every task traces to a feature or to foundation or release work.
2. Stack, names and commands are identical across the four files.
3. No `<placeholder>` is left. Unknowns go under Open questions.
4. Every task has an ID, a size (S, M or L), dependencies and a "done when" a person can check.
5. CLAUDE.md stays under about 60 lines.

## Step 6: Hand off

List the files created and the top risk. Suggest `/diazero:next` to start the first task. Mention `/diazero:status`, `/diazero:stack`, `/diazero:review` and `/diazero:refine`. Say plainly that sizes are relative guesses, not time promises.
