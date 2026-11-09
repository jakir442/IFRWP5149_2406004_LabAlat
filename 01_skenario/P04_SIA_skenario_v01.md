<!-- Deskripsi skenario -->

Tugas ini berbeda dari tugas pertemuan sebelumnya. Tugas Pertemuan 2 adalah jadwal kuliah dan tugas Pertemuan 3 adalah pengajuan KRS. Tugas Pertemuan 4 adalah layanan hasil studi, dengan teknik generalization dan collaboration yang sama seperti studi kasus, tetapi diterapkan pada skenario baru tanpa contoh jawaban.
Skenario tugas berikut fiktif untuk praktikum dan berbeda dari tugas Pertemuan 2 (jadwal kuliah) dan Pertemuan 3 (pengajuan KRS).
Mahasiswa dan dosen sama-sama merupakan Civitas Akademika yang dapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir. Mahasiswa melihat Kartu Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan. Admin Akademik mengelola data mahasiswa: menambah data mahasiswa baru, mengubah data mahasiswa, dan menghapus data mahasiswa. Dua use case utama, Input Nilai Mata Kuliah dan Lihat KHS, ditunjukkan realisasinya oleh collaboration yang bersesuaian.


<!-- Kebutuhan -->
| ID      |                                          Kebutuhan tugas 
-----------------------------------------------------------------------------------------------------------------
| SIA-R07 | Mahasiswa dan Dosen, sebagai Civitas Akademika, dapat melihat kalender akademik.                    
| SIA-R08 | Dosen dapat menginput nilai mata kuliah yang diampunya.                                             
| SIA-R09 | Mahasiswa dapat melihat KHS untuk semester yang nilainya sudah dipublikasikan.                      
| SIA-R10 | Admin Akademik dapat mengelola data mahasiswa.                                                      
| SIA-R11 | Pengelolaan data mahasiswa terdiri dari tiga bentuk khusus: tambah, ubah, dan hapus data mahasiswa. 
| SIA-R12 | Model menunjukkan collaboration yang menghubungkan Input Nilai Mata Kuliah dan Lihat KHS.           
----------------------------------------------------------------------------------------------------------------


<!-- Batas dan asumsi -->
• Kode kebutuhan dimulai dari SIA-R07 agar SIA-R01 dan SIA-R02 (Pertemuan 2) serta SIA-R03 sampai SIA-R06 (Pertemuan 3) tetap empunyai identitas berbeda.
• Pengguna telah terautentikasi dan memiliki hak akses sesuai peran.
• Kalender akademik pada tugas ini adalah agenda resmi institusi (awal semester, batas KRS, masa ujian, dan sejenisnya); jangan menyamakannya dengan jadwal kuliah pada Pertemuan 2.
• Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut. Nilai yang diinput belum terpublikasi sebelum dinyatakan resmi oleh ketentuan tugas ini: KHS hanya menampilkan nilai yang sudah dipublikasikan.
• Hapus Data Mahasiswa hanya untuk mahasiswa yang tidak memiliki dataakademik aktif. Ketentuan ini fiktif untuk latihan.
• Pengajuan KRS tetap digambar sebagai bagian diagram kumulatif dari Pertemuan 3. Pembayaran dan perancangan basis data berada di luar tugas ini.


<!-- Identifikasi Aktor -->
Nama Aktor                                   Deskripsi Peran
Mahasiswa                           Melihat kalender akademik dan melihat Kartu Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan.
Admin Akademik                      Mengelola data mahasiswa, meliputi menambah, mengubah, dan menghapus data mahasiswa sesuai ketentuan.
Dosen Wali                          Melihat kalender akademik dan menginput nilai mata kuliah yang diampunya.
Civitas Akademika	                Aktor umum yang mewakili Mahasiswa dan Dosen dalam melihat kalender akademik.


<!-- Identifikasi Aktor dan Use Case SIA -->
|ID        |         Nama Use Case                   |        Peran dalam Model
-----------------------------------------------------------------------------------------------------
| SIA-R01  |  Melihat Jadwal Kuliah                  |  Fungsi utama mahasiswa
| SIA-R02  |  Mengelola Jadwal Kuliah                |  Fungsi utama admin akademik
| SIA-R03  |  Mengajukan KRS                         |  Fungsi utama mahasiswa
| SIA-R04  |  Memvalidasi KRS                        |  Perilaku yang disertakan di SIA-R03
| SIA-R05  |  Mengunduh Bukti Pengajuan              |  Tambahan bersyarat (extend) pada SIA-R03
| SIA-R06  |  Menyetujui / Menolak KRS               |  Fungsi utama dosen wali
| SIA-R07  |  Melihat Kalender Akademik	             |  Fungsi umum Civitas Akademika
| SIA-R08  |  Input Nilai Mata Kuliah	             |  Fungsi utama Dosen
| SIA-R09  |  Lihat KHS	                             |  Fungsi utama Mahasiswa
| SIA-R10  |  Mengelola Data Mahasiswa	             |  Fungsi utama Admin Akademik
| SIA-R11  |  Tambah Data Mahasiswa	                 |  Spesialisasi dari Mengelola Data Mahasiswa
| SIA-R11  |  Ubah Data Mahasiswa	                 |  Spesialisasi dari Mengelola Data Mahasiswa
| SIA-R11  |  Hapus Data Mahasiswa	                 |  Spesialisasi dari Mengelola Data Mahasiswa
| SIA-R12  |  Collaboration Input Nilai & Lihat KHS  |  Menunjukkan hubungan realisasi antar use case
-----------------------------------------------------------------------------------------------------

<!-- Relasi Include dan extend -->
Tetapkan relasi
SIA-R03 «include» SIA-R04
Alasan: pemeriksaan menjadi bagian validasi pengajuan KRS.

SIA-R05  extend   SIA-R03
Extension point: Bukti pengajuan tersedia.
Kondisi: [mahasiswa memilih cetak].
Alasan: pengajuan tetap berhasil tanpa pencetakan.

Generalization (Aktor)
Mahasiswa -> Civitas Akademika
Dosen -> Civitas Akademika
Alasan: Mahasiswa dan Dosen memiliki perilaku umum yang sama, yaitu melihat Kalender Akademik (SIA-R07), sehingga dimodelkan sebagai spesialisasi dari aktor Civitas Akademika.

Generalization (Use Case)
Tambah Data Mahasiswa -> Mengelola Data Mahasiswa
Ubah Data Mahasiswa -> Mengelola Data Mahasiswa
Hapus Data Mahasiswa -> Mengelola Data Mahasiswa
Alasan: Ketiga aktivitas tersebut merupakan bentuk khusus dari proses Mengelola Data Mahasiswa.

Collaboration/Realization 
Input Nilai Mata Kuliah -> Lihat KHS
Alasan: Nilai yang diinput oleh Dosen menjadi data yang dipublikasikan oleh sistem dan kemudian digunakan dalam proses Lihat KHS oleh Mahasiswa.