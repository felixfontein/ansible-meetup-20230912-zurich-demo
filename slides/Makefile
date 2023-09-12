SVGs = ansible

ALL = \
    $(SVGs:%=intermediate/%.pdf) \
    beamer.pdf

all: intermediate $(ALL)

intermediate:
	mkdir -p intermediate

clean:
	rm -f $(ALL)
	rm -rf intermediate

intermediate/%.pdf: source/%.svg
	inkscape $< --export-pdf=$@

# Presentation
beamer.pdf: source/beamer.tex source/*.png
	rubber --shell-escape -m pdftex -W all -I source --into intermediate $<
	cp intermediate/beamer.pdf .
