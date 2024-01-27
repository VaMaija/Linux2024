## X) komennot tiivistettynä: 

$ -merkkiä ei tarvitse itse kirjoittaa, se on komentorivissä automaattisesti:

  **$ sudo apt-get update**  päivittää ohjelmat ajantasalle, kannattaa käyttää aina aluksi.  
  **$ pwd** näyttää nykyisen hakemiston.  
  **$ ls** näyttää kansion sisällön.  
  **$ cd /** siirtyy omaan kotihakemistoosi.   
  **$ cd /kansionnimi/** siirtää sinut haluttuun kansioon.   
  **$ cd ..** siirtää sinut kansiopolussa yhden kansion taaksepäin.  
  **$ less koira.txt** näyttää koira.txt tekstin (välilyönnillä eteenpäin; b edellinen sivu, / etsii tekstistä ja q poistuu tekstiistä)

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
    ctrl + R etsii historiakomennoista. 

  
  
  
  
  
  **$ apt-cache search** etsitämäsana etsii ohjelmasta kyseisen hakusanan mukaan.  

Lähteet: 
X)

  Linux.f/Wiki https://www.linux.fi/wiki/Luokka:Komentorivin_perusty%C3%B6kalut luettu 27.1.2024  
  Karvinen, T  https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited luettu 27.1.2024 tekijä Tero Karvinen.  
  Mäntysalo, J https://homepages.tuni.fi/jori.mantysalo/jutut/unix/grep.html luettu 27.1.2024 Tekijä Jori Mäntysalo  



