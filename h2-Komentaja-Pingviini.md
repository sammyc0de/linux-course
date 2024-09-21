# h2 Komentaja Pingviini

### x) Karvinen 2020: Command line basics revisited

- Sivulla kerrotaan Linuxin peruskomentoja ja toimintoja joilla pääsee hyvin alkuun
- Komennot on jaettu seuraaviin osioihin: 
  - Liikkuminen kansioissa / tiedostojen katselu
  - Tiedostonhallinto, kansioiden ja tiedostojen luonti / muokkaus / poisto
  - Etäyhteyden muodostaminen SSH:n avulla
  - Komentojen ohjeiden tarkastelu
  - Aiempien komentojen näyttäminen sekä komennon automaattinen täydentäminen Tab-näppäimen avulla
- Lisäksi sivulla käydään läpi tärkeimmät kansiot, pakettien hallinta sekä päivitysten ajo
- Sivuille voisi lisätä vielä:
  - Komennot palveluiden (services) hallintaan
  - Toimintojen (tasks) ajastaminen (crontabilla)

### Tietokone, jolla alla olevat testit suoritettiin:

- CPU: 12th Gen Intel® Core™ i5-12400F
- GPU: AMD Radeon™ RX 6600 XT 8GB
- Emolevy: Asus Prime B760M-K D4 BIOS Ver. 1658
- Muisti: 32GB DDR4-3600
- SSD: WD Black SN770 1TB (Windows 11), WD Blue SN580 1TB (Debian 12)
 
### a) Micro. Asenna micro-editori.
- Micro-editorin asennus onnistui kommennolla: sudo apt-get -y install micro. Parametrin '-y' avulla asennusta saadaan nopeutettua, jolloin kaikkiin kehotettaisiin vastataan automaattisesti 'yes' (kyllä). 
![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%20(2).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%20(2).png)
- Asennuksen jälkeen Micro-editori käynnistettiin komennolla 'micro'.
 ![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%20(3).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%20(3).png)
### b) Apt.
- Valitsin komentoriviohjelmiksi htopin, treen, ja nmapin. Ohjelmien asennus samanaikaisesti onnistui kuvassa näkyvällä komennolla:
![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%20(4).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%20(4).png)
  - Htop on kätevä ohjelma tietokoneen resurssien tarkistamiseen. Ohjelma kertoo mm. cpu:n ja muistin kokonaiskäytön, sekä miten käynnissä olevat prosessit vievät resursseja. Mikäli halutaan optimoida koneen resursseja, on hyödyllistä selvittää mikä vie esim. eniten resursseja. Ohjelmalla on myös mahdollista sammuttaa ajossa olevia prosesseja. Ohessa kuvakaappaus, jossa prosessit järjestetty sen mukaan mikä vie vie eniten suoritintehoja. Ohjelma käynnistettu komennolla htop ilman parametreja.
![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%20(5).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%20(5).png)
  - Tree-komento luo puumaisen näkymän hakemisto rakenteesta. Tree-komentoa on mahdollista käyttää useammalla eri parametrillä. Kuvakaappauksen esimerkissä käytetty parametria joka näyttää vain hakemistot käyttäjän Sami kotihakemistossa.
 ![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%20(6).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%20(6).png)
  - Nmapin avulla on mahdollista tutkia verkkoa, skannata verkossa olevia laitteita sekä selvittää esimerkiksi verkossa olevien laitteiden avoimia portteja. Kuvakaappauksessa tutkittu traceroute parametrillä reittiä osoitteeseen omalta koneelta. Nmapin käytössä tulee noudattaa varovaisuutta. EDIT: Piilotettu kuvasta jälkikäteen ip-osoitetiedot tietoturvasyistä sekä lisätty tarkennus nmapin käyttöön.
![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%20(7).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%20(7).png)

     
### c) FHS.
  - Oheisissa kuvakaappauksissa esitelty tehtävässä määritetyt kansiot kuvissa näkyvillä komennoilla. Viimeisessä kuvakaappauksessa esitelty osa yhden tiedoston sisällöstä cat-komennolla. 
![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%20(8).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%20(8).png)
![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%20(9).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%20(9).png)
![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%20(10).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%20(10).png)

### d) The Friendly M.
  - Grep-komennolla tein kuvakaappauksissa näkyvät testit.
    - Sanan hakeminen tiedostosta, siten että ko. sana merkitään eri värillä.
    ![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%20(11).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%20(11).png)
    - Grep-kommennolla voidaan selvittää myös käytössä oleva verkkoadapteri, sekä sen ip-osoite kun se yhdistetään ip addr -komentoon putkella ("|").
     ![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%20(12).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%20(12).png)
    - Sanan "debian" haku kotihakemistosta oheisella kommennolla.
![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%20(13).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%20(13).png)
### e) Pipe. 
  - Putkella (pipe, "|") on mahdollista yhdistää useampia komentoja toisiinsa.
    - Pipen käyttäminen on esimerkiksi kätevää kun listataan hakemisto jossa paljon kansioita ja tiedostoja. Tällöin näytetään tiedostoja vain ruutu kerrallaan.
     ![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%20(14).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%20(14).png)
    - Tai vastaavasti hakemistojen ja tiedostojen listaus päinvastaisessa järjestyksessä, hyödyntäen sort-komentoa ls-kommennossa putken avulla.
      ![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%20(15).png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%20(15).png)
### f) Rauta.    
- Lswh -komentoa ei ollut aiemmin asennettu Debianiin, joten lswh -asennettiin ensiksi komennollla "sudo apt-get install -y lshw"
- Tämän jälkeen päästiin ajamaan listaus laitteistosta komennolla sudo lshw -short -sanitize
  - Komennon avulla saatiin selvitettyä mm. seuraavat olennaiset tiedot laitteistosta:
    - Emolevyn malli (H/W path 0 - PRIME B760M-K D4)
    - Muistin kokonaismäärä (H/W path 0/c - 32GiB) sekä tiedot muistikammoista (koko, tyyppi ja nopeus - H/W path 0/c/0-1 - 2 x 16GiB DIMM DDR4 Synchronous 3600 MHz)
    - Suorittimen malli (processor) sekä suorittimen välimuistin koot (H/W path 0/19, /0/1, /0/1b, /0/1c)
      - 12th Gen Intel(R) Core(TM) i5-12400F
        - 288KiB L1 cache
        - 192KiB L1 cache
        - 7680KiB L2 cache 
        - 18MiB L3 cache
    - Näytönohjaimen mallisarja (/dev/fb0 - Radeon RX 6600/6600 XT/6600M)
    - Asennetut nvme SSD-levyt emon nvme paikkoihin 0 ja 1 (/dev/nvme0 WD Black SN770 NVMe SSD ja /dev/nvme1 WD_BLACK SN770 1TB) 
    - Levyjen osiot sekä kokonaistila
    -   NVME paikassa 0 (Windows 11) /dev/nvme0-alkuiset
    -   NVME paikassa 1 (Debian 12)  /dev/nvme1-alkuiset
    - Emoelvym integroitu RAID-ohjain (H/W path /0/100/e)
    -   Volume Management Device NVMe RAID Controller (ei käytössä)
    - Tietokoneen emoon integroitu verkkokortti (network - RTL8125 2.5GbE Controller)
    - Tietokoneeseen kytketyt äänikortit ja kamera (multimedia)
      - Näytönohjaimen integroitu äänikortti Navi 21/23 HDMI/DP Audio Controller
      - Kuulokkeiden langaton usb-dongle Jabra Link 370
      - Ulkoinen usb-äänikortti Notepad-5
      - USB-web-kamera Microsoft® LifeCam HD-3000: Mi    
 
  - <pre><span style="color:#26A269"><b>sami@Desktop-Debian</b></span>:<span style="color:#12488B"><b>/</b></span>$ sudo lshw -short -sanitize
    H/W path            Device          Class          Description
    ==============================================================
                                        system         System Product Name (SKU)
    /0                                  bus            PRIME B760M-K D4
    /0/0                                memory         64KiB BIOS
    /0/c                                memory         32GiB System Memory
    /0/c/0                              memory         16GiB DIMM DDR4 Synchronous 3600 MHz (0,3 ns)
    /0/c/1                              memory         16GiB DIMM DDR4 Synchronous 3600 MHz (0,3 ns)
    /0/19                               memory         288KiB L1 cache
    /0/1                                memory         192KiB L1 cache
    /0/1b                               memory         7680KiB L2 cache
    /0/1c                               memory         18MiB L3 cache
    /0/1d                               processor      12th Gen Intel(R) Core(TM) i5-12400F
    /0/100                              bridge         Intel Corporation
    /0/100/1                            bridge         12th Gen Core Processor PCI Express x16 Controller #1
    /0/100/1/0                          bridge         Navi 10 XL Upstream Port of PCI Express Switch
    /0/100/1/0/0                        bridge         Navi 10 XL Downstream Port of PCI Express Switch
    /0/100/1/0/0/0      /dev/fb0        display        Navi 23 [Radeon RX 6600/6600 XT/6600M]
    /0/100/1/0/0/0.1    card1           multimedia     Navi 21/23 HDMI/DP Audio Controller
    /0/100/1/0/0/0.1/0  input21         input          HDA ATI HDMI HDMI/DP,pcm=3
    /0/100/1/0/0/0.1/1  input22         input          HDA ATI HDMI HDMI/DP,pcm=7
    /0/100/1/0/0/0.1/2  input23         input          HDA ATI HDMI HDMI/DP,pcm=8
    /0/100/1/0/0/0.1/3  input24         input          HDA ATI HDMI HDMI/DP,pcm=9
    /0/100/1/0/0/0.1/4  input25         input          HDA ATI HDMI HDMI/DP,pcm=10
    /0/100/6                            generic        RST VMD Managed Controller
    /0/100/a                            generic        Platform Monitoring Technology
    /0/100/e                            storage        Volume Management Device NVMe RAID Controller
    /0/100/14                           bus            Intel Corporation
    /0/100/14/0         usb1            bus            xHCI Host Controller
    /0/100/14/0/1       card0           multimedia     Jabra Link 370
    /0/100/14/0/6                       bus            USB 2.0 Hub
    /0/100/14/0/6/1                     input          USB Receiver
    /0/100/14/0/6/1/0   input14         input          Logitech G602
    /0/100/14/0/6/2     input15         input          Logitech Gaming Keyboard G213 Keyboard
    /0/100/14/0/6/3     card2           multimedia     Notepad-5
    /0/100/14/0/6/4     card3           multimedia     Microsoft® LifeCam HD-3000: Mi
    /0/100/14/0/8                       input          AURA LED Controller
    /0/100/14/0/a                       bus            USB2.0 Hub
    /0/100/14/1         usb2            bus            xHCI Host Controller
    /0/100/14/1/a                       bus            USB3.0 Hub
    /0/100/14.2                         memory         RAM memory
    /0/100/15                           bus            Intel Corporation
    /0/100/16                           communication  Intel Corporation
    /0/100/17                           generic        RST VMD Managed Controller
    /0/100/1a                           generic        RST VMD Managed Controller
    /0/100/1c                           bridge         Intel Corporation
    /0/100/1c.7                         bridge         Intel Corporation
    /0/100/1c.7/0       enp5s0          network        RTL8125 2.5GbE Controller
    /0/100/1d                           bridge         Intel Corporation
    /0/100/1f                           bridge         Intel Corporation
    /0/100/1f/0                         system         PnP device PNP0c02
    /0/100/1f/1                         communication  PnP device PNP0501
    /0/100/1f/2                         system         PnP device PNP0c02
    /0/100/1f/3                         system         PnP device PNP0c02
    /0/100/1f/4                         system         PnP device PNP0c02
    /0/100/1f/5                         system         PnP device PNP0c02
    /0/100/1f/6                         system         PnP device PNP0c02
    /0/100/1f.4                         bus            Intel Corporation
    /0/100/1f.5                         bus            Intel Corporation
    /0/6                                bridge         12th Gen Core Processor PCI Express x4 Controller #0
    /0/6/0                              storage        WD Black SN770 NVMe SSD
    /0/17                               storage        Intel Corporation
    /0/101                              bridge         Intel Corporation
    /0/101/0                            storage        Sandisk Corp
    /1                  /dev/nvme0      storage        WD_BLACK SN770 1TB
    /1/0                hwmon1          disk           NVMe disk
    /1/2                /dev/ng0n1      disk           NVMe disk
    /1/1                /dev/nvme0n1    disk           1TB NVMe disk
    /1/1/1              /dev/nvme0n1p1  volume         99MiB Windows FAT volume
    /1/1/2              /dev/nvme0n1p2  volume         15MiB reserved partition
    /1/1/3              /dev/nvme0n1p3  volume         930GiB Windows NTFS volume
    /1/1/4              /dev/nvme0n1p4  volume         767MiB Windows NTFS volume
    /2                  /dev/nvme1      storage        WD Blue SN580 1TB
    /2/0                hwmon2          disk           NVMe disk
    /2/2                /dev/ng1n1      disk           NVMe disk
    /2/1                /dev/nvme1n1    disk           1TB NVMe disk
    /2/1/1                              volume         299MiB Windows FAT volume
    /2/1/2              /dev/nvme1n1p2  volume         896GiB EXT4 volume
    /2/1/3              /dev/nvme1n1p3  volume         34GiB Linux swap volume
    /3                  input0          input          Sleep Button
    /4                  input1          input          Power Button
    /5                  input19         input          PC Speaker
    /6                  input2          input          Power Button
    /7                  input20         input          Eee PC WMI hotkeys</pre>   

### g) Vapaaehtoinen: Valitse muutama rivi lokeista. Tulkitse ja analysoi.
- Debianin lokitietoja on mahdollista tarkistaa journalctl -kommennolla. Oheisessa esimerkissä tarkistettiin f-parametrillä viimeaikaisia tapahtumia järjestelmässä. Lokissa on nähtävissä aiemmassa tehtävässä tarvitun lshw-komennon asennus sekä laitteiston tietojen listaus lswh -kommennolla.
 ![https://github.com/sammyc0de/linux-course/blob/a4b5ab180a34bdbcf3b329f527b0e28e15d585f3/Kuvat/h2/h2-%2016.png](https://github.com/sammyc0de/linux-course/blob/main/Kuvat/h2/h2-%2016.png)
 

## Lähteet

- Karvinen, Tero. Linux Palvelimet 2024 alkusyksy. https://terokarvinen.com/linux-palvelimet/#laksyt
- Karvinen, Tero. Command Line Basics Revisited. https://terokarvinen.com/2006/raportin-kirjoittaminen-4/
- Debian. APT package handling utility, Debian system reference manual for apt-get. man apt-get
- Htop. https://htop.dev/
- Tree. https://www.geeksforgeeks.org/tree-command-unixlinux/
- Nmap. https://nmap.org/
- Digita Ocean. Grep Command in Linux/UNIX. https://www.digitalocean.com/community/tutorials/grep-command-in-linux-unix
- Geeks for Geeks. Piping in Unix or Linux. https://www.geeksforgeeks.org/piping-in-unix-or-linux/
- Digita Ocean. How To Use Journalctl to View and Manipulate Systemd Logs. https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs
