# Kalos T200 Korean pre-facelift regression fixture

This fixture is included to document a real failure case that `my-dream-car` must avoid repeating.

## Files

- `korean_prefacelift_ground_truth.png` — user-confirmed Korean pre-facelift ground truth
- `01_matching_front_reference.jpg` — accepted front reference
- `02_matching_front_detail_reference.jpg` — accepted front detail reference
- `03_matching_rear_reference.jpg` — accepted rear reference
- `99_conflicting_front_reference_wrong_market_or_variant.jpg` — conflicting front reference that must be quarantined
- `01_failed_shape_anchor_after_search.png` — known failed anchor used as a negative example
- `02_failed_prefacelift_poster.png` — known failed poster used as a negative example
- `failure_progression.jpg` — visual summary of the failure path
- `visual_comparison_reference_to_anchor.jpg` — comparison image showing the mismatch

## Usage

These files are regression and analysis fixtures.

- Positive references may be used only after provenance review.
- The conflicting front reference must not be used as a positive pre-facelift reference.
- The failed anchor and failed poster are **negative examples**. They exist to define failure, not to guide generation.
