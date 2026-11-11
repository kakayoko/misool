# Arfanitha Misool Trip — Website Satu Halaman

Website satu halaman (*single-page standalone website*) untuk bisnis wisata **Arfanitha Misool Trip** di Misool, Raja Ampat, Papua Barat Daya. Dibuat murni dengan HTML, CSS, dan JavaScript tanpa framework atau dependensi berat, mengusung konsep visual **peta laut Misool** (*maritime nautical chart*).

---

## 📁 Struktur File

```
├── index.html        # File utama website (berisi semua HTML, CSS, dan JS)
├── README.md         # Petunjuk penggunaan dan deployment
├── foto/             # Folder foto wisata Misool
│   ├── karawapop.jpg   # Foto laguna hati Karawapop (rasio 4:5 di beranda)
│   ├── profil.jpg      # Foto profil pemandu Arfanitha (rasio 3:4 di About Me)
│   ├── guests-1.jpg    # Foto dokumentasi tamu
│   ├── guests-2.jpg
│   ├── homestay-1.jpg  # Foto penginapan homestay terapung
│   ├── homestay-2.jpg
│   ├── snorkeling-1.jpg# Foto terumbu karang & snorkeling
│   ├── snorkeling-2.jpg
│   ├── scenery-1.jpg   # Foto lanskap tebing karst Misool
│   └── scenery-2.jpg
└── arfanitha-misool-trip.zip # Paket siap pakai / deploy
```

---

## ⚙️ Cara Mengganti Pengaturan

Semua pengaturan utama tersimpan di satu objek `CONFIG` di dalam tag `<script>` file `index.html` (sekitar baris 830).

### 1. Mengganti Nomor WhatsApp & Email

Buka `index.html` dengan teks editor (VS Code, Notepad, dll), lalu cari bagian berikut:

```javascript
const CONFIG = {
  phone: '6281237693078',               // Format internasional tanpa tanda plus (+), contoh: 6281237693078
  displayPhone: '+62 812-3769-3078',     // Format tampilan nomor yang dilihat pengunjung
  email: 'lestaluhusuherni@gmail.com',  // Alamat email Anda
  ...
};
```

Ganti nilai di atas sesuai data baru Anda. Nomor WhatsApp dan email di tombol pemesanan, form, kartu kontak, serta tombol salin otomatis akan tersinkronisasi.

---

### 2. Menambah atau Mengganti Foto Galeri

1. Masukkan file foto baru Anda ke dalam folder `foto/` (misalnya: `guests-3.jpg` atau `homestay-3.jpg`).
2. Buka `index.html`, cari array `CONFIG.gallery`:

```javascript
gallery: [
  // Foto Tamu & Homestay selalu diletakkan paling atas
  {
    type: 'guests',                     // Kategori: 'guests', 'homestay', 'snorkeling', atau 'scenery'
    src: 'foto/guests-3.jpg',           // Lokasi file foto
    r: 1.33,                            // Rasio lebar/tinggi asli (misal 4:3 = 1.33, 16:9 = 1.77, 3:4 = 0.75)
    cap: 'Dokumentasi tamu di laguna karst Misool' // Keterangan foto untuk popup lightbox
  },
  ...
]
```

> **Catatan Resiliensi:** Jika ada file foto yang belum diunggah atau tidak ditemukan, website tidak akan menampilkan icon gambar rusak, melainkan kotak berlabel nautical yang rapi sesuai rasio foto.

---

## 🚀 Cara Menayangkan Website (Gratis)

Karena website ini berformat **murni HTML statis**, Anda tidak membutuhkan server khusus, database, ataupun Node.js.

### Pilihan A: Menayangkan di Netlify (Paling Mudah, 1 Menit)
1. Buka browser dan kunjungi [app.netlify.com/drop](https://app.netlify.com/drop) (login atau daftar gratis).
2. Tarik (*drag & drop*) folder yang berisi `index.html` dan folder `foto/` ke area unggah Netlify Drop.
3. Selesai! Website Anda langsung tayang dengan URL publik instan (misalnya: `https://arfanitha-misool.netlify.app`). Anda juga bisa menghubungkan domain pribadi (seperti `.com` atau `.id`).

### Pilihan B: Menayangkan di GitHub Pages
1. Buat repositori baru di [GitHub.com](https://github.com), misalnya bernama `arfanitha-misool-trip`.
2. Unggah file `index.html` dan folder `foto/` ke branch `main`.
3. Masuk ke tab **Settings** repositori > pilih menu **Pages** di sisi kiri.
4. Pada bagian **Build and deployment > Source**, pilih **Deploy from a branch**, lalu pilih branch `main` dan folder `/ (root)`.
5. Klik **Save**. Dalam 1-2 menit, website Anda aktif di `https://username.github.io/arfanitha-misool-trip/`.

---

## 🎨 Fitur Khusus Website

- **Peta Laut Misool Aesthetic**: Pita beranda biru laut dalam (`#0B3340`) dengan siluet karst vektor SVG, background buih laut (`#EDF3F1`), teal brand (`#0B7A85`), dan aksen jingga senja (`#C9431D`) khusus WhatsApp.
- **Tipografi Google Fonts**: *Bricolage Grotesque* untuk judul, *Figtree* untuk teks utama, dan *IBM Plex Mono* untuk koordinat/label maritim.
- **Form Pemesanan Cerdas**: Menyusun pesan WhatsApp otomatis dalam Bahasa Inggris. Bidang jumlah malam (*nights*) hanya muncul jika memilih layanan *Homestay booking*. Terdapat validasi nama wajib diisi.
- **Mode Gelap / Terang**: Otomatis mengikuti pengaturan perangkat (`prefers-color-scheme`) dan dapat diganti secara manual melalui tombol ikon di pojok kanan atas.
- **Aksesibilitas & Keyboard Friendly**: Tombol salin clipboard memiliki fallback otomatis, modal lightbox mendukung tombol `Esc` dan panah keyboard, serta menghormati `prefers-reduced-motion`.
- **Tombol WhatsApp Mengambang**: Tombol mengambang di pojok kanan bawah yang ramah sentuhan tanpa mengganggu konten.
