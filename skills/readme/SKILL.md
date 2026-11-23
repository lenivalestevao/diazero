---
name: readme
description: Generate a README.md for the user's project from its plan files and code. Covers what it is, features, stack, how to run it, roadmap and license. Use when the user wants a README or a public project page, or runs /diazero:readme. Gera o README do projeto.
argument-hint: [--lang pt|en] [--bilingual] [--short] [--badges] [--license NAME]
---

# Dia Zero: readme

Write the README that a stranger needs to understand, run and trust the project. It should be accurate to the code, not to the dream.

Arguments given with the command, if any: $ARGUMENTS

## Options

Flags may appear in `$ARGUMENTS` before or after the free text. Unknown flags: say so and ignore them. A flag always beats the default.

| Flag | Effect |
|---|---|
| `--lang pt\|en` | Language of the README. A bare `pt-BR` or `en` still works. |
| `--bilingual` | Both languages in one file, pt-BR first. |
| `--short` | Name, description, getting started and license only. |
| `--badges` | Add badges, only those that point at things that exist (license file, CI workflow). |
| `--license NAME` | Use this license instead of asking. |

## Steps

1. **Read** PROJECT.md, ARCHITECTURE.md, TASKS.md and CLAUDE.md, plus the manifests and top-level folders of the code. Prefer what the code does over what the plan says, and note the difference when they disagree.
2. **Pick the language.** Use `$ARGUMENTS` when given, otherwise the language of the plan files (default pt-BR). Offer a bilingual README when the project is public.
3. **Check the commands.** Every install, run and test command in the README must come from CLAUDE.md or the manifests. Run the quick ones when it is safe. Never write a command you did not verify; mark it "verify" instead.
4. **Write** these sections, short and in this order:
   - name and one-line description;
   - what it does and who it is for;
   - features (only those that exist now, with planned ones under Roadmap);
   - stack;
   - getting started (requirements, install, run, test);
   - project structure (a few lines);
   - roadmap, built from unchecked tasks and Could items;
   - contributing, in two lines;
   - license.
5. **Leave out** screenshots and claims you cannot back, and badges unless `--badges` is given. Add a short "Screenshots" placeholder note only if the user wants one.
6. **License.** Ask which license to use if the project has none. Do not choose for the user.
7. **If README.md exists,** show a short summary of the changes and ask before overwriting.

Finish with the list of things only the user can fill in, such as screenshots, a demo link or contact details.
