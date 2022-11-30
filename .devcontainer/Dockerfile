FROM mcr.microsoft.com/devcontainers/base:ubuntu


RUN apt update 
RUN apt install -y git make automake curl bison flex libgmp-dev clang clang-14 build-essential

RUN mkdir work 
WORKDIR /work
RUN git clone https://github.com/waywardgeek/datadraw.git \
    && cd datadraw \
    && ./autogen.sh \
    && ./configure \
    && make \
    && sudo make install

RUN git clone https://github.com/google/rune.git \
    && git clone https://github.com/pornin/CTTK.git \
    && cp CTTK/inc/cttk.h CTTK \
    && cd rune \
    && make \
    && ./runtests.sh \
    && sudo make install
