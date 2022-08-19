#Download base image ubuntu 22.04
FROM ubuntu:22.04 As builder

# Disable prompts on Ubuntu
ARG DEBIAN_FRONTEND=noninteractive

COPY docker/*sources.list.ex /etc/apt/sources.list
RUN apt-get update && \
    apt-get -y -q install cmake g++-11 \
    git curl wget autoconf ninja-build cmake-curses-gui \
    clang-14 clangd-14 clang-format-14 clang-tidy-14 \
    flex bison \
    gosu sudo \
    binutils-dev libunwind-dev libfmt-dev && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /workspace

COPY docker/entrypoint.sh /workspace/entrypoint.sh
RUN chmod +x /workspace/entrypoint.sh

CMD ["bash"]
ENTRYPOINT ["/workspace/entrypoint.sh"]

#docker build -t duckdb_dev -f docker/Dockerfile .
