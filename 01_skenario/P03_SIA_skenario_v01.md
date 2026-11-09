# STUDI KASUS

## Sistem Informasi Akademik (SIA)

### 1. Deskripsi Skenario

Mahasiswa mengajukan Kartu Rencana Studi (KRS) dengan memilih mata kuliah yang akan diambil pada semester berjalan.

Setiap pengajuan KRS akan menjalankan proses validasi yang dilakukan oleh sistem. Validasi tersebut mencakup:

- Pemeriksaan kelengkapan prasyarat mata kuliah.
- Pemeriksaan benturan jadwal perkuliahan.

Jika proses validasi berhasil, sistem akan menyimpan pengajuan KRS dengan status **Menunggu Persetujuan Dosen Wali**.

Setelah pengajuan berhasil disimpan, mahasiswa dapat memilih untuk mengunduh bukti pengajuan melalui proses konfirmasi penyimpanan.

Selanjutnya, dosen wali bertugas memproses pengajuan KRS dengan memberikan keputusan berupa persetujuan atau penolakan, disertai catatan keputusan.

---

### 2. Kebutuhan Sistem

Ketentuan dalam studi kasus ini bersifat fiktif dan hanya digunakan untuk keperluan praktikum.

Batas jumlah SKS, aturan pembayaran, serta kewenangan institusi nyata tidak boleh ditambahkan tanpa sumber yang jelas.

Berikut daftar kebutuhan sistem yang harus dipenuhi:

| ID Kebutuhan | Deskripsi Kebutuhan                                                                |
| ------------ | ---------------------------------------------------------------------------------- |
| SIA-R01      | Mahasiswa dapat melihat jadwal kuliah.                                             |
| SIA-R02      | Admin akademik dapat mengelola jadwal kuliah.                                      |
| SIA-R03      | Mahasiswa dapat mengajukan KRS.                                                    |
| SIA-R04      | Sistem memvalidasi KRS sebagai bagian dari proses pengajuan.                       |
| SIA-R05      | Mahasiswa dapat mengunduh bukti apabila memilihnya pada saat konfirmasi pengajuan. |
| SIA-R06      | Dosen wali dapat memproses persetujuan atau penolakan KRS.                         |

---

### 3. Batas Sistem dan Asumsi

Berikut batasan sistem dan asumsi yang digunakan dalam pemodelan:

1. **Autentikasi Pengguna**

   Seluruh pengguna sistem telah terautentikasi sebelum menggunakan fitur yang tersedia.

2. **Ketersediaan Data**

   Data mata kuliah, prasyarat mata kuliah, dan jadwal kuliah telah tersedia di dalam sistem.

3. **Ketentuan Validasi KRS**

   Apabila proses validasi gagal, pengajuan KRS belum berhasil disimpan oleh sistem.

4. **Ketentuan Unduh Bukti Pengajuan**

   Pengunduhan bukti pengajuan bukan merupakan syarat keberhasilan pengajuan KRS. Mahasiswa tetap dapat menyelesaikan pengajuan meskipun tidak mengunduh bukti.

5. **Status Pengajuan KRS**

   KRS yang berhasil disimpan belum berarti telah disetujui. Pengajuan harus menunggu keputusan dari dosen wali.

6. **Fitur di Luar Lingkup Tugas**

   Beberapa hal berikut tidak termasuk dalam cakupan pemodelan:
   - Pembayaran.
   - Pengisian nilai.
   - Implementasi basis data.

---

### 4. Identifikasi Aktor

Terdapat tiga aktor utama yang terlibat dalam Sistem Informasi Akademik.

| Nama Aktor         | Deskripsi Peran                                                                          |
| ------------------ | ---------------------------------------------------------------------------------------- |
| **Mahasiswa**      | Melihat jadwal kuliah, mengajukan KRS, dan mengunduh bukti pengajuan apabila diperlukan. |
| **Admin Akademik** | Mengelola jadwal kuliah.                                                                 |
| **Dosen Wali**     | Memproses pengajuan KRS dengan memberikan persetujuan atau penolakan.                    |

---

### 5. Identifikasi Aktor dan Use Case Sistem

Berikut daftar use case berdasarkan kebutuhan sistem yang telah ditentukan.

| ID Use Case | Nama Use Case             | Peran dalam Model                                    |
| ----------- | ------------------------- | ---------------------------------------------------- |
| SIA-UC01    | Melihat Jadwal Kuliah     | Fungsi utama Mahasiswa.                              |
| SIA-UC02    | Mengelola Jadwal Kuliah   | Fungsi utama Admin Akademik.                         |
| SIA-UC03    | Mengajukan KRS            | Fungsi utama Mahasiswa.                              |
| SIA-UC04    | Memvalidasi KRS           | Perilaku yang disertakan (_include_) dalam SIA-UC03. |
| SIA-UC05    | Mengunduh Bukti Pengajuan | Fungsi tambahan bersyarat (_extend_) pada SIA-UC03.  |
| SIA-UC06    | Menyetujui / Menolak KRS  | Fungsi utama Dosen Wali.                             |

---

### 6. Identifikasi Relasi Use Case

Relasi antar-use case digunakan untuk menggambarkan hubungan antara proses utama dengan proses pendukung atau proses tambahan di dalam sistem.

#### 6.1. Relasi Include

Relasi `<<include>>` menunjukkan bahwa suatu use case selalu menyertakan perilaku dari use case lainnya sebagai bagian dari proses pelaksanaannya.

| Use Case Utama           | Use Case yang Disertakan  | Keterangan                                                                                                                                          |
| ------------------------ | ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| SIA-UC03: Mengajukan KRS | SIA-UC04: Memvalidasi KRS | Sistem selalu melakukan validasi KRS sebagai bagian dari proses pengajuan. Validasi mencakup pemeriksaan prasyarat mata kuliah dan benturan jadwal. |

**Alasan penggunaan relasi include:**

Proses validasi merupakan bagian wajib dari pengajuan KRS. Oleh karena itu, setiap pengajuan harus menjalankan proses validasi terlebih dahulu sebelum KRS berhasil disimpan.

#### 6.2. Relasi Extend

Relasi `<<extend>>` menunjukkan perilaku tambahan yang hanya dijalankan apabila kondisi tertentu terpenuhi.

| Use Case Utama           | Use Case yang Memperluas            | Extension Point           | Kondisi                   |
| ------------------------ | ----------------------------------- | ------------------------- | ------------------------- |
| SIA-UC03: Mengajukan KRS | SIA-UC05: Mengunduh Bukti Pengajuan | Bukti pengajuan tersedia. | [Mahasiswa memilih unduh] |

**Alasan penggunaan relasi extend:**

Pengunduhan bukti pengajuan merupakan fungsi tambahan yang bersifat opsional. Mahasiswa dapat memilih untuk mengunduh bukti setelah pengajuan berhasil disimpan.

Pengajuan KRS tetap dinyatakan berhasil meskipun mahasiswa tidak memilih untuk mengunduh bukti pengajuan.

---

### 7. Ringkasan Relasi Use Case

Berikut ringkasan hubungan antar-use case dalam sistem:

| Relasi        | Use Case Sumber                     | Use Case Tujuan           | Keterangan                                                                       |
| ------------- | ----------------------------------- | ------------------------- | -------------------------------------------------------------------------------- |
| `<<include>>` | SIA-UC03: Mengajukan KRS            | SIA-UC04: Memvalidasi KRS | Validasi wajib dilakukan sebagai bagian dari pengajuan KRS.                      |
| `<<extend>>`  | SIA-UC05: Mengunduh Bukti Pengajuan | SIA-UC03: Mengajukan KRS  | Pengunduhan bukti dilakukan secara opsional setelah pengajuan berhasil disimpan. |

**Catatan arah panah UML:**

- `<<include>>`: panah mengarah dari use case utama menuju use case yang disertakan.
- `<<extend>>`: panah mengarah dari use case tambahan menuju use case utama yang diperluas.

---

### 8. Ringkasan Kebutuhan dan Use Case

Untuk memastikan seluruh kebutuhan sudah memiliki representasi dalam model, berikut pemetaan kebutuhan terhadap use case.

| ID Kebutuhan | Nama Kebutuhan              | ID Use Case | Nama Use Case             |
| ------------ | --------------------------- | ----------- | ------------------------- |
| SIA-R01      | Melihat jadwal kuliah       | SIA-UC01    | Melihat Jadwal Kuliah     |
| SIA-R02      | Mengelola jadwal kuliah     | SIA-UC02    | Mengelola Jadwal Kuliah   |
| SIA-R03      | Mengajukan KRS              | SIA-UC03    | Mengajukan KRS            |
| SIA-R04      | Memvalidasi KRS             | SIA-UC04    | Memvalidasi KRS           |
| SIA-R05      | Mengunduh bukti pengajuan   | SIA-UC05    | Mengunduh Bukti Pengajuan |
| SIA-R06      | Menyetujui atau menolak KRS | SIA-UC06    | Menyetujui / Menolak KRS  |

---

### 9. Kriteria Akhir Pengerjaan

Sebelum diagram dikumpulkan, pastikan seluruh ketentuan berikut sudah terpenuhi.

- [✅] Aktor Mahasiswa sudah terhubung dengan use case Melihat Jadwal Kuliah.
- [✅] Aktor Mahasiswa sudah terhubung dengan use case Mengajukan KRS.
- [✅] Aktor Admin Akademik sudah terhubung dengan use case Mengelola Jadwal Kuliah.
- [✅] Aktor Dosen Wali sudah terhubung dengan use case Menyetujui / Menolak KRS.
- [✅] Use case Mengajukan KRS sudah terhubung dengan Memvalidasi KRS menggunakan relasi `<<include>>`.
- [✅] Use case Mengunduh Bukti Pengajuan sudah terhubung dengan Mengajukan KRS menggunakan relasi `<<extend>>`.
- [✅] Extension point sudah dicantumkan dengan nama **Bukti pengajuan tersedia**.
- [✅] Kondisi extend sudah dicantumkan, yaitu **[Mahasiswa memilih unduh]**.
- [✅] Seluruh kebutuhan SIA-R01 sampai SIA-R06 sudah direpresentasikan dalam diagram.
- [✅] Diagram konsisten dengan deskripsi skenario, kebutuhan, dan asumsi sistem.

---

### 10. Kesimpulan

Sistem Informasi Akademik pada studi kasus ini memiliki tiga aktor utama, yaitu Mahasiswa, Admin Akademik, dan Dosen Wali.

Sistem menyediakan fungsi melihat jadwal kuliah, mengelola jadwal kuliah, mengajukan KRS, memvalidasi KRS, mengunduh bukti pengajuan, serta memproses persetujuan atau penolakan KRS.

Dalam pemodelan use case, proses validasi KRS menggunakan relasi `<<include>>` karena wajib dilakukan dalam setiap pengajuan. Sementara itu, proses mengunduh bukti pengajuan menggunakan relasi `<<extend>>` karena bersifat opsional dan tidak menentukan keberhasilan pengajuan KRS.
