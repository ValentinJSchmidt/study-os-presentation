# Course submissions (LaTeX)

Migrated from the markdown sources in the `study-os-thesis` repo
(`submission/project-journey-portfolio/` and `submission/individual-reflections/`).

| File | Submission |
|---|---|
| `project-journey-portfolio.tex` | Group submission — one PDF for the whole team |
| `individual-reflection-valentin.tex` | Individual submission — Valentin |
| `individual-reflection-domi.tex` | Individual submission — Domi |
|  `preamble.tex` | Shared style — plain black and white, `\input` by all three |

The two `assignment.md` prompt files were not migrated — they are the exercise
briefs, not deliverables.

## Build

```bash
make              # all three PDFs
make portfolio    # only the group portfolio
make reflections  # only the individual reflections
make clean        # drop aux files, keep PDFs
```

Each document compiles standalone with `latexmk -pdf <file>.tex`, but must be
built from this directory so `\input{preamble}` resolves.
