# Review queue

## Active items

```yaml
- id: feel-burned-out
  focus: collocation
  prompt_context: Describe feeling exhausted after a demanding day in a new situation.
  target: Use feel burned out or a valid equivalent to describe the state.
  source_sessions:
    - sessions/2026/2026-10-12-1538-quick-weekend-plans.md
  next_review: 2026-10-13
  correct_streak: 0
  streak_started_on: null
  last_success_on: null
  last_reviewed: null
  last_review_session: null
  status: scheduled

- id: leave-the-office
  focus: grammar
  prompt_context: Describe leaving the workplace in a fresh situation.
  target: Use leave the office or left the office without an unnecessary from.
  source_sessions:
    - sessions/2026/2026-10-12-1538-quick-weekend-plans.md
  next_review: 2026-10-13
  correct_streak: 0
  streak_started_on: null
  last_success_on: null
  last_reviewed: null
  last_review_session: null
  status: scheduled

- id: spend-time-with
  focus: collocation
  prompt_context: Describe relaxing with a friend or family member in a new situation.
  target: Use spend time with someone or a valid equivalent for companionship.
  source_sessions:
    - sessions/2026/2026-10-12-1538-quick-weekend-plans.md
  next_review: 2026-10-13
  correct_streak: 0
  streak_started_on: null
  last_success_on: null
  last_reviewed: null
  last_review_session: null
  status: scheduled
```

## Use during practice

- Retain due items until the learner next chooses to practice; do not require a fixed practice schedule or clearing the entire backlog.
- Prioritize due items in review or quiz mode. During general conversation, incorporate a small number only when they fit the learner's scenario and requested length naturally.
- Do not let review items replace the requested activity or reveal their targets before testing retrieval.
- Require independent correct production across separate sessions before marking an item mastered.

## Scheduling rules

Follow [review-policy.md](../.agents/skills/english-coach/references/review-policy.md) for intervals, selection limits, assisted answers, and mastery. It is the canonical policy; dates are based on the learner's local calendar and the actual practice date.

## Entry schema

```yaml
- id: short-stable-id
  focus: grammar | vocabulary | collocation | naturalness | register
  prompt_context: short description of what to retrieve
  target: target expression or behavior
  source_sessions:
    - relative/path/to/session.md
  next_review: YYYY-MM-DD
  correct_streak: 0
  streak_started_on: null  # YYYY-MM-DD after the first counted success
  last_success_on: null  # YYYY-MM-DD; retained on failure to prevent same-day recounting
  last_reviewed: null  # YYYY-MM-DD after an assessed review
  last_review_session: null  # relative session path, for evidence and duplicate protection
  status: due | scheduled | improving | mastered
```

Test an item in a fresh context without showing `target` first. Increase `correct_streak` only after independent correct production, and retain source links instead of copying full transcripts.
