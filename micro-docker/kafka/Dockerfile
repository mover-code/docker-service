FROM wurstmeister/kafka

USER root
RUN echo "listeners=PLAINTEXT://kafka:9092" >> /opt/kafka_2.13-2.8.1/config/server.properties && \
    echo "advertised.listeners=PLAINTEXT://kafka:9092" >> /opt/kafka_2.13-2.8.1/config/server.properties && \
    ./opt/kafka_2.13-2.8.1/bin/kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 -partitions 1 --topic exchange-log