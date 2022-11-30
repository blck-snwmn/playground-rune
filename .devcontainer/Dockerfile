FROM mcr.microsoft.com/devcontainers/base:ubuntu


RUN apt update 
RUN apt install -y git make automake curl bison flex libgmp-dev clang-14 build-essential

RUN mkdir work 
WORKDIR /work
RUN git clone https://github.com/waywardgeek/datadraw.git
WORKDIR /work/datadraw
RUN ./autogen.sh
RUN ./configure
RUN make
RUN sudo make install

WORKDIR /work

RUN apt install -y clang 
RUN git clone https://github.com/google/rune.git
RUN git clone https://github.com/pornin/CTTK.git
RUN cp CTTK/inc/cttk.h CTTK
WORKDIR /work/rune
RUN make
RUN ./runtests.sh
RUN sudo make install
