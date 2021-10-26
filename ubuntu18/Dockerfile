FROM ubuntu:18.04 as base

RUN \
    apt-get update -y && \
    apt-get install -y \
    wget \
    git \
    tmux \
    vim \
    zsh \
    gcc g++ gdb


WORKDIR /root
CMD ["bash"]
