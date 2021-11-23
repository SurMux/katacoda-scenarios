producer.py

`producer.py`{{open}}

<pre class="file" data-filename="producer.py" data-target="replace">
import time
import json
import random
from datetime import datetime
from data import generate
from kafka import KafkaProducer
</pre>

<pre class="file" data-filename="producer.py" data-target="replace">

def serializer(data):
    return json.dumps(data).encode('utf-8')

producer = KafkaProducer(
    bootstrap_servers = ['localhost:9092'],
    value_serializer = serializer
)    

</pre>

<pre class="file" data-filename="producer.py" data-target="replace">

topics = ["dwh_kafka_topic_1", "dwh_kafka_topic_2"]

if __name__ == '__main__':
    while True:
        random_topic = random.choice(topics)
        data = generate()
        print(f'{datetime.now()} Generiere Datensatz: {str(data)}')
        producer.send(random_topic, data)

        time.sleep(4)      

</pre>