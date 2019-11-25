MAIN=main
CHAPTERS=intro.tex morphologies.tex electrical.tex synaptics.tex circuit.tex projections.tex software.tex title.tex 

all: pdf1 bibs pdf2

pdf1: clean ${MAIN}.tex refs.bib ${CHAPTERS}
	mkdir -p output/appendices_latex
	pdflatex -interaction=nonstopmode -halt-on-error -output-directory=./output ${MAIN}.tex

bibs:
	cp refs.bib output
	cd output; for i in intro synaptics morphologies projections software circuit composition electrical; do bibtex $$i; done; cd ..

pdf2:
	pdflatex -interaction=batchmode -halt-on-error -output-directory=./output ${MAIN}.tex
	pdflatex -interaction=batchmode -halt-on-error -output-directory=./output ${MAIN}.tex
	pdflatex -interaction=batchmode -halt-on-error -output-directory=./output ${MAIN}.tex

debug:
	pdflatex  -output-directory=./output ${MAIN}.tex 2>&1 | tee build.log

draft:
	mkdir -p output/appendices_latex
	pdflatex -output-directory=./output ${MAIN}.tex

clean:
	rm -rf output
