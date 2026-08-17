# Initial intake questionnaire

Use this when certainty is medium/low or when exact variant fidelity matters.

## Goal

Reduce uncertainty before expensive research and generation. Ask one short grouped message, not a long interview.

## Default grouped intake message

You can adapt this wording naturally:

`To make the car accurately, a few quick checks first:`

- `If you have reference images, please upload them. I will prioritize them.`
- `If you do not have images, I can verify the car through web/image search and continue.`
- `If known, please tell me the year / generation / pre-facelift or facelift / trim / market.`
- `If there is a must-match design detail such as the lamps, grille, rear fender, or wheel design, please tell me.`
- `If the poster specs should follow a specific market version, please tell me that too.`

## Ask / skip rules

Ask when:
- generation or facelift ambiguity matters
- regional-market design differences exist
- the vehicle is obscure or newly released
- two sibling variants are requested together
- a prior failure exists for this model
- the user explicitly emphasizes accuracy

Skip when:
- the requested variant is already very specific and unambiguous
- the user already provided exact reference images and variant info
- asking again would provide no meaningful accuracy gain

## Response handling

- If the user uploads images, treat them as the highest-priority ground truth.
- If the user answers only some fields, continue with those answers and research the rest.
- If the user declines to answer and tells you to proceed, continue using best-effort research and record assumptions.
- Do not force the user to answer all questions.

## Maximum interaction rule

The intake should usually take at most **one grouped question round**.
A second short follow-up is allowed only if there is still a major unresolved ambiguity that would clearly change the car.
