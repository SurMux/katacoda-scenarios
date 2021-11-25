Nun kommt es schließlich zur Implemetierung des Producers und Consumers sowie des Datengenerators.

Wenn alle Befehle ausgeführt wurden, so befindet sich das Terminal aktuell im root-Verzeichnis. 

Python besitzt ein Kafka-Modul, dass die Entwicklung und Anbindung der Programme erleichtert.

`python3 -m pip install kafka-python`{{execute}}

# Datengenerator

Um die Entwicklung zu beginnen, muss zuerst eine Python-Datei angelegt werden.

`touch random_data.py`{{execute}}

Da der Datengenerator zufällige Künstlerdaten erstellt und diese Objekte wenigstens teilweise verständlich lesbar sein sollten, wird ein Zufallsgenerator für Namen angebunden.

`python3 -m pip install names`{{execute}}

Mit einem Klick auf folgende Datei wird sie im Editor geöffnet.

`random_data.py`{{open}}

Den Anfang machen die Importe. Keiner dieser Module ist verpflichtet, sie werden allerdings für die hier erstellten Zufallsdaten benötigt.

<pre class="file" data-filename="random_data.py" data-target="replace">
import datetime
import random
import string
import names
</pre>

Folgend eine leicht angepasste Methode für die Ermittlung eines zufälligen Jahres für die Veröffentlichung der Musik.

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

Nun kommt es zum eigentlichen Datengenerator. 
Er setzt den Künstlernamen mit der importierten Methode aus dem zuvor genannten name-Modul.
Der Liedtitel ist eine zufällige Folge von ASCII-Zeichen.
Das Veröffentlichungsdatum wird mit der oben stehenden Methode gesetzt und die insgesamten Zuhörer werden ebenfalls zufällig bestimmt.

<pre class="file" data-filename="random_data.py" data-target="append">
def generate():
    
    artist = names.get_full_name()
    song = ''.join(random.choice(string.ascii_letters) for i in range(10))
    release = random_date(2000)
    views = random.randint(3, 3999999)

    return {
        'artist': artist,
        'song': song,
        'release': release,
        'views': views
    }
    
</pre>

Die main-Methode dient eigentlich nur zu Testzwecken, um eine fehlerfreie Generierung auszugeben.

<pre class="file" data-filename="random_data.py" data-target="append">
if __name__ == '__main__':
    print(generate())
</pre>

