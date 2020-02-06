FROM debian:unstable-slim
MAINTAINER Johan von Forstner <johan.forstner@gmail.com>
ENV DEBIAN_FRONTEND noninteractive

ENV LANG C.UTF-8

ENV HUGO_VERSION 0.64.0
ENV HUGO_DOWNLOAD_URL https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_Linux-64bit.tar.gz

# install packages
RUN apt-get update \
  && apt-get install --no-install-recommends -y \
    wget git make ssh python3 python3-pip ca-certificates rsync ruby-full zlib1g-dev
RUN gem install html-proofer --no-document

# install hugo
RUN wget $HUGO_DOWNLOAD_URL && \
    tar -xzf hugo_extended_${HUGO_VERSION}_Linux-64bit.tar.gz && \
    mv hugo /usr/bin/hugo && \
    rm hugo_extended_${HUGO_VERSION}_Linux-64bit.tar.gz LICENSE README.md
    
# install pip packages
RUN pip3 install --upgrade setuptools \
  && pip3 install academic
  
# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
