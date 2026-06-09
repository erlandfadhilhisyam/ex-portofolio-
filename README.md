Plaintext
================================================================================
                      DOKUMENTASI TEKNIS & ARSITEKTUR KODE
                           PERSONAL PORTFOLIO WEBSITE
================================================================================
Developer   : Erland Fadhil Hisyam                                                                                                                                   Institusi   : SMK Bina Informatika Bintaro
Tech Stack  : HTML5 (Semantic), CSS3 (Vanilla / Custom Properties)
Deployment  : GitHub + Vercel
URL Live    : https://ex-portofolio.vercel.app/
Version     : 1.0.0 (Release)
================================================================================

1. IKHTISAR PROJEK (PROJECT OVERVIEW)
--------------------------------------------------------------------------------
Website ini dikembangkan sebagai platform portofolio digital satu halaman (Single
Page Application) yang responsif. Fokus utama dari proyek ini adalah menyediakan
antarmuka web yang bersih, cepat, dan modern untuk mempublikasikan hasil karya,
kompetensi teknis, serta laporan praktikum administrasi jaringan secara daring.

2. STRUKTUR DIREKTORI (DIRECTORY STRUCTURE)
--------------------------------------------------------------------------------
Untuk memastikan seluruh aset (gambar dan dokumen) termuat dengan sempurna di 
sisi klien, pohon direktori pada lingkungan produksi/lokal diatur sebagai berikut:

[portfolio-erland] (Root Directory)
 |
 +-- index.html           # File markup utama, berisi struktur DOM & internal CSS
 +-- README.txt           # File dokumentasi teknis mendalam ini
 +-- foto-erland.jpg      # Kompresi aset gambar profil utama (Aspek Rasio 1:1)
 +-- project1.jpg         # Dokumentasi visual Praktikum SSH Server (Password)
 +-- project2.jpg         # Dokumentasi visual Praktikum SSH Key (Termius)
 +-- project3.jpg         # Dokumentasi visual Praktikum DHCP Server
 +-- project4.jpg         # Dokumentasi visual Praktikum FTP Server

3. ANALISIS ARSITEKTUR KODE (CODE ARCHITECTURE)
--------------------------------------------------------------------------------
A. Struktur HTML5 (Semantic Elements):
   - `<nav>`   : Digunakan untuk area navigasi global dengan mekanisme sticky.
   - `<header>`: Representasi hero-section (intro perkenalan diri).
   - `<section>`: Pembagian modular untuk About, Skills, Projects, dan Contact.
   - `<footer>`: Informasi hak cipta dan kepemilikan projek.

B. Struktur Implementasi CSS3:
   - Reset CSS       : Menggunakan `box-sizing: border-box` untuk konsistensi layout.
   - Typography      : Integrasi font modern dengan fallback sistem sans-serif.
   - Layouting       : Kombinasi Flexbox untuk penataan elemen linear (Nav/Hero) 
                       dan CSS Grid untuk penataan multi-kolom yang dinamis 
                       (Cards pada Section Projects & Skills).
   - Responsive Web  : Menggunakan pendekatan Media Queries untuk memastikan 
                       tampilan optimal di resolusi Mobile, Tablet, dan Desktop.

4. DETAIL INTEGRASI PROJEK PRAKTIKUM (PROJEK SECTION)
--------------------------------------------------------------------------------
Setiap card proyek pada elemen HTML terhubung ke laporan eksternal yang disimpan
di Google Drive melalui atribut jangkar (`<a>`). 

Daftar Modul yang Didokumentasikan:
- Projek 1: Konfigurasi Remote Server SSH pada Ubuntu Server (Autentikasi Password)
- Projek 2: Pengamanan Remote Server dengan Autentikasi SSH Key-Based via Termius
- Projek 3: Konfigurasi dan Implementasi DHCP Server pada Linux Ubuntu
- Projek 4: Konfigurasi File Server Berbasis FTP pada Ubuntu Server

5. RIWAYAT TROUBLESHOOTING (KENDALA & SOLUSI TEKNIS)
--------------------------------------------------------------------------------
Selama fase pengembangan web dan pengujian sistem jaringan, ditemukan beberapa
kendala teknis yang berhasil diselesaikan:

* Kendala 1: Kesalahan parsing tautan (URL) pada file index.html.
  - Deskripsi: Tombol jangkar tidak merespons perintah klik di web browser.
  - Analisis : Terjadi kesalahan penempatan sintaks, di mana URL Google Drive
               secara tidak sengaja dimasukkan ke dalam atribut 'class', sementara 
               atribut 'href' masih bernilai standar ('#').
  - Solusi   : Melakukan refactoring kode dengan memindahkan URL ke dalam atribut
               'href' dan mengembalikan penamaan 'class="project-link"'.

* Kendala 2: Hambatan koneksi remote pada pengujian SSH Server.
  - Deskripsi: Aplikasi PuTTY/Termius pada sistem host gagal melakukan jabat tangan
               (handshake) dengan Ubuntu Server di dalam VirtualBox.
  - Analisis : Pengaturan Network Adapter default menggunakan 'Bridged' yang 
               mengalami konflik alokasi IP pada segmen jaringan lokal.
  - Solusi   : Mengubah konfigurasi jaringan di VirtualBox menjadi 'Host-Only Adapter'
               dan menetapkan IP statis satu segmen antara host dan VM.

6. ALUR DEPLOYMENT (CI/CD PIPELINE)
--------------------------------------------------------------------------------
Proses publikasi website dari lokal ke internet memanfaatkan teknologi modern:
1. Version Control (Git): Kode lokal diinisialisasi dan didorong (push) ke 
   repositori publik di GitHub.
2. Cloud Hosting (Vercel): Repositori GitHub dihubungkan ke platform Vercel. 
   Vercel secara otomatis mendeteksi perubahan file index.html, melakukan build,
   dan mempublikasikannya ke edge network global secara instan.

================================================================================
© 2026 Erland Fadhil Hisyam. Hak Cipta Dilindungi Undang-Undang.
================================================================================
