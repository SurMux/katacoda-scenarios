consumer.py

`consumer.py`{{open}}

<pre class="file" data-filename="consumer.py" data-target="replace">
import json
from kafka import KafkaConsumer, consumer
</pre>

<pre class="file" data-filename="consumer.py" data-target="append">

if __name__ == '__main__':

     consumer1 = KafkaConsumer(
        'dwh_kafka_topic_1',
        bootstrap_servers = 'localhost:9092',
        auto_offset_reset = 'earliest'
    )

    dwh_kafka_topic_1_part = TopicPartition(topic, 0)
    
    for data in dwh_kafka_topic_1_part:
        print(json.loads(data.value)) 

</pre>