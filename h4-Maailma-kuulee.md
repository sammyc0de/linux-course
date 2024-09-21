# h4 Maailma kuulee


### x) Tiivistelmät 

#### Susanna Lehto 2022: Teoriasta käytäntöön pilvipalvelimen avulla 


- a) Oma julkinen palvelin vuokrataan pilvestä ja palvelinta varten voi vuokrata domain nimen, joka kohdistetaan palvelimelle. Githubin Education paketin avulla on mahdollista saada ilmaiseksi palvelin tilaa ja domain nimi.
- a) DigitalOceaniin rekisteröidään ensiksi jonka jälkeen määritetään maksutapa ja ladataan rahaa tilille palveluiden käyttöä varten. Virtuaalipalvelin hankitaan 'Droplets' -kautta jonka jälkeen määritetään palvelin
- a) Namecheapissa vuokrataan ensiksi domain nimi jonka jälkeen määritetään DNS-tietueisin virtuaalipalvelimen ip-osoite
- d) Palomuuri asennetaan Linuxiin kommennolla 'sudo apt-get install ufw' ja avattavat portit määritetään kommennolla 'sudo ufw allow [porttinro]. Muuri kytketään päälle kommennolla ' sudo ufw enable'
- e) Kotisivuja varten asennetaan apachen web-palvelin. Web-palvelinta varten avattava tcp-portti 80 palomuuriin. Web-palvelimen toimivuutta voidaan testata domain nimellä, joka on määritetty virtuaalipalvelimeen. Asentamalla userdir-moduuli, voidaan ottaa käyttöön käyttäjäkohtaiset kotisivut.
- f) Palvelimelle saadaan asennettua viimeisimmät päivitykset ja tietoturvapäivityset komennoilla: sudo apt-get update, sudo apt-get upgrade ja  sudo apt-get dist-upgrade

#### Karvinen 2012: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS

- Karvisen sivulla käydään läpi esimerkkinä Ubuntu-palvelimen hankkimisesta DigitalOceanilta. DNS-nimen hankkimisessa käytetään esimerkkinä NameCheap -palvelua. Palvelu on mahdollista hankkia hyödyntämällä ilmaista GitHub Education student pack:ia, joka on ilmainen opiskelijoille.
- Sivulla käydään yksityiskohtaisesti läpi seuraavat vaiheet: kirjautuminen virtuaalikoneesen ssh-yhdeyden avulla, palomuurin asetus, käyttäjän luonti sekä käyttäjän lisäys pääkäyttäjäksi, root-tunnuksen ottaminen poista käytöstä sekä ohjelmien päivitys
- Lopuksi muistetetaan portin 80 avaamisesta web-palvelimelle, sekä käydään läpi julkisen DNS-nimen hankkimisesta NameCheap-palvelusta, sekä sen määrittäminen omalle virtuaalipalvelimelle

### a) Vuokraa oma virtuaalipalvelin haluamaltasi palveluntarjoajalta. 

Aiemmalla oppitunnilla olin tehnyt tunnukset DigitalOceaniin ja samalla olin myös ladannut DigitalOcean tilille rahaa virtuaalikonetta varten. Tätä raporttia varten poistin aiemmin tunnilla tekemäni virtuaalikoneen ja aloitin alusta tekemällä uuden virtuaalikoneen. 

Virtuaalikoneen saa luotua DigitalOcean:ssa valitsemalla vasemmasta valikosta 'Droplets' ja sen jälkeen 'Create Droplet'. Vaihtoehtoinen tapa on käyttää ylhäällä näkyvää vihreää 'Create' -painiketta.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(2).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(2).png)

Seuraavaksi määritetään virtuaalikone. Virtuaalikone kannattaa vuokrata yleensä mahdollisimman läheltä, jotta yhteydet toimii mahdollisimman nopeasti. 

Päätin vuokrata tilan virtuaalikoneelle Amsterdamin AMS3 palvelimelta. Käyttöjärjestelmäksi valitsin tutun Debian ja uusimman 12 version, jota olen käyttänyt aiemminkin. Paketiksi valitsin edullisemman 4 taalan vaihtoehdon. 512 mb muistia, 1 cpu, 10 gb levytilaa ja 500 gb siirtokapasiteettia riittää vallan hyvin tämän tyyppisiin harjoitukseen. Konetta voi myös myöhemmin päivittää mikäli tulee tarvetta. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(3).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(3).png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(4).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(4).png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(5).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(5).png)

Lopuksi piti vielä määrittää root-tunnuksen salasana ja hostname. Tämän jälkeen klikkasin 'Create Droplet', jolloin virtuaalikoneen luonti alkoi. Palvelu loi virtuaalikoneen alle minuutissa.  

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(6).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(6).png)

Kun virtuaalikone oli luotu, dashboardissa näkyi luomani virtuaalikone ja sen ip-osoite. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(7).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(7).png)

### b) Tee alkutoimet omalla virtuaalipalvelimellasi: tulimuuri päälle, root-tunnus kiinni, ohjelmien päivitys.

#### Tietokone, jolla otettiin etäyhteys DigitalOceanin virtuaalikoneeseen:

- CPU: 12th Gen Intel® Core™ i5-12400F
- GPU: AMD Radeon™ RX 6600 XT 8GB
- Emolevy: Asus Prime B760M-K D4 BIOS Ver. 1658
- Muisti: 32GB DDR4-3600
- SSD: WD Black SN770 1TB (Windows 11), WD Blue SN580 1TB (Debian 12)


Muodostin SSH-etäyhteyden Debian käyttöjärjestelmän terminaalilla DigitalOceanin virtuaalikoneeseen, jonka olin luonut aiemmassa vaiheessa. SSH-yhteyden muodostin virtuaalikoneen julkisella ip-osoitteella. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(8).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(8).png)

Root-tunnus kannattaa poistaa käytöstä ja korvata se omalla tunnuksella. Siispä tein ensiksi oman tunnuksen virtuaalikoneeseen komennolla ```sudo adduser sami``` kuvassa näkyvillä määrityksillä. Tämän jälkeen lisäsin uuden käyttäjän sudoers-ryhmään komennolla  ```sudo adduser sami sudo```. Näin saatiin käyttäjälle 'sami' pääkäyttäjän oikeudet.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(9).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(9).png)

Nyt pitäisi onnistua SSH etäyhteyden muodostus uudella käyttäjällä, joten kirjauden ulos root-käyttäjänä, komennolla ```exit```. SSH toimi hienosti käyttäjällä 'sami', joten seuraavaksi päätin lukita root-tunnuksen. Root-tunnuksen lukitus onnistui kommennolla  ``` sudo usermod --lock root```

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(10).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(10).png)

Palomuuri on hyvä laittaa päälle, mutta ennen sitä ajoin vielä päivitykset Debianiin. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(11).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(11).png)

Palomuurin asennus onnistui komennolla ```sudo apt-get install ufw```. Seuraavaksi avasin portin SSH:lle eli TCP-portti 22 auki komennolla ```sudo ufw allow 22/tcp ``` jonka jälkeen muuri päälle käskyllä  ```sudo ufw enable ```. Nyt on virtuaalikone suojattu, ainoastaan SSH:llä pääsee sisälle. Myöhemmin täytyy avata vielä http-portti 80 web-palvelimen liikenteelle.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(12).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(12).png)

Päivitin vielä asennutetut paketit komennolla ```sudo apt-get dist-upgrade``` jonka jälkeen uudelleen käynnistin virtuaalikoneen ```sudo systemctl reboot```-komennolla.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(13).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(13).png)

Uudelleen käynnistyksen jälkeen kirjauduin uudestaan SSH:llä palvelimelle ja estin root-tunnukselta SSH-kirjautumisen komennolla ```sudoedit /etc/ssh/sshd_config```. Config-tiedostossa on kohta 'PermitRootLogin' jonka perään vaihdoin arvoksi 'no', aiemman 'yes'-arvon sijaan. Lopuksi tallensin tiedoston ja käynnistin vielä ssh servicen uudelleen komennolla ```sudo service ssh restart```.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(14).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(14).png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(15).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(15).png)


### c) Asenna weppipalvelin omalle virtuaalipalvelimellesi. 

Kirjauduin virtuaalipalvelimelle SSH-yhdeydellä omasta tietokoneesta. Päivitykset olin ajanut edeltävänä päivänä, joten käynnistin suoraan apachen asennuksen kommennolla ```sudo apt-get -y install apache2```

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(16).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(16).png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(17).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(17).png)

Apachen asennuksen jälkeen testasin että web-palvelin toimii ja näyttää oletussivun komennolla ```curl localhost```.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(18).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(18).png)

Seuraavaksi testasin sivun näkymistä julkisesti ja ennen sitä avoin http-portin palomuurin.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(19).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(19).png)

Laitoin virtuaalipalvelimen julkisen ip-osoitteen tietokoneeni Firefox-selaimeen ja Apachen oletussivu avautui hienosti.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(20).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(20).png)

Yhteydet toimii web-palvelimelle, joten seuraavaksi lähdin korvaamaan oletussivua, omalla sivulla. Ensiksi kokeilin nopeaa tapaa korvaten oletussivu kommennolla ```echo Maailma kuulee! |sudo tee /var/www/html/index.html```. Oletussivu päivitetty onnistuneesti ja Firefox-näytti päivityn sivun.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(21).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(21).png)

Sivu avautui hienosti myös kännykällä.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(22).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(22).png)

Lopuksi lisäsin hieman html-koodia oletussivulle komennolla ```sudoedit /var/www/html/index.html``` ja testailin sen näkyvyyttä tietokoneen Firefox-selaimella.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h4/h4%20%20(23).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h4/h4%20%20(23).png)


### Lähteet

- Karvinen, Tero. Linux Palvelimet 2024 alkusyksy. https://terokarvinen.com/linux-palvelimet/#laksyt-
- Lehto. Teoriasta käytäntöön pilvipalvelimen avulla (h4). https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/
- Karvinen 2012. First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS. https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/
- Karvinen 2018. Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address. https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/



