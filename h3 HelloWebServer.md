# Hello Web server
### Apache webbipalvelin (demonit vol 1)

## X) The apache softwear foundation 2023, Name based virtual host support. 
  Nimeen perustuva virtuaalipalvelimen hallinta on yksinkertaisempaa kuin ip-osoitteeseen perustuvan varsinaisen verkkopalvelimen hallinta. Verkkosivulla ollessa konkreettinen DNS -osoite se tarvitsee jokaiselle palvelimelle oman ip-osoitteen. Samaan konkreettiseen ip-osoitteeseen voidaan osoittaa useita nimeen perustuvia virtuaalipalvelimia, jolloin ip-osoitteita tarvitaan vähemmän. Nimipalvelin erotetaan isäntäpalvelimesta tekemällä DNS serverille asetukset, jonka perusteella Apache Http serveri löytää oikean sivun.   
  
  Nimeen perustuva virtuaalipalvelin tarvitsee aina ip-osoitteeseen perustuvan verkkosivun alustakseen. Ennen kuin palvelin voi päättää mikä verkkosivustu palautetaan se tarkastaa ip-osoitteen ja portin. Sen jälkeen se vertaa pyynnön Ip-osoitetta ja porttia VirtualHost määrittelyjen kanssa ja valitsee parhaiten vastaavan.  
  
  Käytettäessä nimeen perustuvaa virtuaalipalvelinta ensimmäinen askel on VirtualHost-blokin luonti. Siinä tulee olla ServerName,joka määrittää mitä virtuaalipalvelinta palvellaan ja DocumentRoot joka osoittaa paikan, mistä kyseiset asetukset haetaan. VirtualHost -blokissa määritellään ServerAlias -nimillä kaikki ne nimet, joilla haluaa verkkosivuson löytyvän.  

## A) veppipalvelin localhost-osoitteessa  

![paikallinen isäntä](https://github.com/VaMaija/Linux2024/assets/142913118/b51535ec-bc70-4ce9-9d14-690fda16aef6)

## B) Lokitiedot ja niiden analysointi 




Lähteet: 
  x) The Apache Software Foundation https://httpd.apache.org/docs/2.4/vhosts/name-based.html luettu 30.1.2024 

