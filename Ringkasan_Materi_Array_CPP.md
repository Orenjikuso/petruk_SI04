# Ringkasan Materi & Panduan Slide: ARRAY dalam C++

> Disusun berdasarkan materi PPT "Fungsi dan Array" (bagian Array), dilengkapi
> tambahan materi yang valid sesuai standar bahasa pemrograman C++.

---

## Bagian A — Ringkasan Materi (Konten)

### 1. Pengertian Array
Array adalah kumpulan data (elemen) yang jumlahnya tetap, disimpan secara
berurutan (contiguous) dalam satu lokasi memori, dan seluruh elemennya
memiliki **tipe data yang sama**. Setiap elemen array dapat diakses melalui
**indeks**, di mana indeks di C++ **selalu dimulai dari 0** (bukan 1).

Format penulisan (array satu dimensi):
```cpp
tipe_data namaArray[ukuranArray];
```
Contoh:
```cpp
int nilai[5];       // array kosong berisi 5 elemen bertipe int
int n[5] = {14, 65, 78, 54, 90};   // array langsung diinisialisasi
```

### 2. Array Statis vs Array Dinamis (istilah dalam materi)
Dalam materi PPT, pembagian ini merujuk pada **cara pengisian nilainya**,
bukan pada alokasi memori (perlu penambahan penjelasan agar tidak rancu
dengan istilah *dynamic array* yang sesungguhnya di C++ — lihat Bagian B):

- **"Array statis"** → nilai elemen langsung ditulis saat deklarasi
  (inisialisasi literal), contoh: `int n[5] = {14,16,78,54,90};`
- **"Array dinamis"** (dalam konteks PPT) → nilai elemen diisi lewat input
  pengguna menggunakan perulangan `for` dan `cin`, contoh:
  ```cpp
  int i, a[7];
  for (i = 0; i < 7; i++) {
      cout << "A[" << i << "] = ";
      cin >> a[i];
  }
  ```

### 3. Keuntungan Array dibanding Variabel Biasa
Materi PPT membandingkan penulisan program **tanpa array** (setiap data
memakai variabel terpisah, sehingga hanya nilai terakhir yang tersimpan)
dengan **menggunakan array** (semua nilai tersimpan dan dapat diakses
kembali melalui indeks). Ini menegaskan tujuan utama array: menyimpan
banyak data sejenis secara efisien dan terstruktur.

### 4. Mengakses dan Menampilkan Elemen Array
Elemen array diakses dengan `namaArray[indeks]`, biasanya dikombinasikan
dengan perulangan `for`:
```cpp
for (int j = 0; j < 5; j++)
    cout << "Nilai ke " << j << " adalah : " << n[j] << '\n';
```

---

## Bagian B — Penambahan Materi (Valid, sesuai standar C++)

Bagian ini melengkapi materi PPT agar lebih lengkap dan akurat secara teknis.

### 1. Array Multidimensi (Array Dua Dimensi)
C++ mendukung array lebih dari satu dimensi, umum digunakan untuk data
berbentuk tabel/matriks.
```cpp
tipe_data namaArray[baris][kolom];

int matrix[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};

for (int i = 0; i < 2; i++) {
    for (int j = 0; j < 3; j++)
        cout << matrix[i][j] << " ";
    cout << endl;
}
```

### 2. Array of Characters (C-String)
Array bertipe `char` yang diakhiri karakter null (`'\0'`) dapat digunakan
sebagai representasi string gaya C:
```cpp
char nama[20] = "Andi";   // otomatis ditambahkan '\0' di akhir
cout << nama;
```

### 3. Ukuran Array Harus Konstanta (pada array statis biasa)
Pada array C++ standar (bukan dinamis), ukuran array **harus diketahui saat
kompilasi** (compile-time constant):
```cpp
const int N = 5;
int data[N];   // valid
// int data[n]; // TIDAK valid jika n adalah variabel biasa (pra-C++ standar VLA)
```

### 4. Array Sesungguhnya Bersifat Statis (Fixed-Size)
Perlu diluruskan: array bawaan C++ (`int arr[n]`) bersifat **statis** —
ukurannya tetap dan ditentukan sejak awal, tidak bisa diperbesar/diperkecil
saat program berjalan. Untuk kebutuhan ukuran yang berubah-ubah (array yang
benar-benar dinamis), C++ menyediakan:

**a. Alokasi dinamis dengan `new` / `delete`:**
```cpp
int ukuran;
cin >> ukuran;
int* arr = new int[ukuran];   // alokasi di heap saat runtime
// ... gunakan arr[i] ...
delete[] arr;                 // wajib dibebaskan agar tidak memory leak
```

**b. `std::vector` (direkomendasikan pada C++ modern):**
```cpp
#include <vector>
using namespace std;

vector<int> data;             // ukuran bisa berubah otomatis
data.push_back(10);
data.push_back(20);
cout << data.size();          // jumlah elemen saat ini
```
`vector` lebih aman dan fleksibel dibanding array biasa karena mengelola
memori secara otomatis dan menyediakan fungsi bawaan seperti `.size()`,
`.push_back()`, `.at()`.

### 5. Operasi Umum pada Array
- **Mencari nilai maksimum/minimum**
- **Mencari total/rata-rata elemen**
- **Pencarian (searching)**: Linear Search, Binary Search
- **Pengurutan (sorting)**: Bubble Sort, Selection Sort, dll.
- **Passing array ke fungsi**: array otomatis dilewatkan sebagai referensi
  (pointer), sehingga perubahan pada elemen array di dalam fungsi akan
  mempengaruhi array aslinya:
  ```cpp
  void tampilkan(int arr[], int n) {
      for (int i = 0; i < n; i++)
          cout << arr[i] << " ";
  }
  ```

### 6. Risiko Out-of-Bounds
C++ **tidak melakukan pengecekan batas indeks secara otomatis**. Mengakses
indeks di luar ukuran array (misalnya `arr[10]` pada array berukuran 5)
menyebabkan *undefined behavior* dan berpotensi merusak data lain di memori.
Ini adalah salah satu alasan `std::vector` (dengan `.at()`) lebih disarankan
untuk kode yang mengutamakan keamanan.

---

## Bagian C — Panduan Penyusunan Materi Per Slide

Berikut struktur slide yang disarankan untuk menyampaikan materi Array
secara berurutan dan mudah dipahami.

| Slide | Judul Slide | Isi / Poin Utama |
|---|---|---|
| 1 | **ARRAY** (judul bab) | Judul besar "ARRAY", sebagai pembuka topik baru setelah materi Fungsi |
| 2 | **Pengertian Array** | Definisi array: kumpulan data sejenis berurutan dalam memori, diakses via indeks (mulai dari 0) |
| 3 | **Format Penulisan Array** | Sintaks `tipe_data namaArray[ukuran];` + contoh deklarasi kosong dan langsung berisi nilai |
| 4 | **Perbandingan: Tanpa Array vs Dengan Array** | Tampilkan 2 potongan kode berdampingan untuk menunjukkan kelemahan variabel biasa (data lama tertimpa) vs keunggulan array (semua data tersimpan) |
| 5 | **Contoh Array dengan Inisialisasi Langsung** | Kode `int n[5] = {14,65,78,54,90};` beserta loop `for` untuk menampilkan isi array |
| 6 | **Contoh Array dengan Input dari User** | Kode menggunakan `cin >> a[i]` di dalam `for`, lalu ditampilkan kembali di loop `for` kedua |
| 7 | **Mengakses Elemen Array** | Penjelasan indeks dimulai dari 0, cara membaca dan menulis nilai elemen |
| 8 | **Array Dua Dimensi (Tambahan)** | Sintaks `tipe[baris][kolom]`, contoh matriks & nested loop untuk menampilkan isinya |
| 9 | **Array of Characters / C-String (Tambahan)** | Contoh `char nama[20] = "Andi";` sebagai pengantar hubungan array dengan string |
| 10 | **Array Statis vs Alokasi Dinamis (Tambahan, Pelurusan Konsep)** | Jelaskan array biasa bersifat *fixed-size*; perkenalkan `new`/`delete` dan `std::vector` sebagai solusi ukuran fleksibel |
| 11 | **Operasi Umum pada Array (Tambahan)** | Ringkas: mencari max/min, total/rata-rata, searching, sorting, passing array ke fungsi |
| 12 | **Peringatan: Out-of-Bounds (Tambahan)** | Jelaskan risiko akses indeks di luar batas array dan pentingnya validasi ukuran |
| 13 | **TUGAS KELOMPOK** | Soal aplikasi kasir: tampilkan menu & harga, pilih makanan/minuman, hitung total harga, input uang bayar, tampilkan kembalian/kekurangan — dapat memakai array untuk menyimpan daftar menu & harga |

### Catatan Penyusunan
- Gunakan **satu konsep inti per slide** agar audiens tidak kewalahan.
- Setiap slide kode sebaiknya diikuti slide "Keterangan" singkat (seperti pola
  di materi Fungsi), terutama untuk slide 8–10 yang memuat konsep baru.
- Letakkan slide tambahan (8–12) **setelah** materi inti PPT asli (slide 2–7)
  agar alur belajar tetap mengikuti urutan silabus awal, dengan tambahan
  sebagai pendalaman/pengayaan.
- Slide Tugas Kelompok tetap di akhir sebagai penutup & evaluasi praktik.
