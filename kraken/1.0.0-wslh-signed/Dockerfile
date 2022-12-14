# base image
FROM ubuntu:xenial

# metadata
LABEL base.image="ubuntu:xenial"
LABEL container.version="1"
LABEL software="Kraken"
LABEL software.version="1.0"
LABEL description="Taxonomic sequence classifier"
LABEL website="https://github.com/DerrickWood/kraken"
LABEL license="https://github.com/DerrickWood/kraken/blob/master/LICENSE"
LABEL maintainer="Kelsey Florek(signed)"
LABEL maintainer.email="kelsey.florek@slh.wisc.edu"

# install dependencies
RUN apt-get update && apt-get -y install \
  wget \
  zlib1g-dev \
  make \
  g++ \
  cpanminus \
  rsync

# DL Jellyfish, unpack, and install
RUN wget https://github.com/gmarcais/Jellyfish/releases/download/v1.1.12/jellyfish-1.1.12.tar.gz && \
  tar -zxf jellyfish-1.1.12.tar.gz && rm -rf jellyfish-1.1.12.tar.gz

RUN cd jellyfish-1.1.12 && ./configure --prefix=/opt/ && make -j 4 && make install

# DL Kraken v1.0, unpack, and install
RUN wget https://github.com/DerrickWood/kraken/archive/v1.0.tar.gz && \
  tar -xzf v1.0.tar.gz && \
  rm -rf v1.0.tar.gz && \
  cd kraken-1.0 && \
  mkdir /opt/kraken && \
  ./install_kraken.sh /opt/kraken/ && \
  mkdir /data

ENV PATH="$PATH:/opt/kraken:/opt/bin" \
    LC_ALL=C

WORKDIR /data

# this perl module and rsync required for kraken-build
RUN cpanm Getopt::Std

# DL MiniKraken database
RUN mkdir /kraken-database && \
  cd /kraken-database && \
  wget https://ccb.jhu.edu/software/kraken/dl/minikraken_20171019_4GB.tgz && \
  tar -zxf minikraken_20171019_4GB.tgz && \
  rm -rf minikraken_20171019_4GB.tgz
