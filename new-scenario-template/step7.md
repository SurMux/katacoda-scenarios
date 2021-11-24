

`docker exec -it kafka /bin/sh`{{executeT1}}

`cd /opt/kafka/bin`{{executeT1}}

`kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic dwh_kafka_topic_1 --from-beginning`{{executeT1}}

`docker exec -it kafka /bin/sh`{{executeT2}}

`cd /opt/kafka/bin`{{executeT2}}

`kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic dwh_kafka_topic_2 --from-beginning`{{executeT2}}

`pzthon3 producer.py`{{executeT3}}

`pzthon3 consumer.py`{{executeT4}}