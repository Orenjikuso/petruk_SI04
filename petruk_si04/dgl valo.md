# 🎯 Design Guideline PPT: Tactical C++ Programming
**Role:** Pemateri Utama / Asisten Praktikum  
**Materi:** Pemrograman Terstruktur C++  
**Tema Visual:** IDE Dark Mode x Valorant Tactical UI  

---

## 1. Filosofi Desain (The Concept)
Presentasi ini bukan diskusi santai, melainkan **Pemaparan Materi Akademik**. Oleh karena itu, desain harus terlihat **profesional, bersih, fokus pada kode (legible)**, namun tetap memiliki aksen *edgy* ala antarmuka (UI) Valorant untuk menjaga perhatian mahasiswa. 
Kita akan menggunakan pendekatan "Tactical Operation" di mana setiap konsep C++ diibaratkan sebagai taktik atau *skill* dalam menyelesaikan misi (program).

---

## 2. Palet Warna (Color Palette)
Gunakan kombinasi warna tema *Dark Mode* pada IDE (seperti VS Code) yang dipadukan dengan aksen warna Valorant.

* **Background Utama:** `#0F1923` (Valorant Dark Navy) - Sangat nyaman di mata untuk menampilkan teks kode yang panjang.
* **Warna Teks Utama (Body):** `#ECE8E1` (Off-White) - Untuk teks penjelasan materi.
* **Aksen Primer (Highlight/Judul):** `#00599C` (C++ Blue) - Identitas asli bahasa C++.
* **Aksen Sekunder (Alert/Error):** `#FF4655` (Valorant Red) - Gunakan HANYA untuk menunjukkan *Error*, peringatan, atau poin krusial.
* **Aksen Tersier (Success/Output):** `#00F5FF` (Neon Cyan) - Gunakan untuk menunjukkan hasil *Output* program yang sukses.

---

## 3. Tipografi (Typography)
Pastikan teks kode bisa dibaca dengan jelas dari kursi paling belakang di kelas.

* **Judul Slide (Heading):** `Oswald` atau `Tungsten` (Bold, Uppercase, Spasi huruf agak renggang).
* **Teks Penjelasan (Body):** `Inter` atau `Segoe UI` (Regular, ukuran minimal 20pt).
* **Teks Kode (Code Snippets):** `Fira Code` atau `Consolas` (Monospace, ukuran minimal 18pt). *Wajib monospace agar rapi.*

---

## 4. Penggunaan Aset Ikon (SVG Folder Integration)
Karena Anda sudah menyiapkan ikon *skill* Valorant di *path* lokal Anda:
`C:\laragon\www\kuliah\asprak\petruk_si04\svg`

Kita akan memetakan ikon-ikon tersebut ke konsep Pemrograman Terstruktur C++. **Gunakan fitur "Insert > Pictures > This Device" di PowerPoint untuk memasukkan file `.svg` tersebut (PowerPoint modern mendukung SVG dan warnanya bisa diubah).**

### 🗺️ Pemetaan Ikon Skill Valorant ke Konsep C++:

1.  **Initiator (Mencari Info / Memulai):** * *Ikon:* Mata Sova / Drone / Flash.
    * *Materi C++:* **Input & Output (`cin` & `cout`)**, Deklarasi Variabel, dan Tipe Data.
    * *Filosofi:* Mengumpulkan data dari *user* dan menampilkannya, langkah awal sebuah program.
2.  **Sentinel (Bertahan / Kondisional):**
    * *Ikon:* Trapwire Cypher / Turret Killjoy / Barrier Sage.
    * *Materi C++:* **Control Flow / Percabangan (`if`, `else if`, `switch case`)**.
    * *Filosofi:* Membatasi dan mengarahkan jalannya program berdasarkan kondisi tertentu (menjaga alur kode).
3.  **Duelist (Agresif / Eksekusi Berulang):**
    * *Ikon:* Dash Jett / Blast Pack Raze.
    * *Materi C++:* **Looping / Perulangan (`for`, `while`, `do-while`)**.
    * *Filosofi:* Mengeksekusi blok kode secara cepat dan berulang-ulang hingga target (kondisi) tercapai.
4.  **Controller (Membagi Area / Modularitas):**
    * *Ikon:* Smoke Omen / Viper Wall.
    * *Materi C++:* **Fungsi (Functions / Void) & Struct**.
    * *Filosofi:* Memecah program menjadi bagian-bagian kecil (memblokir area masalah) agar kode lebih rapi dan bisa digunakan ulang.

---

## 5. Struktur & Tata Letak Slide (Slide Layouts)

### A. Slide Judul (Title Slide)
* **Kiri:** Teks "PERTEMUAN X: PEMROGRAMAN TERSTRUKTUR C++" dengan font judul yang besar. Tambahkan garis vertikal tebal berwarna biru C++ di sebelah teks.
* **Bawah:** Nama Anda ("Pemateri: [Nama Anda]") dan logo Universitas/Fakultas.
* **Kanan:** Elemen grafis minimalis (garis sudut 45 derajat ala HUD Valorant).

### B. Slide Agenda (Mission Briefing)
* Gunakan *list* dengan ikon kotak-kotak kecil.
* Beri judul: "MISSION BRIEFING" atau "AGENDA HARI INI".

### C. Slide Penjelasan Konsep (Theory Slide)
* **Kiri:** Penjelasan teks 2-3 poin penting (jangan terlalu banyak teks).
* **Kanan:** Ikon SVG Valorant berukuran sedang sebagai visualisasi analogi (misal: ikon Sentinel untuk menjelaskan `if-else`).

### D. Slide Kode (Execution Slide)
* Ini adalah slide paling penting.
* Gunakan bentuk kotak dengan sudut yang tajam (tanpa *rounded corner*) dan *background* hitam pekat (`#000000`) untuk meletakkan kode C++.
* Beri *header* kecil pada kotak kode bertuliskan `main.cpp`.
* Berikan kotak *highlight* (kotak transparan dengan pinggiran merah/cyan) pada baris kode yang sedang Anda jelaskan.

---

## 6. Tips Tambahan Saat Presentasi
1.  **Gunakan *Syntax Highlighting*:** Saat menyalin kode ke PPT, pastikan warna *keyword* C++ (`int`, `return`, `include`) berbeda dengan warna string (`"Halo"`). Anda bisa *copy-paste* langsung dari VS Code untuk mempertahankan warna kodenya.
2.  **Transisi Minimalis:** Jangan gunakan animasi rumit. Gunakan transisi *Fade* atau *Push* ke atas secara cepat untuk memberikan kesan antarmuka digital yang responsif.
3.  **Sikap (Attitude):** Anda menggantikan dosen, jadi pertahankan wibawa. Gunakan analogi game ini HANYA sebagai jembatan untuk mempermudah logika mahasiswa, tapi fokus utama tetap pada kebenaran sintaks dan logika pemrograman C++.