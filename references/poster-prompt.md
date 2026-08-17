# Final poster prompt template

Use this only after a shape anchor has passed all hard gates.

---

Create a premium vertical automotive poster featuring **{{exact_model_name}}**.

## Image roles

If reference images are supplied:
- style reference image: use only for layout/style inspiration
- validated shape-anchor image: highest-priority fidelity reference for the car itself
- a prior finished poster from the same requested set: treat it as the layout anchor and preserve its canvas size, repeated element positions, and whitespace system
- additional accepted research references: secondary vehicle-fidelity references
- quarantined/conflicting references: do not use

## Vehicle fidelity — highest priority

Depict the real production vehicle accurately.

Vehicle identity:
- Manufacturer: {{manufacturer}}
- Model: {{model}}
- Generation/chassis: {{generation_or_chassis}}
- Facelift state: {{facelift_state}}
- Year/era: {{year_or_era}}
- Trim/variant: {{trim_or_variant}}
- Market: {{market}}
- Body style: {{body_style}}
- Exterior color: {{exterior_color}}

Must-match shape-critical notes:
{{shape_critical_notes}}

Negative constraints:
{{negative_constraints}}

## Composition

- tall vertical poster, approximately 9:16
- hero vehicle centered in the middle/lower-middle area
- front three-quarter view unless another researched angle is better for identity
- natural perspective without distorted proportions
- vehicle large enough that the exact model-specific features are obvious
- visible front showroom plate reading `{{showroom_plate_text}}`

## Visual style

Use the bundled `assets/poster-style-reference.png` as inspiration while creating an original design.

- bright white / very light gray studio environment
- soft premium commercial lighting
- subtle floor reflection
- enormous pale background typography behind the vehicle
- a small, widely spaced uppercase line at the top
- restrained tire marks and light haze if suitable
- clean monochrome typography and generous whitespace
- elegant, brochure-like, minimal

## Typography

Top small text:
`{{top_line}}`

Large pale background word:
`{{background_word}}`

Lower main title:
`{{main_title}}`

Short description:
`{{one_sentence_description}}`

Bottom specification strip: use four evenly spaced cells separated by thin vertical rules.

{{spec_cell_1_label}}: {{spec_cell_1_value}}
{{spec_cell_2_label}}: {{spec_cell_2_value}}
{{spec_cell_3_label}}: {{spec_cell_3_value}}
{{spec_cell_4_label}}: {{spec_cell_4_value}}

All displayed text must be legible, correctly spelled, and consistent in units.

## Layout lock for paired or multi-poster sets

If a previous finished poster from the same set is provided, preserve these elements as closely as possible:

- exact canvas size and aspect ratio
- top-line position
- background-word size and position
- hero-car placement zone
- main-title baseline and approximate size
- description block placement
- bottom rule and four-cell spec-strip placement
- overall whitespace rhythm

Only the car identity, variant-specific wording, and verified specs should change.
