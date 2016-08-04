FROM ubuntu:14.04

RUN echo "deb http://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list \
 && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 642AC823 \
 && apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y sbt g++ \
 && rm -rf /var/lib/apt/lists/*

# Ensure compiler-interface being compiled
ADD ../res/build.sbt /tmp/
ADD ../res/t.scala /tmp/
RUN cd /tmp/ && sbt compile

ENTRYPOINT cd /data/ && sbt
