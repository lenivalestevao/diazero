# Contributing / Contribuindo

Thanks for helping. / Obrigado por ajudar.

## Good first contributions
- **A new playbook** in `skills/new/playbooks.md`: stack defaults, up to 2 extra questions, data-model prompts, a risk checklist, phase 1 seeds and a "done when" example. Follow the shape of the existing sections.
- **Better interview questions** in `skills/new/SKILL.md`. Keep groups of at most 2 questions.
- **A new example** in `examples/<name>/` with all four files, consistent with each other.
- **Bug reports:** include the command, what you expected, and what the plugin did.

## Rules of thumb
- Keep skills short and specific. Say what to do, not how to feel about it.
- The plugin must not state versions, prices or legal rules from memory. Use "verify".
- Read-only skills (`status`, `review`) stay read-only.
- Update the README (both languages) and CHANGELOG when behavior changes.

## Try your change
```bash
claude --plugin-dir ./diazero
```
Then run the command you changed in a scratch project folder.
