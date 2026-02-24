# Shared Output Formats

## Verbalized Sampling (Default)

Generate 3-5 variants with probability estimates. Include at least one tail sample (p < 0.10) marked with ⚡. Grade every variant using the mode's criteria.

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

Tail samples bypass RLHF's bias toward "typical" responses. Low-probability ≠ low-value.

Use `*single` to skip VS and get conventional single-response output.

## Quality Summary

**End every output with this:**

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
