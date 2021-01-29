FROM kieluniphysik/texlive
MAINTAINER Johan von Forstner <johan.forstner@gmail.com>
ENV DEBIAN_FRONTEND noninteractive

ENV LANG C.UTF-8

# install packages
RUN apt-get update \
  && apt-get install --no-install-recommends -y \
    python3 python3-pip python3-dev python3-setuptools python3-wheel python3-virtualenv python3-venv build-essential zlib1g-dev libssl-dev nfs-common git cmake pkg-config ca-certificates lsb-release wget \
    libc6 libgcc1 libgl1 libglib-2.0-0 libice6 libsm6 libstdc++6 libx11-6 libxext6 libxrender1
    
# install pip packages
RUN python3 -m pip install --upgrade setuptools wheel pip \
  && pip3 install numpy>=1.16.5 scipy matplotlib pandas ipython requests python-dateutil uncertainties Pillow trackpy Sphinx numpydoc sphinx_rtd_theme pytest pytest-cov pytest-mpl lmfit \
  && pip3 install statsmodels
  
# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
