# Failure lessons used in my-dream-car

This document summarizes what went wrong in the Kalos T200 Korean pre-facelift failure and how `my-dream-car` should respond.

## What went wrong before

1. A conflicting front reference with uncertain market/year entered the pre-facelift set.
2. The image model followed that visually strong but wrong image more than the correct ground-truth image.
3. The resulting anchor failed the real geometric identity but still passed a weak validation step.
4. The wrong anchor was then treated as authoritative and propagated into the poster.
5. Repair was attempted by editing a fundamentally wrong front fascia instead of regenerating.

## Safeguards applied by the skill

- triggers a short intake routine when uncertainty is meaningful
- raises user-confirmed references to primary ground-truth status
- records provenance for accepted positive references
- enforces a within-set consistency gate
- requires hard-gate evidence notes for lamp / indicator / grille / bumper identity
- distinguishes local repair from identity-critical regenerate-from-scratch cases
- treats failed anchors and failed posters as regression examples

## Practical rule

If the car looks broadly correct but the identity-critical front geometry is wrong, it is still a failure.
