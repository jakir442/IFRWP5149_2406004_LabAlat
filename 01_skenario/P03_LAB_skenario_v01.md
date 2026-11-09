# STUDI KASUS

## Sistem Informasi Peminjaman Peralatan Laboratorium

### 1. Deskripsi Skenario

Mahasiswa mengajukan peminjaman peralatan laboratorium dengan memilih peralatan, menentukan jumlah, serta menentukan rentang waktu peminjaman.

Setelah mahasiswa mengajukan peminjaman, sistem akan melakukan pemeriksaan ketersediaan peralatan. Apabila peralatan tersedia dan seluruh data pengajuan telah lengkap, sistem akan menyimpan pengajuan dengan status **Menunggu Keputusan**.

Setelah pengajuan berhasil disimpan, sistem menampilkan halaman konfirmasi. Pada halaman tersebut, mahasiswa dapat memilih untuk mencetak bukti pengajuan peminjaman.

Selain itu, Petugas Laboratorium memiliki tanggung jawab untuk:

- Mengelola data peralatan.
- Menyetujui pengajuan peminjaman.
- Menolak pengajuan peminjaman.

Sementara itu, Kepala Laboratorium memiliki hak untuk melihat laporan peminjaman peralatan.

---

### 2. Kebutuhan Sistem

Berikut daftar kebutuhan sistem yang harus dipenuhi dalam studi kasus ini.

| ID Kebutuhan | Deskripsi Kebutuhan                                                                               |
| ------------ | ------------------------------------------------------------------------------------------------- |
| LAB-R01      | Mahasiswa dapat melihat ketersediaan peralatan.                                                   |
| LAB-R02      | Petugas dapat mengelola data peralatan.                                                           |
| LAB-R03      | Mahasiswa dapat mengajukan peminjaman. Sistem memeriksa ketersediaan sebelum menyimpan pengajuan. |
| LAB-R04      | Mahasiswa dapat mencetak bukti pada halaman konfirmasi pengajuan apabila memilihnya.              |
| LAB-R05      | Petugas dapat menetapkan persetujuan atau penolakan pengajuan peminjaman.                         |
| LAB-R06      | Kepala Laboratorium dapat melihat laporan peminjaman.                                             |

---

### 3. Batas Sistem dan Asumsi

Berikut batasan sistem dan aturan yang digunakan dalam pemodelan:

1. **Batas Sistem**

   Sistem hanya bertugas mencatat dan menyediakan informasi. Perpindahan fisik peralatan tidak dilakukan di dalam perangkat lunak.

2. **Autentikasi dan Hak Akses**

   Seluruh pengguna telah terautentikasi dan memiliki hak akses sesuai dengan perannya masing-masing.

3. **Status Pengajuan**

   Setiap pengajuan yang berhasil diterima oleh sistem akan memiliki status **Menunggu Keputusan**, bukan otomatis berstatus Disetujui.

4. **Ketentuan Ketersediaan Peralatan**

   Apabila peralatan yang dipilih tidak tersedia, pengajuan tidak akan disimpan sebagai pengajuan yang berhasil.

5. **Ketentuan Pencetakan Bukti**

   Pencetakan bukti pengajuan bukan merupakan syarat keberhasilan proses pengajuan peminjaman. Mahasiswa tetap dapat menyelesaikan pengajuan meskipun tidak mencetak bukti.

6. **Persetujuan Peminjaman**

   Persetujuan yang diberikan oleh petugas belum dimodelkan sebagai reservasi teknis stok peralatan.

7. **Fitur di Luar Lingkup Model**

   Beberapa proses berikut belum dianalisis dalam potongan model ini:
   - Pengambilan peralatan.
   - Pengembalian peralatan.
   - Pemeriksaan kondisi peralatan.
   - Penerapan denda.

---

### 4. Identifikasi Aktor

Terdapat tiga aktor utama yang terlibat dalam Sistem Informasi Peminjaman Peralatan Laboratorium.

| Aktor                    | Tujuan terhadap Sistem                                                               |
| ------------------------ | ------------------------------------------------------------------------------------ |
| **Mahasiswa**            | Melihat ketersediaan peralatan, mengajukan peminjaman, dan mencetak bukti pengajuan. |
| **Petugas Laboratorium** | Mengelola data peralatan serta memproses keputusan peminjaman.                       |
| **Kepala Laboratorium**  | Melihat laporan peminjaman peralatan.                                                |

---

### 5. Katalog Use Case

Berikut daftar use case yang terdapat dalam Sistem Informasi Peminjaman Peralatan Laboratorium.

| ID Use Case | Nama Use Case                | Peran dalam Model                                    |
| ----------- | ---------------------------- | ---------------------------------------------------- |
| LAB-UC01    | Lihat Ketersediaan Peralatan | Fungsi utama Mahasiswa.                              |
| LAB-UC02    | Kelola Data Peralatan        | Fungsi utama Petugas Laboratorium.                   |
| LAB-UC03    | Ajukan Peminjaman            | Fungsi utama Mahasiswa.                              |
| LAB-UC04    | Periksa Ketersediaan         | Perilaku yang disertakan (_include_) dalam LAB-UC03. |
| LAB-UC05    | Cetak Bukti Pengajuan        | Fungsi tambahan bersyarat (_extend_) pada LAB-UC03.  |
| LAB-UC06    | Proses Keputusan Peminjaman  | Fungsi utama Petugas Laboratorium.                   |
| LAB-UC07    | Lihat Laporan Peminjaman     | Fungsi utama Kepala Laboratorium.                    |

---

### 6. Identifikasi Relasi Use Case

Relasi antar-use case digunakan untuk menggambarkan hubungan antara proses utama dan proses pendukung atau tambahan dalam sistem.

#### 6.1. Relasi Include

Relasi `<<include>>` menunjukkan bahwa suatu use case selalu menyertakan perilaku dari use case lainnya sebagai bagian dari proses pelaksanaannya.

| Use Case Utama              | Use Case yang Disertakan       | Keterangan                                                                                                               |
| --------------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| LAB-UC03: Ajukan Peminjaman | LAB-UC04: Periksa Ketersediaan | Sistem selalu memeriksa ketersediaan peralatan sebagai bagian dari proses pengajuan sebelum pengajuan berhasil disimpan. |

**Alasan penggunaan relasi include:**

Pemeriksaan ketersediaan merupakan bagian wajib dari proses pengajuan peminjaman. Sistem harus memastikan bahwa peralatan yang dipilih tersedia sebelum menyimpan pengajuan sebagai pengajuan yang berhasil.

#### 6.2. Relasi Extend

Relasi `<<extend>>` menunjukkan perilaku tambahan yang hanya dijalankan apabila kondisi tertentu terpenuhi.

| Use Case Utama              | Use Case yang Memperluas        | Extension Point           | Kondisi                   |
| --------------------------- | ------------------------------- | ------------------------- | ------------------------- |
| LAB-UC03: Ajukan Peminjaman | LAB-UC05: Cetak Bukti Pengajuan | Bukti pengajuan tersedia. | [Mahasiswa memilih cetak] |

**Alasan penggunaan relasi extend:**

Pencetakan bukti pengajuan merupakan fungsi tambahan yang bersifat opsional. Mahasiswa dapat memilih untuk mencetak bukti setelah pengajuan berhasil disimpan.

Pengajuan peminjaman tetap dinyatakan berhasil meskipun mahasiswa tidak memilih untuk mencetak bukti pengajuan.

---

### 7. Ringkasan Relasi Use Case

Berikut ringkasan hubungan antar-use case dalam sistem:

| Relasi        | Use Case Sumber                 | Use Case Tujuan                | Keterangan                                                                                                     |
| ------------- | ------------------------------- | ------------------------------ | -------------------------------------------------------------------------------------------------------------- |
| `<<include>>` | LAB-UC03: Ajukan Peminjaman     | LAB-UC04: Periksa Ketersediaan | Pemeriksaan ketersediaan wajib dilakukan sebagai bagian dari proses pengajuan.                                 |
| `<<extend>>`  | LAB-UC05: Cetak Bukti Pengajuan | LAB-UC03: Ajukan Peminjaman    | Pencetakan bukti merupakan proses tambahan yang dilakukan secara opsional setelah pengajuan berhasil disimpan. |

**Catatan arah panah UML:**

- `<<include>>`: panah mengarah dari use case utama menuju use case yang disertakan.
- `<<extend>>`: panah mengarah dari use case tambahan menuju use case utama yang diperluas.

---

### 8. Pemetaan Kebutuhan terhadap Use Case

Untuk memastikan seluruh kebutuhan sistem sudah memiliki representasi dalam model, berikut pemetaan kebutuhan terhadap use case.

| ID Kebutuhan | Nama Kebutuhan                                     | ID Use Case | Nama Use Case                |
| ------------ | -------------------------------------------------- | ----------- | ---------------------------- |
| LAB-R01      | Melihat ketersediaan peralatan                     | LAB-UC01    | Lihat Ketersediaan Peralatan |
| LAB-R02      | Mengelola data peralatan                           | LAB-UC02    | Kelola Data Peralatan        |
| LAB-R03      | Mengajukan peminjaman                              | LAB-UC03    | Ajukan Peminjaman            |
| LAB-R03      | Memeriksa ketersediaan sebelum menyimpan pengajuan | LAB-UC04    | Periksa Ketersediaan         |
| LAB-R04      | Mencetak bukti pengajuan                           | LAB-UC05    | Cetak Bukti Pengajuan        |
| LAB-R05      | Memproses persetujuan atau penolakan               | LAB-UC06    | Proses Keputusan Peminjaman  |
| LAB-R06      | Melihat laporan peminjaman                         | LAB-UC07    | Lihat Laporan Peminjaman     |

---

### 9. Kriteria Akhir Pengerjaan

Sebelum diagram dikumpulkan, pastikan seluruh ketentuan berikut sudah terpenuhi.

- [✅] Aktor Mahasiswa sudah terhubung dengan use case Lihat Ketersediaan Peralatan.
- [✅] Aktor Mahasiswa sudah terhubung dengan use case Ajukan Peminjaman.
- [✅] Aktor Petugas Laboratorium sudah terhubung dengan use case Kelola Data Peralatan.
- [✅] Aktor Petugas Laboratorium sudah terhubung dengan use case Proses Keputusan Peminjaman.
- [✅] Aktor Kepala Laboratorium sudah terhubung dengan use case Lihat Laporan Peminjaman.
- [✅] Use case Ajukan Peminjaman sudah terhubung dengan Periksa Ketersediaan menggunakan relasi `<<include>>`.
- [✅] Use case Cetak Bukti Pengajuan sudah terhubung dengan Ajukan Peminjaman menggunakan relasi `<<extend>>`.
- [✅] Extension point sudah dicantumkan dengan nama **Bukti pengajuan tersedia**.
- [✅] Kondisi extend sudah dicantumkan, yaitu **[Mahasiswa memilih cetak]**.
- [✅] Seluruh kebutuhan LAB-R01 sampai LAB-R06 sudah direpresentasikan dalam diagram.
- [✅] Diagram konsisten dengan deskripsi skenario, kebutuhan, batas sistem, dan asumsi.

---

### 10. Kesimpulan

Sistem Informasi Peminjaman Peralatan Laboratorium pada studi kasus ini memiliki tiga aktor utama, yaitu Mahasiswa, Petugas Laboratorium, dan Kepala Laboratorium.

Sistem menyediakan fungsi untuk melihat ketersediaan peralatan, mengelola data peralatan, mengajukan peminjaman, memeriksa ketersediaan, mencetak bukti pengajuan, memproses keputusan peminjaman, serta melihat laporan peminjaman.

Dalam pemodelan use case, proses pemeriksaan ketersediaan menggunakan relasi `<<include>>` karena wajib dilakukan sebagai bagian dari pengajuan peminjaman. Sementara itu, proses pencetakan bukti pengajuan menggunakan relasi `<<extend>>` karena bersifat opsional dan tidak menentukan keberhasilan pengajuan peminjaman.
