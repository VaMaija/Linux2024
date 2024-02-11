  Pohjat:   
  Kone:  
  Käytössäni on käytettynä hankittu HP Elitebook DESKTOP-284RPGL  
  Suoritin Intel(R) Core(TM) i7-5500U CPU @ 2.40GHz 2.40 GHz -Asennettu RAM 16,0 Gt (15,4 Gt käytettävissä)   
  Keskusmuistia käyettävissä 8,3 Gt  
  Koneeseen on asennettu: Windows 10 Education suomeksi Versio 22H2  
  päivitetty 17.1.2023   

  Virtuaalikone: 
  Oracle VM virtual Box tuoteversio 7.0.14.16195  
  siinä käytössä Debian (live 12.4.0-amd-xfce.iso)  



## X) asiaan liittyvät tekstit:  
  Susanna Lehdon [blogipostauksessa](https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/) Lehto antoi selkät askeleet pilvipalvelun hankkimiseksi, konfiguroimiseksi ja nimipalvelun liittämiseksi ko palveluun.  
  -Pilvipalvelimen vuokraus ja asennus  
  -palvelimen suojaus palomuurilla  
  -Kotisivut palvelimelle ja  
  -palvelimen ohjelmien päivitys  

  Tero Karvisen [kirjoituksessa](https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/)
  Hän muistutti valitsemaan vahvat salasanat, päivittämään aina softan ja huolehtimaan palomuurista ja root-käyttäjän suojauksesta.

## a) Vuokrasin pilveä
 ostin Digitaloceanista tilaa kokeilulle: 

 ![digitalocean](https://github.com/VaMaija/Linux2024/assets/142913118/449747ba-782c-4786-912b-b4e08b865160)
![debian](https://github.com/VaMaija/Linux2024/assets/142913118/3d720cd6-fc2b-42bd-a500-4a653507efbc)
![cpu](https://github.com/VaMaija/Linux2024/assets/142913118/dba4d38e-7a34-4592-bf4c-de04612f061f)
![droplet hontti](https://github.com/VaMaija/Linux2024/assets/142913118/deb5c275-5e0e-455e-a0a9-f3b80551785a)
![speksit ja ip-osoite](https://github.com/VaMaija/Linux2024/assets/142913118/270a0a72-0c1e-4f55-8e50-69083130e2a0)

  Tämän jälkeen suuntasin etäkäytön kautta kyseiseen osoitteeseen: 
![ssh@root](https://github.com/VaMaija/Linux2024/assets/142913118/e485feb1-8b18-4d53-a940-8dd9bca9e738)
![sormenjälki ja salasana rootiin](https://github.com/VaMaija/Linux2024/assets/142913118/18031b45-c424-4c85-9e91-db8b9d70a765)
![palomuuri ennen apachea](https://github.com/VaMaija/Linux2024/assets/142913118/1dd07539-2912-407a-823a-6c17c616471a)
  Palomuuri aiheutti harmaita hiuksia ja pistin koneen kiinni kiukkuisena.  
 
## b) alkutoimet: 
  Palasin agendaan sunnuntaina töiden jälkeen: 
  Rennompana onnistuin saamaan palomuurin kuntoon ja reiän oikeaan paikkaan. 

  loin käyttäjän maija, jolle annoin sudo-oikeudet (adduser maija, adduser maija sudo)  
  Annoin maijalle myös adm oikeudet 

  sitten jätin rootin rauhaan ja palasin touhuamaan maijana eli päivitin ohjelmistot updatella ja upgradella. 

## C) weppipalvelin omalle palvelimelle: 

![lopputulos](https://github.com/VaMaija/Linux2024/assets/142913118/d07ad696-49b9-43e4-80ea-60fb5681fc6c)  
 En saanut varaamaani nimeä petosmuija.pro -toimimaan sillä nimipalvelimella oli hieman haasteita palvelussa. Ja minulla oli haasteita huomata vahvistussähköpostia. 
 Nimen ja ip:n yhdistäminen jäi tällä kertaa tekemättä. 

 ip-osoitteella etsitty sivu näkyi puhelimella hyvin. 

![namecheap kumossa](https://github.com/VaMaija/Linux2024/assets/142913118/b522dfb4-3fb5-4809-8578-712c01642061)

Lähteet: 

Lehto, https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/ luettu 11.2.2024  
Karvinen https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/ luettu 11.2.2024
Tero Karvisen tunti 6.2.2024 


  
