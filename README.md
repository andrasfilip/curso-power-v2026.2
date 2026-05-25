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

The materials come in two formats:

- **Conceptual slides** (PDF, Spanish) in `slides/` — the big-picture
  introduction we project during the live sessions.
- **Handouts** (long-form, self-contained HTML, one per course part) in
  `scripts/` — these are the **primary deliverable** for self-study. 

There is one handout per course part (Parts 1, 1.2, 2–9), one practical
exercise paired with Part 1, and a **Part 0 R primer** for participants
who do not use R regularly.

## Folder structure

```
curso-power-v2026.2/
├── _simulations_final.Rproj  RStudio project (open this first)
├── README.md                 this file
├── data/
│   ├── raw_data/             read-only data (ldt_data.csv)
│   └── processed_data/       precomputed power grids
│                             (power_grid_2d.RData, power_grid_sub_eff.RData)
├── img/                      figures + logos used by the handouts
├── slides/                   conceptual decks (Spanish)
│   ├── 01_SLIDES_SUPERPOWER.pdf
│   ├── 02_SLIDES_SIMULACIONES_v2.pdf
│   └── 02_SLIDES_SIMULACIONES_v2.pptx
└── scripts/                  Quarto sources + rendered handouts
    ├── 0. Basic R primer.qmd / .html
    ├── 1. Introduction and between-subject design - handout.qmd / .html
    ├── 1.2 Between-subjects design and linear modeling - handout.qmd / .html
    ├── ... (Parts 2–9 follow the same pattern)
    └── Exercise_1_Power_Simulation_Between_Subjects.qmd / .html
```

The repository does **not** include the Exercise 1 solutions, the
`_archive/` folder, or the helper visualization scripts — these will be
shared separately. See `.gitignore` for the full exclusion list.

## Course parts (intended order)

| Part | Topic |
|------|-------|
| 0    | R básico — primer for those new to R |
| 1    | Introduction & between-subjects design |
| 1.2  | Between-subjects design & linear modeling |
| 2    | Within-subjects design & linear modeling |
| 3    | Repeated measures |
| 4    | By-participant adjustments to the slope |
| 5    | Correlated slopes and intercepts |
| 6    | By-item varying intercepts |
| 7    | Modeling reaction time data (log-normal) |
| 8    | Power analysis across varying sample sizes and effect sizes |
| 9    | Recap — generative formulas and `gendat_*()` functions |

Exercise: `Exercise_1_Power_Simulation_Between_Subjects.qmd` is paired with
Part 1. The worked-solutions file (`..._solutions.qmd`) is not in the repo
yet — it will be added after the live session.

## Required R packages

To run the code in the handouts you will need:

```r
install.packages(c("tictoc", "MASS", "lme4", "lmerTest", "ggplot2",
                   "rio", "performance", "ggdist", "dplyr"))
```

Part 0 (the R primer) needs only base R.

## Just want to read the materials?

Open any of the `scripts/*- handout.html` files in a web browser. They are
**self-contained** (`embed-resources: true`), so the single `.html` file
carries everything it needs — no images folder, no internet connection,
no Quarto install. You can also email them to a colleague as-is.

## Want to run the code yourself?

1. Clone this repository (or download it as a ZIP from GitHub).
2. Open `_simulations_final.Rproj` in RStudio. The working directory is
   set to the project root automatically, so all relative paths
   (`data/raw_data/ldt_data.csv`, `img/for_loop.png`, etc.) just work.
3. Open any `.qmd` file from `scripts/` and run the chunks interactively,
   or re-render the whole handout:

```bash
quarto render "scripts/1. Introduction and between-subject design - handout.qmd"
```

## How the paths work (for those who edit the source)

All paths inside the `.qmd` files are relative to the project root:

- Data: `data/raw_data/ldt_data.csv`
- Precomputed RData: `data/processed_data/power_grid_*.RData`

When you render a handout with `quarto render scripts/<file>.qmd`, the
rendered HTML appears next to the QMD inside `scripts/`. The handouts are
**self-contained** (`embed-resources: true`), so the single `.html` file
carries all the images and data it needs — nothing else is required to
share it.
