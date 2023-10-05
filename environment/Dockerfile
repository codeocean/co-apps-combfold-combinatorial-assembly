# hash:sha256:b840c48109d2ece48c9fe222ab3f14667e749da9d51780ebe9a81b1213e13e9d
FROM registry.apps.codeocean.com/codeocean/mambaforge3:22.11.1-4-ubuntu22.04

ARG DEBIAN_FRONTEND=noninteractive

ARG GIT_ASKPASS
ARG GIT_ACCESS_TOKEN
COPY git-askpass /

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        g++=4:11.2.0-1ubuntu1 \
        libboost-all-dev=1.74.0.3ubuntu7 \
        make=4.3-4.1build1 \
    && rm -rf /var/lib/apt/lists/*

RUN mamba install -y \
        jupyterlab==4.0.6 \
    && mamba clean -ya

RUN pip3 install -U --no-cache-dir \
    biopython==1.81 \
    numpy==1.25.2 \
    py3dmol==2.0.3 \
    scipy==1.11.2

COPY postInstall /
RUN /postInstall
