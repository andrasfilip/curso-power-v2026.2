# Simulation-Based Power Analysis

Quarto materials for the doctoral-level course
**Justificación del tamaño muestral y análisis de potencia estadística**
at CIMCYC, Universidad de Granada.

Instructors: Filip Andras, David López-García & David Sánchez Casasola.

## Before the first session: run the online task (~3–4 min)

Before the course starts, please complete this short online lexical-decision
task. It uses the same paradigm we will simulate and analyse throughout the
course, so you will arrive with a feel for what the data look like:

> **<https://exponline.ugr.es/publix/1164/start?batchId=1373&generalMultiple>**

It takes about **3–4 minutes** to finish. No installation, just click the link.

## What is in this repository

The materials are produced in two parallel formats:

- **Slide decks** (RevealJS) — for the live sessions.
- **Handouts** (long-form HTML) — for self-study, with full prose and tabsets.

Each of the nine course parts (1, 1.2, 2–9) has both a slide deck and a
handout. There is also one practical exercise paired with Part 1, and a
**Part 0 R primer** for participants who do not use R regularly.

## Folder structure

```
curso-power-v2026.2/
├── _simulations_final.Rproj  RStudio project (open this first)
├── custom.css                shared CSS for the Quarto slide decks
├── data/
│   ├── raw_data/             read-only data (ldt_data.csv)
│   └── processed_data/       precomputed power grids (.RData)
├── img/                      shared figures + logos used in slides and handouts
├── slides/                   conceptual deck (Spanish): .pptx + .pdf
└── scripts/                  source code + rendered handouts
    └── *.qmd                 10 slide decks + 10 handouts + 1 exercise + Part 0 primer
```

## Course parts (intended order)

| Part | Topic | Slide deck | Handout |
|------|-------|------------|---------|
| 0    | R básico — primer for those new to R | — | ✓ |
| 1    | Introduction & between-subjects design | ✓ | ✓ |
| 1.2  | Between-subjects design & linear modeling | ✓ | ✓ |
| 2    | Within-subjects design & linear modeling | ✓ | ✓ |
| 3    | Repeated measures | ✓ | ✓ |
| 4    | By-participant adjustments to the slope | ✓ | ✓ |
| 5    | Correlated slopes and intercepts | ✓ | ✓ |
| 6    | By-item varying intercepts | ✓ | ✓ |
| 7    | Modeling reaction time data (log-normal) | ✓ | ✓ |
| 8    | Power analysis across varying sample sizes and effect sizes | ✓ | ✓ |
| 9    | Recap — generative formulas and `gendat_*()` functions | ✓ | ✓ |

Exercise: `Exercise_1_Power_Simulation_Between_Subjects.qmd` is paired with
Part 1. Try it first, then check
`Exercise_1_Power_Simulation_Between_Subjects_solutions.qmd` for the worked
answers.

## Required R packages

```r
install.packages(c("tictoc", "MASS", "lme4", "lmerTest", "ggplot2",
                   "rio", "performance", "ggdist", "dplyr"))
```

## Rendering

Open `_simulations_final.Rproj` in RStudio first — it sets the working
directory to the project root automatically and the relative paths below
will work.

Render a single QMD from the scripts folder:

```bash
quarto render "scripts/1. Introduction and between-subject design.qmd"
```

Render everything at once:

```bash
./render_all.sh
```

## How the paths work

All paths are relative to the project root (`_simulations final/`):

- Images: `img/for_loop.png`, `img/bivariate_normal.jpg`, `img/plot_*.png`
- Data: `data/raw_data/ldt_data.csv`
- Precomputed RData: `data/processed_data/power_grid_*.RData`
- CSS: `../custom.css` (one level up from `scripts/`)

When you render a QMD with `quarto render scripts/<file>.qmd`, the resulting
HTML and `*_files/` folder are written next to the QMD inside `scripts/`.
This is intentional: the relative paths in the rendered HTML
(`../img/...`, `../data/...`) only resolve correctly when the HTML stays at
that level.

The contents of `output/slides/` and `output/exercises/` are the frozen
deliverables from earlier renders; fresh renders overwrite the HTML in
`scripts/`.
