FROM debian:jessie
MAINTAINER Johan von Forstner <johan.forstner@gmail.com>
ENV DEBIAN_FRONTEND noninteractive
COPY texlive.profile /

# install packages
RUN apt-get update \
  && apt-get install --no-install-recommends -y \
    wget perl fontconfig libwww-perl python-pygments unzip

# install texlive    
RUN wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz \
  && tar xzvf install-tl-unx.tar.gz \
  && ./install-tl-*/install-tl -profile texlive.profile \
  && rm -rf install-tl-*
  
RUN wget https://github.com/mozilla/Fira/archive/master.zip \
  && unzip master.zip \
  && sudo cp Fira-master/otf/* /usr/local/share/fonts/ \
  && rm master.zip \
  && rm -rf Fira-master
  
# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*