FROM debian:stable-slim
MAINTAINER Johan von Forstner <johan.forstner@gmail.com>
ENV DEBIAN_FRONTEND noninteractive

# install packages
RUN mkdir -p /usr/share/man/man1 \
  && apt-get update \
  && apt-get install -y apt-utils libpaper1
  
RUN apt-get install -y \
    wget perl git fontconfig libwww-perl python3-pygments unzip locales ssh pdftk-java ghostscript make fonts-font-awesome texlive-full
    
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

RUN wget https://www.fontsquirrel.com/fonts/download/lato -O lato.zip \
  && unzip lato.zip -d /usr/share/fonts/truetype -x "*.txt" \
  && rm lato.zip

RUN wget https://www.fontsquirrel.com/fonts/download/raleway -O raleway.zip \
  && unzip raleway.zip -d /usr/share/fonts/truetype -x "*.txt" \
  && rm raleway.zip
  
RUN fc-cache
  
# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
