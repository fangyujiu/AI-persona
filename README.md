# 女娲 · nuwa-openclaw-skill

> Distill anyone's thinking into a runnable AI persona.

Adapted from [nuwa-skill](https://github.com/alchaincyf/nuwa-skill) for [OpenClaw](https://github.com/openclaw/openclaw) agents.

nuwa-openclaw-skill captures **how someone thinks** — not just what they said — and generates a Perspective Skill you can activate in any OpenClaw agent.

## What It Does

Give it a name (or even a vague request like "I want to think about decisions better"), and Nuwa will:

1. **Research** — 6 parallel agents investigate writings, interviews, social media, critics, key decisions, and life timeline
2. **Dual-track extraction** — 2 independent agents distill mental models, decision heuristics, and expression DNA, then cross-validate
3. **Build** — generates a complete Perspective Skill with role-play rules, sourced models, and expression guidelines
4. **Adversarial validation** — tests direction alignment, reverse induction, boundary behavior, and distinctiveness

The output is a ready-to-use OpenClaw skill that lets your agent **think and speak as that person**.

## Quick Start

### Install as OpenClaw Skill

```bash
# From ClawHub (when published)
openclaw skill install nuwa

# Or manually
cp -r nuwa/ ~/.openclaw/workspace-<agent>/skills/nuwa
```

### Usage

Just tell your agent:

- "蒸馏纳瓦尔" / "Distill Naval Ravikant"
- "造人：张一鸣" / "Build a persona for Elon Musk"
- "女娲" (triggers the skill)
- "我想提升决策质量" (Nuwa picks the best thinker for you)

Nuwa handles everything autonomously — research, extraction, validation — and delivers a complete skill in 30-60 minutes.

## Output Structure

```
output/
├── SKILL.md                    # The generated Perspective Skill
└── research/
    ├── 00-summary.md           # Source overview & quality assessment
    ├── 01-writings.md          # Books, essays, long-form
    ├── 02-interviews.md        # Podcasts, talks, interviews
    ├── 03-social.md            # Twitter/X, social platforms
    ├── 04-critics.md           # Criticism & counter-perspectives
    ├── 05-decisions.md         # Key decisions & reasoning
    ├── 06-timeline.md          # Life timeline & turning points
    ├── synthesis-A.md          # Extraction track A
    ├── synthesis-B.md          # Extraction track B
    ├── cross-validation.md     # A vs B comparison
    └── validation-report.md    # Adversarial test results
```

## How It Works

### Mental Model Validation (Triple Test)

A claim becomes a "mental model" only if it passes all three:

| Test | Question |
|------|----------|
| **Cross-domain recurrence** | Does it appear in 2+ different domains? |
| **Generative power** | Can you predict their stance on new problems? |
| **Exclusivity** | Is it distinctive, not generic wisdom? |

Fail any test → downgraded to heuristic. Fail all → discarded.

### Search Tool Cascade

Nuwa tries four levels of search, auto-falling back on failure:

1. **Tavily** (AI-optimized search API)
2. **ddgs + trafilatura** (free, no API key needed)
3. **Browser automation** (for JS-rendered / login-required pages)
4. **Model knowledge** (clearly labeled as unverified)

### Celebrity vs. Niche Adaptation

- **Well-known figures** (10+ primary sources): Standard skill (~3K tokens)
- **Niche figures** (<10 primary sources): Extended skill with key quotes archive (~6-8K tokens) so the model can accurately simulate even unfamiliar people

## Requirements

- [OpenClaw](https://github.com/openclaw/openclaw) agent runtime
- Internet access (for research phase)
- Python 3 with `ddgs` and `trafilatura` (auto-installed by search fallback script)

## File Overview

```
nuwa/
├── SKILL.md                          # Main skill definition
├── references/
│   ├── extraction-framework.md       # Methodology: triple validation, 6-axis research
│   ├── skill-template.md             # Output template for generated skills
│   └── perspectives-index.md         # Registry of distilled personas
└── scripts/
    └── search.sh                     # Fallback search script (ddgs + trafilatura)
```

## Acknowledgments

Inspired by [nuwa-skill](https://github.com/alchaincyf/nuwa-skill) by [花叔 (Huashu)](https://github.com/alchaincyf) — the original Nuwa for Claude Code that distills how anyone thinks. This project adapts the methodology for [OpenClaw](https://github.com/openclaw/openclaw) agents with parallel sub-agent research, dual-track cross-validation, and adversarial testing.

## License

MIT
