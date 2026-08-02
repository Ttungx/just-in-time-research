---
name: zen-of-search
description: Select and combine available search, retrieval, extraction, repository, and browsing tools for external information acquisition. Use when a task requires current facts, source discovery, URL reading, structured lookup, difficult-page acquisition, website exploration, or independent verification. Start from the information gap, use one primary tool, and add another only when it performs a distinct stage better.
---

# Zen of Search

Search is the reduction of uncertainty through evidence.

Use the shortest reliable path from the question to an inspected source.

## Read the Retrieval Shape

Before choosing a tool, determine:

1. Is the target known precisely or only describable by meaning?
2. Do freshness, exact phrases, dates, domains, geography, or filters matter?
3. Is the information structured or repeated across several entities?
4. Is discovery difficult, or is acquiring the source content difficult?
5. Does the claim require an original source, an independent check, or a counterexample?

Let the information gap choose the capability. Tool names and schemas in the current environment are authoritative.

## Choose by Capability

### Semantic discovery

Use a semantic search capability when the desired source is easier to describe than to name.

Best for unknown projects, similar products, niche articles, companies, people, technical approaches, and early exploration before the correct terminology is known.

Describe the ideal source: what it discusses, what type of page it is, and why it would be relevant. Form a small candidate set, then inspect the strongest originals.

When available, Exa commonly fits this role.

### Precise and fresh retrieval

Use a precise web-search capability when the target is clear and current relevance, dates, exact phrases, domain filters, or geographic filters matter.

Best for current events, releases, prices, schedules, named facts, policies, and version-sensitive information.

Prefer native filters over increasingly long queries. After discovery, inspect the canonical source rather than relying on result summaries.

When available, Tavily commonly fits this role.

### Structured and parallel lookup

Use a structured or vertical search capability when the question maps to known records or contains several independent lookups.

Best for CVEs, tickers, DOIs, patents, academic records, travel data, identifiers, and repeated comparisons across entities.

Inspect the tool schema first. Batch independent queries when supported, but not when later queries depend on earlier findings.

When available, AnySearch commonly fits this role.

### Source acquisition

Use an extraction or crawling capability when obtaining usable source content is the difficult part.

Best for dynamic pages, PDFs, tables, screenshots, structured extraction, site mapping, and bounded multi-page collection.

Use a single-page operation for a known URL, site mapping when the relevant path is unknown, and crawling only when several pages are genuinely necessary.

When available, Firecrawl commonly fits this role.

### Repository and document inspection

Use repository, documentation, file, or local-code tools when the fact lives in a project rather than the open web.

Prefer official documentation for contracts, repository source and tests for implementation, issues and pull requests for behavioral history, and local code or logs for the user's actual environment.

Do not route project-internal evidence through generic web search when a direct connector or local tool is available.

## Combine Across Stages

Tools may overlap. Start with the capability that addresses the dominant difficulty, then add another only for a distinct job.

```text
semantic discovery
→ select candidate URLs
→ acquire difficult sources

precise lookup
→ open the canonical source
→ verify the exact claim

structured batch lookup
→ select material results
→ inspect original records

website investigation
→ map paths
→ scrape selected pages
→ crawl only if necessary

claim verification
→ inspect the likely primary source
→ seek an independent source, limitation, or contradiction when warranted
```

Do not repeat the same query across providers merely to collect more links.

## Follow a Small Loop

1. State the exact information gap.
2. Choose one primary capability.
3. Retrieve a small candidate set, usually three to eight results.
4. remove duplicates, mirrors, syndicated copies, and low-value summaries;
5. inspect the strongest original sources;
6. add a complementary tool only when coverage is weak, content cannot be acquired, structured retrieval reduces work, or a consequential claim needs independent verification;
7. stop when evidence is sufficient and expose material uncertainty.

Search snippets locate evidence; they are not evidence themselves.

## Use Sources Close to the Fact

Prefer, as appropriate:

1. official documentation, repositories, standards, datasets, filings, and first-party records;
2. maintainers, authors, researchers, institutions, and direct participants;
3. reputable independent reporting and technical analysis;
4. community discussions and secondary summaries.

This is not a universal ranking. Match the source to the claim: code can outrank documentation for actual behavior, and direct incident reports can reveal failures absent from official descriptions.

## Keep the Discipline

- Start with one provider or capability; two are enough for most researched answers.
- Use a third only for a consequential dispute or clear coverage gap.
- Batch independent queries and URLs when supported.
- Do not fetch every result.
- Use native filters before multiplying queries.
- Map before crawling, and bound every crawl.
- Escalate acquisition gradually.
- Search for limitations or contradictions when a claim is important or surprising.
- Do not retry the same failed strategy indefinitely.
- Prefer a few inspected sources over many shallow results.
- Stop when further searching is unlikely to change the conclusion.
- Answer the user's question directly; do not narrate routine tool calls.
- Distinguish sourced facts from inference and judgment.

## The Way

```text
Let the question reveal the retrieval shape.
Let one tool handle one stage well.
Combine tools only across distinct stages.
Read the source, not merely the result.
Verify in proportion to consequence.
Stop when more searching no longer changes the answer.
```
