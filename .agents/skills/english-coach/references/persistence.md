# Persistence rules

## Conversation and practice records

Create one Markdown record at:

`sessions/<YYYY>/<YYYY-MM-DD-HHMM>-<mode>-<topic-slug>.md`

Use the learner's local date and time. Choose a short lowercase hyphenated topic slug. If a filename collision exists, add a numeric suffix.

Use `templates/session.md` as the canonical structure. Copy it into the new record, replace all placeholders, repeat the dialogue block for every learner turn, and remove unused optional placeholders.

Include:

1. YAML frontmatter with date, mode, topic, status, and number of learner turns
2. Scenario and roles
3. Each learner message exactly as written
4. The corresponding natural revision and concise coaching notes
5. The coach's English reply
6. Final strengths, corrections, useful expressions, and next target

Use `status: completed` only after a normal stop or an automatic mode limit. Do not place inferred private details in the record.

## Derived knowledge

Create the required `knowledge/` files when they do not yet exist. Update only items supported by the completed activity:

- `knowledge/error-patterns.md`: recurring or potentially important issues, with category, evidence count, first seen, last seen, examples, and status
- `knowledge/review-queue.md`: specific grammar, vocabulary, collocation, or pragmatic items worth retrieving again; follow [review-policy.md](review-policy.md) for creation, dated evidence, outcomes, scheduling, and mastery. Save the source session before applying each item's update once.
- `knowledge/scenario-history.md`: date, mode, category, and topic, used to prevent accidental repetition

Do not update `knowledge/current-level.md` after every ordinary chat. Update it only after baseline or analysis mode, or when a meaningful evidence-backed change is clear.

Keep knowledge files concise. Link to session records instead of duplicating full transcripts. Preserve previous evidence when revising a conclusion.

## Assessment records

Save baseline and analysis reports at:

`assessments/<YYYY>/<YYYY-MM-DD>-<assessment-type>.md`

If the same type already exists for the date, add a numeric suffix. Record the evidence window, assessed dimensions, confidence, limitations, findings, and next actions.

## Completion report

After writing records, tell the learner which paths changed. Do not create a Git commit or push automatically.
