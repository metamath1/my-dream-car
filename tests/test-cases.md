# Manual test cases

These tests are designed to verify the intake routine, provenance filtering, and variant fidelity.

## Test 1 — Kalos paired-variant regression

Prompt:

`my-dream-car로 GM 대우 칼로스 전기형과 후기형 포스터를 각각 한장씩 만들어줘.`

Expected behavior:
- trigger the initial Q&A because this is a paired, market-sensitive, accuracy-sensitive request
- ask whether the user has reference images
- if a Korean pre-facelift reference image is provided, treat it as primary ground truth
- quarantine the known conflicting front reference if it disagrees with the user-confirmed photo
- generate clearly different pre-facelift and facelift outputs
- keep `KALOS V` on the showroom plate

## Test 2 — recent generation-sensitive sedan

Prompt:

`my-dream-car로 현대 아반떼 CN8 포스터를 만들어줘.`

Expected behavior:
- if the request is not fully specific, ask a short intake question set
- use image research actively
- avoid drifting into CN7 cues
- use a shape anchor before the final poster

## Test 3 — facelift split within one generation

Prompt:

`my-dream-car로 BMW 118d 전기형과 후기형 포스터를 각각 만들어줘.`

Expected behavior:
- isolate references per variant
- use a variant delta matrix
- produce visibly different front-end results

## Test 4 — obscure or uncommon vehicle

Prompt:

`my-dream-car로 Isuzu Piazza 포스터를 만들어줘.`

Expected behavior:
- ask for references if appropriate
- continue with strict research if none are provided
- avoid overclaiming uncertain specs

## Test 5 — user-driven ground truth

Prompt:

`이 차 참고해서 포스터 만들어줘.` + user reference image

Expected behavior:
- prioritize the uploaded image over search images
- only use search to supplement missing views or factual specs

## Test 6 — series layout consistency

Prompt:

`my-dream-car로 현대 라비타와 라비타 1차 페이스리프트 포스터를 각각 한장씩 만들어줘.`

Expected behavior:
- ask the initial clarifying question set if needed
- produce two posters with the same canvas size and a clearly shared layout template
- keep title, description block, and spec strip aligned across the pair
- vary the car and variant-specific details while preserving series consistency

## Test 7 — multi-generation orientation consistency

Prompt:

`my-dream-car로 폭스바겐 골프 GTI 1세대부터 8세대까지 같은 시리즈 포스터로 각각 만들어줘.`

Expected behavior:
- use one coherent poster template across all generations
- keep the exact same canvas size and repeated layout positions
- show every vehicle in a front three-quarter view with the nose pointing toward canvas left
- reject or regenerate any member that faces the opposite direction or appears horizontally mirrored
- preserve generation-specific exterior identity while keeping the series visually consistent

## Test 8 — series preference checkpoint hard stop

Prompt:

`my-dream-car로 폭스바겐 골프 GTI를 세대별로 한 장씩 포스터로 만들어줘.`

Expected behavior:
- before the first image, ask only for missing shared preferences that materially affect the series, especially color policy and market basis
- if a clarification question is asked, stop that response and wait for the user's reply
- generate zero images in the same response as the question
- after the user replies, apply the confirmed shared preferences consistently across the series

## Test 9 — mandatory minimum preference checkpoint on a single car

Prompt:

`my-dream-car로 SM7 뉴아트 포스터 만들어줘.`

Expected behavior:
- before generating any image, ask whether the user has a reference image
- before generating any image, ask what exterior color the user wants
- group those questions into one short response
- generate zero images in that response
- after the user answers, continue with research and generation

## Test 10 — Avante CN8 whole-body geometry regression

Prompt:

`my-dream-car로 현대 아반떼 CN8 포스터를 만들어줘. 참고 이미지는 없고 흰색으로 해줘.`

Expected behavior:
- do not repeat the already-answered reference/color questions
- research the exact CN8 using multiple angles, including usable side/profile and rear-three-quarter evidence
- validate not only the front fascia but also front-fender shoulder, rear-fender volume, wheel arches, door surface planes, rocker treatment and C-pillar/rear-quarter geometry
- fail an anchor whose front fascia is plausible but whose side body is flattened or genericized
- preserve distinctive side geometry in the final poster
