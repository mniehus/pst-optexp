### Makefile ---  

## Author: cbersch@ioip0136
## Version: $Id: Makefile,v 0.0 2008/09/12 10:20:31 cbersch Exp $
## Keywords: 
## X-URL: 
#
# This Makefile compiles TeX files containing
# TeXtoEPS environments to eps with automatically adjusted
# bounding box and then to pdf
# 
# When using target 'all', all .tex files in the directory are
# compiled
#
LATEX = latex -interaction=nonstopmode
OBJECTS=$(shell ls *.tex)
FILELIST=$(basename $(OBJECTS))
POE=$(shell kpsewhich pst-optexp.tex pst-optexp.pro)

export TEXINPUTS := ..:
export DVIPSHEADERS := ..:

.PHONY: all clean veryclean

.SECONDARY: $(addsuffix .ps, $(FILELIST))

all: $(addsuffix .pdf, $(FILELIST))

%.pdf: %.ps
	ps2pdf $<

%.ps: %.dvi
	dvips $< # 2>&1 >/dev/null

%.dvi: %.tex $(POE)
	$(LATEX) $< #2>&1 >/dev/null 
	rm -f $*.aux $*.log

clean: 
	$(RM) $(addsuffix .aux, $(FILELIST)) \
	      $(addsuffix .log, $(FILELIST)) \
	      $(addsuffix .dvi, $(FILELIST)) \
	      $(addsuffix .out, $(FILELIST))

veryclean: clean
	$(RM) $(addsuffix .ps, $(FILELIST)) \
	      $(addsuffix .pdf, $(FILELIST))

### Makefile ends here
