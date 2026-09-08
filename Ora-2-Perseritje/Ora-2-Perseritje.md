# Kodi i Saktë për Klasë — kopjo/ngjit direkt
### Çdo hap tregon FILE-in e PLOTË siç duhet të duket pas atij hapi. Thjesht zëvendëso përmbajtjen e file-it me këtë.
*(Pjesa e listave/dl u hoq — kaluam direkt nga imazhet te div/span.)*

---

# PJESA 1 — HTML (`index.html`)

## H1 — Struktura bazë

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

---

## H2 — Titujt (h1, h2) + `<br>`

```html
<!DOCTYPE html>
<html lang="sq">
<head>
  <meta charset="UTF-8">
  <title>Karta Ime Personale</title>
</head>
<body>

  <h1>Emri Mbiemri</h1>

  <h2>Kush jam unë</h2>
  <p>
    Unë jam nxënës në jCoders.<br>
    Po mësoj HTML dhe CSS.
  </p>

</body>
</html>
```

---

## H3 — `<strong>` dhe `<em>`

```html
<!DOCTYPE html>
<html lang="sq">
<head>
  <meta charset="UTF-8">
  <title>Karta Ime Personale</title>
</head>
<body>

  <h1>Emri Mbiemri</h1>

  <h2>Kush jam unë</h2>
  <p>
    Unë jam nxënës në jCoders dhe po mësoj <strong>HTML</strong> dhe <em>CSS</em>.<br>
    Kjo është një faqe që po e ndërtoj hap pas hapi në klasë.
  </p>

</body>
</html>
```

---

## H4 — Lidhjet `<a>`

```html
<!DOCTYPE html>
<html lang="sq">
<head>
  <meta charset="UTF-8">
  <title>Karta Ime Personale</title>
</head>
<body>

  <h1>Emri Mbiemri</h1>

  <h2>Kush jam unë</h2>
  <p>
    Unë jam nxënës në jCoders dhe po mësoj <strong>HTML</strong> dhe <em>CSS</em>.<br>
    Kjo është një faqe që po e ndërtoj hap pas hapi në klasë.
  </p>

  <h2>Linqet e mia</h2>
  <a href="https://www.jcoders.com">jCoders</a>
  <a href="https://www.google.com" target="_blank">Google</a>
  <a href="https://www.github.com">GitHub</a>

</body>
</html>
```

---

## H5 — Imazhi `<img>`

```html
<!DOCTYPE html>
<html lang="sq">
<head>
  <meta charset="UTF-8">
  <title>Karta Ime Personale</title>
</head>
<body>

  <img src="foto.jpg" alt="Foto e nxënësit">

  <h1>Emri Mbiemri</h1>

  <h2>Kush jam unë</h2>
  <p>
    Unë jam nxënës në jCoders dhe po mësoj <strong>HTML</strong> dhe <em>CSS</em>.<br>
    Kjo është një faqe që po e ndërtoj hap pas hapi në klasë.
  </p>

  <h2>Linqet e mia</h2>
  <a href="https://www.jcoders.com">jCoders</a>
  <a href="https://www.google.com" target="_blank">Google</a>
  <a href="https://www.github.com">GitHub</a>

</body>
</html>
```
*(Nxënësit duhet të kenë një foto `foto.jpg` në të njëjtin folder me `index.html`, ose përdorni ndonjë foto shembull.)*

---

## H6 — `<div>`, `<span>`, class

```html
<!DOCTYPE html>
<html lang="sq">
<head>
  <meta charset="UTF-8">
  <title>Karta Ime Personale</title>
</head>
<body>

  <img src="foto.jpg" alt="Foto e nxënësit">

  <h1>Emri Mbiemri</h1>

  <div class="rreth-meje">
    <h2>Kush jam unë</h2>
    <p>
      Unë jam nxënës në jCoders dhe po mësoj <strong>HTML</strong> dhe <span class="highlight">CSS</span>.<br>
      Kjo është një faqe që po e ndërtoj hap pas hapi në klasë.
    </p>
  </div>

  <h2>Linqet e mia</h2>
  <a href="https://www.jcoders.com">jCoders</a>
  <a href="https://www.google.com" target="_blank">Google</a>
  <a href="https://www.github.com">GitHub</a>

</body>
</html>
```
*(`em` u zëvendësua me `span class="highlight"` te CSS-ja për të pasur një `span` real.)*

---

## H7 — Semantics (header, nav, section, footer)

```html
<!DOCTYPE html>
<html lang="sq">
<head>
  <meta charset="UTF-8">
  <title>Karta Ime Personale</title>
</head>
<body>

  <header>
    <img src="foto.jpg" alt="Foto e nxënësit">
    <h1>Emri Mbiemri</h1>
  </header>

  <nav id="main-nav">
    <a href="https://www.jcoders.com">jCoders</a>
    <a href="https://www.google.com" target="_blank">Google</a>
    <a href="https://www.github.com">GitHub</a>
  </nav>

  <section class="rreth-meje">
    <h2>Kush jam unë</h2>
    <p>
      Unë jam nxënës në jCoders dhe po mësoj <strong>HTML</strong> dhe <span class="highlight">CSS</span>.<br>
      Kjo është një faqe që po e ndërtoj hap pas hapi në klasë.
    </p>
  </section>

  <footer>
    <p>&copy; 2026 jCoders</p>
  </footer>

</body>
</html>
```

---

## H8 — Tabela

```html
<!DOCTYPE html>
<html lang="sq">
<head>
  <meta charset="UTF-8">
  <title>Karta Ime Personale</title>
</head>
<body>

  <header>
    <img src="foto.jpg" alt="Foto e nxënësit">
    <h1>Emri Mbiemri</h1>
  </header>

  <nav id="main-nav">
    <a href="https://www.jcoders.com">jCoders</a>
    <a href="https://www.google.com" target="_blank">Google</a>
    <a href="https://www.github.com">GitHub</a>
  </nav>

  <section class="rreth-meje">
    <h2>Kush jam unë</h2>
    <p>
      Unë jam nxënës në jCoders dhe po mësoj <strong>HTML</strong> dhe <span class="highlight">CSS</span>.<br>
      Kjo është një faqe që po e ndërtoj hap pas hapi në klasë.
    </p>
  </section>

  <section>
    <h2>Orari im javor</h2>
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
  </section>

  <footer>
    <p>&copy; 2026 jCoders</p>
  </footer>

</body>
</html>
```

**Ky është file-i final i HTML-së** — nuk ndryshon më deri në fund. Nga këtu e tutje punojmë vetëm te `style.css`.

---

# PJESA 2 — CSS (`style.css`)

## C1 — Si shtohet CSS (demo, jo pjesë e file-it final)

Bëj këtë demo **direkt në `index.html`**, pastaj hiqe:

**1) Inline** (shto përkohësisht te `<h1>`):
```html
<h1 style="color: red;">Emri Mbiemri</h1>
```

**2) Internal** (shto përkohësisht te `<head>`):
```html
<style>
  h1 {
    color: blue;
  }
</style>
```

**3) External** — kjo mbetet përgjithmonë. Shto te `<head>`:
```html
<link rel="stylesheet" href="style.css">
```
Dhe krijo file-in `style.css` (bosh për momentin). Hiq inline dhe internal nga hapat 1 dhe 2.

---

## C2 — Selektorët (element, class, id)

`style.css`:
```css
body {
  font-family: Arial, sans-serif;
}

.highlight {
  background-color: yellow;
}

#main-nav {
  background-color: lightgray;
}
```

---

## C3 — Tipografia (pjesa 1)

```css
body {
  font-family: Arial, sans-serif;
}

.highlight {
  background-color: yellow;
}

#main-nav {
  background-color: lightgray;
}

header {
  text-align: center;
}

h1, h2 {
  font-family: Georgia, serif;
  color: #2c3e50;
}
```

---

## C4 — Tipografia (pjesa 2)

```css
body {
  font-family: Arial, sans-serif;
}

.highlight {
  background-color: yellow;
}

#main-nav {
  background-color: lightgray;
}

header {
  text-align: center;
}

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

---

## C5 — Box Model (padding, border, margin)

```css
body {
  font-family: Arial, sans-serif;
}

.highlight {
  background-color: yellow;
}

#main-nav {
  background-color: lightgray;
}

header {
  text-align: center;
}

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

.rreth-meje {
  padding: 20px;
  border: 2px solid #2c3e50;
  margin: 10px 0;
}
```

---

## C6 — Box-sizing (problemi + zgjidhja)

**Pa box-sizing (shiko problemin — width "rritet"):**
```css
.rreth-meje {
  width: 300px;
  padding: 20px;
  border: 2px solid #2c3e50;
  margin: 10px 0;
}
```

**Me box-sizing (zgjidhja — width mbetet 300px):**
```css
.rreth-meje {
  width: 300px;
  padding: 20px;
  border: 2px solid #2c3e50;
  margin: 10px 0;
  box-sizing: border-box;
}
```
*(Vazhdo me versionin e dytë, me `box-sizing`.)*

---

## C7 — Display: inline-block (navbar horizontale)

Shto/ndrysho vetëm rregullin `nav a`:
```css
nav a {
  display: inline-block;
  padding: 8px 15px;
  text-decoration: none;
  color: #2c3e50;
}
```

---

## C8 — Box-shadow (foto)

Shto këtë rregull të ri:
```css
img {
  width: 150px;
  border-radius: 50%;
  box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.3);
}
```

---

## C9 — Stilizimi i tabelës

Shto këtë rregull të ri:
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

---

## `style.css` — FILE-I FINAL I PLOTË (C1–C9 së bashku)

```css
body {
  font-family: Arial, sans-serif;
}

.highlight {
  background-color: yellow;
}

#main-nav {
  background-color: lightgray;
}

header {
  text-align: center;
}

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

.rreth-meje {
  width: 300px;
  padding: 20px;
  border: 2px solid #2c3e50;
  margin: 10px 0;
  box-sizing: border-box;
}

nav a {
  display: inline-block;
  padding: 8px 15px;
  text-decoration: none;
  color: #2c3e50;
}

img {
  width: 150px;
  border-radius: 50%;
  box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.3);
}

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

## C10 — Rekap final
Asnjë kod i ri — hap `index.html` në browser dhe shiko rezultatin e plotë (Kartën Personale). Kjo është faqja që prezantojnë nxënësit.
