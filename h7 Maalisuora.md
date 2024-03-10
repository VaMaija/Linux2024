5.3.2024 19.20

### a) Kolmella kielellä   
   Python:   
  $ micro ekakieli.py  
  print("hei maailma!")  
  $ python3 ekakieli.py  
![1 ekakieli python](https://github.com/VaMaija/Linux2024/assets/142913118/e0a7a4f2-f055-4204-b4e6-47cdbf866e3a)

  Bash:   
  $ micro tokakieli.sh  
  echo ”hei maailma!”  
  $ bash tokakeli.sh  
![2  tokakieli bash](https://github.com/VaMaija/Linux2024/assets/142913118/5f3d7c55-d04f-46a3-af69-d79b762e138b)

  Ruby:   
  $ micro kolmaskieli.rb  
  print (”hei maailma\n”)  
  $ ruby kolmaskieli.rb  
![3  kolmaskieli ruby](https://github.com/VaMaija/Linux2024/assets/142913118/c0806fe3-8f74-4c89-bd16-29b658763a86)

  ohjeet [Tero Karviselta](https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/?fromSearch=bash) 5.3.2024  



  ### b)  uusi komento kaikille  
  $ micro käyttäjätiedot  
  $ cat käyttäjätiedot  
  #!/usr/bin/bash  
  date  #komennon ajankohta  
  id #käyttäjätiedot  
  last # Viimeiset koneelle kirjautuneet käyttäjät  
![4  b käyttäjätiedot bash](https://github.com/VaMaija/Linux2024/assets/142913118/2d98ba55-7204-40c1-940b-647d48d15b38)

  $ bash käyttäjätiedot  
  toimii.   
  $ chmod ugo-rx käyttäjätiedot  #annetaan muillekin execute ja read -oikeudet ohjelmaan  
  $ ls -l  
  ![5  oikedet muille](https://github.com/VaMaija/Linux2024/assets/142913118/6f1f8bc2-9f5c-4cbb-8f9d-7435077b4f57)

  $ cp käyttäjätiedot /usr/local/bin  #kopioidaan toimiva komento kaikkien käytettäväksi
  ei onnistunut, permission denied. vaatii sudon toimiakseen, koska komento muodostetaan käyttöön kaikille. 
  $ sudo cp käyttäjätiedot /usr/local/bin  
  ![6  lopputulos](https://github.com/VaMaija/Linux2024/assets/142913118/bc03dfb9-871f-41a9-b228-313664a26b47)


  ### uusi virtuaalikone

  Tein uuden virtuaalikoneen valmiiksi loppuharjoitusta varten. 
  kloonasin koneen loppuvaiheen tehtäviin muistitikulle. 
  latasin debian-live-12.5.0-amd64-xfce -kuvakkeen [Debianin suvustolta](https://cdimage.debian.org/cdimage/release/current-live/amd64/iso-hybrid/)

  asensin koneen Terokarvinen.comin [ohjein](https://terokarvinen.com/2021/install-debian-on-virtualbox/) ohjein. 
  
  
  valmis 5.3.2024 21:45  käytetty aika 2h + päivän 6h 
  Tero karvisen Linux-kurssin tunnit 5.3.2024  

  ### C) vanha loppuharjoitus 

   lähdin ratkomaan vuoden 2023 [harjoitusta](https://terokarvinen.com/2023/linux-palvelimet-2023-arvioitava-laboratorioharjoitus/)  
   
   9.3.2024 17:35

  Otin käyttöön kloonikoneen (maalisuora clone) muistitikulta  
  $ sudo apt-get update  
  $ sudo apt-get upgrade  
  $ sudo install micro nano apache2 ssh  
   asensin micro tekstieditorin, nano tekstieditorin, apace 2 webbipalvelimen ja ssh -ohjelmiston.   
   **"Tallenna raportti nimellä report/index.md . Laita samaan kansioon jpg tai png -muotoiset kuvat."**
  $ mkdir report  
  $ cd micro index.md  
  **kirjoitin raportin tänne  **
  tarkastin, että tehtävässä piti testata tehdyt toimenpiteet muuten niitä ei ole todettu tehdyiksi.   
  loppuraporttia ei saa julkaista kesken harjoituksen.   
  #### C) raportin suojaus Linux-oikeuksilla niin että muut eivät pääse katsomaan:  
  
  $ /report$ ls -l index.md   
  -rw-r--r-- 1 maijav maijav 67  9. 3. 18:00 index.md  
  tallensin aluksi sinne kohdan a tiedot, läksyraportin linkin hain virtuaalikoneen netin kautta.   
  Suojasin index.md -tekstitiedoston seuravilla komennoilla  
  $ chmod o-r  
  $ chmod g-r  
  tarkastin setin   
  $ ls -l index.md  
  oikeudet oikein ja pääsin vielä käyttäjänä tekstitiedostoon sisälle.  
  apuja sivustolta https://cets.seas.upenn.edu/answers/chmod.html   

  ![10  suojattu raportti](https://github.com/VaMaija/Linux2024/assets/142913118/2d966f63-7831-4231-a36c-7739d4b28a6f)  

  #### D) Hey Tee kaikkien käyttäjien käyttöön komento 'hey'

  ![11  hey komento](https://github.com/VaMaija/Linux2024/assets/142913118/560d6fa6-0c1c-48cf-aa6e-bbc33d4142d4)  
  ![12 komento](https://github.com/VaMaija/Linux2024/assets/142913118/ea35d35c-40f4-42c3-ac5b-6e62b1c6366f)  
  ![14  komento bash hey testattu](https://github.com/VaMaija/Linux2024/assets/142913118/d3f15618-f12f-478c-a15b-260bc0d438ff)

  #### E) Asenna Micro-editori ja sille jokin plugin
  ![E micro](https://github.com/VaMaija/Linux2024/assets/142913118/5cb53e53-09d3-4545-aea1-2c99807e974c)
  ![E plugin](https://github.com/VaMaija/Linux2024/assets/142913118/66a67ca8-98ca-4c43-964c-9e9dd9edebbb)  
  En saanut gothamia toimimaan, ilmeisesti värien olisi pitänyt muuttua. 

  #### F) Erkki Esimerkin seikkailut

  ![15  adduser erkki](https://github.com/VaMaija/Linux2024/assets/142913118/2d66a600-7fcb-4048-84aa-606fd1172704)  
  ![16  erkki esimerkki sisällä](https://github.com/VaMaija/Linux2024/assets/142913118/e6847599-7549-4807-bcbd-4b9a52ca5659) 
  ![17  Ekillä ei sudo-oikeuksia](https://github.com/VaMaija/Linux2024/assets/142913118/2470df60-71bf-40f1-ac88-8c6e7fe8fec5)
  ![18 erkki käyttäjän verkkosivu ei toimi](https://github.com/VaMaija/Linux2024/assets/142913118/73272724-0ed6-427a-9727-1318a2b5c629)

  Tämän tehtävän kanssa taistelin tuntikausia, enkä saanut sitä kuitenkaan toimimaan.  Nukkumaan 23:40  6h 
  10.3.2024 klo 18:00 raportin kirjoittaminen tähän asti.   
  
  #### G) Asenna ssh- palvelin 
   ![25  ssh](https://github.com/VaMaija/Linux2024/assets/142913118/442aa6a3-04cc-405d-9b9a-5c7e81023185)  
   loin uuden käyttäjän:  
   ![g uusi käyttäjä](https://github.com/VaMaija/Linux2024/assets/142913118/0b81ea23-ef69-499e-afc4-d12267370d5e)  
   Localhost on sekaisin Erkki Esimerkin vuoksi: Poistin erkki.example.com.conf laitoin taiain alkuperäisen 000-default.conf ja käynnistin Apache2 uudelleen. Localhost vastaa ip-osoitteesta 127.0.0.1 ja localhost.

   Kirjaduin sisään localhostiin uudella käyttäjällä:  
   $ ssh testimuija@localhost
   $ ssh-keygen luo julkisen ja yksityisen avaimen, ei salasanoja tai lauseita     
   ![26  ssc keygen](https://github.com/VaMaija/Linux2024/assets/142913118/dc52ab90-ee7c-4987-a6e9-e8ee0a9a9d28)

   $ ssh-copy-id testimuija@localhost 
   kopioi avaimet localhostin muistiin. Avain on lisätty localhostiin testimuijan avaimeksi, mutta edelleen vaaditaan salasanaa. Ssh ei toimi. 

   En osaaa vaitaa ssh kuuntelemaan toista porttia. 
   Ei tehty  

   #### H) asenna Django

   $ sudo apt-get install virtualenv
   $ export EDITOR=micro
   $ echo "Testihommat loppuillasta"| sudo tee /var/www/html/index.html 
  ![30 virtualenv](https://github.com/VaMaija/Linux2024/assets/142913118/90cdcbaa-d193-466d-90d7-5c80eb1f0fe7)  

   toimii localhostissa. 
   en saanut toimimaan sitten staattisessa testisivussa:  
  ![31  staattinen testisivu](https://github.com/VaMaija/Linux2024/assets/142913118/0b3a5f77-8e40-4185-8c7d-924c818bd35d)
  ![32  maijaoy static conf](https://github.com/VaMaija/Linux2024/assets/142913118/94a21199-cff0-4874-a5da-5b1671e14f83)  
  ![33  epäonnistuminen](https://github.com/VaMaija/Linux2024/assets/142913118/d9fa51bd-e92c-4008-972f-d5ba2ad80ad9)

  harjoituksen päätin tähän, sillä aamulla jälleen työpäivä. Tämä ei onnistunut aikaisemmassakaan harjoituksessa, joten samoilla ohjeilla tehtynä en saanut sitä edelleenkään onnistumaan. 
  
  klo 21:10 

  

  
  

  Lähteet:  
  a) https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/?fromSearch=bash  
  b) Tero Karvisen tunnit 5.3.2024 
  C) TeroKarvinen.com https://terokarvinen.com/2023/linux-palvelimet-2023-arvioitava-laboratorioharjoitus/?fromSearch=2023 luettu 9.3.2024 10.3.2024   
      https://terokarvinen.com/2022/deploy-django/  10.3.2024
      https://terokarvinen.com/ssh_public_key_authentication.html  10.3.2024
      
      
      
    
