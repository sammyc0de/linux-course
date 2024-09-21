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

![image](https://github.com/user-attachments/assets/fde5c835-127b-444f-a072-94f95e6712d9)

Seuraavaksi määritetään virtuaalikone. Virtuaalikone kannattaa vuokrata yleensä mahdollisimman läheltä, jotta yhteydet toimii mahdollisimman nopeasti. 

Päätin vuokrata tilan virtuaalikoneelle Amsterdamin AMS3 palvelimelta. Käyttöjärjestelmäksi valitsin tutun Debian ja uusimman 12 version, jota olen käyttänyt aiemminkin. Paketiksi valitsin edullisemman 4 taalan vaihtoehdon. 512 mb muistia, 1 cpu, 10 gb levytilaa ja 500 gb siirtokapasiteettia riittää vallan hyvin tämän tyyppisiin harjoitukseen. Konetta voi myös myöhemmin päivittää mikäli tulee tarvetta. 

![image](https://github.com/user-attachments/assets/0ce3ed56-17b6-4b1d-9bc0-ab790575253a)

![image](https://github.com/user-attachments/assets/ebf3779a-8ba5-4e46-91a5-fe63cb5a04a2)

![image](https://github.com/user-attachments/assets/ffe90280-b813-436c-94dd-bdeb368951e2)

Lopuksi piti vielä määrittää root-tunnuksen salasana ja hostname. Tämän jälkeen klikkasin 'Create Droplet', jolloin virtuaalikoneen luonti alkoi. Palvelu loi virtuaalikoneen alle minuutissa.  

![image](https://github.com/user-attachments/assets/cfb5ebfa-0842-4401-b05c-d04efadfa484)

Kun virtuaalikone oli luotu, dashboardissa näkyi luomani virtuaalikone ja sen ip-osoite. 

![image](https://github.com/user-attachments/assets/ce6f27ad-773b-4c8a-a83c-770e7e992ed2)

### b) Tee alkutoimet omalla virtuaalipalvelimellasi: tulimuuri päälle, root-tunnus kiinni, ohjelmien päivitys.

#### Tietokone, jolla otettiin etäyhteys DigitalOceanin virtuaalikoneeseen:

- CPU: 12th Gen Intel® Core™ i5-12400F
- GPU: AMD Radeon™ RX 6600 XT 8GB
- Emolevy: Asus Prime B760M-K D4 BIOS Ver. 1658
- Muisti: 32GB DDR4-3600
- SSD: WD Black SN770 1TB (Windows 11), WD Blue SN580 1TB (Debian 12)


Muodostin SSH-etäyhteyden Debian käyttöjärjestelmän terminaalilla DigitalOceanin virtuaalikoneeseen, jonka olin luonut aiemmassa vaiheessa. SSH-yhteyden muodostin virtuaalikoneen julkisella ip-osoitteella. 

![image](https://github.com/user-attachments/assets/ecb381c1-5f75-4458-8e2c-9250e946f5ef)

Root-tunnus kannattaa poistaa käytöstä ja korvata se omalla tunnuksella. Siispä tein ensiksi oman tunnuksen virtuaalikoneeseen komennolla ```sudo adduser sami``` kuvassa näkyvillä määrityksillä. Tämän jälkeen lisäsin uuden käyttäjän sudoers-ryhmään komennolla  ```sudo adduser sami sudo```. Näin saatiin käyttäjälle 'sami' pääkäyttäjän oikeudet.

![image](https://github.com/user-attachments/assets/fff956ec-5ad8-4a67-b110-a56924ad6089)

Nyt pitäisi onnistua SSH etäyhteyden muodostus uudella käyttäjällä, joten kirjauden ulos root-käyttäjänä, komennolla ```exit```. SSH toimi hienosti käyttäjällä 'sami', joten seuraavaksi päätin lukita root-tunnuksen. Root-tunnuksen lukitus onnistui kommennolla  ``` sudo usermod --lock root```

![image](https://github.com/user-attachments/assets/2946a86f-0888-4f54-aaeb-e8278d6289e0)

Palomuuri on hyvä laittaa päälle, mutta ennen sitä ajoin vielä päivitykset Debianiin. 

![image](https://github.com/user-attachments/assets/9f2ae2f0-f0e5-4f02-8511-b3b13def0a1e)

Palomuurin asennus onnistui komennolla ```sudo apt-get install ufw```. Seuraavaksi avasin portin SSH:lle eli TCP-portti 22 auki komennolla ```sudo ufw allow 22/tcp ``` jonka jälkeen muuri päälle käskyllä  ```sudo ufw enable ```. Nyt on virtuaalikone suojattu, ainoastaan SSH:llä pääsee sisälle. Myöhemmin täytyy avata vielä http-portti 80 web-palvelimen liikenteelle.

![image](https://github.com/user-attachments/assets/d7ff8609-d6c8-4e27-8f7d-270823edf7b5)

Päivitin vielä asennutetut paketit komennolla ```sudo apt-get dist-upgrade``` jonka jälkeen uudelleen käynnistin virtuaalikoneen ```sudo systemctl reboot```-komennolla.

![image](https://github.com/user-attachments/assets/f721a604-07e4-4bc4-a3a0-f6d2a28a0e12)

Uudelleen käynnistyksen jälkeen kirjauduin uudestaan SSH:llä palvelimelle ja estin root-tunnukselta SSH-kirjautumisen komennolla ```sudoedit /etc/ssh/sshd_config```. Config-tiedostossa on kohta 'PermitRootLogin' jonka perään vaihdoin arvoksi 'no', aiemman 'yes'-arvon sijaan. Lopuksi tallensin tiedoston ja käynnistin vielä ssh servicen uudelleen komennolla ```sudo service ssh restart```.

![image](https://github.com/user-attachments/assets/5eb64cfe-d39e-4562-8257-26419cce1c49)

![image](https://github.com/user-attachments/assets/fd14c76b-c287-4bb4-90f2-31fb68bdb434)


### c) Asenna weppipalvelin omalle virtuaalipalvelimellesi. 

Kirjauduin virtuaalipalvelimelle SSH-yhdeydellä omasta tietokoneesta. Päivitykset olin ajanut edeltävänä päivänä, joten käynnistin suoraan apachen asennuksen kommennolla ```sudo apt-get -y install apache2```

![image](https://github.com/user-attachments/assets/15aeaba2-74d7-417b-94e2-abbc56e78285)

![image](https://github.com/user-attachments/assets/cd355a19-72ed-49be-95d4-6208cf198a66)

Apachen asennuksen jälkeen testasin että web-palvelin toimii ja näyttää oletussivun komennolla ```curl localhost```.

![image](https://github.com/user-attachments/assets/e540996e-0908-4cd0-8f0b-7f2a0644b7d5)

Seuraavaksi testasin sivun näkymistä julkisesti ja ennen sitä avoin http-portin palomuurin.

![image](https://github.com/user-attachments/assets/ec62aa3e-8575-4e6d-8fe7-f50454c5fdd1)

Laitoin virtuaalipalvelimen julkisen ip-osoitteen tietokoneeni Firefox-selaimeen ja Apachen oletussivu avautui hienosti.

![image](https://github.com/user-attachments/assets/8cadc34f-c9d0-42db-b1ce-370d12d6ff82)

Yhteydet toimii web-palvelimelle, joten seuraavaksi lähdin korvaamaan oletussivua, omalla sivulla. Ensiksi kokeilin nopeaa tapaa korvaten oletussivu kommennolla ```echo Maailma kuulee! |sudo tee /var/www/html/index.html```. Oletussivu päivitetty onnistuneesti ja Firefox-näytti päivityn sivun.

![image](https://github.com/user-attachments/assets/1949d1a6-303e-43e4-b595-2954eb100c88)

Sivu avautui hienosti myös kännykällä.

![image](https://github.com/user-attachments/assets/1f630add-bb15-4f1b-a100-47918afbae4a)

Lopuksi lisäsin hieman html-koodia oletussivulle komennolla ```sudoedit /var/www/html/index.html``` ja testailin sen näkyvyyttä tietokoneen Firefox-selaimella.

![image](https://github.com/user-attachments/assets/8a6e89dc-0040-424e-ae59-cace48366145)


### Lähteet

- Karvinen, Tero. Linux Palvelimet 2024 alkusyksy. https://terokarvinen.com/linux-palvelimet/#laksyt-
- Lehto. Teoriasta käytäntöön pilvipalvelimen avulla (h4). https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/
- Karvinen 2012. First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS. https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/
- Karvinen 2018. Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address. https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/



