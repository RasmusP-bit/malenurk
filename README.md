# Malenurk

Malenurk on eestikeelne, serverivaba maleharjutuste veebiprogramm 9–12-aastastele noortele, kes on malet treeninguna õppinud vähemalt kolm aastat.

## Käivitamine

Lihtsaim viis on avada `index.html` veebilehitsejas. Kui soovid kasutada lokaalset serverit, käivita selles kaustas näiteks `py -m http.server 3001` ja ava http://localhost:3001. See projekt ei kasuta ega puuduta aadressi localhost:3000.

## Tehnoloogia ja põhifunktsioonid

Programm on üks HTML-fail, milles on HTML, CSS ja JavaScript. Väliseid teeke, serverit, andmebaasi ega kontosid ei kasutata. Rakenduses on õppijavaade, seadistatav harjutusseanss, interaktiivne klõpsatav malelaud, ühekäiguliste lahenduste kontroll, järkjärgulised vihjed, tulemused, salasõnaga treeneri vaade ja õpetaja 5-palline tagasisidevorm.

Treeneri vaate avamiseks tuleb sisestada salasõna `male2026`. Seda saab muuta `index.html` failis konstandis `COACH_PASSWORD`. Kuna rakendus on täielikult serverivaba, ei ole see salasõna päris turvameede: tehnikateadlik kasutaja võib selle lähtekoodist leida. See lahendus sobib õpilaste eest juhusliku ligipääsu peitmiseks; päris konfidentsiaalsuse jaoks oleks vaja serveripoolset autentimist.

## Ülesannete andmestruktuur ja kontroll

Ülesanded asuvad `index.html` JavaScripti massiivis `puzzles`. Igal objektil on teema (`t`), tase (`l`), FEN-seis (`fen`), küsimus (`q`), lahendus UCI-kujul (`s`), vihjed (`h`) ja selgitus (`e`). Uue ülesande lisamiseks lisa massiivi sama väljadega objekt; kogu ülejäänud kasutajaliides täidab end automaatselt.

Algversioon kasutab töökindluse hoidmiseks kontrollitavaid ühekäigulisi taktikaid: rakendus kontrollib valge malendi lähte- ja sihtruudu ning võrdleb käiku ülesande lahendusega. Mõnes „matt kahe käiguga“ ülesandes kontrollitakse esimest võtmekäiku ja kirjeldatakse järelmõtet; täielikku vastase kõigi vastuste otsingut siin ei tehta. See piirang on teadlikult dokumenteeritud, et mitte anda näiliselt korrektset mitmekäigulise mängu kontrolli.

Ülesanded on jaotatud kolmeks sisemiseks tasemeks: keskmine (üks selge taktikaline idee), tugev (rohkem kandidaate või täpsem arvutus) ja väga tugev (varjatum idee). Praegune andmebaas sisaldab 26 näidet seitsmest teemast. Need on käsitsi konstrueeritud treeningseisud; enne õppetöös kasutamist peaks maleõpetaja need üle vaatama, eriti mattide ja mitmekäiguliste ülesannete puhul.

## Pedagoogika, piirangud ja edasiarendus

Vale käik ei paljasta kohe lahendust. Vihjed avanevad ükshaaval, lahenduse nägemine ja järgmise ülesande juurde liikumine on eraldi tegevused. Seansitulemusi hoitakse ainult brauseri aktiivses kasutuses. Lohistamist, musta poole ülesandeid, täielikku seaduslike käikude generaatorit, tulemuste eksporti ja püsivat salvestust praegune versioon ei sisalda. Edasi saab lisada korrektse malereeglite mootori (nt legalsete käikude kontroll koos matiseisuga), suurema kontrollitud ülesandekogu, eksportimise ning õpetaja koostatud komplektid.

## Codexi kasutamine

Codexit kasutati programmi struktuuri, kasutajaliidese, JavaScripti andmestruktuuri, interaktiivse laua, vihjete, tulemuste, treenerivaate ja tagasisidevormi loomisel. Codex pakkus tehnilise lahenduse ja esmased näidisseisud; rakenduse autor peab kontrollima iga seisu malealaselt enne pärisõppetöös kasutamist. Autori enda roll on määrata sihtrühm, õppimiseesmärgid, teemade ja tasemete loogika, valida ning kontrollida ülesanded, hinnata kasutatavust ja teha muudatusi pärast maleõpetaja tagasisidet. Praeguses algversioonis ei ole veel pärast eraldi õpetajaekspertiisi tehtud muudatusi.
