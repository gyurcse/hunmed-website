# Hunmed - Hostolási Útmutató

## 🌐 Hostolási lehetőségek

### 1. Hagyományos webszerver (legegyszerűbb)

Ha már van meglévő tárhelyed (pl. ahol a WordPress volt):

```bash
# FTP-vel töltsd fel az összes fájlt:
index.html
rolunk.html
termekek.html
szolgaltatasok.html
kapcsolat.html
css/style.css
js/main.js
images/ (összes kép)
```

**Népszerű magyar szolgáltatók:**
- [Rackhost](https://rackhost.hu) - ~2000 Ft/év
- [Tárhely.eu](https://tarhely.eu) - ~3000 Ft/év
- [Websupport](https://websupport.hu) - ~4000 Ft/év
- [Mikes](https://mikes.hu) - ~1500 Ft/év

---

### 2. Ingyenes hostolás (ajánlott teszteléshez)

#### **GitHub Pages** (Teljesen ingyenes)

1. Hozz létre GitHub fiókot: https://github.com
2. Új repository: `hunmed-website`
3. Töltsd fel a fájlokat
4. Settings → Pages → Source: main branch
5. Elérhető lesz: `https://felhasznalonev.github.io/hunmed-website`

#### **Netlify** (Ingyenes + egyedi domain)

1. Regisztrálj: https://netlify.com
2. "New site from Git" vagy drag & drop a mappát
3. Automatikusan HTTPS-t kapsz
4. Egyedi domain csatlakoztatható

#### **Vercel** (Ingyenes)

1. Regisztrálj: https://vercel.com
2. Import projekt
3. Automatikus deployment

#### **Cloudflare Pages** (Ingyenes)

1. Regisztrálj: https://pages.cloudflare.com
2. Connect to Git vagy Direct Upload
3. Gyors CDN + ingyenes SSL

---

### 3. Saját VPS szerver

Ha teljes kontrollt szeretnél:

#### **Ajánlott VPS szolgáltatók:**
- [DigitalOcean](https://digitalocean.com) - $4/hó
- [Linode](https://linode.com) - $5/hó
- [Vultr](https://vultr.com) - $5/hó
- [Hetzner](https://hetzner.com) - €3.29/hó (EU szerver)

#### **Nginx konfiguráció:**

```nginx
server {
    listen 80;
    server_name hunmed.hu www.hunmed.hu;
    root /var/www/hunmed;
    index index.html;
    
    location / {
        try_files $uri $uri/ =404;
    }
    
    # Gzip tömörítés
    gzip on;
    gzip_types text/plain text/css application/javascript;
    
    # Cache beállítások
    location ~* \.(jpg|jpeg|png|gif|ico|css|js)$ {
        expires 30d;
        add_header Cache-Control "public, immutable";
    }
}
```

#### **Apache konfiguráció (.htaccess):**

```apache
# Gzip tömörítés
<IfModule mod_deflate.c>
    AddOutputFilterByType DEFLATE text/html text/css application/javascript
</IfModule>

# Cache
<IfModule mod_expires.c>
    ExpiresActive On
    ExpiresByType image/jpg "access plus 1 month"
    ExpiresByType image/jpeg "access plus 1 month"
    ExpiresByType image/png "access plus 1 month"
    ExpiresByType text/css "access plus 1 week"
    ExpiresByType application/javascript "access plus 1 week"
</IfModule>

# Clean URLs
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([^\.]+)$ $1.html [NC,L]
```

---

## 📁 Fájlstruktúra

```
hunmed.hu/
├── index.html          ← Főoldal
├── rolunk.html         ← Rólunk
├── termekek.html       ← Termékeink
├── szolgaltatasok.html ← Szolgáltatások
├── kapcsolat.html      ← Kapcsolat
├── css/
│   └── style.css       ← Stílusok
├── js/
│   └── main.js         ← JavaScript
├── images/
│   ├── DSC_6067_2-2.jpg
│   ├── DSC_6085_2-2.jpg
│   ├── DSC_6102_2-2.jpg
│   ├── DSC_6116_2-3.jpg
│   └── DSC_7416_2-3.jpg
└── HOSTING.md          ← Ez a fájl
```

---

## 🔧 Domain beállítás

### DNS rekordok (ha van saját domain):

```
Típus   Név     Érték
A       @       [szerver IP címe]
A       www     [szerver IP címe]
CNAME   www     hunmed.hu
```

### Ingyenes domain alternatívák:
- `.hu` domain: ~3000 Ft/év (domain.hu, rackhost.hu)
- Freenom: ingyenes .tk, .ml, .ga domainok

---

## 🔒 SSL tanúsítvány (HTTPS)

### Let's Encrypt (ingyenes):

```bash
# Certbot telepítése
sudo apt install certbot python3-certbot-nginx

# Tanúsítvány generálás
sudo certbot --nginx -d hunmed.hu -d www.hunmed.hu

# Automatikus megújítás
sudo certbot renew --dry-run
```

### Cloudflare (ingyenes):
- Regisztrálj Cloudflare-re
- Add hozzá a domaint
- Automatikus SSL aktiválás

---

## 🚀 Deployment checklist

- [ ] Fájlok feltöltve
- [ ] Domain beállítva
- [ ] SSL aktív (HTTPS)
- [ ] Képek optimalizálva
- [ ] Tesztelve mobilon
- [ ] Kapcsolati űrlap működik
- [ ] Google Analytics hozzáadva (opcionális)
- [ ] Sitemap.xml létrehozva (SEO)

---

## 📊 Képoptimalizálás feltöltés előtt

A jelenlegi képek nagyok. Csökkentsd őket:

```bash
# ImageMagick-kel (ha telepítve van):
convert input.jpg -resize 800x800 -quality 85 output.jpg

# Vagy online:
# - https://squoosh.app
# - https://tinypng.com
```

Ajánlott méret: max 200-300 KB / kép

---

## 📧 Kapcsolati űrlap működtetése

A jelenlegi űrlap csak kliens oldali. Valódi email küldéshez:

### 1. Formspree (ingyenes, egyszerű)
```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```

### 2. Netlify Forms (ha Netlify-on hostolsz)
```html
<form name="contact" netlify>
```

### 3. Saját backend (PHP)
```php
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $to = "info@hunmed.hu";
    $subject = $_POST["subject"];
    $message = $_POST["message"];
    $headers = "From: " . $_POST["email"];
    mail($to, $subject, $message, $headers);
}
?>
```

---

## 💡 Tippek

1. **Rendszeres mentés** - Készíts biztonsági másolatot
2. **Verziókezelés** - Használj Git-et a változások követésére
3. **CDN** - Cloudflare ingyenes CDN-t biztosít
4. **Monitoring** - UptimeRobot ingyenes elérhetőség figyelés

---

## 🆘 Segítség

Ha elakadsz:
- [Stack Overflow](https://stackoverflow.com)
- [MDN Web Docs](https://developer.mozilla.org)
- Vagy kérdezz itt! 🙂

