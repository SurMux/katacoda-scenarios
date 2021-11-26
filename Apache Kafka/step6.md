Ein letztes mal muss eine Datei erstellt werden.

`touch consumer.py`{{execute}}

Und auch im Editor geöffnet werden.

`consumer.py`{{open}}

Die Consumer-Datei ist in diesem Beispiel nicht unbedingt vonnöten, da die angesammelten Daten über die Kafka Shell ausgegeben werden können.
Allerdings kann ein Consumer, wie bereits angesprochen, Daten zusätzlich verarbeiten. Dafür wäre die ANbindung eines Consumer mittels einer Datei notwendig, was folgend auch demonstriert wird.

Folgend werden dennoch beide Wege für die Datenausgabe vorgeführt.

Zuerst aber wieder einmal der Importblock, der ebenfalls ein Kafka-Modul beinhaltet.

<pre class="file" data-filename="consumer.py" data-target="replace">
import json
from kafka import KafkaConsumer, consumer
</pre>

Die main-Methode legt den Consumer unter Angabe des Topics an. Anschließend sollen alle bereits gesammelten und die noch ankommenden Daten auf dem Terminal ausgegeben werden. [5]

<pre class="file" data-filename="consumer.py" data-target="append">

if __name__ == '__main__':

    consumer2 = KafkaConsumer(
        'dwh_kafka_topic_2',
        bootstrap_servers = 'localhost:9092',
        auto_offset_reset = 'earliest'
    )
    
    for data in consumer2:
        print('Neuer Datensatz: ', json.loads(data.value)) 

</pre>