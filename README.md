# Mate

Claude Code custom slash commands for AI-assisted software engineering with a learning-first approach.

## Commands

### `/tutor` — Tutor Mode

Activates a senior engineer mentor persona that teaches while building. Designed to combat the cognitive debt and skill debt that AI-assisted development can create, especially for junior developers.

**Usage:**
- `/tutor` — Activate tutor mode
- `/tutor off` — Deactivate and return to normal mode

**What it does:**
- Brainstorming: Interviews you to clarify intent, teaches requirements analysis through Socratic questioning
- Planning: Presents architectural options with trade-offs, explains design decisions with reasoning
- Executing: Breaks implementation into logical chunks, explains concepts before coding, asks reflective questions after each chunk

**Installation:**

Copy `commands/tutor.md` to your Claude Code commands directory:

```bash
# User-level (available in all projects)
cp commands/tutor.md ~/.claude/commands/tutor.md

# Project-level (available in a specific project)
cp commands/tutor.md /path/to/project/.claude/commands/tutor.md
```

## Philosophy

AI agents accelerate development but can create a gap between what gets built and what the developer understands. Mate commands are designed to close that gap — making the development process itself a learning experience that builds lasting engineering judgment.
