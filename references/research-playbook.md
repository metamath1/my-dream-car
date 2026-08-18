# Research playbook

## Goal

Build enough evidence to depict the exact requested car and print only defensible specifications.

## Research principle

The problem is not merely “search more.” The problem is often “filter better.”
The workflow emphasizes provenance, internal consistency, conflict quarantine, and user-confirmed ground truth.

## Identity resolution

Look for these clues in the request or intake answers:

- year
- generation/chassis code
- facelift wording
- trim/engine
- market/region
- body style
- must-match detail supplied by the user

If ambiguity remains significant after one short intake round, either ask one focused follow-up or proceed with clearly documented assumptions.

## Search strategy

Use several specific queries rather than one broad query.

Typical patterns:
- `"<year> <manufacturer> <model> official"`
- `"<manufacturer> <model> brochure"`
- `"<manufacturer> <model> press photo"`
- `"<generation/chassis> front three quarter"`
- `"<model> pre facelift"`
- `"<model> facelift"`
- `"<market name> <trim> official"`

For recent vehicles, official launch assets are especially valuable.
For older vehicles, brochure scans and period press photos are especially valuable.

## Multi-angle reference coverage

Do not let a strong front image substitute for the rest of the vehicle.

For strict grounding, aim to collect:
- front or front three-quarter
- side/profile
- rear or rear three-quarter

The side/profile view is the primary evidence for:
- front-fender shoulder and wheel-arch shape
- rear-fender / quarter-panel volume
- door surface planes and character lines
- rocker / side-skirt geometry
- glasshouse, C-pillar and rear-quarter-window silhouette

The rear three-quarter view is especially useful for confirming whether the rear fender projects outward as a real body volume rather than being flattened into a generic sedan side.

If side-body geometry is a published or visually obvious design signature, missing side coverage is a research gap that should be repaired before generation.

## Provenance requirements

For every accepted positive reference, record:
- source URL
- source name
- claimed market
- claimed year or era
- body style
- view angle
- identity-critical features observed
- status and reason

An image whose source, market, or era cannot be recovered should not become the primary front-fascia reference when market-specific differences exist.

## Conflict handling

If references conflict on identity-critical features:

- do not send all of them to the image model
- quarantine the conflicting image
- verify its market/year/body style
- prefer the set that is corroborated by independent sources and, when available, user-confirmed ground truth

## Within-set consistency gate

Before generation, references inside the same variant set must agree on the geometry visible in their respective angles:
- headlamp outer contour
- indicator relationship
- grille outline
- bumper openings
- badge placement relationship
- front-fender and wheel-arch form
- rear-quarter / rear-fender volume
- side character-line and surface-plane structure
- glasshouse / C-pillar silhouette

If not, stop and repair the reference set first.

## User-confirmed reference priority

A user-confirmed exact-variant photo outranks search images.
If a search image conflicts with the user-confirmed photo, discard or quarantine the search image.

## Specification research

Search the exact variant. Include year, market, engine, and transmission when relevant.
Beware of:
- PS vs hp vs bhp
- mph vs km/h
- 0–60 mph vs 0–100 km/h
- manual vs automatic performance
- regional output differences

When a value remains uncertain, omit it and substitute another verified field.
