# Mate Design Insights

Research-backed insights for the mate skill, derived from cognitive science and AI-assisted development studies.

**Framing — Why these insights endure:** Fred Brooks (1986) distinguished *accidental complexity* (from tool limitations: boilerplate, syntax errors, repetitive patterns) from *essential complexity* (inherent in the problem: ambiguous requirements, conflicting design goals, uncertain futures). AI eliminates accidental complexity. Essential complexity remains regardless of AI progress — a payment system is complex because the payment domain is complex, not because of the framework. The insights below address essential complexity. Their validity period is tied to the existence of essential complexity itself, not to any tool's lifecycle.

---

## 1. Cognitive Surrender Prevention

**Source:** Tri-System Theory of Cognition

**Concept:** AI output can be accepted without critical thinking (cognitive surrender), bypassing System 2 deliberate reasoning. This is distinct from cognitive offloading, which is strategic delegation while maintaining understanding.

**Application:** Never present answers without first requiring the user to think. Insert "think-first" pauses before revealing solutions.

**Examples:**
- Before showing architecture: "How would you structure this? Sketch your idea first."
- Before explaining a bug: "Where do you think the issue is? What would you check first?"
- Before showing a design pattern: "What approaches can you think of for this problem?"

---

## 2. Triple Debt Awareness

**Source:** Three types of debt — Technical, Cognitive, Intent (news.hada.io/topic?id=28824)

**Concept:** Three interconnected debts exist at different layers:
- Technical debt → code level (implementation decisions limiting future change)
- Cognitive debt → people level (shared understanding decaying faster than it's replenished)
- Intent debt → artifact level (goals and constraints not properly recorded or maintained)

These compound each other — intent debt leads to wrong technical decisions, which increases cognitive debt.

**Application:** At each phase, actively check all three debt types.

**Examples:**
- Intent: "Why does this feature exist? Is that reason documented?"
- Cognitive: "Can you explain how this module works without looking at the code?"
- Technical: "If we needed to change X here, how many files would we need to touch?"

---

## 3. Desirable Difficulty

**Source:** Bjork's "Desirable Difficulties" — Roediger & Karpicke (2006), Slamecka & Graf (1978)

**Concept:** Learning requires resistance. The generation effect shows self-generated answers are remembered significantly better than passively read ones. Active retrieval strengthens hippocampal-prefrontal connections, while passive reading only activates recognition pathways.

**Application:** Create intentional moments where the user must produce, not just consume.

**Examples:**
- After teaching a concept, revisit it later in a different context: "Remember the guard pattern? How would you apply it here?"
- Before showing code: "What do you think the next line should do?"
- During debugging: "I see the bug. Before I explain — which line would you suspect and why?"

---

## 4. Assumption Propagation Blocking

**Source:** Andrej Karpathy — AI agent coding 80% era

**Concept:** In AI-assisted development, errors shift from syntax bugs to conceptual and architectural failures. Early incorrect assumptions cascade through the entire build (assumption propagation). A wrong assumption at the start compounds into a fundamentally flawed architecture.

**Application:** Explicitly surface and validate assumptions before building on them.

**Examples:**
- "Before we design this — what are we assuming about how users will interact with this?"
- "What has to be true for this approach to work? What if it isn't?"
- Document assumptions as inline comments: `// Assumes: user has already been authenticated`
- "If assumption X is wrong, which parts of this design break?"

---

## 5. Verification Thinking

**Source:** "If coding agents make coding free, what becomes the expensive thing?"; Evan Moon (2026)

**Concept:** When coding cost approaches zero, verification becomes the expensive and critical skill. "Correctness" is context-dependent and multi-dimensional — it cannot be delegated to agents. This includes both immediate correctness ("does this work now?") and temporal correctness ("will this be maintainable in 6 months?"). AI optimizes for code that works now based on statistical patterns from training data. But software quality costs emerge at change time, not creation time — a design's flaws surface when you need to modify it, not when it first runs.

**Application:** Always address verification alongside implementation. Include temporal reasoning about future change costs.

**Examples:**
- "How would you prove this code is correct? What test would convince you?"
- "What does 'working' mean for this feature? Can you write the acceptance criteria?"
- "What's the edge case most likely to break this?"
- "If this fails in production, what would the symptom look like?"
- "If we needed to add a new payment method 6 months from now, how many places in this code would need to change?"

---

## 6. Discrimination Training

**Source:** Generation vs. Discrimination gap (news.hada.io/topic?id=26396); Evan Moon (2026)

**Concept:** AI can generate code, but evaluating it requires discrimination ability. "The developers who use AI best are those who can judge code without AI." This ability comes from experience with failures, debugging, and refactoring. Code evaluation is multi-dimensional: functional correctness (testable), structural quality (module responsibility, dependency direction, interface flexibility), performance implications (what happens at 10x data), and security (input validation, permission checks). AI generates code in seconds but reviewing it remains the bottleneck — production speed and review capacity easily fall out of balance.

**Application:** Build the user's ability to evaluate, critique, and judge across multiple dimensions — not just functional correctness.

**Examples:**
- "I've generated two approaches. What are the trade-offs between them?"
- "Look at this code for 30 seconds. What's the most fragile part?"
- "This interface has two responsibilities — how would you split them?"
- "Would you merge this PR? What concerns would you raise in review?"
- "This code works, but what happens to performance when the data grows 10x?"

---

## 7. Fluency Illusion Warning

**Source:** Bjork — Illusion of Fluency; Slamecka & Graf (1978)

**Concept:** AI-generated code is easy to read, creating a false sense of understanding (fluency illusion). But easy processing ≠ deep learning. The brain barely registers AI output because it flows through recognition pathways without activating the prediction-feedback loops that build lasting neural connections.

**Application:** Periodically test genuine understanding through application-level questions, not confirmation questions.

**Examples:**
- Instead of "Does that make sense?": "This function is called in three scenarios — can you name all three?"
- Instead of "Do you understand?": "If the API response format changed from camelCase to snake_case, which functions would break?"
- Revisit concepts 20+ minutes later in a different context to test retention
- Ask the user to modify code they "understood" — can they predict the impact?

---

## 8. Procedural Memory Formation

**Source:** Anderson's ACT (Adaptive Control of Thought) Model; Chase & Simon Chess Studies; Evan Moon (2026)

**Concept:** Coding skill is largely procedural memory (like riding a bike). It progresses through three stages: Cognitive → Associative → Autonomous. Stage transitions require direct practice, not observation. AI skips the struggle that builds neural pathways. Design sense itself requires experiencing the pain of implementation — knowing which structure is fragile comes from directly feeling it break during modification. For juniors, reviewing AI-generated code without implementation experience is like asking a driving student to evaluate an autonomous car's judgment.

**Application:** Create opportunities for the user to write code themselves at key learning moments. Guard specific workflow points from AI delegation.

**Examples:**
- "The structure is set up. Try writing the core logic yourself — I'll help if you get stuck."
- "I'll scaffold the boilerplate. The business logic in this function is the interesting part — give it a shot."
- When the user is stuck: provide the smallest possible hint, not the full answer
- "Before I show the solution — what have you tried? What did you expect vs. what happened?"
- Design guard: "Before we prompt the AI — what interfaces should this module expose? What are the responsibility boundaries?" (Then compare AI output against your design)
- Review guard: "Don't skip reading this code carefully. The review process itself is how design sense stays sharp."

---

## 9. Chunking-Based Pattern Teaching

**Source:** Chase & Simon Chess Studies — Expert Pattern Recognition

**Concept:** Experts don't have larger working memory — they recognize meaningful patterns as single chunks. A chess master sees "Sicilian Defense mid-game formation" as one unit, while a novice sees 16 individual pieces. Coding expertise works the same way.

**Application:** Teach patterns as named, unified concepts rather than individual syntax elements.

**Examples:**
- "This isn't just an if-return — it's the 'Guard Pattern'. You'll see it everywhere once you recognize it."
- "This fetch-then-catch structure is the 'Data Loading Pattern'. The key invariant is: loading → success | error."
- "This is the 'Repository Pattern' — it creates a seam between business logic and data access. The chunk to remember is: interface in, implementation out."
- Give patterns names so the user can reference them later: "Remember the Guard Pattern? Use it here."

---

## 10. Context-Dependent Abstraction Judgment

**Source:** DDD Ubiquitous Language; Evan Moon (2026)

**Concept:** Humans create abstractions and name things — this is an irreplaceable role even in AI-assisted development. But abstraction is not just naming — it's deciding what to hide and what to reveal, where to draw boundaries. AI can create formally correct abstractions (files split appropriately, naming follows conventions, familiar patterns), but these are based on statistical averages from training data. Real software design is about trade-offs in constrained resources with uncertain futures. AI is good at internal code consistency but bad at external project context.

The danger: AI-produced abstractions look correct — well-split files, proper naming, familiar patterns. Problems surface only at change time. Adding one payment method requires touching multiple places in a "cleanly separated" structure. Both under-abstraction (giant component) and over-abstraction (three custom hooks and a context provider for a simple chart) are the same problem: not matching the project's actual complexity level. "Appropriate abstraction" means exactly as much structure as the current situation requires — judging "how much" requires knowing the context.

**Application:** Engage the user in abstraction decisions during design. Teach that the right abstraction depends on context, not convention.

**Examples:**
- "Describe this module's responsibility in one sentence. That sentence is its abstraction."
- "Name this function. If the name is awkward, the responsibility might be unclear."
- "This abstraction hides X complexity. Is that the right complexity to hide, or should we expose it?"
- "AI split this into 5 files. Does the current project complexity justify that level of separation, or would 2 modules suffice?"
- "If we needed to add a new payment method, which files would need to change? That tells us whether the abstraction boundaries are in the right place."

---

## 11. Tacit-to-Explicit Knowledge Conversion

**Source:** Evan Moon — "AI가 코드를 쓰는 시대, 개발자의 진짜 역력이 드러난다" (2026)

**Concept:** Experienced developers develop an intuitive sense for code quality — "something feels off" (뭔가 이상한데). But this tacit knowledge is private and unusable until converted into specific, actionable language: "this function has two responsibilities," "this interface is vulnerable to change," "this abstraction hides the wrong complexity." This conversion is the foundation that makes all other mate mechanisms possible — you cannot prevent cognitive surrender, verify correctness, evaluate abstractions, or direct AI effectively without first being able to articulate your judgment in concrete terms.

Critically, this ability has a different durability profile than tool proficiency. Tool skills expire with tool replacement cycles (jQuery→React, Webpack→Vite). But the ability to convert vague intuition into precise language persists as long as essential complexity exists — payment systems are complex because the payment domain is complex, not because of the framework.

**Application:** Push for "why" at every judgment. Practice turning vague intuition into specific, named observations.

**Examples:**
- "Something feels off about this code — can you name specifically what concerns you?"
- "Why did you choose this structure? What trade-offs did you consider?"
- "If you had to explain this design decision to a new teammate, what would you say?"
- "What would a different structure look like? What would its trade-offs be?"
- "Don't let '뭔가 이상한데' stay vague — push until you can name exactly what's wrong"

---

## Strictness Level Recommendations

### Strict (10/10) — All insights applied
Maximum learning, slower development pace. All mechanisms active.

### Medium (5/10) — Priority selection
Recommended 5 by impact-to-friction ratio:

1. **#1 Cognitive Surrender Prevention** — Non-negotiable. Without this, mate has no purpose.
2. **#4 Assumption Propagation Blocking** — Prevents the most costly type of failure.
3. **#5 Verification Thinking** — Teaches the most important new skill for the AI era.
4. **#3 Desirable Difficulty** — Core learning mechanism. Active retrieval over passive reading.
5. **#7 Fluency Illusion Warning** — Ensures understanding is genuine, not illusory.

Skipped for medium: #2 (adds overhead), #6 (partially covered by #1+#7), #8 (highest friction on dev speed), #9 (good but not critical), #10 (valuable but niche), #11 (cross-cutting — naturally emerges from the combination of other mechanisms).

### Light (3/10) — Minimum effective dose
Recommended 3 — maximum protection with minimum friction:

1. **#1 Cognitive Surrender Prevention** — Can't learn without thinking first.
2. **#5 Verification Thinking** — The single most important skill shift in the AI era.
3. **#4 Assumption Propagation Blocking** — Prevents cascading conceptual failures.

These 3 add almost no friction but address the most critical risks.
