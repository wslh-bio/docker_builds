# base image
FROM ubuntu:bionic

# metadata
LABEL base.image="ubuntu:bionic"
LABEL version="1"
LABEL software="pandas"
LABEL software.version="1.3.2"
LABEL description=""
LABEL website=""
LABEL license=""
LABEL maintainer="Abigail Shockey"
LABEL maintainer.email="abigail.shockey@slh.wisc.edu"

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
  libxml2-dev \
  libxslt1-dev \
  zlib1g-dev \
  g++

RUN python3.7 -m pip install cython
RUN python3.7 -m pip install wheel
RUN python3.7 -m pip install numpy  
RUN python3.7 -m pip install pandas==1.3.2

ENV LC_ALL=C
