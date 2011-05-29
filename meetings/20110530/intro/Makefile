-include prefs.mk

MARKDOWN?=pandoc

FILENAME?=presentation

txtFiles=$(FILENAME).mdown

all: clean nuke tex pdf

tex:
	$(MARKDOWN) --template beamer.template -i $(txtFiles) -o $(FILENAME).tex
	perl -pe 's/\\section/\\end{frame}\n\\begin{frame}[fragile]/' -i $(FILENAME).tex
	perl -pe 's/\\end{document}/\\end{frame}\n\\end{document}/' -i $(FILENAME).tex

pdf:
	pdflatex $(FILENAME).tex < /dev/null

clean:
	rm -f $(FILENAME).{tex,aux,bbl,blg,log,nav,snm,toc,out,vrb}
	
nuke: clean
	rm -f $(FILENAME).pdf
