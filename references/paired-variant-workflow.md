# Paired-variant workflow

Use this whenever the user requests two or more sibling variants such as:
- pre-facelift / facelift
- early / late
- domestic / export
- sedan / hatchback under one name

## Rules

1. Each variant gets its own research record.
2. Each variant gets its own accepted reference set.
3. Each variant gets its own shape anchor generation call.
4. Each variant must be validated both against its own references and against the sibling variant.

## Differential gate

Fail the pair if the two outputs differ mainly by:
- color
- wheels
- typography
- lighting

Pass the pair only when the visible differences expected from research actually appear in the rendered cars.

## Do-not-cross-copy list

For each pair, write a short list of features that must not leak from A to B or B to A.

Example categories:
- lamp outer contour
- indicator architecture
- grille family
- bumper opening layout
- taillamp family

## Poster-series consistency rule

After variant A and B have passed their shape-anchor checks, generate the first final poster and use it as the layout anchor for the companion poster. The two final posters should look like they belong to one design system, not two loosely similar layouts.

Check that the title baseline, background word, car placement, and bottom spec strip are aligned across the pair.
