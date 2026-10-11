# Malenurk

Malenurk on eestikeelne, serverivaba maleharjutuste veebiprogramm 9–12-aastastele noortele, kes on malet treeninguna õppinud vähemalt kolm aastat.

## Käivitamine

Lihtsaim viis on avada `index.html` veebilehitsejas. Kui soovid kasutada lokaalset serverit, käivita selles kaustas näiteks `py -m http.server 3001` ja ava http://localhost:3001. See projekt ei kasuta ega puuduta aadressi localhost:3000.

## Tehnoloogia ja põhifunktsioonid

Programm on üks HTML-fail, milles on HTML, CSS ja JavaScript. Väliseid teeke, serverit, andmebaasi ega kontosid ei kasutata. Rakenduses on õppijavaade, seadistatav harjutusseanss, reegleid kontrolliv klõpsatav malelaud, rohelise/punase sihtruudu märgistus, järkjärgulised vihjed, tulemused, salasõnaga treeneri vaade ja õpetaja 5-palline tagasisidevorm.

Treeneri vaate avamiseks tuleb sisestada salasõna `male2026`. Seda saab muuta `index.html` failis konstandis `COACH_PASSWORD`. Kuna rakendus on täielikult serverivaba, ei ole see salasõna päris turvameede: tehnikateadlik kasutaja võib selle lähtekoodist leida. See lahendus sobib õpilaste eest juhusliku ligipääsu peitmiseks; päris konfidentsiaalsuse jaoks oleks vaja serveripoolset autentimist.

## Ülesannete andmestruktuur ja kontroll

Harjutuste algandmed asuvad `index.html` massiivis `guidedPuzzles` ja kasutajaliides kasutab neid massiivina `puzzles`. Igal objektil on teema (`t`), tase (`l`), FEN-seis (`fen`), küsimus (`q`), kontrolli tüüp (`mode`), vihjed (`h`) ja selgitus (`e`). Uue ülesande lisamiseks lisa sama väljadega objekt ning vali sobiv kontrolli tüüp: `capture`, `defend`, `escape`, `fork`, `pin`, `skewer` või `mate`. Kahvli puhul määra kaks `targets`-sihtmärki; läbistava rünnaku puhul `target`.

Harjutuste reeglimootor kontrollib malendi liikumismustrit, teel olevaid nuppe, enda nupu löömise keeldu, vastase kuninga löömise keeldu ning seda, et oma kuningas ei jääks või ei läheks tule alla. Ülesande vastus ei ole ainult üks etteantud ruudupaar: liikumise ülesanne lubab iga seadusliku käigu, löömise ülesanne seadusliku löögi, tule ülesanne tule andva käigu, tule alt pääsemise ülesanne iga käigu, mis eemaldab tule, ning mati ülesanne ainult tegeliku mati. Kaitsmise ülesanne võrdleb pärast käiku sihtnupu ründajate arvu.

Ülesanded on jaotatud kolmeks sisemiseks tasemeks: keskmine (üks selge taktikaline idee), tugev (rohkem täpsust nõudev käik) ja väga tugev (varjatum idee või kuningaohutus). Praegune õppijajada sisaldab 8 kontrollitavat taktikaülesannet: matt ühe käiguga, kahvel, sidumine, topeltrünnak, materialivõit, läbistav rünnak, rünnak ja kaitse ning kaitsev käik. Lihtsad malendite liikumise harjutused ei kuulu enam sellesse sihtrühma mõeldud põhijadasse.

## Pedagoogika, piirangud ja edasiarendus

Vale käik ei paljasta kohe lahendust: seadusvastane sihtruut muutub punaseks ja annab selgituse; seaduslik, kuid ülesande ideed mitte lahendav käik muutub samuti punaseks. Õige sihtruut muutub roheliseks. Vihjed avanevad ükshaaval, „Proovi uuesti” puhastab märgistuse ning „Järgmine ülesanne” liigub alati edasi. Seansitulemusi hoitakse ainult brauseri aktiivses kasutuses. Lohistamist, musta poole ülesandeid, vangerduse ja möödaminnes löömise erireegleid ning püsivat salvestust praegune versioon ei sisalda. Edasi saab lisada suurema kontrollitud ülesandekogu, täielikuma erireeglite toe ja õpetaja koostatud komplektid.

## Codexi kasutamine

Codexit kasutati programmi struktuuri, kasutajaliidese, JavaScripti andmestruktuuri, interaktiivse laua, vihjete, tulemuste, treenerivaate ja tagasisidevormi loomisel. Codex pakkus tehnilise lahenduse ja esmased näidisseisud; rakenduse autor peab kontrollima iga seisu malealaselt enne pärisõppetöös kasutamist. Autori enda roll on määrata sihtrühm, õppimiseesmärgid, teemade ja tasemete loogika, valida ning kontrollida ülesanded, hinnata kasutatavust ja teha muudatusi pärast maleõpetaja tagasisidet. Praeguses algversioonis ei ole veel pärast eraldi õpetajaekspertiisi tehtud muudatusi.
