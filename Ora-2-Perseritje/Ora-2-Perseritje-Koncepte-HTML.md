# Ora 2 — Përsëritje: HTML (Konceptet)
## Udhëzues i Koncepteve — Pjesa 1

---

Në orën e kaluar e ndërtuam "Kartën Personale" hap pas hapi, duke kopjuar kod të gatshëm në secilin hap. Ky udhëzues **nuk e përsërit** atë kod hap-pas-hapi — shpjegon **konceptet** pas elementeve HTML që përdorëm, me shembuj konkretë kodi për secilën. Kjo është **Pjesa 1 (HTML)** — Pjesa 2 (CSS) është një dokument më vete.

---

## 1. Struktura bazë e një faqeje HTML

Çdo faqe HTML fillon me të njëjtën "skelet":

```html
<!DOCTYPE html>
<html lang="sq">
<head>
  <meta charset="UTF-8">
  <title>Karta Ime Personale</title>
</head>
<body>

</body>
</html>
```

- **`<!DOCTYPE html>`** — i thotë browser-it që ky është një dokument HTML modern.
- **`<html lang="sq">`** — "kutia" që përfshin gjithçka; `lang` i thotë browser-it/screen readers gjuhën e faqes.
- **`<head>`** — informacion **PËR** browser-in, nuk shfaqet vizualisht.
- **`<body>`** — gjithçka që **SHEH** përdoruesi.

Ja e njëjta skelet, tani me pak përmbajtje reale brenda `<body>`, që të shohim si funksionon në praktikë:

```html
<body>
  <h1>Emri Mbiemri</h1>
  <p>Unë jam nxënës në jCoders.</p>
</body>
```

> 💡 Nëse diçka nuk shfaqet siç duhet në faqe, kontrollo së pari nëse e ke shkruar brenda `<body>` e jo aksidentalisht brenda `<head>` — `<head>` nuk shfaq asgjë, sado kod të vlefshëm të ketë brenda.

---

## 2. Tituj dhe tekst — `h1`–`h6`, `p`, `br`, `strong`, `em`

`h1` deri `h6` janë titujt, të renditur sipas **rëndësisë strukturore**, jo sipas madhësisë që duam të shohim vizualisht (madhësinë e ndryshojmë më vonë me CSS):

```html
<h1>Titulli kryesor i faqes</h1>
<h2>Nëntitull i rëndësishëm</h2>
<h3>Nëntitull më i vogël</h3>
<h4>...</h4>
<h5>...</h5>
<h6>Titulli më i vogël</h6>
```

Brenda një paragrafi `<p>`, `<strong>` dhe `<em>` kanë kuptime të ndryshme (jo vetëm pamje të ndryshme):

```html
<p>
  Unë jam nxënës në jCoders dhe po mësoj <strong>HTML</strong> dhe <em>CSS</em>.<br>
  Kjo është një faqe që po e ndërtoj hap pas hapi në klasë.
</p>
```

- **`<strong>`** — thekson diçka si **e rëndësishme** (browser-i zakonisht e shfaq bold).
- **`<em>`** — thekson diçka me **theks/intonacion** (browser-i zakonisht e shfaq italic).
- **`<br>`** — vetëm një thyerje rreshti brenda të njëjtit paragraf, jo paragraf i ri.

---

## 3. Lidhjet dhe imazhet — `<a>` dhe `<img>`

```html
<a href="https://www.jcoders.com">jCoders</a>
<a href="https://www.google.com" target="_blank">Google</a>
<a href="https://www.github.com" target="_blank">GitHub</a>
```

- **`href`** — përcakton **ku** të çon lidhja.
- **`target="_blank"`** — e hap në një tab të re, në vend që ta largojë përdoruesin nga faqja jonë.

```html
<img src="foto.jpg" alt="Foto e nxënësit">
```

- **`src`** — cilin file ta shfaqë.
- **`alt`** — përshkrimi tekstual; përdoret nga screen readers dhe shfaqet nëse imazhi nuk ngarkohet dot. Nuk është opsional "për mirësjellje".

Të dyja bashkë, siç i patëm te "Linqet e mia":

```html
<h2>Linqet e mia</h2>
<a href="https://www.jcoders.com">jCoders</a>
<a href="https://www.google.com" target="_blank">Google</a>
<a href="https://www.github.com">GitHub</a>
```

---

## 4. `<div>`/`<span>` kundrejt tags semantike

`<div>` dhe `<span>` janë "kuti" neutrale — nuk kanë kuptim të vetin:

```html
<div class="rreth-meje">
  <p>
    Unë jam nxënës në jCoders dhe po mësoj <strong>HTML</strong> dhe
    <span class="highlight">CSS</span>.
  </p>
</div>
```

- **`<div>`** — merr gjithë rreshtin (block).
- **`<span>`** — rri brenda rreshtit (inline), përdoret për të "veçuar" vetëm pjesë teksti.

Krahaso me tags semantike, që komunikojnë **qëllimin** e pjesës:

```html
<header>
  <img src="foto.jpg" alt="Foto e nxënësit">
  <h1>Emri Mbiemri</h1>
</header>

<nav id="main-nav">
  <a href="https://www.jcoders.com">jCoders</a>
  <a href="https://www.google.com" target="_blank">Google</a>
</nav>

<section class="rreth-meje">
  <h2>Kush jam unë</h2>
  <p>Unë jam nxënës në jCoders...</p>
</section>

<footer>
  <p>&copy; 2026 jCoders</p>
</footer>
```

> 💡 Rregull i përgjithshëm: përdor tag semantik kur ekziston një që përshtatet (`<nav>`, `<footer>`...), dhe rezervoje `<div>`/`<span>` për "hooks" të thjeshtë stilizimi (`class="highlight"`) ose kur asnjë semantik nuk përshtatet.

---

## 5. `class` kundrejt `id`

```html
<p>Unë mësoj <span class="highlight">HTML</span> dhe <span class="highlight">CSS</span>.</p>

<nav id="main-nav">
  <a href="#">jCoders</a>
</nav>
```

- **`class="highlight"`** — përdoret te **dy** `<span>` të ndryshme; CSS-ja `.highlight { background: yellow; }` do i stilizojë të dyja njëkohësisht.
- **`id="main-nav"`** — **unik**, vetëm një `<nav>` në gjithë faqen mund ta ketë; përdoret kur duam të synojmë atë element **specifik**, jo një grup.

---

## 6. Tabelat — `<table>`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, `<td>`

```html
<table>
  <thead>
    <tr>
      <th>Dita</th>
      <th>Aktiviteti</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>E Hënë</td>
      <td>HTML</td>
    </tr>
    <tr>
      <td>E Mërkurë</td>
      <td>CSS</td>
    </tr>
    <tr>
      <td>E Premte</td>
      <td>Projekt</td>
    </tr>
  </tbody>
</table>
```

- **`<tr>`** — një rresht (table row).
- **`<th>`** — qeliza e **titullit** të kolonës.
- **`<td>`** — qeliza e të dhënave normale.
- **`<thead>`/`<tbody>`** — grupojnë titujt veç nga trupi, që të mund t'i stilizojmë ndryshe më vonë me CSS.

> ⚠️ Tabelat përdoren për të dhëna që **vërtet** kanë rreshta/kolona (si oraret) — jo si mjet për të pozicionuar elemente të përgjithshme në faqe.

---

## Përmbledhje e shpejtë

```
1. <!DOCTYPE html> + <html> + <head> (info) + <body> (çka shihet)
2. h1-h6 = hierarki rëndësie, jo madhësi; strong=rëndësi, em=theks; br=thyerje rreshti
3. a href/target -- ku çon lidhja; img src/alt -- alt është domosdoshëm
4. div/span = neutral; header/nav/section/footer = kanë kuptim (semantikë)
5. class = për shumë elemente; id = unik, një element i vetëm
6. table/thead/tbody/tr/th/td -- vetëm për të dhëna tabelare reale
```

---

## Fjalë të shkurtra

- **Semantikë** — kur një tag HTML komunikon kuptimin/qëllimin e përmbajtjes, jo vetëm strukturën
- **Accessibility** — sa e përdorshme është faqja për të gjithë, përfshi përdorues me screen readers
- **Block** — element që merr gjithë gjerësinë e disponueshme (p.sh. `<div>`)
- **Inline** — element që rri brenda rrjedhës së tekstit (p.sh. `<span>`)

---

## 🎯 Sfida jote (pikë ekstra)

Shkruaj (jo vetëm shpjego) një mini-faqe HTML `sfida.html`, e ndërtuar vetëm me elementet e këtij udhëzuesi:

1. Skelet i plotë (`<!DOCTYPE html>`, `<head>` me `<meta charset>` dhe `<title>`, `<body>`).
2. Të paktën **dy** tags semantike (`<header>`, `<nav>`, `<section>` ose `<footer>`).
3. Një `<h1>` dhe një `<h2>`, me një fjalë të theksuar me `<strong>` dhe një me `<em>`.
4. Një `<img>` me `alt` kuptimplotë, dhe dy `<a>` — njëra prej tyre me `target="_blank"`.
5. Një `class` e përdorur te **dy** elemente të ndryshme, dhe një `id` e përdorur te **vetëm një** element.
6. Një `<table>` me `<thead>`/`<tbody>`, me të paktën 2 rreshta të dhënash.
