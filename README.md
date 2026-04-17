# Profesor Claudio

**Claude Code skill for technical learning based on cognitive science.**

A learning coach that implements 7 evidence-backed techniques from cognitive science meta-analyses. Designed to be used with Claude Code as a one-on-one tutor — solving Bloom's 2 Sigma problem at zero marginal cost.

---

## What it does

Profesor Claudio is a Claude Code skill + wizard command that turns any technical learning session into a structured, science-backed process. Instead of explaining content and hoping it sticks, it forces active retrieval, calibrates metacognition, progressively removes scaffolding, and spaces review over time.

It works for any technical topic: programming languages, frameworks, architectures, DevOps tools, AI/ML stacks, or any subject where you need durable understanding — not just familiarity.

---

## Scientific basis

All techniques are backed by meta-analyses with large effect sizes. See [`research/`](research/) for the full report.

| Technique | Source | Effect Size |
|---|---|---|
| Retrieval Practice | Adesope et al. 2017, 217 studies | d = 0.62 |
| Spaced Practice | Latimier et al. 2020, 271 studies | d = 0.60 |
| Worked Examples + Fading | CLT meta-analysis 2024; Cooper & Sweller | d = 0.57 |
| Self-Explanation | Bisra et al. 2017 meta-analysis | d = 0.55 |
| Interleaved Practice | Rohrer et al. 2022; npj 2021 | d = 0.42 |
| Project-Based Learning | Xu & Liu 2023, 66 studies | SMD = 0.44 |
| Deliberate Practice | Ericsson et al. 1993 | High (qualitative) |

Theoretical framework: **Cognitive Load Theory** (Sweller, 1988). Objective: minimize extrinsic cognitive load, maximize germane load.

---

## How it works

The skill organizes learning in **5 phases**:

| Phase | Name | What happens |
|---|---|---|
| 1 | Orientación | Mental map of the domain before entering details |
| 2 | Worked Examples | Scaffolded examples that fade as expertise grows |
| 3 | Fading + Proyecto Semilla | Completion problems + real project starts here |
| 4 | Práctica Deliberada | Micro-exercises targeting weak points specifically |
| 5 | Mantenimiento Espaciado | Spaced reviews at 1→3→7→14→30 day intervals |

Each concept cycle within a phase follows this exact sequence:

```
1. Activación          → You explain what you think it is before being taught
2. Worked Example      → Scaffolded to your current expertise level
3. Elaborative Interr. → "Why does this work? What problem does it solve?"
4. Retrieval Check     → Explain it from memory, no notes
5. Metacognition       → "How confident are you? (0–100%)" BEFORE answer is revealed
```

**Andamiaje fading** (Expertise Reversal Effect): the scaffolding level changes as you progress:

```
Novato absoluto  → Complete worked example + line-by-line explanation
Principiante     → Partial example with gaps to fill
Intermedio       → Structure/spec only — you build the rest
Avanzado         → Open problem, no scaffolding
```

---

## Installation

### 1. Install the skill

Copy [`skill/SKILL.md`](skill/SKILL.md) to your Claude Code skills directory:

```bash
# macOS / Linux
mkdir -p ~/.claude/skills/tech-study
cp skill/SKILL.md ~/.claude/skills/tech-study/SKILL.md

# Windows
mkdir -p $env:USERPROFILE\.claude\skills\tech-study
cp skill\SKILL.md $env:USERPROFILE\.claude\skills\tech-study\SKILL.md
```

### 2. Install the wizard command

Copy [`command/profesor-claudio.md`](command/profesor-claudio.md) to your Claude Code commands directory:

```bash
# macOS / Linux
cp command/profesor-claudio.md ~/.claude/commands/profesor-claudio.md

# Windows
cp command\profesor-claudio.md $env:USERPROFILE\.claude\commands\profesor-claudio.md
```

### 3. Reload Claude Code

Restart Claude Code or open a new session. The command will appear in the skill list.

---

## Usage

In any Claude Code session, run:

```
/profesor-claudio
```

The wizard will ask 5 questions:

1. **Tema** — What are you studying? (load an existing plan or describe the topic)
2. **Nivel** — Novato absoluto / Principiante / Intermedio / Avanzado
3. **Tiempo** — 30 min / 1h / 2h / sesión libre
4. **Archivos** — Which support files to generate (optional):
   - `notas-[tema].md` — updated after each concept with your Feynman explanation
   - `planning-[tema].md` — phase calendar with spaced repetition dates
   - `progreso-[tema].md` — concept tracker, metacognition log, project status
5. **Punto de inicio** — From the beginning / continue / spaced review session

After confirming, the session starts immediately.

---

## What Claude does (and does NOT do)

| Claude DOES | Claude does NOT |
|---|---|
| Ask you to explain concepts before teaching them | Explain first, test later |
| Ask "¿cómo de seguro estás?" before revealing if you're right | Tell you if you're right without a confidence check |
| Give one hint when you fail — not the answer | Give the answer when you fail |
| Progressively remove scaffolding as you advance | Keep giving full examples indefinitely |
| Mix previous concepts into every exam (interleaving) | Test only the most recent concept |
| Tell you when difficulty is too low and increase it | Let comfortable sessions continue unchallenged |
| Track which concepts you failed for deliberate practice | Treat all concepts equally regardless of failure history |

---

## Techniques that are explicitly prohibited

Per Dunlosky et al. (2013), the following have **low utility** despite being popular. Claude will never suggest them:

- Re-reading documentation
- Highlighting / underlining
- Summarizing passively
- Watching tutorials without active output

---

## Files

```
profesor-claudio/
├── README.md                          # This file
├── skill/
│   └── SKILL.md                       # Claude Code skill definition (v2.0)
├── command/
│   └── profesor-claudio.md            # Wizard command (/profesor-claudio)
└── research/
    └── Metodología Científica para    # Scientific basis (PDF, Spanish)
        Aprender Contenido Técnico.pdf
```

---

## Research

The full scientific report is in [`research/`](research/). It covers:

- Cognitive Load Theory (Sweller, 1988) — why technical learning fails
- The Forgetting Curve (Ebbinghaus) — 50–80% lost in 24–48h without structured review
- The Illusion of Competence — why "I understand it" after reading is not real learning
- 7 techniques with meta-analysis backing and concrete technical application
- The 5-phase integrated methodology
- Bloom's 2 Sigma Problem — why 1-on-1 tutoring produces +2 standard deviations of gain
- Instructions for implementing this methodology with an AI tutor

---

## License

MIT
