# Core mode acceptance cases

Use these cases to check behavior after changing `AGENTS.md`, the `english-coach` skill, learner settings, knowledge schemas, or the session template. A live run may create the normal session and knowledge records; review those files as part of the result.

## Random mode

Prompt: `開始隨機模式`

Expected behavior:

- Read learner preferences and the scenario history.
- Select daily life, workplace, or travel using the configured balance without claiming true statistical randomness from one run.
- Briefly set the scene in Traditional Chinese and speak first in English.
- Do not invent feedback before the learner has replied.
- After `結束這次的聊天`, stop role-play, summarize, save one session, and update supported knowledge only.

## Specified mode

Prompt: `開始指定模式：你是美國同事，我要在 stand-up 說明功能延期，請使用一般職場口吻。`

Expected behavior:

- Preserve the specified roles, situation, and neutral workplace register.
- Begin without asking for details that are not material.
- Coach each learner reply in Traditional Chinese, then continue in English as the colleague.
- Do not silently change the scenario before completion.

## Quick mode

Prompt: `開始快速模式`

Expected behavior:

- Choose a compact scenario and keep coaching concise.
- Accept no more than three learner replies.
- End automatically after the second or third learner reply without requiring the stop phrase.
- Produce a summary and persist a completed quick-mode session exactly once.

## Review mode with an empty queue

Prompt: `開始複習模式`

Precondition: `knowledge/review-queue.md` contains no scheduled items.

Expected behavior:

- State briefly that no historical review item is available.
- Run a short diagnostic retrieval exercise instead of fabricating prior weaknesses.
- Add review items only when the learner's answers provide evidence.

## Review mode with due items

Prompt: `開始複習模式`

Precondition: At least one item in `knowledge/review-queue.md` has `status: due` or a due `next_review` date.

Expected behavior:

- Prioritize due items and test them in fresh contexts without revealing targets first.
- Update correctness only from independent learner production.
- Retain unresolved items and avoid marking mastery after one lucky answer.
