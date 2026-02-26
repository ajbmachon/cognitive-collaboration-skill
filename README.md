# Cognitive Collaboration Skill

A Claude Code skill providing twelve cognitive modes for bulletproofing decisions and expanding thinking.

## Installation

Install directly from GitHub in Claude Code:

```
/plugin marketplace add andremachon/cognitive-collaboration-skill
/plugin install cognitive-collaboration@cognitive-collaboration-dev
```

You can also specify an installation scope:

```
/plugin install cognitive-collaboration@cognitive-collaboration-dev --scope project
```

Scopes: `user` (default, all projects), `project` (shared with collaborators), `local` (you only, this repo).

Requires Claude Code 1.0.33 or later.

## Cognitive Modes

### CRITIQUE Modes (Stress-test ideas)

| # | Mode | Core Question |
|---|------|---------------|
| 1 | **Red Team** | "How would critics destroy this?" |
| 2 | **Steelman** | "What's the strongest case against me?" |
| 3 | **Pre-Mortem** | "Why did this fail?" (from the future) |
| 4 | **Assumptions** | "What am I taking for granted?" |
| 5 | **Biases** | "Am I fooling myself?" |

### EXPANSION Modes (Explore possibilities)

| # | Mode | Core Question |
|---|------|---------------|
| 6 | **First Principles** | "If I started fresh, would I do this?" |
| 7 | **Analogist** | "What patterns from other domains apply?" |
| 8 | **Scenario Weaver** | "What futures should I prepare for?" |
| 9 | **Perspective Shifter** | "How do different stakeholders see this?" |
| 10 | **Synthesizer** | "What's the throughline connecting these?" |
| 11 | **Option Generator** | "What alternatives haven't I considered?" |
| 12 | **Values Clarifier** | "What do I actually value vs. claim to?" |

## Usage

Invoke by asking Claude to use cognitive collaboration modes, or when preparing pitches, making decisions, stress-testing ideas, or exploring alternatives.

### Commands

- Type a number (1-12) to select a mode
- `*chain 4,1,3` - Run a sequence of modes (e.g., Assumptions -> Red Team -> Pre-Mortem)
- `*single` - Single response (skip verbalized sampling)
- `*quick` - Fast single-question analysis
- `*skip` - Bypass context gathering
- `*help` - Show the mode menu

### Suggested Chains

| Chain | Sequence | Best For |
|-------|----------|----------|
| Full Stress Test | 4 -> 1 -> 3 | Major proposals, strategic pivots |
| Opposition Analysis | 2 -> 1 | Debates, negotiations |
| Decision Audit | 5 -> 6 | Contentious decisions |
| Launch Prep | 3 -> 1 | Product launches |
| Expansion Sprint | 11 -> 7 -> 10 | Generating new ideas |
| Values Check | 12 -> 4 -> 6 | Personal/org decisions |

## Project Structure

```
skills/cognitive-collaboration/
  SKILL.md              # Main skill definition
  reference/            # Mode reference files
    red-team.md
    steelman.md
    pre-mortem.md
    assumptions.md
    biases.md
    first-principles.md
    analogist.md
    scenario-weaver.md
    perspective-shifter.md
    synthesizer.md
    option-generator.md
    values-clarifier.md
    shared-format.md
```

## License

MIT License - Copyright (c) 2025 Andre Machon. See [LICENSE](LICENSE) for details.

## Author

Andre Machon
