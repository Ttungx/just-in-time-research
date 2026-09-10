---
name: zen-of-search
description: Retrieve external information when a task needs current facts, source discovery, URL reading, site exploration, or claim verification, even without an explicit search request. Favor Exa for discovery, Firecrawl CLI for acquisition, Tavily as an independent path, compose tools across stages, inspect sources, stop at sufficiency.
---

# Zen of Search

Search is not link collection. Reduce uncertainty until you have enough evidence to answer, decide, or continue the real task.

Works with equivalent search and retrieval tools. Firecrawl examples assume the Firecrawl CLI is installed and authenticated.

## Shape the Information Gap

Identify what is missing before choosing a tool:

- **Discovery** — find the right source, project, term, person, document, paper, or direction.
- **Acquisition** — read, traverse, or extract information from a source you already know or have found.
- **Verification** — test an important claim against stronger, fresher, or genuinely independent evidence.

Treat freshness, exact identifiers, domain scope, language, geography, and source quality as constraints on those problems rather than separate workflows.

## Compose Capabilities, Not Providers

Choose the best capability for the **next information gap**, not one tool for the whole task. Non-trivial search work often benefits from handing evidence between complementary tools: discover broadly with one system, acquire the underlying source with another, then verify remaining uncertainty through an independent path.

Useful combinations include:

- **Exa → Firecrawl** — discover semantically, then read or traverse the strongest sources.
- **Tavily → Firecrawl** — locate fresh or precisely filtered results, then inspect the underlying pages.
- **Exa + Tavily → Firecrawl** — use independent discovery paths when verification matters, then ground the conclusion in the original sources.

Do not invoke multiple tools merely for provider diversity. Combine them when each one resolves a different remaining uncertainty. A simple lookup may need one tool; a serious research task may naturally use several.

## Keep a Loose Tool Map

- **Exa — semantic discovery.** Prefer it when the target is easier to describe than to name, when related material matters, or when you are still learning the vocabulary of the problem.
- **Firecrawl CLI — acquisition and traversal.** Prefer it when you need the source itself: page content, site structure, multiple pages, developer/research indexes, or browser interaction. Using the CLI avoids exposing a large persistent MCP tool surface.
- **Tavily — precision or an independent path.** Use it when freshness, explicit filters, conventional web lookup, or a second retrieval path can add information that the current path lacks.

These roles overlap. Follow capabilities rather than brands, and use an equivalent tool when the current environment offers a shorter or better route.

## Firecrawl CLI Quick Reference

Use Firecrawl progressively; these are common primitives, not a mandatory pipeline.

```bash
# General web search
firecrawl search "query"

# Bound result count
firecrawl search "query" --limit 10

# Recent news / time-bounded search
firecrawl search "query" --sources news --tbs qdr:w

# Search and retrieve result content
firecrawl search "query" --scrape

# Programming-oriented search: issues, merged PRs, READMEs, docs
firecrawl search "query" --categories developer

# Read a known page
firecrawl scrape https://example.com

# Discover relevant URLs on a site
firecrawl map https://example.com --search "docs"

# Retrieve multiple pages when they are genuinely needed
firecrawl crawl https://example.com --limit 50 --max-depth 2 --wait

# Search the research-paper index
firecrawl research search-papers "query" --limit 20

# Inspect / expand / verify a strong paper
firecrawl research inspect-paper <paper-id>
firecrawl research related-papers <paper-id> --intent "question"
firecrawl research read-paper <paper-id> --question "claim to verify"

# Search GitHub issue / PR history and repository READMEs
firecrawl research search-github "query" --limit 10

# Interact with the last scraped page when static retrieval is insufficient
firecrawl interact "Extract the pricing table"

# Check current flags and capabilities
firecrawl <command> --help
```

A useful escalation intuition is `search → scrape → map → crawl → interact`: move deeper only when the current level cannot resolve the uncertainty, and skip levels freely.

## Search for Information Gain

Make each additional retrieval action answer a different remaining question. If a search stalls, diagnose what failed — query wording, source class, retrieval mode, page access, freshness, or the assumption behind the search — and change that dimension rather than repeating the same action elsewhere.

Treat search results and snippets as pointers. Inspect the underlying source before relying on a claim that carries the answer. Prefer evidence close to the underlying fact; use independent or community sources when they add implementation reality, contradiction, context, or triangulation.

Scale verification with consequence. Independence matters more than source count.

## Stop at Sufficiency

Stop when the important uncertainty is resolved, the load-bearing claims have adequate support, and another plausible retrieval step is unlikely to change the conclusion.

If code inspection, local data, measurement, experimentation, or user input now has higher expected information value than another search, leave search and do that instead.

## The Way

```text
Let the question reveal the retrieval shape.
Choose the next capability, not one provider for the whole task.
Compose tools when their information value is complementary.
Use the smallest sufficient search surface.
Read the source, not merely the result.
Escalate only while uncertainty remains.
Stop when more retrieval is unlikely to change the answer.
```
