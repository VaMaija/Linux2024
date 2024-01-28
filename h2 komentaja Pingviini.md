## X) Komennot tiivistettynä: 

$ -merkkiä ei tarvitse itse kirjoittaa, se on komentorivissä automaattisesti:
    
  **$ pwd** näyttää nykyisen hakemiston.  
  **$ ls** näyttää kansion sisällön.  
  **$ cd /** siirtyy omaan kotihakemistoosi.   
  **$ cd /kansionnimi/** siirtää sinut haluttuun kansioon.   
  **$ cd ..** siirtää sinut kansiopolussa yhden kansion taaksepäin.  
  **$ less koira.txt** näyttää koira.txt tekstin (välilyönnillä eteenpäin; b edellinen sivu, / etsii tekstistä ja q poistuu tekstiistä)  
  **$ apt-cache search** etsitämäsana etsii ohjelmasta kyseisen hakusanan mukaan. 

  -kaikkien komentojen toiminnot voidaan lukea komentonäytöllä yksi näytöllinen kerrallaan |less  -päätteellä. 

### Tiedostojen käsittely

  Tekstieditorit: Nano ja pico avaavat tekstitiedoston **$ nano teksti.txt** tai **$ pico teksti.txt**  
  **$ mkdir UUSIKANSIO** luo uuden hakemistokansion.  
  **$ mv VANHANIMI UUSINIMI** siirtää kansion tai tiedoston sijaintia, tai jos sijaintia ei ole luotu nimeään kansion tai tiedoston uuden nimen mukaan.  Jos käytössä on jo UUSINIMI -niminen kansio, niin se ylikirjoitetaan erillistä lupaa kysymättä.  
  **$ mv UUSIJUTTU VANHAKANSIO/** Siirtää tiedoston annettuun kansioon.   
  **$ cp -r ALKUPERÄINEN KOPIO** Alkuperäinen kopioidaan sisältönsä kanssa. -r tarkoittaa recursivea eli käy läpi kaikki alihakemistojen tiedostot. /Mäntysalo, J   
  **$ rmdir** Tyhjäkansio poistaa tyhjän kansion nimeltä Tyhjäkansio.  
  **$ rm tämätiedosto** poistaa kyseisen tiedoston.  
  **$ rm -r tämäkansiojasensisältö** poistaa kansion ja sen sisällön.  

### SSH Etäkäyttö

  **$ ssh maija@serveri.com** avaa käyttäjän maija serverillä serveri.com. Voit toimia etäkoneen komentorivillä ja vastaus palautuu sinulle **W** kirjaimella näet kuka muu on etäyhteydellä ko koneella. 
  **remotecomputer$ exit** poistuu etäkäytöstä omalle koneelle.  
  **$ scp -r KANSIO maija@serveri.com:public-html/** kopioi KANSIOn omalta koneelta käyttäjän maija serveri.com etäkäyttökoneelle public_html/ -kansioon.  

### Apua!

  **$ man ls** näyttää ohjesivut.  
     **$ ls --help** lyhennetty apukomento 
     **$ wget -h** lyhennetty apukomento 

### Historia ja arvuuttaja 

  Käyttämällä kaksi kertaa tabulaattoria ja voit nähdä mitä voit kirjoittaa seuraavaksi. Tab myös auttaa tiedostojen nimien kirjoittamisessa ja nuolinäppäimillä voit valita listasta oikean.   
  **$ history** näyttää komennot joita on aiemmin käytetty komentorivillä ja   
    **ctrl + R** etsii historiakomennoista. 

### Paketin hallinta ja asennukset

  **$ sudo apt-get update**  päivittää ohjelmat ajantasalle, kannattaa käyttää aina aluksi.  
  apt-cache search 


## A) Asenna Micro -editori

![Micro tekstieditori](https://github.com/VaMaija/Linux2024/assets/142913118/acfc8ca8-482b-4e01-a922-df2c9d9fe24e)

## B) Asenna lshw ja selitä raudan speksit

![LSHW](https://github.com/VaMaija/Linux2024/assets/142913118/d9e3230a-4d1c-4b90-873e-7e6e947a4c58)
![hardware](https://github.com/VaMaija/Linux2024/assets/142913118/bc772702-2e5f-4ca4-bfd8-f16859205bab)

Selitykset: 
  - Järjestemä toimii VirtualBox alustalla, siinä on käynnistysmuistia 128 kilotavua.  
  - Keskusmuistia on 4 gigatavua
  - Prosessorina näyttää fyysisen koneen prosessorin tiedot.
  - /0/100 Bridge Intel 440FX - 82441 PMX pohjoissilta, toimen päämikropiiri (muistiohjain keskusmuistille) /Wikipedia  
      - /0/100/1 Bridge 82371SB Piix3 ISA eteläsilta, toinen mikropiiri, sillassa kiinnitettynä:  
          - /0/100/1/0 PnP = Plug & Play -laitteiden input reitti
          - /0/100/1/1 PnP = Plug & Play -laitteiden input reitti
          - /0/100/1.1 Scsi1 kovalevy
              - /0/100/1.1/0.0.0 Cd-rom levykeasema
                - /0/100/1.1/0.0.0/0 levy 
      - /0/100/2 GPU: SVGA II Adapter on virtuaalikoneelle asennettu sovitin /Linuxmint.com
      - /0/100/3 Ethernet controller > lähiverkon ajurit
      - /0/100/4 Sisääntuloportti 9 VirtuaaliBoxin hiiri
      - /0/100/5 card 0 multimedia äänikortti
      - /0/100/6 usb ajuri KeyLargo
          - /0/100/6/1 OCHI PCI isäntä, joka toimii usb2 tukena /host controller  
            - /0/100/6/1/1 sisääntuloportti 10 Virtaaliboxin Usb Tablet parantaa hiiren käytettävyyttä raudan ja virtuaalikoneen välillä. /ChatGPT
      - /0/100/7 Piix4 Acpi -silta.
      - /0/100/b bus Usb käyttöliittymä
          - /0/100/b/1 Usb 1
      - /0/100/d sataliittymä muistiin  
        - /0/100/d/0.0.0 liittymä sata-kaapelin kautta koneen virtuaalimuistiin
            - /0/100/d/0.0.0/1 virtuaalimuistin sisällä oleva 41 gigatavun muisti ja
            - /0/100/d/0.0.0/2 swap -muistin määrä 840 megatavua
  - /1 sisääntuloportti 0 näppäimistön ajurit ja käännösautomaatio.  
  - /2 sisääntuloportti 2 virtanäppäin  
  - /3 sisääntuloportti 3 video bus, kuvadatan siirto?
  - /4 sisääntuloportti 4 lepotila
  - /5 sisääntuloportti 5 hiiren ajurit  
  - /6 sisääntuloportti 8 tietokoneen kaiuttimen sisääntulo
  
  
## C) Asenna kolme eri ohjelmaa komentoriviltä ja käytä ohjelmia: 

 c1) $ sudo apt-get install gnome  
 graafinen käyttöliittymä (GUI) laaja ohjelmisto, asentui 10 min. 

![mahong](https://github.com/VaMaija/Linux2024/assets/142913118/b8588c52-84e3-4a60-af74-92b892931ce3)

c2) $ sudo apt-get install nano
tekstieditori  

![nano tekstieditori](https://github.com/VaMaija/Linux2024/assets/142913118/062f36a9-77f1-4ef7-9a1f-882e0a0f5a1f)

c3)    
  $ sudo apt-get install lynx  
  $ lynx yle.fi  

  ![lynx ohjelma](https://github.com/VaMaija/Linux2024/assets/142913118/e856f76b-a2aa-401f-a23d-083361296b4b)

  Lynx näyttää nettiselaimen tekstimuodossa. Behold YLE uutiset TekstiTV -muodossa:
![teksti tv](https://github.com/VaMaija/Linux2024/assets/142913118/408b5ccd-3a00-4e42-8479-e1ff79cef9a0)

Kaikki Kolme kerralla: 

![kolme kerralla](https://github.com/VaMaija/Linux2024/assets/142913118/5d18036d-ba58-424c-b67a-0cf0d8f956fb)


## D) FHS Kansiot selitettyinä: 

  /              On juurikansio, pohja kaikelle Linuxissa ei ole c- tai d- asemia kuten Windowsissa vaan kaikki on "/" kansion alla.   
  /home/         Kansio, joka sisältää kaikkien käyttäjien kotihakemistot. 
  /home/maijav/  Käyttäjän maijav koytihakemisto ja ainoa paikka, johon käyttäjä maijav voi tallentaa dataa pysyvästi. 
  /etc/          Kaikki järjestemän asetukset kirjattuna luettavassa muodossa. 
  /media/        hakemistokansio, johon ulkopuolinen tallennustila asennetaan automaattisesti käytettäväksi. 
  /var/log/      Hakemisto, joka sisältää erilaisia loktietoja. Se tallentaa järjestelmän eri osien tapahtumatietoja ja virheitä.
                




  


  
    








Lähteet: 
X)

  Linux.f/Wiki https://www.linux.fi/wiki/Luokka:Komentorivin_perusty%C3%B6kalut luettu 27.1.2024  
  Karvinen, T  https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited luettu 27.1.2024 tekijä Tero Karvinen.  
  Mäntysalo, J https://homepages.tuni.fi/jori.mantysalo/jutut/unix/grep.html luettu 27.1.2024 Tekijä Jori Mäntysalo  

B) 

  bridge 440FX https://en.wikipedia.org/wiki/Intel_440FX luettu 27.1.2024  
  bridge 82371SB https://en.wikipedia.org/wiki/PIIX luettu 27.1.2024  
  Linuxmint.com https://forums.linuxmint.com/viewtopic.php?t=308018 luettu 27.1.2024  
  host controller https://www.sciencedirect.com/topics/computer-science/host-controller luettu 27.1.2024  
  chatGPT https://chat.openai.com/c/b85eaa04-fb35-47b4-b203-1576a6dc96f1 kysytty 27.1.2024: "mitä virtuaaliboxin usb tablet tekee?" 

C) 

  käyttäjä HortTemppa GitHub https://github.com/HortTemppa/horttemppa.github.io/blob/main/h2.md idea Lynxiin 28.1.2024   

D) 

    Kapil Bhise https://medium.com/analytics-vidhya/linux-directories-explained-75c376173947 luettu 28.1.2024 

  

 



