#### Tietokone, jossa testit a ja b ajettiin

- CPU: 12th Gen Intel® Core™ i5-12400F
- GPU: AMD Radeon™ RX 6600 XT 8GB
- Emolevy: Asus Prime B760M-K D4 BIOS Ver. 1658
- Muisti: 32GB DDR4-3600
- SSD: WD Black SN770 1TB (Windows 11), WD Blue SN580 1TB (Debian 12)
- Virtualisointi: VirtualBox Debian 12 käyttöjärjestelmässä

#### Virtuaalikone, jossa ajettiin osa osion C-testeistä

- 2 CPU, 4 GB muistia, 30 GB HDD, Debian 12

### a) Kirjoita ja aja "Hei maailma" kolmella kielellä.

Kirjaudun sisään Debian-tietokoneeseeni ja avasin tietokoneesta 'Terminal'-ohjelman. Tein 'Hei maailma' -ohjelmat pythonilla, bashilla ja C-kielellä. Loin kaikki tiedostot 'Documents' -kansioon Micro-editorilla, ja käytin apuna Teron lähdettä 'Hello World Python3, Bash, C, C++, Go, Lua, Ruby, Java – Programming Languages on Ubuntu 18.04.' Kaikki ohjelmat löytyivät ennestään Debianista joten asennuksia ei tarvinnut tehdä tällä kertaa. 

Kuvakaappaukssessa näkyvissä tiedostojen luonnit sekä millä komennolla tiedostot ajettiin.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h7/h7-a1.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h7/h7-a1.png)

### b) Laita Linuxiin uusi komento niin, että kaikki käyttäjät voivat ajaa sitä.

Halusin tehdä komennon jolla näkee tietokoneen ip-osoitteen ja hostnamen eli tietokoneen nimen. Tein tiedoston kansioon /home/sami/ käyttäen micro-editoria ja oikeudet määritin tiedostoon komennolla ```chmod a+x iphost```. Apuna käytin Teron ohjetta 'Shell Scripting'. Kuvakaappauksessa näkyvissä tiedoston sisältö, sekä ajetun komennon tulos. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h7/h7-b1.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h7/h7-b1.png)

### c) Ratkaise vanha arvioitava laboratorioharjoitus soveltuvin osin.

Valitsin viime kevään laboratorioharjoituksen 'Final Lab for Linux Palvelimet 2024 Spring' (https://terokarvinen.com/2024/arvioitava-laboratorioharjoitus-2024-linux-palvelimet/ ) ja ratkaisin sieltä osiot c, d, e ja g soveltuvin osin. Valitettavasti muiden osioiden suorittamiseen ei jäänyt tällä kertaa aikaa.

#### c) Ei kolmea sekoseiskaa

Tein tiedoston eisekoseiskaa.md micro-editorilla kansioon /home/sami/Documents. Tarkistin tiedoston luonnin jälkeen oikeudet ja oletuksena tiedostoa pääsi lukemaan myös muut käyttäjät. Komennolla ```chmod 700 eisekoseiskaa.md``` sain muutettua tiedoston oikeudet niin että pääsin vain itse lukemaan ja muokkaaman tiedostoa. Oikeuksia kertasin Pluralsightin artikkelista 'How to change directory permissions in Linux with chmod'

Kuvakaappauksessa näkyvissä tiedoston oikeudet ennen ja jälkeen. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h7/h7-c1.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h7/h7-c1.png)

#### d) 'howdy'

Tein komennon joka näyttää päivämäärän ja ajan sekä tietokoneen ip-osoitteen. Tein tiedoston howdy micro-editorilla. Oikeudet määritin tiedostoon kommennolla ```chmod a+x howdy```, joka salliin myös muiden käyttäjien suorittaa komento. Kuvakaappauksessa näkyvissä komennon tulos sekä tiedoston oikeudet. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h7/h7-c2.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h7/h7-c2.png)

#### e) Etusivu uusiksi

Tämän tehtävän tein VirtualBoxin virtuaalikoneella (Debian 12), jonka olin asentanut jo aiempia tehtäviä varten. Tehtävässä pyydettiin tekemään yritykselle AI Kakone kotisivu, joka pitäisi näkyä koneen IP-osoitteella. 

Otin koneeseen SSH-yhteyden toisesta tietokoneesta. Virtuaalikoneella oli jo ennestään asennettuna apachen web-palvelin, joten lähdin katsomaan kansion '/etc/apache2/sites-available' sisältöä mitä sivustoja koneella oli. Listaus paljasti että koneella oli aiemmissa viikkotehtävissä tehdyt Django (sammyc0de.conf) sekä hattu-sivusto. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h7/h7-c3.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h7/h7-c3.png)

Komennolla ```sudoedit aikakone.conf``` tein uuden virtual hostin config-tiedoston sivua varten, jonne määritin sivuston nimen ja polun. En määrittänyt sivustolle mitään päätettä koska tehtävässä pyydettiin että sivu pitäisi näkyä ip-osoitteella. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h7/h7-c4.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h7/h7-c4.png)

Seuraavaksi laitoin uuden sivun päälle ja käynnistin apachen web-palvelimen uudelleen. Tämän jälkeen siirryin kotihakemistoon ja aiemmin luotuun publicsites kansioon jonne tein uuden 'aikakone' kansion. Aikakone kansioon tein index.html tiedoston komennolla ```nano index.html```, jonne lisäsin lyhyen pätkän html-koodia. Hyödynsin Teron sivulla olevaa html-esimerkkiä (https://terokarvinen.com/2012/short-html5-page/)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h7/h7-c5.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h7/h7-c5.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h7/h7-c6.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h7/h7-c6.png)

Seuraavaksi muistin etten ollut vielä ottanut pois päältä vanhoja sivuja, joten palasin takaisin kansioon '/etc/apache2/sites-available'. Otin molemmat aiemmin käytössä olleet sivut pois päältä jonka jälkeen käynnistin Apachen uudelleen. Hattu-sivun kohdalla sain ilmoituksen että sivu oli otettu pois päältä jo aiemmin.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h7/h7-c7.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h7/h7-c7.png)

Seuraavaksi testailin sivun näkyvyyttä toisella koneella, virtuaalikoneen ip-osoitteella ja sivu näkyi oikein. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h7/h7-c8.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h7/h7-c8.png)

Lopuksi vielä tarkistin että oikeudet kunnossa ja että sivua pääsee muokkaamaan ilman sudoa.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h7/h7-c9.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h7/h7-c9.png)

#### g) Salattua hallintaa

Jatkoin samalla virtuaalikoneella ja tein sinne uuden käyttäjän "Sami Hiltunen test", login nimellä 'samite01'. SSH-palvelin koneeessa oli jo ennestään asennettuna, joten ohitin sen asennuksen. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h7/h7-c10.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h7/h7-c10.png)

Seuraavaksi avasin terminal-ohjelman tietokoneesta jossa ajoin virtualiboxia. Tein uuden avaimen komennolla ```ssh-keygen```. Olin tehnyt vastaavan avaimen jo aiemmin, josta komento herjasi. Päätin ylikirjoittaa aiemmin tehdyn avaimen, enkä määrittänyt passphrasea. Lopuksi vielä kopioisin avaimen kuvassa näkyvällä komennolla virtuaalikoneelle.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h7/h7-c11.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h7/h7-c11.png)

Seuraavaksi kokeilin ottaa SSH-yhteyden koneeseen uudella samite01 käyttäjällä, mutta yhteys kysyikin vielä salasanaa. Tajusin tässä kohtaa että avain pitää kopioida sillä käyttäjällä, joka tulee käyttämään ssh-yhteyttä. Kopioin uudestaan SSH avaimen, tällä kertaa komennolla ```ssh-copy-id samite01@192.168.1.100```. Nyt SSH-kirjautuminen onnistui ilman salasanaa käyttäjällä 'samite01'.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h7/h7-c12.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h7/h7-c12.png)

Käytin tehtävässä apuan DigitalOceanin ohjetta https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-debian-11

### Lähteet

- Karvinen, Tero. Linux Palvelimet 2024 alkusyksy. https://terokarvinen.com/linux-palvelimet/#laksyt-
- Karvinen 2018. Hello World Python3, Bash, C, C++, Go, Lua, Ruby, Java – Programming Languages on Ubuntu 18.04. https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/
- Karvinen 2007. Shell Scripting. https://terokarvinen.com/2007/12/04/shell-scripting-4
- Karvinen 2024. Final Lab for Linux Palvelimet 2024 Spring https://terokarvinen.com/2024/arvioitava-laboratorioharjoitus-2024-linux-palvelimet/
- Pluralsight 2023. How to change directory permissions in Linux | Pluralsight | Pluralsight. https://www.pluralsight.com/blog/it-ops/linux-file-permissions
- Karvinen 2012. Short HTML5 page. https://terokarvinen.com/2012/short-html5-page/
- DigitalOcean. How to Set Up SSH Keys on Debian 11. https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-debian-11
