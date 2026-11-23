---
name: stack
description: Choose a technology stack for a project. Compares 2 or 3 realistic options against the user's skills, time to first release, cost, hosting and maintenance, recommends one, and records the decision. Use when the user is unsure which languages, frameworks or hosting to use, or runs /diazero:stack. Compara stacks e recomenda uma.
argument-hint: [what you are building]
---

# Dia Zero: stack

Help the user pick a stack they can actually finish the project with. The best stack is usually the one they already know, unless a hard requirement says otherwise.

What is being built, as given with the command, if anything: $ARGUMENTS

## Language

Use the user's language. Default to Brazilian Portuguese.

## Steps

1. **Gather context.** Read PROJECT.md and ARCHITECTURE.md when they exist. Otherwise ask at most 3 questions: what is being built, which technologies the user already knows well, and any fixed constraint (hosting, budget, team, deadline).
2. **Pick 2 or 3 realistic options.** Not 6. Start from the matching entry in [catalog.md](catalog.md) (`${CLAUDE_SKILL_DIR}/catalog.md`), which covers 28 project types; if none fits, build the options yourself. At least one option must use technologies the user already knows. Skip options that fail a hard constraint and say why. Treat the catalog as a starting point, not as verified fact.
3. **Verify the facts that age.** Versions, pricing, free tiers and end-of-life dates change. Check with web search when it is available. Without it, mark each such fact "verify" and do not invent numbers.
4. **Compare** in one table. Rows: fit with the user's skills, time to a first working release, hosting and running cost, ecosystem and libraries for this need, how easy it is to hire or find help, main risk. Keep each cell to a few words.
5. **Recommend one.** Give the reason in two or three sentences, and the main trade-off you accept. If the answer is close, say what would tip it.
6. **Record the decision.** Offer to update the Stack table and add a row to the Decisions table in ARCHITECTURE.md (ID, decision, why, rejected alternatives, revisit when). If the file does not exist, offer `/diazero:new`. Write only after the user agrees.

## Rules

- Do not recommend a trendy stack to a beginner with a deadline.
- Do not pad the comparison. If one option clearly wins, say so in one line and show the runner-up.
- Be explicit about what you could not verify.
