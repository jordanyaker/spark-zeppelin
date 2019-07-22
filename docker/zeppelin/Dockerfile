FROM apache/zeppelin:0.8.0

RUN wget https://archive.apache.org/dist/spark/spark-2.1.1/spark-2.1.1-bin-hadoop2.7.tgz && \
  tar -xzvf spark-2.1.1-bin-hadoop2.7.tgz && \
  mv spark-2.1.1-bin-hadoop2.7 /opt/spark

ENV SPARK_HOME=/opt/spark

RUN add-apt-repository ppa:deadsnakes/ppa && \
  apt-get -y update && \
  apt-get -y install python3.4