# base image
FROM ubuntu:focal

# metadata
LABEL base.image="ubuntu:focal"
LABEL version="1"
LABEL software="pandas"
LABEL software.version="1.5.0"
LABEL description=""
LABEL website=""
LABEL license=""
LABEL maintainer="Kelsey Florek"
LABEL maintainer.email="kelsey.florek@slh.wisc.edu"

RUN apt-get update && apt-get install -y software-properties-common && \
	apt install -y python3.8 python3-pip

RUN pip install 'pandas==1.5.0'

ENV LC_ALL=C
