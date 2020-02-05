# the base image is a trusted java build (https://registry.hub.docker.com/_/java/)
# FROM java:8

FROM ubuntu:18.04

ENV SPARK_VERSION 2.3.4
ENV HADOOP_PROFILE 2.7

MAINTAINER chris@scut.tl

####installing [software-properties-common] so that we can use [apt-add-repository] to install Java8
RUN apt-get update -y && \
apt-get install wget openjdk-8-jdk-headless supervisor -y


####downloading & unpacking Spark 2.2.1 [prebuilt for Hadoop 2.6+ and scala 2.10]
RUN mkdir -p /opt/spark && wget -O - -nc https://www.apache.org/dist/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_PROFILE}.tgz | tar -xz -C /opt/spark


#####adding conf files [to be used by supervisord for running spark master/slave]
COPY master.conf /opt/conf/master.conf
COPY slave.conf /opt/conf/slave.conf


#######exposing port 8080 for spark master UI
EXPOSE 8080

#default command: running an interactive spark shell in the local mode
CMD ["/opt/spark/bin/spark-shell", "--master", "local[*]"]
