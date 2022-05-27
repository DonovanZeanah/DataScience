FROM python:3.9.6-slim-buster
ENV NODE_OPTIONS --max-old-space-size=4096

# start up
RUN apt update -y \ 
  && apt upgrade -y \
  && ln -s /usr/bin/pip3 /usr/bin/pip

RUN apt install -y --no-install-recommends --fix-broken \
  software-properties-common \
  curl \
  vim \
  texlive-lang-japanese \
  texlive-xetex \
  pandoc \
  pandoc-citeproc \
  texlive-generic-extra \
  texlive-fonts-recommended \
  fontconfig
  RUN curl -fsSL https://deb.nodesource.com/setup_current.x | bash - \
  && apt install -y nodejs \
  && apt autoremove -y \
  && apt clean

# setup project
WORKDIR /app
# setup python dependencies
ADD ./requirements.txt /app/requirements.txt
RUN  pip install --upgrade pip --no-cache-dir  &&  pip install -r requirements.txt --no-cache-dir  \
  && jupyter labextension install \
    @krassowski/jupyterlab-lsp \
    @jupyterlab/toc \
    @ryantam626/jupyterlab_code_formatter \
  && jupyter serverextension enable --py jupyterlab_code_formatter \
  && rm ~/.jupyter/jupyter_notebook_config.json

# Japanese PDF export compat
ADD ./resources/index_ja.tex.j2 /usr/local/share/jupyter/nbconvert/templates/latex/index.tex.j2
# Configuration
COPY ./config/jupyter_server_config.json ~/.jupyter/jupyter_server_config.json
COPY ./config/jupyter_lab_config.py  ~/.jupyter/jupyter_lab_config.py 