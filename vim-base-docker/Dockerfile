FROM ubuntu

MAINTAINER holo3344 holo3344@163.com

WORKDIR /root

COPY Dockerfile ./

ENV DEBIAN_FRONTEND=noninteractive
ENV TZ=Asia/Chendu

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y tzdata && \
    apt-get install -y net-tools rsync inetutils-ping git curl wget unzip && \
    apt-get install -y build-essential cmake vim-nox python3-dev && \
    apt-get install -y pkg-config autoconf automake

COPY ./package ./
RUN cd ctags && \
    ./autogen.sh && \
    ./configure && \
    make -j4&& \
    make install && \
    cd .. && \
    rm -rf ctags
