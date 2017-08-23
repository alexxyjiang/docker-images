FROM debian:stable
MAINTAINER Alex, Jiang <alexxyjiang@gmail.com>
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
RUN apt update --fix-missing
RUN apt install -y curl wget gnupg2 apt-transport-https
COPY ./sources.list /etc/apt/sources.list
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2EE0EA64E40A89B84B2DF73499E82A75642AC823
RUN apt update --fix-missing

# version control and develop tools
RUN apt install -y build-essential cmake exuberant-ctags git
RUN apt install -y openjdk-8-jdk
RUN apt install -y scala sbt
RUN apt install -y python3 python3-dev python3-pip python3-tk

# jupyterlab with python3
RUN useradd -m -g users -s /bin/bash devuser
USER devuser
RUN pip3 install --user --upgrade pip
RUN pip3 install --user --upgrade setuptools
RUN pip3 install --user --upgrade jupyterlab
RUN cd && git clone https://github.com/jupyter-scala/jupyter-scala.git && cd jupyter-scala && ./jupyter-scala && cd
COPY ./jupyter_notebook_config.py /home/devuser/.jupyter/jupyter_notebook_config.py
RUN mkdir -p /home/devuser/data

ENTRYPOINT ["/home/devuser/.local/bin/jupyter", "lab", "--no-browser"]
