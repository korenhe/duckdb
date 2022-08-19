#Download base image ubuntu 22.04
FROM ubuntu:22.04 As builder

# Disable prompts on Ubuntu
ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get -y -q install cmake g++-11 \
    git curl wget autoconf ninja-build cmake-curses-gui \
    flex bison \
    gosu sudo \
    binutils-dev libunwind-dev libfmt-dev && \
    rm -rf /var/lib/apt/lists/*

VOLUME ["/duckdb-src"]
WORKDIR /duckdb-src

RUN mkdir /workspace
COPY docker/entrypoint.sh /workspace/entrypoint.sh
RUN chmod +x /workspace/entrypoint.sh

ENTRYPOINT ["/workspace/entrypoint.sh"]
