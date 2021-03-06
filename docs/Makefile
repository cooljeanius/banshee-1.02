# Copyright (c) 2000-2004
#      The Regents of the University of California.  All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met:
# 1. Redistributions of source code must retain the above copyright
#    notice, this list of conditions and the following disclaimer.
# 2. Redistributions in binary form must reproduce the above copyright
#    notice, this list of conditions and the following disclaimer in the
#    documentation and/or other materials provided with the distribution.
# 3. Neither the name of the University nor the names of its contributors
#    may be used to endorse or promote products derived from this software
#    without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE REGENTS AND CONTRIBUTORS ``AS IS'' AND
# ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
# IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
# ARE DISCLAIMED.  IN NO EVENT SHALL THE REGENTS OR CONTRIBUTORS BE LIABLE
# FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
# DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS
# OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION)
# HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
# LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY
# OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF
# SUCH DAMAGE.

banshee_bindir = ../bin

ALL = banshee.ps banshee-manual.pdf
PAPERTYPE = letter
SOURCES = banshee.tex banshee-manual.tex

all: $(ALL)

banshee-manual.pdf: banshee-manual.tex banshee-manual.bib
	pdflatex $(@:.pdf=.tex)
	bibtex banshee-manual
	pdflatex $(@:.pdf=.tex)
	pdflatex $(@:.pdf=.tex)

%.ps: %.dvi
	dvips -P cmz -t $(PAPERTYPE) $< -o $@

%.dvi: $(SOURCES)
	$(banshee_bindir)/slatex $(@:.dvi=.tex)

clean:
	-rm -f *.aux *.dvi *.log *.bbl *.blg *.ps *.toc *.lof *.lot *.xyc .cache* .cache.new *~ *.idx

distclean: clean
maintainer-clean: distclean
	-rm -f banshee-manual.pdf
