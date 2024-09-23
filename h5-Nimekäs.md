 
#### Tietokone, jolla otettiin etäyhteys DigitalOceanin virtuaalikoneeseen:

- CPU: 12th Gen Intel® Core™ i5-12400F
- GPU: AMD Radeon™ RX 6600 XT 8GB
- Emolevy: Asus Prime B760M-K D4 BIOS Ver. 1658
- Muisti: 32GB DDR4-3600
- SSD: WD Black SN770 1TB (Windows 11), WD Blue SN580 1TB (Debian 12)


#### DigitalOceanin virtuaalikone pilvessä
- 1 CPU, 512 MB memory, 10 GB SSD Disk, 500 GB transfer limit


### a) Kotisivu. Tee vähintään kolmen erillisen weppisivun kotisivu ja kopioi se näkymään palvelimellesi. Jos sinulla on oikea palvelin Internetissä, kannattaa käyttää sitä. Käytä name based virtual hosting tekniikkaa. Sivujen muokkaamisen pitää onnistua ilman pääkäyttäjän oikeuksia, niiden kopioiminen pääkäyttäjänä testisivun paikalle ei käy. Kotisivujen ei tarvitse olla hienoja, mutta niiden tulee olla validia HTML:ää ja linkittää toisiinsa.

Kirjauduin DigitalOceanin virtuaalikoneeseen ja ajoin ensiksi päivitykset. Sen jälkeen kävin muistelemassa miltä näyttää koneen 'etc/apache2/sites-available' -kansiossa. Siellä tosiaan on vaan oletussivu määritettynä, joten seuraavaksi pitäisi pohtia miten saadan näkyviin kolmen sivun web-sivusto. Muistin myös etten ollut asentanut vielä micro-editoria DigitalOceanin virtuaalikoneeseen, joten asensin sen myös tässä kohtaa. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a1.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a1.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a1-2.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a1-2.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a3.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a3.png)

Tehtävän annossa oli että sivut pitäisi kopioida palvelimelle. Seuraavaksi aloin luomaan kolmea eriilistä web-sivua ensiksi omalle koneelle, index.html, contact.html ja about.html.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h5/h5%20a4.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h5/h5%20a4.png)

Tein oman koneen Documents-kansion alle kansion Web, jonne aloin luomaan sivuja micro-editorilla. Käytin sivujen luonnissa apuna Tero Karvisen Short html5 page -pohjaa.

[kuvia]

Tein ensiksi index.html sivun. Tallennuksen jälkeen siirsin sivun vielä Web-kansioon. Seuraavaksi otin tiedostoista kopiot, joilla tein contact.html ja about.html tiedostot. Tämän jälkeen muokkasin micro-editorilla hieman vielä sivuja.

[kuvia]

Seuraavaksi palasin takaisin DigitalOceanin virtuaalikoneeseen ja loin "Public_html" -kansion kotihakemistoon. Tämän jälkeen aktivoisin kotihakemiston ajamalla komennon 'sudo a2enmod userdir', jonka jälkeen apachen uudelleen käynnistys.

[kuvia]

Tämän jälkeen palasin takaisin omalle koneelle jossa oli web-sivujen tiedostot. Yritin useamman kerran tiedostojen kopiointia scp-komennolla omalta koneelta DigitalOceanin virtuaalikoneeseen, eri tavoilla onnistumatta siinä.

[kuva]

Tässä kohtaa tuli mieleen onko mahdollista tehdä edes tiedostoa paikallisesti 'home/sami/public_html' -kansioon. Avasin micron ja yritin tallentaa uutta tiedostoa joka herjasi että vaaditaan sudo-oikeuksia. Kysin Copilolta tässä miten saada oikeudet kuntoon 'public_html' kansioon. Ensimmäinen vastaus oli että vaihtamalla kansion omistaja oikeaksi ja määritämällä groupiksi www-data. Komennon jälkeen sain onnistuneesti luotua myös testi-tiedoston (jonka poistin heti seuraavaksi).

Seuraavaksi hyppäsin takaisin omalle konelle ja kokeilin uudestaan tiedostojen kopiointia. Nyt sain kaikki tiedostot kopsattua onnistuneesti kerralla! Sivutkin näytti toimivan.

[kuva]

Sivut eivät näy suoraan vielä domanini juuressa vaan ~sami -takana joten tein seuraavaksi config tiedoston domainille komennolla ```sudoedit /etc/apache2/sites-available/sammyc0de.com.conf```. Tiedoston luonnin jälkeen sivu vielä päälle sekä apachen uudelleen käynniystys.

Nyt sivut näkyvät suoraan myös osoitteella http://sammyc0de.com/. Muokkasin lopuksi hieman sivuja micro-editorilla.



### b) Alidomain. Tee kaksi uutta alidomainia, jotka osoittava omaan koneeseesi. Esimerkiksi palvelu on example.com -> linuxkurssi.example.com. Tee toinen alidomain A-tietueella ja toinen CNAME-tietueella. Alidomainit ovat tyypillisesti ilmaisia, kun sinulla on päädomain (example.com).

Minulla oli ennestään hankkittuna domain-nimi sammyc0de.com Namecheap-palvelusta. Määritin palvelun 'Advanced DNS' -asetuksissa itselleni kaksi uutta alidomainia. A-tietueella määritin alidomainin blog.sammyc0de.com ja CNAME-tietueella alidomanin linux.sammyc0de.com

Käytiin apuna lähdettä https://www.namecheap.com/support/knowledgebase/article.aspx/9776/2237/how-to-create-a-subdomain-for-my-domain/

[Lisää kuva nmapista]

DigitalOceanin virtuaalikone oli valmiina auki edellisestä tehtävästä joten tein seuraavaksi kansiot alidomaineille. 

[Lisää kuva]

Tämän jälkeen muokkasin tiedostoa ```sudoedit /etc/apache2/sites-available/sammyc0de.com.conf```, ohjeen mukaan jonka löysin Apachen sivulta https://httpd.apache.org/docs/2.4/vhosts/name-based.html. Määritin tiedostoon uudet alidomainit jonka jälkeen käynnistin apachen uudelleen. Seuraavaksi kävin lisäämässä vielä index.html -tiedostot alidomaineille. Alidomainit näkyvät oikein selaimessa.

[Lisää kuva]

### c) Pubkey. Automatisoi kirjautuminen julkisella SSH-avaimella.

Seurasin DigitalOceanin ohjetta 'How to Set Up SSH Keys on Debian 11', jonka avulla sain tehtyä pubkeyn.

Ensiksi ajoin komennon ```ssh-keygen``` ja valitsin oletus tallennus paikan avaimelle. Seuraavaksi komento kysyi passphrasea joka oli ohjeen mukaan erittäin suotavaa määrittää. Laitoin ohjeen mukaisesti sen myös. Komento loi tässä kohtaa avaimen. 

Seuraaava vaihe oli kopioida avain DigitalOceanin virtuaalikoneeseen. Se onnistui kommennolla ```ssh-copy-id sami@188.166.25.109```. 

[kuva]

Kun kaikki vaiheet oli tehty, kokeilin ottaa DigitalOceanin virtuaalikoneeseen yhteyttä ssh-komennolla. Ekalla kerralla piti syöttää passphrase jonka olin luonut aiemmin, mutta toisella kertaa pääsin sisälle ilman salasanaa. Kätevää ja onnistui todella helposti ja nopeasti!

[kuva]

### d) Tutki jonkin nimen DNS-tietoja 'host' ja 'dig' -komennoilla.  

Host oli jo aiemmalta tunnilta tuttu komento, mutta dig-komennosta en ollut kuullut aiemmin. Siispä selvittämään löytyykö moista koneelta. Eipä löytynyt, eikä saanut heti myöskään asennettua. Tecmintin sivulta löysin että komento tulisi dnsutils mukana joten seuraavaksi asentamaan sitä. 

[kuva]

Ajoin ensiksi molemmat komennot omalta domainilta sammyc0de.com. Host näytti ekalla rivillä domainin ip-osoitteen ja muut rivit liittyivät postipalveluihin. Kokeilin myös muita parametrejä host-komennolla mutta en saanut juurikaan niistä enempää irti.

[kuva]

```Dig sammyc0de.com +short``` palautti pelkän domainin ip-osoitteen. +all palautti tarkat tiedot mm. kyselyn ajan, käytetyn serverin ja milloin data haettiin.

Kokeilin samoja komentoja nuorkauppakamarin sivulle. Komennoista on luettavissa tälläkin kertaa domanin ip-osoite. Dig-komennosta on nähtävissä että A-tietua viittaa ip-osoitteeseen, kun taas CNAME on tehty domain-nimellä. Nappasin ip-osoitteen vielä dig -x komentoon joka ajaa reverse dns lookupin. Tällä kommennolla oli nähtävissä että osoite viittaa xetnetin palvelimelle, joten tästä voi päätellä sivujen hostingin.

[kuva]

Spotifyn kohdalla selvisi että nimellä on myös käytössä ipv6-osoite, ipv4-osoitteen lisäksi. Ajamalla reverse DNS lookup käyttämällä spotifyn ip-osoittea paljasti spotifyn palvelu sijaitsee Googlen-palvelimella.

### Lähteet

https://terokarvinen.com/linux-palvelimet/

Namecheap https://www.namecheap.com/support/knowledgebase/article.aspx/9776/2237/how-to-create-a-subdomain-for-my-domain/


https://terokarvinen.com/2012/short-html5-page/


https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/

https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/

https://httpd.apache.org/docs/2.4/vhosts/name-based.html

https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-debian-11

https://www.tecmint.com/install-dig-and-nslookup-in-linux/#digdebian

https://phoenixnap.com/kb/linux-dig-command-examples