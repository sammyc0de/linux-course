 
#### Tietokone, jolla otettiin etäyhteys DigitalOceanin virtuaalikoneeseen:

- CPU: 12th Gen Intel® Core™ i5-12400F
- GPU: AMD Radeon™ RX 6600 XT 8GB
- Emolevy: Asus Prime B760M-K D4 BIOS Ver. 1658
- Muisti: 32GB DDR4-3600
- SSD: WD Black SN770 1TB (Windows 11), WD Blue SN580 1TB (Debian 12)


#### DigitalOceanin virtuaalikone pilvessä
- 1 CPU, 512 MB memory, 10 GB SSD Disk, 500 GB transfer limit


### a) Kotisivu. Tee vähintään kolmen erillisen weppisivun kotisivu ja kopioi se näkymään palvelimellesi. Jos sinulla on oikea palvelin Internetissä, kannattaa käyttää sitä. Käytä name based virtual hosting tekniikkaa. Sivujen muokkaamisen pitää onnistua ilman pääkäyttäjän oikeuksia, niiden kopioiminen pääkäyttäjänä testisivun paikalle ei käy. Kotisivujen ei tarvitse olla hienoja, mutta niiden tulee olla validia HTML:ää ja linkittää toisiinsa.

Kirjauduin DigitalOceanin virtuaalikoneeseen SSH:llä ja ajoin ensiksi päivitykset. Sen jälkeen kävin muistelemassa miltä näyttää koneen 'etc/apache2/sites-available' -kansiossa. Siellä tosiaan on vaan oletussivu määritettynä, joten seuraavaksi pitäisi pohtia miten saadaan näkyviin kolmen sivun web-sivusto. Muistin myös etten ollut asentanut vielä micro-editoria DigitalOceanin virtuaalikoneeseen, joten asensin sen myös tässä kohtaa. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a1.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a1.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a1-2.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a1-2.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a2.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a2.png)

Tehtävän annossa oli että sivut pitäisi kopioida palvelimelle. Seuraavaksi aloin luomaan kolmea erillistä web-sivua ensiksi omalle koneelle, index.html, contact.html ja about.html. Tein oman koneen Documents-kansion alle kansion Web, jonne aloin luomaan sivuja micro-editorilla. Käytin sivujen luonnissa apuna Tero Karvisen Short html5 page -pohjaa.

Tein ensiksi index.html sivun. Tallennuksen jälkeen siirsin sivun vielä Web-kansioon. Seuraavaksi otin tiedostoista kopiot, joilla tein contact.html ja about.html tiedostot. Tämän jälkeen muokkasin micro-editorilla hieman vielä sivuja.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a4.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a4.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a4-2.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a4-2.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a5.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a5.png)

Seuraavaksi palasin takaisin DigitalOceanin virtuaalikoneeseen ja loin "Public_html" -kansion kotihakemistoon. Tämän jälkeen aktivoisin kotihakemiston ajamalla komennon 'sudo a2enmod userdir', jonka jälkeen apachen uudelleen käynnistys.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a6v1.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a6v1.png)

Tämän jälkeen palasin takaisin omalle koneelle jossa oli web-sivujen tiedostot. Yritin useamman kerran ja eri tavoilla tiedostojen kopiointia scp-komennolla omalta koneelta DigitalOceanin virtuaalikoneeseen, kuitenkaan onnistumatta siinä.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a7.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a7.png)

Tässä kohtaa tuli mieleen kokeilla onko mahdollista tehdä edes tiedostoa paikallisesti 'home/sami/public_html' -kansioon. Avasin micron ja yritin tallentaa uutta tiedostoa joka herjasi että vaaditaan sudo-oikeuksia. Kysyin Copilotilta tässä kohtaa miten saada oikeudet kuntoon 'public_html' kansioon.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a8.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a8.png)

Ensimmäinen vaihtoehto oli että vaihtamalla kansion omistaja  ja määritämällä groupiksi www-data. Tämä kuulosti hyvältä ja komennon jälkeen sain onnistuneesti luotua myös testi-tiedoston (jonka poistin heti seuraavaksi).

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a9-2.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a9-2.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a10.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a10.png)

Seuraavaksi hyppäsin takaisin omalle konelle ja kokeilin uudestaan tiedostojen kopiointia. Nyt sain kaikki tiedostot kopioitua onnistuneesti kerralla! Sivutkin näytti toimivan.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a11.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a11.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a12.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a12.png)

Sivut eivät näkyneet suoraan vielä domaninin juuressa vaan ~sami -alle joten tein seuraavaksi virtual host config tiedoston domainille komennolla ```sudoedit /etc/apache2/sites-available/sammyc0de.com.conf```. Tiedoston luonnin jälkeen sivu vielä päälle sekä apachen uudelleen käynniystys.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a13.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a13.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a14.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a14.png)

Nyt sivut näkyivät suoraan myös osoitteella http://sammyc0de.com/. Muokkasin lopuksi hieman sivuja micro-editorilla.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a15.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a15.png)


### b) Alidomain. Tee kaksi uutta alidomainia, jotka osoittava omaan koneeseesi. Esimerkiksi palvelu on example.com -> linuxkurssi.example.com. Tee toinen alidomain A-tietueella ja toinen CNAME-tietueella. Alidomainit ovat tyypillisesti ilmaisia, kun sinulla on päädomain (example.com).

Minulla oli ennestään hankkittuna domain-nimi sammyc0de.com Namecheap-palvelusta. Määritin palvelun 'Advanced DNS' -asetuksissa itselleni kaksi uutta alidomainia. A-tietueella määritin alidomainin blog.sammyc0de.com ja CNAME-tietueella alidomanin linux.sammyc0de.com

Käytiin apuna Namecheapin ohjetta How to Create a Subdomain for my Domain (https://www.namecheap.com/support/knowledgebase/article.aspx/9776/2237/how-to-create-a-subdomain-for-my-domain/)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20b1%20-%20namecheap.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20b1%20-%20namecheap.png)

DigitalOceanin virtuaalikone oli valmiina auki edellisestä tehtävästä joten tein seuraavaksi kansiot alidomaineille kansioon /home/sami/public_html. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20b2.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20b2.png)

Tämän jälkeen muokkasin tiedostoa ```sudoedit /etc/apache2/sites-available/sammyc0de.com.conf``` ohjeen mukaan jonka löysin Apachen sivulta (https://httpd.apache.org/docs/2.4/vhosts/name-based.html). Määritin tiedostoon uudet alidomainit jonka jälkeen käynnistin apachen uudelleen. Seuraavaksi kävin lisäämässä vielä index.html -tiedostot alidomaineille. Alidomainit näkyivät oikein selaimessa.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20b3.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20b3.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20b4.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20b4.png)

### c) Pubkey. Automatisoi kirjautuminen julkisella SSH-avaimella.

Seurasin DigitalOceanin ohjetta 'How to Set Up SSH Keys on Debian 11', jonka avulla sain tehtyä pubkeyn.

Ensiksi ajoin omalla koneella komennon ```ssh-keygen``` ja valitsin oletus tallennuspaikan avaimelle. Seuraavaksi komento kysyi passphrasea joka oli ohjeen mukaan erittäin suotavaa määrittää. Laitoin ohjeen mukaisesti sen myös. Komento loi tässä kohtaa avaimen. 

Seuraaava vaihe oli kopioida avain DigitalOceanin virtuaalikoneeseen. Se onnistui kommennolla ```ssh-copy-id sami@188.166.25.109```. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20c1.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20c1.png)

Kun kaikki vaiheet oli tehty, kokeilin ottaa DigitalOceanin virtuaalikoneeseen yhteyttä ssh-komennolla. Ekalla kerralla piti syöttää passphrase jonka olin luonut aiemmin, mutta toisella kertaa pääsin sisälle ilman salasanaa. Kätevää ja onnistui todella helposti ja nopeasti!

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20c2.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20c2.png)

### d) Tutki jonkin nimen DNS-tietoja 'host' ja 'dig' -komennoilla.  

Host oli jo aiemmalta tunnilta tuttu komento, mutta dig-komennosta en ollut kuullut aiemmin. Siispä selvittämään löytyykö moista koneelta. Eipä löytynyt, eikä saanut heti myöskään asennettua. Tecmintin sivulta löysin että komento tulisi dnsutils mukana joten seuraavaksi asentamaan sitä. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20d1.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20d1.png)

Ajoin ensiksi molemmat komennot omalta domainilta sammyc0de.com. Host näytti ekalla rivillä domainin ip-osoitteen ja muut rivit liittyivät postipalveluihin. Kokeilin myös muita parametrejä host-komennolla mutta en saanut juurikaan niistä enempää irti.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20d2.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20d2.png)

```Dig sammyc0de.com +short``` palautti pelkän domainin ip-osoitteen. Parametri +all palautti tarkat tiedot mm. kyselyn ajan, käytetyn serverin ja milloin data haettiin.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20d3-1.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20d3-1.png)

Kokeilin samoja komentoja nuorkauppakamarin sivulle. Komennoista on luettavissa tälläkin kertaa domanin ip-osoite. Dig-komennosta on nähtävissä että A-tietua viittaa ip-osoitteeseen, kun taas CNAME on tehty domain-nimellä. Nappasin ip-osoitteen vielä dig -x komentoon joka ajaa reverse dns lookupin. Tällä komennolla oli nähtävissä että osoite viittaa xetnetin palvelimelle, joten tästä voi päätellä sivujen hostingin.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20d4.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20d4.png)

Spotifyn kohdalla selvisi että nimellä on myös käytössä ipv6-osoite, ipv4-osoitteen lisäksi. Ajamalla reverse DNS lookup käyttämällä spotifyn ip-osoitetta paljastui että spotifyn sivusto sijaitsee Googlen-palvelimella.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20d5.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20d5.png)


### Lähteet

- Karvinen, Tero. Linux Palvelimet 2024 alkusyksy. https://terokarvinen.com/linux-palvelimet/#laksyt-
- Namecheap. How to Create a Subdomain for my Domain. https://www.namecheap.com/support/knowledgebase/article.aspx/9776/2237/how-to-create-a-subdomain-for-my-domain/
- Karvinen 2012. Short HTML5 page. https://terokarvinen.com/2012/short-html5-page/
- Lehto, Susanna. Teoriasta käytäntöön pilvipalvelimen avulla (h4). https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/
- Karvinen 2018. Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address. https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/
- Apache. Name-based Virtual Host Support. https://httpd.apache.org/docs/2.4/vhosts/name-based.html
- DigitalOcean. How to Set Up SSH Keys on Debian 11. https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-debian-11
- Techmint. Installing dig & nslookup on Debian / Ubuntu. https://www.tecmint.com/install-dig-and-nslookup-in-linux/#digdebian
- PhoenixNAP. dig Command in Linux with Examples. https://phoenixnap.com/kb/linux-dig-command-examples
- Microsoft. Copilot. https://copilot.microsoft.com/
