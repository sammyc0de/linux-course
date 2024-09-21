# h3 Hello Web Server

EDIT 11.9.24: Lisätty tarkennetut lähteet tiivistelmään.

### x) Tiivistelmät 
### The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support
### Karvinen 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address

- IP-pohjaiset virtual hostit (IP-based virtual hosts) perustuvat IP-osoitteisiin, siten että jokainen host tarvitsee oman ip-osoitteen. (The Apache Software Foundation 2023)
- Nimi-pohjainen virtual hosting (name-based virtual hosting) perustuu hostnameen, jolloin useampi host voi jakaa saman ip-osoitteen. (The Apache Software Foundation 2023)
- Nimi-pohjaiset virtual hostit ovat myös yksinkertaisempia. Tällöin riittää että nimipalvelimella (DNS server) määritetään hostname osoittaamaan oikealle ip-osoitteelle sekä  Apachen web-palvelimelle määritetään vastaavat hostnamet. (The Apache Software Foundation 2023)
- Apachen web-palvelimella virtual host määritetään luomalla .conf-tiedosto /etc/apache2/sites-available/ -hakemistoon. (Karvinen 2018)
- Mikäli sivuston osoite on esimerksi 'pyora.example.com', luodaan pyora.example.com.conf tiedosto ko. hakemistoon. Hakemisto sivustolle on myös muistettava luoda mkdir komennolla, esim. mkdir -p /home/xubuntu/publicsites/pyora.example.com/. (Karvinen 2018)
- Conf-tiedostoon tehdään seuraavat määritykset (Karvinen 2018):
  - ServerName: sivuston domain-name, esim. pyora.example.com
  - ServerAlias: domainin aliasnimi, esim. www.pyora.example.com
  - DocumentRoot: sivuston polku palvelimella, esim. /home/xubuntu/publicsites/pyora.example.com
  - Directory: Hakemiston määritykset, esim. kenelle sallitaan pääsy hakemistoon
- Kun conf-tiedostoon on tehty tarvittavat määritykset,  laitetaan virtual host päälle sudo a2ensite [ServerName] -komennolla ja käynnistetään apachen web-palvelin uudelleen komennolla sudo systemctl restart apache2. (Karvinen 2018)

Esimerkki conf-tiedostosta (Karvinen 2018):
```  
<VirtualHost *:80>
 ServerName pyora.example.com
 ServerAlias www.pyora.example.com
 DocumentRoot /home/xubuntu/publicsites/pyora.example.com
 <Directory /home/xubuntu/publicsites/pyora.example.com>
   Require all granted
 </Directory>
</VirtualHost>  
```

### Tietokone johon virtuaalikone asennettiin testejä varten.

- CPU: 12th Gen Intel® Core™ i5-12400F
- GPU: AMD Radeon™ RX 6600 XT 8GB
- Emolevy: Asus Prime B760M-K D4 BIOS Ver. 1658
- Muisti: 32GB DDR4-3600
- SSD: WD Black SN770 1TB (Windows 11), WD Blue SN580 1TB (Debian 12)
- Virtualisointi: VirtualBox Debian 12 käyttöjärjestelmässä

Olin asentanut aiemmassa tehtävässä Debianin suoraan yllä olevalla raudalle, mutta en halunnut asentaa web-palvelinta raudalle. Tästä syystä tein virtuaalikoneen web-palvelinta varten, asentamalla Debian 12 -käyttöjärjestelmän VirtualBox:lle.

### Virtuaalikoneen asennus testejä varten.

1) Käynnistin aiemmin asennetun VirtualBoxin ja valitsin valikosta Machine -> New. Tämän jälkeen tein kuvassa näkyvät määritykset luotavalle virtuaalikoneelle. Asennus mediana käytin debian-12.7.0-amd64-netinst.iso -tiedostoa. Seuraavaksi valitsin 'Next'.
   
![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(2).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(2).png)

2) Virtuaalikoneelle määritin muistiksi 4 GB sekä 2 CPU corea.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(3).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(3).png)

3) Virtuaalikoneen levyn kooksi asetin 30 GB.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(4).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(4).png)

4) Lopuksi vielä tarkistin 'Summary' ruudulta että kaikki määritykset oikein ja valitsin lopuksi 'Finish'.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(5).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(5).png)

5) Seuraavaksi käynnistin virtuaalikoneen valitsemalla 'Start', jonka jälkeen virtuaalikone käynnistyi Debianin asennukseen, aiemmin ladatulta iso-tiedostolta. Valitsin valikosta 'Install' jonka jälkeen ohjattu asennus alkoi.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(6).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(6).png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(7).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(7).png)

6) Asennuksen aikana määritin seuraavat asetukset Debianin virtuaalikoneelle:
    - Location: Finland
    - Country to base default locale settings: United States
    - Keyboard: Finnish
    - Hostname: debian-web
    - Username: sami
    - Partioning scheme: All files in one partition
    - Software selection: web server, SSH server, standard system utilities. HUOM! tässä kohdassa jätin tarkoituksella pois graafisen käyttöliittymän koska web-palvelinta voi hallita myös ilman sitä.
![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(8).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(8).png)

7) Asennuksen jälkeen käynnistin virtuaalikoneen joka käynnistyi suoraan command lineen.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(9).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(9).png)

8) SSH etäyhteyttä varten määritin virtuaalikoneelle  kiinteän ip-osoitteen. Kiinteän ip-osoitteen määritin muokkaamalla /etc/network/interfaces -tiedostoa nanolla. Tämän jälkeen käynnistin network servicen uudelleen jonka jälkeen kiinteä ip-osoite oli käytössä.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(10).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(10).png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(11).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(11).png)


### a) Testaa, että weppipalvelimesi vastaa localhost-osoitteesta

- Kirjauduin aiemmassa vaiheessa tehtyyn virtuaalikoneeseen SSH:llä käyttäen virtuaalikoneen kiinteä ip-osoitetta.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(12).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(12).png)

- Palvelin vastaa localhost-osoitteesta, curl-komento näyttää web-palvelimen oletus sivun.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(13).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(13).png)


### b) Etsi lokista rivit, jotka syntyvät, kun lataat omalta palvelimeltasi yhden sivun.

- sudo tail /var/log/apache2/access.log -komento näyttää seuraavat lokirivit kun avasin palvelimelta oletus web-sivun

  ![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(14).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(14).png)

```
192.168.1.205 - - [08/Sep/2024:15:53:34 +0300] "GET / HTTP/1.1" 200 3380 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.0.0 Safari/537.36"
192.168.1.205 - - [08/Sep/2024:15:53:34 +0300] "GET /icons/openlogo-75.png HTTP/1.1" 200 6040 "http://192.168.1.100/" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.0.0 Safari/537.36"

```
- **192.168.1.205 - - [08/Sep/2024:15:53:34 +0300] "GET / HTTP/1.1" 200 3380 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.0.0 Safari/537.36"**
  - **192.168.1.205** - IP-osoite josta pyyntö tehty
  - **[08/Sep/2024:15:53:34 +0300]**- Pyynnön päivämäärä ja aika
  - **"GET / HTTP/1.1"** - Pyynnön tyyppi ja resurssi jota pyydettiin. Sivun lataus käyttäen HTTP-prokollaa.
  - **200** - HTTP response statuksen koodi. 200 = OK, pyyntö onnistunut.
  - **3380** - Objektin koko joka palautui pyynnön tekijälle
  - **"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.0.0 Safari/537.36"** - tiedot selaimesta jota käytettiin pyynnön tekemiseen

- **192.168.1.205 - - [08/Sep/2024:15:53:34 +0300] "GET /icons/openlogo-75.png HTTP/1.1" 200 6040 "http://192.168.1.100/" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.0.0 Safari/537.36"**
  - **192.168.1.205**- IP-osoite josta pyyntö tehty
  - **[08/Sep/2024:15:53:34 +0300]** - Pyynnön päivämäärä ja aika
  - **"GET /icons/openlogo-75.png HTTP/1.1"** - Pyynnön tyyppi ja resurssi jota pyydettiin. Kuva web-sivulla.
  - **200** - HTTP response statuksen koodi. 200 = OK, pyyntö onnistunut.
  - **6040** - Objektin koko joka palautui pyynnön tekijälle
  - **"http://192.168.1.100/"** - Web-palvelimen ip-osoite
  - **"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.0.0 Safari/537.36"** - tiedot selaimesta jota käytettiin pyynnön tekemiseen

### c) Etusivu uusiksi & e) Tee validi HTML5 sivu.

Tehtävässä käytin apuna Tero Karvisen tekemää ohjetta [Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address](https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/). 
Ensiksi korvaan web-palvelimen oletussivun komennolla echo "Default"|sudo tee /var/www/html/index.html. Tämän jälkeen ei tulee enää Apachen oletussivua web-palvelimen ip-osoitteella tai localhostilla. Localhost antaa tulokseksi nyt vain 'Default'. Tämän vaiheen olisi voinut myös mielestäni ohittaa, kun localhost täytyy muutenkin korvata uudella sivulla hattu.example.com.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(15).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(15).png)

Seuraavaksi luon uuden conf-tiedoston hattu.example.comia varten komennolla sudoedit /etc/apache2/sites-available/hattu.example.com.conf. Määritän tiedostoon ServerNamen, ServerAliaksen, Document Rootin sekä Directoryn. Ohjeessa näkyy DocumentRootissa ja Directoryssa 'Xubuntu' mutta virtuaalikoneessa ei ole ketään sen nimistä käyttäjää, joten korvaan sen omalla käyttäjänimellä. Tallennan lopuksi hattu.example.com.conf tiedoston.
![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(16).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(16).png)

Tämän jälkeen aktivoin web-sivuston komennolla sudo a2ensite hattu.example.com. Komennon jälkeen saan ilmoituksen että lokalisoinnin määritys ei onnistu. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(17).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(17).png)

Googlen kautta löysin artikkelin [Perl: warning: Setting locale failed in Debian and Ubuntu](https://www.cyberciti.biz/faq/perl-warning-setting-locale-failed-in-debian-ubuntu/) jossa tarjottiin ratkaisuksi määrittämällä LC_ALL or LC_TYPE paikalliseksi kieleksi. Tämä onnistui artikkelissa mainitulla komennolla ```export LC_ALL=C```. Tämän jälkeen pysäytin vielä sivuston ja laitoin uudestaan päälle, eikä ainakaan tässä kohtaa tullut enää vastaavaa herjaa. Web-palvelin piti käynnistää vielä uudestaan komennolla ```sudo systemctl reload apache2 ```

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(18).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(18).png)

Seuraavaksi loin hakemiston hattu.example.com sivustolle jonka polun olin aiemmin määrittänyt conf-tiedostoon. Sen jälkeen lisäsin index.html tiedoston vielä hakemistoon, jossa teksti hattu. Curl-komennolla sain tarkistettua vielä että hattu.example.com vastaa.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(19).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(19).png)

Muokkasin hattu.example.comin index.html tiedostoa, siten että sivusta tuli validi html5 -sivu. Muokkasin sivua ilman sudoa, komennolla nano index.html

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(20).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(20).png)

Tarkistin tekemäni sivun W3C Markup Validation Servicessä ja validator antoi varoituksen puuttuvasta lang - attribuutista, joten lisäsin sen vielä sivulle.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(21).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(21).png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(22).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(22).png)

Nyt tarkistus meni läpi eikä herjannnut enää virheistä.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(23).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(23).png)

Tämän jälkeen halusin testata pääsyä sivulle toisesta tietokoneesta, joten kävin lisäämässä web-palvelin ip osoitteen tietokoneen hosts-tiedostoon komennolla ```sudoedit /etc/hosts```. Hattu.example.com näytti aukenevan hienosti toisesta tietokoneesta.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(24).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(24).png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(25).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(25).png)

Tehtävän annossa kerrottiin että palvelimen localhost tulee ohjautua myös hattu-sivulle. [Apachen dokumentaation](https://httpd.apache.org/docs/2.2/mod/core.html#serveralias) mukaan conf-tiedostossa voi olla useita ServerAlias tietueita joten kokeilin lisätä toisen ServerAliaksen eli localhost ServerAliaksen hattu.example.com.conf tiedostoon. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(26).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(26).png))

Tämän jälkeen pysäytin vielä oletus sivun komennolla ```sudo a2dissite 000-default.conf ``` ja käynnistin web-palvelimen uudelleen komennolla ``` sudo systemctl reload apache2 ```.
Näiden jälkeen tarkistin vielä curl-komennolla että localhost ohjautuu hattu-sivulle onnistuneesti.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(27).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(27).png)

### f) Anna esimerkit 'curl -I' ja 'curl' -komennoista.

Curl-komentoa testatin ensiksi -I parametrilla. Man curl kertoi että -I parametri näyttää otsake tiedot osoitteesta. Ohessa esimerkki localhost osoitteesta sekä selitetty muutama otsake.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(28).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(28).png)

- **HTTP/1.1 200 OK** - Protokolla ja HTTP response koodi. 200 = OK eli onnistunut. 
- **Date: Sun, 08 Sep 2024 17:43:43 GMT** - Pyynnön ajankohta UTC-ajassa
- **Server: Apache/2.4.62 (Debian)**- Web-palvelimen tyyppi
- **Last-Modified: Sun, 08 Sep 2024 16:46:15 GMT**- Viimeksi muokattu
- ETag: "110-6219e60f2fcb0"
- Accept-Ranges: bytes
- **Content-Length: 272** - Pyynnön koko
- Vary: Accept-Encoding
- **Content-Type: text/html** - sisällön tyyppi, html-sivu

Pelkällä curl-komennolla on mahdollista nähdä sivun html-lähdekoodi.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(29).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(29).png)

### m) Vapaaehtoinen, suosittelen tekemään: Hanki GitHub Education -paketti.

Tein hakemuksen Github Education -paketista osoitteessa https://education.github.com/. Lopuksi sain ilmoituksen että pyyntö vastaanotettu. Valitettavasti sain kuitenkin myöhemmin sähköpostia Githubilta etteivät voi myöntää Github Education pakettia minulle, koska lähettämäni opintotodistus ei kelpaa. Githubin kanssa selvittelyt siis jatkuvat ja teen heille tukipyynnön vielä.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h3/h3%20%20(30).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h3/h3%20%20(30).png)


## Lähteet

- Karvinen, Tero. Linux Palvelimet 2024 alkusyksy. https://terokarvinen.com/linux-palvelimet/#laksyt- 
- Apache HTTP SERVER PROJECT. Name-based Virtual Host Support. https://httpd.apache.org/docs/2.4/vhosts/name-based.html
- Karvinen, Tero. Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address. https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/
- LinuxTechi. How to Assign Static IP Address on Debian 12. https://www.linuxtechi.com/configure-static-ip-address-debian/
- Sumo logic. Understanding the Apache Access log: View, Locate and Analyze. https://www.sumologic.com/blog/apache-access-log/
- MDN Web docs. HTTP response status codes. https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
- CyberCiti. Perl: warning: Setting locale failed in Debian and Ubuntu. https://www.cyberciti.biz/faq/perl-warning-setting-locale-failed-in-debian-ubuntu/
- Karvinen, Tero. Short HTML5 page. https://terokarvinen.com/2012/short-html5-page/
- W3C. Markup Validation Service. https://validator.w3.org/
- MDN Web docs. HTTP range requests. [https://developer.mozilla.org/en-US/docs/Web/HTTP/Status](https://developer.mozilla.org/en-US/docs/Web/HTTP/Range_requests)
