---
name: routing
description: Calculate travel times, distances, and directions between locations. Supports driving, cycling, and walking. Use when the user asks how long it takes to get somewhere, for directions, or anything related to travel time and routes.
allowed-tools: Bash(route-cli:*)
---

# Travel Time & Directions

Calculate travel times, get directions, and analyze reachability using OpenRouteService.

## Quick start

```bash
route-cli time "Vienna" "Graz"                    # Quick travel time
route-cli directions "Vienna" "Graz"               # Full turn-by-turn
route-cli time "Vienna" "Graz" foot-walking         # Walking time
```

## Commands

### Travel time (quick)

```bash
route-cli time <from> <to> [profile]
```

Profiles: `driving-car` (default), `cycling-regular`, `foot-walking`, `driving-hgv`

### Directions (detailed)

```bash
route-cli directions <from> <to> [profile]
```

Returns duration, distance, and turn-by-turn steps.

### Geocode

```bash
route-cli geocode <place_name>                     # Look up coordinates
```

### Matrix (compare multiple destinations)

```bash
route-cli matrix <place1> <place2> [place3...]     # Time between all pairs
route-cli matrix "Vienna" "Graz" "Linz" --profile cycling-regular
```

### Isochrone (reachability)

```bash
route-cli isochrone <place> <minutes> [profile]    # Area reachable in N minutes
```

## Location formats

Both place names and coordinates work:
```bash
route-cli time "Stephansplatz, Vienna" "Schönbrunn"
route-cli time 16.3738,48.2082 15.4395,47.0707
```

## Examples

```bash
# How long from Vienna to Graz by car?
route-cli time "Vienna" "Graz"

# Compare driving vs cycling
route-cli time "home" "office" driving-car
route-cli time "home" "office" cycling-regular

# Which airport is closest?
route-cli matrix "Vienna" "Vienna Airport" "Bratislava Airport" "Budapest Airport"

# What can I reach in 30 minutes by car?
route-cli isochrone "Vienna" 30
```
