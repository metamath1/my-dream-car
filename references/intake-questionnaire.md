# Initial user-preference checkpoint

Use this before the first image generation for every new poster job.

## Minimum required check

Unless the user's request already states the answers explicitly, confirm these two items:

1. **Reference images**
   - Ask whether the user has reference images to upload.
   - If not, confirm that web/image research should be used.

2. **Exterior color**
   - For one poster, ask the desired car color.
   - For a series, ask the color policy:
     - one shared color for the whole series
     - representative color per model/generation
     - user-specified colors

These two checks are required even when the model name itself is unambiguous.

## Additional questions only when needed

Ask additional items only when they materially affect identity or factual accuracy:

- exact year / generation / facelift / trim
- market or regional version
- must-match exterior detail
- preferred market for printed specs
- special series-wide presentation preference

## Default grouped message

Adapt naturally. For example:

`작업 전에 두 가지만 확인할게요.`

- `참고할 실제 차량 이미지가 있으면 올려주세요. 없으면 제가 웹/이미지 검색으로 정확한 차량을 확인해서 진행하겠습니다.`
- `차량 색상은 어떤 색으로 할까요? 시리즈라면 전부 같은 색 / 세대별 대표 색 / 직접 지정 중에서 선택할 수 있습니다.`

Add other questions only if necessary.

## Hard-stop rule

If any preference or clarification question is asked, **that response ends with the question set**.

Do not:
- generate an image in the same response
- generate a shape anchor in the same response
- continue poster generation before the user replies
- silently choose an unanswered color and continue

Wait for the next user message.

## Skip rule

Skip a question only when the user already supplied its answer.

Examples:
- `참고 이미지는 없어. 흰색으로 만들어줘.` → do not ask either minimum question again.
- `이 사진 참고해서 검정색으로 만들어줘.` → do not ask either minimum question again.
- `색은 아무거나.` → color is resolved; choose a defensible representative color.

## Response handling

- User-provided or user-confirmed images are highest-priority ground truth for the visible geometry.
- If the user has no images, use web/image research to supplement all necessary angles.
- If the user says `알아서 진행해줘`, use defensible assumptions and proceed.
- Keep the checkpoint short; normally one grouped round is enough.
