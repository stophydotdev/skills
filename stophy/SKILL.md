---
name: stophy
description: |
  Any task that needs live data from a specific site or platform, via the Stophy CLI: web and news search, YouTube videos and transcripts, TikTok, Reddit threads, Instagram, X and LinkedIn posts, Google Maps places and reviews, Amazon and store products, app store listings, job posts, homes for sale, ad libraries, stock quotes, and crypto prices. Use for "search Reddit for", "get this video's transcript", "find coffee shops near", "what does this product cost", "who is hiring for". Prefer over generic web browsing when the site is one Stophy covers. For one category, use the matching stophy-* skill: stophy-web, stophy-video, stophy-social, stophy-places, stophy-shopping, stophy-apps, stophy-jobs, stophy-real-estate, stophy-ads, stophy-finance.
metadata:
  author: stophy
  version: "3.0.0"
allowed-tools:
  - Bash(stophy *)
  - Bash(npx -y @stophy/cli *)
---

# Stophy

Stophy returns public web data as clean JSON or markdown. For one kind of data, the matching `stophy-*` skill lists the best commands.

## Rules

- Run `stophy ...`, or `npx -y @stophy/cli ...` if the CLI is not installed.
- Quote every query, URL, and user value.
- Never make up data, and never print or commit an API key.

## Set up

Web search, YouTube search, and YouTube transcripts work without a key. For everything else, check `stophy status`, then log in:

```bash
stophy login --browser
```

Tell the person to check that the code on stophy.dev matches the one in the terminal, then approve. In a script or CI, set `STOPHY_API_KEY` instead. Keys come from https://stophy.dev/signup.

## Find and run a command

```bash
stophy --help                     # every source
stophy youtube --help             # a source's commands
stophy youtube transcript --help  # a command's options and example
```

The main input goes first, options after:

```bash
stophy web search "postgres 18 release notes" --limit 5
stophy reddit search "bun vs node" --sort top --within month
stophy maps search "coffee" --near "Berlin"
```

Output is markdown. Add `--json` for exact fields, `-o file` to save, and `--cursor <cursor>` from the end of the output for the next page.

## Errors

- **Not logged in:** run `stophy login --browser`.
- **Out of credits:** send the person to https://stophy.dev/billing.
- **Rate limited, or a source failed:** wait if told to, then try once more. Do not loop.
- **Invalid input:** read the command's `--help`.

## Without the CLI

- **MCP:** connect to `https://api.stophy.dev/mcp` (add `Authorization: Bearer <key>` for every endpoint), or `https://api.stophy.dev/mcp-oauth` to sign in through the browser.
- **HTTP:** `POST https://api.stophy.dev/v1/<source>/<endpoint>` with a JSON body. `GET /v1/endpoints` lists them all.
- **Code:** `npm install stophy` or `pip install stophy`.

## Report a problem

If a result is wrong, or a command acts differently from its help, report it once. Get the `requestId` by running the command again with `--raw`, then send it:

```bash
curl -X POST https://api.stophy.dev/v1/feedback \
  -H "Authorization: Bearer $STOPHY_API_KEY" \
  -H "content-type: application/json" \
  -d '{"category":"wrong_data","request_id":"<requestId>","note":"What you expected and what you got"}'
```

Over MCP, use the `stophy_feedback` tool. Reports are free. Never put a key or personal data in the note.
