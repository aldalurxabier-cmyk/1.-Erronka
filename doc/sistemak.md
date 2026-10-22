---
layout: page
title: Sistemak
---
## Sarrera

Ikasgai honetan, sistema gure sistema eragilearen funtzioak eta bere osagaiak zeintzuk diren zehaztu, windows familiako sistema instalatu eta konfiguratu, disko gogorren bolumenak kudeatu eta RAID egiturak sortu eta disko gogorretako informazioen galeren aurrean ahalik eta informazio gutxien galtzeko prestatu dugu gure sistema. Hauetaz aparte, zerbitzarian lan egingo duten erabiltzaileak eta taldea zein diren zehaztu, hauen baimenak prestatu, pasahitzen segurtasun politikak zeintzuk izango diren zehaztu, web zerbitzaia martxan jarri eta segurtasun kopiak egitea ere ahalbidetu ditugu. Jarraian, hauek lortzako emandako pausoak azalduko ditugu.

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

1. Administratzaileari Pasahitza Ezarri:

System Administrator (Administrator) kontuarentzat pasahitz sendo bat ezarri (letra maiuskulak, minuskulak, zenbakiak eta ikurrak erabiliz). Gure kasuan, honela utzi dugu:

* **Erabiltzailea**: administrador
* **Pasahitza**: 3T_123

2. Ekipoaren izena aldatu:

Ekipoak defektuz ekartzen duen izena aldatu dugu, zerbitzari-ingurune batean erraz identifikatu ahal izateko (adibidez, zerbitzuak, IIS edo kudeaketa-lanak egiterakoan zein makina den argi jakiteko) eta sareko beste ekipoekin izen-gatazkarik egon ez dadin:

**Ekipoaren Izena**: 1ERRONKASERVER

2. Guest Additions Instalatu:

    1. VirtualBox-eko goiko menuan: Devices > Insert Guest Additions CD image....
    2. Windows Server barruan, ireki unitate optikoa eta exekutatu VBoxWindowsAdditions.exe.
    3. Berrabiarazi makina birtuala pantailaren erresoluzioa eta integrazioa optimizatzeko.

3. Sistema eguneratu:

Sistemaren lehen instalazioa dugunez, sistema eguneratu gabe dago. Oraingo pausoa, eguneraketa guztiak aplikatzea izango dugu. Azken finean, sistemaren eguneraketa egiteak azken segurtasun-adabakiak eta kontrolatzaileen eguneratzeak aplikatzen direla bermatzen du, ezagututako ahultasunak babestuz. Horrez gain, ondoren egingo ditugun urrats guztiak (webgunea igotzea, pasahitz eta segurtasun politikak, etab.) ingurune fidagarri baten gainean eraikiko direla bermatzen du.

Hau egiteko, Sistemaren konfiguraziora sartu eta **Windows Update** hautatuko dugu. Jarraian eskatzen dituen eguneraketak aplikatzeko eskatuko diogu. Hauek amaitutakoan, makina berrabiarazi eta eguneraketa guztiak zuzen aplikatu direla bermatuko dugu.

Azken pauso honekin, gure Windows server-a prest utzi dugu berarekin lanean hasi ahal izateko. Hau egin ondoren, beste lan batzuekin jarraitu ahal dugu (Beharrezko Rolak eta herramintak instalatu, erabiltzaileak, pasahitza eta politikak sortu, baimenak kudeatu…)

## 2. IP-a konfiguratu

Gure zerbitzariarekin lan egin ahal izateko eta sistemaren kanpo aldetik konektatzeko, IP estatiko bat eman diogu. Izatez, DHCP-ak berak automatikoki asignatu ahal dio, baina gerta daikete, zerbitzaria abiarazi bakoitzean IP ezberdina aurkitzea eta honek zerbitzaria gure sarean aurkitzerakoan arazoak ematea. Horrenbestez, IP finko bat ezarri diogu. 

Gure kasuan, beste ikaskideek ere beraien IP-ak beharko dituztelako, ezin izan dugu edozein jarri, zeren beste norbaitek gure IP berdina erabiliko badu, makinekin konektatzeko garaian, arazoak izango ditugu. Horrenbestez, gelako kideen artean IP-ak banatu ditugu, gelako zerrendako ordenaren arabera. Guk erabiliko dugun IP-a 192.168.70.1 izango da (Maskara 255.255.255.0). 70 zenbakia, SISA1 gelari dagokion sarea da eta 1 zenbakia, Xabier gelako zerrenda gelako lehena dugunez, berak libre duen IP-etako bat a hori da.

Gure gailuari IP finkoa ezartzeko urratsak ondorengo hauek dira:

* Administrador de servidor sartu.
* Servidor Local aukeratu.
* Enthernet atalean sartu.
* IP eta maskara jarri.

IP manualki jarri dugunez, gure interneteko sarreraren IP-a ere jarri behar dugu. Informatikako SISA1 gelako kasuan, IP hau 192.168.70.254 dugu.

Jarri dugun IP-a hau da:

* IP zerbitzaria: 192.168.70.1
* Maskara: 255.255.255.0
* Ateribidea (Puerta de enlace): 192.168.70.254

Hauek idatzi ondoren, ez dugu arazorik izango gure zerbitzaria sarean aurkitzeko.

## 3. Segurtasun politikak (Pasahitzak)

Enpresa batean, oso garrantzitsuak dira segurtasun politikak zehatz eta egoki betetzea. Azken finean, oso informazio garratzitsua egon ohi da enpresetako zerbitzarietan eta pasaitz desegoki batek, informazioa galtzea edo norbaitek ostea ekar diezaioke. Kontu honek, arazo larriak ekarri ahal dizkio enpresa bati. Arazo hauek ekiditeko, segurtasun politikak ezarri ohi dira.

Hauek dira jarraitu ditugun pausoak politika hauek ezartzeko:

* Directiva de seguridad Local sartu.
* Directiva de cuentas aukeratu.

Bertan bi aukera ditugu. Alde batetik, pasahitzek izan behar dituzten ezaugarriak zehazten dira (Gutxieneko luzera, erabili beharreko gutxieneko karaktereak...). Bestaldetik berriz, pasahitzen erabilera desegoki baten aurrean gure zerbitzariak nola jokatu asignatzen da (Hainbat aldiz jarraian pasahitza gaizki sartuko balitz, kontua blokeatu adibidez). Hauek dira guk ezarri ditugun politikak:

* Gutxienez 8 karaktereko pasaitzak
* Azken 12 pasahitz gogoratuko dira (Historial de contraseñas)
* Konplexutasuna bai (Karaktere berezien erabilera, maiuskulak eta zenbakiak erabili beharra)
* 60 eguean behin pasahitza aldatu behar da
* Pasahitza 5 aldiz jarraian gaizki sartzen bada, kontua 30 minutuz blokeatuta izango da.
* Administratzailearen kontuan ere politika hauek eragina izatea ahalbidetu egin dugu.

## 4. Diskoak eta bolumenak

### 4.1 Diskoak

Enpresa batek, egunerokotasuean hainbat fitxategi eta datu garrantzitsu sortzen eta erabiltzen ditu. Guzti hauek, memorietan gordeta egon behar izaten dira normalean (Disko gogorrak, SSD...). Horrenbestez, sistema eragilea instalatu dugun disko gogorraz aparte, disko gehiago sartzea erabaki dugu.

Memoria berri bat erosi eta sartu aurretik, kontuan hartu beharreko hainbat gauza ditugu. Lehenbizi, zenbat memoria behar dugun kalkulatu behar dugu eta honetaz aparte, aurrerago izango den datuen azkundea ere zenbatekoa izango den jakitea oso garrantzitsua da, oso denbora gutxian, memoria beteta gelditu eta berriro diskoak aldatzen ibili beharrik ez izateko. Diskoen abiadura ere zenbatekoa den kontuan hartu beharrekoa izan ohi da.

Gure kasuan, 3 disko gogor gehitu ditugu, bakoitza 50GB koa. (Urrengo ataleak azalduko dugu 3 disko gogor hautatzearen erabakia zergatik hartu dugun.).

Disko hauek, gure makina birtualean dugun zerbitzariadi gehitzeko pasuo hauek jarraitu ditugu.

* VirtualBox-eko makina birtualaren konfigurazioan, ""Almacenamiento"" atalean, disko gogorrak gehitzeko aukerari eman.
* Jarraian, diskoak hautatzeko menuan, disco berriak sortu ditugu.
* Amaitzeko disko hauek makina birtualera geitu ditugu.

## 4.2 Bolumenak

Diskoak gehitu ondoren, disko hauek erabilgarri izateko, bolumenak sortu behar dira. Disko gogor baten bolumena datuak eta artxiboak gorde ahal izateko zatitzen den biltegiratze-espazioaren atal edo zatia da  Sistema eragileak diskoa modu ordenatuan erabiltzeko eta fitxategi-sistema bat (NTFS, FAT32, etab.) ezartzeko erabiltzen du.

Disko bakoitza, bolumen bat edo gehiagotan zatitu ahal da. Gaitasun honi esker, disko gogorra lan eremu ezberdinetan banatzeko aukera ematen digu, nahiz eta izatez disko gogor bakarra izan. Bolumen ezberdinak sortzeko pausoak hauek dira:

* ""Administrador de discos"" sartu.
* Bolumenak sortu nahi diren diskoa hautatu.
* Bolumenari eman nahi zaion memoria kantitatea haukeratu.
* Formatua (FAT32, NTFS...) eta eman nahi zaion letra (C: / D:/ E:/) aukeratu.

Diskoan soberan geratu den memoriarekin behar adina bolumen egin ditzakegu, diskoko memoria osoa bete harte. Gure kasuan, 50GB-ko bolumen bakarra utzi dugu, emango diogun erabilerarrako ez dugulako bolumen ezberdinak egiteko beharrik ikusten.

## 5. RAID

## 6. Erabiltzaileak eta taldeak (Baimenak)



## 7. Sistemaren Rol-ak eta ezaugarriak gehitu (IIS)

