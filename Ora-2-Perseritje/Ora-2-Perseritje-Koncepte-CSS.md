# Ora 2 — Përsëritje: CSS (Konceptet)
## Udhëzues i Koncepteve — Pjesa 2

---

Kjo është **Pjesa 2** e udhëzuesit konceptual për Orën e Përsëritjes — CSS-ja. (Pjesa 1, HTML, është një dokument më vete.) Sërish, fokusi është te **konceptet**, me shembuj kodi për secilën, jo hap-pas-hapi si te versioni origjinal.

---

## 1. Tri mënyrat për të shtuar CSS

**Inline** — direkt te elementi, me atributin `style`:

```html
<h1 style="color: red;">Emri Mbiemri</h1>
```

**Internal** — brenda `<head>`, me `<style>`:

```html
<head>
  <style>
    h1 {
      color: blue;
    }
  </style>
</head>
```

**External** — një file `.css` i veçantë, i lidhur me `<link>`:

```html
<head>
  <link rel="stylesheet" href="style.css">
</head>
```

```css
/* style.css */
h1 {
  color: #2c3e50;
}
```

- **Inline** — shpejt, por vetëm për një element; e vështirë për t'u mirëmbajtur.
- **Internal** — mirë për teste të shpejta brenda një faqeje.
- **External** — mënyra që **përdoret gjithmonë** në projekte reale: një file mund të stilizojë shumë faqe njëkohësisht, dhe HTML-ja mbetet e pastër.

---

## 2. Selektorët CSS — element, class, id

```css
p { color: black; }              /* çdo <p> në faqe */
.highlight { background: yellow; } /* çdo element me class="highlight" */
#main-nav { background: lightgray; } /* vetëm elementi me id="main-nav" */
```

Kur dy rregulla synojnë të njëjtin element, fiton ai me **specifitet** më të lartë. Shiko këtë konflikt:

```css
p { color: black; }
.highlight { color: green; }
#intro { color: red; }
```

```html
<p id="intro" class="highlight">Ky tekst do jetë i KUQ.</p>
```

Renditja e fitores: **`id` > `class` > element** — pavarësisht se cili rregull është shkruar i fundit në file.

---

## 3. Tipografia — si "flet" teksti

```css
h1, h2 {
  font-family: Georgia, serif;
  color: #2c3e50;
  text-transform: uppercase;
  letter-spacing: 1px;
}

p {
  line-height: 1.6;
  word-spacing: 2px;
}

.rreth-meje p {
  text-indent: 20px;
}

nav a {
  text-decoration: none;
  color: #2c3e50;
}
```

- **`font-family`** — cili shkronjë; zakonisht listohen disa si "rezervë" (`Georgia, serif`).
- **`text-transform: uppercase`** — i bën shkronjat të mëdha vizualisht, pa i ndryshuar në HTML.
- **`letter-spacing`** / **`word-spacing`** — hapësira mes shkronjave / fjalëve.
- **`line-height`** — hapësira mes rreshtave.
- **`text-indent`** — hapësirë bosh para rreshtit të parë të një paragrafi.
- **`text-decoration: none`** — hiqet nënvizimi default i lidhjeve `<a>`.

---

## 4. Box Model dhe `box-sizing`

Çdo element është një "kuti": **content** → **padding** → **border** → **margin**.

```css
/* Problemi: width "rritet" përtej 300px */
.rreth-meje {
  width: 300px;
  padding: 20px;
  border: 2px solid #2c3e50;
  margin: 10px 0;
}
```

```css
/* Zgjidhja: box-sizing e mban width fiks në 300px */
.rreth-meje {
  width: 300px;
  padding: 20px;
  border: 2px solid #2c3e50;
  margin: 10px 0;
  box-sizing: border-box;
}
```

Shumë projekte reale e vendosin këtë si **default universal**, që në krye të file-it CSS, në vend që ta shtojnë element-nga-element:

```css
* {
  box-sizing: border-box;
}
```

> ⚠️ `*` synon **çdo** element në faqe — e fuqishme, por përdoret vetëm për gjëra "universale" si `box-sizing`, jo për ngjyra apo fonte (ato duhen selektorë specifikë).

---

## 5. `display` — si e ndajnë hapësirën elementet

```css
/* block (default për div, p, h1...) */
.karta { display: block; }

/* inline (default për a, span, strong...) */
.etikete { display: inline; }

/* inline-block: krah për krah, POR me width/height/padding si block */
nav a {
  display: inline-block;
  padding: 8px 15px;
  text-decoration: none;
  color: #2c3e50;
}
```

- **`block`** — merr gjithë gjerësinë, gjithmonë "hidhet" në rresht të ri.
- **`inline`** — vetëm aq hapësirë sa i duhet përmbajtjes; `width`/`height` nuk kanë efekt mbi të.
- **`inline-block`** — kombinim: rri krah për krah si inline, por lejon `width`/`height`/padding si block — pikërisht kështu e bëmë navbar-in horizontal me lidhje "të prekshme".

---

## 6. Efekte vizuale — `border-radius` dhe `box-shadow`

```css
img {
  width: 150px;
  border-radius: 50%;
  box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.3);
}
```

```css
.karte {
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  background: white;
}
```

- **`border-radius`** — rrumbullakos qoshet (`50%` mbi një imazh katror e bën rreth të plotë).
- **`box-shadow: X Y blur ngjyrë`** — zhvendosje-horizontale, zhvendosje-vertikale, mjegullim (blur), ngjyrë/transparencë. Këto janë thjesht **dekorative**, nuk prekin strukturën apo renditjen.

---

## 7. Stilizimi i tabelave me CSS

```css
table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  border: 1px solid #ccc;
  padding: 10px;
  text-align: left;
}

thead {
  background-color: #2c3e50;
  color: white;
}
```

`border-collapse: collapse` bashkon kufijtë e qelizave fqinje në një vijë të vetme (pa të, çdo qelizë do kishte kufirin e vet — vija të dyfishta të shëmtuara).

Një shtesë e vogël, shumë e përdorur në praktikë — rreshta të "vijëzuar" për lexueshmëri më të mirë:

```css
tbody tr:nth-child(even) {
  background-color: #f5f5f5;
}
```

`tr:nth-child(even)` synon çdo rresht **çift** brenda `tbody` (2-tin, 4-tin, ...), pa pasur nevojë të shtojmë `class` te secili rresht individualisht.

---

## Përmbledhje e shpejtë

```
1. CSS: inline (1 element) < internal (1 faqe) < external (best practice)
2. Specifiteti: id > class > element
3. Tipografia kontrollon PAMJEN e tekstit: font-family, color, spacing, line-height...
4. Box model: content+padding+border+margin; box-sizing:border-box e ban width fiks
5. display: block (rresht i ri) | inline (brenda tekstit) | inline-block (krah, me width/padding)
6. border-radius & box-shadow = dekorim vizual, jo strukturë
7. border-collapse:collapse bashkon kufijtë; :nth-child(even) vijëzon rreshtat pa class shtesë
```

---

## Fjalë të shkurtra

- **Specifitet (specificity)** — rregulli që përcakton cili selektor CSS "fiton" kur ka konflikt
- **Box model** — modeli content + padding + border + margin
- **`box-sizing: border-box`** — bën që `width` të përfshijë padding+border, jo t'i shtojë mbi to
- **Pseudo-class** (p.sh. `:nth-child()`, `:hover`) — selekton elemente sipas gjendjes/pozicionit, jo class/id

---

## 🎯 Sfida jote (pikë ekstra)

Shto te `style.css` i "Kartës Personale" **të gjitha** këto rregulla (kod real, jo vetëm shpjegim):

1. `* { box-sizing: border-box; }` në krye të file-it.
2. Një klasë `.karte-info` (mund ta vendosësh te `div`-i `.rreth-meje`) me `border-radius: 10px;` dhe `box-shadow: 0 2px 8px rgba(0,0,0,0.2);`.
3. Nëse ke tabelë, shto `tbody tr:nth-child(even) { background-color: #f0f0f0; }` për vijëzim.
4. Në fund, shkruaj si koment `/* ... */` mbi rregullin `#3`: pse `:nth-child(even)` është më praktik se t'i shtosh `class="rresht-cift"` çdo rreshti manualisht?
