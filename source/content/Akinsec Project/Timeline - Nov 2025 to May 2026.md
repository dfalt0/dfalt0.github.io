---
title: "Akinsec — timeline (Nov 2025–May 2026)"
tags:
  - akinsec
  - AskAkin
  - timeline
description: "High-level timeline of AskAkin and akinsec.com work from git history."
---

# Timeline — November 2025 through May 2026

Single-page narrative derived from **git history** in the AskAkin and akinsec workspaces. Detail lives in the linked notes per repo.

## 2025-11 — 2026-01 (AskAkin: heavy upstream cadence)

- The AskAkin tree carried a **large volume of upstream LibreChat** changes (security fixes, MCP OAuth behavior, Meilisearch, Redis streaming, Helm/Docker, accessibility, model catalog updates).
- Notable upstream themes visible in history: **rate limiting and IP handling**, **MCP reconnect and OAuth** hardening, **artifact and Sandpack/Monaco** work, **Bedrock and Vertex** fixes, **shared links and permissions** refactors.
- Release markers in history include **v0.8.2** and move toward **v0.8.3** / **rc** lines in this window.

## 2026-02 — 2026-03 (AskAkin: admin, tenancy, and ops polish)

- Upstream continued with **multi-tenant isolation**, **admin APIs** (users, groups, roles, grants), **DB-backed MCP config**, and broad **TypeScript migration** in backend packages.
- Documentation and packaging touches around **hosted deployment templates** (public docs only — no secrets here).
- **v0.8.4** and **v0.8.5** (and rc) appear in the log as upstream release aggregation points.

## 2026-04 (both tracks)

**AskAkin**

- Ongoing upstream: **GitNexus**-related CI/search experimentation, **MCP OAuth** tenant callback fixes, **Claude Opus 4.7** support, dependency audits.
- **Fork-specific:** **Wazuh** integration commit; **login page and icons** refresh; **onboarding and Railway-oriented features** (wording only — no env values).

**akinsec website**

- **2026-04-12** — Initial commit, **Svelte migration**.
- **2026-04-13** — Theme and marketing sections; **split** of website vs app concerns in history.
- **2026-04-13–15** — **Better Auth** health checks; **Wazuh API**-related backend functionality; **Railway** backend wiring (descriptive only).
- **2026-04-26–30** — Homepage and **pricing** UI iterations, **about** subpages, **legal** files, theme/background fixes.

## 2026-05

**AskAkin**

- Dependency and **workspace** maintenance; **font/build** adjustments.
- **Package manager:** history shows migration intent from **Bun to pnpm** with associated review.
- Continued small **code review** commits.

**akinsec website**

- Incremental **+page** and content tweaks; minor **UI** fixes through early May.

## How to refresh this file

From each repo root (examples, adjust dates):

```bash
git log --since="2025-11-01" --pretty=format:"%ad %s" --date=short
```

Re-summarize themes; do not paste secrets or full remote merge URLs.
