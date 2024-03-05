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



  valmis 20:16  
  Tero karvisen Linux-kurssin tunnit 5.3.2024  




  Lähteet:  
  a) https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/?fromSearch=bash  
  b) Tero Karvisen tunnit 5.3.2024 
  C)
