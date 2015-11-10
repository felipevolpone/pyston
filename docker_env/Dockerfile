FROM ubuntu:14.04
MAINTAINER felipevolpone@gmail.chmod
ENV LC_ALL en_US.UTF-8
ENV DEBIAN_FRONTEND noninteractive

RUN mkdir -p /home/pyston

RUN apt-get update

WORKDIR /home/pyston

RUN apt-get install -yq git cmake ninja-build ccache libncurses5-dev liblzma-dev libreadline-dev libgmp3-dev autoconf libtool python-dev texlive-extra-utils clang libssl-dev libsqlite3-dev pkg-config libbz2-dev

RUN git clone https://github.com/dropbox/pyston.git ~/pyston

RUN git clone git://github.com/llvm-mirror/llvm.git ~/pyston_deps/llvm-trunk
RUN git clone git://github.com/llvm-mirror/clang.git ~/pyston_deps/llvm-trunk/tools/clang

git submodule update --init --recursive build_deps
make llvm_up
make
make check