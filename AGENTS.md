# AGENTS.md

## Prompt History Convention

Every time an agent works on this repository, it **must** append both sides of
the current conversation turn to `PROMPT.md` as two separate, fenced plaintext
code blocks — **in this order**:

1. **User block** — the exact user message that triggered this session.
2. **Agent block** — a concise summary of what the agent did / replied.

### Format

~~~markdown
```
<user message verbatim>
```

```
<agent response summary>
```
~~~

### Rules

- Always append to the **end** of `PROMPT.md`; never edit existing blocks.
- Use plain fenced code blocks (triple backticks, no language tag).
- Keep the agent block short but informative (one or a few sentences).
- Do this **before** calling `report_progress` for the final commit so that
  the turn is included in the same commit as the rest of the changes.
