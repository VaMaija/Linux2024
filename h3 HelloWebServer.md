# Hello Web server
### Apache webbipalvelin (demonit vol 1)

## X) The apache softwear foundation 2023, Name based virtual host support. 
  Nimeen perustuva virtuaalipalvelimen hallinta on yksinkertaisempaa kuin ip-osoitteeseen perustuvan varsinaisen verkkopalvelimen hallinta. Verkkosivulla ollessa konkreettinen DNS -osoite se tarvitsee jokaiselle palvelimelle oman ip-osoitteen. Samaan konkreettiseen ip-osoitteeseen voidaan osoittaa useita nimeen perustuvia virtuaalipalvelimia, jolloin ip-osoitteita tarvitaan vähemmän. Nimipalvelin erotetaan isäntäpalvelimesta tekemällä DNS serverille asetukset, jonka perusteella Apache Http serveri löytää oikean sivun.   
  
  Nimeen perustuva virtuaalipalvelin tarvitsee aina ip-osoitteeseen perustuvan verkkosivun alustakseen. Ennen kuin palvelin voi päättää mikä verkkosivustu palautetaan se tarkastaa ip-osoitteen ja portin. Sen jälkeen se vertaa pyynnön Ip-osoitetta ja porttia VirtualHost määrittelyjen kanssa ja valitsee parhaiten vastaavan.  
  
  Käytettäessä nimeen perustuvaa virtuaalipalvelinta ensimmäinen askel on VirtualHost-blokin luonti. Siinä tulee olla ServerName,joka määrittää mitä virtuaalipalvelinta palvellaan ja DocumentRoot joka osoittaa paikan, mistä kyseiset asetukset haetaan. VirtualHost -blokissa määritellään ServerAlias -nimillä kaikki ne nimet, joilla haluaa verkkosivuson löytyvän.  

## A) veppipalvelin localhost-osoitteessa  

![paikallinen isäntä](https://github.com/VaMaija/Linux2024/assets/142913118/84608f65-97cf-42a7-9f96-382c00394641)

## B) Lokitiedot ja niiden analysointi 

Koin tuskan hetkiä, kun en löytänyt lokitietoja millään. 

![access denied](https://github.com/VaMaija/Linux2024/assets/142913118/ca07020b-5e34-4269-a089-16a095799755)

Kiitos kurssikaveri K Syrjän (puhelu 1.2.2024) pääsin hajulle siitä missä niitä lymyää, mutta en edelleenkään löytänyt verkkosivun lokituksia. 

Seuraaavana päivänä palasin yrityksen ääreen: 

Lopulta ajattelin tarpeeksi yksinkertaisesti ja yritin journalctl f ja sudo tail -f komennoilla eteenpäin. Eli katsoin vihdoin Teron ohjeita (tää pitää tehdä kuin Ikean huonekalut, ensin ilman ohjeita ja sitten oluen voimalla ja ohjeiden kanssa. )

![sudo tail ei toimi](https://github.com/VaMaija/Linux2024/assets/142913118/c8b926d2-c459-4677-90af-6ddc3d2fd9a3)  
  Tämä komento ei toiminut. 

![accesslog1](https://github.com/VaMaija/Linux2024/assets/142913118/607f618b-84eb-4c80-b2f1-07ed31614635)
  Komento toimi, mutta antoi vanhat lokitiedot.  

![error loki](https://github.com/VaMaija/Linux2024/assets/142913118/2f7c2769-d68b-4149-a1e2-b7eb6557446f)
antoi virhetietoja oikeasta päivästä. Nettikäyttäjän tietoja ei kuitenkaan löytynyt. 

Lopulta löysin pääkäyttäjän lokitiedot 

![vhosts access log](https://github.com/VaMaija/Linux2024/assets/142913118/91506c2d-8c03-4a9a-b33f-4907f734610c)

ja 
![oikea komento](https://github.com/VaMaija/Linux2024/assets/142913118/0bd7dbea-053f-46b4-93e7-f9cc9f6e0063)

![netin käyttäjätiedot](https://github.com/VaMaija/Linux2024/assets/142913118/46c5e607-72ed-4cd4-a7dc-a2fe1daa6297)




## m) GitHUb Education paketti hankittu

https://education.github.com/ 

##  



Lähteet: 
  x) The Apache Software Foundation https://httpd.apache.org/docs/2.4/vhosts/name-based.html luettu 30.1.2024 

