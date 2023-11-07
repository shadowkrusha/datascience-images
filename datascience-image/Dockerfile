FROM jupyter/datascience-notebook:94ab69dde0ad

ARG TARGETPLATFORM

RUN pip install \
    jupyter-server-proxy mesa

RUN conda install -c conda-forge \
    jupyterlab-lsp \
    python-lsp-server r-languageserver

USER root

# Java Installation
RUN apt-get update --yes && \
    apt-get install --yes --no-install-recommends \
    default-jdk unixodbc unixodbc-dev odbcinst  unixodbc-common libodbc2 libodbccr2 libodbcinst2 libltdl7 && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

ENV SNOWFLAKE_ODBC_VERSION=3.1.1

RUN \
  case ${TARGETPLATFORM} in \
    "linux/amd64") DOWNLOAD_ARCH="x86_64"; DOWNLOAD_DIR="linux" ;; \
    "linux/arm64") DOWNLOAD_ARCH="aarch64"; DOWNLOAD_DIR="linuxaarch64" ;; \
  esac \
  && cd /tmp \
  && echo https://sfc-repo.snowflakecomputing.com/odbc/${DOWNLOAD_DIR}/${SNOWFLAKE_ODBC_VERSION}/snowflake-odbc-${SNOWFLAKE_ODBC_VERSION}.${DOWNLOAD_ARCH}.deb  \
  && wget https://sfc-repo.snowflakecomputing.com/odbc/${DOWNLOAD_DIR}/${SNOWFLAKE_ODBC_VERSION}/snowflake-odbc-${SNOWFLAKE_ODBC_VERSION}.${DOWNLOAD_ARCH}.deb \
     -O snowflake-odbc.deb \
  && dpkg -i snowflake-odbc.deb \
  && rm snowflake-odbc.deb
    
USER ${NB_UID}
