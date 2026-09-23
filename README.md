# Nagybani Gastro — Piaci árfigyelő térkép

Egyfájlos webapp a Budapesti Nagybani Piacon való eligazodáshoz és árköveteshez. Google Maps alapú, a piac területére rögzítve, Firebase-en valós időben szinkronizál több telefon között.

## Fő funkciók

**Térkép**
- A térkép mindig csak a Nagybani Piac területét mutatja — nem lehet kihúzni vagy kizoomolni máshova.
- Élő kék pont mutatja a saját pozíciódat.
- Standot fel lehet venni a kék pontra kattintva, vagy a térkép bármely pontján hosszan nyomva.
- Minden stand egy feliratos pin — a névvel együtt jelenik meg a térképen.
- A ma megvásárolt standok élénk pink színnel kiemelődnek, a kedvenc standok ⭐-gal.

**Árazás vs. Vásárlás**
- **Mentés** = árazás — csak megnézted az árat, nem vetted meg.
- **🛒 Vásárolva** = ténylegesen megvásárolt tétel, mennyiséggel.
- Mindkettő a GPS-pozíciód alapján megkérdezi, melyik közeli standhoz rögzítse, és egy megerősítő képernyőn kell jóváhagyni — véletlen elgépelés/rossz stand ellen.
- Mértékegység választható: Ft/kg, Ft/db, Ft/rekesz, Ft/láda.
- Vásárlásnál jelölhető, ha csere rekeszt/ládát kell vinni (típus + mennyiség).

**Segéd funkciók**
- Hiányzó ár/termék felismerése, elgépelés-javaslat a korábban rögzített termékekhez képest.
- 🎤 Hangbevitel gyors rögzítéshez.
- Visszavonás gomb minden mentés után.

**Listák (📋 gomb)**
- **📝 Árazások** — összes felmért ár, szűrhető.
- **🛒 Vásárlások** — ténylegesen megvett tételek, napi összköltséggel.
- **🧺 Elviendő** — megvásárolt, de még fel nem pakolt tételek pipálható checklistje, a szükséges csere edényzet összesítésével.
- **💰 Legolcsóbb ma** — a mai árazások alapján zöldségenként, standonként rendezve, a legolcsóbb kiemelve.

**Stand adatlap**
- Átnevezhető, csillagozható (kedvenc), szabad szöveges jegyzettel (minőség, telefonszám, nyitvatartás stb.).

## Technikai háttér
- Egyfájlos HTML (`index.html`), build eszköz nélkül.
- Google Maps JavaScript API a térképhez.
- Firebase Realtime Database a szinkronizáláshoz (offline módban localStorage-ba esik vissza).
- GitHub Pages-en hosztolva.

## Verziózás
Minden módosítás git commit + tag formájában kerül a repóba (`VERSION` fájl követi az aktuális verziószámot).
