Auch hier zuerst die Datei erstellen.

`touch producer.py`{{execute}}

Ebenfalls im Editor zum Bearbeiten Öffnen.

`producer.py`{{open}}

Der Importblock des Producers besitzt zwei obligatorische Module.
Das KafkaProducer-Modul sowie die geneate-Methode aus dem Datengenerator.

<pre class="file" data-filename="producer.py" data-target="replace">
import time
import json
import random
from datetime import datetime
from random_data import generate
from kafka import KafkaProducer
</pre>

Ein Producer wird angelegt unter Angabe des Ports und eines Serialisierers.
Dieser wird ebenfalls angelegt und sagt aus, dass die Daten als json-Objekt behandelt werden sollen.

<pre class="file" data-filename="producer.py" data-target="append">

def serializer(data):
    return json.dumps(data).encode('utf-8')

producer = KafkaProducer(
    bootstrap_servers = ['localhost:9092'],
    value_serializer = serializer
)    

</pre>

Die main-Methode generiert und sendet die Daten eigentlich nur jede 3 Sekunden an den Empfänger.
Der restliche Code dient zur zufälligen Bestimmung des Empfängers, um eine Abwechsulng zu schaffen.
Die Daten werden entweder an eine bestimmte Partition aus dem ersten Topic gesendet oder einfach an das zweite Topic. [5]

<pre class="file" data-filename="producer.py" data-target="append">

topics = ["dwh_kafka_topic_1", "dwh_kafka_topic_2"]

if __name__ == '__main__':
    while True:
        data = generate()
        random_topic = random.choice(topics)
        print(f'{datetime.now()} Generiere Datensatz: {str(data)}')
        if random_topic == "dwh_kafka_topic_1":
            rand_part = random.randint(0, 1)
            producer.send(random_topic, data, partition = rand_part)
            print(f'Sende an Topic: {random_topic} Partition: {rand_part}')
        else:
            producer.send(random_topic, data)
            print(f'Sende an Topic: {random_topic}')

        time.sleep(3)      

</pre>