---
layout: page
title: Datu Baseak
---

# DESKRIBAPENA 

Streaming plataforma batek bere datu-basean erabiltzaileak, perfilak, planak, edukiak eta bistaratzeak kudeatu nahi ditu.

Erabiltzaile bakoitzak ID Erabiltzaile, Posta elektronikoa, izena eta jaiotze-data ditu. Erabiltzaileek planak kontratatu ditzakete, eta plan bakoitzak bere identifikazio zenbakia, izena eta prezioa ditu. Erabiltzaile batek plan bat kontratatzen du eta kontratazio bakoitzean planaren hasiera eta amaiera datak gordetzen dira. 

Erabiltzaile bakoitzak perfil bat edo gehiago izan ditzake baina perfil bat erabiltzaile batena da. Perfilak, ID perfilak, izena, mota eta rola izango ditu. Plataforman hainbat eduki daude ikusgai, eta eduki bakoitzari buruz identifikazio zenbakia, mota eta adin sailkapena gordetzen da. Profil bakoitzak hainbat eduki ikus ditzake, eta eduki bera hainbat profilek ikus dezakete. Ikusitako edukien eta profilen arteko erlazioa gordetzeko, ikusitako eduki bakoitzaren biztaratzeak ere erregistratzen dira. 

Edukiak hiru motatakoak izan daitezke: pelikulak, telesailak eta dokumentalak. Pelikulei buruz, izena eta pelikulen biztaratzeak gordetzen dira. Telesail bakoitzari buruz ere, izena eta bistaratze telesailak gordetzen dira. Dokumental bakoitzari buruz, izena eta bistaratze dokumentalak erregistratzen dira. 

Telesail bakoitzak denboraldi bat edo gehiago izan ditzake, eta denboraldi bakoitza telesail bakar bati dagokio. Denboraldiei buruz, identifikazio zenbakia, gaia eta izen-zenbakia gordetzen da. 

Bukatzeko denboraldi bakoitzak kapitulu bat edo gehiago ditu, eta kapitulu bakoitza denboraldi bakar batekoa da. Kapitulu bakoitzari buruz, Id-kapituloa, izena, zenbakia eta bistaratzeak gordetzen dira. Kapituluak dagokion denboraldiarekin lotuta erregistratzen dira, denboraldi bakoitzeko kapituluak identifikatu eta antolatu ahal izateko.

# ER DIAGRAMA 

![Mi foto](img/DB/ER%20diagrama.png)

# EREDU ERLAZIONALA

Erabiltzaileak: ( Id erabiltzailea, izena, posta elektronikoa, jaiotze-data, ┄┄ Id Plan ┄┄ )

Planak: ( Id Plan, izena, prezioa )

Profilak: ( Id profila, ┄┄ Id erabiltzailea ┄┄, Mota, izena, rola )

Ikusi: ( <text underline>Id profila</text>, <text underline>Id edukia</text>, Bistaratzeak ) text

Edukiak: ( Id edukia, Mota, Adin-sailkapena )

Pelikulak: ( Bistaratzeak, izena, (ID: Edukiaren FK) )

Dokumentalak: ( Bistaratzeak, izena, (ID: Edukiaren FK) )

Telesailak: ( Bistaratzeak, izena, (ID: Edukiaren FK) )

Denboraldiak: ( <text underline>Id edukia</text>, Id denboraldia, gunea, denbora/banaketa )

Kapituluak: ( Id kapitulua, ┄┄ Id denboraldiak ┄┄, Bistaratzeak, zenbakia, izena )

