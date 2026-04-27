# Mate

A Claude Code plugin that activates a senior engineer mentor persona — teaching while building, combating cognitive debt, intent debt, and technical debt in AI-assisted development.

## Skills

### `/mate:mate` — Activate Mentor Mode

Activates a persistent mentor persona for the session. The mentor teaches through Socratic questioning, explains design reasoning, and breaks implementation into learnable chunks.

**Usage:**
- `/mate:mate` — Activate mate mode
- `/mate:mate stop` — Deactivate and return to normal mode

**Strictness levels** control how many learning interventions are active:
- **Light (3/10):** Cognitive Surrender Prevention, Verification Thinking, Assumption Blocking
- **Medium (5/10):** Light + Desirable Difficulty, Fluency Illusion Warning
- **Strict (10/10):** All mechanisms including Procedural Memory Formation, Chunking Patterns, Discrimination Training

### `/mate:setup` — Configure Strictness

Configure which learning mechanisms are active. Run this before `/mate:mate` to set your preference.

**Usage:**
- `/mate:setup` — Opens interactive configuration

## Installation

Install as a Claude Code plugin:

```bash
# Clone the repository
git clone https://github.com/bright-e6r/mate.git

# Link to your Claude Code plugins directory
ln -s $(pwd)/mate ~/.claude/plugins/cache/mate/mate/1.0.0

# Or copy the commands to your project
cp commands/mate.md /path/to/project/.claude/commands/mate.md
cp commands/setup.md /path/to/project/.claude/commands/setup.md
```

## How It Works

The plugin is grounded in cognitive science research on how AI-assisted development affects learning:

1. **Cognitive Surrender** — AI output can bypass critical thinking. Mate forces "think-first" pauses.
2. **Desirable Difficulty** — Learning requires resistance. Active retrieval beats passive reading (Bjork, Roediger & Karpicke).
3. **Assumption Propagation** — Early wrong assumptions cascade into architectural failures. Mate surfaces them early.
4. **Verification Thinking** — When coding is cheap, verification is expensive. Mate teaches how to define "correct."
5. **Fluency Illusion** — AI code reads easily but doesn't stick. Mate tests genuine understanding.

See [research/insights.md](research/insights.md) for the full research basis.

## Philosophy

AI agents accelerate development but create a gap between what gets built and what the developer understands. Mate closes that gap — making the development process itself a learning experience that builds lasting engineering judgment.
