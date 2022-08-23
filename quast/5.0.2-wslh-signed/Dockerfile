FROM ubuntu:xenial

# For easy upgrade
ARG QUAST_VER=5.0.2

LABEL base.image="ubuntu:xenial"
LABEL dockerfile.version="1"
LABEL software="QUAST"
LABEL software.version="5.0.2"
LABEL description="Genome assembly evaluation tool"
LABEL website="https://github.com/ablab/quast"
LABEL license="https://github.com/ablab/quast/blob/master/LICENSE.txt"
LABEL maintainer="Abigail Shockey"
LABEL maintainer.email="abigail.shockey@slh.wisc.edu"

RUN apt-get update && apt-get install -y zlib1g-dev \
  pkg-config \
  libfreetype6-dev \
  libpng-dev \
  wget \
  g++ \
  make \
  perl \
  python \
  python-setuptools \
  python-matplotlib \
  python-simplejson \
  python-joblib \
  locales \
  python-pip && \
  locale-gen en_US.UTF-8 && \
  apt-get clean && \
  apt-get autoclean && \
  rm -rf /var/lib/apt/lists/*

# for singularity compatibility
ENV LC_ALL=C

# install quast and make /data directory
RUN wget https://github.com/ablab/quast/releases/download/quast_${QUAST_VER}/quast-${QUAST_VER}.tar.gz && \
    tar -xzf quast-${QUAST_VER}.tar.gz && \
    rm -rf quast-${QUAST_VER}.tar.gz && \
    cd /quast-${QUAST_VER} && \
    /quast-${QUAST_VER}/setup.py install && \
    mkdir /data

WORKDIR /data
