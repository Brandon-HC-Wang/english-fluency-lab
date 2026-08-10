# Review queue

No review item is scheduled yet.

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
  status: due | scheduled | improving | mastered
```

Test an item in a fresh context without showing `target` first. Increase `correct_streak` only after independent correct production, and retain source links instead of copying full transcripts.
