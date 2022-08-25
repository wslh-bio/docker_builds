FROM ubuntu:xenial

# Based on https://github.com/StaPH-B/docker-builds/blob/master/quast/5.0.2/Dockerfile
LABEL base.image="ubuntu:xenial"
LABEL dockerfile.version="1"
LABEL software="QUAST"
LABEL software.version="5.0.2"
LABEL description="Genome assembly evaluation tool"
LABEL website="https://github.com/ablab/quast"
LABEL license="https://github.com/ablab/quast/blob/master/LICENSE.txt"
LABEL maintainer="Abigail Shockey"
LABEL maintainer.email="abigail.shockey@slh.wisc.edu"

# Install dependencies 
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

# For singularity compatibility
ENV LC_ALL=C

# Install quast and make /data directory
RUN wget https://github.com/ablab/quast/releases/download/quast_5.0.2/quast-5.0.2.tar.gz && \
    tar -xzf quast-5.0.2.tar.gz && \
    rm -rf quast-5.0.2.tar.gz && \
    cd /quast-5.0.2 && \
    /quast-5.0.2/setup.py install && \
    mkdir /data

# Set working directory
WORKDIR /data
