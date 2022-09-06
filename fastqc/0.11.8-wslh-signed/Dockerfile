# base image
FROM ubuntu:xenial

# based on https://github.com/StaPH-B/docker-builds/blob/master/fastqc/0.11.8/Dockerfile
# metadata
LABEL base.image="ubuntu:xenial"
LABEL version="1"
LABEL software="FASTQC"
LABEL software.version="0.11.8"
LABEL description="A quality control analysis tool for high throughput sequencing data"
LABEL website="https://www.bioinformatics.babraham.ac.uk/projects/fastqc/"
LABEL license="https://github.com/s-andrews/FastQC/blob/master/LICENSE.txt"
LABEL maintainer="Abigail Shockey"
LABEL maintainer.email="abigail.shockey@slh.wisc.edu"

RUN apt-get update && apt-get install -y \
  unzip \
  wget \
  perl \
  default-jre \
  && apt-get clean && apt-get autoclean && rm -rf /var/lib/apt/lists/*

RUN wget https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.11.8.zip && \
    unzip fastqc_v0.11.8.zip && \
    rm fastqc_v0.11.8.zip && \
    chmod +x FastQC/fastqc


ENV PATH="${PATH}:/FastQC/"\
 LC_ALL=C

RUN mkdir /data
WORKDIR /data
