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

## Review scheduling and mastery

Use synthetic items and session outcomes in a temporary directory or a dry run. Do not add these fixtures to the learner's actual records. Apply [review-policy.md](../.agents/skills/english-coach/references/review-policy.md).

| Case | Given and action | Expected result |
| --- | --- | --- |
| New item | A useful correction is observed in a completed October 12 session | Streak 0, null review evidence fields, `scheduled`, next review October 13; no recurring weakness invented |
| Graduated intervals | Independent successes on October 13, 16, and 23 | Streaks 1, 2, 3; next dates October 16, 23, November 6; mastery only at the third success |
| Maintenance | That mastered item is answered independently on November 6 | Retain `mastered`; next review December 6 |
| Failure | An improving or mastered item is answered incorrectly on October 23 | Streak 0, null streak start, `scheduled`, next review October 24; retain source evidence |
| Assisted answer | The learner produces the target only after a hint or model answer | Same scheduling reset as failure; a corrected retry does not count as success |
| Valid alternative | The learner uses a different expression that independently satisfies the target | Count it as correct; unrelated errors do not invalidate the target |
| Same-day repetition | Independent successes in multiple October 13 sessions | Only one streak increment; the first successful schedule remains unchanged |
| Same-day later failure | A different session on October 13 has an incorrect first attempt after an earlier success | Reset the streak; next review October 14; no second same-day success counted |
| Same-day success after failure | After that success and failure, a third October 13 session produces a correct answer | Record correct practice but retain streak 0 and the October 14 date; the day's success cannot count twice |
| Early successes | Independent successes on October 13, 14, and 15 | Streak 3 but still `improving`; next review October 29 because the span is only two days |
| Long break | An item due October 13 is first successfully reviewed November 1 | First success schedules November 4; no catch-up exercises or automatic failure |
| Mastered item due | A mastered item has a maintenance date on or before today | Eligible for selection while its stored progress status remains `mastered` |
| No assessed answer | The item is skipped, unanswered when practice ends, or cannot be judged | No streak, date, status, or review evidence changes |
| Duplicate completion | Completion handling encounters the same `last_review_session` again | No second streak update or rescheduling |
| Missing historical fields | An old item has a claimed streak but no supporting session evidence | Reset unsupported streak and mastery, retain source links and due date; fabricate nothing |

## Review selection and conversation integration

Expected behavior:

- Review or quiz mode selects up to three due items ordered by oldest date, lower streak, and ID; honors the learner's requested length.
- Review mode finishes after the selected items' initial attempts, feedback, and any optional retries, then persists once. Quiz mode retains its own question limit.
- General conversation incorporates at most one due item that fits naturally, preserving the requested scenario and stopping condition.
- An empty due set with unresolved items permits one early check. If none are unresolved, use a short diagnostic fallback without inventing weaknesses.
- Untested backlog items remain unchanged; no requirement to practice on a due date or clear the backlog.
