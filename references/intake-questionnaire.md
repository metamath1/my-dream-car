# Initial user-preference checkpoint

Use this before the first image generation when uncertainty or missing user preferences can materially affect accuracy or series consistency.

## Goal

Get the user's important choices before generation rather than correcting avoidable assumptions afterward.

The checkpoint should feel like one short confirmation, not a long interview.

## Strong trigger conditions

Ask when:
- generation or facelift ambiguity matters
- regional-market design differences exist
- the vehicle is obscure, newly released, or difficult to identify precisely
- two or more sibling variants are requested together
- a multi-generation or multi-poster series is requested
- the user has not specified an important series-wide choice such as color policy or market basis
- a prior failure exists for this model
- the user explicitly emphasizes accuracy

## Series preference checkpoint

For paired or multi-poster requests, check only the shared choices that are still missing:

- target market / regional specification
- color policy:
  - one shared color for all posters
  - representative color per generation/model
  - user-specified color(s)
- reference images available or web/image research authorized
- must-match exterior details
- any explicit series-wide presentation preference

Do not ask for choices the user already provided.

## Default grouped message

Adapt naturally. For example:

`Before I generate the series, I want to lock the few choices that affect consistency.`

- `If you have reference images, please upload them; I will prioritize them. Otherwise I can verify each vehicle through web/image search.`
- `Which market or regional version should I use, if that matters?`
- `For color, should I use one shared color for the whole series, a representative color for each generation, or colors you specify?`
- `If there is any must-match exterior detail, please tell me.`

## Hard-stop rule

If any preference or clarification question is asked, **that response ends with the question set**.

Do not:
- generate any image in the same response
- generate a shape anchor in the same response
- continue the generation workflow before the user replies
- silently choose an unanswered preference and continue

Wait for the next user message.

## Skip rule

Skip this checkpoint when the original request already contains enough information to proceed reliably.

Examples:
- exact generation/facelift/market already specified
- user already provided or declined reference images
- series color policy is already specified
- no meaningful unresolved preference remains

## Response handling

- User-provided or user-confirmed images are highest-priority ground truth.
- If the user answers only some items, continue unless a remaining ambiguity would materially change the result.
- If the user says `그냥 알아서 진행해줘`, use defensible assumptions and proceed.
- Do not force the user to answer every optional question.

## Interaction limit

Usually use only **one grouped checkpoint round**.
A second short follow-up is allowed only when a remaining ambiguity would clearly change the vehicle identity or the requested series.
