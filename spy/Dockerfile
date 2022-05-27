FROM jupyter_base_notebook:latest
ENV JAVA_HOME /root/.cache/coursier/jvm/adopt@1.11.0-11
ENV PATH ${JAVA_HOME}/bin/:/root/.local/share/coursier/bin:$PATH
RUN curl -fLo cs https://git.io/coursier-cli-linux \
  && chmod +x ./cs && ./cs install cs && rm ./cs \
  && cs java --jvm adopt:11 --setup \
  && cs launch almond:0.11.0 --scala 2.13.4 -- --install --id scala213 --display-name "Scala (2.13)" \
  && cs launch almond:0.11.0 --scala 2.12.12 -- --install --id scala212 --display-name "Scala (2.12)" \
  && cs install metals

ADD ./config/metals-ls.json /usr/local/etc/jupyter/jupyter_server_config.d/metals-ls.json