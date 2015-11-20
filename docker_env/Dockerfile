FROM ubuntu:14.04
MAINTAINER felipevolpone@gmail.com
ENV LC_ALL en_US.UTF-8
ENV DEBIAN_FRONTEND noninteractive

RUN mkdir -p /home/pyston
RUN mkdir -p /home/pyston/pyston_deps

RUN apt-get update -y

WORKDIR /home/pyston

RUN apt-get install -y git cmake ninja-build ccache libncurses5-dev liblzma-dev libreadline-dev libgmp3-dev autoconf libtool python-dev texlive-extra-utils clang libssl-dev libsqlite3-dev pkg-config libbz2-dev

RUN git clone https://github.com/dropbox/pyston.git 

RUN git clone https://github.com/llvm-mirror/llvm.git ~/pyston_deps/llvm-trunk
RUN git clone https://github.com/llvm-mirror/clang.git ~/pyston_deps/llvm-trunk/tools/clang

WORKDIR /home/pyston/pyston
RUN git config --global user.email "pyston@email.any"
RUN git config --global user.name "Pyston Project"
RUN git submodule update --init --recursive build_deps
RUN make llvm_up
RUN make
RUn make check