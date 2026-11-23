# Playbooks by project type

Use the section that matches the type. Stack defaults are proposals: prefer what the user already knows, and check current versions before naming any.

## Web app

- **Defaults:** a framework the user knows (Laravel, Django, ASP.NET, Next.js or React with an API), PostgreSQL or MySQL, managed hosting. Start as a monolith.
- **Extra questions:** Is there login, and which roles? Payments? Public pages that need SEO, or a private panel? Mobile-first?
- **Data-model prompts:** users and roles, the core entity and its lifecycle states, timestamps, soft delete, audit trail.
- **Risk checklist:** session and auth security, personal data (LGPD, GDPR), payment provider lock-in, email deliverability, admin panel scope creep.
- **Phase 1 seeds:** repo and CI, project skeleton, migration for the core entity, one end-to-end flow (create, list, view), deploy to staging.
- **Done-when example:** "a new user can sign up, create X and see it in the list on the staging URL."

## API / backend

- **Defaults:** the framework the user knows, PostgreSQL, OpenAPI description, token-based auth, containerized deploy.
- **Extra questions:** Who consumes it (own frontend, third parties)? Expected load? Versioning needs? Webhooks?
- **Data-model prompts:** resources and their relations, idempotency keys, pagination style, error format.
- **Risk checklist:** breaking changes for consumers, rate limiting, authorization holes (object-level), secrets, observability.
- **Phase 1 seeds:** skeleton with health endpoint, auth, one resource with full CRUD, automated API tests, deploy.
- **Done-when example:** "GET /health returns 200 on staging and the CRUD tests pass in CI."

## Mobile app

- **Defaults:** Flutter or React Native for one codebase, native only if a device feature demands it. A small backend or a managed backend service.
- **Extra questions:** iOS, Android or both? Offline use? Push notifications? Store accounts already available?
- **Data-model prompts:** local versus remote data, sync conflicts, user session, permissions requested.
- **Risk checklist:** store review rules, permission prompts, offline sync bugs, device fragmentation, push delivery.
- **Phase 1 seeds:** app shell with navigation, one real screen backed by real data, build running on a device, internal test build.
- **Done-when example:** "the build installs on a physical device and shows the list from the API."

## Automation / script

- **Defaults:** Python or Node, a scheduler (cron or the platform's), structured logs, config through environment variables.
- **Extra questions:** What triggers it and how often? What happens on failure? Who is told? Is any step destructive?
- **Data-model prompts:** inputs and outputs, state kept between runs, idempotency (safe to run twice).
- **Risk checklist:** silent failures, duplicate side effects, credentials in code, third-party API changes, no dry-run mode.
- **Phase 1 seeds:** one run end to end on sample data, dry-run flag, logging, failure notification, scheduled run.
- **Done-when example:** "a dry run prints what it would do, and a real run twice produces no duplicates."

## Library / CLI

- **Defaults:** the language of its users, a test runner, a package registry, semantic versioning, a changelog.
- **Extra questions:** Who installs it and how? Which platforms? What is the public interface?
- **Data-model prompts:** public API surface, configuration, exit codes and output formats, error messages.
- **Risk checklist:** breaking the public API, platform differences, missing docs and examples, supply-chain hygiene.
- **Phase 1 seeds:** package skeleton, one working command or function, tests in CI, install from a clean machine, README with usage.
- **Done-when example:** "a fresh install on a clean machine runs the quick-start example from the README."

## Site / landing page

- **Defaults:** a static site generator or plain HTML and CSS, a CDN host, a form service for contact. Add a CMS only if non-developers will edit content.
- **Extra questions:** What is the single action a visitor should take? Who edits the content later? Does it need SEO or analytics?
- **Data-model prompts:** pages and sections, content source, form fields and where submissions go.
- **Risk checklist:** slow pages, missing mobile layout, forms that silently fail, cookie and consent rules, domain and DNS mistakes.
- **Phase 1 seeds:** repo and deploy pipeline, one real page live on the final domain, working form or call to action.
- **Done-when example:** "the page loads on the real domain on a phone and the form sends a test message to the owner."

## Data / AI project

- **Defaults:** Python, notebooks only for exploration, a reproducible script or pipeline for anything that must run again, a simple evaluation set from day one.
- **Extra questions:** Where does the data come from and may it be used? What does a good result look like, in a number? Who uses the output and how?
- **Data-model prompts:** raw versus cleaned data, features or prompts, evaluation set, where results are stored.
- **Risk checklist:** unclear data rights, personal data, no baseline to beat, results that cannot be reproduced, model or API cost, silent quality drops.
- **Phase 1 seeds:** load a small real sample, a baseline result, an evaluation script, one end-to-end run that anyone can repeat.
- **Done-when example:** "one command reproduces the baseline score from the sample data."
