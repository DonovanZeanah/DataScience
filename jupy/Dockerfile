FROM jupyter_base_notebook:latest

ENV JULIA_VERSION 1.6.2
ENV PATH  /root/jl/julia-${JULIA_VERSION}/bin:$PATH
RUN  mkdir /root/jl \
  && curl -L https://julialang-s3.julialang.org/bin/linux/x64/1.6/julia-${JULIA_VERSION}-linux-x86_64.tar.gz > /tmp/julia-linux-x86_64.tar.gz \
  && tar zxvf /tmp/julia-linux-x86_64.tar.gz -C /root/jl \
  && rm /tmp/julia-linux-x86_64.tar.gz && julia -e 'using Pkg;pkg"add IJulia LanguageServer;build IJulia"'