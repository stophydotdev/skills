---
name: stophy-shopping
description: |
  Get product listings, prices, and best sellers from Amazon, Walmart, AliExpress, and any Shopify store. Use for "what does this product cost", "find the cheapest", "what's selling well in this category", "does this store carry", "compare prices for this item". For app listings use stophy-apps. For places and local businesses use stophy-places.
metadata:
  author: stophy
  version: "3.0.0"
allowed-tools:
  - Bash(stophy *)
  - Bash(npx -y @stophy/cli *)
---

# stophy shopping

Search products and prices on Amazon, Walmart, AliExpress, and Shopify stores.

**Prerequisite:** every command here needs `stophy login --browser` or `STOPHY_API_KEY`. See the stophy skill for setup.

## Quick start
```bash
# search a marketplace by keyword
stophy amazon search --query "wireless earbuds" --sort priceLow -o .stophy/amazon.md

# one product's price and details
stophy amazon product B08N5WRWNW -o .stophy/product.md

# what's popular in a category
stophy amazon bestsellers electronics --limit 50 -o .stophy/bestsellers.md

# same idea on Walmart or AliExpress
stophy walmart search "air fryer" --sort priceLow -o .stophy/walmart.md
stophy aliexpress search "phone case" --limit 60 -o .stophy/aliexpress.md

# any Shopify store's catalog
stophy shopify products allbirds.com --limit 50 -o .stophy/shopify.md
```
Run `stophy amazon --help`, `stophy walmart --help`, `stophy aliexpress --help`, or `stophy shopify --help` for every command, and `stophy <source> <command> --help` for all options.

**Done when:** you named the specific product, price, and store, not a generic price range.

## Tips
- `search` returns product IDs; feed one into `product` for full details, price, and rating.
- `shopify products`/`collections`/`store` take the store's domain (e.g. `allbirds.com`), not a search query: Shopify has no full-text product search.
- Page long result lists with `--cursor`; save anything past a handful of items with `-o` and read it in parts.

## See also
- [stophy](../stophy/SKILL.md): setup, errors, and reporting a problem
- [stophy-apps](../stophy-apps/SKILL.md): App Store and Google Play listings, not physical products
- [stophy-places](../stophy-places/SKILL.md): local businesses and stays, not products
