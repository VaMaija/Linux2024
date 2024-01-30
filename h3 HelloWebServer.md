# Hello Web server
### Apache webbipalvelin (demonit vol 1)

## X) The apache softwaer foundation 2023, Name based virtual host support. 
  Nimeen perustuva virtuaalipalvelimen hallinta on yksinkertaisempaa kuin ip-osoitteeseen perustuvan varsinaisen verkkopalvelimen hallinta. Verkkosivulla ollessa konkreettinen DNS -osoite se tarvitsee jokaiselle palvelimelle oman ip-osoitteen. Samaan konkreettiseen ip-osoitteeseen voidaan osoittaa useita nimeen perustuvia virtuaalipalvelimia, jolloin ip-osoitteita tarvitaan vähemmän. Nimipalvelin erotetaan isäntäpalvelimesta tekemällä DNS serverille asetukset, jonka perusteella Apache Http serveri löytää oikean sivun. 
  Nimeen perustuva virtuaalipalvelin tarvitsee aina ip-osoitteeseen perustuvan verkkosivun alustakseen. Ennen kuin palvelin voi päättää mikä verkkosivustu palautetaan se tarkastaa ip-osoitteen ja portin. Sen jälkeen se vertaa pyynnön Ip-osoitetta ja porttia VirtualHost määrittelyjen kanssa ja valitsee parhaiten vastaavan. 
  Käytettäessä nimeen perustuvaa virtuaalipalvelinta ensimmäinen askel on Virtual-Host- blokin luonti. Siinä tulee olla ServerName,joka määrittää mitä virtuaalipalvelinta palvellaan ja DocumentRoot joka osoittaa paikan, mistä kyseiset asetukset haetaan.  
  
esimerkkierkki:  
<VirtualHost *:80>
    # This first-listed virtual host is also the default for *:80
    ServerName www.example.com
    ServerAlias example.com 
    DocumentRoot "/www/domain"
</VirtualHost>

<VirtualHost *:80>
    ServerName other.example.com
    DocumentRoot "/www/otherdomain"
</VirtualHost>






Lähteet: 
  x) The Apache Software Foundation https://httpd.apache.org/docs/2.4/vhosts/name-based.html luettu 30.1.2024 
