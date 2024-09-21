# h1 Oma Linux

## **x) Artikkelit**

**Raportin kirjoittaminen**
- Raportissa kuvattu täsmällisesti mitä tehty eri vaiheissa, raportti on toistettava
- Raportin pitää olla täsmällinen ja siinä pitää näkyä mitä eri vaiheissa on tapahtunut.
- Raportti on helppolukuinen, siten että siinä käytetään väliotsikoita ja kieli on huoliteltua.
- Lähteisiin tulee viitata ja ne tulee merkitä raporttiin
- Raportissa ei tule sepittää eikä muutenkaan kopioida toisten tekstejä ilman lähdettä. Sama koskee myös kuvia, niiden luvatta käyttäminen on myös kiellettyä.

**Free Software Foundation**

- Free software" eli suomennettu "ilmainen ohjelmisto" tarkoittaa että ohjelmistoa voi vapaasti ajaa, kopioida, jakaa, opiskella, muuttaa sekä parantaa
- Ohjelmia voi käyttää vapaasti mihin tahansa tarkoitukseen.
- Ohjelmia voi vapaasti tutkia miten ne toimivat sekä muuttaa sen mukaisesti miten ohjelman haluaa toimivan. Ehtona on että lähdekoodiin annetaan pääsy. Ohjelman kopioita voi jakaa vapaasti, auttaakseen muita.
- Ohjelman muokattuja versiota voi vapaasti jakaa muille, jotta muut pääsevät hyötymään myös ohjelmistoon tehdyistä muutoksista. Ehtona on että lähdekoodin annetaan pääsy.

## **a) Linuxin asennus**

EDIT: Lisätty tarkennuksia tietokoneen tietoihin sekä lisätty näytönohjain 28.8.24

Linuxille oli tarvetta itse kasaattuun pöytäkoneesen Windowsin rinnalle. Koneessa oli jo aiemmin asennettuna Windows 11 ja nyt Debian asennettiin kokonaan Windowsin rinnalle toiselle M.2 NVME -levylle. Asennusta varten latasin 'debian-live-12.6.0-amd64-gnome.iso' levykuvan ja levykuva ajettiin asennustikulle Rufus -ohjelmalla Windowsissa. Itse pidän eniten Gnomen -työpöytäympäristöstä joten päädyin lataamaan sen levykuvan. 

Tietokoneen tiedot:

- CPU: 12th Gen Intel® Core™ i5-12400F 
- GPU: AMD Radeon™ RX 6600 XT 8GB
- Emolevy: Asus Prime B760M-K D4 BIOS Ver. 1658
- Muisti: 32GB DDR4-3600
- SSD: WD Black SN770 1TB (Windows 11), WD Blue SN580 1TB (Debian asennettiin tähän)

### Asennus

Asennus aloitettiin menemällä tietokoneen BIOS:iin josta valittiin asennustikku oletus käynnistyslevyksi. 

![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h1/h1-1.jpg](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-1.jpg)

Asennusruudusta valittiin "Live system (amd64)". Samalla saatiin testattua  Debianin toimivuus tietokoneessa.

![[[https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-2.jpg](https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h1/h1-2.jpg)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-2.jpg)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-2.jpg)

Kun tietokone käynnistyi Debianiin, valittiin "Install Debian" taskbarista jonka jälkeen asennusohjelma avautui. 'Welcome' ruudusta jatkettiin eteenpäin oletusasetuksilla.

![[[[![Screenshot from 2024-08-27 16-24-06](https://github.com/user-attachments/assets/29359230-e96f-41f4-b5c1-4890bdb34fdb)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-3.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-1.jpg)](https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h1/h1-3.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-3.png)

'Location' -ruudussa valittin oikea aikavyöhyke, jonka jälkeen 'Next' -painikkeesta eteenpäin.

![[[![Screenshot from 2024-08-27 19-26-38](https://github.com/user-attachments/assets/44d4071d-f8aa-4642-88ec-6970b65f6a13)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-4.png?raw=true)](https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h1/h1-4.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-4.png)

Näppäimistöasetteluksi valitsin 'Finnish' jonka jälkeen Nextillä seuraavalle ruudulle.

![[[![Screenshot from 2024-08-27 19-26-59](https://github.com/user-attachments/assets/6779f743-efb7-4100-9de2-12bce646e893)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-5.png)](https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h1/h1-5.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-5.png)

Valitsin asennuslevyksi kokonaan tyhjän levyn jolla ei ollut ennestään mitään. Tällöin molemmat käyttöjärjestälmät ovat erillisillä levyillä.

![[[![Screenshot from 2024-08-27 19-27-26](https://github.com/user-attachments/assets/51463b43-8706-42da-b8f9-285367c512b5)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-6.png)](https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h1/h1-6.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-6.png)

'Users'-ruudussa määritin itselleni käyttäjätunnuksen, salasanan sekä kuvaavan nimen tietokoneelle.

![[[![Screenshot from 2024-08-27 19-28-07](https://github.com/user-attachments/assets/5191ac0b-9664-49a1-816d-c541dc150fc8)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-7.png)](https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h1/h1-7.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-7.png)

Lopuksi vielä tarkistin tiedot ennen varsinaista asennusta. Kaikki tiedot ok, joten asennus aloitettiin valitsemalla 'Install'. Asennusvaihe kesti n. 5 minuuttia, jonka jälkeen tuli näkyviin 'Finish' -ruutu. Tässä kohtaa valitsin 'Done' jonka jälkeen tietokone käynnistyi uudestaan. Asennustikku poistettiin myös tässä kohtaa. 

![[[![Screenshot from 2024-08-27 19-28-25](https://github.com/user-attachments/assets/7537e7e6-3a41-442c-b778-18a6ff8bc22b)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-8.png)](https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h1/h1-8.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-8.png)

![[[[![Screenshot from 2024-08-27 19-31-38](https://github.com/user-attachments/assets/bfcf3aa6-7d8f-4459-872d-f397f7b429b2)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-8.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-9.png)](https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h1/h1-9.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h1-9.png)

![[[![Screenshot from 2024-08-27 19-36-29](https://github.com/user-attachments/assets/626faa94-32f7-4216-ac30-fa9aa6d8bdb9)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-10.png)](https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h1/h-10.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-10.png)

### Asennuksen viimeistely

Asennus loi automaattisesti GRUB -käynnistyslataajan. GRUB mahdollistaa 'dual bootin' ja valikosta voi valita käynnistetäänkö Debian vai Windows. Debian on oletuksena joka käynnistyy automaattiesti muutaman sekunnin päästä.

![[![IMG_0382](https://github.com/user-attachments/assets/44182ff2-79c5-4dbc-a49e-9195a678658b)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-11.jpg)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-11.jpg)

Debianin käynnistyksen jälkeen valitaan kirjautumisruudusta oma käyttäjätunnus ja syötetään salasanaa.

![[![IMG_0383](https://github.com/user-attachments/assets/9fa4d68c-b1cd-444f-8612-2896514d036d)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-12.jpg)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-12.jpg)

Tämän jälkeen avautuu työpöydälle vielä 'Initial setup'. Valitsin joka kohtaan oletusasetuksen, lukuunottamatta 'Privacy' ruutua josta klikkasin pois päältä sijaintipalvelut. Lopuksi tuli näkyviin 'Setup complete' -ruutu. Debian on nyt valmis käytettäväksi!

![![![[![Screenshot from 2024-08-27 19-40-10](https://github.com/user-attachments/assets/e4dbc016-a176-4faf-8679-77e6b5df5da1)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-13.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-13.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-14.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-13.png)

### Käytön aloitus

Huomaan ensiksi että tietokoneen kello on väärässä n. kolme tuntia. Korjaan ajan oikeaksi asetuksista (Settings -> Date & Time). Tätä pitää seurata onko vikaa mahdollisesti tietokoneen paristossa tms. 

![![[![Screenshot from 2024-08-27 16-40-46](https://github.com/user-attachments/assets/5fcb4eb6-82c7-42a6-a556-2ad8a61d22a6)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-14.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-15.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-14.png)

Seuraavaksi ajoin viimeisimmät päivitykset alla näkyvällä komennolla. Päivitysten jälkeen laitoin vielä käyttöjärtestelmän palomuuurin päälle, komennoilla "sudo apt-get -y install ufw" (muurin asennus) sekä "sudo ufw enable" (muuri päälle).

![[![Screenshot from 2024-08-27 16-41-42](https://github.com/user-attachments/assets/b7d07222-bf85-4fbb-bae7-411caf3f4408)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-15.png)](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h1/h-15.png)

## Lähteet

- Linux Palvelimet 2024 alkusyksy https://terokarvinen.com/linux-palvelimet/#laksyt
- Raportin kirjoittaminen https://terokarvinen.com/2006/raportin-kirjoittaminen-4/
- What is Free Software? https://www.gnu.org/philosophy/free-sw.html
- Install Debian on Virtualbox - Updated 2023 https://terokarvinen.com/2021/install-debian-on-virtualbox/