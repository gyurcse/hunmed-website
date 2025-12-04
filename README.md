# Hunmed - Orvosi Műszer Kereskedés

Modern, reszponzív weboldal statikus HTML/CSS/JS alapokon.

## 🚀 Gyors indítás

### Lokális megtekintés

```bash
cd /Users/endre.gyurcsovics/Egyetem/Hunmed
python3 -m http.server 8080
```

Majd nyisd meg: **http://localhost:8080**

### Alternatív szerverek

```bash
# Node.js
npx serve

# PHP
php -S localhost:8080

# Ruby
ruby -run -e httpd . -p 8080
```

---

## 📁 Fájlstruktúra

```
Hunmed/
├── index.html          # Főoldal
├── rolunk.html         # Rólunk
├── termekek.html       # Termékeink  
├── szolgaltatasok.html # Szolgáltatások
├── kapcsolat.html      # Kapcsolat
├── css/
│   └── style.css       # Stílusok
├── js/
│   └── main.js         # JavaScript
├── images/
│   └── *.jpg           # Csapatfotók
├── README.md           # Ez a fájl
└── HOSTING.md          # Részletes hostolási útmutató
```

---

## 🎨 Testreszabás

### Színek módosítása

Nyisd meg a `css/style.css` fájlt és módosítsd a CSS változókat:

```css
:root {
    --primary: #0066CC;       /* Fő szín */
    --primary-dark: #004C99;  /* Sötétebb változat */
    --secondary: #00A86B;     /* Másodlagos szín */
}
```

### Tartalom szerkesztése

Egyszerűen szerkeszd a HTML fájlokat bármilyen szövegszerkesztővel.

---

## 📝 Teendők (dummy adatok cseréje)

- [ ] Kolléga nevek frissítése (`rolunk.html`)
- [ ] Céges elérhetőségek módosítása
- [ ] Valós termékek hozzáadása
- [ ] Kapcsolati űrlap backend beállítása
- [ ] Google Maps embed frissítése

---

## 🌐 Hostolás

Részletes útmutató: **[HOSTING.md](HOSTING.md)**

Gyors lehetőségek:
- **Netlify** - ingyenes, drag & drop
- **GitHub Pages** - ingyenes
- **Bármilyen webszerver** - FTP feltöltés

---

## 📱 Funkciók

- ✅ Teljesen reszponzív dizájn
- ✅ Modern, letisztult megjelenés
- ✅ Mobil navigáció
- ✅ Animációk scroll-ra
- ✅ Kapcsolati űrlap
- ✅ SEO-barát struktúra

---

## 🛠️ Technológiák

- HTML5
- CSS3 (CSS Variables, Grid, Flexbox)
- Vanilla JavaScript
- Google Fonts (Poppins, Inter)

---

**© 2024 Hunmed Kft.**
