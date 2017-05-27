FROM buildbot/buildbot-worker:master

ARG DEBIAN_FRONTEND=noninteractive
ARG PYTHON_VERSION

USER root

RUN apt-get update && apt-get install -y wget

RUN cd /root \
 && wget --quiet https://www.python.org/ftp/python/${PYTHON_VERSION}/Python-${PYTHON_VERSION}.tar.xz \
 && tar xf Python-${PYTHON_VERSION}.tar.xz \
 && cd Python-${PYTHON_VERSION} \
 && ./configure \
 && make \
 && make altinstall \
 && cd .. \
 && rm -rf Python-${PYTHON_VERSION}*

RUN pip install -U pip wheel virtualenv

USER buildbot
