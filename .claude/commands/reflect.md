---
description: Review session and recommend updates to CLAUDE.md, skills, docs, and comments
---

# Session Reflection

Review this session and identify learnings worth capturing. Focus on:

- **Corrections** - Where you made mistakes and had to fix them
- **Discoveries** - Things we figured out about this codebase, tools, or workflows
- **Patterns** - Approaches that worked well and should be repeated
- **Decisions** - The choices that we made

## Guiding Principles

- **Terse** - Minimal words, maximum signal
- **Tactical** - Specific and actionable, not abstract guidance
- **Evidence-based** - Each recommendation must tie to a specific session event
- **Simplest thing possible** - Seek to improve, not fix
- **Project-local only** - Never modify global config or ~/.claude/

## Update Targets

| Target | Location | When to use |
|--------|----------|-------------|
| CLAUDE.md | `./CLAUDE.md` | Project conventions, gotchas, tool usage |
| Skills | `./.claude/skills/` | Reusable workflows worth capturing |
| Docs | `**.md` | Documentation gaps discovered |
| Code | code files | Comments that should be added or updated |
| Stale docs | `docs/NEEDS_UPDATE.md` | Review and action items logged during development |

**Scoping rule:** If a learning relates to a global skill, recommend copying it to `.claude/skills/` first, then modifying the local copy.

Guidelines:
- Only update CLAUDE.md with topics that effect the entire project. Avoid context bloat.
- Prefer code comments for isolated topics. Explain why. Don't repeat what the code already says.
- Use docs for procedures and architecture.

## Output Format

Present recommendations in two tiers:

```
## Recommended

1. [CLAUDE.md] <brief description of what to add/update>
2. [skill] <brief description of skill to create/update>
3. [doc] <brief description of doc to create/update>
4. [cleanup] <file to remove>
5. etc...

## Consider

4. [CLAUDE.md] <lower confidence suggestion>
5. [skill] <broader scope idea>
6. etc...

```

## Instructions

1. Review the session and make a list of corrections, discoveries, patterns, and decisions
2. Check for temporary artifacts (screenshots, debug output, generated files) and flag them for deletion.
3. Apply the guiding principles strictly - when in doubt, leave it out
4. Decide how best to apply each item - docs or skills
5. Review `docs/NEEDS_UPDATE.md` if it exists — incorporate its items into your recommendations and clear the file after addressing them.
6. Identify any documentation, comments, etc. that is out-of-date and should be updated or removed.
7. Present recommendations in the format above
8. **Wait for user approval** - do not make any changes yet
9. After user responds, apply only the approved items
10. Confirm what was updated

If the session has no meaningful learnings, say so briefly and don't force recommendations.
