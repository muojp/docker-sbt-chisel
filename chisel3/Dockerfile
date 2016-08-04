FROM ubuntu:14.04

RUN echo "deb http://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list \
 && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 642AC823 \
 && apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y sbt git make autoconf g++ flex bison openjdk-7-jdk \
 && rm -rf /var/lib/apt/lists/* \
 && cd /opt \
 && git clone https://github.com/ucb-bar/firrtl.git \
 && cd firrtl \
 && make build-scala \
 && cd /opt \
 && git clone http://git.veripool.org/git/verilator \
 && cd verilator \
 && git checkout verilator_3_880 \
 && unset VERILATOR_ROOT \
 && autoconf \
 && ./configure \
 && make -j2 \
 && make install

ENV PATH $PATH:/opt/firrtl/utils/bin

# Build Chisel 3 and install it locally
RUN cd /opt \
 && git clone https://github.com/ucb-bar/chisel3.git \
 && cd chisel3 \
 && sed -i -e 's/"3.0"/"3.0-SNAPSHOT"/' build.sbt \
 && sbt compile \
 && sbt publish-local \
 && rm -rf /opt/chisel3

# Ensure compiler-interface being compiled
ADD ../res/build.sbt /tmp/
ADD ../res/t.scala /tmp/
RUN cd /tmp/ && sbt compile

ENTRYPOINT cd /data/ && sbt
