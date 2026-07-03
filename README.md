# StudyOS Thesis-Finder — Faculty Presentation

LaTeX Beamer slides that pitch the [study-os-thesis](../study-os-thesis)
project to faculty members: an agent-skill package that takes students from
vague interests to a well-prepared first contact with a fitting thesis
supervisor.

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

Output: `studyos-thesis-finder.pdf` (16:9, 11 slides).

Clean build artifacts with:

```bash
latexmk -c
```

## Content sources

The slides are distilled from the thesis repo's planning and research docs,
mainly `MASTERPLAN.md`, `STATUS.md`, `docs/research/product_positioning.md`,
and `docs/research/skill_architecture_summary.md`. Professor quotes and
statistics come from the 27-professor interview study summarized there;
names are intentionally omitted from the slides.
