
1
`clear`{{execute T1}}

`docker exec -it kafka /bin/sh`{{execute T1}}

`cd /opt/kafka/bin`{{execute T1}}

`kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic dwh_kafka_topic_1 --partition 0`{{execute T1}}

`^C`{{execute ctrl-seq T1}}

`exit`{{execute ctrl-seq T1}}
2
`printf 'Öffne Terminal 2'`{{execute T2}}

`docker exec -it kafka /bin/sh`{{execute T2}}

`cd /opt/kafka/bin`{{execute T2}}

`kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic dwh_kafka_topic_1 --partition 1`{{execute T2}}

`^C`{{execute ctrl-seq T2}}

`exit`{{execute ctrl-seq T2}}
3
`printf 'Öffne Terminal 3'`{{execute T3}}

`python3 consumer.py`{{execute T3}}

`^C`{{execute ctrl-seq}}
4
`printf 'Öffne Terminal 4'`{{execute T4}}

`python3 producer.py`{{execute T4}}

`^C`{{execute ctrl-seq}}