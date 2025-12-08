# session-reflection

A Claude Code plugin that enables self-learning by reviewing sessions and recommending updates to project documentation.

## Installation

Copy the command file to your project's `.claude/commands/` directory:

```bash
mkdir -p .claude/commands
curl -o .claude/commands/reflect.md https://raw.githubusercontent.com/nmix/session-reflection/main/.claude/commands/reflect.md
```

Or clone and copy manually:

```bash
git clone https://github.com/nmix/session-reflection.git
cp session-reflection/.claude/commands/reflect.md your-project/.claude/commands/
```

## Usage

Run `/reflect` at the end of a Claude Code session to trigger self-reflection. Claude will:

1. Review the session for corrections, discoveries, and patterns
2. Present recommendations in two tiers (Recommended / Consider)
3. Wait for your approval before making changes
4. Apply only the approved updates to CLAUDE.md, skills, or docs