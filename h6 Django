X) Lue ja tiivistä. 
Verkkosivuillaan artikkelissaan [Django 4 Instant Customer Database Tutorial]( https://terokarvinen.com/2022/django-instant-crm-tutorial/) Tero Karvinen antoi ohjeet Django weppisovelluksen julkaisemisesta palvelimelle. Siinä on ohjeet asiakastieto-projektin luomisesta ja projektin konfiguraatioiden tekemisestä. Ohjeissa käydään läpi myös PostgreSQL-tietokantaa, mutta en ymmärrä tässä vaiheessa sisältöä tarpeeksi. 
Toisessa Tero Karvisen artikkelissa [Deploy Django 4]( https://terokarvinen.com/2022/deploy-django/)  hän antaa samaan aiheeseen liittyen yksityiskohtaisemmat ohjeet 

Lähteet: 
https://chat.openai.com/c/c74f0736-1548-4a1e-bf29-d4ada38ace07
Terokarvinen.com

Su 3.3.2024 17:57
~$ sudo apt-get update
~$ sudo apt-get upgrade
~$ sudo apt-get -y install virtualenv
Virtualenv (Virtual Environment) on työkalu Pythonin kehittäjille, joka mahdollistaa erillisen Python-ympäristön luomisen projektin tarpeisiin. Tämä tarkoittaa sitä, että voit luoda erillisen Python-ympäristön jokaiselle projektille ja hallita projektikohtaisia riippuvuuksia erillään muista projekteista. (Chatgpt)
$ virtualenv --system-site-packages -p python3 env/
virtualenv on komento, joka käynnistää virtuaaliympäristön luonnin
--system-site-packages mahdollistaa pääsyn järjestelmän Python asenjuksen kirjastoihin virtguaaliympäristöstä. 
-p Python3 ilmoitta, että haluamme käyttää Python3 virtuaaliympäristön tulkkina. 
env/  hakemisto, johon virtuaaliympäristö luodaan. 
$ source env/bin/activate
lisäsi env-laatikon käyttäjänimen eteen merkiksi siitä, että toimitaan juuri luodussa virtuaaliympäristössä. 
$ which pip
/home/maijav/env/bin/pip 
pidetään pip ja sudo erossa toisistaan, sillä se saattaa aiheuttaa ongelmia tietoturvan kannalta. Antamalla Pipile sudo-oikeudet annan sille täydet käyttäjäoikeuden käyttäjäjärjestelmään. 
$ sudo apt-get install micro nano
$ micro requirements.txt kirjoitin tektitiedostoon django (oikeinkirjoitusta painotettiin tunnilla 27.2)
$ cat requirements.txt
$ pip install -r requirements.txt
asentaa kaikki tekstitiedostoon kirjatut ohjelmat. Tässä asennettiin django versio 5.0.2
18:38
$ django-admin startproject uusitehtava
$ cd uusitehtava
uusitehtava/ ./manage.py runserver 
En onnistunut pääsemään verkkosivulle. 

Otin varalla olleen virtuaalikoneen käyttöön. Tein samat ohjelmakomennot kuin alussa. Nyt huomasin, että olin aiemmassa koneessa poistunut ENV -tilasta jossain vaiheessa, joten django ei asentunut oikeaan paikkaan. Vaihdettuani konetta onnistuin kun tein kaiken uudelleen. 

Lisätään pääkäyttäjän käyttöliittymä. 
Env oli tipahtanut pois käytäjänimen edestä. $source /env/bin/activate
~/uusitehtava$ ./manage.py makemigrations
~/uusitehtava$ ./manage.py migrate
$ sudo apt-get install pwgen 
pwgen on komentoriviohjelma, joka luo satunnaisia, vahvoja salasanoja. Kun suoritat pwgen-komentoa ilman parametreja, se generoi yhden satunnaisen salasanan ja tulostaa sen komentoriville. Voit myös määrittää haluamasi pituisen salasanan ja/tai kuinka monta salasanaa haluat generoida
$ pwgen -s 20 1 loi minulle yhden 20 merkkiä pitkän salasanan, 
$ ./manage.py createsuperuser loi pääkäyttäjän, jolle annoin ko salasanan.  
Yritin tarkastaa verkkosivulta http://127.0.0.1:8000/admin/ mutta sivu ei latautunut. 
palasin ohjeissa taakepäin ja katsoin, miten sen aiemmin sain toimimaan. 
komento
 ./manage.py runserver?
Onnistui tällä komennolla. 
Syötin adminille käyttäjänimeni ja luodun salasanan. 

Sisällä 20:02
Customer database
menin täysin ohjeiden mukaan, koska osaamista muusta ei vielä ole. 
~/uusitehtava$ ./manage.py startapp crm
$ micro uusitehtava/settings.py
lisäsin listaan ’crm’, 
kuva
$ micro crm/models.py 
$./manage.py makemigrations

./manage.py makemigrations on Django-kehyksen hallintaskriptin komento, jota käytetään tietokannan muutosten seurauksena tulevien migratioiden luomiseen.
Kun kehittäjä tekee muutoksia Django-sovelluksen malleihin (models.py-tiedostot), kuten lisäämällä uusia tauluja tai muuttamalla olemassa olevia tauluja, nämä muutokset on heijastettava tietokantaan. makemigrations-komento luo nämä migratiotiedostot, jotka ovat Python-skriptejä, jotka kuvaavat tietokannan rakenteen muutokset.
Nämä migratiotiedostot tallennetaan sovelluksen migrations-hakemistoon ja niitä käytetään myöhemmin migrate-komennon avulla, joka todellisuudessa muuttaa tietokantaa vastaamaan näitä migratiotiedostoja.
Lyhyesti sanottuna ./manage.py makemigrations luo uudet migratiotiedostot Django-sovelluksen muutoksille, jotka vaikuttavat tietokannan rakenteeseen. /Chat.gpt

$ ./manage.py migrate 	soveltaa juuri haettuja tietokantoja tietokantaan
$ ./manage.py runserver antaa virheilmoituksen, jonka mukaan olen tehnyt kirjoitusvirheen: 

$ micro crm/admin.py
kirjoitusvirheen korjaaminen 
$ ./manage.py runserver uudelleen
pääsin sisään ja näin crm -tiedot, mutta en pystynyt muokkaamaan tietoja. 
palasin ensin katsomaan mikä on mennyt pieleen. 
menin katsomaan uusitehtava-kansiosta settings.py tietoja. 
Niitä ei löytynyt. Muistin ne kuitenkin tehneeni. 
Selvisi, että olen luonut uusitehtävä -kansion sisään uusitehtävä-kansion. 
Takana sen verran rankka viikko, että jätin tehtävän tässä vaiheessa tähän ja palaan uusilla aivoilla asiaan myöhemmin. 
