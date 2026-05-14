---
title: "Akinsec — timeline (Nov 2025–May 2026)"
tags:
  - akinsec
  - AskAkin
  - timeline
  - architecture
description: "In-depth timeline: website structure, repo organization, and the shift from VPS + n8n toward Railway + LibreChat + API tokens."
---

# Timeline — November 2025 through May 2026

This page mixes two sources:

1. **Git history** — **your** AskAkin commits (author-filtered) and the akinsec website repo (no secrets, no env values).
2. **Architecture notes** — how the *product and ops model* evolved (VPS / Hostinger + **n8n** for AI webhooks → **Railway**-hosted services → **LibreChat**-centric flows with **provider API keys** instead of per-customer automation glue). Those bullets are **operator narrative** for the devblog, not something inferred from filenames alone.

**Code-level commit digests** (paths touched, `git show --stat` summaries): [[AskAkin - Git notes]] (**your** AskAkin-authored commits only), [[akinsec.com website - Git notes]] (full **2026-04–05** website repo history).

---

## Architecture evolution (operator notes)

### Phase A — “VPS + n8n” mental model

Early experimentation treated each moving part as **something you SSH into**:

- A **VPS** (e.g. Hostinger-class generic Linux host) held ad hoc services and static-ish endpoints.
- **n8n** owned **AI-shaped glue**: HTTP webhooks in, call an LLM API or a small script out, fan results to email/Slack/another webhook.

**What that optimized for:** speed to wire a demo, one-off automations, and “I control the box.”

**What it fought against as the product grew:**

- **Blast radius** — credentials and workflows lived next to generic server chores; upgrades and backups became bespoke.
- **n8n as the “chat brain”** — conversation state, auth, file uploads, and model routing do not map cleanly to workflow nodes; you end up re-building a product inside workflows.
- **Per-user or per-tenant VPS thinking** — tempting (“spin another box”), expensive to secure, patch, observe, and rotate.

### Phase B — n8n for AI webhooks, still central

Automation stayed useful for **notifications and integrations**, but using n8n as the **primary** AI surface meant:

- Duplicate **auth** and **idempotency** problems at every webhook boundary.
- Harder **audit story** for security buyers (who changed what workflow, when, with which key).

The direction became: keep automation for **peripheral** triggers if needed, **not** as the main reasoning UI or long-lived investigation surface.

### Phase C — Railway as the default host

**Railway** (and similar PaaS patterns) replaced “log into VPS #7” for **deployed** workloads:

- **Git-connected** builds, env vars per **service**, health checks, and fewer snowflakes.
- The akinsec production layout documented in-repo is explicitly **two SvelteKit services** in one project mindset: **marketing** (`akinsec-website`) vs **product** (`akinsec-app`), each with its own root directory, env template, and `railway.toml` behavior (e.g. migrations + `/health` on the app).

**Organizational win:** environments (staging/production) and **databases** (Postgres on the app service) are first-class, not something you remember to `apt upgrade`.

### Phase D — LibreChat (AskAkin) + API tokens / BYOK

The current product stance (also reflected on the marketing site copy) is closer to:

- **LibreChat fork (AskAkin)** as the **durable chat plane**: agents, MCP, memory, artifacts, enterprise-style auth — one application boundary instead of many webhooks pretending to be an app.
- **Provider keys** (BYOK or centrally managed keys, depending on tenant policy) live **inside that app model**, not scattered across n8n credentials × N servers.
- **Wazuh** and **Security Engine** messaging tie investigations to a SOC stack; Railway appears in copy as where customer **engine** deployments run, aligned with server-side provisioning code paths (org → Railway project id, etc.) without documenting secrets here.

**Net shift in one sentence:** move **intelligence and conversation** into **LibreChat**, move **shipping and tenancy** onto **Railway-style services**, retire the idea of **n8n + per-user VPS** as the primary architecture for core product use.

---

## AskAkin — your work (this devblog omits other authors)

Anything you shipped on AskAkin in this period is captured **only** in [[AskAkin - Git notes]] (per-commit file lists). Third-party / vendor commits on the same repo are intentionally **not** catalogued here.

---

## akinsec.com + app — site structure and how it landed in git

The production monorepo (`akinsec-prod`) is organized as **two apps under `apps/`**, documented for **two Railway services**:

| App | Public role | Structure / intent |
| --- | --- | --- |
| **`akinsec-website`** | Marketing at apex / `www` | Routes under `(marketing)` for **story pages**: home (hero, “what’s inside”, workspace preview), **About** (stack narrative: Wazuh + LibreChat, BYOK), **AI Chat** (LibreChat feature grid with links to upstream docs), **Security Engine** (Railway-hosted engine framing), **Documentation** (e.g. workspace doc page tying product to LibreChat lineage), **FAQ** data in `lib/marketing`. |
| **`akinsec-app`** | Product at `app.` | **Better Auth**, Postgres + Drizzle, **`/health`** for probes, workspace UI that mirrors marketing preview patterns, **server-side Railway GraphQL** helpers and **org → Railway project** provisioning vision (`org_infra_stack`, Wazuh connection fields — schema-level, not secrets). |

### Chronological landing (from short website repo history)

**2026-04-12 — “Initial commit” + Svelte migration**

- Hard cut to **SvelteKit** as the implementation baseline for both surfaces (marketing + product direction in one tree over time).

**2026-04-13 — split and vertical slices**

- **“Split akinsec-website and akinsec-app”** — enforced separation so marketing deploys **without** Postgres, and the product service owns **DB migrations**, auth URL alignment, and infra health checks.
- **Theme + feature showcase + sections** — first pass at **information architecture**: hero, feature bands, and consistent marketing chrome instead of a single long page.

**2026-04-13–15 — backend and auth “shape”**

- **Better Auth health checks** — operationalizes “is auth up” the same way Railway expects **HTTP health**, not “SSH and curl localhost.”
- **Wazuh API–related** commits and **“railway backend”** — moves integration logic **into the app** (typed routes, env-driven config) rather than external webhook-only glue.
- **Merge PRs #1–#3** — branch hygiene while the above stabilized.

**2026-04-26–30 — marketing refinement**

- **Homepage UI** iterations: **pricing cards**, **“What’s inside”** card edits, **theme/background** fixes, **CTA** buttons pointing at the **app** origin (single configured `PUBLIC_APP_ORIGIN` pattern per README).
- **About** subpages and **legal** files — **trust and structure** for a security product: what you run, where it runs, compliance-adjacent pages colocated with the story.

**2026-05-02+**

- **Legal + UI fixes**; continued **`+page.svelte`** tweaks — smaller **copy/layout** passes once the skeleton routes existed.

### What was “organized” vs “structured”

- **Organized:** two deployables, two env.example files, two `railway.toml` stories (marketing: `/`; app: `/health` + migrate pre-deploy). CTAs and auth probes all **key off the same public origins** documented in README tables.
- **Structured:** marketing routes each answer one buyer question — **what is AI Chat (LibreChat)?**, **what is the Security Engine?**, **how does workspace relate to LibreChat docs?** — instead of one blob FAQ on the homepage.

---

## 2026-05 snapshot (AskAkin — your commits)

- **pnpm** migration, **code review**, **fonts**, **deps**, **workspace** Waz UI pass, **agents security** module, etc. — see [[AskAkin - Git notes]] for hashes and paths.

---

## How to refresh this file

```bash
# AskAkin — only your commits
git -C /path/to/AskAkin log --author="markakinshev@gmail.com" --pretty=format:"%ad %s" --date=short

# akinsec
git -C /path/to/akinsec log --pretty=format:"%ad %s" --date=short
```

Reconcile dates; extend the **Architecture evolution** section when the ops story changes again. **Never** paste tokens, `.env` lines, or private dashboard URLs.

## Related

- [[AskAkin - Git notes]]
- [[akinsec.com website - Git notes]]
- [[Index - Akinsec devblog]]
