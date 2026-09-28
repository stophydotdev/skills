---
name: stophy-finance
description: |
  Get stock quotes, price history, company profiles, and crypto prices, including DEX pairs and wallet balances. Use for "what's this stock trading at", "how has this stock moved this year", "what's bitcoin's price", "what's trending in crypto right now", "what's in this wallet". For general company news outside stocks use stophy-web.
metadata:
  author: stophy
  version: "3.0.0"
allowed-tools:
  - Bash(stophy *)
  - Bash(npx -y @stophy/cli *)
---

# stophy finance

Stock quotes and history, and crypto coin prices, DEX pairs, and wallet balances.

**Prerequisite:** every command here needs `stophy login --browser` or `STOPHY_API_KEY`. See the stophy skill for setup.

## Quick start
```bash
# live quotes for one or more tickers
stophy finance quote --symbols AAPL,MSFT -o .stophy/quotes.md

# a stock's price over time
stophy finance history AAPL --within month -o .stophy/history.md

# find a ticker and its recent news
stophy finance search tesla -o .stophy/finance-search.md

# a coin's price, supply, and details
stophy crypto coin bitcoin -o .stophy/coin.md

# what's trending across crypto right now
stophy crypto trending -o .stophy/trending.md

# a wallet's balance and tokens
stophy crypto wallet --chain ethereum --wallet "0xd8dA6BF26964aF9D7eEd9e03E53415D37aA96045" -o .stophy/wallet.md
```
Run `stophy finance --help` or `stophy crypto --help` for every command, and `stophy <source> <command> --help` for all options.

**Done when:** you named the specific price, symbol, or balance and its timestamp, not a stale or rounded figure.

## Tips
- `crypto coin` takes a coin's slug (`bitcoin`, not `BTC`); `finance quote`/`history` take the ticker symbol instead.
- Use `crypto dex search` for a token that isn't on a major exchange yet, and `crypto pump coins` for newly launched pump.fun tokens.
- Page long lists with `--cursor`; save anything past a handful of rows with `-o` and read it in parts.

## See also
- [stophy](../stophy/SKILL.md): setup, errors, and reporting a problem
- [stophy-web](../stophy-web/SKILL.md): general news search, not stock-specific
