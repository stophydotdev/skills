---
name: stophy-places
description: |
  Get places, hotels, attractions, stays, and flights: Google Maps search and reviews, Tripadvisor ratings, Airbnb listings and calendars, and Google Flights prices. Use for "find coffee shops near", "what do reviews say about this restaurant", "find a place to stay in", "is this Airbnb available", "flights from JFK to LAX". For homes for sale or rent use stophy-real-estate. For hotel or store product prices use stophy-shopping.
metadata:
  author: stophy
  version: "3.0.0"
allowed-tools:
  - Bash(stophy *)
  - Bash(npx -y @stophy/cli *)
---

# stophy places

Search places on Google Maps and Tripadvisor, Airbnb stays, and flights on Google Flights.

**Prerequisite:** every command here needs `stophy login --browser` or `STOPHY_API_KEY`. See the stophy skill for setup.

## Quick start
```bash
# find places by keyword and location
stophy maps search coffee --near "Austin, TX" --limit 20 -o .stophy/maps.md

# reviews for one place
stophy maps reviews "ChIJrTLr-GyuEmsRBfy61i59si0" --sort newest --limit 20 -o .stophy/reviews.md

# hotels, restaurants, or attractions
stophy tripadvisor search "Eiffel Tower" --type attractions -o .stophy/tripadvisor.md

# available stays for a date range
stophy airbnb search "Lisbon, Portugal" --checkIn 2026-11-10 --checkOut 2026-11-15 -o .stophy/airbnb.md

# flight prices and times
stophy googletravel flights --origin JFK --destination LAX --departDate 2026-11-01 -o .stophy/flights.md
```
Run `stophy maps --help`, `stophy tripadvisor --help`, `stophy airbnb --help`, or `stophy googletravel --help` for every command, and `stophy <source> <command> --help` for all options.

**Done when:** you named the specific place, rating, price, or flight and its source, not a generic "there are several options."

## Tips
- `maps search` takes a plain place name; `maps place`/`maps reviews` and `tripadvisor place`/`reviews` want the ID from a prior search, not the name again.
- `airbnb calendar` shows which dates are actually open before you commit to a `checkIn`/`checkOut` search.
- Page long review or listing lists with `--cursor`; save anything past a handful of results with `-o` and read it in parts.

## See also
- [stophy](../stophy/SKILL.md): setup, errors, and reporting a problem
- [stophy-real-estate](../stophy-real-estate/SKILL.md): homes for sale or rent, not stays or attractions
- [stophy-shopping](../stophy-shopping/SKILL.md): product prices, not places
