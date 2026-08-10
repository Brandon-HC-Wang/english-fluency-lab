---
session_id: "{{YYYY-MM-DD-HHMM-mode-topic}}"
started_at: "{{ISO-8601 local datetime}}"
completed_at: "{{ISO-8601 local datetime}}"
mode: "{{random | specified | quick | quiz | review | reading | writing | weakness-training}}"
category: "{{daily-life | workplace | travel | other}}"
topic: "{{short topic}}"
status: "{{completed | interrupted}}"
learner_turns: 0
---

# {{Session title}}

## Context

- Scenario: {{brief situation}}
- Learner role: {{role}}
- Coach role: {{role}}
- Practice focus: {{optional target}}

## Dialogue

### Turn 1

#### Learner — original

{{Preserve the learner's message exactly as written.}}

#### Coaching

- Classification: {{錯誤 | 不自然 | 語氣調整 | 可選說法 | 自然}}
- Natural revision: {{revision, or "No change needed"}}
- 中文說明: {{one to three high-value points}}

#### Coach — English reply

{{in-character reply}}

<!-- Repeat the turn structure for each learner message. -->

## Session summary

### Strengths

- {{evidence-based strength}}

### High-value corrections

- `{{original}}` → `{{revision}}`: {{reusable explanation}}

### Useful expressions

- `{{expression}}`: {{meaning or usage note in Traditional Chinese}}

### Next practice target

- {{one prioritized target}}

## Knowledge updates

- Error patterns: {{updated item IDs or "None"}}
- Review queue: {{added or updated item IDs or "None"}}
- Scenario history: {{row added or "Not applicable"}}
