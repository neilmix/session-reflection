# Session Reflection Plugin Design

## Overview

A Claude Code slash command (`/reflect`) that triggers end-of-session self-reflection. Claude analyzes the current session, identifies learnings, and presents recommended updates for user approval. All changes are project-local.

## Trigger & Flow

1. User runs `/reflect` at any point (typically end of session)
2. Claude reviews the session context it already has
3. Claude identifies correction moments, discoveries, and patterns
4. Claude presents recommendations in two tiers:
   - **Recommended** - High confidence, directly tied to session events
   - **Consider** - Lower confidence or broader scope
5. User responds (approve all, cherry-pick, modify, reject)
6. Claude applies approved changes

## Update Targets

| Target | Location | Purpose |
|--------|----------|---------|
| CLAUDE.md | `./CLAUDE.md` | Project-specific guidance, conventions, gotchas |
| Skills | `./.claude/skills/` | Reusable prompts/workflows discovered during session |
| Docs | `./docs/` | Project documentation gaps identified |

**Scoping rule:** If a learning relates to a global skill (`~/.claude/skills/`), the recommendation is to copy that skill into the project's `.claude/skills/` directory first, then modify the local copy. Global files are never touched.

## Guiding Principles

- **Terse** - Minimal words, maximum signal
- **Tactical** - Specific and actionable, not abstract
- **Evidence-based** - Tied directly to a session event (quote or reference it)
- **Simplest thing possible** - One small improvement; seek to improve, not fix
- **Project-local only** - No changes to global config or skills

## Output Format

When `/reflect` runs, Claude presents recommendations like this:

```
## Recommended

1. [CLAUDE.md] Document that integration tests require `docker compose up` before running
2. [skill] Create a "db-migration" skill capturing the migration workflow we figured out
3. [CLAUDE.md] Note that the `/api/v2` routes expect snake_case, not camelCase

## Consider

4. [doc] The authentication flow could use a diagram in docs/auth.md
5. [skill] The debugging approach we used for memory leaks might be worth capturing
```

User responds naturally:
- "1 and 3" (approve specific items)
- "All recommended"
- "1, but make it shorter"
- "Skip for now"

Claude applies approved items and confirms what was updated.

## Implementation

Single file: `.claude/commands/reflect.md`

Contains a prompt that instructs Claude to:
1. Review the session for corrections, discoveries, and patterns
2. Apply the guiding principles (terse, tactical, evidence-based, simplest)
3. Present recommendations in the two-tier format
4. Wait for user approval before making changes
5. Apply only what's approved
