---
name: zen-of-search 
description: Select and combine Exa, Tavily, AnySearch, and Firecrawl for general-purpose external information retrieval. Use when a task requires current facts, web discovery, source finding, URL reading, fact verification, parallel lookup, or website exploration. Match the question to each MCP's strengths, start with the most suitable tool, and combine tools only when they solve different parts of the search problem.
---

# Zen of Search

Search is the reduction of uncertainty through evidence.

Before choosing a tool, ask:

1. Is the target precisely known or only semantically describable?
2. Does freshness or exact filtering matter?
3. Is the information structured or repeated across several entities?
4. Is finding the source difficult, or is acquiring its content difficult?

Use the shortest reliable path from the question to an inspected source.

## Work With the Available Environment

Use the MCP tools available in the current environment and treat their current schemas as authoritative.

When the information already exists in an accessible repository, document collection, connected service, or local file, prefer the direct source tool.

## Know the Tools

### Exa — discover by meaning

Use Exa when the desired source is easier to describe than to name.

It is well suited to unknown projects, similar products, niche articles, companies, people, technical approaches, and exploration before the correct terminology is known.

Describe the ideal source in natural language, form a candidate set, and inspect the strongest results.

Exa answers:

> **Where might the relevant knowledge be?**

### Tavily — retrieve with precision and freshness

Use Tavily when the target is clear and current relevance, dates, exact phrases, domains, geography, or filters matter.

It is well suited to recent events, releases, prices, schedules, named facts, and focused search–extract workflows.

Prefer native filters over increasingly complicated queries. After discovery, inspect the strongest canonical source.

Tavily answers:

> **What currently and precisely matches the question?**

### AnySearch — retrieve by structure and multiplicity

Use AnySearch when the question maps to a supported vertical domain or contains several independent lookups.

It is well suited to identifiers and structured subjects such as CVEs, tickers, DOIs, patents, academic records, travel data, and comparisons across entities.

Inspect the available schema and batch independent queries when doing so reduces work.

AnySearch answers:

> **Can this problem be expressed as structured or parallel queries?**

### Firecrawl — acquire the source itself

Use Firecrawl when obtaining usable source content is the difficult part.

It is well suited to dynamic pages, PDFs, tables, screenshots, structured extraction, site mapping, and bounded crawling.

Use scrape for a known page, map when the relevant path is unknown, and crawl only when several pages are genuinely required.

Firecrawl answers:

> **How can the source be reliably acquired and transformed?**

## Route and Combine

Choose the primary tool according to the dominant difficulty:

| Need                                  | Start with |
| ------------------------------------- | ---------- |
| Unknown source or fuzzy concept       | Exa        |
| Current, exact, or filterable fact    | Tavily     |
| Structured record or several entities | AnySearch  |
| Difficult page or website structure   | Firecrawl  |

These tools overlap. Do not assign them rigid territories.

Let the question determine the first tool, then let the remaining information gap determine whether another is needed.

Common combinations include:

```text
Semantic discovery:
Exa
→ select sources
→ fetch directly or use Firecrawl for difficult pages

Fresh factual lookup:
Tavily
→ canonical source
→ inspect the relevant content

Structured lookup:
AnySearch
→ select important results
→ inspect original sources

Website investigation:
map
→ select paths
→ scrape
→ crawl only if necessary

Independent verification:
likely answer
→ primary source
→ independent evidence, limitation, or contradiction
```

A second tool should perform a different job.

Do not repeat the same search across providers merely to collect more links.

## Follow a Small Search Loop

1. Identify the exact information gap.
2. Choose the most suitable primary tool.
3. Retrieve a small candidate set.
4. Remove duplicates, mirrors, and low-value summaries.
5. Inspect the strongest original sources.
6. Expand, switch, or combine tools only when the remaining gap justifies it.
7. Stop when further searching is unlikely to change the answer.

Spend effort on the unknowns most likely to affect the result rather than researching every aspect equally.

## Match Sources to Claims

Prefer sources close to the underlying fact:

1. official documentation, source repositories, standards, datasets, filings, and first-party records;
2. maintainers, authors, researchers, institutions, and direct participants;
3. reputable independent reporting and technical analysis;
4. community discussions and secondary summaries.

This is not a universal ranking.

Match the source to the claim. Official documentation may establish an intended contract, while source code, tests, measurements, or direct incident reports may better establish actual behavior.

Use secondary sources to discover, explain, compare, or challenge stronger evidence.

Search snippets locate evidence; they are not evidence by themselves.

## Keep the Discipline

- Start with the tool that best matches the dominant uncertainty.
- Add another provider only when it contributes a different capability.
- Batch independent work, but keep dependent searches sequential.
- Prefer a few inspected sources over many shallow results.
- Use native filters before multiplying queries.
- Map before crawling and keep crawls bounded.
- Escalate acquisition gradually rather than starting with the heaviest method.
- Look for limitations or contradictions when a claim is important or surprising.
- Trace repeated claims to their original source when independence matters.
- Do not repeat a failed strategy without changing the approach.
- Cite sources actually inspected.
- Distinguish sourced facts from inference and judgment.

Search is sufficient when the main uncertainty is resolved, important claims are supported, and another plausible search is unlikely to change the conclusion.

When code inspection, experimentation, measurement, or user input would provide more value than further retrieval, stop searching and move to that step.

## The Way

```text
Let the question reveal the retrieval shape.
Let one tool handle one stage well.
Combine tools only across distinct stages.
Read the source, not merely the result.
Verify in proportion to consequence.
Stop when more searching no longer changes the answer.
```
