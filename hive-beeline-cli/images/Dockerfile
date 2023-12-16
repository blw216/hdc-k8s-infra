# Use a base image with Java (Hive requires Java)
FROM openjdk:8-jdk

# Optional: Set a maintainer or author label
LABEL maintainer="blawoods@icloud.com"

# Set environment variables for Hive and Hadoop (adjust versions as needed)
ENV HIVE_VERSION 3.1.2
ENV HADOOP_VERSION 3.3.6
ENV HIVE_HOME /opt/hive
ENV HADOOP_HOME /opt/hadoop
ENV HADOOP_PREFIX /opt/hadoop
ENV PATH $HIVE_HOME/bin:$HADOOP_HOME/bin:$PATH

# Install dependencies and tools
RUN apt-get update \
    && apt-get install -y wget procps \
    && rm -rf /var/lib/apt/lists/*

# Download and install Apache Hive
RUN wget https://downloads.apache.org/hive/hive-$HIVE_VERSION/apache-hive-$HIVE_VERSION-bin.tar.gz \
    && tar -xzf apache-hive-$HIVE_VERSION-bin.tar.gz -C /opt \
    && mv /opt/apache-hive-$HIVE_VERSION-bin $HIVE_HOME \
    && rm apache-hive-$HIVE_VERSION-bin.tar.gz

# Download and install Apache Hadoop (needed by Hive)
RUN wget https://downloads.apache.org/hadoop/common/hadoop-$HADOOP_VERSION/hadoop-$HADOOP_VERSION.tar.gz \
    && tar -xzf hadoop-$HADOOP_VERSION.tar.gz -C /opt \
    && mv /opt/hadoop-$HADOOP_VERSION /opt/hadoop \
    && rm hadoop-$HADOOP_VERSION.tar.gz

# Set the entrypoint to Beeline
ENTRYPOINT ["beeline"]
