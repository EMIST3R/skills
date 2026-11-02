---
name: content-relevance
description: >-
  Scores distinct facts already gathered in intake from 0 to 3 into
  contentItems[] and requires score 3 facts on the public site. Sub-skill of
  every local build: local-build-from-intake calls it after intake and before
  the site spec. No re-crawl and no paid API.
---

# Content relevance

Sub-skill of every build. [`local-build-from-intake`](../local-build-from-intake/SKILL.md) calls this **after intake and before the site spec**, including file intake. It is not a command the operator types.

Public copy: https://github.com/EMIST3R/skills/tree/main/skills/content-relevance

## Low impact

Pages are already fetched. Do **not** crawl again. Do **not** score every sentence. Do **not** call a paid API.

Read facts already in hand:

- [`intake/extracted.json`](../../../intake/extracted.json) — `claims[]`, `services[]`, `business`, `contact`, `documentExtractions[]`
- [`intake/raw/`](../../../intake/raw/) snippets when present
- page text from the intake that just ran

Write `contentItems[]` back onto `extracted.json`. One row per distinct fact. Leave the rest of the extraction in place.

## Row

| Field | Meaning |
|-------|---------|
| `id` | Stable slug, unique in the array. Later steps keep this id in `site.json` or a page file. |
| `text` | Short fact. Not a paragraph and not a slogan. |
| `sourceUrl` | Page URL or file path the fact came from. |
| `score` | Integer 0–3. |
| `placement` | Section it belongs on: `services`, `about`, `faq`, `contact`, `hours`, or a new page such as `courses`. |

## Scores

| Score | Meaning | Public site |
|-------|---------|-------------|
| 3 | A visitor needs it to choose or contact: offerings, prices, who it is for, credentials, hours, place, programs | Must appear |
| 2 | Useful proof or detail: FAQ, about, test centers, teacher facts | Include if it fits a section |
| 1 | Thin or duplicate: old posts, repeated nav, boilerplate | Intake only |
| 0 | Not about the business: cookies, ads, unrelated widgets | Drop |

Score **0**: do not add a row. Drop it.

Scores stay in intake. Never render a score on the public page. Public copy is visitor voice: no “the old site says…”, “Facebook post…”, or other source attribution. Provenance stays in `sourceUrl` and `claims[]`.

## What this skill does not do

- It does not edit the site spec, scaffold, or `clients/`.
- Score 3 mapping is [`intake-to-site-spec`](../intake-to-site-spec/SKILL.md). Rendering is [`scaffold-client-site`](../scaffold-client-site/SKILL.md).
- Homepage hero stays within [`local-web-design`](../local-web-design/SKILL.md) hero rules. Extra facts go in the matching section below. Do not omit a score 3 item to keep the homepage sparse.

## Unfetched pages

Intake records URLs it did not fetch as `pages_not_fetched:<absolute-url>` in `missing[]`. Leave those entries. Do not invent facts for pages that were not fetched.
