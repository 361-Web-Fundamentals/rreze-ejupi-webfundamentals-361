# Aktiviteti 25&26 — Flexbox
## Udhëzues

---

Deri tani i kemi ndërtuar faqet tona duke lënë elementet të vendosen natyrshëm, njëri poshtë tjetrit — çdo `<div>` merr rreshtin e vet. Kjo funksionon, por nuk na jep asnjë kontroll të vërtetë mbi renditjen: si t'i vendosim elementet krah për krah, si t'i qendërzojmë, si t'i shpërndajmë hapësirën mes tyre. Sot mësojmë **Flexbox** — mjeti që na jep pikërisht këtë kontroll.

Ky udhëzues shpjegon konceptet dhe hapat që i ndoqëm, në rendin e duhur.

---

## 1. Çka është Flexbox-i?

Për shumë kohë, e vetmja mënyrë për të ndërtuar layout-e (dizajne) më komplekse në web ka qenë `float` — një property që fillimisht ishte menduar për diçka krejt tjetër (të lëshosh tekst rreth një imazhi, si në një revistë). Përdorimi i `float`-eve për layout-e të tëra shpejt bëhet i vështirë dhe i paparashikueshëm.

Për këtë arsye, W3 (organizata që përcakton standardet e web-it) krijoi **Flexbox** ("kutia fleksibile") — një mënyrë e re, e menduar posaçërisht për të kontrolluar radhitjen, drejtimin, rendin dhe madhësinë e elementeve brenda një kontejneri.

> 💡 Flexbox nuk e zëvendëson gjithçka që dinim deri tani (p.sh. `display: block`) — thjesht na jep një mënyrë shumë më të fuqishme për të organizuar elementet kur na duhet kontroll mbi renditjen e tyre.

---

## 2. Flex Container dhe Flex Items

Flexbox punon me dy lloje "kutish":

- **Flex Container** — një element që "mban" brenda tij elementet e tjera dhe kontrollon si radhiten ato.
- **Flex Item** — çdo element HTML që është fëmijë direkt i një flex container quhet flex item.

```html
<div class="container">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>
```

Këtu `.container` është flex container-i, ndërsa tre `.item`-at brenda tij janë flex items. Items mund të manipulohen edhe individualisht, por zakonisht është container-i ai që vendos si organizohen fëmijët e tij.

---

## 3. Krijimi i një Flex Container — `display: flex`

Për ta bërë një element flex container, i shtojmë property-n `display: flex` (ose `display: inline-flex`).

```css
.container {
  display: flex;
}
```

- **`flex`** — krijon një flex container të nivelit **block** (merr gjithë gjerësinë e prindit, si një `<div>` normal).
- **`inline-flex`** — krijon një flex container **inline** (merr vetëm aq hapësirë sa i duhet përmbajtjes).

Në momentin që shtojmë `display: flex`, fëmijët e atij elementi automatikisht radhiten **krah për krah** (horizontalisht), pa asnjë property tjetër.

> ⚠️ `display: flex` prek vetëm **fëmijët direkt** të container-it, jo nipërit (fëmijët e fëmijëve).

---

## 4. Flex Direction

`flex-direction` përcakton **drejtimin** në të cilin radhiten elementet brenda container-it.

```css
.container {
  display: flex;
  flex-direction: row;
}
```

Vlerat e mundshme:

- **`row`** (default) — i rendit elementet horizontalisht, nga e majta në të djathtë.
- **`row-reverse`** — horizontalisht, nga e djathta në të majtë.
- **`column`** — vertikalisht, nga lart poshtë.
- **`column-reverse`** — vertikalisht, nga poshtë lart.

---

## 5. Flex Wrap

Kur elementet brenda container-it nuk kanë hapësirë të mjaftueshme në një rresht të vetëm, `flex-wrap` përcakton nëse ato lejohen të kalojnë në rresht të ri.

```css
.container {
  display: flex;
  flex-wrap: wrap;
}
```

- **`nowrap`** (default) — të gjitha elementet mbeten në një rresht/kolonë të vetme, edhe nëse "shtrydhen".
- **`wrap`** — elementet kalojnë në rreshta shtesë, nga lart poshtë, kur nuk ka hapësirë.
- **`wrap-reverse`** — njësoj si `wrap`, por rreshtat shtesë shtohen nga poshtë lart.

---

## 6. Justify Content

`justify-content` kontrollon si shpërndahen elementet përgjatë **boshtit kryesor** (main axis) — boshti në të cilin lëviz `flex-direction`.

```css
.container {
  display: flex;
  justify-content: center;
}
```

Vlerat më të përdorura:

- **`flex-start`** (default) — elementet mblidhen në fillim të container-it.
- **`flex-end`** — mblidhen në fund.
- **`center`** — mblidhen në mes.
- **`space-between`** — hapësirë e barabartë **mes** elementeve (asgjë në skaje).
- **`space-around`** — hapësirë e barabartë **rreth** çdo elementi.
- **`space-evenly`** — hapësirë plotësisht e barabartë kudo, përfshi skajet.

---

## 7. Align Items

`align-items` kontrollon si radhiten elementet përgjatë **boshtit sekondar** (cross axis) — boshti pingul me `flex-direction`.

```css
.container {
  display: flex;
  align-items: center;
}
```

Vlerat më të përdorura:

- **`flex-start`** — elementet mblidhen në krye të boshtit sekondar.
- **`flex-end`** — mblidhen në fund të tij.
- **`center`** — qendërzohen.
- **`stretch`** (default) — elementet zgjaten sa e gjithë hapësira e disponueshme e boshtit sekondar.
- **`baseline`** — radhiten sipas vijës bazë të tekstit të tyre.

> ⚠️ **Kujdes!** Cili bosht është "horizontal" dhe cili "vertikal" ndryshon sipas `flex-direction`-it:
>
> - Në `flex-direction: row` → **horizontal = `justify-content`**, **vertikal = `align-items`**
> - Në `flex-direction: column` → **horizontal = `align-items`**, **vertikal = `justify-content`**

---

## 8. Align Content

`align-content` përdoret **vetëm** kur container-i ka **më shumë se një rresht** (pra kur `flex-wrap: wrap` është aktiv dhe elementet vërtet kalojnë në disa rreshta). Ai përcakton si pozicionohet çdo rresht brenda container-it, jo elementet brenda një rreshti.

```css
.container {
  display: flex;
  flex-wrap: wrap;
  align-content: space-between;
}
```

Vlerat: `flex-start`, `flex-end`, `center`, `stretch`, `space-between`, `space-around`.

---

## 9. Flex Order

Me `order` mund të ndryshojmë **renditjen vizuale** të një flex item-i, pa prekur fare renditjen e tij në kodin HTML.

```css
.item-3 {
  order: -1;
}
```

Të gjithë items fillimisht kanë `order: 0`. Elementi me `order` më të vogël shfaqet më parë; me `order` më të madh, më pas. Kjo e bën shumë të lehtë, p.sh., të nxjerrësh një kartë "të veçantë" e para pa e lëvizur fare në HTML.

---

## 10. `align-self` dhe `justify-self` (përjashtim për një item të vetëm)

Ndonjëherë duam që **vetëm një** flex item të sillet ndryshe nga të tjerët, pa ndryshuar rregullin e përgjithshëm të container-it.

```css
.item-2 {
  align-self: flex-end;
}
```

- **`align-self`** — mbivendos `align-items` të container-it, por **vetëm** për këtë item (boshti sekondar).
- **`justify-self`** — mbivendos rreshtimin në boshtin kryesor, por vetëm për këtë item (mbahet parasysh se suporti i tij në Flexbox është më i kufizuar se te `align-self`; për raste të tilla shpesh mjafton `margin: auto` në një drejtim).

---

## Ushtrimi që bëmë në klasë

Praktikuam konceptet me **Flexbox Froggy** (flexboxfroggy.com) — një lojë ku duhet të çosh secilën bretkosë tek zambaku (lily pad) i saj duke shkruar property-t e sakta të Flexbox-it (`justify-content`, `align-items`, `flex-direction`, etj.) në panelin e kodit. Çdo nivel shton nga një property të ri, në të njëjtin rend siç i mësuam sot.

---

## Përmbledhje e shpejtë

```
1. Flexbox = alternativë ndaj float-eve për kontroll të plotë mbi radhitjen e elementeve
2. Flex container = display: flex (ose inline-flex); flex items = fëmijët e tij direkt
3. flex-direction: row | row-reverse | column | column-reverse -- drejtimi i boshtit kryesor
4. flex-wrap: nowrap (default) | wrap | wrap-reverse -- a kalojnë items në rreshta të rinj
5. justify-content -- rreshtimi përgjatë boshtit KRYESOR (main axis)
6. align-items -- rreshtimi përgjatë boshtit SEKONDAR (cross axis)
7. Në row: justify-content=horizontal, align-items=vertikal. Në column: e kundërta!
8. align-content -- pozicionon rreshtat (jo items) kur ka flex-wrap: wrap
9. order -- ndryshon renditjen VIZUALE e një item-i, pa prekur HTML-in
10. align-self / justify-self -- mbivendosin rregullin e container-it, vetëm për një item
```

---

## Fjalë të shkurtra

- **Flex Container** — elementi me `display: flex`, që kontrollon radhitjen e fëmijëve të vet
- **Flex Item** — një fëmijë direkt i një flex container
- **Main axis (boshti kryesor)** — boshti në drejtimin e `flex-direction`; kontrollohet nga `justify-content`
- **Cross axis (boshti sekondar)** — boshti pingul me boshtin kryesor; kontrollohet nga `align-items`
- **`flex-direction`** — drejtimi (row/column) në të cilin radhiten items
- **`flex-wrap`** — a lejohet kalimi i items në rreshta/kolona shtesë
- **`justify-content`** — shpërndarja e items përgjatë boshtit kryesor
- **`align-items`** — shpërndarja e items përgjatë boshtit sekondar
- **`order`** — renditja vizuale e një item-i, e pavarur nga renditja në HTML

---

## 🎯 Sfida jote (pikë ekstra)

Ndërto një rresht të vogël me **3 karta** (secila me një `<div>` që përmban një titull dhe një paragraf), duke përdorur vetëm Flexbox:

1. Krijo një `.container` me `display: flex`.
2. Shpërndaji 3 kartat në mënyrë të barabartë përgjatë rreshtit, me hapësirë mes tyre (`justify-content`).
3. Qendërzoji vertikalisht (`align-items`), edhe nëse kartat kanë lartësi të ndryshme.
4. Shto `flex-wrap: wrap`, ngushto dritaren e browser-it dhe vëzhgo si kalojnë kartat në rresht të ri kur s'ka më hapësirë.
5. (Bonus) Përdor `order` për ta bërë kartën e mesit të shfaqet **e para**, pa e prekur fare renditjen në HTML.
