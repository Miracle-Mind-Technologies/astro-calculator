# Status

**Last updated:** 2026-10-24 (docs trim; history in `docs/archive/status-history-2026-10.md`)

## Needs Matthew

- none

## What works

- Next.js 16, TypeScript strict, AGPL-3.0; Swiss Ephemeris wrapper with auto-download of data files
- **16 REST endpoints live** at `/api/v1/*` with Zod validation (transit, synastry, composite, sky-weather, returns suites included)
- Calculators (verified against external references):
  - **Astrology**: natal positions, house cusps (7 systems), aspects, Part of Fortune, South Node
  - **Astrocartography**: MC/IC/AC/DC lines per planet, parans
  - **Human Design**: type, profile, gates, channels, centers, authority, incarnation cross, Variables
  - **Gene Keys**: all 11 Hologenetic Profile spheres
  - **Life Path** numerology and **Destiny Card** (Robert Lee Camp Solar Spread)
  - **Returns**: solar return any year; Sun–Saturn first return on/after a datetime, optionally relocated; secondary progressions
  - **Transits**: sky snapshot, transit-to-natal overlay, multi-year event scanner; per-aspect `orbs` override merged over defaults on all three
  - **Synastry** (shared `computeOverlay` core) and **Composite** (midpoints, 2–10 births)
  - **Transit combination matrix**: 13 × 19 × 6 with sign/house context; stable `comboKey`; 17,784-key manifest
  - **Sky weather**: stations, moon phases, ingresses, eclipses (up to 20-year horizon)
  - **Aspect patterns** (stellium, grand trine, T-square, grand cross, yod, kite, mystic rectangle) and **chart ruler**
- `/chart` UI, `/sky` page, Swagger UI at `/docs`, OpenAPI 3.1 at `/api/openapi.json` (request bodies contract-tested against Zod)
- Accuracy anchored in three layers, each with a normative doc:
  - L1 ephemeris vs JPL Horizons (`docs/accuracy.md`): 0.005″ RMS over 1800–2005, fixtures harvested offline
  - L2 time and houses (`docs/time-conventions.md`, `docs/chart-conventions.md`)
  - L3 interpretive conventions (`docs/aspect-conventions.md`)
- Test suite: 1381 tests across 34 files (as of 2026-08-14)
- Polar charts report the house system that actually produced the cusps (`houses.system` / `houses.requestedSystem`) and flag retrograde wheels
- Pre-1800 births served from Moshier, labelled `ephemeris: "moshier"`; Chiron reported in `unavailableBodies`
- Accuracy findings F1–F11: all actionable ones fixed (details in the archive)

## In progress

- (none)

## Next

- Davison chart variant
- Cards of Destiny Planetary Ruling Card + Karma Cards (needs reference table)
- Topocentric flag (concurrency design needed for sweph's global `set_topo`)
- Sidereal zodiac with selectable ayanamsa

## Recent changes

| Date | Change |
|---|---|
| 2026-10-24 | Docs trim: CLAUDE.md CI section updated (CI is off); STATUS/TODO cut to current state, history moved to `docs/archive/` |
| 2026-08-14 | Orphaned `mira/env-validation` and `mira/claude-md-refresh` branches pushed to origin; both already merged (PRs #4, #5), kept as record |
| 2026-08-13 | `npm run lint` fixed for built git worktrees (PR #28/#29) |
| 2026-08-13 | OpenAPI request bodies corrected on nine endpoints + contract test (PR #26/#27) |
| 2026-08-13 | Synastry orb-override test made able to fail (PR #24/#25) |
| 2026-08-13 | `orbs` override on `/api/v1/astrology/transits` (PR #22/#23) |

## Known limitations

- No rate limiting yet (planned: Vercel Firewall WAF); no caching layer (planned: LRU + Vercel Runtime Cache)
- Tropical and geocentric only (sidereal, topocentric deferred)
- HD/GK ignore lat/lon; only the UT instant matters
- Pre-1800 positions from Moshier: arc-second for Sun/planets, coarser for the Moon; no Chiron
- Above the polar circles Placidus/Koch are undefined and Regiomontanus/Campanus can run retrograde (reported, not hidden); only `equal` and `whole_sign` stay ordered at every latitude
