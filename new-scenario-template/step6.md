consumer.py

`consumer.py`{{open}}

<pre class="file" data-filename="consumer.py" data-target="replace">
import json
from kafka import KafkaConsumer, consumer
</pre>

<pre class="file" data-filename="consumer.py" data-target="append">

if __name__ == '__main__':

    consumer = KafkaConsumer(
        'messages',
        bootstrap_servers = 'localhost:9092',
        auto_offset_reset = 'earliest'
    )
    
    for msg in consumer:
        print(json.loads(msg.value))   

</pre>