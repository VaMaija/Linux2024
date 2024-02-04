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

Seuraaavana päivänä (2.2.2024) palasin yrityksen ääreen: 

Lopulta ajattelin tarpeeksi yksinkertaisesti ja yritin journalctl f ja sudo tail -f komennoilla eteenpäin. Eli katsoin vihdoin Teron ohjeita (tää pitää tehdä kuin Ikean huonekalut, ensin ilman ohjeita ja sitten oluen voimalla ja ohjeiden kanssa. )

![sudo tail ei toimi](https://github.com/VaMaija/Linux2024/assets/142913118/c8b926d2-c459-4677-90af-6ddc3d2fd9a3)  
  Tämä komento ei toiminut. 

![accesslog1](https://github.com/VaMaija/Linux2024/assets/142913118/607f618b-84eb-4c80-b2f1-07ed31614635)
  Komento toimi, mutta antoi vanhat lokitiedot.  

![error loki](https://github.com/VaMaija/Linux2024/assets/142913118/2f7c2769-d68b-4149-a1e2-b7eb6557446f)
antoi virhetietoja oikeasta päivästä. Nettikäyttäjän tietoja ei kuitenkaan löytynyt. 

Lopulta löysin pääkäyttäjän lokitiedot 

![vhosts access log](https://github.com/VaMaija/Linux2024/assets/142913118/91506c2d-8c03-4a9a-b33f-4907f734610c)

  Ensimmäinen rivi:   
  **maija.example.com** = vhostin nimi  
  **80:** = Vhostin porttitieto  
 **127.0.0.1** = localuser -sivulle annettu ip.osoite  
 **[tapahtuman aikaleima]**  
 **"GET /HTTP/1.1"** = komento, ota yhteyttä aloitussivuun. 
 **200 239** = http-koodit "ok" ja "Redirect" 
 **Mozilla/5.0 (X11; Linux x86_64; rv 109.0) Gecko/20100101 Firefox/115.0)** = Käyttäjäagentin tiedot

  Toinen rivi;  
   **maija.example.com** = vhostin nimi  
   **80:** = Vhostin porttitieto  
   **127.0.0.1** = localuser -sivulle annettu ip.osoite  
   **[tapahtuman aikaleima]**   
   **"GET /favicon.ico HTTP/1.1"** Etsi kuva hakukenttään  
    ![favicon ico](https://github.com/VaMaija/Linux2024/assets/142913118/2decc13d-598f-46ba-a5c4-a3169cb20327)  
   **404 487** = http-koodit "Not Found" ja "Request Terminated#  
  **"http://localhost/"** = osoite mihin yhdistetään ja sen jälkeen tietona uudelleen Käyttäjäagentin tiedot

ja oikealla komennolla: 
![oikea komento](https://github.com/VaMaija/Linux2024/assets/142913118/0bd7dbea-053f-46b4-93e7-f9cc9f6e0063)  

Löysin käyttäjän tiedot: 
![netin käyttäjätiedot](https://github.com/VaMaija/Linux2024/assets/142913118/46c5e607-72ed-4cd4-a7dc-a2fe1daa6297)

  Tässä on aikaleima alussa  
  sen jälkeen näkyy virtuaalikoneen nimi ja dbus-daemon eli virtuaalikoneen dataliikenteen välittäjän numero. Linux Virtual Delivery Agent 2201  
  [session uid=1000] = avautuvan yhteyden tunnus  
  [pid:2201] = prosessin tunniste (sama kuin dbus-daemonin tunniste?)  
  Activating service name = org.xfce.Xconf = avautuva palvelu on kyseisen tiedoston sisällön mukainen  
  requested by 1.43 = pyydetty sekunteja sitten?  
  (uid=1000, pid=2525,   
  comm= xfsettingsd = demonin asetukset   
  sm-client-id numeroyhdistelmällä löytyy yhteyden käyttäjätieto.   

  Tässä tiedon takaa löytyi seuraava vastaus: 

  ![käyttäjän tiedot](https://github.com/VaMaija/Linux2024/assets/142913118/8fc34563-148b-400e-8433-5364931dd61a)

## c) Etusivu uusiksi

  4.2.2024 18.20 availin virtuaalikoneen ja pakotin itseni tehtävän pariin. Tuntui kun aivoni olisivat tyhjentyneet kaikesta tarvittavasta tiedosta. 

  Käytin apuna (Youtuben videota)[https://www.youtube.com/watch?v=rvwYzs6IMog&t=673s]

   18:20 $ sudo apt-get update | upgrade
       $ sudo systemctl reboot apache2 (copypaste ei toiminut edelleenkään.)
 18:33 sudo systemctl status apache2
    luodaan polku verkkosivuston tiedostoille: 
       $ sudo mkdir -p /var/www/hattu.example.com 
    tarkastin muodostuiko polku oikein: 
       $ ls /var/www/hattu.example.com, mitään sisältöä ei löytynyt
 18:50 $ sudo nano /var/www/hattu.example.com/index.html
	Kirjoitin lyhyen tervehdyksen. 
	
	Luodaan virtuaali-isännöitsijä: 
 19:05
		$ cd /etc/apache2/sites-available/
		/etc/apache2/sites-available$ sudo cp 000-default.conf ./hattu.example.com.conf
		/etc/apache2/sites-available$ sudo nano hattu.example.com.comf
	kirjoitin väliin ServerName ja ServerAliaksen ja loin yhteyden var/www/hattu.example.com, josta tiedot on luettavissa
	Seuraavaksi pitäisi ottaa hattu.example.com.conf käyttöön. 
		/etc/apache2/sites-available$ sudo a2ensite hattu.example.com.comf
	Se ei onnistunut, sillä olen nimennyt tiedoston väärin: hattu.example.com.comf vaikka pitäisi olla hattu.example.com.conf 
	Korjauspuuhat nimeämisessä: sudo mv hattu.example.com.comf hattu.example.com.conf
		/etc/apache2/sites-available$ sudo a2ensite hattu.example.com.conf
		/etc/apache2/sites-available$ sudo systemctl reload apache2 
	Shift+reload ja localhost 
	
	korjataan tekstiä aloitussivulla 
	/var/www/hattu.example.com$ sudo nano index.html
20:10	
	Näkymä localhostissa: 

  
  
  

 




## m) GitHUb Education paketti hankittu

https://education.github.com/ 





Lähteet: 
  x) The Apache Software Foundation https://httpd.apache.org/docs/2.4/vhosts/name-based.html luettu 30.1.2024 
  b) http koodit /Iana https://www.iana.org/assignments/http-status-codes/http-status-codes.xhtml  
  ja https://www.kinexmedia.com/blog/http-status-codes/ luettu 2.2.2024  
   mozilla käyttäjäagentti https://myip.ms/view/comp_browseragents/2912097/Mozilla_5_0_X11_Ubuntu_Linux_x86_64_rv_109_0_Gecko_20100101_Firefox_109_0.html  
   Favicon.ico https://en.wikipedia.org/wiki/Favicon luettu 2.2.2024

   dbus-daemon [2201] https://docs.citrix.com/en-us/linux-virtual-delivery-agent/2201/linux-virtual-delivery-agent-2201.pdf oogletettu 2.2.202024
   pid  https://www.baeldung.com/linux/pid-tid-ppid googletettu 2.2.2024  ja  
     https://stackoverflow.com/questions/23243154/finding-ip-address-using-linux-pid  
   
 
  

