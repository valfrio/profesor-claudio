# Profesor Claudio

**Claude Code skill for technical learning based on cognitive science.**

A learning coach that implements 7 evidence-backed techniques from cognitive science meta-analyses. Designed to be used with Claude Code as a one-on-one tutor — solving Bloom's 2 Sigma problem at zero marginal cost.

---

## What it does

Profesor Claudio is a Claude Code skill + wizard command that turns any technical learning session into a structured, science-backed process. Instead of explaining content and hoping it sticks, it forces active retrieval, calibrates metacognition, progressively removes scaffolding, and spaces review over time.

It works for any technical topic: programming languages, frameworks, architectures, DevOps tools, AI/ML stacks, or any subject where you need durable understanding — not just familiarity.

> The skill operates in Spanish. The wizard, study sessions, and generated files are all in Spanish.

---

## Scientific basis

All techniques are backed by meta-analyses with large effect sizes. See [`research/`](research/) for the full report.

> **Note:** The research document in `research/` is written in Spanish.

| Technique | Source | Effect Size |
|---|---|---|
| Retrieval Practice | Adesope et al. 2017, 217 studies | d = 0.62 |
| Spaced Practice | Latimier et al. 2020, 271 studies | d = 0.60 |
| Worked Examples + Fading | CLT meta-analysis 2024; Cooper & Sweller | d = 0.57 |
| Self-Explanation | Bisra et al. 2017 meta-analysis | d = 0.55 |
| Interleaved Practice | Rohrer et al. 2022; npj 2021 | d = 0.42 |
| Project-Based Learning | Xu & Liu 2023, 66 studies | SMD = 0.44 |
| Deliberate Practice | Ericsson et al. 1993 | High (qualitative) |

Theoretical framework: **Cognitive Load Theory** (Sweller, 1988). Goal: minimize extrinsic cognitive load, maximize germane load.

---

## How it works

Learning is organized in **5 phases**:

| Phase | Name | What happens |
|---|---|---|
| 1 | Orientation | Mental map of the domain before entering details |
| 2 | Worked Examples | Scaffolded examples that fade as expertise grows |
| 3 | Fading + Seed Project | Completion problems + real project starts here |
| 4 | Deliberate Practice | Micro-exercises targeting weak points specifically |
| 5 | Spaced Maintenance | Reviews at 1→3→7→14→30 day intervals |

Each concept cycle within a phase follows this exact sequence:

```
1. Activation       → You explain what you think it is before being taught anything
2. Worked Example   → Scaffolded to your current expertise level
3. Elaboration      → "Why does this work? What problem does it solve?"
4. Retrieval Check  → Explain it from memory, no notes
5. Metacognition    → "How confident are you? (0–100%)" BEFORE the answer is revealed
```

**Scaffolding fading** (Expertise Reversal Effect): scaffolding level changes as you progress:

| Level | Strategy |
|---|---|
| Absolute beginner | Complete worked example + line-by-line explanation |
| Beginner | Partial example with gaps to fill |
| Intermediate | Structure/spec only — you build the rest |
| Advanced | Open problem, no scaffolding |

---

## Installation

### 1. Install the skill

Copy [`skill/SKILL.md`](skill/SKILL.md) to your Claude Code skills directory:

```bash
# macOS / Linux
mkdir -p ~/.claude/skills/tech-study
cp skill/SKILL.md ~/.claude/skills/tech-study/SKILL.md

# Windows (PowerShell)
mkdir -Force "$env:USERPROFILE\.claude\skills\tech-study"
cp skill\SKILL.md "$env:USERPROFILE\.claude\skills\tech-study\SKILL.md"
```

### 2. Install the wizard command

Copy [`command/profesor-claudio.md`](command/profesor-claudio.md) to your Claude Code commands directory:

```bash
# macOS / Linux
cp command/profesor-claudio.md ~/.claude/commands/profesor-claudio.md

# Windows (PowerShell)
cp command\profesor-claudio.md "$env:USERPROFILE\.claude\commands\profesor-claudio.md"
```

### 3. Restart Claude Code

Restart Claude Code to index the new command. Then run `/profesor-claudio` in any session.

---

## Usage

```
/profesor-claudio
```

The wizard asks 5 questions:

1. **Topic** — What are you studying? Load an existing plan file or describe the topic.
2. **Level** — Absolute beginner / Beginner / Intermediate / Advanced
3. **Time available** — 30 min / 1h / 2h / open session
4. **Support files** — Which optional files to generate:
   - `notes-[topic].md` — updated after each concept with your own Feynman explanation
   - `planning-[topic].md` — phase calendar with spaced repetition dates
   - `progress-[topic].md` — concept tracker, metacognition log, project status
5. **Starting point** — From the beginning / continue / spaced review session

After confirming the setup, the study session starts immediately.

---

## What Claude does (and does NOT do)

| Claude DOES | Claude does NOT |
|---|---|
| Ask you to explain concepts before teaching them | Explain first, test later |
| Ask confidence level (0–100%) before revealing correctness | Reveal answers without a metacognition check |
| Give one hint when you fail — not the answer | Give the answer when you fail |
| Progressively remove scaffolding as you advance | Keep giving full worked examples indefinitely |
| Mix previous concepts into every exam (interleaving) | Test only the most recent concept |
| Increase difficulty when sessions feel too easy | Let comfortable sessions continue unchallenged |
| Track failed concepts for deliberate practice targeting | Treat all concepts equally regardless of failure history |

---

## Techniques that are explicitly prohibited

Per Dunlosky et al. (2013), the following have **low utility** despite being widely used. Claude will never suggest them:

| Technique | Why it fails |
|---|---|
| Re-reading documentation | Produces familiarity, not retrieval |
| Highlighting / underlining | No active processing |
| Passive summarizing | Only benefits those who already know the material |
| Watching tutorials without active output | Creates illusion of learning |

---

## Repository structure

```
profesor-claudio/
├── README.md
├── skill/
│   └── SKILL.md                    # Claude Code skill definition (v2.0)
├── command/
│   └── profesor-claudio.md         # Wizard command (/profesor-claudio)
└── research/
    └── Metodología Científica      # Scientific basis PDF (Spanish)
        para Aprender Contenido
        Técnico.pdf
```

---

## License

MIT
