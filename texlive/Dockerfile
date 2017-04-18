FROM debian:jessie
MAINTAINER Johan von Forstner <johan.forstner@gmail.com>
ENV DEBIAN_FRONTEND noninteractive
COPY texlive.profile /
RUN apt-get update \
  && apt-get install --no-install-recommends -y \
    wget perl fontconfig libwww-perl python-pygments \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* \
  && wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz \
  && tar xzvf install-tl-unx.tar.gz \
  && ./install-tl-*/install-tl -profile texlive.profile \
  && rm -rf install-tl-*
  
# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*