---
title: "AskAkin — my commits (author notes)"
tags:
  - AskAkin
  - akinsec
  - devblog
description: "AskAkin: only commits authored by markakinshev@gmail.com, with file-level git show notes."
---

# AskAkin — my commits

AskAkin is built on **LibreChat**. This page documents **only work I committed** (Git author **`markakinshev@gmail.com`** — `dfalt0` / `Mark`). **No** third-party or upstream contributor history is summarized here.

To regenerate the list locally:

```bash
git log --author="markakinshev@gmail.com" --format="%h %ai %s" --reverse
```

---

## Commits — code-level summary (`git show --stat`)

Newest first. Vague git titles are kept in headings; bullets describe **what actually changed**.

### `3f6630b80` — 2026-05-14 — thorough code review and swap from bun to pnpm

- **Package manager:** removed root **`bun.lock`** and large **`package-lock.json`** churn; added **`pnpm-lock.yaml`**, **`pnpm-workspace.yaml`**, **`.npmrc`**; **`package.json`**, **`turbo.json`**, Dockerfiles, **`.devcontainer`**, **`.do/gitnexus`**, `config/*` scripts updated for pnpm.
- **CI:** Playwright workflow reshuffle (`playwright.yml` removed, **`playwright-e2e.yml`** added), **`npm-audit-scheduled.yml`**, edits across `backend-review`, `client`, `data-provider`, `eslint-ci`, `frontend-review`, `gitnexus-index`, etc.
- **Akinsec MCP server:** **`api/server/mcp/akinsec/`** — `auth.js`, `context.js`, `server.js`, `tools.js`, `smoke.js`, **`__tests__/`** (auth, server, tools specs).
- **Client / product:** **`sanitizeHtml.ts`**, **`isValidGtmId`**, **`gtm.ts`**, tests; **`ModelSelector`** + **`chrome.tsx`**, **`layout.ts`**, **`layout.spec.ts`**; **`ChatMessageTurnRoot`**; **`SidePanel/brand.tsx`**; **`TrustSection`**; **`MCPServerList`**; **`vite.config.ts`** large update; **`deploy/csp-headers.example`**; **`librechat.example.yaml`**.
- **packages/api:** import/path fixes for pnpm resolution (`redisClients`, `apiKeys`, `mcp/connection`, etc.).

### `8abdc233d` — 2026-05-12 — code review

- **Rate limiters:** `forkLimiters`, `importLimiters`, `loginLimiter`, `messageLimiters`, `registerLimiter`, `resetPasswordLimiter`, `sttLimiters`, `ttsLimiters`, `uploadLimiters`, `verifyEmailLimiter` — aligned edits across **`...Limiter.js`** files.
- **React shell:** **`App.jsx`**, **`AuthContext.tsx`**, **`ApiErrorBoundaryContext.tsx`**, **`main.jsx`**, **`ChatRoute.tsx`**, **`index.tsx`**, new **`routerFuture.ts`**, **`shims.ts`**.
- **Theme env:** **`getThemeFromEnv.js` → `getThemeFromEnv.ts`**.
- **Banners:** **`Banner.tsx`** + **`Banner.spec.tsx`**.
- **Agents / storage:** **`packages/api/src/agents/chain.ts`**, **`client.ts`**, **`storage/s3/crud.ts`**, **`files/encode/utils.ts`**, **`tools/classification.ts`**, **`utils/ports.ts`** (+ spec), **`data-provider/src/request.ts`**.
- **Docs / config:** **`AGENTS.md`**, **`librechat.example.yaml`**, **`a11y.yml` workflow**.

### `7689cdee6` — 2026-05-08 — update dependencies again

- **`package.json`**, **`bun.lock`**, **`package-lock.json`** — dependency / lockfile cleanup (~1542 deletions in lockfile chunk).

### `487bcdb70` — 2026-05-08 — updated dependencies and npm package

- **`package-lock.json`** large refresh; **`package.json`** (root, `api`, `client`, `packages/api`, `data-provider`); **`client/vite.config.ts`**; **`data-provider/src/actions.ts`**.

### `3cc9d1019` — 2026-05-08 — Update package-lock.json

- **`package-lock.json`** only (~1160 insertions) — lockfile sync.

### `1448f9bcd` — 2026-05-07 — font updates to build

- **Font binaries:** **`client/fonts/`** — Inter (regular/semibold/bold + italics), Roboto Mono latin subsets (woff2).
- **`client/package.json`**, **`bun.lock`**, **`.gitignore`**.

### `33d4a96a8` — 2026-05-07 — workspace changes

- **Wazuh workspace pages:** **`ActivityWorkspacePage`**, **`AlertsWorkspacePage`**, **`CloudWorkspacePage`**, **`ConfigWorkspacePage`**, **`DevicesWorkspacePage`**, **`OpsWorkspacePage`**, **`ThreatsWorkspacePage`**, **`WazuhWorkspaceSkeleton`**, **`DonutSummary`** — UI and data-binding edits.
- **New:** `SecurityEngineSetupBanner.tsx`.
- **`lib/wazuh/mocks.ts`**, **`locales/en/translation.json`** (+~183 lines), **`package.json`**, **`bun.lock`**, **`Chat/Header.tsx`**.

### `edbcde16a` — 2026-05-05 — *(vague git title)*

- **Agents security module:** **`packages/api/src/agents/security/`** — `policy.ts`, `context.ts`, `audit.ts`, `redact.ts`, `types.ts`, **`index.ts`**, **`.spec.ts`** files; **`handlers.ts`** + **`handlers.security.spec.ts`**.
- **API:** **`api/server/controllers/tools.js`** expanded; **`agents/openai.js`**, **`responses.js`**, **`Endpoints/agents/initialize.js`** touched.
- **Client:** **`WorkspaceAreaTabs.tsx`**, **`workspaceNavItems.ts`**, **`SidePanel/MCPBuilder/MCPServerList.tsx`**, **`useSideNavLinks.ts`**, auth layout/footer/login/registration, **`Landing.tsx`**, **`Startup.tsx`**, **`style.css`**, **`vite.config.ts`**, **`librechat.example.yaml`**, **`translation.json`**, **`client/fonts/.gitkeep`**.

### `ecea3c07d` — 2026-04-29 — Onboarding and railway features

- **API:** **`AkinsecOnboardingController.js`**, **`akinsecOnboarding.js`**, **`verifyAkinsecOnboardingJwt.js`**, **`akinsecRailwayWazuhProvision.js`**, **`akinsecSecurityEngineUser.js`**, **`railwayGraphql.js`**; **`wazuhContextMiddleware.js`**; **`wazuh.js`**, **`wazuhThreats.js`**, **`AuthService.js`**, **`AuthController.js`**, **`jwtStrategy.js`**.
- **Wazuh:** **`requestContext.js`**, **`indexerClient`**, **`managerClient`** updates.
- **Schema / client API:** **`packages/data-schemas`** user fields (`railwayProjectId`, `railwayEnvironmentId`, etc.); **`packages/data-provider`** (`api-endpoints`, `data-service`, `config`, `request`, `types`, exports).
- **Client:** **`SecurityEngineOnboarding.tsx`**, **`Registration.tsx`**, **`Landing.tsx`**, **`Footer.tsx`**, **`ExpandedPanel.tsx`**, **`Startup.tsx`**, **`index.tsx`**, **`translation.json`**, **`.env.example`**.

### `47ed288d5` — 2026-04-28 — Updated icons and loginpage

- **Branding:** **`client/public/assets/akinsec-favicon.png`**, **`client/index.html`**.
- **Auth screens:** **`AuthLayout.tsx`**, **`Login.tsx`**, **`LoginForm.tsx`**, **`Registration.tsx`**, **`RequestPasswordReset.tsx`**, **`ResetPassword.tsx`**, **`TwoFactorScreen.tsx`**, **`VerifyEmail.tsx`**, **`Footer.tsx`**, **`TwoFactorController.js`**, **`AuthService.js`**, **`config.js`**, **`.env.example`**, **`vite.config.ts`**, **`Startup.tsx`**.

### `bdd9cacd6` — 2026-04-28 — Wazuh - Initial Integration

- **Backend:** **`api/server/routes/wazuh.js`**, **`wazuhThreats.js`**, route registration in **`routes/index.js`**, **`index.js`**; **`services/wazuh/managerClient.js`**, **`indexerClient.js`**; **`Tools/credentials.js`**.
- **Client workspace:** **`WorkspaceAreaTabs.tsx`**, **`WorkspaceNavContext.tsx`**, **`WorkspaceNewChatButton.tsx`**, **`workspaceNavItems.ts`**, **`WazuhWorkspace/*`** (Activity, Alerts, Cloud, Config, Devices, DonutSummary, Ops, Threats, skeleton, panel), **`lib/wazuh/api.ts`**, **`mocks.ts`**.
- **Chat shell:** **`ChatView.tsx`**, **`Header.tsx`**, **`ChatForm.tsx`**, **`Landing.tsx`**, **`TemporaryChat.tsx`**, **`MessagesView.tsx`**, **`App.jsx`**, **`ChatRoute.tsx`**, **`style.css`**, **`vite.config.ts`**.
- **Theming / docs:** **`ThemeQuickSelect.tsx`**, **`SandThemeHtmlFix.tsx`**, **`ThemeProvider.tsx`**, **`ThemeSelector.tsx`**, **`Dropdown.css`**, **`docker-compose.yml`**, **`librechat.example.yaml`**, **`README.md`**, **`README.zh.md`**, **`AGENTS.md`**, **`bun.lock`**.

---

## Sensitive information

Do **not** publish: `.env` values, API keys, DB URIs, JWT secrets, or private webhook URLs. Commit hashes are fine.

## Related

- [[Timeline - Nov 2025 to May 2026]]
- [[akinsec.com website - Git notes]]
