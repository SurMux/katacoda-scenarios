consumer.py

`consumer.py`{{open}}

<pre class="file" data-filename="consumer.py" data-target="replace">
import json
from kafka import KafkaConsumer, consumer
</pre>

<pre class="file" data-filename="consumer.py" data-target="append">

if __name__ == '__main__':

    consumer2 = KafkaConsumer(
        'dwh_kafka_topic_2',
        bootstrap_servers = 'localhost:9092',
        auto_offset_reset = 'earliest'
    )
    
    for data in consumer2:
        print(json.loads(data.value)) 

</pre>