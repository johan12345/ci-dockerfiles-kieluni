FROM kieluniphysik/texlive
MAINTAINER Johan von Forstner <johan.forstner@gmail.com>
ENV DEBIAN_FRONTEND noninteractive

# install packages
RUN apt-get update \
  && apt-get install --no-install-recommends -y \
    python python-dev build-essential

RUN apt-get build-dep python3

# Get Python 3
RUN wget https://www.python.org/ftp/python/3.6.1/Python-3.6.1.tgz && \
	tar xvf Python-3.6.1.tgz && \
	cd Python-3.6.1 && \
	./configure --enable-optimizations && \
	make -j4 && \
	make altinstall
    
# We want a current pip
ADD get-pip.py /tmp/get-pip.py
RUN python /tmp/get-pip.py
    
# install pip packages
RUN pip install --upgrade setuptools pip
RUN pip install numpy scipy matplotlib pandas ipython requests python-dateutil uncertainties Sphinx numpydoc sphinx_rtd_theme pytest pytest-cov Pygments
  
# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*