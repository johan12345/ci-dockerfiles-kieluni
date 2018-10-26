FROM kieluniphysik/texlive
MAINTAINER Johan von Forstner <johan.forstner@gmail.com>
ENV DEBIAN_FRONTEND noninteractive

ENV LANG C.UTF-8

# install packages
RUN apt-get update \
  && apt-get install --no-install-recommends -y \
    python3 python3-pip python3-dev build-essential zlib1g-dev libssl-dev nfs-common git
    
# install pip packages
RUN pip3 install --upgrade setuptools \
  && pip3 install numpy scipy matplotlib pandas ipython requests python-dateutil uncertainties Pillow trackpy Sphinx numpydoc sphinx_rtd_theme pytest pytest-cov \
  && pip3 install statsmodels
  
# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
