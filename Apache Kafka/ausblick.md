Der Nutzen von Apache Kafka wurde in diesem Szenario ersichtlich.
Als Streaming Plattform erlaubt Kafka das Versenden, Speichern, Bearbeiten und Laden von Daten in Echtzeit.

Diesen Vorteil Nutzen schon viele Unternehmen weltweit. Beispiele hierfür sind Airbnb, Cisco, Netflix oder auch BMW und jeder dieser Unternehmen verwendet Kafka, um ein anderes Ziel zu verwirklichen. Dafür werden die in diesem Szenario nicht ausgeführten zusätzlichen Funktionalitäten von Apache Kafka verwendet.

Dennoch basiert alles auf der selben Grundlage und das ist die Verarbeitung von Datenströmen, was in diesem Katacoda Szenario mit Hilfe eines Programmentwurfs erläutert wurde.

# Zukunft

Wie bereits angesprochen, erlauben neuere Versionen von Apache Kafka die Verarbeitung von Datenströmen ohne die Nutzung von Apache Zookeeper.
Zookeeper ablösen soll der sogenannte Quorum Controller. Grund dafür ist eine über die Jahre entstandene Komplexität in der Kombination von Zookeeper und Kafka, die nun aufgelöst werden soll.

Diese Versionen sind bereits öffentlich zugänglich, aber eine stabile Funktionalität ist nicht garantiert. Deswegen hat dieses Szenario die aktuell stabilere Einrichtung von Kafka mittels Zookeeper näher gebracht.

Ob ein Zookeeper freies Kafka oder weitere Kafka Funktionalitäten, im Bereich der Streaming Plattform Kafka gibt es noch viel zu lernen, was eine bessere Verarbeitung und größere Distribution von Daten ermöglicht.