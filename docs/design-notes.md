# Design notes

## Vehicle fidelity

Vehicle identity is resolved before poster styling. Generation, facelift state, body style, regional-market differences, and other identity-critical details are treated as hard constraints.

## Intake

Every new poster job confirms two user preferences before the first image unless they were already supplied: reference-image availability and exterior color (or series color policy). Other questions remain adaptive and are asked only when they materially affect identity or factual accuracy.

## Reference handling

User-confirmed images have the highest priority. Search references should have recoverable provenance and must agree on identity-critical geometry before they are passed to image generation.

## Shape anchor

Accuracy-sensitive requests use a clean shape-anchor image before poster styling. Validation covers both front identity and whole-body geometry. When a vehicle has distinctive side surfacing, front/rear fender volume, wheel arches, door planes, rocker treatment and rear-quarter geometry are hard-gate features rather than decorative details.

## Repair policy

Localized errors may be repaired by editing. Identity-critical errors require discarding the anchor and regenerating from validated references.

## Poster sets

For paired or multi-poster requests, the first accepted poster becomes the layout anchor. Canvas size, typography zones, hero-car framing, whitespace, and the bottom specification strip should remain visually aligned across the set.

Vehicle orientation is also part of the layout lock. The default series orientation is a front three-quarter view with the nose pointing toward canvas left. All posters in the set should keep that direction unless the user explicitly requests another shared direction.
