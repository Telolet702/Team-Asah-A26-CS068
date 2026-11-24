# Team-Asah-A26-CS068
# 🍜 Sistem Kasir Digital & Asisten Rekap AI — Mie Ayam Paddock Blatuk

**Capstone Project Asah 2026 (led by Dicoding supported by GoTo)**

* **ID Tim:** `A26-CS068`

* **Mitra UMKM:** Mie Ayam Paddock Blatuk (Bidang Kuliner)

* **Judul Use Case:** Digitalisasi Sistem Pemesanan Kasir untuk Mempercepat Alur Transaksi pada UMKM Mie Ayam Paddock

## 📋 Deskripsi Proyek

Warung **Mie Ayam Paddock Blatuk** menghadapi kendala operasional utama berupa pencatatan pesanan dan perhitungan pembayaran yang masih dilakukan secara manual menggunakan kertas dan kalkulator fisik. Hal ini memicu antrean panjang saat jam sibuk (*peak hours*), risiko kesalahan hitung (*human error*), serta proses rekapitulasi penjualan bulanan yang memakan waktu.

Aplikasi berbasis web ini dikembangkan sebagai solusi kasir digital (POS) sederhana yang terintegrasi dengan analitik penjualan dan asisten AI untuk mempercepat alur transaksi kasir maupun mempermudah pemantauan bisnis bagi pemilik warung.

### ✨ Fitur Utama (MVP)

1. **Katalog Menu & Pencatatan Pesanan Digital:** Pemilihan menu, pengaturan jumlah item, dan pengiriman pesanan langsung ke antrean kasir tanpa kertas.

2. **Kalkulasi Otomatis & Split Bill:** Perhitungan total pesanan otomatis, kembalian tunai, serta fitur pemisahan tagihan (*split bill*) untuk satu pesanan.

3. **Antrean Real-Time & Riwayat Transaksi:** Pemantauan status pesanan masuk hingga konfirmasi pembayaran (Tunai / QRIS) yang tersimpan otomatis ke riwayat harian.

4. **Dashboard Ringkasan Penjualan (Data Science):** Visualisasi total pendapatan, jumlah transaksi, menu terlaris, dan tren harian berdasarkan filter rentang tanggal.

5. **Asisten Rekap & Rekomendasi Bundling (AI Engineer):** Layanan berbasis **Gemini API** untuk tanya jawab rekapitulasi penjualan bagi pemilik serta rekomendasi paket menu (*bundling*).

## 📁 Struktur Folder Repositori

Pembagian direktori disesuaikan dengan alur kerja masing-masing *learning path* agar kolaborasi berjalan paralel tanpa konflik kode:

```
Team-Asah-A26-CS068/
├── frontEnd/          # Antarmuka Web POS (Kasir, Split Bill, Antrean, & Tampilan Dashboard)
├── backEnd/           # RESTful API, logika transaksi, koneksi database, & layanan produksi Gemini API
├── dataScience/       # Dataset transaksi 30 hari (.csv), notebook EDA (.ipynb), & validasi metrik dashboard
├── genAi/             # Notebook eksperimen prompt LLM, prototipe bundling, & evaluasi 15 skenario uji
├── docs/              # Dokumentasi teknis, kontrak API, panduan pengguna (kasir/pemilik), & hasil pengujian
├── .env.example       # Template variabel lingkungan (API Key & konfigurasi database)
├── .gitignore         # Daftar file/folder yang dikecualikan dari Git (termasuk .env asli)
└── README.md          # Dokumentasi utama proyek

```

## 🚀 Cara Menjalankan Proyek (Lokal)

### 1. Prasyarat

Pastikan perangkat Anda sudah terinstal:

* **Git** & **GitHub Desktop**

* **Node.js** (v18+ disarankan)

* **Python** (v3.10+)

### 2. Clone Repositori

```
git clone https://github.com/Telolet702/Team-Asah-A26-CS068.git
cd Team-Asah-A26-CS068

```

### 3. Konfigurasi Environment Variable (`.env`)

Salin file `.env.example` menjadi file baru bernama `.env` di folder utama (*root*), lalu isi dengan kredensial yang dibagikan di grup tim:

```
cp .env.example .env

```

Contoh isi variabel di dalam `.env`:

```
GEMINI_API_KEY=masukkan_api_key_gemini_anda
DATABASE_URL=sqlite:///kasir_paddock.db
PORT=5000

```

> ⚠️ **Penting:** Jangan pernah mengunggah (*commit/push*) file `.env` asli ke GitHub.

### 4. Menjalankan Layanan Aplikasi (2 Terminal)

Karena kode produksi Gemini API (asisten rekap pesanan & rekomendasi *bundling*) digabungkan ke dalam server *backend*, tim maupun penguji cukup menjalankan **dua layanan** berikut secara bersamaan:

* **Terminal 1 — Server Back-End & AI (`backEnd/`):**
  Menjalankan RESTful API untuk transaksi kasir, *split bill*, koneksi *database*, dan *endpoint* Gemini API.

  ```
  cd backEnd
  # Perintah instalasi & jalankan server menyusul setelah framework disepakati
  # Contoh Node.js : npm install && npm run dev
  # Contoh Python  : pip install -r requirements.txt && uvicorn main:app --reload
  
  ```

* **Terminal 2 — Antarmuka Web (`frontEnd/`):**
  Menjalankan server tampilan web untuk halaman pemesanan kasir, antrean transaksi, dan *dashboard* penjualan.

  ```
  cd frontEnd
  # Perintah instalasi & jalankan server menyusul setelah framework disepakati
  # Contoh: npm install && npm run dev
  
  ```

### 5. Menjalankan Notebook Analisis & Eksperimen (`dataScience/` & `genAi/`)

Untuk keperluan *Exploratory Data Analysis* (EDA), validasi metrik *dashboard*, maupun pengujian *prompt* LLM, buka file `.ipynb` pada folder `dataScience/` dan `genAi/` menggunakan **Google Colab** atau **Jupyter Notebook**.

## 🌐 Catatan Rencana Deployment (Vercel) 

Masih rencana mau pakai vercel atau tidak nanti di diskusikan lagi oke.

Untuk kebutuhan demo online pada Minggu ke-3, repositori ini akan di-*deploy* ke **Vercel** sebagai dua proyek terpisah dari satu repositori yang sama:

1. **Proyek Back-End (`Root Directory: backEnd`):** Menjalankan API transaksi & Gemini API (perlu konfigurasi CORS, `vercel.json`, serta migrasi *database* dari SQLite lokal ke PostgreSQL gratis seperti Supabase/Neon).

2. **Proyek Front-End (`Root Directory: frontEnd`):** Menjalankan antarmuka web utama yang terhubung ke URL *back-end* melalui *Environment Variables*.

## 👥 Daftar Anggota Tim (`A26-CS068`)

| ID Peserta | Nama Lengkap | Learning Path | Fokus Tanggung Jawab | 
| ----- | ----- | ----- | ----- | 
| `` | **Muhammad Adzan Putra Pratama** | Full Stack Developer (FS) | Database menu, logika *split bill*, konfirmasi pembayaran, & dokumentasi teknis | 
| `` | **Syawe Manisha P. Siregar** | Full Stack Developer (FS) | Pencatatan pesanan, kalkulasi otomatis, riwayat harian, UI responsif, & koordinator demo UMKM | 
| `` | **Nadila Putri** | Data Science (DS) | Penyusunan dataset transaksi 30 hari, analisis awal (EDA), & dokumentasi | 
| `` | **Rahma** | Data Science (DS) | Agregasi metrik penjualan, *dashboard* ringkasan penjualan, & panduan pengguna | 
| `` | **Ahmad Khumaeni Gibran** | AI Engineer (AE) | Arsitektur layanan Gemini API, pengamanan *API key*, & rekomendasi *bundling* | 
| `` | **Aden Teguh Tri Satrio** | AI Engineer (AE) | Pengembangan asisten rekap pesanan berbasis LLM, evaluasi 15 skenario uji, & rekomendasi *bundling* | 

## 🤝 Aturan Kolaborasi Git (Alur Kerja Tim)

1. **Jangan melakukan *push* langsung ke `main`.** Selalu buat *branch* baru dari `main` sebelum mengerjakan tugas.

2. **Konvensi Penamaan Branch:**

   * `feat/<nama-fitur>` — Pengembangan fitur aplikasi (`frontEnd/` & `backEnd/`)

   * `data/<nama-tugas>` — Pengolahan data & *dashboard* (`dataScience/`)

   * `ai/<nama-modul>` — Integrasi Gemini API & eksperimen AI (`genAi/` & `backEnd/`)

   * `docs/<nama-dokumen>` — Pembaruan dokumentasi & pengujian (`docs/`)

3. **Pull Request (PR):** Setelah selesai *commit* dan *push* ke *branch* masing-masing, buat **Pull Request** di GitHub menuju `main` dan minta minimal 1 rekan tim untuk melakukan *review* sebelum di-*merge*.