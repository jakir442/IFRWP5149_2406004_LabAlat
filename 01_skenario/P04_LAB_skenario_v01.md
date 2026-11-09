# STUDI KASUS PERTEMUAN 4

## Pengembangan Sistem Informasi Peminjaman Peralatan Laboratorium

### 1. Deskripsi Skenario

Skenario berikut merupakan bahan latihan yang ditetapkan untuk jobsheet, bukan hasil pengumpulan kebutuhan dari laboratorium nyata. Skenario ini merupakan pengembangan dari potongan model Pertemuan 3.

Selain mahasiswa, dosen juga dapat meminjam peralatan laboratorium untuk kegiatan praktikum dan penelitian. Mahasiswa dan dosen memiliki hak yang sama untuk melihat ketersediaan peralatan serta mengajukan peminjaman.

Petugas laboratorium bertanggung jawab mengelola data peralatan, yang meliputi:

- Menambahkan data peralatan baru.
- Mengubah data peralatan.
- Menghapus data peralatan yang tidak lagi digunakan.

Setelah peminjaman disetujui dan peralatan diambil, petugas laboratorium dapat mencatat pengembalian peralatan. Pada proses pencatatan pengembalian, petugas juga memeriksa dan mencatat kondisi peralatan.

Terdapat dua use case utama pada pengembangan model ini, yaitu:

1. **Ajukan Peminjaman**, yang realisasinya ditunjukkan melalui collaboration yang bersesuaian.
2. **Catat Pengembalian Peralatan**, yang realisasinya ditunjukkan melalui collaboration yang bersesuaian.

Seluruh fungsi dari Pertemuan 3 tetap berlaku dan harus tetap ditampilkan, meliputi:

- Pemeriksaan ketersediaan peralatan dalam proses pengajuan peminjaman.
- Pencetakan bukti pengajuan oleh mahasiswa.
- Proses keputusan peminjaman oleh petugas laboratorium.
- Pembuatan laporan peminjaman untuk kepala laboratorium.

**Catatan:** Diagram Pertemuan 4 merupakan pengembangan dari diagram Pertemuan 3 dengan menambahkan kebutuhan baru, bukan diagram baru yang menggantikan diagram sebelumnya.

---

### 2. Kebutuhan Sistem

Berikut daftar kebutuhan sistem yang harus dipenuhi dalam pengembangan model Pertemuan 4.

| ID Kebutuhan         | Deskripsi Kebutuhan                                                                                                                   |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| LAB-R01 s.d. LAB-R06 | Kebutuhan Pertemuan 3 tetap berlaku dan tidak mengalami perubahan arti. Lihat Jobsheet Pertemuan 3.                                   |
| LAB-R07              | Mahasiswa dan Dosen, sebagai Peminjam, dapat melihat ketersediaan peralatan dan mengajukan peminjaman.                                |
| LAB-R08              | Petugas laboratorium dapat mengelola data peralatan dalam tiga bentuk khusus, yaitu menambah, mengubah, dan menghapus data peralatan. |
| LAB-R09              | Petugas laboratorium dapat mencatat pengembalian peralatan untuk peminjaman yang berstatus **Dipinjam**.                              |
| LAB-R10              | Sistem memeriksa dan mencatat kondisi peralatan sebagai bagian dari proses pencatatan pengembalian.                                   |
| LAB-R11              | Model menunjukkan collaboration yang merealisasikan use case **Ajukan Peminjaman** dan **Catat Pengembalian Peralatan**.              |

---

### 3. Batas Sistem dan Aturan

Berikut batasan sistem dan aturan yang digunakan dalam pemodelan:

1. **Batas Sistem**

   Sistem hanya bertugas mencatat dan menyediakan informasi. Perpindahan fisik peralatan tidak dilakukan di dalam perangkat lunak. Ketentuan ini tetap berlaku dari Pertemuan 3.

2. **Autentikasi dan Hak Akses**

   Seluruh pengguna telah terautentikasi dan memiliki hak akses sesuai dengan perannya masing-masing. Ketentuan ini tetap berlaku dari Pertemuan 3.

3. **Ketentuan Pengembalian Peralatan**

   Pengembalian hanya dapat dicatat untuk peminjaman yang berstatus **Dipinjam**.

   Peminjaman dengan status berikut tidak dapat dicatat pengembaliannya:
   - Menunggu Keputusan.
   - Ditolak.

4. **Kondisi Peralatan**

   Kondisi peralatan yang dicatat pada saat pengembalian hanya memiliki tiga pilihan:
   - Baik.
   - Rusak Ringan.
   - Rusak Berat.

5. **Ketentuan Penghapusan Data Peralatan**

   Data peralatan hanya dapat dihapus apabila peralatan tersebut:
   - Tidak sedang dipinjam.
   - Tidak memiliki pengajuan peminjaman aktif.

6. **Keterlambatan dan Denda**

   Keterlambatan pengembalian dan ketentuan denda belum dimodelkan pada pertemuan ini.

   Hal tersebut harus dicatat sebagai **pertanyaan terbuka pada berkas kebutuhan**, bukan dibuatkan aturan denda sendiri.

7. **Kriteria Penerimaan Model**

   Model dinyatakan memenuhi kebutuhan apabila:
   - Seluruh kebutuhan LAB-R01 sampai LAB-R11 memiliki representasi pada diagram kumulatif.
   - Arah relasi _generalization_ dan _realization_ sudah benar.
   - Diagram konsisten dengan deskripsi kebutuhan dan skenario sistem.

---

### 4. Identifikasi Aktor

Aktor yang terlibat dalam Sistem Informasi Peminjaman Peralatan Laboratorium adalah sebagai berikut.

| Aktor                    | Kedudukan                                           | Tujuan terhadap Sistem                                                                                                                                  |
| ------------------------ | --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Peminjam**             | Aktor umum (_general_), baru pada Pertemuan 4.      | Merupakan peran umum bagi pengguna yang meminjam peralatan. Mewariskan fungsinya kepada aktor Mahasiswa dan Dosen.                                      |
| **Mahasiswa**            | Aktor khusus dari Peminjam, tetap dari Pertemuan 3. | Melihat ketersediaan dan mengajukan peminjaman (fungsi yang diwarisi dari Peminjam), serta mencetak bukti pengajuan sebagai asosiasi khususnya sendiri. |
| **Dosen**                | Aktor khusus dari Peminjam, baru pada Pertemuan 4.  | Melihat ketersediaan dan mengajukan peminjaman (fungsi yang diwarisi dari Peminjam).                                                                    |
| **Petugas Laboratorium** | Tetap dari Pertemuan 3.                             | Mengelola data peralatan, memproses keputusan peminjaman, dan mencatat pengembalian peralatan.                                                          |
| **Kepala Laboratorium**  | Tetap dari Pertemuan 3.                             | Melihat laporan peminjaman.                                                                                                                             |

**Catatan relasi aktor:**

Aktor Mahasiswa dan Dosen merupakan turunan dari aktor Peminjam. Dengan demikian, keduanya mewarisi fungsi yang dimiliki aktor Peminjam melalui relasi _generalization_.

---

### 5. Katalog Use Case

Berikut daftar use case yang terdapat dalam sistem, termasuk fungsi yang dipertahankan dari Pertemuan 3 dan fungsi tambahan pada Pertemuan 4.

| ID Use Case | Nama Use Case                | Peran dalam Model                                                                                                   | Sumber Kebutuhan |
| ----------- | ---------------------------- | ------------------------------------------------------------------------------------------------------------------- | ---------------- |
| LAB-UC01    | Lihat Ketersediaan Peralatan | Tetap dari Pertemuan 3. Menjadi fungsi aktor umum Peminjam.                                                         | LAB-R01, LAB-R07 |
| LAB-UC02    | Kelola Data Peralatan        | Tetap dari Pertemuan 3. Menjadi use case umum (_parent_) bagi LAB-UC08, LAB-UC09, dan LAB-UC10.                     | LAB-R02, LAB-R08 |
| LAB-UC03    | Ajukan Peminjaman            | Tetap dari Pertemuan 3. Menjadi fungsi aktor umum Peminjam, menyertakan LAB-UC04, dan direalisasikan oleh LAB-CO01. | LAB-R03, LAB-R07 |
| LAB-UC04    | Periksa Ketersediaan         | Tetap dari Pertemuan 3. Menjadi perilaku yang disertakan oleh LAB-UC03 melalui relasi _include_.                    | LAB-R03          |
| LAB-UC05    | Cetak Bukti Pengajuan        | Tetap dari Pertemuan 3. Menjadi tambahan bersyarat pada LAB-UC03 melalui relasi _extend_.                           | LAB-R04          |
| LAB-UC06    | Proses Keputusan Peminjaman  | Tetap dari Pertemuan 3. Menjadi fungsi utama Petugas Laboratorium.                                                  | LAB-R05          |
| LAB-UC07    | Lihat Laporan Peminjaman     | Tetap dari Pertemuan 3. Menjadi fungsi utama Kepala Laboratorium.                                                   | LAB-R06          |
| LAB-UC08    | Tambah Data Peralatan        | Baru pada Pertemuan 4. Menjadi use case khusus (_child_) dari LAB-UC02.                                             | LAB-R08          |
| LAB-UC09    | Ubah Data Peralatan          | Baru pada Pertemuan 4. Menjadi use case khusus (_child_) dari LAB-UC02.                                             | LAB-R08          |
| LAB-UC10    | Hapus Data Peralatan         | Baru pada Pertemuan 4. Menjadi use case khusus (_child_) dari LAB-UC02.                                             | LAB-R08          |
| LAB-UC11    | Catat Pengembalian Peralatan | Baru pada Pertemuan 4. Menjadi fungsi utama Petugas Laboratorium dan direalisasikan oleh LAB-CO02.                  | LAB-R09          |
| LAB-UC12    | Periksa Kondisi Peralatan    | Baru pada Pertemuan 4. Menjadi perilaku yang disertakan oleh LAB-UC11 melalui relasi _include_.                     | LAB-R10          |

---

### 6. Identifikasi Relasi Use Case

Relasi antar-use case digunakan untuk menunjukkan hubungan antara fungsi umum, fungsi khusus, serta perilaku tambahan dalam sistem.

#### 6.1. Relasi Include

Relasi `<<include>>` menunjukkan bahwa suatu use case selalu menyertakan perilaku dari use case lainnya dalam proses pelaksanaannya.

| Use Case Utama                         | Use Case yang Disertakan            | Keterangan                                                                            |
| -------------------------------------- | ----------------------------------- | ------------------------------------------------------------------------------------- |
| LAB-UC03: Ajukan Peminjaman            | LAB-UC04: Periksa Ketersediaan      | Sistem selalu memeriksa ketersediaan peralatan ketika peminjam mengajukan peminjaman. |
| LAB-UC11: Catat Pengembalian Peralatan | LAB-UC12: Periksa Kondisi Peralatan | Pemeriksaan kondisi peralatan menjadi bagian dari proses pencatatan pengembalian.     |

**Alasan penggunaan relasi include:**

- Pemeriksaan ketersediaan merupakan bagian wajib dari proses pengajuan peminjaman.
- Pemeriksaan kondisi peralatan merupakan bagian dari proses pencatatan pengembalian.

#### 6.2. Relasi Extend

Relasi `<<extend>>` menunjukkan perilaku tambahan yang hanya dijalankan apabila kondisi tertentu terpenuhi.

| Use Case Utama              | Use Case yang Memperluas        | Keterangan                                                                                                                         |
| --------------------------- | ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| LAB-UC03: Ajukan Peminjaman | LAB-UC05: Cetak Bukti Pengajuan | Pencetakan bukti pengajuan menjadi fungsi tambahan yang dilakukan oleh mahasiswa setelah mengajukan peminjaman apabila memilihnya. |

**Ketentuan Extend:**

- **Extension Point:** Bukti pengajuan tersedia.
- **Kondisi:** [Mahasiswa memilih cetak].

**Alasan penggunaan relasi extend:**

Pencetakan bukti pengajuan merupakan fungsi tambahan yang bersifat opsional. Pengajuan peminjaman tetap dinyatakan berhasil meskipun mahasiswa tidak memilih untuk mencetak bukti pengajuan.

---

### 7. Identifikasi Collaboration

Collaboration digunakan untuk menunjukkan realisasi dari use case tertentu melalui interaksi antarobjek yang terlibat di dalam sistem.

Berdasarkan kebutuhan LAB-R11, terdapat dua collaboration yang harus dibuat.

| ID Collaboration | Nama Collaboration           | Use Case yang Direalisasikan           |
| ---------------- | ---------------------------- | -------------------------------------- |
| LAB-CO01         | Ajukan Peminjaman            | LAB-UC03: Ajukan Peminjaman            |
| LAB-CO02         | Catat Pengembalian Peralatan | LAB-UC11: Catat Pengembalian Peralatan |

**Penjelasan:**

1. **LAB-CO01 – Ajukan Peminjaman**

   Collaboration ini merepresentasikan interaksi antarobjek dalam proses pengajuan peminjaman peralatan oleh Peminjam, termasuk pemeriksaan ketersediaan peralatan.

2. **LAB-CO02 – Catat Pengembalian Peralatan**

   Collaboration ini merepresentasikan interaksi antarobjek dalam proses pencatatan pengembalian peralatan oleh Petugas Laboratorium, termasuk pemeriksaan dan pencatatan kondisi peralatan.

---

### 8. Pertanyaan Terbuka

Terdapat beberapa hal yang belum ditentukan dalam kebutuhan sistem dan perlu dikonfirmasi lebih lanjut.

| No. | Pertanyaan Terbuka                                                                                    | Status           |
| --- | ----------------------------------------------------------------------------------------------------- | ---------------- |
| 1   | Bagaimana aturan penanganan keterlambatan pengembalian peralatan?                                     | Belum ditentukan |
| 2   | Apakah keterlambatan pengembalian akan dikenakan denda? Jika iya, bagaimana mekanisme perhitungannya? | Belum ditentukan |

Kedua hal tersebut belum dimasukkan ke dalam model karena belum terdapat aturan yang ditetapkan.

---

### 9. Kriteria Akhir Pengerjaan

Sebelum diagram dikumpulkan, pastikan seluruh ketentuan berikut sudah terpenuhi.

- [✅] Seluruh kebutuhan LAB-R01 sampai LAB-R11 sudah direpresentasikan dalam diagram kumulatif.
- [✅] Aktor Peminjam sudah dibuat sebagai aktor umum.
- [✅] Mahasiswa dan Dosen sudah terhubung dengan Peminjam menggunakan relasi _generalization_.
- [✅] Seluruh fungsi dan use case dari Pertemuan 3 tetap dipertahankan.
- [✅] Use case Tambah Data Peralatan sudah ditambahkan.
- [✅] Use case Ubah Data Peralatan sudah ditambahkan.
- [✅] Use case Hapus Data Peralatan sudah ditambahkan.
- [✅] Ketiga use case pengelolaan peralatan sudah terhubung dengan Kelola Data Peralatan menggunakan relasi \*generalization
