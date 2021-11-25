# Apache Kafka

Apache Kafka ist eine kostenfreie Software zur Speicherung und Verarbeitung von Datenströmen, dessen Inhalte auch exportiert werden können.

# Funktionsweise

Daten in jeglicher Form werden an ein oder an mehrere sogenannte Topics gesendet. Diese Topics sind vergleichbar mit voneinander getrennte Datenbanken, die lediglich für die Aufnahme und Speicherung von Daten zuständig sind. Jedes einzelne Topic befindet sich allerdings im selben Kafka Cluster.

![Apache Kafka simple Architektur[1]](katacoda-scenarios/Apache Kafka/assets/kafka-arch.PNG)

Die Abbildung stellt den Datenfluss ausgehend vom sogenannten Producer, über die Topics, bis zum Consumer dar.
Kafka stellt noch weitere Funktionalitäten bereit, jedoch ist das Ziel dieses Szenarios genau diesen Datenfluss herzustellen.

# Topic

![Apache Kafka Topic](katacoda-scenarios/Apache Kafka/assets/kafka-arch.PNG)

Ein einzelnes Topic kann partitioniert werden. Dadurch erlaubt Kafka eine logische Trennung zwischen Daten eines gemeinsamen Topics, was eine Sortierung bereits beim Einlesen ermöglicht.
Als Data Stream (Datenstrom) ist standardmäßig der komplette Topicinhalt gemeint, allerdings werden hier die Daten durch eine Partition als Data Stream bezeichnet, denn dadurch steigt die visuelle Aussagekraft der Abbildung.
Bekommt ein Topic Daten zugesendet, so hängt Kafka, ähnlich wie bei einer verketteten Liste, den Datensatz an die hinterste Stelle der Partition an. Diese Daten können anschließend jederzeit von Verbrauchern abgerufen werden.
Durch die zu sehende Indexierung können auch Datenbereiche widergegeben werden.
