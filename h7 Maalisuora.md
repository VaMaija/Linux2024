5.3.2024 19.20

###a) Kolmella kielellä 
 Python: 
$ micro ekakieli.py
print("hei maailma!")
$ python3 ekakieli.py

Bash: 
$ micro tokakieli.sh
echo ”hei maailma!”
$ bash tokakeli.sh

Ruby: 
$ micro kolmaskieli.rb
print (”hei maailma\n”)
$ ruby kolmaskieli.rb

ohjeet [Tero Karviselta](https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/?fromSearch=bash)

###b) 
$ micro käyttäjätiedot
$ cat käyttäjätiedot
#!/usr/bin/bash
date  #komennon ajankohta
id #käyttäjätiedot
last # Viimeiset koneelle kirjautuneet käyttäjät

$ bash käyttäjätiedot
toimii. 
$ chmod ugo-rx käyttäjätiedot
$ ls -l
$ cp käyttäjätiedot /usr/local/bin
ei onnistunut, permission denied
$ sudo cp käyttäjätiedot /usr/local/bin


valmis 20:16
Tero karvisen Linux-kurssin tunnit 5.3.2024






