# Ora 3 — Forms
## Udhëzues

---

Deri tani faqet tona kanë qenë "njëkahëshe" — ne i shfaqim informacione, por përdoruesi nuk mund të na dërgojë asgjë prapa. **Forms** (formularët) e zgjidhin këtë: na japin një mënyrë të mbledhim të dhëna nga përdoruesi — emër, email, zgjedhje, tekst i lirë — përmes elementeve HTML të dedikuara për input.

Ky udhëzues shpjegon konceptet pas elementeve që përdorëm te `Ora-3-Forms`, `Ora-4-Contact-Form` dhe `Ora-5-Detyra-Form`.

---

## 1. Elementi `<form>`

```html
<form>
  ...
</form>
```

`<form>` është "kutia" që mbështjell **të gjitha** fushat e një formulari — pa të, browser-i nuk e di cilat inpute i përkasin bashkë. Në praktikë reale, `<form>` mund të ketë edhe `action` (ku dërgohen të dhënat) dhe `method` (si dërgohen, p.sh. `POST`) — ne ende s'kemi një server ku t'i dërgojmë, prandaj i lëmë bosh ose `action="#"` për momentin dhe testojmë vetëm pamjen dhe sjelljen në browser.

---

## 2. `<label>` i lidhur me `<input>`

```html
<label for="emri">Emri:</label>
<input type="text" id="emri" name="emri">
```

`for="emri"` te `<label>` duhet të përputhet saktësisht me `id="emri"` te `<input>`. Kjo lidhje nuk është vetëm kozmetike:

- Kur klikon mbi **tekstin** e label-it, fokusi shkon automatikisht te inputi (provo — shumë e dobishme për checkbox/radio, ku "kutia" e klikimit është e vogël).
- Screen readers e lexojnë label-in si përshkrim të fushës — pa këtë lidhje, dikush që përdor screen reader nuk do dinte çka pritet në atë fushë.

> ⚠️ `id` duhet të jetë **unik** në faqe — nëse dy inpute kanë të njëjtin `id`, lidhja `for` bëhet e paqartë dhe mund të mos funksionojë siç pritet.

---

## 3. Llojet e `<input type="">`

E njëjta tag `<input>` sillet krejt ndryshe varësisht `type`:

- **`text`** — një rresht tekst i lirë, pa validim të veçantë.
- **`email`** — dukshëm njësoj si `text`, por browser-i **e vlerëson formatin** vetë (kërkon një `@` etj.) para se ta lërë formularin të "submitohet", nëse ke `required`.
- **`password`** — çdo karakter i shkruar shfaqet i fshehur (`•••`), për arsye privatësie — vlera reale mbetet e njëjtë "nën kapuçin".
- **`radio`** — zgjedh **VETËM NJËRËN** nga disa opsione. Që browser-i t'i njohë si grup (dhe të lejojë vetëm një të zgjedhur njëherë), të gjitha radio-t e grupit duhet të kenë **të njëjtin `name`** (p.sh. `name="gjinia"`), edhe pse secili ka `id` të ndryshëm.
- **`checkbox`** — zgjedh **SA TË DUASH** nga disa opsione, të pavarura nga njëra-tjetra — nuk kanë nevojë të ndajnë `name` mes tyre, sepse secili checkbox është zgjedhje e vetvetishme (po/jo).

```html
<label for="mashkull">Mashkull</label>
<input type="radio" id="mashkull" name="gjinia" value="mashkull">

<label for="femer">Femër</label>
<input type="radio" id="femer" name="gjinia" value="femer">
```

> 💡 Nëse harron ta japësh të njëjtin `name` te dy radio që duhet të jenë "ose-ose", browser-i i trajton si dy pyetje krejt të veçanta — mund të zgjedhësh të dyja njëkohësisht, gjë që s'ka kuptim (p.sh. "Mashkull" DHE "Femër" të dyja të zgjedhura).

---

## 4. Atributet e rëndësishme të `<input>`

- **`placeholder`** — tekst gri "udhëzues" brenda fushës (p.sh. "Shkruaj emailin"); **zhduket** sapo fillon të shkruash dhe **NUK dërgohet** si vlerë — është vetëm një këshillë vizuale, jo zëvendësim për label.
- **`value`** — vlera reale e fushës. Te `text`/`email` zakonisht fillon bosh (plotësohet nga përdoruesi); te `radio`/`checkbox`, `value` përcakton **çka dërgohet** nëse ajo opsion është e zgjedhur.
- **`required`** — i thotë browser-it të mos e lërë formularin të "submitohet" pa e plotësuar këtë fushë.
- **`name`** — **kyçi** që përdoret kur të dhënat dërgohen diku (te një server). Pa `name`, edhe nëse fusha duket mirë dhe përdoruesi e plotëson, ajo vlerë **nuk dërgohet fare**. `id` shërben për HTML/CSS/label; `name` shërben për vetë dërgimin e të dhënave — shpesh na duhen **të dyja**, me role të ndryshme.

---

## 5. `<textarea>` — tekst i lirë me shumë rreshta

```html
<label for="bio">Biografia:</label>
<textarea id="bio" name="bio" rows="4" placeholder="Shkruaj diçka..."></textarea>
```

Ndryshe nga `<input type="text">` (një rresht i vetëm), `<textarea>` lejon tekst të gjatë me shumë rreshta — e përdorëm për "Biografia" te `Ora-3-Forms` dhe për "Mesazhi" te `Ora-4-Contact-Form`. `rows` përcakton lartësinë fillestare (sa rreshta duken pa u rrolluar).

---

## 6. `<select>` dhe `<option>` — zgjedhje nga një listë fikse

```html
<select id="fusha" name="fusha">
  <option value="it">Teknologji Informacioni</option>
  <option value="marketing">Marketing</option>
</select>
```

Përdoret kur ka një grup **fiks** opsionesh dhe duam vetëm një dropdown kompakt (siç u përdor te `Ora-5-Detyra-Form` për "Fusha e Interesit"). `value` te çdo `<option>` është ajo që dërgohet nëse zgjidhet, ndërsa teksti mes tags është ajo që **shihet** në dropdown — të dyja mund të jenë të ndryshme.

---

## 7. Butonat — `type="submit"` kundrejt `type="reset"`

```html
<button type="submit">Dërgo</button>
<button type="reset">Pastro</button>
```

- **`submit`** — dërgon (ose provon të dërgojë) formularin.
- **`reset`** — i kthen **të gjitha** fushat e formularit në vlerat e tyre fillestare (fshin çka ka shkruar përdoruesi).

> ⚠️ Nëse një `<button>` brenda një `<form>` **s'ka fare** `type`, browser-i e trajton si `submit` nga default-i — kjo shpesh befason kur ke disa butona brenda të njëjtit formular.

---

## 8. Stilizimi i formave me CSS

Konceptet janë të njëjta si te Ora 2 (selektorë, box model) — vetëm i aplikojmë te elementet e formularit:

```css
.fusha-teksti {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 6px;
  box-sizing: border-box;
}
```

Te `Ora-5-Detyra-Form` i vendosëm të njëjtën klasë `.fusha-teksti` te `text`, `email`, `password`, `textarea` DHE `select` — kështu i stilizojmë të gjitha njësoj (gjerësi e plotë, padding, kufij të rrumbullakosur) pa përsëritur të njëjtin rregull për secilën veç e veç. Radio/checkbox mbeten jashtë kësaj klase (marrin klasën `.kutize`) sepse duken dhe sillen ndryshe — nuk kanë kuptim me `width: 100%`.

---

## Përmbledhje e shpejtë

```
1. <form> mbështjell të gjitha fushat që i përkasin bashkë
2. label for="x" + input id="x" -- lidhje për accessibility, jo vetëm pamje
3. input type: text | email | password | radio | checkbox -- secili sillet ndryshe
4. radio: i njëjti name = zgjidh VETËM NJËRIN; checkbox: pa name të përbashkët = zgjidh SA DO
5. placeholder = këshillë vizuale (s'dërgohet); value = e dhëna reale; required = validim; name = kyçi për dërgim
6. textarea = tekst i lirë me shumë rreshta; select+option = listë fikse zgjedhjesh
7. button type="submit" (dërgon) kundrejt type="reset" (pastron); pa type = submit nga default-i
8. Klasë e përbashkët (p.sh. .fusha-teksti) = stilizim konsistent pa përsëritje
```

---

## Fjalë të shkurtra

- **`<form>`** — elementi që grupon fushat e një formulari
- **`for` / `id`** — çifti që lidh një `<label>` me inputin e tij
- **`name`** — atributi që përcakton çka dërgohet kur formulari "submitohet"
- **Grup radio** — disa `<input type="radio">` me të njëjtin `name`, ku vetëm një mund të zgjidhet
- **`<select>` / `<option>`** — dropdown me një listë fikse zgjedhjesh
- **`submit` / `reset`** — dërgon formularin / e rikthen në gjendjen fillestare

---

## 🎯 Sfida jote (pikë ekstra)

Hap formularin te `Ora-5-Detyra-Form` (`detyra.html`) dhe, pa e rishkruar krejt formularin, bëj këtë:

1. Shpjego me shkrim (koment `<!-- ... -->` në krye të file-it): cilat **tre** fusha të atij formulari do të humbnin vlerën e tyre gjatë dërgimit nëse do u hiqej `name`, edhe nëse `id` mbetet — dhe pse `id` vetëm nuk mjafton.
2. Shto **një** fushë të re `<select>` për "Qyteti", me të paktën 3 `<option>` (p.sh. Prishtinë, Prizren, Pejë), duke përdorur klasën `fusha-teksti` që të përshtatet me stilin ekzistues.
3. Shpjego pse `value`-t që zgjodhe për `<option>`-at e tua janë të përshtatshme (p.sh. pa hapësira/shkronja speciale) për t'u dërguar si të dhëna.
