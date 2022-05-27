FROM jupyter_base_notebook:latest
RUN pip install plotly \
  && jupyter labextension install \
    @jupyter-widgets/jupyterlab-manager \
    plotlywidget \
    jupyterlab-plotly