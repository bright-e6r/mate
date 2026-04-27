---
description: Configure mate strictness level (light/medium/strict)
allowed-tools: ["Read", "Write", "AskUserQuestion"]
---

# Mate Setup

Configure the strictness level for the mate mentor persona. Strictness controls how many learning mechanisms are active during development.

**FIRST**: Use the Read tool to check if `.mate-config.json` exists in the current project directory. If it does, load it and show the current configuration.

---

## Configuration Flow

Ask the user one question:

### Q1: Strictness Level

- header: "Strictness"
- question: "Choose mate's strictness level. Higher strictness means more active learning interventions but slower development pace."
- multiSelect: false
- options:
  - "Strict (10/10)" — All learning mechanisms active. Maximum growth, slowest pace. Best for dedicated learning sessions.
  - "Medium (5/10) (Recommended)" — Core learning mechanisms active. Good balance of growth and pace. Prevents the most critical risks.
  - "Light (3/10)" — Minimum interventions. Fastest pace with essential protections only. Best when you need speed but still want to learn.

After selection, explain what's included in the chosen level.

---

## Strictness Definitions

### Strict (10/10) — All mechanisms active

All 11 learning interventions are enabled:

1. **Cognitive Surrender Prevention** — Always ask the user to think before revealing answers
2. **Triple Debt Awareness** — Check intent, cognitive, and technical debt at each phase
3. **Desirable Difficulty** — Create intentional struggle moments (active retrieval, generation effect)
4. **Assumption Propagation Blocking** — Surface and validate all assumptions before building
5. **Verification Thinking** — Teach how to define correctness and write meaningful tests
6. **Discrimination Training** — Build the user's ability to evaluate and critique code
7. **Fluency Illusion Warning** — Test genuine understanding through application questions
8. **Procedural Memory Formation** — Create opportunities for the user to write code themselves
9. **Chunking-Based Pattern Teaching** — Teach named patterns as unified concepts
10. **Naming and Abstraction Participation** — Engage the user in naming and abstraction design
11. **Tacit-to-Explicit Knowledge Conversion** — Practice turning vague intuition into specific, actionable language

### Medium (5/10) — Core mechanisms (Recommended)

5 learning interventions enabled:

1. **Cognitive Surrender Prevention** — Always ask the user to think before revealing answers
2. **Assumption Propagation Blocking** — Surface and validate all assumptions before building
3. **Verification Thinking** — Teach how to define correctness and write meaningful tests
4. **Desirable Difficulty** — Create intentional struggle moments (active retrieval, generation effect)
5. **Fluency Illusion Warning** — Test genuine understanding through application questions

Disabled: Triple Debt Awareness, Discrimination Training, Procedural Memory Formation, Chunking-Based Patterns, Naming/Abstraction Participation.

### Light (3/10) — Minimum effective dose

3 learning interventions enabled:

1. **Cognitive Surrender Prevention** — Always ask the user to think before revealing answers
2. **Verification Thinking** — Teach how to define correctness and write meaningful tests
3. **Assumption Propagation Blocking** — Surface and validate all assumptions before building

Disabled: Triple Debt Awareness, Discrimination Training, Procedural Memory Formation, Chunking-Based Patterns, Naming/Abstraction Participation, Tacit-to-Explicit Knowledge Conversion.

---

## Write Configuration

Write to `.mate-config.json` in the current project root:

```json
{
  "strictness": "medium",
  "enabledMechanisms": [
    "cognitive-surrender-prevention",
    "assumption-propagation-blocking",
    "verification-thinking",
    "desirable-difficulty",
    "fluency-illusion-warning"
  ],
  "disabledMechanisms": [
    "triple-debt-awareness",
    "discrimination-training",
    "procedural-memory-formation",
    "chunking-based-patterns",
    "naming-abstraction-participation",
    "tacit-to-explicit-conversion"
  ],
  "configuredAt": "<ISO 8601 timestamp>"
}
```

---

## After Writing

Say: "Mate configured with `[level]` strictness (`[N]/10` mechanisms active). Run `/mate:mate` to start your session."
