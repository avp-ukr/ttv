FROM ubuntu:trusty

RUN export DEBIAN_FRONTEND=noninteractive \
  && apt-get update \
  && apt-get -y install --no-install-recommends \
    wget \
    ca-certificates \
    libpython2.7 \
    python-setuptools \
    python-m2crypto \
    python-apsw \
  && apt-get clean && rm -rf /var/lib/apt/lists/* \
  && wget -nv -O - http://dl.acestream.org/ubuntu/14/acestream_3.0.5.1_ubuntu_14.04_x86_64.tar.gz | tar xvz \
  && mv acestream_3.0.5.1_ubuntu_14.04_x86_64 /usr/share/acestream

ENTRYPOINT ["/usr/share/acestream/acestreamengine"]
