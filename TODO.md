# TODO

Completed items and their write-ups: `docs/archive/todo-done-2026-10.md`.

## Critical (blocks production)

- (none)

## Bugs (broken functionality)

- (none)

## Tech Debt (code quality)

- [ ] Additional strict-lint pass: zero warnings is enforced locally; consider narrower ESLint overrides file-by-file if needed.

## Enhancements (nice to have)

- [ ] Davison chart endpoint (time/space-midpoint variant; midpoint composite shipped 2026-07-24).
- [ ] Client-side test coverage for new UI (Transits tab, Sky page, Synastry sub-tab, planet/aspect filter chips).
- [ ] HD PHS sub-labels: Digestion labels like "Buzzing (Nervous Touch)" and "Direct"/"InDirect"; map color+tone+base sub-classifications (needs lookup tables per variable).
- [ ] Verify J (Juxtaposition) cross names against MyBodyGraph (RA/LA structurally verified; J entries single-source).
- [ ] Sabian Symbols: 360-degree symbolic image per zodiac degree (needs the canonical 360-entry table).
- [ ] Cards of Destiny Planetary Ruling Card + Karma Cards (needs verified lookup tables).
- [ ] Topocentric flag: design concurrency for sweph's global `set_topo` state (mainly affects Moon, ~1°).
- [ ] Sidereal zodiac with selectable ayanamsa (Lahiri / Krishnamurti / Fagan-Bradley).
- [ ] Caching layer (in-memory LRU + Vercel Runtime Cache).
- [ ] Rate limiting via Vercel Firewall WAF rules.
- [ ] OpenAPI response schemas: responses are description-only, so consumers can't codegen response types; ideally derive from Zod output schemas.
- [ ] SDK packages (`@astro-calculator/client-ts`, Python).
- [ ] Render astrocartography lines on an interactive world map in `/chart`.
- [ ] Cross-validate Mandela fixture values against Astrodienst once its Cloudflare gate is passable (currently seeded from our sweph-based calculator).
