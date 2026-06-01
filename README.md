# HUN-MED Kft. – Vállalati weboldal

Modern, letisztult vállalati weboldal statikus HTML/CSS/JS alapokon. A Hun-Med orvostechnikai képviseleteit, munkatársait és elérhetőségeit mutatja be.

## Gyors indítás

```bash
cd /Users/endre.gyurcsovics/Egyetem/Hunmed
python3 -m http.server 8080
```

Megnyitás: **http://localhost:8080**

## Fájlstruktúra

```
Hunmed/
├── index.html           # Főoldal (hero, szakmai területek, kapcsolat előnézet)
├── kepviseleteink.html  # Gyártói képviseletek
├── munkatarsak.html     # Munkatársak
├── kapcsolat.html       # Elérhetőség, űrlap, térkép
├── css/style.css
├── js/main.js
└── images/              # Fotók, később: images/partners/ logók
```

## Oldalak

| Menüpont | Tartalom |
|----------|----------|
| Főoldal | Hero, 5 szakmai terület, kapcsolat + űrlap |
| Képviseleteink | 8 partner kártya (2 oszlop desktop) |
| Munkatársak | 6 munkatárs kártya |
| Kapcsolat | Céges adatok, űrlap, Google Maps |

## Testreszabás

- **Színek:** `css/style.css` → `:root` (navy, szürke árnyalatok)
- **Partnerlogók:** helyezze az `images/partners/` mappába a hivatalos logókat, majd frissítse a `kepviseleteink.html` `img` útvonalait
- **Munkatárs fotók:** cserélje a `.staff-initials` blokkot `<img>` elemre a `munkatarsak.html`-ben
- **Űrlap:** jelenleg szimulált küldés (`js/main.js`); élesítéshez Formspree, Netlify Forms vagy saját backend

## Hostolás

Részletesen: **[HOSTING.md](HOSTING.md)**

## Technológiák

- HTML5, CSS3, Vanilla JavaScript
- Google Fonts (Inter)
- Font Awesome ikonok

**© 2026 HUN-MED Kft.**
