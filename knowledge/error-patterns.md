# Error patterns

No recurring error pattern has been established yet.

## Entry schema

Use one entry per distinct pattern:

```yaml
- id: category-short-name
  category: grammar | vocabulary | collocation | naturalness | register | coherence
  pattern: concise reusable description
  evidence_count: 0
  first_seen: YYYY-MM-DD
  last_seen: YYYY-MM-DD
  status: observed | practicing | improving | stable
  examples:
    - session: relative/path/to/session.md
      original: exact learner wording
      revision: natural revision
```

Count the same pattern at most once per session. Do not promote a one-off mistake to a recurring weakness without independent recurrence; it may remain only in its session record.
