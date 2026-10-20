---
layout: page
title: Sistemak
---
## Sarrera

Ikasgai honetan, sistema gure sistema eragilearen funtzioak eta bere osagaiak zeintzuk diren zehaztu, windows familiako sistema instalatu eta konfiguratu, disko gogorren bolumenak kudeatu eta RAID egiturak sortu eta disko gogorretako informazioen galeren aurrean ahalik eta informazio gutxien galtzeko prestatu dugu gure sistema. Jarraian, hauek lortzako emandako pausoak azalduko ditugu.

## 1. Gida Teknikoa: Windows Server-en Instalazioa eta Oinarrizko Konfigurazioa (VirtualBox)

### 1.1. Sarrera eta Helburua

Gida honekin VirtualBox ingurune birtualizatuan **Windows Server** sistema eragilea instalatzeko eta konfiguratzeko hasierako urratsak azalduko ditugu. Konfigurazio hau web-zerbitzaria (IIS) ostatu hartzeko eta diskoen bolumenak (RAID) kudeatzeko oinarri gisa erabiliko da.

### 1.2. Aurrebaldintzak
Instalazioari ekin aurretik, honako baliabide hauek behar ditugu:
* **VirtualBox** eta **Guest Additions** instalatuta izatea.
* **Windows Server ISO** irudia jaitsita izatea (Windows Server 2022 ofiziala kasu honetan).
* Gutxieneko hardware baliabideak ostalariko makinatik (Host):
    * **RAM**: Gutxienez 4 GB (gomendatua: 4096 MB edo gehiago).
    * **CPU**: Gutxienez 2 prozesadore-nukleo (vCPU).
    * **Disko-espazioa**: Gutxienez 32 GB (disko nagusirako).

### 1.3. Makina Birtuala (VM) Sortzea VirtualBox-en

* Makina Birtual Berria Sortu:
    1. Ireki Oracle VM VirtualBox.
    2. Sakatu **"Nueva"** (Berria) botoia.
    3. **Izena**: 1. Erronka
    4. **Mota (Type)**: Microsoft Windows
    5. **Bertsioa (Version)**: Windows Server 2022 x64 es-ES
    6. **Proceed with Unattended instalation, MARKATU GABE** utziko dugu, virtualbox-ek administratzailearen izenak eta pasahitzak automatikoki sortu partez, geuk manualki aldatu ahal izateko instalazio garaian.

* Hardware Baliabideak Esleitu:
    * **Memoria RAM**: 4096 MB (4 GB).
    * **Prozesadoreak (Processors)**: 4 vCPU. (Zerbitzariak behar duen gutxienekoa baino 2 nukleo gehiago ezarri dizkiogu, zerbitzaria hobeto ibili dadin. Gehiago ere jar ditzakegu baina orduan, gure mahaigaineko ordenagailuaren abiadura konprometituko genuke)

* Disko Gogor Birtuala Sortu:
    1. Hautatu **"Create a Virtual Hard Disk Now"**.
    2. Formatua: VDI (VirtualBox Disk Image).
    3. Biltegiratzea: Dynamically allocated (Dinamikoki esleitua).
    4. **Tamaina nagusia**: 50 GB (Sistema eragilerako).

### 1.4. Windows Server-en Instalazio Prozesua

* ISO Irudia Kargatzea:
    1. Makina birtualaren Settings > Storage atalean, hautatu unitate optikoa (Empty).
    2. Sakatu diskoaren ikonoan eta hautatu jaitsitako **Windows Server ISO fitxategia**.
    3. Gorde konfigurazioa eta sakatu **"Start"** (Hasi).

* Hasierako Konfigurazioa (Installer):
    1. **Hizkuntza eta Formatua**: Aukeratu testuinguruari dagokion hizkuntza, ordu-formatua eta teklatu-diseinua (adib. Spanish / Spanish Keyboard).
    2. Sakatu **"Install Now"**.

* Bertsio Hautaketa:
    1. Aukeratu **Windows Server Standar Edition (Desktop Experience) / Experiencia de escritorio** bertsioa (Interfaze grafikoa eduki ahal izateko).
    2. Onartu lizentzia-baldintzak.
* Partizioak Kudeatzea:
    1. Aukeratu sortutako disko nagusia (Unallocated Space) eta sakatu **Next**.
    2. Instalazio prozesua hasiko da (fitxategiak kopiatu, prestatu eta instalatu). Amaitzean makina birtuala berrabiaraziko da.

Windows Server-en instalazioan, aukeratu gabeko espazioan (Unallocated Space) zuzenean **"Next"** sakatzean, sistemak automatikoki sortzen ditu sistema abiarazteko eta kudeatzeko beharrezkoak diren partizio bereziak. honako hauek dira:

* **System Partition** (Sistemaren partizioa) Formatua: NTFS: Windows-ek bere zereginetarako erreserbatzen duen partizio bat da.
* **Recovery Partition** (Berreskuratze Partizioa) Formatua: NTFS: Windows-en Berreskuratze Ingurunea (WinRE - Windows Recovery Environment) gordetzen du. Sistema crahseatzen denean edo abiarazi ezin denean, konpontzeko tresnak bertatik exekutatzen dira.
* **Primary Partition** (Partizio Nagusia - C: Unitatea) Formatua: NTFS: Windows Server sistema eragile osoa, programak, zerbitzuak (IIS, etab.) eta erabiltzaileen datuak biltegiratzen dituen partizio nagusia da.

### 1.5. Hasierako Konfigurazioa

* Administratzaileari Pasahitza Ezarri:
o	System Administrator (Administrator) kontuarentzat pasahitz sendo bat ezarri (letra maiuskulak, minuskulak, zenbakiak eta ikurrak erabiliz). Gure kasuan, honela utzi dugu:

**Erabiltzailea**: administrador
**Pasahitza**: A1234@

* Ekipoaren izena aldatu:
Ekipoak defektuz ekartzen duen izena aldatu dugu, zerbitzari-ingurune batean erraz identifikatu ahal izateko (adibidez, zerbitzuak, IIS edo kudeaketa-lanak egiterakoan zein makina den argi jakiteko) eta sareko beste ekipoekin izen-gatazkarik egon ez dadin:

**Ekipoaren Izena**: 1ERRONKASERVER

* Guest Additions Instalatu:
    1. VirtualBox-eko goiko menuan: Devices > Insert Guest Additions CD image....
    2. Windows Server barruan, ireki unitate optikoa eta exekutatu VBoxWindowsAdditions.exe.
    3. Berrabiarazi makina birtuala pantailaren erresoluzioa eta integrazioa optimizatzeko.

* Sistema eguneratu:
Sistemaren lehen instalazioa dugunez, sistema eguneratu gabe dago. Oraingo pausoa, eguneraketa guztiak aplikatzea izango dugu. Azken finean, sistemaren eguneraketa egiteak azken segurtasun-adabakiak eta kontrolatzaileen eguneratzeak aplikatzen direla bermatzen du, ezagututako ahultasunak babestuz. Horrez gain, ondoren egingo ditugun urrats guztiak (webgunea igotzea, pasahitz eta segurtasun politikak, etab.) ingurune fidagarri baten gainean eraikiko direla bermatzen du.

Hau egiteko, Sistemaren konfiguraziora sartu eta **Windows Update** hautatuko dugu. Jarraian eskatzen dituen eguneraketak aplikatzeko eskatuko diogu. Hauek amaitutakoan, makina berrabiarazi eta eguneraketa guztiak zuzen aplikatu direla bermatuko dugu.

Azken pauso honekin, gure Windows server-a prest utzi dugu berarekin lanean hasi ahal izateko. Hau egin ondoren, beste lan batzuekin jarraitu ahal dugu (Beharrezko Rolak eta herramintak instalatu, erabiltzaileak, pasahitza eta politikak sortu, baimenak kudeatu…)