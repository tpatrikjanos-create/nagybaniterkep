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
