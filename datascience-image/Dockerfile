FROM jupyter/datascience-notebook:846f4cd31970

RUN pip install \
    jupyter-server-proxy mesa
    
RUN conda install -c conda-forge \
    'jupyterlab>=3.0.0,<4.0.0a0' \
    jupyterlab-lsp \
    python-lsp-server r-languageserver

USER root

# Java Installation
RUN apt-get update --yes && \
    apt-get install --yes --no-install-recommends \
    default-jdk && \
    apt-get clean && rm -rf /var/lib/apt/lists/*
    
USER ${NB_UID}
