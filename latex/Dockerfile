FROM debian:sid

# run with something like:
#     docker run -it --rm \
#           --net host \
#           -v $(pwd):/usr/src/latex \
#           --workdir="/usr/src/latex" \
#           fschl/latex pdflatex main.tex
# or any other latex command



LABEL maintainer "fschl.code@gmail.com"

RUN apt-get update && apt-get install -y \
    python-pygments \
    gnuplot \
    --no-install-recommends \
    && rm -rf /var/lib/apt/lists/*

#    texlive-common \
RUN apt-get update && apt-get install -y \
    texlive-base \
    texlive-bibtex-extra \
    texlive-extra-utils \
    texlive-font-utils \
    texlive-fonts-extra \
    texlive-generic-extra \
    texlive-generic-recommended \
    texlive-lang-english \
    texlive-lang-german \
    texlive-latex-base \
    texlive-latex-extra \
    texlive-latex-recommended \
    texlive-pictures \
    texlive-science \
    python-pygments \
    gnuplot \
    --no-install-recommends \
    && rm -rf /var/lib/apt/lists/*
