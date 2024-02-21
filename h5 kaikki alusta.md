# Kaikki alusta
  
  Pohjat:  
  Kone:  
  Käytössäni on käytettynä hankittu HP Elitebook DESKTOP-284RPGL  
  Suoritin Intel(R) Core(TM) i7-5500U CPU @ 2.40GHz 2.40 GHz -Asennettu RAM 16,0 Gt (15,4 Gt käytettävissä)  
  Keskusmuistia käyettävissä 8,3 Gt  
  Koneeseen on asennettu: Windows 10 Education suomeksi Versio 22H2  
  päivitetty 17.1.2024  

  Virtuaalikone:  
  Oracle VM virtual Box tuoteversio 7.0.14.16195  
  siinä käytössä Debian (live 12.4.0-amd-xfce.iso)  latasin live 12.5.0-amd-xfce.iso -kuvakkeen  
  Käytän nettiä matkapuhelimen kautta mobiilitukiasemasta. 
  

## a) koko juttu: 

  18.2.2024 klo 19:53  
  aloitus.  
  Hävitin edellisen koneen.   

  Uusi kone:  
  Base memory 4069MB ja virtuaalimuistia 40GB   
  käynnistin koneen iso -imagella debian-live-12.5.0-amd64-xfce.iso (ladattu 17.2.2024)  
  ![Ihmekone1 aloitus](https://github.com/VaMaija/Linux2024/assets/142913118/20cdf160-9693-4c29-b825-fd35e1a2064e)
  ![ihmekone2 tiedot](https://github.com/VaMaija/Linux2024/assets/142913118/08160cb0-123a-4f32-8774-9bec1b09d3bc)

  Käynnistin Debianin valikon ensimmäisestä kohdasta (Live)  
  
  20:02 Klikkasin Install Debian -kuvakkeesta työpöydältä, ”launch anyway”    
  Kieli American English  
  Aikavyöhyke Helsinki  
  Näppäimistö Finnish Default  
  "erase disk"  
  Täytin omat tietoni, salasanan ja koneen uuden nimen Ihmekone. Klikkasin alhaalta komentoa ”Install”  
  20:07 – 20.25 valmis  
  20:13 $ sudo apt-get update  
  20:14 $ sudo apt-get upgrade  
  20.15 $ sudo apt-get install ufw  
  20:18 $ systemctl status ufw, palomuuri on koneessa, mutta se ei ole käynnissä.  
  ![ihmekone3 tulimuuri kuoli](https://github.com/VaMaija/Linux2024/assets/142913118/e0da80f2-cef6-44d0-9fc0-8cc5d6ec281b)

  20:23 $ exit  
  20:25 Ihmekoneen asennus valmis, uudelleenkäynnistys.  
  ![ihmekone 4 valmis](https://github.com/VaMaija/Linux2024/assets/142913118/26eaadd6-93f8-433a-8608-3fdc888ea37e)

  20:32 Ihmekoneen alkunäytöltä  Devices > Insert Guest additions DC image…   
  File system -välilehdeltä VBox_GAs_7.0 > vasemmalla klikkauksella Mount    
  poistin ”cd-levyn” levyasemasta.   

  **Terminaalista**   
  20:43 ei löytänyt ufw:n statusta  
  $ sudo apt-get -y install ufw  
  $ sudo ufw enable  
  $ sudo apt-get install micro  
  $ sudo apt-get install nano  
  20:46 $ sudo apt-get install apache2  
  20:49 muistin, että en ole käynnistänyt VBoxLinuxAdditionia. Suuntasin sinne: cd /media/maijav/ ja yritin löytää ls komennolla tietoja. Siellä ei ollut mitään, koska olin poistanut cd-levyn asemasta. Menin GUI:n kautta laittamaan levyn takaisin. Palasin takaisin terminaaliin:  
  /media/maijav/ ls ja sieltä löytyi ko kansio.   
  20:53 $ sudo bash /media/maijav/VBox_GAs_7.0.14/VBoxLinuxAdditions.run  
  21:02 Restart   
  21:07 cd-levy pois asemasta  
  21:08 testasin toimiiko netti. Kello näyttää olevan oikeassa ajassa ja Iltalehden etusivu näyttää hyvältä.   
  21:10 Testasin localhost-etusivun. Näytti Apachen Default Pagen oikein.   
  21:15 $ echo ”Virhepainallus, palaa takaisin lahtoruutuun” | sudo tee /var/www/html/index.html  
  21:18 localhost sivulle ja shift+refresh = teksti päivittyy localhost-sivulle  
  21:21 $ sudoedit /etc/apache2/sites-available/ihmekone.example.com.conf  
  21.27 $ cat /etc/apache2/sites-available/ihmekone.example.com.conf  
  21:30 korjataan kirjoitusvirheet  
  21:31 $ sudo a2ensite ihmekone.example.com  
  21:32 $ sudo systemctl restart apache2  
  21:33 $ mkdir -p /home/debian/publicsites/ihmekone.example.com  
  ei lupaa. Tajusin, että kyseessä pitäsi olla /home/maijav/publicsites… korjaukset hostin conf -tiedostoon  
  21:41 $ mkdir -p /home/maijav/publicsites/ihmekone.example.com  
  21:45 echo lillerilalleri > /home/maijav/publicsites/ihmekone.example.com/index.html ei toiminut. Lillerilalleri ei lisääntynyt localhostin tekstiin.   
  21:48 cd /etc/apache2/  
  /etc/apache2/ cd sites-available/  
  siellä se ihmekone on, ei ole päällä.   
  22:00 sudo a2ensite ihmekone.example.com    
  kone on jo päällä.    
  cd /etc/apache2/sites-enabled > siellä on myös 000-default.conf vielä päällä.   
  sudo a2dissite 000-default.conf   
  systemctl reload apache2  
  kieltäytyi  
  22:10 localhost avautuu ihmekone.example.comin index.html tekstinä lillerilalleri.   
  sudoedit /etc/hosts -kautta voisin asentaa ihmekoneen ip-osoitteeksi ostamani ip-osoitteen.   
  Uniaika 22:14 kone pauselle  

  **jatkuu 19.2.2024** 18:30 luin raportistani, mitä olin jo tehnyt. Katselin ottamani kuvakaappaukset myös.  
  etsin localhostiin vaikuttavan index.html -tiedoston ja vaihdoin siihen tekstin:   
  ~/publicsites/ihmekone.example.com$ echo ”tuttuluu” > index.html  
  18:40 Tarkastin etusivulta, että teksti vaihtui sopivaksi.   
  
  18:55 tein lyhyen html-sivun etusivulle ihmekone.example.com/index.html , jonka käynnistin localhostissa.    
  toimii   
  Menin digitaloceanin sivulle ja kirjauduin sisälle.     
  19:12 loin uuden projektin, jotta muistaisin, miten tämä menee.     
   + new project ”uusikone”     
  	getting started   
  	deploy a virtual machine   
  	Amsterdam  
  	Debian  
  	Debian 12 x64   
  	size : Shared CPU Basc (Plan selected)  
  	CPU Regular Disk type SSD  
  	6$ /month, 1GB/1CPU/25GM SSD Disk/1000 GB transfer  
  	hostname ihmekone  
  	tags #petosmuija   

  **Sitten namecheapiin**:   
  19:29 kirjauduin sisään namecheapiin ja menin omalle profiilisivulleni.  
  Advanced DNS kohdasta poistin petosmuija.pro nimen aiemmalta ip-osoitteelta 164.92.211.151  
  ”Remove”  
  klo 19:25 liitin petosmuija.pro -nimen vastaamaan ostamastani ip-osoitteesta.   
  palasin Debianin terminaaliin:   
  komennolla ssh root@178.62.222.121 yritin ottaa yhteyden ostamaani ip-osoitteeseen, mutta huomaisin että ihmekoneeseen ei ole vielä asennettu ssh ohjelmaa.   
  sudo apt-get install ssh  
  uusi yritys samalla komennolla. Sormenjälkivarmistus kirjoittamalla ”yes”   
  19:48 digitaloceanista saamani root-salasanan avulla pääsin sisään.  
  19:50 apt-get upgrade  
  19:50 apt-get update  
  19:53 apt-get install ufw  
  19:53 ufw allow 22/tcp  
  19:54 ufw enable  
  19:55 adduser maikki  
  lisäsin käyttäjälle salasanan ja kerroin käyttäjän nimen   
  adduser maikki sudo  
  19:59 testasin toisessa terminaalissa, että pääsin kirjautumaan käyttäjällä sisälle.   
  maikki@ihmekone:~$ ssh maikki@178.62.222.121  
  onnistui.   
  kokeilin peruskyttäjä Maikilla asentaa sudo-oikeuksin ko osoitteeseen nanon.   
  sudo apt-get install nano  
  voidaan sulkea root:  
  $sudo usermod -lock root  
  20.07 ei onnistunut, koska root oli käytössä toisessa terminaalissa. Root -terminaalissa komento ”exit” päättää etäyhteyden. yritin samaa uudelleen lopetettuani root yhteyden. En onnistunut.  
  Tarkastin käskyn TeroKarvien.comista  ja käsky oli --lock root  
  annoin käskyn rootista ja sen jälkeen poistuin root -käyttäjän tilasta exitillä  
  [root] usermod –lock root  
  $ sudoedit /etc/ssh/sshd_config  
  vaihdoin kohtaan PermitRootLogin sanan ”yes” manuaalisesti sana ”no”  
  $ sudo service ssh restart  
  $ sudo apt-get update  
  $ sudo apt-get upgrade  
  $ sudo ufw allow 80/tcp  
  yritin varmistaa että uusi ip toimii lyömällä ip-osoitteen osoiteriville. Ei toiminut, koska siellä ei ollut mitään tietoa.   
  20.37$ sudo apt-get install apache2  
  ja sitten debianin default-sivu tuli näkyviin. Kokeilin googlettaa ”petosmuija.pro” ja sen kautta sain myös näkyviin ko default-sivun.  
  muutetaan defaultia: echo ”petosmuijan sivu” | sudo tee /var/www.html/index.html  
  etusivulla taas shift + refresh  
   20:56 sudo apt-get install micro nano  
  luodaan konfiguraatiot   
  ![petosmuija com konfiguraatiot](https://github.com/VaMaija/Linux2024/assets/142913118/5044a1e8-86b7-4b3f-bbdd-13d1cd0c41a2)


  **luodaan verkkosivun sisältö**:  
  21:11   
  21:20 sudo a2ensite petosmuija.example.com.conf  
  21:20 sudo a2dissite 000-default.com.conf  
  21.24 sudo systemctl reboot apache2  
  21.25 ssh maikki@petosmuija.pro	  
  pääsin sisään.   

 **20.2.2024**   
  17:00 Jatkuu, minulla oli nyt kaksi ip-osoitetta 178.62.222.121 (hankittu 19.2.2024) ja 164.92.211.151 (hankittu 11.2.2024 ) lyömällä hakukenttään ip-osoitteen 164.92.211.151 tulee tulokseksi petosmuija.pro -sivut, jotka on luotu viime kerralla.  
  Lyömällä osoitteeksi 178.62.222.121 tulee tulokseksi echolla aluksi syöttämni tervehdys, joka löytyy osoitteesta /var/www/html/ eli alkuperäisestä index.html -osoitteesta eikä osoitteesta 
cd /home/maikki/publicsites/petosmuija.example.com/index.html  
  Löysin eilen luodusta petosmuijan configista puuttuvan kaksoispisteen, korjasin sen  ja uudelleenkäynnistin apachen. katsoin selaimesta toimiiko, ei toimi. Antoi uuden virheilmoituksen ”403, Access denied you are forbidden to access this resource”  
  Aavistein, että minun pitää antaa käyttölupa ko tietoon erikseen, mutta tarkastin asiaa logitiedoista /var/log/apache2/  +less error.log, se antoi saman vastauksen.  
  Logitiedoista päättelin myös, että virtuaalikoneen kello on eri ajassa kuin rauta.  
  Menin oman käyttäjän publicsites -kansioon ja annoin sieltä komennon chmod o=r  
  Menin digitaloceanin dropletiin ja tuhosin ensimmisen ip-osoitteen jospa se auttaisi. ei auttanut.   
  petosmuija.prota ei enää löydy eikä ip-osoitteeseen saa yhteyttä. 	 

![portti 80 forbidden](https://github.com/VaMaija/Linux2024/assets/142913118/7c5814f3-f909-451e-8926-1294d6b7be52)
![viimeinen tilanne](https://github.com/VaMaija/Linux2024/assets/142913118/5ed2201b-a658-450f-8a8a-741a8965ba60)
 Olin antamassa periksi ja menin iltalehden sivuille virtuaalikoneen kautta. weppisivuja ei löydy. Kyse ei siis ollut pelkästään vääristä konfiguraatioista. Käynnistin koko virtuaalikoneen uudelleen.  
 
## B) ssh

  Tähän piti etsiä tietoja paljon netistä, koska asiasta ei ollut juuri opetusmateriaalia kurssilla.  
  21.2.2024  
  Kirjauduin sisälle etäyhteydellä  
  $ ssh maikki@petosmuija.pro  
  $ ssh-keygen  
  Hyväksyin ehdotetun tallennuspaikan ( /home/maikki/ .sh/id_rsa) painamalla enter  
  En antanut salasanaa tai lausetta, menin eteenpäin painamalla enter/return, sain key fingerprintin.  
  Varmistin, että avaimen .ssh hakemiston käyttöoikeudet ovat vain omistajalla ja avaimen myös  
  Omistajalle täydet oikeudet kansioon:   
  $ chmod u=rwx, go= .ssh  
    Omistajalle täydet oikeudet avaimiin:   
  $ chmod=rwx, go= .ssh/*  
  $ ls -l ~/ .ssh/* näytti, että id_rsa (yksityinen avain) ja id_rsa.pub on tallennettuna Maikki käyttäjälle.  
  $ cat ~/ .ssh/id_rsa.pub näytti julkisen avaimen.  
  kopioin julkisen avaimen seuraavalla käskyllä   
  $ ssh-copy-id maikki@178.62.222.121, jolloin sama julkinen avain kopioitui palvelimen authorized_keys -kohtaan. Tarkistin sen komennolla  
  $ cat ~/ .ssh/autohorized_keys  
  Kyseinen komento antoi näkyviin julkisen avaimen.   
  ![ssh serverillä](https://github.com/VaMaija/Linux2024/assets/142913118/e7299fc2-e92c-4655-8845-af0d90c781c4)

  
  Käyttöön ohjeistus täältä:    
  Youtube, [Akamai developer](https://www.google.com/search?q=youtube+ssh+keygen+linux&sca_esv=ca099d9a36fc4ee2&sxsrf=ACQVn09NxqKBwrsV2Y9OofIdz0XyNuOSoA%3A1708515495918&ei=p-DVZcPTN6vUwPAPjNSpgAk&udm=&oq=youtube+ssh+keygen+lin&gs_lp=Egxnd3Mtd2l6LXNlcnAiFnlvdXR1YmUgc3NoIGtleWdlbiBsaW4qAggAMgUQIRigATIFECEYoAEyBRAhGKABSPMZUIIGWNUKcAF4AZABAJgBpQGgAd0DqgEDMS4zuAEByAEA-AEBwgIKEAAYRxjWBBiwA8ICBhAAGBYYHogGAZAGCA&sclient=gws-wiz-serp#fpstate=ive&vld=cid:5da732e0,vid:33dEcCKGBO4,st:0)  katsottu 21.2.2024 ja täältä 
 [Helsingin yliopisto](https://www.cs.helsinki.fi/group/kuje/compfac/ssh_avain.html)  luettu 21.2.2024  

 ## C) digging host

   Asiaa ei ole opetettu kurssilla millään tavoin. Menin hommassa [Youtubevideon](https://www.google.com/search?sca_esv=d15b179212b804a0&sxsrf=ACQVn08ruDZ3dT07lgLYvGloOoj3Xf2TdQ:1708528928385&q=using+host+and+dig+debian+12&tbm=vid&source=lnms&sa=X&ved=2ahUKEwiQn_We3ryEAxWFKxAIHSfnB5UQ0pQJegQIDBAB&biw=1707&bih=781&dpr=1.13#fpstate=ive&vld=cid:7f58e41b,vid:_rK2CZfvWZk,st:0) avulla eteenpäin.  

   $ sudo apt-get install -y bind9-dnsutils bind9-host  
   $ dig petosmuija.pro  
  ![dig petosmuija pro](https://github.com/VaMaija/Linux2024/assets/142913118/7c3dc47c-b3ad-404a-bb7f-08471379c0a0)

  kuvasta näkyy, että petosmuija.pro -sivusto vastaa ip:stä 178.62.222.121 ei erroreita. Server vastaa osoitteesta 67.207.67.2 . Tämä on [traficomin](https://www.traficom.fi/en/communications/fi-domains/whois-shows-public-information-domain-name) ip-tiedustelun mukaan digitaloceanin osoite.  
  ![traficom ip](https://github.com/VaMaija/Linux2024/assets/142913118/856a047b-6fe4-4b9f-9956-4ec19afbbae8)

 **Host**

 $ host petosmuija.pro  
 ![host petosmuija pro](https://github.com/VaMaija/Linux2024/assets/142913118/a2d0627b-2c45-4633-a226-c53be9c83cce)  
 komento antoi nytille tiedon, että minulla on käytössäni ilmeisesti sähköpostin välityspalvelin. Kävin kasomassa tilanteen namecheapin asetuksista ja vaihdoin asetukset niin, että sähköpostipalvelua ei tarvita. 
 ![vaihto namecheapissa](https://github.com/VaMaija/Linux2024/assets/142913118/cc10c06c-18ef-4e2c-b88c-e346aa262c4a)
  Homma muuttui seuraavasti :  
 ![before after sähköposti](https://github.com/VaMaija/Linux2024/assets/142913118/e0005383-ee7d-48b4-9034-8416596e5100)

 
 ## m) vagrant

   kokeilu epäonnistui  

   ![vagrant epäonnistuminen](https://github.com/VaMaija/Linux2024/assets/142913118/9da31506-31fc-4e38-8457-abdcf530b456)

   ![eipä onnistunut](https://github.com/VaMaija/Linux2024/assets/142913118/f689f1c9-1b96-4069-a707-22f91a8b84af)


  Tehtävien tekemiseen meni kolme iltaa. Alkoi 19.2.2024 klo 19:54 ja lopetin 21.2.2024 21.2.2024 klo 19:25 . 
 


 
   






### lähteet:  

  uusi iso-kuvake https://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/ 

  Tero karvinen: *https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/  luettu 19.2., 20.2., 21.2. 
  *https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/  luettu 19.2., 20.2., 21.2.
  Susanna Lehto  *https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/  luettu 19.2., 20.2., 21.2.

  [Akamai developer](https://www.youtube.com/watch?v=33dEcCKGBO4&t=907s))  katsottu 21.2.2024
  
 [Helsingin yliopisto](https://www.cs.helsinki.fi/group/kuje/compfac/ssh_avain.html)  luettu 21.2.2024  

  dig ja host  
  [@IDGTECHtalk](https://www.youtube.com/watch?v=_rK2CZfvWZk) katsottu 21.2.2024  
  [Geeks for geeks-sivusto](https://www.geeksforgeeks.org/host-command-in-linux-with-examples/)  luettu 21.2.2024
  [Traficom](https://www.traficom.fi/en/communications/fi-domains/whois-shows-public-information-domain-name) katsottu 21.2.2024

 



