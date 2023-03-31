FROM jupyter/datascience-notebook:f16d1e3a935a

RUN pip install \
    jupyter-server-proxy mesa

USER root

# Java Installation
RUN apt-get update --yes && \
    apt-get install --yes --no-install-recommends \
    default-jdk && \
    apt-get clean && rm -rf /var/lib/apt/lists/*
    
USER ${NB_UID}
