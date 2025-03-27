FROM alpine:latest AS builder

WORKDIR /tmp

COPY apache-zookeeper-*.tar.gz .
RUN tar -zxvf apache-zookeeper-*.tar.gz -C /

COPY jdk-* .
RUN tar -zxvf jdk-*.tar.gz -C /

FROM ubuntu:latest

RUN mkdir -p /home/zookeeper

WORKDIR /home/zookeeper

COPY --from=builder apache-zookeeper-* /home/zookeeper/zookeeper-current
COPY --from=builder /jdk-* /opt/java

RUN mkdir -p /home/zookeeper/cluster-data/zk/data

ENV PATH="/opt/java/bin:/home/zookeeper/zookeeper-current/bin:${PATH}"
ENV JAVA_HOME='/opt/java'

CMD ["/usr/bin/bash"]
