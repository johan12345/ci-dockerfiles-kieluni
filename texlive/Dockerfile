FROM debian:unstable-slim
MAINTAINER Johan von Forstner <johan.forstner@gmail.com>
ENV DEBIAN_FRONTEND noninteractive

# install packages
RUN mkdir -p /usr/share/man/man1 \
  && apt-get update \
  && apt-get install --no-install-recommends -y \
    wget perl fontconfig libwww-perl python-pygments unzip locales ssh pdftk-java ghostscript make fonts-font-awesome texlive-full
    
# utf-8
RUN locale-gen C.UTF-8 && \
    /usr/sbin/update-locale LANG=C.UTF-8 && \
    apt-get remove -y locales
ENV LANG C.UTF-8

RUN wget https://github.com/mozilla/Fira/archive/master.zip \
  && unzip master.zip \
  && cp Fira-master/otf/* /usr/share/fonts/truetype \
  && rm -r Fira-master \
  && rm master.zip
  
RUN fc-cache
  
# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
