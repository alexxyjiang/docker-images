FROM debian:stable
MAINTAINER Alex, Jiang <alexxyjiang@gmail.com>
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
RUN apt update --fix-missing

# version control and develop tools
RUN apt install -y build-essential cmake exuberant-ctags git \
    && apt install -y python3 python3-dev python3-pip python3-tk \
    && apt install -y graphviz xdg-utils

# jupyterlab with python3
RUN useradd -m -g users -s /bin/bash devuser
USER devuser
RUN pip3 install --user --upgrade six setuptools \
    && pip3 install --user --upgrade pip \
    && pip3 install --user --upgrade ipython numpy scipy requests graphviz matplotlib seaborn \
    && pip3 install --user --upgrade keras nltk sklearn statsmodels tensorflow \
    && pip3 install --user --upgrade jupyterlab
COPY ./jupyter_notebook_config.py /home/devuser/.jupyter/jupyter_notebook_config.py
RUN mkdir -p /home/devuser/data

ENTRYPOINT ["/home/devuser/.local/bin/jupyter", "lab", "--no-browser"]
