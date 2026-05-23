# Sistem Informasi Appointment Klinik Kampus

Nama: M. Putra Mulya Pratama  
NIM: 021240083P  
Gemini Link: https://gemini.google.com/share/c62ba0865790

---

## 1. Analisis Masalah

- **Masalah Utama:** Pengelolaan janji temu dan antrean pasien harian masih menggunakan WhatsApp dan pencatatan langsung, sehingga staf administrasi kewalahan dan antrean di klinik sering menumpuk.

- **Penyebab:** Belum ada media informasi terpusat yang dapat diakses bersama untuk melihat jadwal dokter secara langsung. Selain itu, pencatatan kunjungan masih ditulis manual di buku besar.

- **Dampak:** Mahasiswa harus menanyakan jadwal dokter berulang kali melalui pesan teks, waktu tunggu di klinik menjadi lama, dan risiko jadwal bentrok sangat tinggi.

- **Risiko Jika Dibiarkan:** Buku pendaftaran fisik rentan rusak atau hilang, staf klinik terus mengalami kelelahan kerja, dan rekapitulasi data untuk laporan bulanan kampus membutuhkan waktu yang lama serta rawan salah hitung.

- **Solusi Prioritas:** Menyediakan sistem informasi berbasis web yang menyajikan jadwal dokter, fitur pendaftaran janji temu mandiri, halaman pantauan antrean hari berjalan, dan rekapitulasi laporan otomatis.

---

## 2. Kebutuhan Fungsional

Sistem wajib menyediakan fitur-fitur utama berikut:

- **Akses Pengguna (Login):** Mahasiswa masuk ke dalam sistem menggunakan Nomor Induk Mahasiswa (NIM) dan staf klinik menggunakan nama pengguna (username).

- **Informasi Jadwal Dokter:** Menampilkan jadwal praktik dokter yang aktif serta sisa kuota harian yang tersedia.

- **Pendaftaran Janji Temu:** Mahasiswa memilih jadwal dokter dan tanggal kunjungan. Sistem akan langsung menerbitkan nomor antrean secara otomatis jika kuota masih tersedia.

- **Halaman Pantauan Antrean:** Layar monitor digital yang dapat diakses oleh mahasiswa untuk melihat nomor antrean yang sedang dilayani oleh staf atau dokter pada hari tersebut.

- **Pengelolaan Jadwal & Antrean (Sisi Staf):** Menu bagi staf klinik untuk menambah/mengubah jadwal dokter serta memperbarui nomor antrean yang sedang berjalan (Mengubah status dari Terdaftar -> Dipanggil -> Selesai).

- **Laporan Kunjungan Dasar:** Fitur bagi staf klinik untuk melihat dan mengunduh rekap total kunjungan pasien berdasarkan periode waktu tertentu.

---

## 3. Kebutuhan Non-Fungsional

- **Kemudahan Penggunaan:** Tampilan sistem harus sederhana dan responsif agar nyaman dibuka oleh mahasiswa melalui ponsel, serta praktis digunakan oleh staf melalui komputer klinik.

- **Keamanan Dasar:** Pembatasan hak akses yang jelas antara akun mahasiswa dan staf klinik agar data kunjungan tidak disalahgunakan.

- **Performa:** Proses penguncian kuota janji temu berjalan instan agar tidak terjadi nomor antrean ganda untuk satu slot waktu yang sama.

- **Ketersediaan:** Sistem dapat diakses penuh selama 24 jam agar mahasiswa bisa mendaftar janji temu kapan saja, termasuk di luar jam operasional klinik.

- **Kemudahan Akses:** Sistem berbasis web sehingga pengguna cukup membukanya melalui browser internet tanpa perlu mengunduh aplikasi tambahan.

---

## 4. User Stories

### Pasien / Mahasiswa

- Sebagai Pasien/Mahasiswa, saya ingin melihat jadwal dan sisa kuota dokter secara langsung agar saya bisa memilih waktu kunjungan yang tidak bentrok dengan jadwal kuliah.

- Sebagai Pasien/Mahasiswa, saya ingin mendaftar janji temu secara mandiri di sistem agar langsung mendapatkan kepastian nomor antrean tanpa perlu mengirim pesan WhatsApp atau datang pagi-pagi ke klinik.

- Sebagai Pasien/Mahasiswa, saya ingin memantau pergerakan nomor antrean secara online agar saya bisa datang ke klinik tepat waktu dan tidak perlu menunggu lama di ruang tunggu.

### Admin / Staf Klinik

- Sebagai Staf Klinik, saya ingin mengatur dan memperbarui jadwal praktik dokter agar informasi kuota yang dilihat oleh mahasiswa selalu sesuai dengan kondisi di klinik.

- Sebagai Staf Klinik, saya ingin memperbarui status antrean pasien di sistem agar halaman monitor antrean yang dilihat oleh mahasiswa bergerak maju secara aktual.

- Sebagai Staf Klinik, saya ingin menarik data laporan kunjungan secara otomatis agar saya tidak perlu menghitung ulang buku catatan di akhir bulan untuk laporan ke manajemen kampus.

### Dokter

- Sebagai Dokter, saya ingin melihat daftar pasien yang akan datang pada hari tersebut agar saya dapat mengetahui jumlah beban pelayanan dan mempersiapkan diri dengan lebih baik.

---

## 5. Alur Proses Sistem

1. Mahasiswa masuk ke sistem menggunakan NIM.
2. Mahasiswa melihat jadwal dokter dan memilih slot yang kosong.
3. Sistem memvalidasi ketersediaan kuota.
4. Nomor antrean diterbitkan secara otomatis.
5. Mahasiswa memantau antrean secara daring.
6. Staf memanggil pasien dan mengubah status antrean menjadi "Dipanggil".
7. Dokter melakukan pemeriksaan pasien.
8. Setelah selesai, staf mengubah status antrean menjadi "Selesai".
9. Data kunjungan otomatis masuk ke sistem laporan.

---

## 6. Desain Basis Data

### 1. Tabel: `pasien`

| Field | Tipe Data |
|---|---|
| id_pasien | Varchar / Primary Key |
| nama_lengkap | Varchar |
| nomor_telepon | Varchar |
| password | Varchar |

### 2. Tabel: `dokter`

| Field | Tipe Data |
|---|---|
| id_dokter | Integer / Primary Key / Auto Increment |
| nama_dokter | Varchar |
| spesialisasi | Varchar |

### 3. Tabel: `staf`

| Field | Tipe Data |
|---|---|
| id_staf | Integer / Primary Key / Auto Increment |
| username | Varchar |
| nama_staf | Varchar |
| password | Varchar |

### 4. Tabel: `jadwal`

| Field | Tipe Data |
|---|---|
| id_jadwal | Integer / Primary Key / Auto Increment |
| id_dokter | Integer / Foreign Key |
| hari | Varchar |
| jam_mulai | Time |
| jam_selesai | Time |
| kuota_maksimal | Integer |

### 5. Tabel: `appointment`

| Field | Tipe Data |
|---|---|
| id_appointment | Integer / Primary Key / Auto Increment |
| id_pasien | Varchar / Foreign Key |
| id_jadwal | Integer / Foreign Key |
| tanggal_kunjungan | Date |
| nomor_antrean | Integer |
| status_antrean | Varchar |

---

## 7. Daftar Modul / Tampilan

### 1. Halaman Masuk Sistem (Login)

**Fungsi Utama:**  
Pintu masuk aman bagi pengguna untuk mengakses sistem berdasarkan hak akses masing-masing.

**Aktor:**  
Pasien/Mahasiswa dan Staf Klinik.

**Fitur Utama:**  
- Form input NIM/Username
- Form input kata sandi
- Tombol masuk sistem
- Tombol daftar akun mahasiswa baru

### 2. Dashboard Pasien / Mahasiswa

**Fungsi Utama:**  
Halaman utama mahasiswa untuk melihat ringkasan aktivitas janji temu mereka.

**Aktor:**  
Pasien/Mahasiswa.

**Fitur Utama:**  
- Kartu status janji temu aktif
- Riwayat kunjungan
- Tombol pendaftaran janji temu

### 3. Halaman Informasi & Pencarian Jadwal Dokter

**Fungsi Utama:**  
Menyediakan informasi waktu praktik dokter secara aktual agar mahasiswa dapat merencanakan kunjungan.

**Aktor:**  
Pasien/Mahasiswa dan Staf Klinik.

**Fitur Utama:**  
- Filter pencarian dokter
- Filter hari praktik
- Tabel jadwal dokter
- Informasi sisa kuota

### 4. Halaman Pendaftaran Janji Temu (Booking)

**Fungsi Utama:**  
Memfasilitasi mahasiswa untuk melakukan reservasi kuota kunjungan secara mandiri.

**Aktor:**  
Pasien/Mahasiswa.

**Fitur Utama:**  
- Kalender pemilihan tanggal
- Pilihan jadwal dokter
- Ringkasan pendaftaran
- Tombol konfirmasi

### 5. Halaman Pantauan Antrean (Monitor Digital)

**Fungsi Utama:**  
Menampilkan pergerakan antrean pasien secara langsung.

**Aktor:**  
Pasien/Mahasiswa, Staf Klinik, dan Dokter.

**Fitur Utama:**  
- Nomor antrean berjalan
- Daftar antrean tunggu
- Informasi dokter
- Waktu pembaruan antrean

### 6. Dashboard Admin & Manajemen Jadwal

**Fungsi Utama:**  
Pusat kendali operasional klinik bagi staf.

**Aktor:**  
Staf Klinik.

**Fitur Utama:**  
- Kelola jadwal dokter
- Tombol panggil antrean
- Tombol selesai antrean
- Pencarian pasien harian

### 7. Halaman Data Pasien & Riwayat Kunjungan

**Fungsi Utama:**  
Tempat penyimpanan data administratif mahasiswa yang terdaftar.

**Aktor:**  
Staf Klinik dan Dokter.

**Fitur Utama:**  
- Data pasien
- Pencarian pasien
- Riwayat kunjungan

### 8. Halaman Laporan Kunjungan Dasar

**Fungsi Utama:**  
Menyajikan rekapitulasi data kunjungan pasien.

**Aktor:**  
Staf Klinik.

**Fitur Utama:**  
- Filter laporan
- Grafik kunjungan
- Rekap total pasien
- Tombol unduh laporan

---

## 8. Refleksi Penggunaan Gemini

Proses perancangan dokumen analisis kebutuhan ini dibantu oleh Gemini melalui beberapa tahapan iterasi. Gemini membantu menyusun struktur analisis, menjaga konsistensi antarbagian, dan mempercepat proses penyusunan kebutuhan sistem.

Namun, beberapa hasil awal masih terlalu umum dan sempat melebar dari fokus sistem appointment klinik kampus. Oleh karena itu, prompt diperbaiki dan beberapa bagian disesuaikan kembali secara manual agar hasil lebih relevan, natural, dan tetap sesuai dengan batasan sistem.





=================

# Belajar Skill Pemrograman dengan Laravel - Mahasiswa Palcomtech D3 Sistem Informasi

Selamat datang di repositori pembelajaran skill pemrograman terutama dalam penggunaan Laravel, yang dibuat khusus untuk mahasiswa Palcomtech program D3 Sistem Informasi. Repositori ini berisi berbagai informasi, sumber daya, dan contoh yang akan membantu Anda dalam memahami dan menguasai konsep-konsep penting dalam pengembangan web menggunakan Laravel.

## Tentang Repositori Ini

Repositori ini dibuat sebagai panduan belajar untuk membantu mahasiswa Palcomtech D3 Sistem Informasi dalam mempelajari skill pemrograman dengan fokus pada penggunaan Laravel. Di sini Anda akan menemukan:

- Materi belajar tentang dasar-dasar Laravel.
- Contoh kode untuk memahami konsep-konsep penting.
- Referensi ke sumber daya online yang bermanfaat.

## Materi yang Tersedia

Repositori ini mencakup berbagai materi belajar, termasuk:

1. Pengenalan Laravel:
   - Apa itu Laravel dan mengapa itu penting?
   - Instalasi Laravel dan konfigurasi awal.
   
2. Routing dan Views:
   - Membuat route untuk aplikasi web.
   - Membuat dan menggunakan views dalam Laravel.

3. Model-View-Controller (MVC):
   - Memahami konsep MVC dalam konteks Laravel.
   - Membuat dan mengelola model, view, dan controller.

4. Penggunaan Database:
   - Interaksi dengan database menggunakan Eloquent ORM.
   - Migrasi database dan pengelolaan skema.

5. Fitur-Fitur Laravel Lainnya:
   - Validasi data input.
   - Pengelolaan sesi dan autentikasi.
   - Penggunaan middleware untuk memproteksi rute.

6. Pembuatan Aplikasi Sederhana:
   - Langkah-demi-langkah membangun aplikasi web sederhana menggunakan Laravel.

## Cara Menggunakan Repositori Ini

1. Pastikan Anda memiliki pengetahuan dasar tentang PHP dan pemrograman web.
2. Clone repositori ini ke komputer Anda menggunakan perintah berikut: `git clone [URL Repositori]`.
3. Jelajahi direktori-direktori yang berisi materi belajar dan contoh kode.
4. Setiap direktori memiliki README terpisah yang menjelaskan tentang isinya. Bacalah dengan cermat.
5. Lakukan contoh-contoh kode sendiri, eksperimen, dan modifikasi sesuai kebutuhan Anda.
6. Gunakan referensi yang diberikan untuk memperdalam pemahaman Anda tentang Laravel.

## Referensi Tambahan

Selain materi di dalam repositori ini, Anda juga dapat memanfaatkan sumber daya online berikut:

- Dokumentasi Resmi Laravel: [https://laravel.com/docs](https://laravel.com/docs)
- Forum Laravel Indonesia: [https://laravel.web.id](https://laravel.web.id)

## Kontribusi

Jika Anda memiliki perbaikan, tambahan materi, atau saran untuk repositori ini, kami sangat menghargai kontribusi Anda. Silakan buat _pull request_ untuk berdiskusi tentang perubahan yang Anda ingin lakukan.

## Lisensi

Repositori ini dilisensikan di bawah Lisensi MIT. Lihat berkas [LICENSE](LICENSE) untuk informasi lebih lanjut.

---

Semoga repositori ini membantu Anda dalam memahami dan menguasai penggunaan Laravel sebagai mahasiswa Palcomtech D3 Sistem Informasi. Selamat belajar dan selamat mengembangkan aplikasi web Anda!
