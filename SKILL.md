---
name: my-dream-car
description: Research a user-specified real-world car, reduce uncertainty through a short initial Q&A when needed, ground the exact variant in proven references, validate a shape anchor, then generate a premium vertical automotive poster with strong resistance to generation/facelift drift.
---

# my-dream-car

Generate a premium poster of the **exact requested production car**. Vehicle identity and exterior geometry are more important than poster beauty.

The skill is designed to prevent the following failure modes while keeping multi-poster layouts consistent:

- drawing the wrong generation or facelift while the text label is correct
- blending conflicting references from different markets or variants
- letting a wrong shape anchor pass and then propagate to the poster
- treating user-confirmed reference images as optional instead of primary ground truth
- continuing with high uncertainty instead of asking a short clarifying question set
- using edit repair for identity-critical errors that actually require regeneration

## Inputs

Required:
- vehicle name

Optional:
- year
- generation / chassis code
- pre-facelift / facelift / post-facelift wording
- trim / engine variant
- body style
- market / region
- preferred exterior color
- poster language / aspect ratio
- user reference images
- user-specified must-match details
- preferred market for specifications

## Core principles

1. **Vehicle identity outranks style.**
2. **Do not guess when a short question can remove major uncertainty.**
3. **User-confirmed images outrank search images.**
4. **Conflicting references must be quarantined before generation.**
5. **An anchor is authoritative only after passing hard gates.**
6. **Identity-critical anchor failures require regeneration, not cosmetic repair.**
7. **The style poster reference controls composition only, never car shape.**
8. **Front showroom plate is mandatory unless the user explicitly asks to omit it.** The plate text should be the short car name such as `KALOS V`, `BMW 118d`, or `AVANTE`.
9. **Series consistency matters.** When generating a pair or set of posters, use a fixed poster template and consistent layout anchors so that repeated elements stay in the same positions across the set.
10. **For paired posters, do not generate the final posters independently from scratch.** Establish one layout anchor first, then generate the matching companion poster using that layout anchor.

## Required workflow

### 1) Resolve the initial certainty level

Before researching or generating, classify the request internally as one of:

- **high certainty**
- **medium certainty**
- **low certainty**

Factors that reduce certainty:

- the model name spans multiple generations
- pre-facelift / facelift matters
- regional-market front ends differ
- the vehicle is obscure, discontinued, or newly released
- the user explicitly cares about exact shape
- the user asks for two related variants together
- there is a known prior failure mode for this model

### 2) Run the initial Q&A routine when needed

Use `references/intake-questionnaire.md`.

If certainty is **medium** or **low**, or if the user asks for accuracy-sensitive work, ask one grouped intake message before generation.

The intake should be short and practical. It should ask only what materially improves fidelity.

Typical grouped questions:

- Do you have reference images you want me to follow? If yes, please upload them.
- If you do not have images, should I proceed by searching the web for the exact vehicle?
- If known, what are the exact year / generation / pre-facelift or facelift / trim / market?
- Is there a must-match design detail such as the headlamps, grille, rear fender, or wheel design?
- For printed specifications, is there a preferred market or sales version?

#### Intake handling rules

- Ask **one grouped question set**, not many fragmented questions.
- If the user provides only partial answers, proceed with those answers and research the rest.
- If the user provides no references, continue with web/image research instead of stalling.
- Do not ask unnecessary questions when the request is already unambiguous.
- When the user explicitly says to just proceed, continue with documented assumptions.

Record the outcome in `templates/intake-session.md` internally.

### 3) Resolve the exact vehicle identity

Normalize the request into:

- manufacturer
- model
- generation/chassis
- model year/era
- facelift state
- trim/engine variant
- body style
- sales market/region

Check for regional rebadges and market-specific fascia differences. A global model name is not enough when Korean, European, North American, or other market versions differ visually.

### 4) Decide whether strict visual grounding is required

Strict visual grounding is mandatory for:

- newly released cars
- obscure or uncommon cars
- discontinued or older cars
- regional-market cars
- rebadged cars
- pre-facelift vs facelift requests
- two or more variants requested together
- any car that previously produced a shape error
- any request where the user emphasizes exterior accuracy

In strict mode, do not jump directly to poster generation.

### 5) Build proven visual reference sets

Use image search actively unless the user already provided enough exact images.

Prefer sources in this order:

1. official manufacturer press/media images or brochures
2. reputable automotive publications and vehicle databases
3. authentic stock/listing photos only when factory-correct and clearly attributable
4. enthusiast sources only as support

For every shape-critical **positive reference**, record:

- local file or URL
- source URL
- source name/publisher
- claimed market
- claimed year or era
- body style
- view angle
- the visible identity-critical features used for identification
- accepted / quarantined / rejected status
- decision reason

#### Reference provenance gate

A downloaded image without recoverable provenance must not become the primary shape reference when market-specific fascia differences exist.

#### Independent-source rule

“Two references” means two visually corroborating references from at least two **independent sources**, not two crops or thumbnails from the same photo set.

Rear or side-only images do not count as corroboration for front-fascia identity.

#### User-reference priority

When the user supplies or later confirms a real vehicle photo as the correct variant, treat it as the **primary ground-truth reference**. Rebuild the reference set around it and remove conflicting search images before any further anchor generation or repair.

### 6) For sibling variants, isolate and compare sets

If the user requests two related variants such as pre-facelift and facelift, or early/late, or domestic/export:

- create `REFERENCE SET A` only for variant A
- create `REFERENCE SET B` only for variant B
- do not mix them
- fill `templates/variant-delta-matrix.md`

The matrix must describe **visible differences**, not abstract labels.

Compare at minimum:

- headlamp outer shape
- indicator separation/integration
- grille outline and relation to lamps
- badge position
- bumper openings and fog-lamp treatment
- side molding or character lines if changed
- rear lamps / rear bumper if changed
- wheel design only when genuinely variant-specific

### 7) Apply the within-set consistency gate

Before generation, compare all references **inside each variant set**.

They must agree on identity-critical features such as:

- headlamp outer contour
- indicator separation/integration
- grille outline
- badge relationship
- bumper openings

If one image conflicts, quarantine it and verify its market/year. Do not let the image model reconcile conflicting references by blending them.

If the remaining accepted references are too weak, either:
- ask the user for reference images, or
- continue research until a reliable set is formed.

### 8) Build a shape-critical brief

Use `templates/vehicle-research.json` and `templates/shape-critical-notes.md`.

The brief must include concrete geometry such as:

- exact headlamp/indicator relationship
- grille outline and width
- bumper and fog-lamp openings
- hood/fender break lines
- side character lines and lower-door sculpting
- rear-fender flare/volume and wheel-arch treatment
- C-pillar/rear-quarter window silhouette
- taillamp shape
- wheel/stance/proportion cues

Write illustrator-style statements. Avoid vague notes like “looks like the early model.”

### 9) Generate a shape anchor separately for each exact variant

Use `references/anchor-prompt.md`.

The anchor is not a poster. It is a clean vehicle rendering used to verify identity.

Requirements:

- simple neutral background
- no giant typography
- minimal or no decorative effects
- exact variant reference images only
- front three-quarter or the angle that best exposes the differentiating features
- factory-correct proportions
- mandatory showroom front plate with the short car name

For paired variants, generate A and B in separate calls.

### 10) Validate the anchor with hard gates

Inspect the generated anchor directly.

The anchor is valid only if all hard gates pass:

- correct generation/chassis
- correct facelift state
- correct body style
- correct headlamp outer shape
- correct indicator relationship
- correct grille outline and badge relationship
- correct bumper opening topology
- correct major side surfacing
- correct rear-quarter/rear-fender form when visible
- showroom plate exists and shows the short car name
- no obvious drift toward a sibling generation or market variant

#### Evidence note requirement

For each identity-critical hard gate, record a short pass/fail note by comparing a zoomed front crop with the primary real reference.

Do not pass an anchor based only on overall resemblance.

#### Paired-variant differential gate

When A and B are related variants, fail them if they look essentially the same except for:

- paint color
- wheels
- text labels
- lighting
- tiny trim changes

If the researched variants are supposed to have a visibly different front end, the generated anchors must visibly show that difference.

### 11) Choose repair vs regenerate correctly

Use `references/repair-prompt.md` **only for localized errors** when the base vehicle identity is already correct.

Examples of **local errors**:
- showroom plate text rendering
- a small trim detail
- minor wheel-design drift
- a fog-lamp or molding detail

Examples of **identity errors** requiring full anchor discard and regeneration:
- wrong headlamp contour
- wrong indicator architecture
- wrong grille family
- wrong market-specific fascia
- wrong body style
- wrong generation/facelift

If any identity-critical feature is wrong, discard the anchor and regenerate from scratch using only revalidated exact-variant references.

### 12) Research and verify printed specifications

Verify facts from:

1. manufacturer brochures/specs/official archives
2. reputable automotive publications
3. established specification databases

Never invent values. Do not merge different years, engines, transmissions, or markets.

If performance data is uncertain, use another verified field such as:

- torque
- transmission
- drivetrain
- dimensions
- wheelbase
- production years

### 13) Lock the poster layout before generating a multi-poster set

Use `references/layout-consistency-spec.md`.

When the user requests two or more posters that should look like a coherent set, do **not** generate each final poster independently from scratch.

#### Required sequence for paired posters

1. Generate the first final poster only after the shape anchor has passed.
2. Treat that first poster as the **series layout anchor**.
3. Generate the second poster by preserving the first poster's canvas size, margins, text block positions, hero-car placement logic, background-word scale, title baseline, description block spacing, and bottom spec-strip position.
4. Change only the content that must differ: the exact car, variant-specific wording, verified specs, and any necessary vehicle-scale adjustment.

#### Layout-lock requirements

Across a paired or multi-poster set, keep the following consistent unless the user explicitly requests variation:

- exact canvas aspect ratio and export size
- top small-text band position
- pale background-word size and placement
- hero-car framing zone and vertical placement logic
- main-title baseline and size
- description block position and spacing
- bottom rule and four-cell spec-strip position, width, and divider rhythm
- overall whitespace system

Use the first final poster as the **layout anchor** for the remaining posters in the set.

#### Layout consistency gate

Before accepting a paired or multi-poster set, verify:

- the canvases have the same size and aspect ratio
- repeated text blocks align to the same visual positions
- the cars occupy similar visual scale and are centered within the same framing logic
- the bottom spec strip starts and ends at the same positions
- the pair reads as one series rather than two merely similar posters

If layout drift is visible, regenerate or edit the later poster using the earlier poster as the layout anchor.

### 14) Generate the final poster from a validated anchor

Use:

- validated shape anchor = primary vehicle-fidelity reference
- exact-variant research images = secondary fidelity references
- `assets/poster-style-reference.png` = layout/style reference only
- `references/poster-prompt.md` = final poster template

The poster must preserve the anchor’s geometry and the showroom plate. When a multi-poster set is requested, the first finished poster also becomes the layout anchor for the remaining posters.

### 15) Validate the final poster

The poster fails if:

- it regresses to the wrong generation/facelift
- differentiating lamp/grille/bumper features disappear
- side/rear-fender surfacing becomes generic or too smooth
- paired variants again become visually almost identical
- the showroom plate is missing or wrong
- the posters in a set have visibly different canvas sizes or drifting layout positions for repeated elements

If the final poster regresses on a hard-gate feature, repair from the **validated** anchor.

If the anchor itself is later found wrong, invalidate both anchor and poster and restart from real references.

## Regression awareness

The skill must explicitly apply the lessons captured from prior failures. The included Kalos T200 Korean pre-facelift fixture demonstrates that the skill must not:

- accept a conflicting front reference with uncertain market/year as a positive reference
- let a visually larger but incorrect image overpower a user-confirmed ground-truth image
- allow a wrong anchor to pass because the overall silhouette looks similar
- keep editing a fundamentally wrong front fascia instead of regenerating

Use `tests/regression-test-spec.md` and `tests/fixtures/kalos-korea-t200/` as regression guidance.
