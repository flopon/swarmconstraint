FROM ubuntu:20.04
LABEL Description="swarmconstraint" Version="0.4"

ENV TERM xterm

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
  apt-get install -y dialog apt-utils

RUN apt-get upgrade -y

RUN apt-get install -y \
  curl \
  python3 \
  python3-pip \
  ca-certificates \
  && pip3 install --upgrade --no-cache-dir setuptools \
  && apt-get remove --purge software-properties-common \
  && rm -rf /var/cache/apt/*

RUN pip3 install docker

ADD https://github.com/flopon/swarmconstraint/archive/0.4.tar.gz /tmp/swarmconstraint.tar.gz

RUN mkdir /opt/swarmconstraint && \
    tar --extract --file=/tmp/swarmconstraint.tar.gz --strip-components=1 --directory=/opt/swarmconstraint && \
    ln -s /opt/swarmconstraint/swarmconstraint/swarmconstraint.py /usr/local/bin/swarmconstraint.py

RUN which python3

ENTRYPOINT ["/usr/bin/python3", "/usr/local/bin/swarmconstraint.py"]

