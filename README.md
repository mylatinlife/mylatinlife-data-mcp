# MyLatinLife Data — MCP server

Verified residency, citizenship, tax and banking data for Latin America and Latin Europe, as a remote [MCP](https://modelcontextprotocol.io) server and a plain JSON API.

Published by [MyLatinLife](https://mylatinlife.com). Listed in the official MCP Registry as `com.mylatinlife/data`.

This repository holds the listing and documentation only. The server is hosted; there is nothing to install.

## Connect

| | |
|---|---|
| MCP endpoint | `https://mylatinlife.com/mcp` (Streamable HTTP, stateless, no sign-in) |
| JSON API | `https://mylatinlife.com/api/v1/` |
| OpenAPI 3.1 | `https://mylatinlife.com/api/v1/openapi` |
| Docs | `https://mylatinlife.com/api/` |
| Terms of use | `https://mylatinlife.com/api/v1/terms` |

Add it to any MCP client that supports remote servers:

```json
{
  "mcpServers": {
    "mylatinlife-data": {
      "type": "http",
      "url": "https://mylatinlife.com/mcp"
    }
  }
}
```

Claude Code:

```bash
claude mcp add --transport http mylatinlife-data https://mylatinlife.com/mcp
```

## Tools

All tools are read-only.

| Tool | What it answers |
|---|---|
| `list_countries` | Countries and trade blocs covered, with region, a one-line headline and the topics each has |
| `find_visas` | Digital nomad, retirement and investor visas across countries, cheapest entry first, filtered by the income or investment a person can show |
| `get_country_profile` | Everything on one country: visas, years to permanent residency and citizenship (with legal citations), physical presence rules, foreign-income tax, banking, property tax, cost of living, safety, healthcare, passport power and tax blacklist status |
| `compare_countries` | Side-by-side rows for several countries on one topic |
| `get_program` | The full record of one residency, visa or citizenship program, with its country summary |
| `get_recent_changes` | Dated log of what changed in the data: visa minimums, fees, years to citizenship, blacklist listings, new coverage |
| `check_tax_blacklists` | Which tax and AML blacklists or greylists (EU, OECD, FATF, national lists) a jurisdiction is on |
| `about_data` | Every topic with row counts and verification dates, coverage, terms and how to cite (always free) |
| `get_latest_articles` | The newest MyLatinLife articles and guides, optionally matching a search (always free) |
| `get_dataset` | Every row of one topic (commercial key) |

The JSON API exposes the same tools as GET endpoints, for example:

```
https://mylatinlife.com/api/v1/find_visas?visa_type=digital_nomad&max_minimum_usd=2000
```

Example questions an agent can answer with it:

- "Which digital nomad visas in Latin America can I get on $3,000 a month?"
- "How many years from residency to citizenship in Paraguay, and what's the legal basis?"
- "Compare the tax systems of Panama, Uruguay and Costa Rica for foreign income."
- "Is Panama on the EU tax blacklist?"
- "What changed in Paraguay's residency rules recently?"

## Access

Without a key, each caller gets a one-item preview a day; `about_data` and `get_latest_articles` are always free. A commercial key gives complete results, full datasets and the commercial licence; see the terms page for the plan and fair-use limits.

## The data

Every row carries a `last_verified` date and its sources or methodology. Answers include attribution and a disclaimer: this is general information, not legal or tax advice. Rules change, so check the cited sources or speak to [MyLatinLife](https://mylatinlife.com) about your situation.

Problems with the server or the data: open an issue here.

## Licence

Free to use with attribution and a link to mylatinlife.com. No bulk resale or republishing as a competing dataset. Full terms: https://mylatinlife.com/api/v1/terms
