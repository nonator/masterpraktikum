BUILD_FILES = $(addprefix build/, \
	$(addsuffix .pdf, \
		aufspaltungen \
		aufbau \
		dublett \
		auswahlregeln \
		transparenz \
		resonanz \
	) \
)

OUT_DIR = build
TEX_CMD = latexmk \
	--pdf \
	--output-directory=$(OUT_DIR) \
	--halt-on-error \
	--interaction=nonstopmode
PREVIEW_CMD = \
	$(TEX_CMD) --pvc


all: build/main.pdf

build/resonanz.pdf: anleitung_V21_OptischePumpen.pdf | build
		gs -sDEVICE=pdfwrite -dNOPAUSE -dBATCH -dSAFER \
		-dFirstPage=11 \
		-dLastPage=11 \
		-sOutputFile=$@ $<
		pdfcrop --bbox "100 110 600 250"  $@ $@
		pdfcrop $@ $@


build/transparenz.pdf: anleitung_V21_OptischePumpen.pdf | build
		gs -sDEVICE=pdfwrite -dNOPAUSE -dBATCH -dSAFER \
		-dFirstPage=8 \
		-dLastPage=8 \
		-sOutputFile=$@ $<
		pdfcrop --bbox "0 370 420 530"  $@ $@
		pdfcrop $@ $@


build/auswahlregeln.pdf: anleitung_V21_OptischePumpen.pdf | build
		gs -sDEVICE=pdfwrite -dNOPAUSE -dBATCH -dSAFER \
		-dFirstPage=6 \
		-dLastPage=6 \
		-sOutputFile=$@ $<
		pdfcrop --bbox "0 470 420 677"  $@ $@
		pdfcrop $@ $@


build/dublett.pdf: anleitung_V21_OptischePumpen.pdf | build
		gs -sDEVICE=pdfwrite -dNOPAUSE -dBATCH -dSAFER \
		-dFirstPage=5 \
		-dLastPage=5 \
		-sOutputFile=$@ $<
		pdfcrop --bbox "0 125 600 295"  $@ $@
		pdfcrop $@ $@


build/aufbau.pdf: anleitung_V21_OptischePumpen.pdf | build
		gs -sDEVICE=pdfwrite -dNOPAUSE -dBATCH -dSAFER \
		-dFirstPage=16 \
		-dLastPage=16 \
		-sOutputFile=$@ $<
		pdfcrop --bbox "0 385 600 650"  $@ $@
		pdfcrop $@ $@


build/aufspaltungen.pdf: anleitung_V21_OptischePumpen.pdf | build
		gs -sDEVICE=pdfwrite -dNOPAUSE -dBATCH -dSAFER \
		-dFirstPage=4 \
		-dLastPage=4 \
		-sOutputFile=$@ $<
		pdfcrop --bbox "0 160 600 545"  $@ $@
		pdfcrop $@ $@


anleitung_V21_OptischePumpen.pdf:
	wget http://129.217.224.2/HOMEPAGE/PHYSIKER/MASTER/SKRIPT/V21n_TeachSpin_new.pdf -q \
		--user TUDoFP --password WS1819 -O $@


build/main.pdf: $(BUILD_FILES) FORCE | build
	TEXINPUTS=build: BIBINPUTS=build: max_print_line=1048576 \
	$(TEX_CMD) main.tex


preview: $(BUILD_FILES) FORCE | build
	TEXINPUTS=build: BIBINPUTS=build: max_print_line=1048576 \
	$(PREVIEW_CMD) main.tex


FORCE:


build:
	@mkdir -p build


clean:
	rm -rf *.pdf build


.PHONY: all clean FORCE preview