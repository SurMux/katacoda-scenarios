# Heading for Step 2

Kafka

`docker exec -it kafka /bin/sh`{{execute}}

`cd /opt/kafka/bin`{{execute}}

`kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 2 --topic dwh_kafka_topic_1`{{execute}}

`kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic dwh_kafka_topic_2`{{execute}}

`kafka-topics.sh --bootstrap-server=localhost:9092 --describe`{{execute}}

`exit`{{execute}}

