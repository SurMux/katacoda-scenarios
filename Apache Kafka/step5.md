producer.py

`producer.py`{{open}}

<pre class="file" data-filename="producer.py" data-target="replace">
import time
import json
import random
from datetime import datetime
from random_data import generate
from kafka import KafkaProducer
</pre>

<pre class="file" data-filename="producer.py" data-target="append">

def serializer(data):
    return json.dumps(data).encode('utf-8')

producer = KafkaProducer(
    bootstrap_servers = ['localhost:9092'],
    value_serializer = serializer
)    

</pre>

<pre class="file" data-filename="producer.py" data-target="append">

topics = ["dwh_kafka_topic_1", "dwh_kafka_topic_2"]

if __name__ == '__main__':
    while True:
        random_topic = random.choice(topics)
        if random_topic == "dwh_kafka_topic_1":
            rand_part = random.randint(0, 1)
            producer.send(random_topic, data, partition = rand_part)
        else:
            producer.send(random_topic, data)
        data = generate()
        print(f'{datetime.now()} Generiere Datensatz: {str(data)}')

        time.sleep(4)      

</pre>