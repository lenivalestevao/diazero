# Stack catalog

Starting points for /diazero:stack. Each entry lists 2 or 3 realistic options, a default rule and what to watch for. Use the entry that matches the project, then adapt it to the user's skills and constraints. It names no versions, prices or limits on purpose: verify those before recommending.

General rule: if the user already knows one option well, it wins unless a hard requirement says otherwise.

## Websites

### 1. Blog or content site
- **Options:** Astro or Hugo (static, fastest and cheapest) / WordPress (non-technical editors, plugins) / Next.js with a headless CMS (rich app features beside content)
- **Default:** static generator unless non-developers must edit daily; then WordPress or a headless CMS.
- **Watch for:** WordPress plugin and security upkeep; CMS lock-in; slow image handling.

### 2. Landing page or marketing site
- **Options:** Astro or plain HTML and CSS on a CDN host / Next.js (if it will grow into an app) / a site builder such as Webflow or Framer (designer-led, no code)
- **Default:** static on a CDN host. Add a form service for contact.
- **Watch for:** forms that fail silently; missing analytics and consent banner; mobile layout.

### 3. Documentation site or knowledge base
- **Options:** Docusaurus or Starlight (docs-first) / MkDocs (Python teams, Markdown only) / a hosted docs product (least upkeep)
- **Default:** Docusaurus or Starlight with Markdown in the repository.
- **Watch for:** search quality; versioned docs; keeping docs next to the code.

### 4. Online store (e-commerce)
- **Options:** Shopify (fastest, hosted, fees) / WooCommerce (WordPress shops, full control) / custom with Medusa or a framework plus a payment provider (unusual catalog or flows)
- **Default:** Shopify for a first store; custom only for requirements a platform cannot meet.
- **Watch for:** transaction fees; tax and shipping rules by country; payment compliance; email deliverability.

## Web applications

### 5. SaaS or CRUD web app with accounts
- **Options:** Laravel + Livewire or Inertia / Django (+ HTMX or a frontend) / Next.js or Remix with a Postgres database and an auth service
- **Default:** the full-stack framework the user knows best. Start as a monolith.
- **Watch for:** auth and permissions mistakes; billing edge cases; data-privacy rules.

### 6. Internal admin panel or back-office
- **Options:** a framework admin (Django admin, Laravel Filament, Rails admin gems) / a low-code tool (Retool, Appsmith) / custom React admin
- **Default:** framework admin or low-code; custom only when the workflow is unusual.
- **Watch for:** permissions per role; audit trail; the panel growing into the main product.

### 7. Marketplace or multi-sided platform
- **Options:** Rails, Laravel or Django monolith + Stripe Connect or a similar split-payment service / a marketplace platform or plugin / Next.js + Postgres
- **Default:** monolith plus a payment provider that handles splits and payouts.
- **Watch for:** the cold-start problem; payout and refund rules; trust, moderation and legal terms.

### 8. Booking or scheduling app
- **Options:** Laravel + Livewire or Django (own data and rules) / Next.js + Postgres / an embeddable scheduler product (when custom rules are not needed)
- **Default:** monolith with a database constraint that prevents double booking.
- **Watch for:** time zones; double booking under concurrency; reminders by email or messaging; personal data.

### 9. Real-time app (chat, live collaboration, live data)
- **Options:** Node.js + WebSockets (Socket.IO or a managed realtime service) / Elixir Phoenix (many concurrent connections) / a backend platform with realtime built in (Supabase, Firebase)
- **Default:** a managed realtime service or backend platform; self-host sockets only when scale or cost demands.
- **Watch for:** reconnection and ordering; scaling stateful connections; message history and moderation.

### 10. Progressive web app (PWA)
- **Options:** the web framework already in use + a service worker / Next.js or SvelteKit with a PWA plugin / Flutter web (only if the mobile app is Flutter)
- **Default:** add PWA features to the existing web app instead of starting over.
- **Watch for:** limited device features on some platforms; offline sync conflicts; install prompts.

## APIs and backends

### 11. REST or GraphQL API
- **Options:** FastAPI (Python, typed, quick) / NestJS or Express (TypeScript, shared language with the frontend) / Go or ASP.NET (performance, strong typing, team already there)
- **Default:** the language the team knows; add an OpenAPI description whatever the choice.
- **Watch for:** breaking changes for consumers; object-level authorization; rate limiting.

### 12. Backend-as-a-service for a small product
- **Options:** Supabase (Postgres, auth, storage) / Firebase (document database, strong mobile tooling) / PocketBase (single binary, simple self-hosting)
- **Default:** Supabase when the data is relational; Firebase for mobile-first with simple data.
- **Watch for:** vendor lock-in; security rules written wrong; cost growth with usage; export path.

### 13. Serverless or event-driven backend
- **Options:** cloud functions on the provider the user already uses (AWS Lambda, Cloud Functions, Azure Functions) / edge functions (Cloudflare Workers, Vercel) / a small container service
- **Default:** a container service for steady traffic; functions for spiky or event-triggered work.
- **Watch for:** cold starts; local testing; surprise cost; hard-to-trace event chains.

### 14. When to split into microservices
- **Options:** modular monolith / a few services split by real boundary (team, scale, tech) / full microservices
- **Default:** modular monolith. Split only for a measured reason.
- **Watch for:** distributed debugging; data consistency; operations cost for a small team.

## Apps for devices

### 15. Cross-platform mobile app
- **Options:** Flutter (one codebase, custom UI) / React Native with Expo (JavaScript teams) / a PWA (if device features are minimal)
- **Default:** React Native for JavaScript or React teams; Flutter otherwise.
- **Watch for:** store review rules; push notification setup; device fragmentation; native modules.

### 16. Native mobile app
- **Options:** Swift + SwiftUI (iOS only) / Kotlin + Jetpack Compose (Android only) / both natively when each platform needs deep features
- **Default:** native only when a device feature or performance demands it.
- **Watch for:** two codebases to maintain; store accounts and review; backward compatibility.

### 17. Desktop app
- **Options:** Tauri (small, Rust core, web UI) / Electron (largest ecosystem, heavier) / native toolkit (.NET MAUI or WPF, Qt, SwiftUI) for a platform-specific app
- **Default:** Tauri or Electron for web teams; native for deep OS integration.
- **Watch for:** auto-update and signing; installer per platform; memory use.

### 18. Browser extension
- **Options:** plain TypeScript + a build tool / WXT or Plasmo (framework for extensions) / a content-script-only approach for tiny tweaks
- **Default:** a framework such as WXT for anything with a popup and storage.
- **Watch for:** store review and permission rules; manifest differences between browsers; updates breaking pages.

### 19. IoT or embedded project
- **Options:** ESP32 with Arduino or MicroPython (cheap, quick) / Raspberry Pi with Python (more power, a full OS) / PlatformIO with C or C++ for tight resources
- **Default:** ESP32 for simple sensors; Raspberry Pi when a full OS or camera is needed.
- **Watch for:** power use; updates in the field; device security and credentials; protocol choice (MQTT, HTTP).

### 20. 2D game or casual web game
- **Options:** Godot (full engine, free, exports to web and desktop) / Phaser (web-first JavaScript) / Unity (largest ecosystem, mobile focus)
- **Default:** Godot for a first game; Phaser when it must live in a web page.
- **Watch for:** scope creep; art and sound assets; performance on mobile browsers; store rules.

## Tools and automation

### 21. Command-line tool
- **Options:** Go (single static binary, easy to ship) / Python with Typer or Click (fastest to write) / Rust with clap (speed and safety, steeper learning)
- **Default:** Go for tools shared with others; Python for personal or quick tools.
- **Watch for:** installing on each platform; exit codes and output formats; help text and examples.

### 22. Library or SDK
- **Options:** the language of its users first, in TypeScript, Python, Go or the platform's own language / generate clients from an OpenAPI description / a core in Rust or Go with thin bindings
- **Default:** the main language of the target users, with tests and a changelog from day one.
- **Watch for:** breaking the public API; semantic versioning; docs and runnable examples.

### 23. Automation, scripts and scheduled jobs
- **Options:** Python or Node script + cron or the platform scheduler / n8n or Make (visual flows, many integrations) / GitHub Actions (repository-related jobs)
- **Default:** a script with logs, a dry-run flag and a failure alert; a visual tool when non-developers will edit it.
- **Watch for:** silent failures; duplicate side effects; credentials in code; API changes.

### 24. Chat bot (Telegram, Discord, WhatsApp)
- **Options:** Node.js or Python with the platform's official library / a managed bot or chat platform (less code) / serverless webhook handlers
- **Default:** official library with a small webhook service; check each platform's terms first.
- **Watch for:** WhatsApp business approval and messaging rules; rate limits; storing user messages.

## Data and AI

### 25. Data collection, scraping and pipelines
- **Options:** Python with requests or Playwright + a scheduler / a managed scraping or ETL service / SQL-first with dbt and a warehouse (analytics teams)
- **Default:** Python scripts that are idempotent and save raw data before cleaning it.
- **Watch for:** site terms and legality; blocking and layout changes; data rights and personal data; reproducibility.

### 26. Dashboard or analytics
- **Options:** a BI tool (Metabase, Looker Studio, Power BI) / Streamlit or Dash (Python, quick) / a custom frontend with a charting library
- **Default:** a BI tool first; Streamlit when logic is Python-heavy; custom only for product-grade UX.
- **Watch for:** slow queries; metric definitions that disagree; access control to the data.

### 27. Machine learning model or prototype
- **Options:** Python with scikit-learn (classic ML) / PyTorch (deep learning) / a hosted model API (when training is not required)
- **Default:** a baseline with scikit-learn or a hosted API before any training.
- **Watch for:** no evaluation set; data leaks; results that cannot be reproduced; cost and latency.

### 28. LLM app (chat, search over documents, agents)
- **Options:** a hosted model API + a thin backend in Python or TypeScript / the same plus a vector store for document search (pgvector, a managed vector database) / an agent framework only if the workflow really needs one
- **Default:** direct API calls with a small evaluation set. Add retrieval only when the data demands it.
- **Watch for:** prompt injection and data leaks; cost per request; quality drift when models change; storing user data.

## Recording the decision

Whatever the entry, write the result in ARCHITECTURE.md as one row in the Decisions table: ID, decision, why, rejected alternatives, revisit when. Name the trigger that would reopen the decision, such as a team growing past a size or traffic reaching a measured level.
