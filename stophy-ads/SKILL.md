---
name: stophy-ads
description: |
  Search ad libraries: Meta (Facebook/Instagram), Google, TikTok, LinkedIn, Pinterest, Microsoft, and Snapchat. Use for "what ads is this brand running", "find ads for this competitor", "what's this company advertising on Facebook", "get this ad's details", "find advertisers in this ad library". For a brand's organic posts (not ads) use stophy-social or stophy-video.
metadata:
  author: stophy
  version: "3.0.0"
allowed-tools:
  - Bash(stophy *)
  - Bash(npx -y @stophy/cli *)
---

# stophy ads

Search the public ad libraries of Meta, Google, TikTok, LinkedIn, Pinterest, Microsoft, and Snapchat.

**Prerequisite:** every command here needs `stophy login --browser` or `STOPHY_API_KEY`. See the stophy skill for setup.

## Quick start
```bash
# a brand's active Facebook and Instagram ads
stophy meta ads search nike --limit 20 -o .stophy/meta-ads.md

# a domain's Google ads
stophy google ads search --domain nike.com --limit 25 -o .stophy/google-ads.md

# a keyword or brand's TikTok or LinkedIn ads
stophy tiktok ads search --query adidas --limit 12 -o .stophy/tiktok-ads.md
stophy linkedin ads search --query software -o .stophy/linkedin-ads.md

# ads in one country's Pinterest library
stophy pinterest ads search DE --limit 24 -o .stophy/pinterest-ads.md

# one ad's full details, by ID from a search result
stophy meta ads ad "123456789012345" -o .stophy/ad.md
```
Run `stophy meta ads --help`, `stophy google ads --help`, `stophy tiktok ads --help`, `stophy linkedin ads --help`, `stophy pinterest ads --help`, `stophy microsoft ads --help`, or `stophy snapchat ads --help` for every command, and `stophy <source> ads <command> --help` for all options.

**Done when:** you named the specific advertiser, ad copy, and platform, with the ad's ID or link, not a generic "they run ads."

## Tips
- `meta ads page` and `google ads advertisers`/`microsoft ads advertisers` find every ad from one advertiser once you have their page or name.
- `pinterest ads search` and `snapchat ads search` take a country code or advertiser name as the main input, not a free-text query. Check `--help` for which.
- Page long result lists with `--cursor`; save anything past a handful of ads with `-o` and read it in parts.

## See also
- [stophy](../stophy/SKILL.md): setup, errors, and reporting a problem
- [stophy-social](../stophy-social/SKILL.md): a brand's organic posts, not paid ads
- [stophy-video](../stophy-video/SKILL.md): a channel's organic videos, not TikTok ads
