# Repair prompt template

Use this only when the base vehicle identity is already correct and the error is localized.

---

Edit the provided image and correct the localized issue while preserving the correct vehicle identity, overall proportions, composition, and rendering quality.

## Vehicle identity to preserve

- Manufacturer: {{manufacturer}}
- Model: {{model}}
- Generation/chassis: {{generation_or_chassis}}
- Facelift state: {{facelift_state}}
- Year/era: {{year_or_era}}
- Trim/variant: {{trim_or_variant}}
- Market: {{market}}
- Body style: {{body_style}}

## Localized fixes

Correct only these localized issues:
{{fix_list}}

## Preserve these correct features
{{preserve_list}}

## Important restriction

Do **not** use this edit workflow if the headlamp contour, indicator architecture, grille family, market-specific fascia, body style, or generation/facelift is wrong. Those are identity errors and require anchor discard plus regeneration from validated real references.
