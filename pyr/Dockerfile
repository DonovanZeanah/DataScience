FROM jupyter_base_notebook:latest

RUN sed -i '/cloud.r-project.org/d' /etc/apt/sources.list \
  && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 'FCAE2A0E115C3D8A' \
  && add-apt-repository 'deb https://cloud.r-project.org/bin/linux/debian buster-cran40/' \
  && apt update -y -qq && apt upgrade -y -qq

ENV R_BASE_VERSION 4.1.0

RUN apt install -y --no-install-recommends --fix-broken \ 
  libjpeg62-turbo-dev \
  libc6-dev \
  libssl-dev \
  make \
  build-essential \
  r-base=${R_BASE_VERSION}-* \
  r-base-core=${R_BASE_VERSION}-* \
  r-recommended=${R_BASE_VERSION}-*

RUN R -e "install.packages(c('repr', 'IRdisplay', 'pbdZMQ','IRkernel','languageserver'));IRkernel::installspec()"

