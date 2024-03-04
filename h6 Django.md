X) Lue ja tiivistä. 
Verkkosivuillaan artikkelissaan [Django 4 Instant Customer Database Tutorial]( https://terokarvinen.com/2022/django-instant-crm-tutorial/) Tero Karvinen antoi ohjeet Django weppisovelluksen julkaisemisesta palvelimelle. Siinä on ohjeet asiakastieto-projektin luomisesta ja projektin konfiguraatioiden tekemisestä. Ohjeissa käydään läpi myös PostgreSQL-tietokantaa, mutta en ymmärrä tässä vaiheessa sisältöä tarpeeksi. 
Toisessa Tero Karvisen artikkelissa [Deploy Django 4]( https://terokarvinen.com/2022/deploy-django/)  hän antaa samaan aiheeseen liittyen yksityiskohtaisemmat ohjeet 

Lähteet:  
  Terokarvinen.com  
  https://chat.openai.com/c/c74f0736-1548-4a1e-bf29-d4ada38ace07  
 

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
![1  pip install -r requirements](https://github.com/VaMaija/Linux2024/assets/142913118/1d90298b-fba3-4cb7-be69-4ef7006073ef)

  asentaa kaikki tekstitiedostoon kirjatut ohjelmat. Tässä asennettiin django versio 5.0.2  
  
  18:38  
  $ django-admin startproject uusitehtava  
  $ cd uusitehtava  
  uusitehtava/ ./manage.py runserver   
  En onnistunut pääsemään verkkosivulle.   

  Otin varalla olleen virtuaalikoneen käyttöön. Tein samat ohjelmakomennot kuin alussa. Nyt huomasin, että olin aiemmassa koneessa poistunut ENV -tilasta jossain vaiheessa, joten django ei asentunut oikeaan paikkaan. Vaihdettuani konetta onnistuin kun tein kaiken uudelleen.   
![3  varakone onnistunut suoritus](https://github.com/VaMaija/Linux2024/assets/142913118/ec144d27-5a64-4430-b0aa-45b51af42699)

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
   ./manage.py runserver   
  Onnistui tällä komennolla. 
  Syötin adminille käyttäjänimeni ja luodun salasanan.   
  

  Sisällä 20:02 
  ![4  onnistunut](https://github.com/VaMaija/Linux2024/assets/142913118/ac7ad9dc-f1c8-45c3-9406-8c97de493d0e)

  Customer database  
  menin täysin ohjeiden mukaan, koska osaamista muusta ei vielä ole.   
  ~/uusitehtava$ ./manage.py startapp crm  
  $ micro uusitehtava/settings.py  
  lisäsin listaan ’crm’,   
![7  add app crm](https://github.com/VaMaija/Linux2024/assets/142913118/118245e2-c2b9-4266-9bd2-4bee3ed9bac3)

  $ micro crm/models.py   
  $./manage.py makemigrations  
![5  managepy makemigrations](https://github.com/VaMaija/Linux2024/assets/142913118/c79aa24b-24e4-4ee2-9da0-ce6121fa6ec9)

  ./manage.py makemigrations on Django-kehyksen hallintaskriptin komento, jota käytetään tietokannan muutosten seurauksena tulevien migratioiden luomiseen.  
  Kun kehittäjä tekee muutoksia Django-sovelluksen malleihin (models.py-tiedostot), kuten lisäämällä uusia tauluja tai muuttamalla olemassa olevia tauluja, nämä muutokset on heijastettava tietokantaan. makemigrations-komento luo nämä migratiotiedostot, jotka ovat Python-skriptejä, jotka kuvaavat tietokannan rakenteen muutokset.  
  Nämä migratiotiedostot tallennetaan sovelluksen migrations-hakemistoon ja niitä käytetään myöhemmin migrate-komennon avulla, joka todellisuudessa muuttaa tietokantaa vastaamaan näitä migratiotiedostoja.  
  Lyhyesti sanottuna ./manage.py makemigrations luo uudet migratiotiedostot Django-sovelluksen muutoksille, jotka vaikuttavat tietokannan rakenteeseen. /Chat.gpt  

  $ ./manage.py migrate 	soveltaa juuri haettuja tietokantoja tietokantaan  
  $ ./manage.py runserver antaa virheilmoituksen, jonka mukaan olen tehnyt kirjoitusvirheen:  
![9  managemigrations](https://github.com/VaMaija/Linux2024/assets/142913118/22caeafd-a850-4670-91e4-1b4c409dcece)

  $ micro crm/admin.py  
  kirjoitusvirheen korjaaminen   
  ![8  so far so good](https://github.com/VaMaija/Linux2024/assets/142913118/9e016aa0-a870-4bce-89ba-32dec79cd0e5)

  $ ./manage.py runserver uudelleen  
  pääsin sisään ja näin crm -tiedot, mutta en pystynyt muokkaamaan tietoja.   
  ![12 lisää ongelmia](https://github.com/VaMaija/Linux2024/assets/142913118/6290658b-6e63-4395-a3f2-8ad71f69737b)  

  palasin ensin katsomaan mikä on mennyt pieleen.   
  menin katsomaan uusitehtava-kansiosta settings.py tietoja.   
  Niitä ei löytynyt. Muistin ne kuitenkin tehneeni.   
  Selvisi, että olen luonut uusitehtävä -kansion sisään uusitehtävä-kansion.   
  ![13  kanio kansion sisällä](https://github.com/VaMaija/Linux2024/assets/142913118/d483aa34-663a-4847-be17-5e28f57041ab)

  Takana sen verran rankka viikko, että jätin tehtävän tässä vaiheessa tähän ja palaan uusilla aivoilla asiaan myöhemmin.   



    EDIT:   

    Jatkuu ma 4.3.2024 klo 20:19  

    $ sudo apt-get update  
  $ sudo apt-get upgrade  
  $ sudo apt-get -y install bash-completion  
  $ export EDITOR=micro  
  bash-completion on työkalu, joka laajentaa bash-terminaalin automaattisen täydennyksen toiminnallisuutta, mikä helpottaa komentojen ja tiedostojen nimeämistä.  
  $ sudo apt-get install apache2  
  localhostina näkyy apachen default-sivu  
  $ echo ”testihommat” | sudo tee /var/www/html/index.html   
  toimii localhostin sivulla.   
  $ mkdir -p publicwsgi/petosmuija/static/  
  $ echo "petosmuijajutut talla sivulla" | tee publicwsgi/petosmuija/static/index.html  
  $ sudo a2ensite petosmuija.conf  
  $ sudo a2dissite 000-default.conf  
  $ sudo sytemctl restart apache2  
  petosmuijan testisivu näkyy localhost/static/ -osoitteessa   
  ![14  petosmuija static](https://github.com/VaMaija/Linux2024/assets/142913118/9ae6f066-a9a0-4152-a22f-4ec05391bd5b)  
  $ sudo apt-get -y install virtualenv  
  $ cd publicwsgi/   
  /publicwsgi$ virtualenv -p python3 --system-site-packages env  
  /publicwsgi$ source env/bin/activate  
  /publicwsgi$ which pip  
           /home/maijav/publicwsgi/env/bin/pip  
  /publicwsgi$ micro requirements.txt  
       django  
  /publicwsgi$ pip install -r requirements.txt  
  /publicwsgi$ django-admin –version  
     5.0.3  
  ~/publicwsgi$ django-admin startproject maanantaiprojekti  
  ~/publicwsgi$ ls
  env  maanantaiprojekti  petosmuija  requirements.txt
  ~/publicwsgi$ sudoedit /etc/apache2/sites-available/petosmuija.conf  
  
  ~/publicwsgi$ sudo apt-get -y install libapache2-mod-wsgi-py3  
  /publicwsgi$ /sbin/apache2ctl configtest  
  syntax ok  
  ~/publicwsgi$ sudo systemctl restart apache2  
  ~/publicwsgi$ curl -s localhost|grep title  
  403 forbidden   

  
