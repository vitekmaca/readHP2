# Tajemná komnata 🪄

Interaktivní průvodce druhým rokem v Bradavicích, pro předčítání dětem. Druhý díl stejné appky jako [readHP](https://github.com/vitekmaca/readHP) — stejná struktura, stejné chování, nový obsah. Postavené podle [readLOTR](https://github.com/brychtaj/readLOTR) — fanouškovský projekt, žádná oficiální appka.

## Aktuální stav

- **Postavy:** 31 v appce, **15 má portrét** — převzaté rovnou z dílu 1 u postav, co se vrací (Harry, Ron, Hermiona, Hagrid, Brumbál, McGonagallová, Snape, Neville, Nick, Filch, Fred a George, Percy, Madame Pomfreyová, Voldemort, Draco). Zbylých 16 nových postav zatím portrét nemá (viz seznam níže — tentokrát bez omezení na to, ke komu máme hezkou grafiku).
- **Ilustrace kapitol:** zatím žádná z 18.
- **Audio:** zatím žádné namluvené kapitoly.

Appka funguje úplně stejně jako díl 1 i bez obrázků a audia — postavy mají místo portrétu ikonku, kapitoly bez nahrávky mají vlastní hlášku a ilustrace prostě chybí. Vše se doplní postupně stejným způsobem jako u prvního dílu.

## Co appka umí

- 🎧 **Namluvené kapitoly** — audiopřehrávač u každé kapitoly, doplňuje se postupně jak přibývají nahrávky (soubory v `assets/audio/`).
- 🧙 **Postavy** s portréty a „příběhem zatím", který se dopisuje podle toho, co už bylo přečteno.
- 🖼️ **Malovaná ilustrace** klíčového momentu ke každé z 18 kapitol.
- 📖 **Dva režimy**: *Rodiče* (shrnutí, na co se zaměřit, otázky pro děti, „metr strašidelnosti" ⚠️) a *Děti* (bez spoilerů — jen „co bylo minule" a kvízy).
- 🌍 **Svět** — Tajemná komnata, Mnoholičný lektvar, Fénix, hadí jazyk, národy kouzelnického světa (teď i s domácími skřítky) a časová osa navazující na konec prvního dílu.
- 🌗 Světlý/tmavý motiv v hlavičce.

Appka je jen česky (žádný jazykový přepínač). Jména míst a postav drží oficiální překlad **Pavla Medka** (Bradavice, Nebelvír, Brumbál, Zlatoslav Lockhart, Kornelius Popletal…) — u pár méně jistých jmen (viz níže) to prosím ověř podle svého výtisku. Appka má **vlastní, nezávislý postup čtení** (jiný localStorage klíč než díl 1) — i když jsou obě appky na stejné doméně `vitekmaca.github.io`, progres se nijak nemíchá.

## ⚠️ Autorská práva — proč musí repo zůstat soukromé

15 portrétů (postavy vracející se z dílu 1) je převzato přímo z `readHP` — naskenované/vyfocené stránky z **Jim Kayho Illustrated Edition** (Bloomsbury/Scholastic), komerční chráněné dílo, ne volně šiřitelné. Platí úplně stejné pravidlo jako u dílu 1: použití je v pořádku jen jako **osobní, neveřejná appka pro rodinu**. Repo **nesmí** být veřejné a GitHub Pages **nesmí** být zapnuté, dokud tyhle obrázky v `assets/` jsou.

## Struktura projektu

Identická s dílem 1:

- `index.html` — **sestavená appka** (jeden soubor), otevírá se lokálně.
- `tajemna-komnata.template.html` — **zdrojová šablona** (HTML/CSS/JS + veškerý text). Tady se edituje obsah.
- `assets/` — obrázky a audio (zatím prázdné):
  - `portraits/<id>.jpg` — portréty postav (vkládají se do `index.html` při buildu),
  - `scenes/<n>.jpg` — ilustrace kapitol `1`–`18` (vkládají se při buildu),
  - `audio/<gi>.m4a` — namluvené kapitoly (odkazované, ne vkládané do HTML).
- `build.mjs` — build skript (Node), stejný princip jako u dílu 1.

## Build

```bash
node build.mjs
```

Skript vezme `tajemna-komnata.template.html`, nahradí tokeny obrázků z `assets/` (jako base64 data URI) a zapíše `index.html`. Chybějící obrázky jen vypíše do konzole, build kvůli nim neselže.

---

## Co přesně potřebuju od tebe (obrázky)

Appka bez obrázků nezobrazí nic u postav a scén kapitol (jen ikonku/prázdno). Z **49 souborů** celkem (18 scén + 31 portrétů) už 15 portrétů je hotovo (převzato z dílu 1), zbývá **34** — `build.mjs` ale běží i s částí chybějící.

### 18 ilustrací kapitol

`assets/scenes/1.jpg` … `assets/scenes/18.jpg` — malovaná scéna klíčového momentu dané kapitoly, orientace na šířku. Popisky jsou v šabloně (proměnná `ILLUS`), např.:

| # | Klíčový moment |
|---|---|
| 1 | Harry sedí smutně sám o narozeninách, zatímco dole slaví Dursleyovi s Masonovými |
| 2 | Domácí skřítek Dobby na Harryho posteli, vteřinu před shozeným dortíkem |
| 3 | Rezavý létající ford anglia přistává nad zahradou Doupěte |
| 4 | Rvačka pana Weasleyho s Luciusem Malfoyem v knihkupectví Flourish a Blotts |
| 5 | Rozbitý ford anglia zaklíněný ve Vrbě mlátičce |
| 6 | Třída s chrániči uší kolem řvoucí mandragory na bylinkářství |
| 7 | Zkamenělá paní Norrisová vedle krvavého nápisu na zdi |
| 8 | Stovky duchů na Deathday party kolem zkaženého dortu |
| 9 | Zkamenělí Justin a Skoro bezhlavý Nick na chodbě |
| 10 | Zběsilý potlouk pronásledující Harryho nad famfrpálovým hřištěm |
| 11 | Harry syčí hadím jazykem na Dracem vyčarovaného hada na souboji |
| 12 | Hermioně rostou kočičí vousky nad kotlíkem s Mnoholičným lektvarem |
| 13 | Harry se dívá do deníku, ze kterého se vynořuje Tom Raddle |
| 14 | Ministr Popletal odvádí Hagrida, který ukazuje na pavouky |
| 15 | Harry a Ron tváří v tvář obřímu pavoukovi Aragogovi |
| 16 | Ron odhazuje kamení ze zřícené chodby, Harry mizí sám dál |
| 17 | Harry s mečem čelí Baziliškovi, nad hlavou fénix Fawkes |
| 18 | Harry podává Luciusovi ponožku, Dobby září štěstím |

### 31 portrétů postav

`assets/portraits/<id>.jpg` — orientace na výšku (poměr stran 3:4).

| soubor | postava | |
|---|---|---|
| `harry.jpg` | Harry Potter | ✅ (z dílu 1) |
| `ron.jpg` | Ron Weasley | ✅ (z dílu 1) |
| `hermiona.jpg` | Hermiona Grangerová | ✅ (z dílu 1) |
| `hagrid.jpg` | Hagrid | ✅ (z dílu 1) |
| `brumbal.jpg` | Albus Brumbál | ✅ (z dílu 1) |
| `mcgonagallova.jpg` | Minerva McGonagallová | ✅ (z dílu 1) |
| `snape.jpg` | Severus Snape | ✅ (z dílu 1) |
| `neville.jpg` | Neville Longbottom | ✅ (z dílu 1) |
| `nick.jpg` | Skoro bezhlavý Nick | ✅ (z dílu 1) |
| `filch.jpg` | Argus Filch | ✅ (z dílu 1) |
| `fredgeorge.jpg` | Fred a George Weasleyovi | ✅ (z dílu 1) |
| `percy.jpg` | Percy Weasley | ✅ (z dílu 1) |
| `madampomfreyova.jpg` | Madame Pomfreyová | ✅ (z dílu 1) |
| `voldemort.jpg` | Voldemort | ✅ (z dílu 1) |
| `draco.jpg` | Draco Malfoy | ✅ (z dílu 1) |
| `norrisova.jpg` | Paní Norrisová (kočka) | |
| `ginny.jpg` | Ginny Weasleyová | |
| `dobby.jpg` | Dobby | |
| `lockhart.jpg` | Zlatoslav Lockhart | |
| `myrtle.jpg` | Ufňukaná Uršula | |
| `colin.jpg` | Colin Creevey | |
| `riddle.jpg` | Tom Rojvol Raddle | |
| `lucius.jpg` | Lucius Malfoy | |
| `sprout.jpg` | Profesorka Prýtová | |
| `aragog.jpg` | Aragog (pavouk) | |
| `fawkes.jpg` | Fawkes (fénix) | |
| `bazilisek.jpg` | Bazilišek | |
| `artur.jpg` | Arthur Weasley | |
| `molly.jpg` | Molly Weasleyová | |
| `justin.jpg` | Justin Finch-Fletchley | |
| `popletal.jpg` | Kornelius Popletal | |

### Styl

Zatím nevyřešeno — stejná otázka jako u dílu 1: skeny z Illustrated Edition, originální/AI ilustrace, nebo kombinace. Důležité jen to, aby portréty napříč oběma díly stylově seděly k sobě, pokud možno.

### Jména k ověření

U pár jmen jsem si nebyl stoprocentně jistý přesným zněním v Medkově překladu — zkontroluj prosím v knize:
- **Paní Norrisová** (Mrs Norris, Filchova kočka)
- **Ufňukaná Uršula** (Moaning Myrtle)
- **Tom Rojvol Raddle** (Tom Marvolo Riddle — v originále jde o anagram na „I am Lord Voldemort", Medkův překlad to řeší jménem, co se anagramem překládá na „Já Lord Voldemort")
- **Profesorka Prýtová** (Professor Sprout)
- **Kornelius Popletal** (Cornelius Fudge)

Názvy kapitol v appce jsou moje vlastní parafráze (ne doslovný text knihy) — pokud chceš, aby přesně seděly s tvým výtiskem, klidně mi řekni a upravím.
