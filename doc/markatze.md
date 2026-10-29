---
layout: page
title: Markatze Lengoaiak
---

## Sarrera

Proiektu honetan HTML eta CSS erabiliz webgune bat sortu dugu. Horretarako izenburuak, zerrendak, estekak eta irudiak gehitu ditugu baita menu bat eta footer bat ere. Gainera CSS estiloak aplikatu ditugu webgunearen diseinua hobetzeko eta dokumentazioa GitHub-en egin dugu MD erabiliz.


##  1. Erabilitako programak 

- **HTML:** Testuak, izenburuak, irudiak eta estekak sortzeko.
- **CSS:** Koloreak, tamainak, botoiak eta elementuen kokapena aldatzeko.
- **Visual Studio Code:** Kodea idazteko eta editatzeko.
 ![Mi foto](img/markatze/vcs-removebg-preview.png)
- **GitHub:** Fitxategiak gordetzeko eta lana antolatzeko.
  ![Mi foto](img/Digi/githun-removebg-preview.png)


##  2. Karpeta eta fitxategien egitura 

- **css/**: styleserronka.css fitxategia gordetzen du; webgunearen diseinua definitzen du.
- **doc/img/**: Irudiak gaika antolatzen ditu.
- **HTML fitxategiak:** Webguneko sei orriak dira.
- **Markdown fitxategiak (.md):** Dokumentazioa idazteko erabiltzen dira.
- **_config.yml**: GitHub Pages edo Jekyll erabiltzen bada, konfigurazioa zehazten du.


## 3. HTML etiketak

```html
<!DOCTYPE html>
<html lang="eu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3 TALDEA | Informatika</title>
    <link rel="stylesheet" href="css/styleserronka.css">
</head>
    <header>
        <h1>3 TALDEA</h1>
        <p>INFORMAZIOAREN DIGITALIZAZIO WEBGUNEA</p>
    </header>

        <nav>
            <a href="index.html">Hasiera</a>
            <a href="sareak.html">Sareak</a>
            <a href="sistemak.html">Sistemak</a>
            <a href="markatze.html">Markatzea</a>
            <a href="db.html">Datu-baseak</a>
            <a href="digi.html">Digitalizazioa</a>
            
        </nav>

<main>
<h2>SARRERA</h2>

<p>Erronka honetan, enpresa baten azpiegitura informatikoa landuko dugu. Windows Server eta segurtasuna konfiguratuko ditugu, sareak, ASCII, CRC-6 eta modulazioa aztertuko ditugu, eta ER diagramak eta datu-baseak sortuko ditugu. Horrez gain, HTML eta CSS erabiliz webgune bat egingo dugu. Azkenik, proiektuaren planifikazioa, jarraipena eta dokumentazioa GitHub bidez kudeatuko ditugu.</p>

<img src="doc/img/DB/uni-removebg-preview.png" alt="">
</main>

    <footer>
        <p>3 TALDEA Iker,Iñaki,Xabi,Oier</p>
    </footer>

</body>
</html>

```

- **!DOCTYPE html:** HTML5 formatua adierazten du.
- **html lang="eu":** Dokumentuaren hizkuntza euskara dela adierazten du.
- **head:** Orriaren konfigurazioa gordetzen du.
- **title:** Nabigatzaileko fitxaren izena zehazten du.
- **link:** HTMLa CSS fitxategiarekin lotzen du.
- **body:** Webguneko eduki guztia biltzen du.
- **header:** Goiburua sortzen du.
- **nav:** Nabigazio-menua sortzen du.
- **a href="sareak.html">:** Beste HTML orri batera joateko esteka sortzen du.
- **main:** Eduki nagusia biltzen du.
- **h1, h2 eta h3:** Izenburuak sortzen dituzte.
- **p:** Paragrafoak sortzen ditu.
- **img src="..." alt="...":** Irudiak txertatzen ditu; src kokapena da eta alt deskribapena.
- **footer:** Orriaren beheko zatia sortzen du.

## 4. CSS propietateak

``` css

body {
    background-color: #141414;
    font-family: Arial, sans-serif;
    color: white;
}

.login {
    background-color: #000;
    width: 300px;
    margin: 60px auto;
    padding: 30px;
    border-radius: 5px;
}

h1 {
    color: red;
    text-align: center;
    font-size: 38px;
}

h2 {
    text-align: center;
}

input {
    width: 100%;
    padding: 12px;
    margin: 10px 0;
    box-sizing: border-box;
    background-color: #333;
    color: white;
    border: none;
    border-radius: 4px;
}

```


- **margin:** Kanpoko tartea ezartzen du.
- **padding:** Barruko tartea ezartzen du.
- **background-color:** Atzeko planoaren kolorea aldatzen du.
- **color:** Testuaren kolorea aldatzen du.
- **font-family:** Letra mota zehazten du.
- **text-align:** Testua lerrokatzen du.
- **display: flex:** Elementuak malgutasunez antolatzen ditu.
- **flex-direction: colum:** Elementuak bertikalean kokatzen ditu.
- **justify-content: center:** Elementuak erdian kokatzen ditu.
- **gap:** Elementuen arteko tartea ezartzen du.
- **width eta max-width:** Zabalera zehazten eta mugatzen dute.
- **height: auto:** Irudiaren proportzioak mantentzen ditu.
- **border-radius:** Ertzak biribiltzen ditu.
- **min-height: 100vh:** Gutxieneko altuera pantailaren altuerara egokitzen du.

## 5. Webgunearen diseinua eta nabigazioa 

Webguneko orri guztiek diseinu antzekoa dute. Goiburuak taldearen izena erakusten du, menuak beste orrietara sartzeko botoiak ditu, eta eduki nagusian testuak eta irudiak agertzen dira.

href atributuaren bidez, botoi bakoitza dagokion HTML fitxategiarekin lotzen dugu. CSSren bidez, botoien kolorea, testuaren itxura eta edukien kokapena zehazten ditugu.

Webgunea egiaztatzeko, orriak ireki ditugu, menuaren estekak probatu ditugu eta irudiak zein estiloak behar bezala agertzen direla egiaztatu dugu.

## 6. Webgunearen argazkiak

![Mi foto](img/markatze/PRINCIPAL.png)
![Mi foto](img/markatze/pagina.png)

## 7. Web orrialderako sarbidea 
[Web 3 TALDEA](http://127.0.0.1:5500/index.html)




