FROM ubuntu:14.04

RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y apt-transport-https \
 && echo "deb https://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list \
 && sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2EE0EA64E40A89B84B2DF73499E82A75642AC823 \
 && apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y g++ openjdk-7-jdk \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y sbt \
 && rm -rf /var/lib/apt/lists/*

# Ensure compiler-interface being compiled
ADD res/build.sbt /tmp/
ADD res/t.scala /tmp/
RUN cd /tmp/ && sbt compile

ENTRYPOINT cd /data/ && sbt
