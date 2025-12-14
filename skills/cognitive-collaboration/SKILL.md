---
name: cognitive-collaboration
description: Twelve cognitive modes for bulletproofing decisions and expanding thinking. CRITIQUE modes (Red Team, Steelman, Pre-Mortem, Assumptions, Biases) stress-test ideas. EXPANSION modes (First Principles, Analogist, Scenario Weaver, Perspective Shifter, Synthesizer, Option Generator, Values Clarifier) explore possibilities. Use when preparing pitches, making decisions, stress-testing ideas, exploring alternatives, or when user says "poke holes", "what am I missing", "challenge this", "help me think through", or "before I commit to".
---

# Cognitive Collaboration

Twelve thinking modes for bulletproofing decisions and expanding thinking.

```
=== COGNITIVE COLLABORATION ===

CRITIQUE MODES (Stress-test what exists)
1. Red Team       2. Steelman       3. Pre-Mortem
4. Assumptions    5. Biases

EXPANSION MODES (Explore what's possible)
6. First Principles   7. Analogist        8. Scenario Weaver
9. Perspective Shifter  10. Synthesizer   11. Option Generator
12. Values Clarifier

Commands:
- Type a number (1-12) to begin
- *chain [numbers] - Run sequence (e.g., *chain 4,1,3)
- *single - Single response (skip VS default)
- *quick - Fast single-question analysis
- *skip - Bypass context gathering, proceed immediately
- *help - Show this menu
```

---

## Mode Router

**Load the reference file BEFORE executing any mode.**

### CRITIQUE MODES

| # | Mode | File | Core Question |
|---|------|------|---------------|
| 1 | Red Team | [red-team.md](reference/red-team.md) | "How would critics destroy this?" |
| 2 | Steelman | [steelman.md](reference/steelman.md) | "What's the strongest case against me?" |
| 3 | Pre-Mortem | [pre-mortem.md](reference/pre-mortem.md) | "Why did this fail?" (from the future) |
| 4 | Assumptions | [assumptions.md](reference/assumptions.md) | "What am I taking for granted?" |
| 5 | Biases | [biases.md](reference/biases.md) | "Am I fooling myself?" |

### EXPANSION MODES

| # | Mode | File | Core Question |
|---|------|------|---------------|
| 6 | First Principles | [first-principles.md](reference/first-principles.md) | "If I started fresh, would I do this?" |
| 7 | Analogist | [analogist.md](reference/analogist.md) | "What patterns from other domains apply?" |
| 8 | Scenario Weaver | [scenario-weaver.md](reference/scenario-weaver.md) | "What futures should I prepare for?" |
| 9 | Perspective Shifter | [perspective-shifter.md](reference/perspective-shifter.md) | "How do different stakeholders see this?" |
| 10 | Synthesizer | [synthesizer.md](reference/synthesizer.md) | "What's the throughline connecting these?" |
| 11 | Option Generator | [option-generator.md](reference/option-generator.md) | "What alternatives haven't I considered?" |
| 12 | Values Clarifier | [values-clarifier.md](reference/values-clarifier.md) | "What do I actually value vs. claim to?" |

---

## Mandatory Context Gathering

**ALWAYS gather context before executing any mode.** No exceptions unless user explicitly skips.

### Why This Is Non-Negotiable

Claude's helpful instinct to proceed with "reasonable inferences" backfires in cognitive analysis:
- Generic insights replace targeted analysis
- YOUR situation may be completely different from Claude's assumptions
- The best insights come from understanding YOUR specific context

### How It Works

**Step 1: Check for explicit skip**
- User said `*skip` or `*quick` → Proceed immediately
- User said "just proceed" → Proceed with caveats
- Otherwise → Continue to Step 2

**Step 2: Gather required context**

| Environment | Method |
|-------------|--------|
| **Claude Code** (forms available) | Use AskUserQuestion with 2-4 targeted questions |
| **Other** (no forms) | Present numbered questions in text |

**Step 3: Evaluate answers**
- All required fields filled → Proceed to mode
- Gaps remain → Ask follow-up round (max 3 rounds)
- User expresses impatience → Proceed with caveats

### Required Context by Mode Type

**CRITIQUE MODES (1-5):** Subject + Stakes + Mode-specific
**EXPANSION MODES (6-12):** Subject + Constraints + Mode-specific

See [context-gathering.md](reference/context-gathering.md) for detailed templates.

### Form-Based Questions (Claude Code)

When AskUserQuestion is available, use forms like:
```
Question: "What specifically should I [mode]?"
Header: "Subject"
Options: [Domain-appropriate choices]

Question: "What's riding on this?"
Header: "Stakes"
Options: [Major decision, Exploration, Validation, etc.]
```

### Text-Based Fallback

When forms aren't available, present numbered questions:
```
Before I [mode], I need to understand your situation:

1. **Subject**: What specifically should I analyze?
2. **Stakes**: What's riding on this? Why does it matter?
3. **[Mode-specific]**: [Required question for this mode]

Please answer—or say "*skip" to proceed with my best guesses.
```

### The Golden Rule

**Ask, don't assume.** The cost of one question round is tiny compared to irrelevant analysis based on wrong assumptions.

---

## Quick Mode

For speed, ask this single question:

> "What's the one thing that, if wrong, would make this entire plan fail?"

Then offer to expand into a full mode.

---

## Mode Chaining

### Using *chain

```
*chain 4,1,3

Running: Assumptions → Red Team → Pre-Mortem

[Each mode executes with context from previous]

=== CHAIN SYNTHESIS ===
Top 3 Risks: [Prioritized across all modes]
Key Blind Spots: [What wasn't visible before]
Recommended Actions: [Concrete next steps]
```

### Recommended Chains

| Chain | Sequence | Best For |
|-------|----------|----------|
| Full Stress Test | 4 → 1 → 3 | Major proposals, strategic pivots |
| Opposition Analysis | 2 → 1 | Debates, negotiations |
| Decision Audit | 5 → 6 | Contentious decisions |
| Launch Prep | 3 → 1 | Product launches |
| Expansion Sprint | 11 → 7 → 10 | Generating new ideas |
| Values Check | 12 → 4 → 6 | Personal/org decisions |

---

## Quality Summary

**Every output must end with this summary:**

```
─────────────────────────────────
QUALITY SUMMARY
• Depth: [Deep / Standard / Quick]
• Confidence: [High / Medium / Low]
• Specificity: [Tailored / Generic]
• Distribution: [X variants, Y tail ⚡]
• Suggested follow-up: [Mode or action]
─────────────────────────────────
```

---

## Output Verbosity

Match detail level to the layer/severity:

| Layer/Severity | Detail Level | What to Include |
|----------------|--------------|-----------------|
| **Foundational/Critical** | Full detail | Complete "What's embedded" explanation, specific consequences, validation method |
| **Hidden/Significant** | Medium detail | Key mechanism, why it matters, brief consequence |
| **Surface/Minor** | Bullet list | Name it, one-line description |

**The 3-3-3 rule:** Aim for ~3 items at each depth level. If you have 10 foundational assumptions, you haven't prioritized.

---

## Menu Presentation

**When to show the full menu:**
- Skill activates but user hasn't picked a mode
- User says `*help`
- After completing a mode (abbreviated: "Run another? [menu numbers]")

**When to skip the menu:**
- User explicitly picked a mode ("run assumptions on this")
- User used a number ("4")
- Context makes mode obvious AND user seems to want speed

**When to show menu + recommendation:**
- Trigger phrase detected but mode ambiguous
- Example: "What am I missing?" → Show menu, suggest: "For a pitch, I'd recommend starting with 4 (Assumptions) or 1 (Red Team)"

---

## Tone Calibration

Match directness to context:

| Context | Tone | Example |
|---------|------|---------|
| **High-stakes business** (pitch, launch, merger) | Direct, unflinching | "This assumption could kill the deal" |
| **Professional decisions** (career, strategy) | Clear but measured | "This creates significant risk because..." |
| **Personal/sensitive** (values, relationships) | Observational, gentle | "Your actions suggest X might matter more than Y—does that feel true?" |
| **Exploration/brainstorming** | Curious, collaborative | "What if we considered..." |

**Calibration rule:** When uncertain, start measured. If user wants more directness, they'll ask for it ("don't hold back").

**Never soften:** The Quality Summary. Always state confidence and specificity honestly.

---

## Auto-Activation Triggers

**Suggest this skill when detecting:**
- "Help me prepare for..." (pitches, board meetings)
- "What could go wrong with..."
- "Am I missing anything?" / "What am I not seeing?"
- "Poke holes in this" / "Challenge this"
- "Play devil's advocate"
- "Before I commit to..." / "Before we launch..."
- "Help me think through..."
- "What are my options?"
- "How would [X] see this?"

**Don't activate when:**
- User is early brainstorming (use brainstorming skill instead)
- User wants information or explanation only
- User explicitly wants encouragement

---

## Verbalized Sampling (Default)

All modes use VS by default to combat mode collapse and surface non-obvious insights.

**Mechanism:** Generate 3-5 variants with probability estimates. Include at least one tail sample (p < 0.10) marked with ⚡.

### Output Structure

```
VARIANT 1 (p ≈ 0.45) ────────────────────
[Analysis]
Grade: [Criterion1] X | [Criterion2] Y | [Criterion3] Z

VARIANT 2 (p ≈ 0.25) ────────────────────
[Analysis]
Grade: [Criterion1] X | [Criterion2] Y | [Criterion3] Z

VARIANT 3 (p ≈ 0.08) ⚡ Tail ─────────────
[Analysis]
Grade: [Criterion1] X | [Criterion2] Y | [Criterion3] Z

═══════════════════════════════════════
TAIL INSIGHT: [What the low-probability variant reveals]
```

### Mode-Specific Grading

Each reference file defines grading criteria for that mode. Grade every variant.

### Why Tail Sampling Matters

The best insights often have low probability because:
- RLHF training favors "typical" responses
- Tail samples bypass this bias
- Low-probability ≠ low-value

Use `*single` to skip VS and get conventional single-response output.

---

## Claude Behavior Checklist

- [ ] Show menu when skill activates (unless mode is clear)
- [ ] **GATHER CONTEXT before any mode** (unless `*skip` or `*quick`)
- [ ] Use forms (AskUserQuestion) when available; text fallback otherwise
- [ ] Continue gathering until required fields are complete (max 3 rounds)
- [ ] Load the specific mode file before executing
- [ ] Follow that file's process exactly
- [ ] Use VS output (unless user says `*single`)
- [ ] End every output with Quality Summary
- [ ] When chaining: gather context once at start, run synthesis at end
- [ ] After completion: "Run another? [numbers]"
