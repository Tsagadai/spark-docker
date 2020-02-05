FROM apache/zeppelin:0.8.1

ENV SPARK_VERSION 2.3.4
ENV HADOOP_PROFILE 2.7

RUN mkdir -p /opt/spark && wget -O - -nc https://www.apache.org/dist/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_PROFILE}.tgz | tar -xz -C /opt/spark

ENV SPARK_HOME=/opt/spark

EXPOSE 8080
