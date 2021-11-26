# Producer

In Apache Kafka stellt ein Producer eine Datenquelle dar. Wie bereits dargestellt, kann ein Producer Daten an mehrere Empfänger senden.

Sendet ein Producer Daten an ein bestimmtes Topic ohne Spezifikation der Partionen, so werden die eingetroffenen Daten gleichmäßig über alle Topics verteilt.

Im Praxisbeispiel ist das Senden an ein Topic sowie das Senden an ausgewählte Partitionen umgesetzt, um die Trennung innerhalb eines Topics darzustellen. [1]

# Datengenerator

Um eine visuelle Umsetzung von Kafka zu bieten, werden selbstverständlich Daten benötigt. Einfachheitshalber verwendet die Umsetzung einen selbstgeschriebenen Datengenerator, der zufällige json-Objekte von Künstlern und deren Lieder erstellt.

Die Implementierung findet in Python statt, da es eine leichte Anbindung von Kafka besitzt.

# Consumer

Die Consumer sind die letzte Instanz des Datenstroms. Wenn Daten benötigt werden, können sie aus ausgewählten Topics und/oder Partitionen mittels eines Consumers gezogen werden.

![Apache Kafka Consumer[1]](./assets/consumer.png)

Consumer können zusätzlich die Rolle eines Producers übernehmen, wenn geladene Daten verarbeitet und an andere Partitionen versendet werden müssen. Dieses Szenario bezieht sich allerdings auf das einfache Laden von Daten, ohne diese an weitere Empfänger zu versenden.

Wie bereits im Bild zu sehen, können mehrere Consumer gleichzeitig auf das selbe Topic zugreifen. Es spielt keine Rolle, ob sie auf unterschiedliche oder auf die identischen Partitionen zugreifen.

Wenn das Ausmaß des Datenstroms eines Topics aufgrund verschiedener Producer überschwemmt, kann ein Consumer bei der zeitgleichen Ausgabe nicht mehr mithalten. Deswegen ergibt es in solchen Fällen Sinn, Consumer auf einzelne Partitionen aufzuteilen. [4]