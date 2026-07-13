# StudyOS Thesis-Finder — Presentation

LaTeX Beamer slides for the [study-os-thesis](../study-os-thesis)
project: a **database-less, portable agent-skill package** that takes students
from vague interests to a well-prepared first contact with a fitting thesis
supervisor, across all faculties of the University of Tübingen and BW companies.

The deck tells the project story — the 27-professor research, the pivot
away from a hosted database app, the two-track skill architecture, and where
the project stands and is heading.

## Requirements

You need a TeX distribution with Beamer and the Metropolis theme:

- **TeX Live** (recommended: the full scheme, which includes everything below)
  - `beamer`
  - `beamertheme-metropolis`
  - `pgf` / TikZ (for the diagrams)
  - `booktabs`
  - `fira` fonts (optional — Metropolis falls back to standard fonts under
    `pdflatex`; Fira Sans is only picked up automatically with
    `xelatex`/`lualatex`)
- **latexmk** (ships with TeX Live)

On Debian/Ubuntu, a sufficient install is:

```bash
sudo apt install texlive-latex-extra texlive-fonts-extra latexmk
```

Or install TeX Live directly from [tug.org/texlive](https://www.tug.org/texlive/)
(this repo was built with TeX Live 2025).

## Build

```bash
latexmk -pdf studyos-thesis-finder.tex
```

Output: `studyos-thesis-finder.pdf` (16:9, 12 slides).

Useful variants:

```bash
latexmk -pdf -pvc studyos-thesis-finder.tex   # watch mode: rebuild on save
latexmk -c                                    # remove build artifacts (keeps the PDF)
latexmk -C                                    # remove build artifacts including the PDF
```

## Presenting

Use [pympress](https://github.com/pympress/pympress) to present the PDF:
it gives you a presenter console (current + next slide, timer, notes) on
your screen while the audience sees only the slides.

```bash
sudo apt install pympress    # or: pipx install pympress
pympress studyos-thesis-finder.pdf
```

## Editing the slides

Everything lives in the single file `studyos-thesis-finder.tex`:

- **Presenter and date:** edit the `\author{...}`, `\institute{...}`, and
  `\date{...}` lines near the top — they currently hold placeholders
  ("StudyOS Team", "July 2026").
- **Colors:** the two accent colors are defined once as `sosAccent` and
  `sosDark` (`\definecolor` near the top); change them there and the
  progress bar, frame titles, diagrams, and highlights follow.
- **Slides:** each slide is a `\begin{frame}{Title} ... \end{frame}` block;
  add, remove, or reorder blocks freely. The two diagrams (the one-entry /
  two-track flow, and the two-pass search method) are inline TikZ pictures
  inside their frames.
- **Overflow check:** after larger edits, run the build and look for
  `Overfull \vbox` warnings in `studyos-thesis-finder.log` — they mean a
  slide's content is taller than the frame. (One harmless warning on the
  title slide comes from the Metropolis theme itself.)

To eyeball all slides as images without opening a PDF viewer:

```bash
pdftoppm -png -r 80 studyos-thesis-finder.pdf slide
```

## Content sources

The slides are distilled from the thesis repo's planning and history docs,
mainly `MASTERPLAN.md`, `README.md`, `CHANGELOG.md`, the curated
`docs/thesis-report/` narrative (esp. `01-the-pivot/` and
`03-hardening-and-evaluation/`), and the evaluation scorecard under
`findings/no_db_universal_skill/`. Professor quotes and statistics come from
the 27-professor interview study summarized there; names are intentionally
omitted from the slides.
