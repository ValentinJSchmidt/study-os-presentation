# Build the course submissions.
#   make            build all PDFs
#   make portfolio  build only the group portfolio
#   make clean      remove LaTeX aux files (keeps PDFs)
#   make distclean  remove aux files and PDFs

DOCS = project-journey-portfolio individual-reflection-valentin individual-reflection-domi
LATEXMK = latexmk -pdf -interaction=nonstopmode -halt-on-error

all: $(DOCS:=.pdf)

%.pdf: %.tex preamble.tex
	$(LATEXMK) $<

portfolio: project-journey-portfolio.pdf
reflections: individual-reflection-valentin.pdf individual-reflection-domi.pdf

clean:
	latexmk -c $(DOCS:=.tex)

distclean:
	latexmk -C $(DOCS:=.tex)

.PHONY: all portfolio reflections clean distclean
