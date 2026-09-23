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
