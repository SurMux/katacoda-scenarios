# Topic erstellen

Um Apache Kafka zu verwalten, muss zuallererst die Kafka Shell gestartet werden. Da Kafka innerhalb eines Docker Containers läuft, muss die Shell über ein Docker Kommando geöffnet werden.

`docker exec -it kafka /bin/sh`{{execute}}

Alle Kafka Shell Skripte befinden sich im Kafka bin-Ordner. Um ein Skript auszuführen, muss erst dorthin navigiert werden.

`cd /opt/kafka/bin`{{execute}}

Nun können Topics mit Hilfe des kafka-topics Skriptes erstellt werden.
Der folgende Code Ausschnitt kreiert ein Topic mit dem Namen dwh_kafka_topic_1 und zwei Partitionen. Dabei muss auch der Name sowie der Port von zookeeper angegeben werden.

`kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 2 --topic dwh_kafka_topic_1`{{execute}}

Soll das Topic nicht in unterschiedliche Bereiche partitioniert werden, so verbleibt es bei einer Partition wie im folgenden Beispiel mit dem Topic dwh_kafka_topic_2.

`kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic dwh_kafka_topic_2`{{execute}}

Das selbe Skript erlaubt es zusätzlich alle Topics mit deren Partitionen auszugeben. Die Ausgabe versichert, dass beide Topics fehlerfrei erstellt wurden.

`kafka-topics.sh --bootstrap-server=localhost:9092 --describe`{{execute}}

Das Terminal befindet sich immer noch in der Kafka Shell. Um diese zu schließen, muss der exit Befehl ausgeführt werden.

`exit`{{execute}}

