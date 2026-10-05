# Nagybani Gastro — Piaci árfigyelő térkép

Egyfájlos webapp a Budapesti Nagybani Piacon való eligazodáshoz és árköveteshez.

## Mi került be eddig, verziónként

**v1.0 — Alapok**
- Térkép (Google Maps), standok felvétele kattintással/GPS-szel
- Gyors árbevitel: "termék ár" formátum
- Firebase szinkron több eszköz közt
- GitHub repo + verziózás (git tag minden push-nál)

**v1.1 — Kék pont**
- Élő GPS-pozíció kék pontként a térképen
- Stand felvétele csak a kék pontra kattintva (nem bárhol a térképen)

**v1.2 — Térkép a piacra rögzítve**
- Fix középpont a Nagybani Piacon
- Nem lehet kihúzni/kizoomolni máshova (pan/zoom korlátozás)

**v1.3 — Nagyobb bővítés**
- Hosszan nyomással is felvehető stand bárhol a térképen
- Feliratos pin-ek (stand neve a pötty mellett)
- Ma megvásárolt standok pink kiemeléssel
- Két külön gomb: Mentés (árazás) és 🛒 Vásárolva
- Mindkettő GPS-közelség alapján kérdez rá, melyik standhoz rögzítsen
- Megerősítő képernyő mindkét gombnál (véletlen összekeverés ellen)
- Vásárlások külön tárolva (stand, mennyiség, termék, ár, dátum)
- 💰 Legolcsóbb ma nézet

**v1.4 — Hibavédelem**
- Hiányzó ár/termék jelzése egyértelmű üzenettel
- Elgépelés-ellenőrzés (pl. "ubirka" → "uborka?") a korábbi termékekhez képest

**v1.5 — Munkafolyamat-segítők**
- 🧺 Elviendő lista: megvásárolt, még fel nem pakolt tételek pipálható checklistje
- Napi vásárlási összegzés (tétel + Ft)
- Visszavonás gomb minden mentés után
- 🎤 Hangbevitel gyors rögzítéshez

**v1.6 — Mértékegység és csere edényzet**
- Mértékegység választó: Ft/kg, Ft/db, Ft/rekesz, Ft/láda
- Csere rekesz/láda jelölése vásárláskor (típus + mennyiség)
- Összesítve az Elviendő listán ("vidd magaddal csereként...")

**v1.7 — Stand adatlap bővítés**
- Kedvenc standok csillagozása (⭐ a pin feliratban is)
- Szabad szöveges jegyzet standonként (minőség, telefonszám, nyitvatartás stb.)

## Technikai háttér
Egyfájlos HTML, build eszköz nélkül · Google Maps JS API · Firebase Realtime Database (offline esetén localStorage) · GitHub Pages

## v1.8
- Éjfélkor törlődő ideiglenes standok, fix stand jelölés, jegyzet, kedvencek.

## v2.0 – Kezdőképernyő + bevásárlás
- Kezdőképernyő („Mit csinálunk ma?”: Bevásárlás / Kiszállítás (hamarosan) / Csak térkép).
- Terméklista-összeállító az Excel árlistából (134 termék, 14 kategória), ékezetfüggetlen kereső, mennyiség-léptetők, képek (Wikipedia, élőben töltve és gyorsítótárazva).
- Email/rendelés szöveg automatikus felismerése („5kg fejeskáposzta, 10 kilo répa”).
- Bevásárlás checklist a térképen: kipipáláskor stand (legközelebbi / új tű), ár, mennyiség, csere rekesz/láda.
- Összesítő (stand szerint, összeg, hozandó edényzet) és összegyűjtő checklist.
- Napi lista Firebase-ben (shopSession/current), localStorage fallback.

## v2.1 – Kiszállítás: komissiózás
- „Kiszállítás” gomb élesítve: hány címre szállítunk → üres címek létrehozása.
- Cím szerkesztő: név, cím, megjegyzés; mentett címekből választható, új cím automatikusan elmentődik (Firebase `addressBook`).
- Tételek pontos mennyiséggel, egységgel, egységárral (alap: Excel árlista, átírható); jelzi a ma beszerzett mennyiséghez képest a kiosztott/maradó/hiányzó mennyiséget.
- Kiadott edényzet címenként: rekesz, láda, raklap.
- Szállítólevél / számlamelléklet nyomtatása vagy PDF-be mentése (egy cím vagy az összes).
- „Szállításra kész” jelölés, napi összesítő (rakodandó edényzet). Napi adat: Firebase `deliveryDay/current` + localStorage.

## v2.2 – Szállítás és edényzet-egyenleg
- Új „Szállítás” képernyő: szállításra kész címek listája, kiválasztod, melyiket viszed ki.
- Cím részletek: átadandó tételek pontos mennyiséggel, összeg, kiadandó edényzet, eddigi tartozás, navigáció (Google Maps) a címre.
- „Kiszállítva” → visszahozott rekesz/láda/raklap rögzítése; az új egyenleg (nettó szám címenként) elmentődik a címhez, és a következő szállításnál megjelenik (kártyán, szerkesztőben, szállítólevélen).
- Egyenleg kézzel is megadható/javítható a cím szerkesztőben (kezdő tartozás); a kiszállítás visszavonható.

## v2.3 – Napi archívum és riportok
- Minden nap automatikusan archiválódik (Firebase `archive/<dátum>` + localStorage): szállítások, tételek, árak, megvett termékek.
- Új „Riportok” képernyő (7 / 30 / 90 nap / mind): eladási forgalom, beszerzési költség, becsült árrés, kiszállítások száma.
- Forgalom címenként, legtöbbet értékesített termékek, beszerzési árak (átlag, legolcsóbb stand, árváltozás ▲▼), edényzet-egyenleg címenként.
- CSV-export (Excelben megnyitható) az időszak szállításairól.

## v2.4 – Árcédula-dizájn
- Új vizuális nyelv a piaci világból: ládafal-háttér a kezdőképernyőn, matrica-sárga „árcédulák” (összegek, első riport-mutató, folyamatban lévő bevásárlás), lenyomódó, tapintható gombok.
- Barlow Condensed (címek, számok, gombok) + Barlow (szöveg) – jól olvasható erős napfényben is, magyar ékezetekkel.
- Laposabb, keretes kártyák; a végtelen lebegő animációk és a kártyánkénti beúszás megszűnt, a mozgás a műveletekre (kipipálás, lenyomás, lapok) reagál; a lebegő gomb csak kétszer pulzál.
- Erősebb kontraszt és látható fókuszkeret.

## v2.5 – Windows Aero téma
- Új megjelenés a Windows Vista/7 „Aero” stílusában: égkék háttér fénycsíkokkal, üveg (áttetsző, elmosódó) ablakkeretek fényes címsorral, világos tartalomterület.
- Fényes, kétszínű „gloss” gombok (zöld = fő művelet, narancs = kiemelt, szürke = általános), üveggömb ikonok a kezdőképernyőn, Intéző-stílusú kijelölés, zöld üveg pipák és folyamatjelzők.
- Betűtípus: Segoe UI (Windowson), máshol Open Sans. A korábbi árcédula-dizájn (v2.4) a git előzményekben megmaradt.

## v2.6 – Termékikonok
- Minden termék saját, a fájlba beépített ikont kap (🥕 🍅 🧅 🍄 🍎 …), hálózat nélkül is azonnal látszik; ez jelenik meg a lista, a checklist és a komissiózás termékválasztójában.
- A Wikipédiáról töltött fotó továbbra is megpróbálkozik, és ha sikerül, felülírja az ikont. Ha az eszközön nem érhető el, egy üzenet jelzi, és az ikonok maradnak.

## v2.7 – Logó
- A Nagybani Gastro logó a kezdőképernyőn (kerek, üveg-fénnyel), a szállítólevél fejlécében, valamint böngésző-ikonként / kezdőképernyő-ikonként (apple-touch-icon) is megjelenik. A kép a fájlba van ágyazva, hálózat nélkül is látszik.

## v2.8 – Firebase bekötve
- A `firebaseConfig` a „nagybani-gastro-koltsegkonyv” projektre mutat (közös adatbázis a költségkönyv alkalmazással).
- Az app minden adata a saját `piacTerkep/…` ágon él (vendors, purchases, priceEntries, shopSession, deliveryDay, addressBook, archive), így nem keveredik a költségkönyv adataival.
- Jogosultsági hiba esetén (Rules) látható figyelmeztetés jelenik meg.

## v2.9 – Bejelentkezés és napló
- Firebase Authentication (email + jelszó, vagy Google-fiók): a közös projekt felhasználóival lehet belépni. Belépés nélkül „helyi mód” is van (az adat csak az eszközön marad).
- Minden új rögzítés (stand, árazás, vásárlás, kipipálás) tárolja, ki csinálta (`by`); a szállítás állapotváltásait is.
- „Napló” (kezdőképernyő alján, bejelentkezve): időrendben, ki mit csinált (Firebase `piacTerkep/activity`).

## v2.10 – Kötelező bejelentkezés
- Csak a költségkönyv profiljaival lehet belépni (email + jelszó); a Google-belépés és a „bejelentkezés nélkül” mód megszűnt.
- A bejelentkezési képernyő minden más előtt megjelenik (a térkép betöltésétől függetlenül); ha 7 mp alatt nincs kapcsolat, hibát mutat.

## v2.11 – Saját Firebase projekt
- Az app saját Firebase projektet használ (`gastroapp-36e58`), nem osztozik a költségkönyvvel. A felhasználókat az Authentication → Users résznél kell felvenni (email + jelszó), a Rules-ban a `piacTerkep` ágat kell engedni a bejelentkezetteknek.

## v3.0 – Leaflet térkép (Google nélkül)
- A Google Maps lecserélve Leafletre: nincs API-kulcs, nincs számlázás, nincs „for development purposes only” vízjel.
- Alaptérkép: Esri World Imagery műhold (alapból) és OpenStreetMap utcatérkép, jobb felső sarokban váltható.
- Változatlan működés: a piac köré korlátozott nézet, kék pont a saját pozícióval, hosszan nyomással új stand, feliratos pinek, kiemelés, kedvencek, ideiglenes standok.
- Firebase: újra a költségkönyves projekt (`nagybani-gastro-koltsegkonyv`), a `piacTerkep/…` ágon.

## v3.1 – Külön menüpontok
- A kezdőképernyőn külön menüpont a Bevásárlás, a Komissiózás és a Szállítás (+ Riportok, Csak térkép); a Szállítás képernyő önállóan nyílik, mutatja a kiszállítandó/kiszállított címek számát.
- A Nagybani Gastro logó és a cím középre igazítva; kis képernyőn a menü görgethető.

## v3.2 – Munkafolyamat: bevásárlás → komissiózás → szállítás
- Bevásárlás végén „Tovább a komissiózásra →”.
- Komissiózás: „Szállításra kész ✓ (n)” az összes kitöltött címre egyszerre; ha nincs több piszkozat: „Tovább a szállításra →”.
- A szállításra kész címek napokon át megmaradnak, a Szállítás képernyőn bármelyik napról megjelennek („Komissiózva: dátum” jelzéssel). Kiszállított címek a kiszállítás napja után törlődnek a listáról (az archívumban megmaradnak).
- „Cím törlése” a címszerkesztőben; szállítólevél a komissiózás dátumával; a riport a komissiózás napjához rendeli a címeket (nincs dupla számolás).

## v3.3 – Címek előre, mérés alapú komissiózás, törlések
- Bevásárlás indulása: először a címek és mennyiségek (mint a komissiózásnál), a bevásárlólista ezek összegéből áll össze; extra termékek külön adhatók hozzá. A komissiózásnál a címek kitöltve várnak.
- Nagy zöld „Kész ✓” gomb jobb felül; a lista beillesztése visszafogott link.
- Komissiózás/szállítólevél: nincs Ft, csak a mért mennyiség (kg/db…); riportból a forgalom/árrés kikerült.
- Belépés felhasználónévvel (a @kiadas.local automatikus).
- Megszakítás/törlés: mai bevásárlás törlése (listán és minden bevásárlás panelen), összes nem kiszállított cím törlése, egy cím törlése.

## v3.4 – Cím-lépés, raktár, törlések
- Bevásárlás 1. lépés: csak a címek (név, cím, megjegyzés) – mentett partnerekre egy koppintás, új cím automatikusan mentődik partnerként; „Tovább” után jön a terméklista (mennyiségek összesen). A jobb felső gomb és a ☑ szűrő megszűnt.
- Komissiózás után a kezdőképernyő „komissiózásra vár” kártyája eltűnik.
- Komissiózás: „Ki nem osztott áru” – „Raktárba küldtem” (mennyiség megadható), raktár-lista, bejegyzés törölhető.
- Komissiózott és kiszállított címek is törölhetők (cím szerkesztő, Szállítás részletek, „Kiszállított címek törlése”); a riportokból is kikerülnek.

## v3.5 – Eladási ár és árrés a bevásárlásnál
- A kiválasztott terméknél látszik az összesen vásárlandó mennyiség, és megadható az eladási ár (Ft/egység); az ár megjegyződik a következő napra is.
- Kipipáláskor élő árrés (Ft és %) a beszerzési ár alapján; a bevásárlás-listában és az összesítőben (várható árrés) is látszik.
- A térképen a stand árlistájában a rögzített ár mellett az árrés is megjelenik, ahol az eladási ár ismert.

## v3.6 – Szállítás: Címek és Új kiszállítás; Komissiózás: Új rendelés raktárkészletből
- Szállítás képernyő: „📍 Címek” (mentett címek, edényzet-egyenleg címenként és összesen, szerkesztés/törlés, „+ Új cím”), „+ Új kiszállítás” (csak szállítás, komissiózás nélkül; mentett vagy új cím, tételek opcionálisak). A komissiózott, szállításra kész rendelések itt jelennek meg.
- Komissiózás: „+ Új rendelés”; a tételválasztóban a Raktárkészlet külön szekció, a felvett mennyiség levonódik a raktárból (módosításkor/törléskor visszakerül).

## v3.7 – Egy cím egyszerre, edényzet-tartozás, vissza gomb az appon belül
- Komissiózás: a mentett címek azonnal előjönnek; egy cím kiválasztása után a szerkesztőben „✓ Kész — szállításra kész”, utána „Még egy cím a szállítmányhoz?” (következő mentett cím vagy új cím).
- Edényzet: csak tartozás van (náluk lévő edényzet); negatív egyenleg megszűnt, a feliratok „tartozás”-ra váltottak.
- Navigáció: a böngésző/telefon „vissza” gombja az alkalmazás menüpontjai között lép (előző képernyő), megnyitott ablak/panel esetén azt zárja be.
