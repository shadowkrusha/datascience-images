FROM jupyter/scipy-notebook:846f4cd31970

RUN pip install \
    jupyter-server-proxy mesa

RUN conda install -c conda-forge \
    jupyterlab-lsp \
    python-lsp-server

