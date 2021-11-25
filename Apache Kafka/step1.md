# Docker Image aufsetzen

Für die praktische Umsetzung von Apache Kafka wurde eine Testumgebung durch ein Docker Image beritgestellt. Die benötigten Container stehen im Docker Hub bereit und die zugehörige docker-compose Datei befindet sich bereits im Verzeichnis. 
Der folgende Befehl sollte dies belegen. Analog lässt sich die Datei auch im Editor über dem Terminal finden.

`ls`{{execute}}

Falls sie sich ordnungsgemäß im root Verzeichnis befindet, so können die Images erstellt werden.

`docker-compose -f docker-compose.yml up -d`{{execute}}

Die docker-compose setzt die Namen sowie Ports der Images und gibt die Quellen der zu ziehenden Container von Docker Hub an.
Ob beide Images ordnungsgemäß laufen, belegt folgender Befehl.

`docker ps`{{execute}}

