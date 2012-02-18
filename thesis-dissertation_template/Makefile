# ****** ****** ****** ****** ****** ****** ****** ****** ******
# ... GNU Make for Bourne Shell ...

# $Id: Makefile,v 1.6 2011/10/26 16:14:06 khoman Exp $

# ****** ****** ****** ****** ****** ****** ****** ****** ******

SHELL = /bin/sh

# ... variable definitions ...

foo = ths
ptotmp = ptoths
rpctmp = rpcths
ptotex = ptotemplate.tex
rpctex = rpctemplate.tex

# ... rules ...

.PHONY : help clean

ins : $(foo).dtx $(foo).ins

	latex $(foo).ins

# ... clean up extracted templates ...
	mv $(ptotex) junk.tex
	csplit -f junka junk.tex "/\documentclass/" "/\endinput/"
	csplit -f junkb junka00  "/mode/" 
	cat junkb01 ../rcshead.tex junka01 ../rcstail.tex > junk.00
	sed 's/<ps>/%/g' junk.00 > junk.01
	sed 's/rcsId/Id/' junk.01 > $(ptotex)
	rm -f junk.tex junk0? junka0? junkb0? junk.0?

	mv $(rpctex) junk.tex
	csplit -f junka junk.tex "/\documentclass/" "/\endinput/"
	csplit -f junkb junka00  "/mode/" 
	cat junkb01 ../rcshead.tex junka01 ../rcstail.tex > junk.00
	sed 's/<ps>/%/g' junk.00 > junk.01
	sed 's/rcsId/Id/' junk.01 > $(rpctex)
	rm -f junk.tex junk0? junka0? junkb0? junk.0?

	touch ins

exec : ins $(foo).dtx $(foo).ins Makefile.template
#	rm -f ins
#	make ins

# ... cp template to subdirectory ...
	-mkdir $(ptotmp)
	cp $(ptotex) $(ptotmp)/template.tex
	cp ptointro.tex $(ptotmp)/intro.tex
	cp Makefile.template $(ptotmp)/Makefile
	chmod ug+w $(ptotmp)/Makefile

	-mkdir $(rpctmp)
	cp $(rpctex) $(rpctmp)/template.tex
	cp Makefile.template $(rpctmp)/Makefile
	cp rpcintro.tex $(rpctmp)/intro.tex
	cp rpcchap.tex $(rpctmp)/chapter.tex
	cp rpcappx.tex $(rpctmp)/appendix.tex
	chmod ug+w $(rpctmp)/Makefile

# ... generate ps/pdf of ptotemplate ...
	make -C $(ptotmp)/ min 
	cp $(ptotmp)/template.ps ptotemplate.base.ps
	sed 's/Page}{ms}/Page}{phd}/g' $(ptotex) > $(ptotmp)/template.tex
	make -C $(ptotmp)/ min
	cp $(ptotmp)/template.ps ptotemplate.phd.ps
	sed 's/age{true}/age{false}/g' $(ptotex) > $(ptotmp)/template.tex
	make -C $(ptotmp)/ min
	cp $(ptotmp)/template.ps ptotemplate.false.ps
	sed 's/dix}{one}/dix}{two}/g'  $(ptotex) > $(ptotmp)/template.tex 
	make -C $(ptotmp)/ min
	cp $(ptotmp)/template.ps ptotemplate.two.ps
	sed 's/times,12pt/12pt/g' $(ptotex) > $(ptotmp)/template.tex
	make -C $(ptotmp)/ min
	cp $(ptotmp)/template.ps ptotemplate.cmfont.ps
	sed 's/times,12pt/timesmtp,12pt/g' $(ptotex) > $(ptotmp)/template.tex
	make -C $(ptotmp)/ min
	cp $(ptotmp)/template.ps ptotemplate.mtprofont.ps
	cp $(ptotex) $(ptotmp)/template.tex
	make -C $(ptotmp)/ min
# ... generate ps/pdf of rpctemplate ...
	make -C $(rpctmp)/
	cp $(rpctmp)/template.ps rpctemplate.base.ps
	sed 's/Page}{ms}/Page}{phd}/g' $(rpctex) > $(rpctmp)/template.tex
	make -C $(rpctmp)/ min
	cp $(rpctmp)/template.ps rpctemplate.phd.ps
	sed 's/age{true}/age{false}/g' $(rpctex) > $(rpctmp)/template.tex
	make -C $(rpctmp)/ min
	cp $(rpctmp)/template.ps rpctemplate.false.ps
	sed 's/dix}{one}/dix}{two}/g'  $(rpctex) > $(rpctmp)/template.tex 
	make -C $(rpctmp)/ 
	cp $(rpctmp)/template.ps rpctemplate.two.ps
	sed 's/times,12pt/12pt/g' $(rpctex) > $(rpctmp)/template.tex
	make -C $(rpctmp)/ min
	cp $(rpctmp)/template.ps rpctemplate.cmfont.ps
	sed 's/times,12pt/timesmtp,12pt/g' $(rpctex) > $(rpctmp)/template.tex
	make -C $(rpctmp)/ min
	cp $(rpctmp)/template.ps rpctemplate.mtprofont.ps
	cp $(rpctex) $(rpctmp)/template.tex
	make -C $(rpctmp)/

	touch exec

dtx : $(foo).dtx
	latex $(foo).dtx
	latex $(foo).dtx
	dvips $(foo).dvi
	ps2pdf $(foo).ps
	touch dtx

all : $(foo).dtx $(foo).ins Makefile.template
	make exec
	make dtx

clean:
	-rm -f dtx ins exec
	-rm -f $(foo).{aux,dvi,log,pdf,ps,toc}
	-rm -f ptotemplate.tex ptointro.tex
	-rm -f ptotemplate.*.ps
	-rm -f rpctemplate.tex rpcintro.tex rpcchap.tex rpcappx.tex
	-rm -f rpctemplate.*.ps

help : 
	@echo "make ins -> generate template.tex and ps file"
	@echo "make dtx -> generate ps version of dtx file"
	@echo "make all -> execute make ins and make dtx"
	@echo "make clean -> remove all generated files"

# ... version control info ...

# $Id: Makefile,v 1.6 2011/10/26 16:14:06 khoman Exp $

# $Log: Makefile,v $
# Revision 1.6  2011/10/26 16:14:06  khoman
# Now generates baseline versions with the free times roman fonts.
# Versions with computer modern and MathTime Pro are also generated.
#
# Revision 1.5  2011/10/25 19:10:52  khoman
# Added Makefile.template as dependency to the exec and ins targets.
# Also added commands to the clean target to remove the empty target files.
#
# Revision 1.4  2011/10/11 14:35:48  khoman
# Edited the all target by deleted the make ins command as it is
# executed as part of the make exec target.
#
# Revision 1.3  2011/10/10 21:39:24  khoman
# Added rm -f of the ins touch file so that the ptotemplate.tex file and
# the rpctemplate.tex files are forced to be regenerated.
#
# Revision 1.2  2011/07/25 21:43:11  khoman
# Final changes in preparation of template for James Tinsley's MS thesis.
#
# Revision 1.1  2004/03/18 18:02:45  khoman
# Initial revision
#
# Revision 1.1  2001/01/11 14:42:17  khoman
# Initial revision
#

# ****** ****** ****** ****** ****** ****** ****** ****** ******

