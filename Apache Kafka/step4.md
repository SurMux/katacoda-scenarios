random_data

Python

`python3 -m pip install kafka-python`{{execute}}

`touch random_data.py`{{execute}}

`touch producer.py`{{execute}}

`touch consumer.py`{{execute}}

`ls`{{execute}}

`python3 -m pip install names`{{execute}}

`random_data.py`{{open}}


<pre class="file" data-filename="random_data.py" data-target="replace">
import datetime
import random
import string
import names
</pre>

<pre class="file" data-filename="random_data.py" data-target="append">
#https://www.kite.com/python/answers/how-to-generate-a-random-date-between-two-dates-in-python
def random_date(year):
    start_date = datetime.date(year, 1, 1)
    end_date = datetime.date(datetime.datetime.now().year, datetime.datetime.now().month, datetime.datetime.now().day)

    time_between_dates = end_date - start_date
    days_between_dates = time_between_dates.days
    random_number_of_days = random.randrange(days_between_dates)
    random_date = start_date + datetime.timedelta(days=random_number_of_days)
    return str(random_date.day) + '.' + str(random_date.month) + '.' + str(random_date.year)
  
</pre>

<pre class="file" data-filename="random_data.py" data-target="append">
def generate():
    
    artist = names.get_full_name()
    song = ''.join(random.choice(string.ascii_letters) for i in range(10))
    release = random_date(2000)
    views = random.choice(range(0, 3999999))

    return {
        'artist': artist,
        'song': song,
        'release': release,
        'views': views
    }
    
</pre>

<pre class="file" data-filename="random_data.py" data-target="append">
if __name__ == '__main__':
    print(generate())
</pre>

