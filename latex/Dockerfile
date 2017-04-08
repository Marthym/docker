FROM debian:jessie
MAINTAINER marthym@github.com

# Update dependency
RUN export DEBIAN_FRONTEND=noninteractive && \
	apt-get -y update && \ 
	apt-get -y install \ 
		texlive-base \ 
		texlive-xetex \ 
		texlive-latex-recommended \ 
		texlive-latex-extra \ 
		texlive-extra-utils \ 
		texlive-fonts-recommended \ 
		texlive-font-utils \ 
		texlive-lang-french \ 
		texlive-math-extra \ 
		texlive-pictures \ 
		latex-xcolor \ 
		texlive-bibtex-extra \ 
		pgf lmodern biber latexmk ghostscript && \
	apt-get clean && \
	apt-get autoclean && \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
