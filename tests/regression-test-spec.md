# Regression test spec: Kalos T200 Korean pre-facelift / facelift

This regression test captures a known Korean pre-facelift Kalos failure in which a conflicting front reference overrode the correct identity.

## Required behavior

- Ask the user for reference images or permission to proceed with search if the request is ambiguous.
- If the user provides a confirmed Korean pre-facelift reference, treat it as primary ground truth.
- Record provenance for accepted positive references.
- Quarantine conflicting references before generation.
- Do not proceed to poster generation until the anchor passes hard gates.

## Korean pre-facelift hard gates

- small rounded-rectangular main headlamps
- thin amber indicator strip completely separated below the main headlamp
- visible body-color gap between the main headlamp and indicator strip
- small, narrow central grille relationship consistent with the user-confirmed image
- basic early bumper opening layout
- front showroom plate reads `KALOS V`

## Immediate pre-facelift failure conditions

- long wedge-like facelift headlamp shape
- indicator integrated into the main headlamp unit
- wide facelift-style upper grille
- a result that differs from the facelift mainly by color, wheels, or caption text

## Repair policy

If headlamp contour, indicator architecture, or grille family is wrong, do not edit-repair the anchor. Discard and regenerate from validated references.
