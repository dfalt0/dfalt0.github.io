---
title: "akinsec.com website — git notes"
tags:
  - akinsec
  - svelte
  - devblog
description: "akinsec repo: every commit with code-level summary from git show --stat (sanitized)."
---

# akinsec.com website — git notes

Monorepo under **`akinsec-prod/`** with two deployables: **`akinsec-website`** (marketing) and **`akinsec-app`** (product, DB, Wazuh, Railway). **Full git history currently spans 2026-04-12 → 2026-05-05** (~31 commits)—there is nothing older in this repository yet.

**Sanitization:** merge commits that named a hosted remote are summarized without URLs.

---

## Commit index (newest first) — message + what actually changed

### `92de4f5` — 2026-05-05 — *(placeholder git title)*

- **`akinsec-app`:** large rewrite of **`auth/login/+page.svelte`**; **`ThemeToggle.svelte`** tweaks.
- **`akinsec-website`:** **`home.css`**, **`HeroAskAkinMock.svelte`** small edits.

### `5ceebf8` — 2026-05-02 — UI changes and fixes; added legal files

- **Legal system:** **`lib/legal/`** — `LegalDocLayout.svelte`, `LegalWorkInProgressBanner.svelte`, **`PrivacyArticle.svelte`**, **`TermsArticle.svelte`**, **`legalNav.ts`**, `privacyConstants.ts`, `termsConstants.ts`.
- **Docs UX:** **`DocSplitShell.svelte`**, **`DocsArticleHeader.svelte`**, **`docSplitAside.ts`**, refactors to **`DocsArticle.svelte`** and **`Documentation/+layout.svelte`**.
- **Routes:** **`Privacy/+page.svelte`**, **`Terms/+page.svelte`**, **`FAQ/+page.svelte`** major expansion; **`BuiltWithLibreChat` renamed to `AIChat`**; removed **`DemoLive`**, **`DesktopApp`**, **`Frameworks`**, **`LegacyHome`** stubs; **`Contact`**, **`Why`**, marketing **`+layout`**, **`app.css`**, **`home.css`**, hero/home/workspace preview tweaks; **`.env.example`** on website.

### `c5a0a3b` / `67a4adb` — 2026-05-01 — Update +page.svelte

- **`c5a0a3b`:** **`Why/+page.svelte`** only — large content/layout rewrite (~199/190 lines churn).
- **`67a4adb`:** **`About/+page.svelte`** — structural/content edits (~51/46 lines).

### `6fcdc9f` — 2026-04-30 — Changes to subpages and main About page

- **New marketing routes:** **`SecurityEngine/+page.svelte`** (large), **`BuiltWithLibreChat/+page.svelte`**, **`Dashboard/+page.svelte`**, **`Frameworks/+page.svelte`**.
- **Removed stub routes:** `DashboardExample`, `FileAnalysisExample`, `FrameworksExample`, `IntegrationsExample`, `ReportsExample`, `TasksExample`, `TemplatesExample`.
- **`About/+page.svelte`** rewrite; **`+layout.svelte`** nav changes; **`HomePage.svelte`** pointer tweak.
- **Assets:** **`static/images/wazuh/*.svg`**; **`docs/wazuh-platform-overview.md`**.

### `2bb04a7` — 2026-04-29 — Updated pricing cards

- **`HomePage.svelte`**, **`lib/site/pricingPlans.ts`**, **`Pricing/+page.svelte`**.

### `ef5b9af` — 2026-04-29 — UI: fixed theme & background bugs

- **`background.svelte.ts`**, **`BackgroundToggle.svelte`**, **`DarkVeil.svelte`**, **`SiteBackground.svelte`**, **`theme.svelte.ts`**, **`HomePage.svelte`**, root **`+layout.svelte`**.

### `6314cd4` — 2026-04-29 — Improved UI: mock and colors across homepage

- **`HeroAskAkinMock.svelte`** very large diff; **`home.css`** (+~291 lines); **`app.html`**; **`ThemeToggle`**, **`BackgroundToggle`**, marketing **`+layout`**, **`Pricing`**, **`tailwind.config.cjs`**, **`WhatsInside.svelte`** minor.

### `8629811` — 2026-04-29 — Update HomePage.svelte

- **`HomePage.svelte`** only — small section tweak (~11 insertions, 3 deletions).

### `3538d5d` — 2026-04-29 — more UI tweeks

- **`home.css`**, **`HomePage.svelte`**, **`(marketing)/+layout.svelte`** — spacing/typography polish.

### `38244fa` — 2026-04-29 — UI & page changes

- **Background stack:** **`background.svelte.ts`**, **`BackgroundToggle.svelte`**, **`Grainient.svelte`**, **`SiteBackground.svelte`**, **`DarkVeil.svelte`**, **`ThemeToggle.svelte`**.
- **Content architecture:** **`lib/marketing/docsNav.ts`**, **`DocsArticle.svelte`**, **`Documentation/+layout.svelte`**, new doc subpages under **`Documentation/`** (`workspace`, `sign-in`, `ai-models`, `alerts-monitoring`, `integrations`, `plans-billing`, `privacy-security`, `support`).
- **Pricing data:** **`lib/site/pricingPlans.ts`**; **`FAQ`**, **`Pricing`**, **`Why`**, marketing **`+layout`**, root **`+layout`**, **`app.css`**, **`home.css`**, **`tailwind.config.cjs`**, **`package.json` / `bun.lock`**.

### `0c2166e` — 2026-04-29 — Whats-Inside Section: Edited the cards

- **`WhatsInside.svelte`**, **`home.css`**, **`HomePage.svelte`**.

### `5999f2c` — 2026-04-28 — Updates to homepage UI

- **New** `WhatsInside.svelte`; **`HomePage.svelte`** slimmed; **`home.css`** expanded; **`HeroAskAkinMock`** tweaks; **`TechStackFlowchart.svelte`** deletions; **`Contact`**, **`Pricing`**, **`Why`** edits; **`button-variants.ts`**, marketing **`+layout`**.

### `b5e9829` / `6638524` / `a3bf599` / `afa8fbe` / `9305131` — merges

- Integrate **`dev`** / **`master`** / **PR #1–#3** (use `git show <merge>` for parent file lists if needed).

### `e91bdf4` — 2026-04-28 — Updated browser title

- **`(marketing)/+page.svelte`**, **`Home/+page.svelte`** — `<title>` / metadata text.

### `c58c1be` — 2026-04-28 — update button

- **`HomePage.svelte`** — two-line CTA/button tweak.

### `b0e4f8a` — 2026-04-28 — Updated home page

- **New** `HeroAskAkinMock.svelte` (~430 lines); **`HomePage.svelte`** restructured; removed part of **`TechStackFlowchart.svelte`**; **`+layout`** server/layout; **`package.json`** dependency trim.

### `71b58c9` — 2026-04-28 — Updated app link in CTA buttons

- **`lib/site/app.ts`**, **`voice.ts`**, **`HomePage.svelte`**, **`+layout.server.ts`** — central app URL for CTAs.

### `f9b54f5` — 2026-04-27 — *(placeholder git title)*

- **`WorkspaceAppPreview.svelte`** massive expansion; **`HomePage.svelte`** reflow; **`TechStackFlowchart`**, marketing **`+layout`**; removed **`SectionIndex.svelte`** usage and **`PageStub`** bits; touch **`About`**, **`Contact`**, **`FAQ`**, **`Pricing`**, **`Why`**.

### `4db63c1` — 2026-04-26 — api stuff

- **`akinsec-app`:** **`src/lib/server/llm/anthropic.ts`**, **`moonshot.ts`**; **`routes/api/llm/chat/+server.ts`** (chat API route); **`.env.example`** LLM vars.

### `196544f` — 2026-04-16 — railway backend

- **`railwayPublicApi.ts`** — GraphQL client for Railway (`projectCreate`, workspace listing).
- **`railwayOrgProject.ts`** — provision empty project per org using server token.
- **`.env.example`** — `RAILWAY_*` variable names documented.

### `82310a5` — 2026-04-15 — real app functionality to wazuh API

- **DB:** Drizzle **`0001_org_infra_stack.sql`**, snapshot/journal; **`orgInfraStack.ts`** schema; **`stackSecret.ts`**, **`orgAccess.ts`**.
- **Wazuh server module:** **`lib/server/wazuh/`** — `client.ts`, `config.ts`, `mappers.ts`, `types.ts`, `jwtCache.ts` (+ test), `indexerPhase2.ts`.
- **Provisioning:** **`railwayOrgProject.ts`** wired toward org projects.
- **Workspace UI:** **`WorkspaceAppShell.svelte`**, **`WorkspaceChatView.svelte`**, **`WorkspaceSectionPanels.svelte`**; **`chatWorkspace.svelte.ts`**, **`nav.ts`**, **`wazuhSnapshot.ts`**.
- **Routes:** **`workspace/+layout.server.ts`**, **`+layout.svelte`**, **`[section]/+page`**, login **`+page.server` / `+page.svelte`**; **`auth.ts`**, **`app.d.ts`**, **`package.json`**, **`bun.lock`**, CI workflow.

### `d9b7c66` — 2026-04-13 — better-auth health checks

- **`routes/health/+server.ts`** — liveness endpoint.
- **`scripts/check-database-url.ts`** — clearer migrate failures.
- **`railway.toml`**, **`package.json`**, **README**, website **`+layout.server.ts`** — health/probe alignment.

### `3a06d23` — 2026-04-13 — Split akinsec-website and akinsec-app

- **Rename/move:** `apps/akinsec` → **`apps/akinsec-app`** and **`apps/akinsec-website`**.
- **Website:** marketing routes; **`createMarketingUrl.ts`**.
- **App:** Drizzle, auth, workspace; **`hooks.server.ts`** as appropriate per app.
- **README** and **CI** updated for two Railway service roots.

### `f6e04c1` — 2026-04-13 — Theme, feature showcase, sections

- **`ThemeToggle.svelte`**, **`theme.svelte.ts`**, root **`+layout.svelte`** class wiring.
- **New** `WorkspaceAppPreview.svelte`; removed **`CustomerGUINode` / `DataSourceNode` / `SecurityVMNode`** flowchart nodes; simplified **`TechStackFlowchart.svelte`**.
- **Global CSS:** **`app.css`**, **`home.css`**, **`app.html`**; **`HomePage`**, **`About`**, **`Contact`**, **`FAQ`**, **`Pricing`**, **`Why`**, app **`+layout`**; **Lottie** files under **`static/animations/`**.

### `1934402` — 2026-04-12 — Svelte Migration

- **Entire first app scaffold** (then `apps/akinsec`): SvelteKit, Tailwind, Drizzle **`0000_init_better_auth.sql`**, Better Auth server/client, marketing route grid (About, Contact, FAQ, Pricing, Why, stubs), **`HomePage.svelte`**, **`TechStackFlowchart`**, **`faqData` / `whyData`**, **`api/me`**, auth routes, **`railway.toml`**, **`bun.lock`**, CI, **README**.

### `64f8f8c` — 2026-04-12 — Initial commit

- **`.gitattributes`** only (repo shell).

---

## Quick reference — top-level folders today

| Path | Role |
|------|------|
| `akinsec-prod/apps/akinsec-website` | Marketing SPA, no Postgres requirement in README. |
| `akinsec-prod/apps/akinsec-app` | Auth, DB, workspace, Wazuh client, Railway provisioner, `/health`. |

## Related

- [[Timeline - Nov 2025 to May 2026]]
- [[AskAkin - Git notes]]
