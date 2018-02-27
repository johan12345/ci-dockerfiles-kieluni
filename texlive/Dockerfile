FROM debian:jessie
MAINTAINER Johan von Forstner <johan.forstner@gmail.com>
ENV DEBIAN_FRONTEND noninteractive
COPY texlive.profile /

# install packages
RUN apt-get update \
  && apt-get install --no-install-recommends -y \
    wget perl fontconfig libwww-perl python-pygments unzip locales ssh pdftk
    
# utf-8
RUN locale-gen C.UTF-8 && \
    /usr/sbin/update-locale LANG=C.UTF-8 && \
    apt-get remove -y locales
ENV LANG C.UTF-8

# install texlive    
RUN wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz \
  && tar xzvf install-tl-unx.tar.gz \
  && ./install-tl-*/install-tl -profile texlive.profile \
  && rm -rf install-tl-*
  
RUN wget https://github.com/mozilla/Fira/archive/master.zip \
  && unzip master.zip \
  && cp Fira-master/otf/* /usr/share/fonts/truetype \
  && rm -r Fira-master \
  && rm master.zip
  
RUN wget https://fontawesome.com/v4.7.0/assets/font-awesome-4.7.0.zip \
  && unzip font-awesome-4.7.0.zip \
  && cp font-awesome-4.7.0/fonts/FontAwesome.otf /usr/share/fonts/truetype \
  && rm -r font-awesome-4.7.0 \
  && rm font-awesome-4.7.0.zip
  
RUN fc-cache
  
# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
