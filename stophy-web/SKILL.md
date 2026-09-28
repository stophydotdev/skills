---
name: stophy-web
description: |
  Get web search results, news, a site's pages and SEO, domain WHOIS/DNS/tech, email deliverability, and Google Trends. Use for "search the web for", "find recent news about", "what tech does this site run on", "who owns this domain", "is this email address real", "what's trending on Google right now". Web search works without an API key. For social platform posts use stophy-social. For ad libraries use stophy-ads.
metadata:
  author: stophy
  version: "3.0.0"
allowed-tools:
  - Bash(stophy *)
  - Bash(npx -y @stophy/cli *)
---

# stophy web

Web search, news, site structure and SEO, domain and email lookups, and Google Trends.

**Prerequisite:** `stophy web search` works without an API key. Everything else here needs `stophy login --browser` or `STOPHY_API_KEY`. See the stophy skill for setup.

## Quick start
```bash
# no login needed: find pages and sources on a topic
stophy web search "postgres 18 release notes" --limit 10 -o .stophy/search.md

# recent coverage of a topic
stophy web news --query "openai" --within week -o .stophy/news.md

# find contact info published on a site
stophy web contacts "https://www.franklinbbq.com" -o .stophy/contacts.md

# see what a domain uses, and who owns it
stophy domain tech "https://www.allbirds.com" -o .stophy/tech.md
stophy domain whois stripe.com -o .stophy/whois.md

# keyword research: autocomplete and search interest
stophy google suggest "best running shoes" --expand alphabet -o .stophy/suggest.md
```
Run `stophy web --help`, `stophy site --help`, `stophy domain --help`, `stophy email --help`, or `stophy google --help` for every command, and `stophy <source> <command> --help` for all options.

**Done when:** you saved or summarized the lookup with its source URL or domain, and any number or contact detail you report matches the file exactly.

## Tips
- For a full site audit, chain `site map` (every URL) into `site seo` on the URLs that matter.
- `google trends interest` and `google trends related` want the bare keyword, not a URL; `domain whois`/`dns`/`tech` want a domain or URL.
- Page long lists with `--cursor` from the previous result; save anything past a few results with `-o` and read it in parts instead of dumping it into chat.

## See also
- [stophy](../stophy/SKILL.md): setup, errors, and reporting a problem
- [stophy-video](../stophy-video/SKILL.md): YouTube, TikTok, and Kick videos
- [stophy-social](../stophy-social/SKILL.md): posts and profiles on Reddit, X, Instagram, and other platforms
- [stophy-ads](../stophy-ads/SKILL.md): ad libraries, including Google's
