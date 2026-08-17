# Shape-anchor prompt template

Use this before the final poster whenever the car is accuracy-sensitive.

---

Create a highly accurate **vehicle shape-anchor image** of **{{exact_model_name}}**.

This is **not** the final poster. The goal is to lock in the correct real-world exterior shape before poster styling.

## Image roles

If reference images are supplied:
- primary ground-truth reference: highest priority, especially if user-confirmed
- secondary corroborating references: support exact geometry only
- quarantined or conflicting references: do not use

## Identity

- Manufacturer: {{manufacturer}}
- Model: {{model}}
- Generation/chassis: {{generation_or_chassis}}
- Facelift state: {{facelift_state}}
- Year/era: {{year_or_era}}
- Trim/variant: {{trim_or_variant}}
- Market: {{market}}
- Body style: {{body_style}}
- Exterior color: {{exterior_color}}

## Highest priority: match the actual car

Depict the factory production vehicle as accurately as possible.

Must-match shape-critical notes:
{{shape_critical_notes}}

Negative constraints — do not drift into these mistakes:
{{negative_constraints}}

## Camera and presentation

- front three-quarter view unless another angle better exposes the identity-critical geometry
- realistic natural lens, not an exaggerated wide angle
- neutral light studio or clean neutral background
- no giant typography
- minimal styling effects
- full car visible and large enough to inspect details clearly
- emphasize readability of lamps, grille, bumper, wheel arches, side surfacing, and rear quarter
- include a front showroom plate reading `{{showroom_plate_text}}`

## Rendering goal

Photoreal, factory-correct, restrained, reference-friendly. No concept-car reinterpretation, no aftermarket parts, no incorrect market mixing.
