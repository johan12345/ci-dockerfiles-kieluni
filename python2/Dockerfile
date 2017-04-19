FROM kieluniphysik/texlive
MAINTAINER Johan von Forstner <johan.forstner@gmail.com>
ENV DEBIAN_FRONTEND noninteractive

# install packages
RUN apt-get update \
  && apt-get install --no-install-recommends -y \
    python python-pip python-dev
    
# install pip packages
RUN pip install --upgrade setuptools pip
RUN pip install numpy scipy matplotlib pandas ipython requests python-dateutil uncertainties
  
# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*