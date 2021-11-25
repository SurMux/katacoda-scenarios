# Producer

In Apache Kafka stellt ein Producer eine Datenquelle dar. Wie bereits dargestellt, kann ein Producer Daten an mehrere Empfänger senden.

Sendet ein Producer Daten an ein bestimmtes Topic ohne Spezifikation der Partionen, so werden die eingetroffenen Daten gleichmäßig über alle Topics verteilt.

Im Praxisbeispiel ist das Senden an ein Topic sowie das Senden an ausgewählte Partitionen umgesetzt, um die Trennung innerhalb eines Topics darzustellen. [1]

# Datengenerator

Um eine visuelle Umsetzung von Kafka zu bieten, werden selbstverständlich Daten benötigt. Einfachheitshalber verwendet die Umsetzung einen selbstgeschriebenen Datengenerator, der zufällige json-Objekte von Künstlern und deren Lieder erstellt.

Die Implementierung findet in Python statt, da es eine leichte Anbindung von Kafka besitzt.

# Consumer

Die Consumer sind die letzte Instanz des Data Streams. Wenn Daten benötigt werden, können sie aus ausgewählten Topics und/oder Partitionen mittels eines Consumers gezogen werden.

![Apache Kafka Consumer[1]](./assets/consumer.png)

