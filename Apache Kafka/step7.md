Wenn alle Dateien korrekt angelegt wurden, müssen sie mit der docker-compose-Datei im root-Verzeichnis liegen.

Um dies zu bestätigen, kann kurz der Verzeichnisinhalt ausgegeben werden.

`ls`{{execute}}

Sind hier alle Dateien zu finden, kann das Terminal gesäubert werden, um die abschließenden Tests zu starten.

`clear`{{execute T1}}

# Erstes Topic Partition 0

Für die Testzwecke wird wieder einmal die Kafka Shel benötigt.

`docker exec -it kafka /bin/sh`{{execute T1}}

Und um die Kafka-Skripte auszuführen, muss das bin-Verzeichnis aufgerufen werden.

`cd /opt/kafka/bin`{{execute T1}}

Der folgende Befehl stellt den vorher angesprochenen Weg dar, ohne einen Consumer Daten einer Partition auszugeben.
Dabei muss das Topic und die Partition angegeben werden.

`kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic dwh_kafka_topic_1 --partition 0`{{execute T1}}

Folgender Befehl dient zur Unterbrechung der Datenausgabe.

`^C`{{execute ctrl-seq T1}}

Ist die Ausgabe unterbrochen, kann die Kafka Shell hoermit verlassen werden.

`exit`{{execute ctrl-seq T1}}

# Erstes Topic Partition 1

Um den Parallelismus von Datenabfragen beziehungsweise den Consumern darzustellen, müssen mehrere Terminals mit unterschiedlichen Empfängern geöffnet werden.

`printf 'Öffne Terminal 2'`{{execute T2}}

Wieder einmal die kafka Shell öffnen und in das bin-Verzeichnis navigieren.

`docker exec -it kafka /bin/sh`{{execute T2}}

`cd /opt/kafka/bin`{{execute T2}}

Der folgende gibt nun noch die zweite Partition des ersten Topics aus.

`kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic dwh_kafka_topic_1 --partition 1`{{execute T2}}

Befehle zum Abbruch von Ausgabe und zum Beenden der Kafka Shell.

`^C`{{execute ctrl-seq T2}}

`exit`{{execute ctrl-seq T2}}

# Consumer

Die selbstgeschriebene Consumer-Datei benötigt ein weiteres Terminal

`printf 'Öffne Terminal 3'`{{execute T3}}

Mittels Python kann die Consumer-Datei dann gestartet werden.

`python3 consumer.py`{{execute T3}}

Zum Beenden des Consumers.

`^C`{{execute ctrl-seq}}

# Producer

Das letzte Terminal für den Producer öffnen.

`printf 'Öffne Terminal 4'`{{execute T4}}

Und wieder mit Hilfe von Python den Producer starten.

`python3 producer.py`{{execute T4}}

Zum Beenden des Producers.

`^C`{{execute ctrl-seq}}