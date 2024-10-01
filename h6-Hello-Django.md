 
#### Tietokone, jossa ajettiin virtuaalikonetta

- CPU: 12th Gen Intel® Core™ i5-12400F
- GPU: AMD Radeon™ RX 6600 XT 8GB
- Emolevy: Asus Prime B760M-K D4 BIOS Ver. 1658
- Muisti: 32GB DDR4-3600
- SSD: WD Black SN770 1TB (Windows 11), WD Blue SN580 1TB (Debian 12)
- Virtualisointi: VirtualBox Debian 12 käyttöjärjestelmässä

#### Virtuaalikone
- 2 CPU, 4 GB muistia, 30 GB HDD, Debian 12

### a) Tee yksinkertainen esimerkkiohjelma Djangolla.

Olin asentanut aiempia tehtäviä varten VirtualBoxin virtuaalikoneen tietokoneeseeni, joten käytin virtuaalikonetta tehtävässä. Otin varoiksi virtuaalikoneesta snapshotin siltä varalta jos jokin menisi pieleen ja käynnistin virtuaalikoneen. Kirjauduin koneeseen SSH-yhteydellä.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a1.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a1.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a2.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a2.png)

Virtuaalikone ei ollut hetkeen päällä joten ajoin koneeseen päivitykset komennolla ```supo apt-get update -y```. Kun päivitykset oli asennettu, lähdin etenemään Teron ohjeen mukaan "Django 4 Instant Customer Database Tutorial".

Aloitin kommennolla ```sudo apt-get -y install virtualenv```, joka asensi kehitysympäristön.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a3.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a3.png)

Loin uuden env-kansion viimeisimmällä python 3 paketeilla, käyttäen komentoa ```virtualenv --system-site-packages -p python3 env/```. Komennolla ```source env/bin/activate``` sain aktivoitua uuden ympäristön ja komento ```which pip``` näytti virtuaaliympäristön polun.
Seuraavaksi loin tekstitiedoston micro-editorilla, joka sisälsi sanan "django". Micro-editori puuttui, joten joutusin asentamaan sen ennen tiedoston luontia.  Asensin tekstitiedoston avulla Djangon version 5.1.1

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a4.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a4.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a5.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a5.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a6.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a6.png)

Djangon asennuksen jälkeen tein Django-projektin nimellä 'sammyc0de' ja käynnistin serverin kommennolla ```./manage.py runserver```

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a7.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a7.png)

Virtuaalikoneessani ei ole graafista käyttöliittymää joten testasin pääsyä toisesta koneesta, mutta en päässyt sivulle. Seuraavaksi aloin tutkimaan Django-manuaalia (https://docs.djangoproject.com/en/5.1/ref/django-admin/) jossa kerrottiin että localhost ip-osoite (127.0.0.1) ei ole saavutettavissa muista verkon koneista. Development serverin saa näkymään muille verkon koneille, laittamalla komennon ```./manage.py runserver``` perään koneen oma ip-osoite. Tässä tapauksessa se onnistui komennolla ```./manage.py runserver 192.168.1.100:8000``` 

Tämän jälkeen sivu aukesi toisessa koneessa, mutta varoitteli vielä että kone ei ole sallittujen listallla. Djangon ohjeesta (https://docs.djangoproject.com/en/5.0/ref/settings/#std-setting-ALLOWED_HOSTS) selvisi että settings-tiedostossa on erikseen määritetty kohta jossa sallitut koneet.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a8.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a8.png)

Settings.py tiedosto löytyi alla olevasta kansiosta ja muokkaus onnistui micro-editorilla. Allowed_hosts-kohtaan laitoin virtuaalikoneen omaan ip-osoitteen, joka näkyi myös selaimen herjassa. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a9-0.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a9-0.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a9.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a9.png)

Tämän jälkeen palvelimen uudellen käynnistys komennolla ```./manage.py runserver 192.168.1.100:8000``` ja nyt sivu näkyi toisessa koneessa, virtuaalikoneen ip-osoitteella.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a10.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a10.png)

Palvelimeen ei päässyt vielä kirjautumaan, joten jatkoin Teron ohjeilla eteenpäin, päivittämällä tietokannnat. Sen jälkeen oli vuorossa uuden käyttäjän luonti, käyttäen apuna salasanan luonti komentoa. Kun käyttäjä oli luotu, laitoin palvelimen päälle ja kirjautuminen onnistui uudella käyttäjällä. Tässä kohtaa oli hyvä lopettaa tältä päivältä (29.9.24).

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a11.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a11.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a12.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a12.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a13.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a13.png)

Jatkoin tehtävää seuraavana päivänä 30.9.24, laittamalla ensiksi virtuaalikoneen päälle ja koneeseen sisälle SSH-yhteydellä.  Päätin tehdä ohjeissa näytetyn asiakasrekisterin, hieman soveltaen. Loin uuden crm-kansion ohjelmalle komennolla ```./manage.py startapp crm```, jonka jälkeen lisäsin settings.py tiedostoon crm-ohjelman.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a14.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a14.png)

Models.py tiedostoon määritin ohjelman 'modelit', komennolla ``` micro crm/models.py ```. Tiedostoon luotiin Customers-luokka ja sen tietueet. Ohjeesta poiketen, sovelsin tässä kohtaa ja lisäsin muitakin kuin nimi-kentän.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a15.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a15.png)

Kun tiedostoon oli määritykset tehty ja tallennettu, päivitin muutokset serverille ajamalla komennot ```./manage.py makemigrations``` ja ```./manage.py migrate```. Uusi tietokanta piti vielä rekisteröidä komennolla ```micro crm/admin.py```. Tiedostoon tehtiin alla näkyvät päivitykset.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a16.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a16.png)

Tämän jälkeen uusi Customers-luokka näkyi onnistuneesti selaimella Djangon admin-käyttöliittymässä. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a17.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a17.png)

Testiksi lisäsin kaksi uutta asiakasta ohjelmaan. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a19.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a19.png)

History-sivu näytti ajankohdan koska asiakas oli lisätty järjestelmään.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a19-2.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a19-2.png)

Lisätyt asiakkaat eivät näkyneet tunnistettavilla nimillä, joten seuraavaksi piti lähteä muokkaamaan models.py-tiedostoa. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a20.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a20.png)

Määritin tiedostoon että listassa asiakkaat näkyvät sukunimen ja etunimen perusteella.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a21.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a21.png)

Kun muutokset oli tehty models.py-tiedostoon, ohjelma listasi asiakkaat oikein, määritetyllä tavalla. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a22.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a22.png)

Kokeilin vielä luoda uuden käyttäjän 'admin', jolle annoin nimen mukaisesti admin-oikeudet. Loin uuden käyttäjä kohdan 'Authentication and authorization' alta ja sieltä kohdasta 'Users' '+ Add'. Kirjautuminen tunnuksella onnistui, käyttäjällä admin-oikeudet toimi. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-a23.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-a23.png)

### b) Tee Djangon tuotantotyyppinen asennus

Jatkoin b-tehtävään suoraan aiemmasta tehtävästä, hyödyntämällä samaa virtuaalikonetta. Noudatin tässä tehtävässä Teron tekemää ohjetta 'Deploy Django 4 - Production Install', mutta soveltaen koska osa määrityksistä tai asennuksista oli jo tehty aiemmin virtuaalikoneelle. Loin ensiksi /home/sami -kansion alle kansiot 'publicwsgi/sammyc0de/static/'. Seuraavaksi tein virtual hostin config-tiedoston sammyc0de.conf komennolla ```sudoedit /etc/apache2/sites-available/sammyc0de.conf``` ja config-tiedostoon tein määritykset ohjeen mukaisesti.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b1.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b1.png)

Jostain syystä en saanut näkymään index-sivun tekstiä 'Statically see you at sammyc0de' komennolla ```curl http://localhost/static/```, jonka olin aiemmin määrittänyt. Olin myös aiemmin poistanut käytöstä oletus sivun komennolla ```sudo a2dissite 000-default.conf```. Komento ```/sbin/apache2ctl configtest``` sen sijaan meni läpi ja kuittasi että syntaksi ok.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b2.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b2.png)

Koska sivu ei näkynyt, päätin käydä katsomassa onko virtuaalikoneella muita sivuja. Virtuaalikoneella oli aiemmassa tehtävässä luotu hattu-sivu joten poistin vielä sen käytöstä. Sen jälkeen käynnistin Apachen uudelleen ja curl-komento näytti oikein static-sivun tekstin. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b3.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b3.png)

Seuraavaksi menin publicwsgi-kansioon ja loin sinne env-kansion kommennolla  ```virtualenv -p python3 --system-site-packages env ```. Sain aktivoitua uuden ympäristön komennolla ```source env/bin/activate``` kuten aiemminkin ja komennolla ```which pip``` sain näkyviin virtuaaliympäristön polun. Loin micro-editorilla tekstitiedoston, joka sisälsi sanan "django" ja asensin sen avulla Djangon version 5.1.1. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b4.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b4.png)

Kopioisin a-tehtävässä tehdyn CRM-projektin kansion publicwsgi alle jonka jälkeen muutin Apachen config-tiedoston sammyc0de.conf ohjeen mukaisesti.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b5.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b5.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b6.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b6.png)

Seuraavaksi asensin Apachen WSGI moduliin kuvasssa näkyvällä komennolla.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b7.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b7.png)

Tarkistin syntaksin kommennolla ``` /sbin/apache2ctl configtest``` joka näytti ok, jonka jälkeen Apachen uudelleen käynnistys. Komento ```curl -s localhost|grep title``` ei mennyt läpi vaan herjasi virhettä '500 Internal Server Error'. 
Tässä kohtaa tuli mieleen tarkistaa tulikohan kaikki määritetty oikein sammyc0de.conf tiedostoon. Tarkistin tiedostoon määritetyt polut kuvakaappausta vasten ja huomasin että TVENV muuttujaan on määritetty polku väärin. Olin kopioinut python kansion nimen suoraan ohjeesta, mutta todellisuudessa kansion nimi olikin python3.11, eikä python3.9. Kävin korjaamassa polun Apachen config-tiedostoon sammyc0de.conf.

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b8.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b8.png)

Kokeilin uudestaan curl-komentoa ja nyt ei tullut enää virheilmoitusta. Tällä kertaa herjasi 'disallowedhost' ilmoitusta mutta olin aiemmin määrittänyt että vain ip-osoitteella pääsee näkemään sivun. Komennolla ```curl -sI localhost|grep Server``` tarkistin että kyseessä on Apache, eikä mikään development server. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b9.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b9.png)

Testasin sivua toisesta koneesta selaimella, mutta näytti jostain syystä vanhoja sivuja. Sivut olivat aktivoituneet uudestaan joten otin ne pois käytöstä kuvassa näkyvillä komennoilla. Sen jälkeen apachen uudelleen käynnistys ja nyt näkyi Django-sivu oikein selaimessa toisella koneella, virtuaalikoneen ip-osoitteella. Curl-komentokin meni läpi, kun vaihdoin localhostin tilalle virtuaalikoneen ip-osoitteen. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b10-1.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b10-1.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b11.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b11.png)

Seuraavaksi jatkoin ohjeen mukaisesti, muokkaamalla settings.py tiedostoa jossa määritin  debug-tilan pois päältä ja lisäsin localhostin sallittujen listalle. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b12.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b12.png)

Tiedoston tallennuksen jälkeen ajoin touch-komennon wsgi.py tiedostolle ja käynnistin apachen uudelleen. Komento ``` curl -s localhost|grep title``` antoi 'Not found' tuloksen kuten ohjeessakin, mutta toisella koneella selain näytti sivun. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b13.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b13.png)

Muotoilut eivät näkyneet vielä oikein sivulla, joten muokkasin settings.py tiedostoa ohjeen mukaan. Lisäsin sinne rivit 'import os' ja 'STATIC_ROOT = os.path.join(BASE_DIR, 'static/')'. Lopuksi vielä komennon ```./manage.py collectstatic ``` ajo, joka korjasi muotoilut oikeaksi. Nyt näkyi selaimessa sivu oikein. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b14.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b14.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b15.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b15.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b16.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b16.png)

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h6/h6-b17.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h6/h6-b17.png)

### Lähteet

- Karvinen, Tero. Linux Palvelimet 2024 alkusyksy. https://terokarvinen.com/linux-palvelimet/#laksyt-
- Karvinen 2021. Django 4 Instant Customer Database Tutorial. https://terokarvinen.com/2022/django-instant-crm-tutorial/
- Karvinen 2021. Deploy Django 4 - Production Install. https://terokarvinen.com/2022/deploy-django/
- Django. 5.1 documentation. Django-admin and manage.py. https://docs.djangoproject.com/en/5.1/ref/django-admin/
- Django. 5.0 documentation. Settings. https://docs.djangoproject.com/en/5.0/ref/settings/#std-setting-ALLOWED_HOSTS
- Django. 5.1 documentation. Models. https://docs.djangoproject.com/en/5.1/topics/db/models/
- Freecodecamp 2023. Django Model Fields – Common Use Cases and How They Work. https://www.freecodecamp.org/news/common-django-model-fields-and-their-use-cases/
