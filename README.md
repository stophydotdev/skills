# Stophy skills

[![skills.sh](https://skills.sh/b/stophydotdev/skills)](https://skills.sh/stophydotdev/skills)

Agent skills for live public web data: search, video, social, places, shopping, apps, jobs, real estate, ad libraries, and finance. They run on [the Stophy CLI](https://www.npmjs.com/package/@stophy/cli).

## Install

```bash
npx skills add stophydotdev/skills
```

Or pick specific skills:

```bash
npx skills add stophydotdev/skills --skill stophy-web --skill stophy-video
```

As a Claude Code plugin:

```
/plugin marketplace add stophydotdev/skills
/plugin install stophy-skills
```

## Requirements

- Node.js ≥18
- The CLI: `npm install -g @stophy/cli`, or run it with `npx -y @stophy/cli`
- An API key from [stophy.dev](https://stophy.dev/signup) for every command except web search, YouTube search, and YouTube transcripts

## Authentication

```bash
stophy login --browser           # opens the browser
export STOPHY_API_KEY=st_xxx     # env var also works
```

Treat the API key as a secret. Do not commit it, print it, or paste it into a shared log.

## Included skills

| Skill | Covers |
|-------|--------|
| [`stophy`](./stophy/SKILL.md) | Setup, login, running any command, errors, and reporting a problem |
| [`stophy-web`](./stophy-web/SKILL.md) | Web and news search, site maps and SEO, domain and email lookups, Google Trends |
| [`stophy-video`](./stophy-video/SKILL.md) | YouTube, TikTok, and Kick: videos, transcripts, comments, channels |
| [`stophy-social`](./stophy-social/SKILL.md) | Reddit, Instagram, X, Threads, Bluesky, Mastodon, Telegram, LinkedIn, Pinterest, Tumblr, Snapchat, Quora |
| [`stophy-places`](./stophy-places/SKILL.md) | Google Maps, Tripadvisor, Airbnb, Google Flights |
| [`stophy-shopping`](./stophy-shopping/SKILL.md) | Amazon, Walmart, AliExpress, Shopify stores |
| [`stophy-apps`](./stophy-apps/SKILL.md) | App Store and Google Play listings and reviews |
| [`stophy-jobs`](./stophy-jobs/SKILL.md) | Indeed, LinkedIn, and Upwork job postings |
| [`stophy-real-estate`](./stophy-real-estate/SKILL.md) | Zillow, Redfin, Realtor.com, Rightmove, ImmoScout24 |
| [`stophy-ads`](./stophy-ads/SKILL.md) | Meta, Google, TikTok, LinkedIn, Pinterest, Microsoft, and Snapchat ad libraries |
| [`stophy-finance`](./stophy-finance/SKILL.md) | Stock quotes and history, crypto prices, DEX pairs, wallets |

## For agents

Pick the narrowest skill for the task. Run the command, read the output, then summarize. Never invent data.

## Docs

Full command reference: [docs.stophy.dev](https://docs.stophy.dev)

## License

MIT
