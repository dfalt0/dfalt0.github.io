---
title: "AskAkin — git notes (fork vs upstream)"
tags:
  - AskAkin
  - akinsec
  - LibreChat
  - devblog
description: "AskAkin repository: fork-specific commits and a high-level read of upstream LibreChat history."
---

# AskAkin — git notes

**AskAkin** is a **LibreChat fork** used as the Akinsec customer chat application. Most commits since late 2025 are **upstream LibreChat** merges and fixes; a small set are **product/fork** specific.

## Scale (sanitized stats)

- Approx. **792** commits in the local log from **2025-11-01** through **2026-05-14** (`git log --since=2025-11-01 --oneline`).
- Treat the long tail as **upstream** unless called out below.

## Fork- and product-specific commits (messages as in git)

These are the clearest **non-upstream-style** subjects at the tip of history (newest first). Placeholder noise is omitted.

| Approx. date | Short hash | Subject |
|--------------|------------|---------|
| 2026-05-14 | `3f6630b80` | thorough code review and swap from bun to pnpm |
| 2026-05-12 | `8abdc233d` | code review |
| 2026-05-08 | `7689cdee6` | update dependencies again |
| 2026-05-08 | `487bcdb70` | updated dependencies and npm package |
| 2026-05-08 | `3cc9d1019` | Update package-lock.json |
| 2026-05-07 | `1448f9bcd` | font updates to build |
| 2026-05-07 | `33d4a96a8` | workspace changes |
| 2026-04-29 | `ecea3c07d` | Onboarding and railway features |
| 2026-04-28 | `47ed288d5` | Updated icons and loginpage |
| 2026-04-28 | `bdd9cacd6` | Wazuh - Initial Integration |

Several nearby commits used **placeholder titles** in git; they were not copied here.

## Upstream LibreChat — how to read the firehose

Instead of listing hundreds of PR titles, group by **theme** when you scan `git log`:

- **MCP:** OAuth discovery, token refresh, reconnect storms, tool discovery permissions, tenant/admin callbacks.
- **Security:** SSRF-style guards for actions/MCP, URL validation, rate limits, ACL and sharing fixes, sanitization for uploads and artifacts.
- **Multi-tenant / admin:** tenant-scoped config, admin auth routes, grants/roles/groups APIs, config route splits.
- **Data layer:** MongoDB/FerretDB compatibility, Redis job store, Meilisearch sync, migrations in `data-schemas` / `packages/api`.
- **UX / a11y:** sidebar redesign, artifacts, model selector, screen reader fixes.
- **Providers:** Bedrock, Vertex, OpenRouter, Gemini, Claude family updates and pricing/context windows.

Upstream **release tags** visible in this period include **v0.8.2**, **v0.8.3**, **v0.8.4**, **v0.8.5** (and `-rc` lines). Use `git tag -l "v0.8*"` locally for the exact set.

## Sensitive information — explicit exclusions

Do **not** add to this devblog:

- Values from `.env`, API keys, database URIs, or JWT secrets.
- Private webhook URLs, signed URLs, or session material.
- Customer-identifying ticket text pasted from issues.

Commit hashes and **public** upstream PR numbers (already in merge subjects) are generally fine; re-check before publish if a PR title ever contained internal names.

## Related

- [[Timeline - Nov 2025 to May 2026]]
- [[akinsec.com website - Git notes]]
