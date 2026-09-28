---
name: stophy-apps
description: |
  Get app listings, details, reviews, and top charts from the Apple App Store and Google Play. Use for "find apps for", "what do reviews say about this app", "what's trending in the App Store", "get this app's rating and description", "compare this app on iOS and Android". For physical products use stophy-shopping.
metadata:
  author: stophy
  version: "3.0.0"
allowed-tools:
  - Bash(stophy *)
  - Bash(npx -y @stophy/cli *)
---

# stophy apps

Search, read, and review apps on the App Store and Google Play.

**Prerequisite:** every command here needs `stophy login --browser` or `STOPHY_API_KEY`. See the stophy skill for setup.

## Quick start
```bash
# search either store by keyword
stophy appstore search "photo editor" --limit 20 -o .stophy/appstore-search.md
stophy googleplay search "photo editor" -o .stophy/googleplay-search.md

# one app's details, by its numeric ID or package name
stophy appstore app 284882215 -o .stophy/appstore-app.md
stophy googleplay app com.spotify.music -o .stophy/googleplay-app.md

# what users say
stophy appstore reviews 284882215 --sort helpful --limit 40 -o .stophy/reviews.md

# what's currently popular
stophy appstore top --chart free --limit 50 -o .stophy/top.md
```
Run `stophy appstore --help` or `stophy googleplay --help` for every command, and `stophy <source> <command> --help` for all options.

**Done when:** you named the specific app, rating, and store, quoting reviews rather than paraphrasing sentiment.

## Tips
- App Store IDs are numeric (from a search result or the App Store URL); Google Play uses the package name (e.g. `com.spotify.music`).
- `appstore top` needs no app ID; it's the current charts for a device and country.
- Page long review lists with `--cursor`; save anything past a handful with `-o` and read it in parts.

## See also
- [stophy](../stophy/SKILL.md): setup, errors, and reporting a problem
- [stophy-shopping](../stophy-shopping/SKILL.md): physical products, not apps
