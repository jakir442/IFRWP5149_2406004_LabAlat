# Studi Kasus Sistem Informasi Akademik (SIA) – Pertemuan 4

## Layanan Hasil Studi

## 1. Deskripsi Skenario

Tugas ini berbeda dari tugas pertemuan sebelumnya. Tugas Pertemuan 2 membahas jadwal kuliah, sedangkan tugas Pertemuan 3 membahas pengajuan Kartu Rencana Studi (KRS). Tugas Pertemuan 4 membahas layanan hasil studi dengan menerapkan teknik _generalization_ dan _collaboration_ pada skenario baru tanpa contoh jawaban.

Skenario berikut bersifat fiktif untuk keperluan praktikum dan berbeda dari skenario Pertemuan 2 dan Pertemuan 3.

Mahasiswa dan dosen merupakan bagian dari **Civitas Akademika** yang dapat melihat kalender akademik. Dosen dapat menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir. Mahasiswa dapat melihat Kartu Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan.

Selain itu, Admin Akademik bertugas mengelola data mahasiswa, yang mencakup penambahan data mahasiswa baru, perubahan data mahasiswa, dan penghapusan data mahasiswa.

Dua use case utama, yaitu **Input Nilai Mata Kuliah** dan **Lihat KHS**, ditunjukkan realisasinya melalui collaboration yang bersesuaian.

## 2. Kebutuhan Sistem

| ID      | Kebutuhan                                                                                                                                 |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| SIA-R07 | Mahasiswa dan Dosen, sebagai Civitas Akademika, dapat melihat kalender akademik.                                                          |
| SIA-R08 | Dosen dapat menginput nilai mata kuliah yang diampunya.                                                                                   |
| SIA-R09 | Mahasiswa dapat melihat KHS untuk semester yang nilainya sudah dipublikasikan.                                                            |
| SIA-R10 | Admin Akademik dapat mengelola data mahasiswa.                                                                                            |
| SIA-R11 | Pengelolaan data mahasiswa terdiri dari tiga bentuk khusus: tambah, ubah, dan hapus data mahasiswa.                                       |
| SIA-R12 | Model menunjukkan collaboration yang menghubungkan proses Input Nilai Mata Kuliah dan Lihat KHS melalui realisasi use case masing-masing. |

### 2.1 Batasan dan Asumsi

1. Kode kebutuhan dimulai dari SIA-R07 agar SIA-R01 dan SIA-R02 dari Pertemuan 2 serta SIA-R03 sampai SIA-R06 dari Pertemuan 3 tetap memiliki identitas berbeda.
2. Pengguna telah terautentikasi dan memiliki hak akses sesuai dengan perannya.
3. Kalender akademik merupakan agenda resmi institusi, seperti awal semester, batas pengisian KRS, masa ujian, dan kegiatan akademik lainnya. Kalender akademik tidak disamakan dengan jadwal kuliah pada Pertemuan 2.
4. Nilai hanya dapat diinput oleh dosen pengampu mata kuliah yang bersangkutan.
5. Nilai yang telah diinput belum dianggap dipublikasikan sebelum dinyatakan resmi sesuai ketentuan tugas. KHS hanya menampilkan nilai yang sudah dipublikasikan.
6. Penghapusan data mahasiswa hanya dapat dilakukan apabila mahasiswa tersebut tidak memiliki data akademik aktif. Ketentuan ini bersifat fiktif untuk latihan.
7. Use case pengajuan KRS tetap ditampilkan sebagai bagian dari diagram kumulatif Pertemuan 3.
8. Pembayaran dan perancangan basis data berada di luar cakupan tugas ini.

## 3. Identifikasi Aktor

| Nama Aktor        | Deskripsi Peran                                                                                                  |
| ----------------- | ---------------------------------------------------------------------------------------------------------------- |
| Mahasiswa         | Melihat kalender akademik dan melihat Kartu Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan. |
| Admin Akademik    | Mengelola data mahasiswa, meliputi menambah, mengubah, dan menghapus data mahasiswa sesuai ketentuan.            |
| Dosen             | Melihat kalender akademik dan menginput nilai mata kuliah yang diampunya.                                        |
| Civitas Akademika | Aktor umum yang mewakili Mahasiswa dan Dosen dalam aktivitas melihat kalender akademik.                          |

### 3.1 Generalization Aktor

Relasi generalization aktor ditetapkan sebagai berikut:

- Mahasiswa → Civitas Akademika
- Dosen → Civitas Akademika

**Alasan:** Mahasiswa dan Dosen memiliki perilaku umum yang sama, yaitu melihat Kalender Akademik (SIA-UC07). Oleh karena itu, keduanya dimodelkan sebagai spesialisasi dari aktor Civitas Akademika.

## 4. Identifikasi Use Case SIA

| ID       | Nama Use Case             | Peran dalam Model                            |
| -------- | ------------------------- | -------------------------------------------- |
| SIA-UC01 | Melihat Jadwal Kuliah     | Fungsi utama Mahasiswa (Pertemuan 2).        |
| SIA-UC02 | Mengelola Jadwal Kuliah   | Fungsi utama Admin Akademik (Pertemuan 2).   |
| SIA-UC03 | Mengajukan KRS            | Fungsi utama Mahasiswa (Pertemuan 3).        |
| SIA-UC04 | Memvalidasi KRS           | Perilaku yang disertakan dalam SIA-UC03.     |
| SIA-UC05 | Mengunduh Bukti Pengajuan | Tambahan bersyarat (_extend_) pada SIA-UC03. |
| SIA-UC06 | Menyetujui / Menolak KRS  | Fungsi utama Dosen Wali (Pertemuan 3).       |
| SIA-UC07 | Melihat Kalender Akademik | Fungsi umum Civitas Akademika.               |
| SIA-UC08 | Input Nilai Mata Kuliah   | Fungsi utama Dosen.                          |
| SIA-UC09 | Lihat KHS                 | Fungsi utama Mahasiswa.                      |
| SIA-UC10 | Mengelola Data Mahasiswa  | Fungsi utama Admin Akademik.                 |
| SIA-UC11 | Tambah Data Mahasiswa     | Spesialisasi dari Mengelola Data Mahasiswa.  |
| SIA-UC12 | Ubah Data Mahasiswa       | Spesialisasi dari Mengelola Data Mahasiswa.  |
| SIA-UC13 | Hapus Data Mahasiswa      | Spesialisasi dari Mengelola Data Mahasiswa.  |

**Catatan penomoran:** ID use case SIA-UC01 sampai SIA-UC06 dipertahankan dari tugas sebelumnya. Use case baru diberi nomor lanjutan SIA-UC07 sampai SIA-UC13. ID kebutuhan dan ID use case merupakan dua jenis identitas yang berbeda.

## 5. Relasi Include dan Extend

### 5.1 Relasi Include

**SIA-UC03 «include» SIA-UC04**

- Use case utama: Mengajukan KRS.
- Use case yang disertakan: Memvalidasi KRS.
- Alasan: Pemeriksaan dan validasi merupakan bagian dari proses pengajuan KRS sehingga harus dijalankan sebagai bagian dari use case tersebut.

### 5.2 Relasi Extend

**SIA-UC05 «extend» SIA-UC03**

- Use case dasar: Mengajukan KRS.
- Use case tambahan: Mengunduh Bukti Pengajuan.
- Extension point: Bukti pengajuan tersedia.
- Kondisi: [Mahasiswa memilih unduh].
- Alasan: Pengajuan KRS tetap dapat berhasil tanpa mahasiswa mengunduh bukti pengajuan. Pengunduhan merupakan perilaku tambahan yang hanya dilakukan jika mahasiswa memilihnya.

## 6. Generalization Use Case

Generalization diterapkan pada pengelolaan data mahasiswa.

| Use Case Khusus                | Use Case Umum                     |
| ------------------------------ | --------------------------------- |
| SIA-UC11 Tambah Data Mahasiswa | SIA-UC10 Mengelola Data Mahasiswa |
| SIA-UC12 Ubah Data Mahasiswa   | SIA-UC10 Mengelola Data Mahasiswa |
| SIA-UC13 Hapus Data Mahasiswa  | SIA-UC10 Mengelola Data Mahasiswa |

**Alasan:** Ketiga aktivitas tersebut merupakan bentuk khusus dari proses Mengelola Data Mahasiswa. Oleh karena itu, ketiganya dimodelkan sebagai spesialisasi dari use case umum tersebut.

## 7. Collaboration dan Realization

Terdapat dua collaboration yang berkaitan dengan use case utama pada layanan hasil studi.

### 7.1 Collaboration Input Nilai Mata Kuliah

- Nama collaboration: Input Nilai Mata Kuliah.
- Use case yang direalisasikan: SIA-UC08 Input Nilai Mata Kuliah.
- Aktor yang terlibat: Dosen.
- Tujuan: Menunjukkan interaksi atau kerja sama objek dalam proses penginputan nilai mata kuliah yang diampu dosen.

### 7.2 Collaboration Lihat KHS

- Nama collaboration: Lihat KHS.
- Use case yang direalisasikan: SIA-UC09 Lihat KHS.
- Aktor yang terlibat: Mahasiswa.
- Tujuan: Menunjukkan interaksi atau kerja sama objek dalam proses menampilkan KHS berdasarkan nilai semester yang sudah dipublikasikan.

**Hubungan kedua collaboration:** Nilai yang diinput oleh Dosen menjadi data yang selanjutnya dapat dipublikasikan secara resmi dan digunakan dalam proses Lihat KHS oleh Mahasiswa. Dengan demikian, kedua collaboration menggambarkan bagian proses layanan hasil studi yang saling berkaitan.

## 8. Ringkasan Relasi Model

| Jenis Relasi            | Relasi                                           |
| ----------------------- | ------------------------------------------------ |
| Generalization Aktor    | Mahasiswa → Civitas Akademika                    |
| Generalization Aktor    | Dosen → Civitas Akademika                        |
| Include                 | SIA-UC03 → SIA-UC04                              |
| Extend                  | SIA-UC05 → SIA-UC03                              |
| Generalization Use Case | SIA-UC11 → SIA-UC10                              |
| Generalization Use Case | SIA-UC12 → SIA-UC10                              |
| Generalization Use Case | SIA-UC13 → SIA-UC10                              |
| Realization             | Collaboration Input Nilai Mata Kuliah → SIA-UC08 |
| Realization             | Collaboration Lihat KHS → SIA-UC09               |

## 9. Catatan Pemodelan

1. Diagram use case dibuat secara kumulatif dengan tetap menampilkan use case dari Pertemuan 2 dan Pertemuan 3.
2. Mahasiswa dan Dosen merupakan spesialisasi dari Civitas Akademika karena keduanya memiliki akses ke fungsi melihat kalender akademik.
3. Dosen yang menginput nilai harus merupakan dosen pengampu mata kuliah tersebut.
4. KHS hanya menampilkan nilai yang sudah dipublikasikan secara resmi.
5. Tambah, ubah, dan hapus data mahasiswa merupakan spesialisasi dari Mengelola Data Mahasiswa.
6. Penghapusan data mahasiswa harus memperhatikan batasan bahwa mahasiswa tidak memiliki data akademik aktif.
7. Collaboration Input Nilai Mata Kuliah dan Collaboration Lihat KHS masing-masing merealisasikan use case yang bersesuaian. Keterkaitan keduanya dijelaskan melalui alur nilai yang diinput, dipublikasikan, kemudian ditampilkan pada KHS.

## 10. Checklist Kelengkapan Tugas

- [✅] Kebutuhan SIA-R07 sampai SIA-R12 sudah direpresentasikan dalam model.
- [✅] Aktor Civitas Akademika sudah dibuat.
- [✅] Mahasiswa dan Dosen sudah menjadi spesialisasi Civitas Akademika.
- [✅] Use case Melihat Kalender Akademik sudah terhubung dengan aktor Civitas Akademika.
- [✅] Use case Input Nilai Mata Kuliah sudah terhubung dengan aktor Dosen.
- [✅] Use case Lihat KHS sudah terhubung dengan aktor Mahasiswa.
- [✅] Use case Mengelola Data Mahasiswa sudah dibuat.
- [✅] Tambah, Ubah, dan Hapus Data Mahasiswa sudah dimodelkan sebagai spesialisasi.
- [✅] Relasi include dan extend dari Pertemuan 3 tetap dipertahankan.
- [✅] Collaboration Input Nilai Mata Kuliah sudah merealisasikan SIA-UC08.
- [✅] Collaboration Lihat KHS sudah merealisasikan SIA-UC09.
- [✅] Diagram kumulatif tetap memuat use case dari Pertemuan 2 dan Pertemuan 3.
