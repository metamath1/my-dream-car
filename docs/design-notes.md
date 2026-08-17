# Design notes

## Vehicle fidelity

Vehicle identity is resolved before poster styling. Generation, facelift state, body style, regional-market differences, and other identity-critical details are treated as hard constraints.

## Intake

Clarification is adaptive rather than mandatory. A grouped question is used when uncertainty can materially change the vehicle appearance or printed specifications.

## Reference handling

User-confirmed images have the highest priority. Search references should have recoverable provenance and must agree on identity-critical geometry before they are passed to image generation.

## Shape anchor

Accuracy-sensitive requests use a clean shape-anchor image before poster styling. Headlamp shape, indicator architecture, grille, bumper topology, body surfacing, and other critical details must pass validation.

## Repair policy

Localized errors may be repaired by editing. Identity-critical errors require discarding the anchor and regenerating from validated references.

## Poster sets

For paired or multi-poster requests, the first accepted poster becomes the layout anchor. Canvas size, typography zones, hero-car framing, whitespace, and the bottom specification strip should remain visually aligned across the set.

Vehicle orientation is part of the series layout lock. Unless the user explicitly requests another direction, every vehicle in the same series should use a front three-quarter view with the nose pointing toward canvas left. Do not mirror individual posters within the same set.
