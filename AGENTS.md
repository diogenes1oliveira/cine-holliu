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

---

## ⚠️ CHATS.md Convention — PRIMARY PROTOCOL (supersedes PROMPT.md) ⚠️

**Every agent session must update `CHATS.md`** — the canonical conversation log.
The `PROMPT.md` section above is **legacy**; once `PROTOCOL.md` exists, skip it.

### CHATS.md turn structure

~~~markdown
## Turn #N — <short description>

### Message #0 — @human

```
<verbatim human text — no formatting, no language tag>
```

### Message #1 — Agent

<formatted markdown prose: `code` spans, **bold**, lists, etc.>

```markdown
<verbatim agent reply, all markdown formatting preserved>
```
~~~

### Rules (memorise these)

1. **Human is always `#0`** and always starts every turn.
2. **Human blocks**: plain ` ``` ` fence, no language tag, verbatim text only.
3. **Agent blocks**: formatted markdown prose **+** verbatim inside a ` ```markdown ` fence.
4. **Turn numbers** are sequential from 1 — never skip or reuse.
5. **Missing turns** → reconstruct from `PROMPT.md`, commit history, and context.
   Mark reconstructed messages with `<!-- reconstructed -->` on the header line.
6. **Gap detection**: `## Turn #` lines must be sequential; every turn must have
   `### Message #0`. A missing `#0` or a gap in N means a turn needs filling.
7. **Parsing turns**: scan for `## Turn #N` → extract N as integer → content ends
   at next `## Turn #` or EOF.
8. **Parsing messages**: within a turn, scan for `### Message #M` → extract M →
   content ends at next `### Message #` or `## Turn #` or EOF.
9. **Do this before `report_progress`** — the turn must be in the same commit.
