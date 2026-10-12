# Review scheduling and mastery

These are workspace defaults, not a validated proficiency scale. Follow a learner's explicit changes to them. Use the learner's local calendar date from `learner/profile.md` for all date comparisons and additions.

## Select items

- An item is eligible when `next_review` is today or earlier, or its stored status is `due`. Include mastered items whose maintenance date has arrived. Treat due dates as selection hints, not appointments or deadlines.
- In review or quiz mode, select up to three eligible items, oldest `next_review` first; break ties by lower `correct_streak`, then item ID. Respect the learner's requested length. Review mode normally ends after one initial attempt per selected item, feedback, and optional retries; quiz mode retains its question limit.
- If fewer items are due, review mode uses those without padding the exercise. Quiz mode may fill its question limit with diagnostic questions without claiming historical weaknesses. If none are due, an early check of one unresolved item is allowed; if there are no unresolved items, use the mode's short diagnostic fallback and explain that there is nothing due.
- In general conversation, incorporate at most one eligible item when it fits the chosen scenario. Do not show its target or change the scenario to force a test. A naturally occurring independent use can also provide evidence for an existing item.
- Leave untested items unchanged. Returning after a long break does not require clearing the backlog or restarting all items.

## Record the outcome

Evaluate whether the learner achieved the item's target in a fresh context; unrelated errors do not make that target incorrect. Accept valid alternatives rather than requiring the stored expression word for word.

Use the first assessable attempt for each item in a session:

- `correct`: independent correct production before a target-revealing hint, model answer, or correction. A spontaneous self-correction before coach feedback may count.
- `incorrect`: an independent attempt fails the target.
- `assisted`: the learner needs a hint, answer, translation of the target, or correction to produce it. An immediate corrected retry is practice, not a new success.
- `unassessed`: the item is skipped, the activity ends before an answer, or the response cannot be judged. Do not change its scheduling or streak.

Count at most one success per item per local calendar date, even across sessions. Check `last_success_on` before counting a correct outcome; update it only when a success counts. Same-day further correct answers may be recorded as practice but do not advance the streak, reschedule the item, or establish mastery. A later incorrect or assisted first attempt in a different session on that date still resets the streak; preserve `last_success_on` so a third session cannot count another same-day success. Within a session, retries do not replace the first outcome.

Keep the prompt, original response, outcome, and any assistance in the session's coaching notes. Maintain `last_reviewed` and `last_review_session` for every assessed outcome and add its session path to `source_sessions` without duplicates; leave them unchanged for `unassessed`. Apply updates only after saving the completed practice session. If that session is already `last_review_session`, do not apply its update again.

## Schedule from the actual practice date

Create an item only from observed learning evidence, not from a control message or an invented weakness. A useful one-off correction can enter the review queue without being declared a recurring error pattern. Do not create items for optional stylistic alternatives merely because an alternative exists.

For a new item, set `correct_streak: 0`, `streak_started_on: null`, `last_success_on: null`, `last_reviewed: null`, `last_review_session: null`, `status: scheduled`, and `next_review` to the completed session's date plus one day. Its source correction is not a successful review.

| Outcome or resulting streak | Stored status | Next review |
| --- | --- | --- |
| Incorrect or assisted | `scheduled`; reset streak to 0 and clear `streak_started_on` | Actual practice date + 1 day |
| First counted correct answer | `improving`; set streak to 1 and `streak_started_on` to today | Actual practice date + 3 days |
| Second counted correct answer | `improving`; streak 2 | Actual practice date + 7 days |
| Third or later counted correct answer before mastery | `improving`, or `mastered` if the criteria below are met | Actual practice date + 14 days |
| Counted correct maintenance of an already mastered item | `mastered` | Actual practice date + 30 days |

All intervals start from when the learner actually practiced, not from the old due date. An early independent check can count under the same rules; successful practice never requires being exactly on schedule. A failure at any stage, including maintenance, uses the one-day reset.

## Mastery and existing entries

- Mark an item `mastered` only after at least three consecutive counted correct answers on distinct dates, in distinct sessions and fresh contexts, spanning at least seven calendar days from `streak_started_on` to the latest success. Same-day correct practice cannot trigger mastery just because time has elapsed.
- `mastered` describes this item's demonstrated retrieval under these rules, not permanent knowledge or overall English proficiency. Keep the item and source evidence for maintenance.
- Compute whether an item is due when selecting it; no background job needs to rewrite `scheduled`, `improving`, or `mastered` to `due` as time passes. Preserve the underlying progress status.
- For existing entries lacking the new evidence fields, reconstruct them only from linked session records. If the history cannot support a streak or mastery claim, keep the source links, reset the unsupported streak to 0 with null evidence fields, and retain its existing due date. Do not invent historical successes.

## Example

For a new item created on October 12: first review is October 13. Independent successes on October 13 and 16 schedule October 16 and 23 respectively. A third success on October 23 meets the seven-day span and schedules November 6 as a mastered item's first maintenance. Correct maintenance then schedules December 6. An incorrect or assisted attempt on any of these dates instead schedules the following day and resets the streak.
