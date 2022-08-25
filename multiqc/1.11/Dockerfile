# base image
FROM ubuntu:bionic

# metadata
LABEL base.image="ubuntu:bionic"
LABEL version="1"
LABEL software="MultiQC"
LABEL software.version="1.11"
LABEL description="Aggregate bioinformatics results across many samples into a single report."
LABEL website="https://github.com/ewels/MultiQC"
LABEL license="https://github.com/ewels/MultiQC/blob/master/LICENSE"
LABEL maintainer="Abigail Shockey"
LABEL maintainer.email="abigail.shockey@slh.wisc.edu"

# install python (3.8) and other dependencies
# R necessary if user wants to run unifrac function in metaphlan

RUN apt-get update && apt-get install -y software-properties-common && \
  add-apt-repository ppa:deadsnakes/ppa && \
  apt-get update && apt-get install -y --no-install-recommends --no-install-suggests \
  gcc \
  wget \
  python3.7 \
  python3.7-dev \
  python3-distutils \
  python3-setuptools \
  python3-pip \
  unzip \
  git

RUN pip3 install Cython --force-reinstall && \
  pip3 install wheel --force-reinstall && \
  pip3 install numpy --force-reinstall && \
  pip3 install -U --force-reinstall pip

RUN wget https://github.com/ewels/MultiQC/archive/refs/tags/v1.11.tar.gz && \
  tar -xvf v1.11.tar.gz && \
  cd MultiQC-1.11 && \
  pip3 install .

ENV LC_ALL='C.UTF-8' LANG='C.UTF-8'

RUN mkdir /data
WORKDIR /data
