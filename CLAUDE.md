# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Respan (formerly Keywords AI) documentation site, built with **Mintlify**. This is a pure documentation repository — all content is MDX files, with no application code. Respan is a full-stack LLM engineering platform providing observability, prompt management, evaluations, and an AI gateway (250+ models).

## Development Commands

```bash
# Install Mintlify CLI (required once)
npm i -g mintlify

# Start local dev server with hot reload
mintlify dev

# Re-install dependencies if dev server fails
mintlify install
```

Deployment is automatic — pushing to `main` triggers production deploy via the Mintlify GitHub App.

## Repository Structure

- **`docs.json`** — Mintlify configuration: navigation tabs/groups, API settings, theme, redirects. This is the central config file. All page routing is defined here.
- **`documentation/`** — Product docs: getting-started guides, feature pages (logs, traces, gateway, prompts, evaluations, automation, users, dashboard), admin, security, resources
- **`apis/`** — REST API reference pages organized by domain: `observe/`, `develop/`, `evaluate/`, `manage/`, `automation/`, `reference/`
- **`sdks/`** — SDK documentation: `python/` (Respan SDK), `python-tracing/` (tracing SDK), `typescript-tracing/` (JS tracing SDK)
- **`integrations/`** — Third-party integration guides: `providers/` (LLM providers), `development-frameworks/` (LangChain, Vercel, etc.), `dev-tools/`, `analytics/`
- **`cookbooks/`** — Tutorials and walkthroughs
- **`changelog/`** — Product update entries
- **`images/`, `logo/`** — Local assets; most images are hosted on S3 (`keywordsai-static.s3.us-east-1.amazonaws.com`)

## Key Conventions

### MDX Page Structure

Every page has YAML frontmatter with `title` and `description`:

```mdx
---
title: "Page Title"
description: "One sentence description (50-160 chars)"
---
```

### URL Routing

URLs map directly to file paths: `/documentation/products/logs/quickstart` → `documentation/products/logs/quickstart.mdx`. New pages must also be added to the `navigation` section in `docs.json`.

### Mintlify Components Used

- `<ParamField>` — API parameter documentation (query, path, body variants)
- `<RequestExample>` / `<ResponseExample>` — API code examples (Python, TypeScript, cURL)
- `<CodeGroup>` — Tabbed code blocks
- `<Tabs>` / `<Tab>` — Content tabs (commonly: OpenAI, Anthropic, Google Gemini)
- `<Steps>` / `<Step>` — Sequential instruction steps
- `<Frame>` — Image wrapper (`<Frame className="rounded-md">`)
- `<Card>` / `<CardGroup>` — Navigation cards
- `<Accordion>` / `<AccordionGroup>` — Collapsible sections
- `<Note>`, `<Warning>`, `<Info>` — Callout blocks

### Documentation Templates

- **Feature pages** follow the SOP in `documentation/products/features_sop.mdx`: What is it → Resources → Steps (tabbed by SDK) → Configuration → Related links
- **API endpoint pages** follow the SOP in `apis/reference/api_endpoints_sop.mdx`: Intro → Query/Path/Body params → Response fields → Request/Response examples (Python, TypeScript, cURL)

### API Base URLs

- Platform: `https://platform.respan.ai/`
- API: `https://api.respan.ai`
- OpenAI-compatible proxy: `https://api.respan.ai/api/`
- Anthropic proxy: `https://api.respan.ai/api/anthropic/`
- Google Gemini proxy: `https://api.respan.ai/api/google/gemini`

### Rebranding Context

The project was recently rebranded from "Keywords AI" to "Respan". Legacy references to `keywordsai` may still exist in S3 image URLs and some content. When editing, use "Respan" / "respan" for all new content.
