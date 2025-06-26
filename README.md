# FinSight: Aplikasi Manajemen Keuangan dan Rekomendasi Bisnis Berbasis AI untuk UMKM

# Link Hosting: https://finsightv2-production.up.railway.app/

# Anggota Kelompok: 
1. Farhan Arya Wicaksono (5054231011)
2. Muhammad Naufal Arifin (5054231006)
3. Jeremiah Kevin Alexander Jagardo Malau (5054231027)

FinSight adalah sebuah aplikasi web yang dirancang khusus untuk membantu para pelaku Usaha Mikro, Kecil, dan Menengah (UMKM) di Indonesia dalam mengelola keuangan mereka dengan lebih cerdas. Tidak hanya sebagai alat pencatatan keuangan, FinSight juga dilengkapi dengan fitur-fitur berbasis kecerdasan buatan (AI) untuk memberikan wawasan (insight), prediksi, dan rekomendasi yang dapat membantu pengembangan bisnis.

Aplikasi ini dibangun menggunakan framework FastAPI untuk backend dan Vanilla JavaScript untuk frontend, serta ditenagai oleh database PostgreSQL.

## Fitur Utama

Berikut adalah beberapa fitur unggulan yang ditawarkan oleh FinSight:

  * **Manajemen Keuangan**: Lacak semua pemasukan dan pengeluaran dengan mudah. Aplikasi ini menyediakan fitur untuk mengkategorikan setiap transaksi, sehingga Anda dapat memantau kesehatan finansial bisnis Anda secara real-time.
  * **Dashboard Interaktif**: Visualisasikan data keuangan Anda melalui grafik yang mudah dipahami, seperti grafik arus kas bulanan dan diagram persentase kategori pengeluaran.
  * **Prediksi Arus Kas**: Dapatkan estimasi pemasukan dan pengeluaran untuk bulan berikutnya berdasarkan data historis transaksi Anda. Fitur ini membantu Anda dalam merencanakan keuangan dan mengantisipasi kebutuhan modal di masa depan.
  * **Rekomendasi Usaha Berbasis AI**: Bingung mau memulai atau mengembangkan usaha apa? Cukup masukkan estimasi modal, minat, dan lokasi Anda, maka AI akan memberikan 3 rekomendasi usaha yang paling sesuai.
  * **Analisis Kelayakan Usaha**: Sebelum mengambil keputusan besar, gunakan kalkulator analisis kelayakan untuk menghitung potensi profit, ROI (Return on Investment), dan BEP (Break-Even Point) dari sebuah ide bisnis. Fitur ini juga dilengkapi dengan insight dari AI untuk memberikan analisis yang lebih mendalam.
  * **Komunitas FinSight**: Terhubung dengan sesama pelaku UMKM, berbagi pengalaman, tips, atau bertanya melalui fitur komunitas. Anda dapat membagikan pencapaian, cerita, atau pertanyaan dan berinteraksi dengan pengguna lain.
  * **Laporan Keuangan PDF**: Unduh laporan keuangan dalam format PDF untuk periode waktu yang Anda tentukan. Laporan ini mencakup ringkasan, rincian transaksi, dan dapat digunakan untuk berbagai keperluan bisnis.

## Tampilan Aplikasi

Berikut adalah beberapa tampilan dari aplikasi FinSight:

  * **Halaman Landing**:
    *Halaman utama yang menjelaskan fitur dan manfaat FinSight bagi pengguna baru.*

  * **Dashboard Utama**:
    *Tampilan ringkasan kondisi keuangan bisnis, termasuk total pemasukan, pengeluaran, dan grafik arus kas.*

## Teknologi yang Digunakan

Proyek ini dibangun dengan menggunakan teknologi modern, antara lain:

  * **Backend**:
      * Python 3
      * FastAPI
      * SQLAlchemy (ORM)
      * PostgreSQL
      * Uvicorn (ASGI Server)
      * Passlib & python-jose (untuk otentikasi dan keamanan)
      * ReportLab (untuk generate PDF)
  * **Frontend**:
      * HTML5
      * CSS3 (dengan TailwindCSS)
      * Vanilla JavaScript (ES6 Modules)
      * Chart.js (untuk visualisasi data)
      * Lucide Icons
  * **Lainnya**:
      * Docker & Docker Compose
      * OpenRouter AI (untuk layanan LLM)

## Cara Menjalankan Proyek Secara Lokal

Ada dua cara untuk menjalankan proyek ini di lingkungan lokal Anda.

### Opsi 1: Menggunakan Docker Compose (Direkomendasikan)

Ini adalah cara termudah karena semua layanan (aplikasi web dan database) akan diatur secara otomatis.

1.  **Pastikan Docker sudah terinstal** di sistem Anda.
2.  **Clone repositori ini**.
3.  **Buat file `.env`** di direktori utama proyek, salin dari contoh di bawah, dan sesuaikan jika perlu.
4.  **Jalankan perintah berikut** di terminal Anda:
    ```bash
    docker-compose up -d --build
    ```
5.  Aplikasi akan berjalan di `http://localhost:8000`.

### Opsi 2: Setup Manual

Jika Anda tidak ingin menggunakan Docker, ikuti langkah-langkah berikut:

1.  **Clone repositori ini**.
2.  **Setup Lingkungan Python**:
    ```bash
    # Buat virtual environment
    python -m venv venv

    # Aktifkan (di Windows)
    venv\Scripts\activate

    # Aktifkan (di macOS/Linux)
    source venv/bin/activate

    # Install semua dependensi
    pip install -r requirements.txt
    ```
3.  **Setup Database PostgreSQL**: Pastikan Anda memiliki PostgreSQL yang berjalan di sistem Anda. Buat database baru (misalnya, `finsight_db`) dan jalankan skrip `finsight_db_schema.sql` untuk membuat semua tabel yang diperlukan.
4.  **Konfigurasi Environment**: Buat file `.env` di direktori utama dan isi dengan konfigurasi yang sesuai:
    ```env
    DATABASE_URL=postgresql://username:password@localhost:5432/finsight_db
    SECRET_KEY=kunci-rahasia-anda-yang-sangat-aman
    ENVIRONMENT=development
    BASE_URL=http://localhost:8000
    OPENROUTER_API_KEY=kunci-api-openrouter-anda
    MODEL_NAME=meta-llama/llama-4-scout:free
    ```
5.  **Jalankan Aplikasi**:
    ```bash
    uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
    ```
6.  Akses aplikasi melalui `http://localhost:8000`.

## Kredensial Login Default

Untuk mencoba aplikasi, Anda bisa menggunakan kredensial berikut atau mendaftar akun baru:

  * **Email**: `user@finsight.com`
  * **Password**: `password123`

## Struktur Proyek

```
/
├── app/                  # Direktori utama kode backend
│   ├── routers/          # File-file routing untuk setiap fitur
│   ├── services/         # Logika untuk berinteraksi dengan layanan eksternal (AI)
│   ├── __init__.py
│   ├── auth.py           # Logika otentikasi JWT
│   ├── config.py         # Konfigurasi aplikasi
│   ├── crud.py           # Fungsi Create, Read, Update, Delete ke database
│   ├── database.py       # Koneksi dan sesi database
│   ├── main.py           # Entry point aplikasi FastAPI
│   ├── models.py         # Model data SQLAlchemy
│   └── schemas.py        # Skema data Pydantic
├── static/               # File-file frontend (CSS, JS, gambar)
│   ├── js/
│   └── css/
├── .env                  # File konfigurasi (tidak ada di repo)
├── docker-compose.yml    # Konfigurasi Docker Compose
├── Dockerfile            # Instruksi untuk membangun image Docker
├── finsight_db_schema.sql # Skema database
├── index.html            # Halaman utama aplikasi
├── landing.html          # Halaman landing untuk pengunjung
└── requirements.txt      # Daftar dependensi Python
```

Semoga dokumentasi ini bermanfaat\!
