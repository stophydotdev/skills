---
name: stophy-real-estate
description: |
  Get homes for sale, for rent, or sold from Zillow, Redfin, Realtor.com, Rightmove, and ImmoScout24. Use for "find homes for sale in", "what's this house worth", "apartments for rent in this city", "recently sold homes near", "flats to rent in the UK or Germany". For hotels, stays, and attractions use stophy-places.
metadata:
  author: stophy
  version: "3.0.0"
allowed-tools:
  - Bash(stophy *)
  - Bash(npx -y @stophy/cli *)
---

# stophy real estate

Search homes for sale, for rent, or sold across US, UK, and German listing sites.

**Prerequisite:** every command here needs `stophy login --browser` or `STOPHY_API_KEY`. See the stophy skill for setup.

## Quick start
```bash
# US homes for sale, with filters
stophy zillow search --location "Austin, TX" --status forSale --bedrooms.min 3 -o .stophy/zillow.md

# same search, cross-checked on Redfin or Realtor.com
stophy redfin search "Seattle, WA" --status forSale -o .stophy/redfin.md
stophy realtor search "Denver, CO" --status forSale -o .stophy/realtor.md

# UK or German listings
stophy rightmove search Manchester --status forSale -o .stophy/rightmove.md
stophy immoscout search Berlin --type apartmentRent -o .stophy/immoscout.md

# one home's price, details, and estimate, by ID from a search result
stophy zillow property "12345678_zpid" -o .stophy/property.md
```
Run `stophy zillow --help`, `stophy redfin --help`, `stophy realtor --help`, `stophy rightmove --help`, or `stophy immoscout --help` for every command, and `stophy <source> <command> --help` for all options.

**Done when:** you named the specific address, price, and listing link, not a generic price range for the area.

## Tips
- Search first to get a property ID, then call `property`/`listing` on it for the full price history and estimate.
- Each site's `--homeTypes`/`--propertyTypes` and `--status` values differ slightly. Check `--help` before filtering rather than guessing a value.
- Page long result lists with `--cursor`; save anything past a handful of listings with `-o` and read it in parts.

## See also
- [stophy](../stophy/SKILL.md): setup, errors, and reporting a problem
- [stophy-places](../stophy-places/SKILL.md): stays, hotels, and attractions, not homes for sale or rent
