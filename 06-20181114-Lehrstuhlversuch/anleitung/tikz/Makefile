all: build/overview.pdf build/imgParam.pdf build/shower.pdf

build:
	mkdir -p $@

build/shower.pdf: shower.tex | build
	latexmk --lualatex --output-directory=build --halt-on-error --interaction=nonstopmode \
		$<
	pdfcrop $@ $@

build/hillas.pdf: hillas.tex | build
	latexmk --pdf --output-directory=build --halt-on-error --interaction=nonstopmode \
		$<

build/theta2.pdf: theta2.tex | build
	latexmk --pdf --output-directory=build --halt-on-error --interaction=nonstopmode \
		$<

build/imgParam.pdf: imgParam.tex | build
	latexmk --pdf --output-directory=build --halt-on-error --interaction=nonstopmode \
		$<

build/overview.pdf: overview.tex build/hillas.pdf build/theta2.pdf | build
	latexmk --pdf --output-directory=build --halt-on-error --interaction=nonstopmode \
		$<

FORCE:

clean:
	rm -rf build

.PHONY: all clean FORCE
