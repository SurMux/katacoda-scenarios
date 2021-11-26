# Apache Kafka

Apache Kafka ist eine kostenfreie Software zur Speicherung und Verarbeitung von Datenströmen, dessen Inhalte auch exportiert werden können.

# Funktionsweise

Daten in jeglicher Form werden an ein oder an mehrere sogenannte Topics gesendet. Diese Topics sind vergleichbar mit voneinander getrennte Datenbanken, die lediglich für die Aufnahme und Speicherung von Daten zuständig sind. Jedes einzelne Topic befindet sich allerdings im selben Kafka Cluster, das die Umgebung für mehrere Kafka Server bereitstellt, wo die Daten schlussendlich gelagert werden.

![Kafka Architektur[1]](./assets/kafka-arch1.png)

Die Abbildung stellt den Datenfluss ausgehend vom sogenannten Producer, über die Topics, bis zum Consumer dar.
Kafka stellt noch weitere Funktionalitäten bereit, jedoch ist das Ziel dieses Szenarios genau diesen Datenfluss herzustellen [2].

# Apache Zookeeper

Zookeeper ist eine ebenfalls von Apache entwickelte Software, die Konfigurations- und Synchronisationsmöglichkeiten für Verteilte Systeme bereitstellt. Auf Kafka bezogen, ist Zookeeper in diesem Szenario für die Überwachung des Kafka Clusters, der Topics und der Partitionen zuständig.

Apache Zookeeper erlaubt zusätzlich das simultane Senden sowie Abfragen von Daten eines einzelnen Topics oder einer Partition.

Neuere Versionen von Apache Kafka sollen Datenströme ohne die Hilfe von Zookeeper erlauben. Allerdings sind das noch Ausblicke, deswegen wurde für dieses Szenario die aktuell noch gängigere Variante, die Nutzung von Zookeeper, gewählt. [3]

# Topic

![Apache Kafka Topic[2]](./assets/topic.png)

Ein einzelnes Topic kann partitioniert werden. Dadurch erlaubt Kafka eine logische Trennung zwischen Daten eines gemeinsamen Topics, was eine Sortierung bereits beim Einlesen ermöglicht.

Als Datenstrom ist standardmäßig der komplette Topicinhalt gemeint, allerdings werden hier die Daten durch eine Partition als Datenstrom bezeichnet, denn dadurch steigt die visuelle Aussagekraft der Abbildung.

Bekommt ein Topic Daten zugesendet, so hängt Kafka, ähnlich wie bei einer verketteten Liste, den Datensatz an die hinterste Stelle der Partition an. Diese Daten können anschließend jederzeit von Verbrauchern abgerufen werden.
Durch die zu sehende Indexierung können auch Datenbereiche widergegeben werden. [2]
