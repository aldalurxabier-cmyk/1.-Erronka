---
layout: page
title: Sareak
---
# Image Example Page

# PSK(2),ASK(2),FSK(2)
PSK(2),ASK(2) eta FSK(2) egin baino lehen guk aukeratutako pasahitza bitarrera aldatu dugu, behin bitarrean izan dugunean zatiketa egin dugu CRC6 formularekin $$(X^6+X^5+X^3+X^2+X+1)$$.

Zatiketaren hondarra lortu eta gero (PSK2,ASK2,FSK2) grafikoak egin ditugu.
Grafikoak egiteko lortu ditugun 54 bit-ak sei-naka banatu ditugu.

## PSK2 - MODULAZIO ARAUAK
* PSK(2) norabidea adierazten digu, baita bitak binaka multzokatzen dira.
* 4 hasiera mota desberdin daude: (00,01,10,11.)
- 00 hasiera: 0-tik hasten da eta gora joaten da.

- 01 hasiera: Goitik hasten da ASK(2) definitzen duen lekutik.

- 10 hasiera: 0-tik hasten da eta behera joaten da.

- 11 hasiera: Betikan hasten ASK(2) definitzen duen lekutik.
![Mi foto](img/Sareak/psk,ask,fsk.png)

## ASK2 - MODULAZIO ARAUAK
* ASK(2) altuera adierazten digu, baita bitak binaka multzokatzen dira.
* 4 altura mota desberdin daude: (00,01,10,11)
* Altuerak marrazteko lehenik taula bat marraztu behar da eta bertan datuak ipini.
argazkia
![Mi foto](img/Sareak/ask.png)
## FSK(2) - MODULAZIO ARAUAK
* FSK(2) uhin kopurua adierazten digu, baita bitak binaka multzokatzen dira.
* 4 uhin mota daude: (00,01,10,11)
- 00 mota: uhin bat bakarrik bidaltzen du.

- 01 mota: 2 uhin bidaltzen ditu.

- 10 mota: 3 uhin bidaltzen ditu.

- 11 mota: 4 uhin bidaltzen ditu.
![Mi foto](img/Sareak/fsk.png)

## PSK(2),ASK(2),FSK(2) ARIKETA
![Mi foto](img/Sareak/PSK(Z),ASK(2),FSK(2).png)

# MANCHESTER IEEE
* Manchester IEEE-k bitak adierazten ditu eta hartzaileari datuak noiz irakurri behar dituen jakiten laguntzen dio.

* Manchester IEEE egiteko lehenik tarte bakoitzari dagokion geziak irudikatu ditugu.
- 0: Gezia behera
- 1: Gezia gora
argazkia
* Prozedura: Zatiketa egin eta gero ateratako 54 bitak ipini ditugu lerro batean, ondoren bakoitzari tarte bat laga diogu. Tartea hutzi eta gero zenbaki bakoitzari dagokion gezia ipini diogu, geziak ipini eta gero geziak lotzen hasi gara. Geziak lotzeko dagokion araua jarraitu dugu. ( Araua: igo baino lehen jaitsi behar da, eta jaitsi baino lehen igo behar da.)
## MANCHESTER IEEE ARIKETA
![Mi foto](img/Sareak/IMG_2213.jpg)


# MANCHESTER DIFERENTZIALA
* Manchester Diferentzialak bitak adierazten ditu, eta 0 eta 1 bereizteko bitaren hasieran aldaketarik dagoen ala ez begiratzen da.
- 0: Gezia berdin mantentzen da
- 1: Geziaren noranzkoa aldatzen da

* Prozedura: Zatiketa egin eta gero ateratako 54 bitak ipini ditugu lerro batean, ondoren bakoitzari tarte bat laga diogu. Tartea hutzi eta gero zenbaki bakoitzari dagokion gezia ipini diogu, geziak ipini eta gero geziak lotzen hasi gara. Geziak lotzeko dagokion araua jarraitu dugu. ( Araua: igo baino lehen jaitsi behar da, eta jaitsi baino lehen igo behar da.)
# MANCHESTER DIFERENTZIAL ARIKETA
![Mi foto](img/Sareak/Diferentziala.PNG)



