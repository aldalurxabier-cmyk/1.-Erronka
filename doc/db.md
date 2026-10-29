---
layout: page
title: Datu Baseak
---

# Sarrera

Lehenik eta behin, enuntziatu bat eman digute eta bertan agertzen den informazioa interpretatu behar izan dugu. Gero, deskribapena egin dugu eta horrekin E/R diagrama osatu dugu. Ondoren, eredu erlazionala sortu dugu eta datu-basea normalizatu dugu. Azkenik, egindako lana Access-en inplementatu dugu.

# 1. Deskribapena

Streaming plataforma batek bere datu-basean erabiltzaileak, perfilak, planak, edukiak eta bistaratzeak kudeatu nahi ditu.

Erabiltzaile bakoitzak NAN, Posta elektronikoa, izena, 2 abizenak eta jaiotze-data ditu. Erabiltzaileek planak kontratatu ditzakete, eta plan bakoitzak bere identifikazio zenbakia, izena eta prezioa ditu. Erabiltzaile batek plan bat kontratatzen du eta kontratazio bakoitzean planaren hasiera eta amaiera datak gordetzen dira. 

Erabiltzaile bakoitzak perfil bat edo gehiago izan ditzake baina perfil bat erabiltzaile batena da. Perfilak, ID perfilak, izena eta rola izango ditu. Plataforman hainbat eduki daude ikusgai, eta eduki bakoitzari buruz identifikazio zenbakia, mota eta adin sailkapena gordetzen da. Profil bakoitzak hainbat eduki ikus ditzake, eta eduki bera hainbat profilek ikus dezakete. Ikusitako edukien eta profilen arteko erlazioa gordetzeko, ikusitako eduki bakoitzaren biztaratzeak ere erregistratzen dira. 

Edukiak hiru motatakoak izan daitezke: pelikulak, telesailak eta dokumentalak. Pelikulei buruz, izena eta pelikulen bistaratzeak gordetzen dira. Telesail bakoitzari buruz ere, izena eta bistaratze telesailak gordetzen dira. Dokumental bakoitzari buruz, izena eta bistaratze dokumentalak erregistratzen dira. 

Telesail bakoitzak denboraldi bat edo gehiago izan ditzake, eta denboraldi bakoitza telesail bakar bati dagokio. Denboraldiei buruz, identifikazio zenbakia, gaia eta izen-zenbakia gordetzen da. 

Bukatzeko denboraldi bakoitzak kapitulu bat edo gehiago ditu, eta kapitulu bakoitza denboraldi bakar batekoa da. Kapitulu bakoitzari buruz, Id-kapituloa, izena, zenbakia eta bistaratzeak gordetzen dira. Kapituluak dagokion denboraldiarekin lotuta erregistratzen dira, denboraldi bakoitzeko kapituluak identifikatu eta antolatu ahal izateko.

# 2. ER Diagrama

![Mi foto](img/DB/ER%20diagrama.png)

# 3. Eredu erlazionala
ER diagrama amaitu eta gero, datu-basearen eredu erlazionala egin dugu. 

![Mi foto](img/DB/EreduErlazionala.png)

# 4. Normalizazioa
Ondoren, datu basearen normalizazioa egin dugu. Hiru forma normalak ( 1FN, 2FN eta 3FN ) aplikatuz.


Normalizazioa eginda ↓

[Sakatu hemen](normalizazioa/Normalizazioa.pdf)

# 5. Datu basea Access-en implementatu 
Atal honetan, gure orain arte egin ditugun Entitate erlazio diagrama, eredu erlazionala eta amaitzeko egindako normalizazioaren ondoren, gure datu base propioa sortzeko beharrezko datuak baditugu. Jarraian, access-ean sortu ditugun taluak eta barruko atribu bakoitza zer den, zertarako den eta zein murrizketa aplikatu ditugun aipatuko dugu:

EDUKIAK : 

Proiektuan dauden ikus-entzunezko eduki nagusiak kudeatzeko taula da. Hauek dira bere atributuak:

•	Id_Edukiak - (Gako nagusia)

Eduki bakoitza modu bakarrean eta errepikaezinean identifikatzeko balio du.

Zenbaki osoa (Auto-zenbaketa) gisa jarri dugu formatua, erregistro bakoitzari zenbaki bat automatikoki emateko.

•	Mota:

Edukiaren Izena edo mota adierazten du.

Testu labur bezala gordeko dugu (30 karaktere).

•	Adin-Sailkapena:

Eduki bakoitza zein adinetik gora ikusi ahalko den zehaztuko du.

Zerrenda desplegablea (Balio-zerrenda) jarri dugu formatu gisa: +3; +7; +12; +16; +18 aukerekin. Eduki bakoitzean balio estandarizatuak bakarrik sartzeko eta akatsak saihesteko. 

PELIKULAK : 

Pelikulen informazio espezifikoa biltzen duen taula da. Hauek dira bere atributuak:

•	Id_Edukiak ( Gako atzerritarra ):

Edukien taularekin erlazioa egiteko eremua da.

Zenbaki oso gisa jarri dugu formatua.

•	Izena:

Pelikularen izena zein den zehazten du.

Testu laburra bezala gordeko dugu datua.

•	Bistaratzea:

Pelikula konkretu bakoitza zenbat aldiz bistaratu den zenbatzen du.

Zenbaki oso gisa jarri dugu formatua.

KAPITULUAK :

 Telesailen kapituluak kudeatzeko taula da. Hauek dira bere atributuak:

•	Id_Edukiak (Gako nagusia):

Eduki konkretu bat dokumentala dela esango du.

Zenbaki oso gisa jarri dugu formatua (Gako printzipala ere hala dago).

•	Izena

Dokumentalaren izena gordetzen du.

Testu labur gisa jarri dugu formatua.

•	Bistaratzeak

Dokumentala zenbat aldiz bistaratu den kontatzen du.

Zenbaki oso gisa jarri dugu formatua (Ezin da behin ere 1,5 aldiz bistaratu eduki bat adibidez).

Murrizketa: Bistaratzeak ezin dira inoiz negatiboak izan, beraz, datua beti 0 tik gora izateko murrizketa ezarri diogu.

DENBORALDIAK : 

 Telesailen denboraldien informazioa gordetzen duen taula da. Hauek dira bere atributuak:

•	Id_denboraldia (Gako nagusia) :

Denboraldi bakoitza bakartzeko eremua da.

Zenbaki osoa (Auto-zenbaketa) gisa jarri dugu formatua.

•	Izena / Zenbakia

Denboraldiaren izena edo zenbatgarrena den idazten du. 

Testu laburra, 30 karaktere.

•	Gaia

Denboraldian gertatuko denaren azalpena eta Gaia gordeko da hemen.

Testu luzea (Paragrafo oso bat idatzi daiteke hemen)

•	Id_Edukiak (Gako atzerritarra):

Denboraldi hori zein telesailetakoa den erlazionatzen du.

Zenbaki oso gisa jarri dugu formatua (Gako printzipala ere hala dago).

TELESAILAK : 

Telesailen datuak biltzen dituen taula da. Hauek dira bere atributuak:

•	Id_Telesailak (Gako nagusia):

Telesail bakoitza banaka identifikatzeko balio du.

Zenbaki osoa (Auto-zenbaketa) gisa jarri dugu formatua.

•	Izena:

Telesailaren izenburua gordetzen du.

Testu labur gisa jarri dugu formatua.

•	Bistaratzea:

Pelikula konkretu bakoitza zenbat aldiz bistaratu den zenbatzen du.

Zenbaki oso gisa jarri dugu formatua.

DOKUMENTALAK :

 Dokumentalen erregistroa kudeatzeko taula da. Hauek dira bere atributuak:

•	Id_Edukiak (Gako nagusia):

Eduki konkretu bat dokumentala dela esango du.

Zenbaki oso gisa jarri dugu formatua (Gako printzipala ere hala dago).

•	Izena

Dokumentalaren izena gordetzen du.

Testu labur gisa jarri dugu formatua.

•	Bistaratzeak

Dokumentala zenbat aldiz bistaratu den kontatzen du.

Zenbaki oso gisa jarri dugu formatua (Ezin da behin ere 1,5 aldiz bistaratu eduki bat adibidez).

Murrizketa: Bistaratzeak ezin dira inoiz negatiboak izan, beraz, datua beti 0 tik gora izateko murrizketa ezarri diogu.

ERABILTZAILEAK :

 Sistemako erabiltzaileen datuak gordetzen dituen taula da. Hauek dira bere atributuak:

•	NAN ( Gako nagusia ):

Pertsona bakoitzaren identifikazio fiskal bakarra gordetzen du.

Testu labur gisa jarri dugu formatua, eta sarrera-maskara jarri diogu. NAN-ak beti egitura bera izango duenez, hau jarritakoan datuak zuzenean sartzea ahalbidetzen du, akatsak murriztuz.

•	Izena:

Erabiltzailearen izena gordetzen da hemen.

 Testu labur gisa jarri dugu formatua (30 karakterera murriztuta), izena ez baita oso luzea izaten.

•	Abizena_1:

Erabiltzailearen lehen abizena gordetzen da hemen.

Testu labur gisa jarri dugu formatua (izena bezala, 30 karakterera murriztuta).

•	Abizena_2:

Erabiltzailearen bigarren abizena gordetzen da hemen.

Testu labur gisa jarri dugu formatua (30 karakterera murriztuta).

•	Posta Elektronikoa:

Erabiltzailearen harremanetarako emaila gordetzen du.

Testu labur gisa jarri dugu formatua (30 karakterera murriztuta).

•	Jaiotze data:

Erabiltzailearen adina edo adin-tarteak kalkulatu ahal izateko data gordetzea.

Data/Ordua gisa jarri dugu formatua, sistemak data gisa interpretatu eta adin-filtroak egin ahal izateko.

18 urtetik beherakoek ezin izango dutenez gure Streaming plataforman erregistratu, daten murrizketa bat jarri diogu atal honi.

PLANAK : 

 Kontratazio edo harpidetza planak kudeatzeko taula da. Hauek dira bere atributuak:

•	Id_Plana (Gako nagusia):

Plan bakoitza modu bakarrean identifikatzeko eremua da.

Zenbaki osoa gisa jarri dugu formatua.

•	Izena:

Planaren izena gordetzen du.

Testu labur gisa jarri dugu formatua.

•	Prezioa:

Planaren kostua zehazten du.

Moneta gisa jarri dugu formatua, balio ekonomikoak eta dezimalak zuzenean kudeatzeko.

PERFILAK :

 Erabiltzaile bakoitzaren profilak kudeatzeko taula da. Hauek dira bere atributuak:

•	Id_Profilak (Gako nagusia):

Profil bakoitza banaka identifikatzeko balio du.

Zenbaki osoa (Auto-zenbaketa) gisa jarri dugu formatua.

•	Izena:

Profilari eman zaion izena gordetzen du.

Testu labur gisa jarri dugu formatua.

•	Rola:

Ze eduki mota erakutsiko duen finkatzen du.

Zerrenda desplegablea (Balio-zerrenda) jarri dugu formatu gisa: +3; +7; +12; +16; +18 aukerekin. Eduki bakoitzean balio estandarizatuak bakarrik sartzeko eta akatsak saihesteko. 

•	NAN ( Gako atzerritarra ):

Profil hori zein erabiltzailearena den adierazten du.

Testu labur gisa jarri dugu formatua, erabiltzailearen taularekin erlazionatzeko.

ERABILTZAILE PLANA :

Erabiltzaileek hautatutako planen erlazio-taula da. Hauek dira bere atributuak:

•	NAN (Gako atzerritarra):

Plana kontratatu duen erabiltzailea zein den adierazten du.

Testu labur gisa jarri dugu formatua. (Gako nagusian bezala)

•	Id_Plana (Gako nagusia):

Kontratatu de plana zein den adierazten du.

Zenbaki oso gisa jarri dugu formatua.

•	Plan hasiera:

Kontratatutako planaren hasiera data gordetzen da.

Data formatuan gordeko dugu datu hau.

•	Plan amaiera:

Kontratatutako planaren amaiera data gordetzen da.

Data formatuan gordeko dugu datu hau.

IKUSI :

 Perfil konkretu batek eduki konkretu bat zenbat aldiz bistaratu duen adierazten du:

•	Id_Perfilak (Gako atzerritarra):

Zein perfiletaz hitz egiten hari garen zehazten du.

Zenbaki osoa gisa jarri dugu formatua.

•	Id_Edukiak (Gako atzerritarra):

Ikusi den edukia zein den zehazten du.

Zenbaki oso gisa jarri dugu formatua.

•	Bistaratzeak:

Perfilak edukia zenbat aldiz bistaratu duen erregistratzen du.

Testu labur gisa jarri dugu formatua.
