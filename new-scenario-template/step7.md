
1
`docker exec -it kafka /bin/sh`{{execute T1}}

`cd /opt/kafka/bin`{{execute T1}}

`kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic dwh_kafka_topic_1 --from-beginning`{{execute T1}}
2
`docker exec -it kafka /bin/sh`{{execute T2}}

`cd /opt/kafka/bin`{{execute T2}}

`kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic dwh_kafka_topic_2 --from-beginning`{{execute T2}}
3
`python3 consumer.py`{{execute T3}}
4
`python3 producer.py`{{execute T4}}