# base image
FROM ubuntu:bionic

# metadata
LABEL base.image="ubuntu:bionic"
LABEL version="1"
LABEL software="bioawk"
LABEL software.version="1.0"
LABEL description="BWK awk modified for biological data "
LABEL website="https://github.com/lh3/bioawk"
LABEL maintainer="Abigail Shockey"
LABEL maintainer.email="Abigail.Shockey@slh.wisc.edu"

RUN apt-get update && apt-get -y upgrade && apt-get -y install build-essential \
  make \
  bison \
  byacc \
  zlib1g-dev \
  libz-dev \
  gawk \
  git && \
  apt-get clean && \
  apt-get autoclean && \
  rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/lh3/bioawk.git && \
  cd bioawk && \
  make

ENV PATH="/bioawk:${PATH}" \
  LC_ALL=C

RUN mkdir data
WORKDIR /data
