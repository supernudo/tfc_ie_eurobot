###########################################################################
# 
# Makefile to generate both book.pdf and anteproyecto.pdf
#
# $Id: Makefile,v 1.9 2014/01/15 01:06:40 macias Exp $
#
# By:
#  + Javier Mac�as-Guarasa. 
#    Departamento de Electr�nica
#    Universidad de Alcal�
#  + Roberto Barra-Chicote. 
#    Departamento de Ingenier�a Electr�nica
#    Universidad Polit�cnica de Madrid   
# 
# Based on original sources by Roberto Barra, Manuel Oca�a, Jes�s Nuevo,
# Pedro Revenga, Fernando Herr�nz and Noelia Hern�ndez. Thanks a lot to
# all of them, and to the many anonymous contributors found (thanks to
# google) that provided help in setting all this up.
#
# See also the additionalContributors.txt file to check the name of
# additional contributors to this work.
#
# If you think you can add pieces of relevant/useful examples,
# improvements, please contact us at (macias@depeca.uah.es)
#
# Copyleft 2013
#
###########################################################################

ROOT_FILENAME=book
ROOT_ANTEPROYECTO_FILENAME=anteproyecto
ROOT_PRESENTACION_FILENAME=presentation
TEX_FILE = $(ROOT_FILENAME).tex
TEX_ANTEPROYECTO_FILE = $(ROOT_ANTEPROYECTO_FILENAME).tex
TEX_PRESENTACION_FILE = $(ROOT_PRESENTACION_FILENAME).tex
RUBBER_TOOL=rubber
LATEXMK_TOOL=latexmk
EPSPDF_TOOL=epspdf
RM=rm -f

###########################################################################
# Support to automagically compile dia+svg files. Adapt to your own needs
DIA_SOURCES=$(wildcard diagrams/*.dia)
SVG_SOURCES=$(wildcard diagrams/*.svg)
EPS_SOURCES=$(wildcard eps/*.eps) $(wildcard ALLcurvesROC-AV16.3/*.eps) $(wildcard ALLcurvesROC-HIFI-MM1/*.eps)

PDFS_FROM_DIA=$(patsubst %.dia,%.pdf,$(DIA_SOURCES)) 
PDFS_FROM_SVG=$(patsubst %.svg,%.pdf,$(SVG_SOURCES)) 
PDFS_FROM_EPS=$(patsubst %.eps,%.pdf,$(EPS_SOURCES)) 

DUMMY_TARGETS=pdf_dia_done pdf_svg_done pdf_eps_done

all: $(DUMMY_TARGETS)
#	$(RUBBER_TOOL) -f -d $(TEX_ANTEPROYECTO_FILE)
#	$(RUBBER_TOOL) -f -d $(TEX_ANTEPROYECTO_FILE)
	$(RUBBER_TOOL) -f -d $(TEX_FILE)
	makeglossaries $(ROOT_FILENAME)
	$(RUBBER_TOOL) -f -d $(TEX_FILE)
	$(RUBBER_TOOL) -f -d $(ROOT_PRESENTACION_FILENAME)

anteproyecto: $(TEX_ANTEPROYECTO_FILENAME)
	$(RUBBER_TOOL) -f -d $(TEX_ANTEPROYECTO_FILE)
	$(RUBBER_TOOL) -f -d $(TEX_ANTEPROYECTO_FILE)

anteproyecto_latexmk: $(TEX_ANTEPROYECTO_FILENAME)
	$(LATEXMK_TOOL) -pdf -pdflatex="pdflatex -interactive=nonstopmode" -use-make $(TEX_ANTEPROYECTO_FILE)
	$(LATEXMK_TOOL) -pdf -pdflatex="pdflatex -interactive=nonstopmode" -use-make $(TEX_ANTEPROYECTO_FILE)

presentacion: $(TEX_PRESENTACION_FILE_FILE)
	$(RUBBER_TOOL) -f -d $(TEX_PRESENTACION_FILE)
	$(RUBBER_TOOL) -f -d $(TEX_PRESENTACION_FILE)

all_latexmk: $(DUMMY_TARGETS)
	$(LATEXMK_TOOL) -pdf -pdflatex="pdflatex -interactive=nonstopmode" -use-make $(TEX_FILE)
	makeglossaries $(ROOT_FILENAME)
	$(LATEXMK_TOOL) -pdf -pdflatex="pdflatex -interactive=nonstopmode" -use-make $(TEX_FILE)

pdf_dia_done: $(PDFS_FROM_DIA)
	echo "Generating pdfs from DIA: [$(PDFS_FROM_DIA)]..."
	touch $@

pdf_svg_done: $(PDFS_FROM_SVG)
	echo "Generating pdfs from SVG: [$(PDFS_FROM_SVG)]..."
	touch $@

pdf_eps_done: $(PDFS_FROM_EPS)
	echo "Generating pdfs from EPS: [$(PDFS_FROM_EPS)]..."
	touch $@

%.pdf: %.dia
	echo "Converting $^ to $@..."
	dia -e $@.eps $^
	$(EPSPDF_TOOL) $@.eps $@
	$(RM) $@.eps

%.pdf: %.svg
	echo "Converting $^ to $@..."
	inkscape $^ --export-pdf=$@ -D

%.pdf: %.eps
	echo "Converting $^ to $@..."
	$(EPSPDF_TOOL) $^ $@ 
#	-epstopdf -outfile=$@ $^ 

tar:
	tar czvf $(ROOT_FILENAME)-latex.tgz `find . -name Makefile -o -name README -o -name "*.txt" -o -name "*.ppt*" -o -name "*.c" -o -name "*.sty" -o -name "*.tex" -o -name "*.bib" -o -name "*.pdf" -o -name "*.png" -o -name "*.PNG" -o -name "*.jpg" -o -name "*.JPG" -o -name "*.dia" -o -name "*.eps" -o -name "*.EPS"` 
	zip $(ROOT_FILENAME)-latex.zip `find . -name Makefile -o -name README -o -name "*.txt" -o -name "*.ppt*" -o -name "*.c" -o -name "*.sty" -o -name "*.tex" -o -name "*.bib" -o -name "*.pdf" -o -name "*.png" -o -name "*.PNG" -o -name "*.jpg" -o -name "*.JPG" -o -name "*.dia" -o -name "*.eps" -o -name "*.EPS"` 

clean:
	$(RUBBER_TOOL) --clean -d $(TEX_ANTEPROYECTO_FILE)
	$(RUBBER_TOOL) --clean -d $(TEX_FILE)
	$(RUBBER_TOOL) --clean -d $(TEX_PRESENTACION_FILE)
#	$(RM) $(PDFS_FROM_DIA)
#	$(RM) $(PDFS_FROM_SVG)
	$(RM) $(DUMMY_TARGETS)


clean_latexmk:
	$(LATEXMK_TOOL) -C $(TEX_ANTEPROYECTO_FILE)
	$(LATEXMK_TOOL) -C $(TEX_FILE)
	$(LATEXMK_TOOL) -C $(TEX_PRESENTACION_FILE)
#	$(RM) $(PDFS_FROM_DIA)
#	$(RM) $(PDFS_FROM_SVG)
	-$(RM) $(ROOT_FILENAME).bbl
	-$(RM) $(ROOT_FILENAME).sbl
	-$(RM) $(ROOT_FILENAME).ist
	-$(RM) $(ROOT_FILENAME).acn
	-$(RM) $(ROOT_FILENAME).cod
	-$(RM) $(ROOT_FILENAME).alg
	-$(RM) $(ROOT_FILENAME).acr
	-$(RM) $(ROOT_FILENAME).sym
	-$(RM) $(ROOT_FILENAME).slg
	-$(RM) $(ROOT_ANTEPROYECTO_FILENAME).blg
	-$(RM) $(ROOT_ANTEPROYECTO_FILENAME).bbl
	-$(RM) $(ROOT_ANTEPROYECTO_FILENAME).out
	-$(RM) $(ROOT_ANTEPROYECTO_FILENAME).aux
	-$(RM) $(ROOT_ANTEPROYECTO_FILENAME).pdf
	-$(RM) $(ROOT_ANTEPROYECTO_FILENAME).log
	-$(RM) $(ROOT_ANTEPROYECTO_FILENAME).fdb_latexmk
	-$(RM) $(ROOT_PRESENTACION_FILENAME).bbl
	-$(RM) $(ROOT_PRESENTACION_FILENAME).sbl
	-$(RM) $(ROOT_PRESENTACION_FILENAME).ist
	-$(RM) $(ROOT_PRESENTACION_FILENAME).acn
	-$(RM) $(ROOT_PRESENTACION_FILENAME).cod
	-$(RM) $(ROOT_PRESENTACION_FILENAME).alg
	-$(RM) $(ROOT_PRESENTACION_FILENAME).acr
	-$(RM) $(ROOT_PRESENTACION_FILENAME).sym
	-$(RM) $(ROOT_PRESENTACION_FILENAME).slg
	$(RM) $(DUMMY_TARGETS)

.PHONY:	all pdf clean tar $(DUMMY_TARGETS)


