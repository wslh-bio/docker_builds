# base image
FROM ubuntu:bionic

# metadata
LABEL base.image="ubuntu:bionic"
LABEL version="2"
LABEL software="SeroBA"
LABEL software.version="1.0.2"
LABEL description="k-mer based Pipeline to identify the Serotype from Illumina NGS reads"
LABEL website="https://github.com/sanger-pathogens/seroba"
LABEL license="https://github.com/sanger-pathogens/seroba/blob/master/LICENSE"
LABEL maintainer="Abigail Shockey"
LABEL maintainer.email="abigail.shockey@slh.wisc.edu"

# Install ubuntu dependencies
RUN apt-get update && apt-get -y upgrade && apt-get -y install git \
  wget \
  unzip \
  zlib1g-dev \
  libbz2-dev \
  liblzma-dev \
  python3 \
  python3-pip \
  libpython3-dev \
  python3-setuptools \
  python-minimal && \
  bioperl=1.6.924-3 && \
  apt-get clean && apt-get autoclean && rm -rf /var/lib/apt/lists/*

# # Get the latest release from github and install dependencies
RUN wget https://github.com/sanger-pathogens/seroba/archive/v1.0.2.tar.gz && \
  tar -xvf v1.0.2.tar.gz && \
   cd seroba-1.0.2 && \
   pip3 install -U --force-reinstall pip && \
   pip3 install pillow && \
   pip3 install pysam==0.15.0 && \
   sed -i 's/KMC_VERSION=3.0.0/KMC_VERSION=3.1.1/g' /seroba-1.0.2/install_dependencies.sh && \
   sed -i 's/KMC3.linux.tar.gz/KMC3.1.1.linux.tar.gz/g' /seroba-1.0.2/install_dependencies.sh && \
  /seroba-1.0.2/install_dependencies.sh

# set path
ENV PATH="/seroba-1.0.2:/seroba-1.0.2/build:/seroba-1.0.2/build/MUMmer3.23:/seroba-1.0.2/build/bowtie2-2.3.1-legacy:/seroba-1.0.2/build/cdhit-4.6.8:${PATH}"\
    LC_ALL=C

RUN pip3 install -U --force-reinstall biopython==1.77

# install seroba and create database (/seroba-1.0.2/database/)
RUN cd /seroba-1.0.2 && \
  python3 setup.py install && \
  seroba createDBs database/ 71

RUN mkdir /data
WORKDIR /data
