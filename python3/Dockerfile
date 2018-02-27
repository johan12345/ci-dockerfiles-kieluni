FROM kieluniphysik/texlive
MAINTAINER Johan von Forstner <johan.forstner@gmail.com>
ENV DEBIAN_FRONTEND noninteractive

ENV LANG C.UTF-8

# install packages
RUN apt-get update \
  && apt-get install --no-install-recommends -y \
    python python-dev build-essential zlib1g-dev libssl-dev nfs-common git

# Get Python 3
RUN wget https://www.python.org/ftp/python/3.6.4/Python-3.6.4.tgz && \
	tar xvf Python-3.6.4.tgz && \
	cd Python-3.6.4 && \
	./configure --enable-optimizations && \
	make -j4 && \
	make altinstall
    
# install pip packages
RUN pip3.6 install --upgrade setuptools pip
RUN pip3.6 install numpy scipy matplotlib pandas ipython requests python-dateutil uncertainties Pillow trackpy statsmodels Sphinx numpydoc sphinx_rtd_theme pytest pytest-cov Pygments
  
# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
