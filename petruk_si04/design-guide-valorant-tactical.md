# DESIGN SYSTEM & PRESENTATION GUIDE
## Tema: "VALORANT TACTICAL BOARD" — Perpaduan HUD Game Tactical Shooter x Coretan Papan Taktik (Whiteboard Strategy)

Dokumen ini adalah panduan desain (design guideline) untuk membangun presentasi bergaya **HUD tactical shooter (terinspirasi Valorant)** yang dipadukan dengan estetika **papan tulis strategi / coret-coretan taktik ala pelatih e-sport atau militer** — garis panah putus-putus, lingkaran tangan, callout crosshair, dan tekstur "spidol di whiteboard". Cocok untuk presentasi bertema strategi, analisis, roadmap, atau apa pun yang ingin terasa "tegas, taktis, dan hidup".

---

## 1. KONSEP VISUAL

Dua lapisan yang dipadukan:

1. **Lapisan HUD Game (Valorant-esque):** warna kontras tinggi (merah/hitam/putih tulang), sudut miring (skewed), garis tegas, corner bracket ala crosshair/UI game, tipografi tebal-kapital.
2. **Lapisan Papan Taktik (Coretan Strategi):** background bertekstur whiteboard/grid map, elemen "digambar tangan" — panah putus-putus, lingkaran spidol, garis coretan, sticky note, tulisan tangan (marker font) sebagai anotasi/highlight.

Prinsip: **HUD untuk struktur, coretan tangan untuk penekanan & narasi.** Jangan biarkan keduanya bertarung — coretan tangan selalu berperan sebagai "anotasi di atas" struktur HUD yang rapi, bukan sebaliknya.

---

## 2. DESIGN TOKENS (CSS VARIABLES)

```css
:root {
  /* === Core Palette (Valorant-inspired) === */
  --color-red: #FF4655;          /* Aksen utama, CTA, highlight kritikal */
  --color-red-dark: #BD3944;     /* Hover/pressed state, shadow aksen */
  --color-ink: #0F1923;          /* Background gelap utama, HUD frame */
  --color-steel: #1F2731;        /* Panel sekunder di atas ink */
  --color-bone: #ECE8E1;         /* Teks di atas gelap, whiteboard base */
  --color-paper: #F5F3EC;        /* Background "papan tulis" terang */
  --color-graphite: #3A3A3A;     /* Coretan spidol hitam */

  /* === Tactical Accent (map/HUD utility) === */
  --color-teal: #00FFC2;         /* Info, status aktif, garis radar */
  --color-amber: #FFB65C;        /* Peringatan, penomoran, sticky note */
  --color-blue-tac: #4A9FE0;     /* Tim/kategori sekunder */

  /* === Typography === */
  --font-display: "Anton", "Bebas Neue", "Arial Narrow", sans-serif; /* HUD headline, ultra bold-condensed */
  --font-body: "Rajdhani", "Inter", sans-serif;      /* Body/label, terasa "teknis" */
  --font-marker: "Permanent Marker", "Caveat", cursive; /* Anotasi tangan, coretan taktik */
  --font-mono: "JetBrains Mono", monospace;          /* Data/koordinat/callsign */

  /* === Texture Tokens === */
  --texture-grid: linear-gradient(var(--color-graphite) 1px, transparent 1px),
                   linear-gradient(90deg, var(--color-graphite) 1px, transparent 1px);
  --texture-grid-size: 32px 32px;
  --texture-grid-opacity: 0.06;

  /* === Motion === */
  --transition-hud: all 0.35s cubic-bezier(0.16, 1, 0.3, 1);
  --transition-color: background-color 0.6s ease, color 0.6s ease;
  --skew-panel: -6deg; /* sudut miring khas panel HUD */
}
```

---

## 3. TIPOGRAFI

* **Headline (Display / HUD):**
  * `text-transform: uppercase;`
  * Weight: 700–900 (Black)
  * `letter-spacing: 0.02em` — kondensasi Anton/Bebas sudah rapat secara natural
  * `line-height: 0.92`
  * Bisa diberi `transform: skewX(-4deg)` pada blok judul untuk kesan "dinamis"
* **Body / Label:**
  * Rajdhani/Inter, weight 500–600, ukuran cukup besar (min 18px di slide) agar terasa "teknis" bukan sekadar teks biasa
  * Label kecil (kategori, nomor slide, koordinat) pakai `--font-mono`, uppercase, tracking lebar (`letter-spacing: 0.15em`)
* **Anotasi Tangan (Marker):**
  * `--font-marker`, dipakai TERBATAS — hanya untuk 1–2 kata penekanan, callout, atau "catatan pelatih di pinggir slide"
  * Warna: merah (`--color-red`) di atas background terang, atau `--color-amber`/putih di atas background gelap
  * Jangan pernah dipakai untuk paragraf panjang — ini elemen aksen, bukan body text

---

## 4. ELEMEN VISUAL KHAS

### A. HUD Frame & Corner Bracket
Setiap slide/panel penting diberi "bingkai crosshair" di sudut — 4 garis L-shape kecil di tiap pojok, seperti reticle kamera tactical.

```html
<div class="hud-frame">
  <span class="corner tl"></span>
  <span class="corner tr"></span>
  <span class="corner bl"></span>
  <span class="corner br"></span>
  <!-- konten slide -->
</div>
```

```css
.hud-frame { position: relative; padding: 48px; }
.hud-frame .corner { position: absolute; width: 24px; height: 24px; border-color: var(--color-red); }
.corner.tl { top: 16px; left: 16px; border-top: 3px solid; border-left: 3px solid; }
.corner.tr { top: 16px; right: 16px; border-top: 3px solid; border-right: 3px solid; }
.corner.bl { bottom: 16px; left: 16px; border-bottom: 3px solid; border-left: 3px solid; }
.corner.br { bottom: 16px; right: 16px; border-bottom: 3px solid; border-right: 3px solid; }
```

### B. Panah Taktik (Tactical Path Arrow)
Garis putus-putus melengkung ala jalur rotasi di papan strategi — dipakai untuk menunjukkan alur/proses/flow antar poin.

```svg
<svg width="240" height="80" viewBox="0 0 240 80" fill="none">
  <path d="M10 60 C 80 10, 160 10, 230 40"
        stroke="var(--color-red)" stroke-width="3"
        stroke-dasharray="10 8" stroke-linecap="round"/>
  <polygon points="230,40 216,32 218,48" fill="var(--color-red)"/>
</svg>
```

### C. Lingkaran Spidol (Marker Circle Highlight)
Untuk menandai satu elemen penting seolah dilingkari spidol saat presentasi live.

```svg
<svg width="140" height="90" viewBox="0 0 140 90" fill="none">
  <ellipse cx="70" cy="45" rx="62" ry="34"
           stroke="var(--color-red)" stroke-width="4"
           stroke-linecap="round" fill="none"
           style="filter: url(#roughen);"/>
</svg>
```
*(opsional: tambahkan SVG filter `feTurbulence` ringan agar garis terasa tidak sempurna/hand-drawn)*

### D. Sticky Note / Callout Tag
Kotak kecil miring (skew) seperti label taktik, dipakai untuk anotasi singkat, angka statistik, atau status ("ACTIVE", "DATA", "01").

```css
.tac-tag {
  display: inline-block;
  background: var(--color-amber);
  color: var(--color-ink);
  font-family: var(--font-mono);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  padding: 4px 12px;
  transform: skewX(var(--skew-panel));
  box-shadow: 3px 3px 0 var(--color-ink);
}
```

### E. Tekstur Grid Peta (Map/Whiteboard Grid)
Background halus bergaris seperti kertas grafik/peta taktik, dipasang di belakang konten dengan opacity rendah agar tidak mengganggu keterbacaan.

```css
.tactical-bg {
  background-color: var(--color-ink);
  background-image: var(--texture-grid);
  background-size: var(--texture-grid-size);
  opacity: 1;
}
.tactical-bg::before {
  content: "";
  position: absolute; inset: 0;
  background: inherit;
  opacity: var(--texture-grid-opacity);
}
```

---

## 5. PALET PER SLIDE (Scroll/Transition Background)

| # | Slide Type            | Background          | Teks             | Aksen         |
|---|------------------------|----------------------|-------------------|----------------|
| 1 | Cover                 | `--color-ink` + grid | `--color-bone`    | `--color-red`  |
| 2 | Latar Belakang        | `--color-paper`      | `--color-graphite`| `--color-red`  |
| 3 | Peta/Timeline         | `--color-ink` + grid | `--color-bone`    | `--color-teal` |
| 4 | Strategi/Poin Utama   | `--color-steel`      | `--color-bone`    | `--color-amber`|
| 5 | Data/Statistik        | `--color-paper`      | `--color-graphite`| `--color-blue-tac` |
| 6 | Kutipan/Refleksi      | `--color-red`        | `--color-ink`     | `--color-bone` |
| 7 | Penutup               | `--color-ink` + grid | `--color-red`     | `--color-bone` |

Aturan transisi: setiap pindah slide, background boleh berubah, tapi HUD frame (corner bracket) dan tipografi display **tetap konsisten** di semua slide — ini yang menjaga identitas "tactical HUD" tetap terasa satu kesatuan.

---

## 6. LAYOUT & KOMPONEN UI

### A. Navigasi
* **Top-left:** ikon menu berbentuk crosshair kecil (bukan hamburger biasa) → membuka drawer miring (skew) berisi daftar slide, gaya "mission select".
* **Top-center:** indikator progres berbentuk bar segmented horizontal (seperti health bar/ammo bar), bukan dot biasa.
* **Top-right:** tombol aksi bulat kecil dengan border tipis merah, ikon minimalis (share, sumber referensi, dsb).

### B. Grid Konten
* Gunakan grid asimetris: 1 kolom besar (headline + visual) + 1 kolom sempit (label/data/anotasi) — meniru layout HUD game yang punya "panel info" di pinggir.
* Elemen visual utama (foto, ikon, diagram) **selalu dipotong miring (clip-path polygon)** di salah satu sisi agar terasa dinamis, bukan kotak sempurna.

```css
.clip-tactical {
  clip-path: polygon(0 0, 100% 0, 100% 88%, 92% 100%, 0 100%);
}
```

### C. Kartu Poin (Untuk grid multi-item seperti "Karakteristik/Strategi")
```css
.tac-card {
  background: var(--color-steel);
  border-left: 4px solid var(--color-red);
  padding: 24px;
  position: relative;
}
.tac-card::before {
  content: attr(data-index);
  font-family: var(--font-mono);
  color: var(--color-red);
  font-size: 12px;
  letter-spacing: 0.2em;
}
```

---

## 7. STRUKTUR SLIDE (TEMPLATE UMUM)

Gunakan struktur ini sebagai kerangka, isi kontennya menyesuaikan topik presentasimu:

1. **Cover** — Judul besar gaya HUD, sub-label mission-brief (nama tugas/mata kuliah), background ink + grid.
2. **Latar Belakang / Objective** — Statement singkat + ringkasan konteks, split-screen: teks besar kiri, ringkasan/data kanan.
3. **Peta / Linimasa (Timeline)** — Alur kronologis dengan panah taktik putus-putus menghubungkan tiap titik peristiwa/tahapan.
4. **Strategi / Poin Utama** — Grid kartu (2–4 kolom) berisi poin-poin pendekatan/karakteristik, tiap kartu diberi nomor mono.
5. **Konsep / Insight Kunci** — Statement besar dengan 1 anotasi tulisan tangan sebagai penekanan emosional/kesimpulan.
6. **Data / Refleksi (Q&A atau Statistik)** — Layout bersih, background terang, cocok untuk highlight angka besar atau kutipan.
7. **Penutup** — Statement penutup + kutipan singkat, background gelap, aksen merah dominan.

---

## 8. FONT PAIRING (Google Fonts — gratis & mirip nuansa Valorant)

| Peran        | Font                          | Alasan |
|--------------|--------------------------------|--------|
| Display/Headline | **Anton** atau **Bebas Neue** | Kondensasi ultra-bold, mirip nuansa "Tungsten" khas HUD Valorant |
| Body/Label   | **Rajdhani**                   | Geometris-teknis, umum dipakai desain esport/HUD |
| Anotasi Tangan | **Permanent Marker** / **Caveat** | Terasa seperti coretan spidol asli di whiteboard |
| Data/Mono    | **JetBrains Mono** / **Space Mono** | Untuk angka, koordinat, label status |

```html
<link href="https://fonts.googleapis.com/css2?family=Anton&family=Rajdhani:wght@500;700&family=Permanent+Marker&family=JetBrains+Mono:wght@500;700&display=swap" rel="stylesheet">
```

---

## 9. ATURAN "JANGAN"

* Jangan pakai lebih dari **1 font marker per slide** — over-use bikin terasa berantakan, bukan tegas.
* Jangan taruh coretan tangan di atas teks body panjang — hanya untuk aksen kata/angka.
* Jangan campur lebih dari 3 warna aksen (`red`, `teal`, `amber`) dalam satu slide — pilih 1 aksen dominan per slide.
* Jangan gunakan logo, ikon senjata, atau aset resmi dari Valorant/Riot Games — semua elemen di panduan ini adalah **gaya visual generik terinspirasi tactical-HUD**, bukan reproduksi aset berlisensi.

---

## 10. QUICK REFERENCE — CONTOH KOMBINASI SLIDE

```css
/* Contoh: Slide "Strategi Utama" */
.slide-strategy {
  background: var(--color-steel);
  color: var(--color-bone);
  position: relative;
  overflow: hidden;
}
.slide-strategy h1 {
  font-family: var(--font-display);
  font-size: clamp(48px, 8vw, 120px);
  transform: skewX(-4deg);
  color: var(--color-bone);
}
.slide-strategy h1 .highlight {
  color: var(--color-red);
}
.slide-strategy .annotation {
  font-family: var(--font-marker);
  color: var(--color-amber);
  font-size: 28px;
  transform: rotate(-4deg);
}
```

---

Panduan ini bisa langsung dipakai sebagai referensi saat membangun deck (HTML/CSS scroll-presentation, atau diterjemahkan manual ke PowerPoint dengan warna & font yang sama). Kalau mau, aku bisa lanjut buatkan **contoh slide HTML interaktif** atau **file .pptx** berdasarkan guideline ini.
